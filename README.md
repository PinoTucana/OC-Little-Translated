# OC-Little: ACPI Hotpatch Samples and Guides for OpenCore
# OC-Little： 适用于 OpenCore 的 ACPI 热补丁示例和指南

[![OpenCore Version](https://img.shields.io/badge/Supported_OpenCore_Version:-≤1.0.0-success.svg)](https://github.com/acidanthera/OpenCorePkg) ![macOS](https://img.shields.io/badge/Supported_macOS:-≤15.0-white.svg) ![Last Update](https://img.shields.io/badge/Last_Update_(yy/mm/dd):-24.06.16-blueviolet.svg)</br>![maciasl](https://user-images.githubusercontent.com/76865553/179583184-5efe6546-9f3a-4899-bdc1-5e9ec5a2927e.png)

## TABLE of CONTENTS
## 目录

**PREFACE**
/ **前言**

* [**Disclaimer**](#disclaimer)
/ **免责声明**
* [**About OC Little Translated**](#about)
/ **关于 OC Little 翻译**
* [**About the translation**](#about-the-translation)
/ **关于本翻译**

**MAIN**
/ **主要内容**

* [**ACPI Basics and Guides**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/00_ACPI)
/ **ACPI 基础知识和指南**
* [**Adding Virtual Devices and enabling Features with SSDTs**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/01_Adding_missing_Devices_and_enabling_Features#readme)
/ **使用 SSDT 添加虚拟设备并启用特性**
* [**Disabling Devices**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/02_Disabling_Devices)
/ **禁用设备**
* [**USB Port Mapping**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/03_USB_Fixes)
/ **USB 端口映射**
* [**Fixing Sleep and Wake Issues**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/04_Fixing_Sleep_and_Wake_Issues)
/ **修复睡眠和唤醒问题**
* [**Laptop-specific Patches**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/05_Laptop-specific_Patches)
/ **笔记本电脑特定的补丁**
* [**CMOS-related Fixes**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/06_CMOS-related_Fixes)
/ **CMOS 相关修复**
* [**BOOT Folder**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/07_BOOT_Folder#adding-and-configuring-contentflavour-and-contentvisibility)
/ **BOOT 文件夹**
* [**Quirks**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/08_Quirks)
/ **怪癖**
* [**Board-ID Skip and VMM Spoof**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/09_Board-ID_VMM-Spoof)
/ **跳过 Board-ID 以及 VMM 欺骗**
* [**Kext Loading Sequence Examples**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/10_Kexts_Loading_Sequence_Examples#readme)
/ **Kext 加载顺序示例**
* [**Graphics**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/11_Graphics) (integrated/discrete)
/ **图形显示（集成/独立）**
* [**MMIO Whitelist**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/12_MMIO_Whitelist)
/ **MMIO 白名单**
* [**Fixing Peripherals**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/13_Peripherals)
/ **修复外设**
* [**Fixing falsely reported RAM speed**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/15_RAM)
/ **修复错误报告的内存速度**
* [**Using OpenCore Legacy Patcher on Wintel systems**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/14_OCLP_Wintel#installing-newer-versions-of-macos-on-legacy-hardware) 
/ **在 Wintel 系统上使用 OpenCore 传统补丁程序**

**APPENDIX**
/ **附录**

* [**macOS 14.4 install workaround**](https://github.com/5T33Z0/OC-Little-Translated/blob/main/W_Workarounds/README.md)
/ **macOS 14.4 安装变通方案**
* [**Updating OpenCore**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/D_Updating_OpenCore#readme)
/ **更新 OpenCore**
* [**Fixing issues with System Update Notifications**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/S_System_Updates#readme)
/ **修复系统更新通知问题**
* [**Config Tips & Tricks**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/A_Config_Tips_and_Tricks#readme)
/ **配置技巧与窍门**
* [**Compatibility Charts**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/E_Compatibility_Charts)
/ **兼容性图表**
* [**Generating EFIs with OCAT**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/F_Desktop_EFIs#readme)
/ **使用 OCAT 生成 EFI**
* [**Create/modify a Layout-ID for AppleALC**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/L_ALC_Layout-ID#readme)
/ **为 AppleALC 创建/修改布局标识**
* [**Windows-related Guides**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/I_Windows)
/ **Windows 相关指南**
* [**Enabling Linux Boot Entries**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/G_Linux#readme)
/ **启用 Linux 引导条目**
* [**Boot Arguments Explained**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/H_Boot-args#readme)
/ **启动参数详解**
* [**OpenCore Calculators**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/B_OC_Calculators)
/ **OpenCore 计算器**
* [**Compiling slimmed-down variants of Kexts**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/J_Compiling_Kexts#readme)
/ **编译经过精简的 Kexts 变种**
* [**Debugging**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/K_Debugging#readme)
/ **调试**
* [**OpenCore EFI Upload Checklist**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/M_EFI_Upload_Chklst#readme)
/ **OpenCore EFI 上传检查表**
* [**Combining all SSDTs into one file (SSDT-ALL)**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/N_SSDT-ALL)
/ **将所有 SSDT 合并为一个文件 (SSDT-ALL)**
* [**Switching to NO_ACPI build of OpenCore**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/O_OC_NO_ACPI)
/ **切换到 OpenCore 的 NO_ACPI 构建**
* [**Using Clover alongside OpenCore**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/R_BootloaderChooser#readme)
/ **在使用 OpenCore 的同时使用 Clover**
* [**Utilities and Resource**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/C_Utilities_and_Resources#readme)
/ **实用工具和资源**
* [**Featured OpenCanopy Themes**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/T_Themes)
/ **OpenCanopy 特色主题**
* [**macOS Virtulization**](https://github.com/5T33Z0/OC-Little-Translated/tree/main/V_Virtualization#virtualization)
/ **macOS 虚拟化**
* [**Terminal Commands**](https://github.com/5T33Z0/OC-Little-Translated/blob/main/Terminal_Commands.md#readme)
/ **终端命令**

___

## DISCLAIMER
## 免责声明

1. OC-Little Translated is not an installation guide for getting your system up and running with macOS – use Dortania's excellent [**OpenCore Install Guide**](https://dortania.github.io/OpenCore-Install-Guide/) for that! Instead, it's a supplementary resource that offers guides and fixes for various issues related to hackintosh systems, along with explanations and context about how they work. It is regularly updated to reflect the latest discoveries and developments of the hackintosh community.

	OC-Little Translated 并不是让你的系统启动并运行 macOS 的安装指南--请使用 Dortania 出色的 [**OpenCore Install Guide**](https://dortania.github.io/OpenCore-Install-Guide/)！相反，它是一个补充资源，提供与 hackintosh 系统相关的各种问题的指南和修复方法，以及关于它们如何工作的解释和背景。它定期更新，以反映 hackintosh 社区的最新发现和发展。

2. The material presented in this repo is designed to empower users to create a *proper* working system running macOS without breaking ACPI-compliancy! Therefore, **OC-Little Translated** does not support methods which do not hold up to this premise – such as patching the `DSDT` – since it's not an *appropriate* measure to get the "Real Vanilla Hackintosh" experience. In fact, it's quite the opposite, [**as discussed here**](https://www.insanelymac.com/forum/topic/352881-when-is-rebaseregions-necessary/#comment-2790870).
	
	本软件仓库中提供的资料旨在帮助用户在不破坏 ACPI 兼容性的情况下，创建一个*正常*运行 macOS 的工作系统！因此，**OC-Little Translated** 不支持不符合这一前提的方法，例如修补`DSDT`，因为这不是一个获得 “真正原版 Hackintosh”体验的*合适*措施。事实上，情况恰恰相反，[**在此讨论**](https://www.insanelymac.com/forum/topic/352881-when-is-rebaseregions-necessary/#comment-2790870)。

## ABOUT
## 关于

Collection of guides, ACPI Hotpatches and Binary Renames for use with the OpenCore Boot Manager based on [**OC-Little by Daliansky**](https://github.com/daliansky/OC-little) translated from Chinese.

基于 [**OC-Little by Daliansky**](https://github.com/daliansky/OC-little) 翻译自中文的用于 OpenCore 启动管理器的指南、ACPI 热补丁和二进制重命名合集。

Besides the original translated guides, this repo contains additional guides complementary to the ones provided by the OpenCore Package and Dortania's OpenCore Guides. It covers a wide range of hackintosh-related topics, including: 

除翻译的原始指南外，该 repo 还包含 OpenCore 软件包和 Dortania 的 OpenCore 指南所提供的补充指南。它涵盖了与 hackintosh 相关的各种主题，包括：

- ACPI basics

	ACPI 基础知识

- Enabling devices and features

	启用设备和特性

- Fixing sleep/wake and other power-related issues

	修复睡眠/唤醒和其他电源相关问题

- Guides for Mapping USB Ports

	USB 端口映射指南

- Fixing Laptop-specific issues

	修复笔记本电脑特定问题

- Fixing graphics-related issues

	修复图形显示相关问题

- Config-related tips

	配置相关的提示

- Guides for using OpenCore Legacy Patcher on Wintel Systems

	在 Wintel 系统上使用 OpenCore Legacy Patcher 的指南

Check the table of contents for more. Although aimed primarily at OpenCore users, all of the SSDTs and most of the guides/techniques are applicable to Clover as well.

查看目录，了解更多信息。虽然主要针对 OpenCore 用户，但所有 SSDT 和大多数指南/技术也适用于 Clover。

### About the translation
### 关于翻译

- AI-based translation using deepL, google translator as well as manual copyediting.

	使用 deepL 和谷歌翻译进行人工智能翻译，并进行人工校对。

- Restructured the repository into more plausible (sub-)sections and categories based on types of issues, components, methods, etc.

	基于问题、组件、方法等分类，将资源库调整为更合理的（子）部分和类别。

- Restructured Texts for better readability and comprehensibility

	调整文本结构，提高可读性和可理解性

- Rewrote whole sections which were confusing/misleading (`ACPI` and `USB Port Mapping` for example)

	重写了全部容易被混淆/被误导的部分（例如 `ACPI` 和 `USB 端口映射`）。

- Added missing descriptions

	添加了缺失的说明

- Added further explanations where necessary

	必要时添加进一步解释

- Added new content (USB Port Mapping via ACPI, Chapters 7 to 14 as well as the whole "Appendix" section)

	添加新内容（通过 ACPI 进行 USB 端口映射、第 7 章至第 14 章，以及全部 “附录 ”部分）

> [!NOTE]
>
> 注意
>
> Due to the fact that I don't speak Chinese the translation might not be 100% accurate.
>
> 由于我不会中文，翻译可能不是 100% 准确。

## CONTRIBUTIONS
## 贡献

If you would like to contribute to the information provided in this repo in order to improve/expand it, feel free to create an issue with a meaningful title, link to the chapter/section and describe what you like to add, change, correct or expand upon.

如果您希望对本 repo 中提供的信息做出贡献，以改进/扩展它们，请创建一个问题，并附上有意义的标题，在问题中链接到相应章节/小节，并描述您希望添加、更改、更正或扩展的内容。

## 5T33Z0's 5H0UT 0UT5
## 来自 5T33Z0 的声音

- Thanks to the [**contributors**](https://github.com/5T33Z0/OC-Little-Translated/graphs/contributors) for improving and expanding the repo. Additional credits for contributors outside of the github realm are listed in the respective sections of the repo.

	感谢 [** 贡献者们**](https://github.com/5T33Z0/OC-Little-Translated/graphs/contributors) 对 repo 的改进和扩展。来自 github 之外的其他贡献者的功劳列在软件仓库的相应部分。

- sascha_77 for Kext Updater, ANYmacOS and helping me to unbrick my Lenovo T530 BIOS!

	感谢 sascha_77 改进了 Kext Updater、ANYmacOS 以及帮我解决联想 T530 BIOS 的故障！

- Apfelnico for introducing me to ASL/AML Basics

	感谢 Apfelnico 向我说明 ASL/AML 的基础知识

- Bluebyte for having good conversations

	与 Bluebyte 进行了有意义的交谈

- Cyberdevs from insanelymac for his Z170X Gaming 5 Guide and for being a prime example of a Moderator who treats others with respect!

	感谢来自 insanelymac 的 Cyberdevs，感谢他的 Z170X Gaming 5 指南 以及作为版主，他是尊重他人的典范！

<details>
<summary><strong>Daliansky's original Credits</strong></summary>
Daliansky 的原始感谢名单

> - Special credit to:
>
>	特别感谢：
>
> 	- @XianWu write these ACPI component patches that useable to OpenCore
>
>	编写可用于 OpenCore 的 ACPI 组件修补程序
>
> 	- @Bat.bat, @DalianSky, @athlonreg, @iStar丶Forever their proofreading and finalization.
>
>	不断地校对和定稿。
>
> - Credits and thanks to：
>
>	感谢：
>
> 	- @冬瓜-X1C5th
> 	- @OC-xlivans
> 	- @Air 13 IWL-GZ-Big Orange (OC perfect)
> 	- @子骏oc IWL
> 	- @大勇-小新air13-OC-划水小白
> 	- @xjn819
> 	- Acidanthera for maintaining OpenCorePkg
</details>
