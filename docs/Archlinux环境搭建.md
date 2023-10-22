# Archlinux 环境搭建

## 安装 ARM GCC 编译环境

- [GNU Arm Embedded Toolchain](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm/downloads)

```shell
sudo pacman -S arm-none-eabi-gcc arm-none-eabi-newlib
```

## 有 ARM 支持的 GDB

有 ARM 仿真支持的 QEMU 用于调试 ARM Cortex-M 程序的 GDB 命令

```shell
sudo pacman -S arm-none-eabi-gdb
```

## Openocd 调试器

- [OpenOCD](http://openocd.org/getting-openocd/)

```shell
sudo pacman -S openocd
```

- 烧录文件

```shell
openocd -f path/to/your/openocd/interface/config.cfg -f path/to/your/openocd/target/config.cfg -c "program path/to/your/compiled/file.elf verify reset exit"
```

- tasks.json, 可以将这些命令添加到 VSCode 的 tasks.json 文件中，以便在 VSCode 中直接执行烧录任务。

```shell
{
  "label": "flash",
  "type": "shell",
  "command": "openocd -f path/to/your/openocd/interface/config.cfg -f path/to/your/openocd/target/config.cfg -c \"program path/to/your/compiled/file.elf verify reset exit\"",
  "group": "build",
  "problemMatcher": []
}
```

## 2.使用 J-Link：

- 首先从 Segger 官网下载并安装 [J-Link 软件包](https://www.segger.com/downloads/jlink/#J-LinkSoftwareAndDocumentationPack)
- 使用以下命令烧录文件（请根据您的目标文件进行修改）：

```shell
JLinkExe -if swd -device YourDeviceName -speed 4000 -autoconnect 1 -CommanderScript path/to/your/jlink_script.jlink
```

- 其中，jlink_script.jlink 是一个包含以下内容的文本文件（请根据您的目标文件进行修改）：

```shell
loadfile path/to/your/compiled/file.hex
r
g
q
```

## ST-Link（仅适用于 STM32 设备）

- 首先安装 ST-Link 实用程序

```shell
sudo pacman -S extra/stlink
```

- 命令烧录文件（请根据您的目标文件进行修改）

```shell
st-flash write path/to/your/compiled/file.bin 0x8000000
```
