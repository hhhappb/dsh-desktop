<h1 align="center">DSH Desktop</h1>

<p align="center">
  <strong>An open-source desktop client for Windows and macOS, built on DeepSeek Harness.</strong><br>
  Everything is a plugin — the desktop itself is a plugin.
</p>

<p align="center"><sub>An independent community project, not affiliated with, authorized by, or endorsed by DeepSeek.<br>No DeepSeek employee or official upstream DeepSeek Harness team member currently participates in this repository; upstream contributors shown by GitHub come from inherited and synchronized Fork history.<br><a href="README.md">中文</a> · English</sub></p>

<p align="center">
  <img src="assets/desktop-hero-en.png" alt="DSH Desktop, an open-source desktop client built on DeepSeek Harness" width="100%">
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-2EA44F?style=flat" alt="MIT License"></a>
  <img src="https://img.shields.io/badge/macOS%20%7C%20Windows-4493F8?style=flat-square" alt="Supports macOS and Windows">
</p>

<p align="center">
  <img src="assets/desktop-preview.png" alt="DSH Desktop preview" width="100%">
</p>

DSH Desktop integrates the local Web UI, Host service, and plugin system from [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness) into a native desktop application. It runs a pinned upstream version unchanged, while this desktop repository owns the window, tray, terminal, work profiles, plugin market, and other desktop capabilities.

## Release status

`hhhappb/dsh-desktop` does not yet have an independent installer or automatic-update channel, so it currently provides no Windows or macOS binary downloads. Do not treat installers published by another maintainer as builds from this Fork.

Run from source:

```sh
git submodule update --init --recursive
corepack yarn install --immutable
corepack yarn dev
```

This section will link to this repository's own downloads after an independent Release is available.

## Documentation

Users can start with the [user guide](docs/user-guide.en.md) and [FAQ](docs/faq.en.md). Developers and maintainers can use these entry points:

| Goal | Entry point |
| --- | --- |
| Browse all documentation | [Documentation index](docs/README.en.md) |
| Understand the product's role | [Why DSH Desktop](docs/why-desktop.en.md) |
| Build ordinary or Desktop plugins | [Plugin development](docs/plugin-development.en.md) |
| Review Desktop plugin capabilities | [Desktop plugin API](dsh-plugin-desktop/docs/plugin-services.md) |
| Review the plugin market design | [DSH Community Market](dsh-community-market/README.md) |
| Understand the application architecture | [Architecture](docs/architecture.en.md) |
| Read package-level build guidance | [dsh-plugin-desktop README](dsh-plugin-desktop/README.md) |

## Features

- **Native desktop shell**: starts and manages the local Harness service and provides the desktop window and system tray.
- **Work profiles**: manages separate DSH work profiles and their plugin compositions.
- **System terminal**: provides a controlled local terminal entry point for the packaged DSH environment.
- **Plugin market**: supports plugin discovery, details, installation, and management.
- **Cross-platform packaging**: includes build paths for Windows x64 and macOS Universal.

## Plugin architecture

DSH Desktop does not directly modify the pinned upstream source. `deepseek-harness/` is a read-only Git submodule; desktop capabilities live in repository-owned packages and compose with upstream through the DeepSeek Harness plugin mechanism.

The desktop shell is itself a DSH plugin. Plugins compatible with the pinned upstream version use the same composition mechanism, while desktop capabilities can evolve independently.

Developers can refer to [Plugin development](docs/plugin-development.en.md) and the [Desktop plugin API](dsh-plugin-desktop/docs/plugin-services.md).

## Relationship to DeepSeek Harness

DSH Desktop is an independent community project built on DeepSeek Harness and the Cordis plugin model.

Upstream DeepSeek Harness provides the core agent capabilities, plugin system, and Web UI. This repository primarily provides:

- Desktop application packaging
- Local service startup, shutdown, and recovery
- Desktop window and system tray integration
- Work profiles, terminal, and plugin market
- Windows and macOS build support

Upstream contributors may appear on GitHub's Contributors page only because their commits were inherited or synchronized. This does not imply participation in this repository or any affiliation, partnership, authorization, or endorsement.

## Acknowledgements

Thanks to [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness) for the core runtime and Web UI, and to [Cordis](https://github.com/cordiverse/cordis) for the plugin foundation.

## Development and verification

Use Node.js `^22.19.0` or `>=24.0.0`, with the repository-pinned Yarn release through Corepack.

```sh
git submodule update --init --recursive
corepack yarn install --immutable
corepack yarn build
corepack yarn typecheck
corepack yarn test
corepack yarn check
```

See [CONTRIBUTING.en.md](CONTRIBUTING.en.md) for contribution guidance.

## License

This project is licensed under the [MIT License](LICENSE).

> “DeepSeek Harness” is a registered trademark of DeepSeek AI. The name is used solely to accurately describe compatibility, technical origin, and this project's relationship to upstream software.

> DSH Desktop is an independent community project and is not affiliated with, sponsored by, authorized by, or endorsed by DeepSeek.
