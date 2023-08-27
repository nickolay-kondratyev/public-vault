---
id: 7ikdy4gnzhygn2coc6rxg5j
title: Creating View Model Data in Model
desc: ''
updated: 1669403304734
created: 1669403131061
---

Creating view model data within the data layer is very-strong code smell. Model data layer shouldn't know anything of view model. 

ViewModel is a higher level of abstraction.

Same as ViewModel shouldn't use View model constructs. Since if any View model constructs are used within ViewModel then the View cannot be swapped out. 
