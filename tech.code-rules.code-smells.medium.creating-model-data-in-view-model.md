---
id: 9tojjl5lnfj2pjz9rquygkb
title: Creating Model Data in View Model
desc: ''
updated: 1669403121591
created: 1669403047450
---

If you are creating model data objects in your view model layer that is a code smell. 

Why isn't the model layer object created within the model layer?

ViewModel is a higher level of abstraction it should get the data layer data and can use it within it, but if its creating it there better be a very strong reason.

