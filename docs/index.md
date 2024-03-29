# GMLIB
### QQ交流群: 931689535
[![Latest Tag](https://img.shields.io/github/v/tag/GroupMountain/GMLIB?label=LATEST%20TAG&style=for-the-badge)
![GitHub Releases (by Asset)](https://img.shields.io/github/downloads/GroupMountain/GMLIB/latest/total?style=for-the-badge)
](https://github.com/GroupMountain/GMLIB/releases/latest)  


`GMLIB` 是一个基于 `LeviLamina` 加载器的第三方插件前置库。为基岩版专用服务器 —— `Bedrock Dedicated Server`（以下简称**
BDS**）的插件开发者提供更多的API，一定程度上弥补了 `LeviLamina` 的API缺口。

`GMLIB` 封装了大量 `LeviLamina` 未直接提供的API，为插件开发者提供了更多便利。
插件开发者可以直接调用 `GMLIB` 中的现成API，而非重复造轮子。

`GMLIB` 的API支持使用头文件和静态链接库导入，我们提供了模板插件和GMLIB的SDK。
对于调用 `GMLIB_API` 的代码来说，如果GMLIB没有API改动，仅需本项目在底层适配更新即可，给插件开发与维护带来了很大的便利。

`GMLIB` 的全部内容均为开源的。

## 💻下载

你可以到[Releases页面](https://github.com/GroupMountain/GMLIB/releases) 来下载最新的版本。

## 📕 编写插件和使用API

请参考开发指南

## 🔨 构建项目

> 前往 [`GitHub Actions`](https://github.com/GroupMountain/GMLIB/actions) 来获取最新的构建工件(artifact)
>
> 当然，如果您愿意自己构建项目，或者向 `GMLIB` 贡献代码，您可以按照以下说明自行构建项目

1. 克隆仓库到本地，并使用你熟悉的 IDE 打开项目目录，对 xmake 项目进行编译生成。
2. 正常构建该项目即可。

## 🎬 参与贡献

您可以使用以下方法为 `GMLIB` 项目做出贡献

1. 贡献代码，封装新的API
2. 帮助我们修改并优化开发文档、使用文档
3. 在 [`GitHub Issues`](https://github.com/GroupMountain/GMLIB/issues) 中反馈使用过程中遇到的问题，或者提出好的建议
4. 帮助我们推广 `GMLIB`，支持我们的发展

⭐⭐⭐我们欢迎您的贡献！⭐⭐⭐

## 📍 许可证
- **开发者不对您负责，开发者没有义务为你编写代码、为你使用造成的任何后果负责**
1. 本前置插件全部代码采用 `LGPL 3.0` 开源协议。
2. 您可以使用任何开源许可证编写基于 `GMLIB` 作为前置的插件，甚至不发布您的源代码。
3. 如果你修改了 `GMLIB` 的源代码，或者基于这个 `GMLIB` 编写了一个新的前置，你必须开源它。
4. 如果你想要分发，转载本前置，你必须得到我们的授权！

## 🏆 致谢
- 感谢 `LeviLamina` 的开源代码和底层API，极大的简化了前置插件开发难度。
- 感谢 `GroupMountain` 开发成员对项目的巨大贡献

## 💎 重要贡献者
- [@Tsubasa6848](https://github.com/Tsubasa6848)
- [@EpsilonZunsat](https://github.com/EpsilonZunsat)
- [@killcerr](https://github.com/killcerr)
- [@lostDeers](https://github.com/lostDeers)