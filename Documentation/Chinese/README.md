# :fox_face: Arctic Fox  
另一个重新设计的、集成 Xcode 代码的计算机项目

## 目录
* [构建说明](#构建说明)  
  * [BIOS 设置](#bios-设置)  
* [准备安装介质](#准备安装介质)  
* [安装引导加载器](#安装引导加载器)  
* [内核扩展](#内核扩展)  
  * [必需](#必需)  
  * [后安装](#后安装)  
  * [可选](#可选)  
* [安装到引导驱动器](#安装到引导驱动器)  
  * USB 闪存盘  
  * 引导驱动器  
* [版本发布](#版本发布)  
* [兼容性](#兼容性)  
* [许可证](#许可证)  
* [免责声明](#免责声明)

## 构建说明
完整规格请查看：`http://gixxer.us/2Jslljx`

## BIOS 设置
详细 BIOS 设置请参阅 [BIOS 设置 Wiki](/English/BIOS.md)。  
 * [M.I.T.](/English/BIOS.md#fox_face-mit)  
 * [系统](/English/BIOS.md#fox_face-system)  
 * [BIOS](/English/BIOS.md#fox_face-bios)  
 * [外设](/English/BIOS.md#fox_face-peripherals)  
 * [芯片组](/English/BIOS.md#fox_face-chipset)  
 * [电源](/English/BIOS.md#fox_face-power)  
 * [保存并退出](/English/BIOS.md#fox_face-save--exit)

## 准备安装介质
1. 从 Mac App Store 下载 [macOS Sierra](https://www.dualbootpc.com/software/system/macos/sierra/) 安装器  
2. 打开终端并输入以下命令格式化 [USB 设备](https://www.dualbootpc.com/hardware/usb/)：
   `diskutil partitionDisk /dev/{DISK_ID} GPT JHFS+ "SierraUSB" 100%`  
3. 将 16GB 分区分为 12GB (SierraUSB) 和 4GB (Post Installation)  
4. [创建可启动 macOS 安装器](https://www.dualbootpc.com/guide/creating-a-usb-installer/)：
   `sudo /Applications/Install\ macOS\ Sierra.app/Contents/Resources/createinstallmedia --volume /Volumes/SierraUSB --applicationpath /Applications/Install\ macOS\ Sierra.app`  
5. 终端完成后，USB 名称为：
   `Install macOS Sierra`

## 安装引导加载器
**USB 闪存盘**  
* 下载 [Clover 2.4k r4934](https://github.com/nyhtml/Arctic-Fox/releases/tag/0.1.0)  
* 使用以下选项自定义安装到 USB：  
  * 仅用于 UEFI 启动  
  * 安装到 ESP  
  * 必需驱动程序：ApfsDriverLoader、AptioMemoryFix、HFSPlus  
  * 推荐驱动程序：AudioDxe、NvmExpress  

**引导驱动器**  
* 从 USB 的 EFI 文件夹导出 **BOOT** 和 **CLOVER** 到目标引导盘  
* 安装 [Clover 2.5k r5119](https://github.com/nyhtml/Arctic-Fox/releases/tag/1.6.4)，并选择以下选项：  
  * 安装 RC 脚本到目标卷  
  * 安装 Clover 设置面板（后安装期间选择）  
* 弹出所有 USB 驱动器并重启进入 BIOS  
* 设置使用 Clover 的驱动器为主启动盘并退出

## 内核扩展
### [必需](https://github.com/nyhtml/Arctic-Fox/releases/tag/0.1.0)  
  * FakeSMC.kext  
  * Lili.kext  
  * WhateverGreen.kext  

### [后安装](https://github.com/nyhtml/Arctic-Fox/releases/tag/1.1.0)  
  * AppleALC.kext  
  * IntelMausiEthernet.kext  
  * USBInjectAll.kext  
  * XHCI-200-series-injector.kext  

### [可选](https://github.com/nyhtml/KEANU)  
  * CPUFriend.kext  
  * RealtekRTL8111.kext  
  * RtWlanU.kext  
  * RtWlanU1827.kext  

## 安装到引导驱动器
1. 将包含 v1.5.0 的 USB 插入 USB2.0 接口并在 BIOS 中设置为第一启动项  
2. 将系统日期改为对应的 [macOS 发布日期](https://www.dualbootpc.com/guide/release-date/)

## 版本发布
请查看 [最新版本](https://github.com/nyhtml/Arctic-Fox/releases)

## 兼容性
* macOS（Big Sur, Catalina, Mojave, High Sierra, Sierra）  
* Ubuntu Desktop  
* Windows（11, 10, 8, 7）

## 许可证
详细信息见 [MIT 许可证](https://github.com/nyhtml/Arctic-Fox/blob/main/LICENSE)

## 免责声明
本 [Arctic Fox](https://github.com/nyhtml/Arctic-Fox/) 仓库按“原样”提供，不提供任何明示或暗示的担保，  
包括但不限于适销性、特定用途适用性及非侵权的担保。作者或版权所有人不对因使用软件产生的任何索赔、  
损害或其他责任承担责任。
