---
id: z5bke8opiluvljv9p9339e3
title: Difference between Quotes and Angle Brackets
desc: ''
updated: 1679163757193
created: 1679163757193
---

In C++, there is a difference between including a header file using double quotes " and using angle brackets < >.

When you use double quotes to include a header file, the compiler first looks for the header file in the current directory, and if it is not found, it searches for it in the directories specified by the -I (capital letter I) option.

On the other hand, when you use angle brackets to include a header file, the compiler only searches for the header file in the directories specified by the -I option. It does not search in the current directory.

In general, headers that are part of the standard C++ library are included using angle brackets, while headers that are specific to a project or library are included using double quotes.

In the case of `#include "git2.h"`, the compiler will first look for the git2.h file in the current directory, and if it is not found there, it will look in the directories specified by the -I option.

In the case of `#include <git2.h>`, the compiler will only look for the git2.h file in the directories specified by the -I option, and not in the current directory.