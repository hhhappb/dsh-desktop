<h1 align="center">DSH Desktop</h1>

<p align="center">
  <strong>基于 DeepSeek Harness 构建的 Windows 和 macOS 开源桌面客户端。</strong><br>
  万物皆「插件」，桌面本身也是「插件」。
</p>

<p align="center"><sub>独立的社区开源项目，与深度求索不存在隶属、合作、授权或背书关系。<br>本仓库目前无深度求索员工或 DeepSeek Harness 上游官方团队成员参与；GitHub Contributors 中显示的上游贡献者来自 Fork 继承和同步的提交历史。<br>中文 · <a href="README.en.md">English</a></sub></p>

<p align="center">
  <img src="assets/desktop-hero-zh.png" alt="DSH Desktop：基于 DeepSeek Harness 构建的开源桌面客户端" width="100%">
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-2EA44F?style=flat" alt="MIT License"></a>
  <img src="https://img.shields.io/badge/macOS%20%7C%20Windows-4493F8?style=flat-square" alt="支持 macOS 和 Windows">
</p>

<p align="center">
  <img src="assets/desktop-preview.png" alt="DSH Desktop 界面预览" width="100%">
</p>

DSH Desktop 将 [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness) 的本地 Web UI、Host 服务和插件系统集成到原生桌面应用中。项目固定并原样运行特定上游版本；桌面仓库负责窗口、托盘、终端、工作配置和插件市场等桌面能力。

## 发布状态

`hhhappb/dsh-desktop` 尚未建立独立的安装包和自动更新渠道，因此当前不提供 Windows 或 macOS 二进制下载。请勿将其他维护者发布的安装包视为本 Fork 的构建产物。

从源码运行：

```sh
git submodule update --init --recursive
corepack yarn install --immutable
corepack yarn dev
```

独立 Release 发布完成后，本节将更新为本仓库自己的下载地址。

## 文档

普通用户可从[用户指南](docs/user-guide.md)和[常见问题](docs/faq.md)开始；开发者和维护者可使用以下入口。

| 目标 | 入口 |
| --- | --- |
| 查看全部文档 | [文档索引](docs/README.md) |
| 了解项目定位 | [为什么做 DSH Desktop](docs/why-desktop.md) |
| 开发普通或 Desktop 插件 | [插件开发](docs/plugin-development.md) |
| 了解桌面插件能力 | [桌面插件接口说明](dsh-plugin-desktop/docs/plugin-services.zh.md) |
| 查看插件市场设计 | [DSH Community Market](dsh-community-market/README.zh.md) |
| 了解应用架构 | [架构说明](docs/architecture.md) |
| 查看包级构建说明 | [dsh-plugin-desktop README](dsh-plugin-desktop/README.zh.md) |

## 主要功能

- **原生桌面壳**：启动并管理本地 Harness 服务，提供桌面窗口和系统托盘。
- **工作配置**：管理不同的 DSH 工作配置及其插件组合。
- **系统终端**：为打包后的 DSH 环境提供受控的本地终端入口。
- **插件市场**：提供插件发现、详情、安装和管理能力。
- **跨平台打包**：代码包含 Windows x64 和 macOS Universal 的构建路径。

## 插件架构

DSH Desktop 不直接修改固定的上游源码。`deepseek-harness/` 是只读的 Git 子模块；桌面能力位于仓库自有包中，并通过 DeepSeek Harness 的插件机制与上游组合。

桌面壳本身也是一个 DSH 插件。与固定上游版本兼容的插件可以按相同的组合机制使用，桌面能力也可以独立演进。

开发者可参考[插件开发指南](docs/plugin-development.md)和[桌面插件接口说明](dsh-plugin-desktop/docs/plugin-services.zh.md)。

## 与 DeepSeek Harness 的关系

DSH Desktop 是基于 DeepSeek Harness 和 Cordis 插件思想构建的独立社区项目。

上游 DeepSeek Harness 提供核心智能体能力、插件系统和 Web UI；本仓库主要负责：

- 桌面应用封装
- 本地服务启动、停止与恢复
- 桌面窗口和系统托盘集成
- 工作配置、终端和插件市场
- Windows 与 macOS 构建支持

GitHub Contributors 页面中可能出现的上游贡献者仅反映继承和同步的提交来源，不代表相关人员参与本仓库，也不构成隶属、合作、授权或背书关系。

## 致谢

感谢 [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness) 提供核心运行时和 Web UI，感谢 [Cordis](https://github.com/cordiverse/cordis) 提供插件化基础。

## 开发与验证

要求 Node.js `^22.19.0` 或 `>=24.0.0`，并通过 Corepack 使用仓库固定的 Yarn 版本。

```sh
git submodule update --init --recursive
corepack yarn install --immutable
corepack yarn build
corepack yarn typecheck
corepack yarn test
corepack yarn check
```

贡献说明见 [CONTRIBUTING.md](CONTRIBUTING.md)。

## License

本项目遵循 [MIT License](LICENSE)。

> “DeepSeek Harness”是深度求索公司的注册商标。本文仅为准确说明兼容性、技术来源及与上游软件的关系而使用该名称。

> DSH Desktop 是独立的社区项目，与深度求索不存在隶属、合作、授权或背书关系。
