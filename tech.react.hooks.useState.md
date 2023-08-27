---
id: tqj6py2sceelcb9bagv052k
title: useState
desc: ''
updated: 1687752524135
created: 1687752106232
---


<details>
<summary>Code of entire Component using this useState</summary>

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
      const interval = setInterval(() => {
         // Note how setYValue is accepting a function rather than a value.
         // 
         // This function takes the previous YValue and increments it.
         setYValue((prevYValue) => prevYValue + 1);
      }, 1000);

      return () => clearInterval(interval);
   }, []);
```
The updater_function 
```js
const [yValue, updater_function] = useState(6);
```
Can accept direct value or a function that uses previous value:

```js
setYValue(10); // Set yValue to 10
```

```js
setYValue((prevYValue) => prevYValue + 1); // Increment yValue by 1
```

## Related
A Related explanation about useEffect can be found here [[tech.react.hooks.useEffect.example-incrementing-value-on-interval-singleRun-of-useEffect]]