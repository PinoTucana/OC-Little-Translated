# Keyboard Layouts
# 键盘布局

The selected keyboard layout determines the language used during macOS installation. It also sets the language used for audio localization. So unless you want to use Russian as your default language, you should change the `prev-lang:kbd` setting in the config.plist beforehand. Both `String` and `Data` are supported data formats.

所选键盘布局决定了 macOS 安装过程中使用的语言。它还会设置用于音频本地化的语言。因此，除非你想使用俄语作为默认语言，否则应事先更改 config.plist 中的 `prev-lang:kbd` 设置。`String` 和 `Data` 都是支持的数据格式。

:bulb: When working with beta releases of macOS, you should use the American English layout to avoid grey screen issues. Grey screens are empty windows with a grey background caused by selecting a localization which hasn't been implemented so [there's no text to display](https://www.hackintosh-forum.de/attachment/154356-fehler-png/) and you can't continue with the installation.

:bulb: 使用 macOS 测试版时，应使用美式英语布局以避免灰屏问题。灰屏是由于选择了尚未实现的本地化而导致的灰背景空窗口，因此 [没有文本显示](https://www.hackintosh-forum.de/attachment/154356-fehler-png/)，无法继续安装。

**Location**: `NVRAM/Add/7C436110-AB2A-4BBB-A880-FE41995C9F82/`</br>
**Key**: `prev-lang:kbd`

Layout | String | Data (HEX)
-------|--------|------
Russian (default)| ru-RU:252 |72752D52553A323532
English (American)| en-US:0| 656e2d55533a30
Spanish (ISO)|es:87|65733A3837
German (De)|de-DE:3|64652D44453A33
French (PC)|fr:60|66723A3630
Italian |it:4|69743A34

**More Layouts**: [AppleKeyboardLayouts.txt](https://github.com/acidanthera/OpenCorePkg/blob/master/Utilities/AppleKeyboardLayouts/AppleKeyboardLayouts.txt) (need to be converted to HEX)

**更多布局**：[AppleKeyboardLayouts.txt](https://github.com/acidanthera/OpenCorePkg/blob/master/Utilities/AppleKeyboardLayouts/AppleKeyboardLayouts.txt) (需要被转换至 HEX)