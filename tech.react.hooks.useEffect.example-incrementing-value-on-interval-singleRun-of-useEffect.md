---
id: p3ox0pkjlll40qggn8gouo3
title: 'useEffect: Example incrementing value on interval (Singel run of useEffect)'
desc: ''
updated: 1687753396308
created: 1687752255145
---

<details>
<summary>Code of entire Component using this useEffect</summary>

```js
/* eslint-disable */
import React, { useState, useEffect } from 'react';
import Plot from 'react-plotly.js';

const MyComponent = () => {
   const [yValue, setYValue] = useState(6);

   useEffect(() => {
      const interval = setInterval(() => {
         setYValue((prevYValue) => prevYValue + 1);
      }, 1000);

      return () => clearInterval(interval);
   }, []);

   return (
      <>
         <Plot
            data={[
               {
                  x: [1, 2, 3],
                  y: [2, yValue, 3],
                  type: 'scatter',
                  mode: 'lines+markers',
                  marker: {color: 'red'},
               },
               {type: 'bar', x: [1, 2, 3], y: [2, yValue, 3]},
            ]}
            layout={{width: 800, height: 400, title: 'A Fancy Plot'}}
         />
      </>
   );
};

export default MyComponent;
```
</details>

```js
   const [yValue, setYValue] = useState(6);

   useEffect(() => {
      // The interval ID returned by setInterval is
      // stored in the interval variable.
      const interval = setInterval(() => {
         setYValue((prevYValue) => prevYValue + 1);
      }, 1000);

      // The effect function returns a cleanup function. 
      // This cleanup function is called when the component unmounts or 
      // when the effect is re-run. 
      // 
      // In this case, it clears the interval using clearInterval to 
      // prevent memory leaks and stop the timer.
      return () => clearInterval(interval);
   }, []);
```



The `useEffect` hook takes two arguments: 
1. a function
2. a dependency array. 

In this case, the dependency array `[]` is empty, indicating that the effect should only run once when the component mounts.