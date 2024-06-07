# Terminal Commands
# 终端命令

## macOS Look and Feel
## macOS 外观和感觉

### Defaults
### 默认值

Collection of `Defaults` commands For modifying macOS default settings/behavior.

`默认` 命令集，用于修改 macOS 默认的设置/行为。

**https://macos-defaults.com/**

### Power Management
### 电源管理

Collection of `PMSET` commands to adjust Powwer Management (Standby, Sleep, Hibernation, etc.)

`PMSET` 命令集，用于调整电源管理（待机、睡眠、休眠等）

**https://www.dssw.co.uk/reference/pmset.html**

#### Check Hibernation Settings
#### 查看休眠设置

`pmset -g`

#### Checking Reasons for Wake
#### 查看唤醒原因

```shell
pmset -g log | grep -e "Sleep.*due to" -e "Wake.*due to"
```

Alternative Command (searches in syslog instead):

替代命令（在 syslog 中搜索）：

```shell
log show --style syslog | fgrep "Wake reason"
```

#### Disable Power Management Scheduler
#### 禁用电源管理调度

Fixes high CPU usage for `Powerd` service in macOS Ventura beta 4

修复 macOS Ventura beta 4 中 `Powerd` 服务 CPU 占用率高的问题

```shell
sudo pmset schedule cancelall
```

### Disable Notification Center
### 禁用通知中心

- Disable:

	禁用：

	```shell
	launchctl unload -w /System/Library/LaunchAgents/com.apple.notificationcenterui.plist
	```
	
- Re-Enable:

	重新启用：

	```shell
	launchctl load -w /System/Library/LaunchAgents/com.apple.notificationcenterui.plist
	```	

### Enable Key Repeating
### 启用按键重复

```shell
defaults write -g ApplePressAndHoldEnabled -bool false
```

### Add "GPU" Tab to Activity Monitor
### 在活动监视器中添加 “GPU” 选项卡

```shell
defaults write com.apple.ActivityMonitor ShowGPUTab -bool true
```

### macOS Info
### macOS 信息

#### Display macOS Version and Build Number
#### 显示 macOS 版本和构建编号

```shell
sw_vers
```
#### Display Darwin Kernel Version
#### 显示 Darwin 内核版本

```shell
uname -r
```

### Display Model Identifier (SMBIOS)
### 显示型号标识符（SMBIOS）

```shell
system_profiler SPHardwareDataType | grep 'Model Identifier'
```

## System Behavior
## 系统行为

### Disable Gatekeeper
### 禁用 Gatekeeper

```shell
sudo spctl --master-disable
```

### Disable DMG verification
### 禁用 DMG 验证

-  Disable Disk Image verification:

    禁用磁盘镜像验证：

	```shell
	defaults write com.apple.frameworks.diskimages skip-verify TRUE
	```
-  To Re-enable: 

    重新启用：

	```shell
	defaults write com.apple.frameworks.diskimages skip-verify FALSE
	``` 

### Change Update Seed to Developer (≤ macOS 12 only)
### 将更新种子切换为开发者（仅适用于 macOS ≤ 12）

1. Unenroll from current seed:

	从当前种子取消注册：

	```shell
	sudo /System/Library/PrivateFrameworks/Seeding.framework/Resources/seedutil unenroll
	```
2. Change seed:

	更换种子：

	```
	sudo /System/Library/PrivateFrameworks/Seeding.framework/Resources/seedutil enroll DeveloperSeed
	```

> [!NOTE]
> 
> 注意
>.
> In macOS 13+, [switching update seeds via seedutil is no longer supported](https://nwstrauss.com/posts/2023-05-18-seedutil-beta-programs/). Instead, registering your system in Apples [beta program](https://beta.apple.com/) via Apple-ID is required. After that you can switch the updated seed in system sttings. 
>
> 在 macOS 13+ 中，不再支持 [通过 seedutil 切换更新种子](https://nwstrauss.com/posts/2023-05-18-seedutil-beta-programs/)。取而代之的是，需要使用 Apple-ID 在苹果 [beta 计划](https://beta.apple.com/) 中注册你的系统。之后，你就可以在系统设置中切换更新种子了。

### Reset all Privacy Settings
### 重置所有隐私设置
Brings back all the window pop-ups that ask for granting pernission to access periferals like microphones, webcams, etc.

恢复所有弹出窗口警告，这些窗口会要求用户授予访问麦克风、网络摄像头等设备的权限。

```shell
tccutil reset All
```

## Finder-related
## Finder 相关

### Show User Library in macOS 11 and newer
### 在 macOS 11 及更高版本中显示用户库

```shell
setfile -a v ~/Library
chflags nohidden ~/Library
```

### Show all Files and Folders in Finder
### 在 Finder中显示所有文件和文件夹

- Show: 

	显示

	```shell
	defaults write com.apple.finder AppleShowAllFiles TRUE && killall Finder
	```
- Hide:

	隐藏

	```shell
	defaults write com.apple.finder AppleShowAllFiles FALSE && killall Finder
	```

> [!NOTE] 
>
> 注意
> 
> Alternatively, simply use this Keyboard Shortcut: <kbd>⌘</kbd><kbd>⇧</kbd><kbd>.</kbd> (Command+Shift+Dot)
>
> 或者，只需使用此键盘快捷键： <kbd>⌘</kbd><kbd>⇧</kbd><kbd>.</kbd> (Command+Shift+Dot)

### Rebuilding Launch Services
### 重建启动服务

You can use this to fix the “Open with…” sub-menu (if it contains entries from apps that are no onger installed, etc.)  
你可以用它来修复 “用......打开” 子菜单（如果其中包含已不再安装的应用程序的条目等）。 

```shell
/System/Library/Frameworks/CoreServices.framework/Frameworks/LaunchServices.framework/Support/lsregister -kill -r -domain local -domain system -domain user
```

### Add "Quit" option to Finder menu
### 在 Finder 菜单中添加 “退出” 选项

```shell
defaults write com.apple.finder "QuitMenuItem" -bool "true" && killall Finder
```

### Disable `.DS_Store` file creation on network storages
### 禁用在网络存储器上创建 `.DS_Store` 文件

- Disable:

	禁用

	```shell
	defaults write com.apple.desktopservices DSDontWriteNetworkStores -bool true
	```

- Re-enable:

	重新启用

	```shell
	defaults write com.apple.desktopservices DSDontWriteNetworkStores -bool false
	```

## Filesystem-related
## 文件系统相关

### Rebuilding the Spotlight Index
### 重建 Spotlight 索引

- System-wide: 
	
	系统级别：

	```shell
	sudo mdutil -a -i off
	sudo mdutil -a -i on
	```

- For a specific volume:

	对于特定的卷：

	```shell
	sudo mdutil -i off /Volumes/Your Volume Name
	sudo mdutil -i on /Volumes/Your Volume Name
	```

### Checking if the APFS volume snapshots is intact
### 检查 APFS 卷的快照是否完好无损

```shell
diskutil apfs list
```

> [!NOTE]
>
> 注意
> 
> If you apply root patches with OCLP, the status of the entry `Snapshot sealed` seal will change from `Yes` to `Broken`. But if you revert the root patches with OCLP *prior* to updating macOS, the seal will become intact again. And if the snapshot is sealed, incremental (or delta) OTA updates are available again so System Update won't download the complete installer!
>
> 如果使用 OCLP 应用执行根修补程序，`快照密封` 密封条目的状态将从 `完整的` 变为 `已受损`。如果在更新 macOS 之前使用 OCLP 还原根修补程序，封印将再次变回完整。如果快照为完整密封状态，增量（也叫 delta）OTA 更新将再次被启用，因此系统更新不会下载完整的安装程序！

### Update the PreBoot Volume (APFS volumes only)
### 更新预启动卷（仅限 APFS 卷）

```shell
sudo diskutil apfs updatePreboot /
```

### Disable Library Validation
### 禁用库验证

```shell
sudo defaults write /Library/Preferences/com.apple.security.libraryvalidation.plist DisableLibraryValidation -bool true
```

> [!NOTE]
>
> 注意
>
> This change is only temporary. Requires a Kernel Patch to make it persistant.
>
> 此更改只是暂时的。需要内核补丁才能使它持久化

### Rebuild DYLD and XPC caches (macOS 10.15 or older only)
#### 重建 DYLD 和 XPC 缓存（仅限 macOS 10.15 或更旧版本）

```shell
sudo update_dyld_shared_cache -force
sudo /usr/libexec/xpchelper --rebuild-cache
```

### Create new snapshot (macOS 11+ only)
### 创建新的快照（仅限 macOS 11+）

In Recovery, enter:
在 Recovery 环境中，输入：

```shell
csrutil authenticated-root disable
bless --folder /Volumes/x/System/Library/CoreServices --bootefi --create-snapshot
``` 
**x** = name of your macOS Volume
**x** = macOS 卷名称

## Enabling/Disabling Features
## 启用/禁用特性

### Enable Sidecar
### 启用侧边栏

```shell
defaults write com.apple.sidecar.display AllowAllDevices -bool true
defaults write com.apple.sidecar.display hasShownPref -bool true
```

> [!NOTE]
>
> 注意
> 
> Requires Intel CPU with on-board graphics and is limited to specific SMBIOSes. It’s easier to enable it via [**FeatureUnlock.kext**](https://github.com/acidanthera/FeatureUnlock)!
>
> 需要配备集成图形处理器的英特尔 CPU，并仅限于特定的 SMBIOS。更为简单的方法是通过 [**FeatureUnlock.kext**](https://github.com/acidanthera/FeatureUnlock) 启用该功能！

### Disable Logging
### 禁用日志记录

```shell
sudo rm /System/Library/LaunchDaemons/com.apple.syslogd.plist
```

### Disable/Delete Metal Support
### 禁用/删除 Metal 支持

```shell
sudo defaults write /Library/Preferences/com.apple.CoreDisplay useMetal -boolean no
sudo defaults write /Library/Preferences/com.apple.CoreDisplay useIOP -boolean no
```
or:

或者：

```shell
sudo defaults delete /Library/Preferences/com.apple.CoreDisplay useMetal
sudo defaults delete /Library/Preferences/com.apple.CoreDisplay useIOP
```
[**Source**](https://github.com/lvs1974/NvidiaGraphicsFixup/releases)
/ **来源**

### Prohibit macOS from mastering iDevices
### 禁止 macOS 掌控 iDevices

```shell
defaults write com.apple.iTunesHelper ignore-devices -bool YES
defaults write com.apple.AMPDeviceDiscoveryAgent ignore-devices 1
defaults write com.apple.AMPDeviceDiscoveryAgent reveal-devices 0
defaults write -g ignore-devices -bool true
```
**Source**: [**Apple-Knowledge**](https://github.com/hack-different/apple-knowledge/blob/main/_docs/USB_Modes.md)
/ **来源**

### Change default state of Bluetooth (on/off)
### 更改蓝牙的默认状态（开/关）

&rarr; Check this [guide](https://mogutan.wordpress.com/2018/07/24/switch-bluetooth-setting-from-command-line-on-macos/) for instructions.

&rarr; 请查阅本 [指南](https://mogutan.wordpress.com/2018/07/24/switch-bluetooth-setting-from-command-line-on-macos/)，了解相关说明。

## Networking
## 网络

### List MAC Addresses of Network Adapters
### 列出网络适配器的 MAC 地址

```shell
networksetup -listallhardwareports
```

### Delete Network .plists
### 删除网络相关的 .plists

```shell
sudo rm /Library/Preferences/SystemConfiguration/NetworkInterfaces.plist
sudo rm /Library/Preferences/SystemConfiguration/preferences.plist
```

## CPU-related
## CPU 相关

### Show CPU Vendor
### 显示 CPU 供应商

```shell
sysctl -a | grep machdep.cpu.vendor
```

### Show CPU Model
### 显示 CPU 型号

Doesn't really tell you much

并没有很多实质内容

```shell
sysctl -a | grep machdep.cpu.model
```

### Show CPU Brand String
### 显示 CPU 品牌

```shell
sysctl machdep.cpu.brand_string
```

### List CPU features
### 列出 CPU 的特性

```shell
sysctl -a | grep machdep.cpu.features
```

### Display Bus and CPU Frequency
### 显示总线和 CPU 频率

```shell
sysctl -a | grep freq
```

### List supported CPU instructions
### 列出受支持的 CPU 指令

```shell
sysctl -a | grep machdep.cpu.leaf7_features
```

### Get CPU details from IO Registry
### 从 IO 注册表中获取 CPU 的详细信息

```shell
ioreg -rxn "CPU0@0"
```

> [!NOTE]
>
> 注意
> 
> Text in quotation marks = CPU name as defined in ACPI. On Intel CPUs it can also be "PR00@0", "P000@0" or "C000@0". Check `SSDT-PLUG`/`SSDT-PM` to find the correct name.
>
> 引号中的文字 = ACPI 中定义的 CPU 名称。在 Intel CPU 上，也可以是 “PR00@0”、“P000@0 ”或 “C000@0”。请核对 `SSDT-PLUG`/`SSDT-PM` 以查找正确的名称。

## Troubleshooting
## 故障排除

### Show log of last boot
### 显示上一次启动日志

```shell
log show --last boot
```

### Search for terms in last boot log
### 在上一次启动日志中搜索条目

```shell
log show --last boot | grep "your search term"
```
**Example**: `log show --last boot | grep "ACPI"`

**例**: `log show --last boot | grep "ACPI"`

### Check OpenCore version
### 检查 OpenCore 版本

```shell
nvram 4D1FDA02-38C7-4A6A-9CC6-4BCCA8B30102:opencore-version
```

### Display currently used Board-ID
### 显示当前使用的 Board-ID

```shell
ioreg -l | grep -i board-id
```
or

或者

```shell
`var_ID=$(ioreg -p IODeviceTree -r -n / -d 1 | grep board-id);var_ID=${var_ID##*<\"};var_ID=${var_ID%%\">};echo $var_ID`
```

### Checking Reasons for Wake
### 检查唤醒原因

```shell
pmset -g log | grep -e "Sleep.*due to" -e "Wake.*due to"
```

Alternative Command (searches in syslog instead):

替代命令（在 syslog 中搜索）：

```shell
log show --style syslog | fgrep "Wake reason"
```

### Check currently active `csr-active-config`
### 检查当前激活的 `csr-active-config` 配置

```shell
nvram 7C436110-AB2A-4BBB-A880-FE41995C9F82:csr-active-config
```

### Check the status of System Integrity Protection (SIP)
### 检查系统完整性保护 (SIP) 的状态

```shell
csrutil status
```

### Install Command Line Developer Tools
### 安装命令行开发工具

```shell
xcode-select --install
```

### Kext-related
### Kext 相关

#### Find loaded Kexts (excluding those from Apple)
#### 查找已加载的 Kext（不包括来自 Apple 的 Kext）

```shell
kextstat | grep -v com.apple
```

#### Rebuild Kext Cache (macOS 11+)
#### 重建 Kext 缓存（macOS 11+）

```shell
sudo kextcache -U /
```

#### Rebuild Kext Cache (macOS 10.15 or older)
#### 重建 Kext 缓存（macOS 10.15 或更旧版本）

```shell
sudo kextcache -i /
```

### Check status of Apple Secure Boot
### 检查 Apple Secure Boot 的状态

1. In Terminal, enter:</br>
    在终端中，输入：</br>
`nvram 94b73556-2197-4702-82a8-3e1337dafbfb:AppleSecureBootPolicy` 
2. Check the Results:

    验证结果：
	-  if `%00` = No Security
	-  if `%01` = Medium Security
	-  if `%02` = Full Security

> [!NOTE]
>
> 注意
>
> To achieve full securiity `02` additional measures are required.
>
> 为实现完整安全性 `02`，还需要采取其他措施。

### Make .command files executable
### 使 .command 文件可执行

`chmod +x` (drag file in terminal, hit enter)

### Finding USB Controller Renames
### 查找被重命名的 USB 控制器

```shell
ioreg -l -p IOService -w0 | grep -i EHC1
ioreg -l -p IOService -w0 | grep -i EHC2
ioreg -l -p IOService -w0 | grep -i XHC1
ioreg -l -p IOService -w0 | grep -i XHCI
```
### Verifying if SMBus is working
### 验证 SMBus 是否正常工作

```shell
kextstat | grep -E "AppleSMBusController|AppleSMBusPCI"
```

> [!NOTE]
> 
> 注意
>
> The search should return two matches: `com.apple.driver.AppleSMBusController` and `com.apple.driver.AppleSMBusPCI`. On modern Laptops, only AppleSMBusController may return in the search results!
>
> 搜索结果应返回两个匹配项： `com.apple.driver.AppleSMBusController` 和 `com.apple.driver.AppleSMBusPCI`。在现代笔记本电脑上，搜索结果可能只显示 AppleSMBusController！

### ACPI-related
### ACPI 相关
#### Debug ACPI Tables
#### 调试 ACPI 表

```shell
log show --predicate "processID == 0" --start $(date "+%Y-%m-%d") --debug | grep "ACPI"
```

#### List ACPI Errors
#### ACPI 错误清单

```shell
log show --last boot | grep AppleACPIPlatform
log show --last boot | grep AppleACPIPlatform > ~/Desktop/Log_"$(date '+%Y-%m-%d_%H-%M-%S')".log
```

The 2nd Command saves a log on the desktop.

第 2 个命令会将日志保存在桌面上。
___

## Keyboard Shortcuts
## 键盘快捷键

### Collection of Keyboard Shortcuts
### 键盘快捷键集

[**Mac Keyboard Shortcuts**](https://support.apple.com/en-us/HT201236)
/ **Mac 键盘快捷键**

### Show hidden Files and Folders in Finder
### 在 Finder 中显示隐藏文件和文件夹

<kbd>⌘</kbd><kbd>⇧</kbd><kbd>.</kbd> (Command+Shift+Dot)

### Disable Press and Hold for Keyboard Keys (requires reboot)
### 禁用键盘按键的长按功能（需要重新启动）

```shell
defaults write -g ApplePressAndHoldEnabled -bool false
```

### Accessing Terminal in macOS Setup-Assistant
### 在 macOS 安装助手中访问终端

<kbd>⌘</kbd><kbd>⌥</kbd><kbd>⌃</kbd><kbd>T</kbd> (Command+Option+Control+T)

---
## Linux

### Generate Audio Codec Dump (in Linux)
### 生成音频编解码器转储（在 Linux 中）

```shell
cd ~/Desktop && mkdir CodecDump && for c in /proc/asound/card*/codec#*; do f="${c/\/*card/card}"; cat "$c" > CodecDump/${f//\//-}.txt; done && zip -r CodecDump.zip CodecDump
```

### Search for firmware used by devices
### 搜索设备使用的固件

```shell
sudo dmesg|grep -i firmware
```
