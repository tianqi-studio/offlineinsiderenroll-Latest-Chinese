# OfflineInsiderEnroll


## 简介
OfflineInsiderEnroll 是一款简易的 Windows 命令提示符脚本，用于在未登录微软账户的设备上启用 **_Windows 预览体验计划_** 的访问权限。
本脚本仅兼容 Windows 11 以及 Windows 10 1809 及更高版本。
* apoint123的简体中文分支：https://github.com/apoint123/offlineinsiderenroll
* abbodi1406的原仓库：https://github.com/abbodi1406/offlineinsiderenroll

## 使用方法
运行本脚本需要管理员权限。你只需右键点击脚本文件，选择「以管理员身份运行」即可执行。

### 安装与配置修改
脚本启动后，会提供 **_Windows 预览体验计划_** 的多个通道选项供你选择。
按下对应选项的字母键，再按回车键即可完成选择。

如果你的设备此前未加入过预览体验计划，系统会提示你重启设备，以启用 _`Microsoft Flight Signing`_（微软飞行签名）——这是 _`Windows 预览体验计划`_ 的必要前提。

### 注意事项
_`Windows 预览体验计划`_ 要求将遥测级别设置为 _`Full`_（完整）。
在将设备加入预览体验计划后，请确认你的诊断数据收集设置已调整为「完整」。如果遥测设置不正确，部分 `Insider Preview` 预览版本可能不会通过 `Windows Update`（Windows 更新）推送给你。

你可以按照以下路径查看或修改遥测设置：
**Windows 11**：_`设置`_ > _`隐私和安全性`_ > _`诊断和反馈`_
**Windows 10**：_`设置`_ > _`隐私`_ > _`诊断和反馈`_

### 恢复 Windows 预览体验计划默认设置
若要将 _`Windows 预览体验计划`_ 恢复为默认设置，只需在 `OfflineInsiderEnroll 脚本` 中选择 `停止接收预览体验成员预览版` 即可。选择该选项后系统会提示重启，因为此操作会禁用 _`Microsoft Flight Signing`_。

## 实现原理
本脚本利用了未公开的注册表值 `TestFlags` 来实现功能。
当该值按位包含 `0x20` 时，所有与 _Windows 预览体验_ 在线服务的连接都会被禁用。借此，我们可以自行配置 Windows 预览体验的相关设置，而不会被在线服务的同步覆盖。由于 `Windows 更新` 不会校验设备是否正式加入了该计划，因此只需在注册表中写入正确的数值，就能收到 _预览体验成员预览版_ 的更新推送。

## 许可证
本项目采用 MIT 许可证开源。详见 `LICENSE` 文件。
