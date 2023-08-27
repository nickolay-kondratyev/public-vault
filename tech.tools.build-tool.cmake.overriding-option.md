---
id: jzjluymaj5yuh11q2h48zc9
title: Overriding Option
desc: ''
updated: 1676474914161
created: 1676443413036
---

Example option in [[tech.tools.build-tool.cmake.CMakeListsTxt]]:
```cmake
option(MY_OPTION "My Option" ON)
```

Example overriding option at runtime:
```shell
cmake -DMY_OPTION=OFF -S . -B ./build && cd build && make && echo "Build done."
```

<details>
<summary>Working Example</summary>

```shell
gt.sandbox.checkout.commit.cleanly 315b92c \
&& cd cpp/cmake-options \
&& cmake -DMY_OPTION=OFF -S . -B ./build && cd ./build && make \
&& ./MyMain
```
</details>

<details>
<summary>Video Ref Timestamp</summary>

[Video Ref timestamp](https://youtu.be/ED-WUk440qc?t=630)
</details>


