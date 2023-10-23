# VSCode 搭建 STM32 开发环境

这是一个使用 VSCode 搭建 stm32f103 开发环境的示例。

## 编译指令配置

当添加新的模块时需要在 `.vscode/c_cpp_properties.json` 与 `.vscode/tasks.json` 文件中进行配置。牵着用于将代码模块引入工作空间，后者用于编译。

新增模块时需要在 `"${workspaceFolder}/user/src/main.c"` 后面将`.c` 文件追加至后面。

## 烧录方式

- ST-Util
- OpenOCD

## 参考

- 2022 年了 vscode 推出了 Embedded IDE 插件，适用于 8051/STM8/Cortex-M/RISC-V 的单片机开发环境。能够在 vscode 上提供 8051, STM8, Cortex-M, RISC-V 项目的 开发, 编译, 烧录 功能。
- [VSCode 和 CMake 搭建嵌入式开发环境](https://blog.csdn.net/jf_52001760/article/details/126826393)
- [VSCode 搭建 STM32 开发环境](https://blog.csdn.net/m0_47329175/article/details/122607874)
