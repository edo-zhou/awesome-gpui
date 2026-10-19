# Awesome GPUI [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> 精选的 GPUI 资源、库、教程、工具和应用列表

[English](README.md) | 中文

[GPUI](https://www.gpui.rs/) 是由 [Zed](https://zed.dev/) 创建者开发的一款混合即时模式与保留模式、GPU 加速的 Rust UI 框架。

## 目录

- [版本与来源说明](#版本与来源说明)
- [官方资源](#官方资源)
- [开发工具](#开发工具)
- [框架与组件库](#框架与组件库)
- [应用基础设施与平台](#应用基础设施与平台)
- [教程](#教程)
- [依赖示例](#依赖示例)
- [应用项目](#应用项目)
- [博客文章](#博客文章)
- [视频](#视频)
- [社区](#社区)

## 版本与来源说明

下表的依赖基线已于 **2026-10-19** 按各项目默认分支的 `Cargo.toml`、锁文件或 package manifest 核对。

GPUI 仍处于 1.0 之前，Rust 类型与源码来源绑定。Zed 官方 `gpui` 与 `gpui-pre`、`gpui-fast`、`bezel-gpui`、`adabraka-gpui`、`gpui-ce` 等替代家族即使 API 相似，也不能直接混用。一个应用的依赖图应只保留一套 GPUI 核心；需要可复现构建时，应把 Git 依赖固定到 commit。

## 官方资源

| 资源 | 说明 | 版本 / GPUI 来源 |
| --- | --- | --- |
| [GPUI](https://github.com/zed-industries/zed/tree/main/crates/gpui) | 位于 Zed 仓库中的官方框架源码。 | crates.io 最新为 [`0.2.2`](https://crates.io/crates/gpui/0.2.2)；Zed `main` 的 manifest 仍写 `0.2.2`，但已经包含大量未发布且有破坏性的变化。 |
| [官方网站](https://www.gpui.rs/) | GPUI 官方网站和入门文档。 | 对应官方 GPUI；部分示例落后于当前 Zed `main`。 |
| [embedded_gpui](https://github.com/zed-industries/embedded_gpui) | 官方实验项目：在原生 GPUI host 中运行受限的 `wasm32-wasip2` GPUI 组件，带类型化 capability 和可选 QuickJS 层。 | 无 Release；workspace `0.1.0`。使用 Zed `gpui-embedded-in-gpui` 分支，锁文件解析为 [`7bc1c05`](https://github.com/zed-industries/zed/commit/7bc1c05d8b30db2b5bd1855847ba5e3b5899863a)。 |

## 开发工具

| 项目 | 说明 | 版本 / GPUI 来源 |
| --- | --- | --- |
| [create-gpui-app](https://github.com/zed-industries/create-gpui-app) | Zed 官方 GPUI 应用脚手架 CLI。 | CLI `0.1.5`；生成项目使用**未固定 commit** 的官方 Zed Git 依赖。仓库最后更新于 2025-04-13。 |
| [gpui-devtools](https://github.com/joris-gallot/gpui-devtools) | 运行时元素选择、盒模型、计算样式与临时样式编辑工具。 | [`0.5.1`](https://github.com/joris-gallot/gpui-devtools/releases/tag/v0.5.1)；使用 `gpui-pre 0.3.6` 和 `inspector` feature。 |
| [GPUI Storybook](https://github.com/stayhydated/gpui-storybook) | 组件画廊、类型化 controls、场景、视觉基线、帧预算和 MCP live session。 | [`0.7.1`](https://github.com/stayhydated/gpui-storybook/releases/tag/gpui-storybook-v0.7.1)；固定 `gpui-pre 0.3.9` 与 GPUI Kit `0.7.3`。要求 Rust 1.99。 |
| [GPUI Kit Canvas](https://github.com/JetSquirrel/gpui-kit-canvas) | 在浏览器中拖放设计 GPUI Kit 窗口，并导出给编程 Agent 使用的实现提示。 | 私有 npm package `0.1.0`；**没有 GPUI 运行时依赖**。它面向 GPUI Kit 组件 API，并用本地 Kit checkout 校验组件名。 |

安装脚手架 CLI：

```bash
cargo install create-gpui-app
create-gpui-app --name my-app
```

## 框架与组件库

| 项目 | 说明 | 版本 / GPUI 来源 |
| --- | --- | --- |
| [GPUI Kit](https://github.com/longbridge/gpui-kit) | Longbridge 的分层应用框架：无样式的 `gpui-base`、75+ 个 `gpui-component` 组件、`gpui-kit` facade，以及实验性的 `gpui-shell`。原仓库名为 `longbridge/gpui-component`。 | [`0.7.3`](https://github.com/longbridge/gpui-kit/releases/tag/v0.7.3)；把 `gpui-pre` 家族固定为 `0.3.9`。可选 `fast` feature 使用 `gpui-fast 0.1.7`。 |
| [gpui-fast](https://github.com/longbridge/gpui-fast) | Longbridge 实验性 GPUI fork/拆分版，加入 retained rendering、滚动层 GPU tile 缓存和原生窗口合成。 | [`0.1.9`](https://github.com/longbridge/gpui-fast/releases/tag/v0.1.9)；使用独立的 `gpui-fast-*` 类型体系。GPUI Kit `0.7.3` 当前选择的是 `0.1.7`，不是 `0.1.9`。 |
| [gpui-toolkit](https://github.com/pierreaubert/gpui-toolkit) | 覆盖桌面、移动端、WASM、Python scene wrapper、图表和 3D primitive 的跨平台 UI/可视化工具箱。 | 最新 Release [`0.10.33`](https://github.com/pierreaubert/gpui-toolkit/releases/tag/v0.10.33)；当前 `main` 的多数 manifest 为 `0.10.44`。使用 vendored 的 `sotf-gpui-toolkit-gpui 0.2.3` fork 家族。 |
| [Bezel](https://github.com/crabtalk/bezel) | 快速演进、偏 SwiftUI 风格的组件框架，包含编辑器、终端、图表、WebView、canvas 和环境样式。 | 最新 Release `0.2.12`；当前 `main` 为 `0.2.17`，使用自己的 `bezel-gpui 0.3.19` fork 家族。 |
| [adabraka-ui](https://github.com/Augani/adabraka-ui) | 受 shadcn 启发、包含 80+ 个组件的桌面组件库；上游生态目前将其标为 dormant。 | `adabraka-ui 0.3.9`；依赖 `adabraka-gpui 0.5` fork，锁文件解析为 `0.5.1`。 |
| [GPUIX](https://github.com/remorses/gpuix) | 通过 Node-API 把 React 和 Solid renderer 接到 GPUI，不依赖 Electron 或 WebView。 | `@gpuix/react`、`@gpuix/solid` 与 native package 均为 `0.10.0`；使用 `remorses/zed` 的 `gpuix` 子模块提交 [`2565b8a`](https://github.com/remorses/zed/commit/2565b8a3e33537c3d3f56d0d45f11e50a17e512d)。Adapter 与 native package 必须同版本。 |

## 应用基础设施与平台

| 项目 | 说明 | 版本 / GPUI 来源 |
| --- | --- | --- |
| [gpui-router](https://github.com/justjavac/gpui-router) | 参考 React Router 的嵌套、动态、通配符及每窗口独立路由。 | [`0.7.0`](https://github.com/justjavac/gpui-router/releases/tag/v0.7.0)；默认使用官方 `gpui 0.2.1`，也可选择 `gpui-pre 0.3.6`。两种后端只能选一个。 |
| [gpui-mobile](https://github.com/itsbalamurali/gpui-mobile) | 实验性的 iOS 与 Android `gpui::Platform` 实现。 | 无 Release；crate `0.1.0`。把官方 Zed GPUI 固定为 [`5688167`](https://github.com/zed-industries/zed/commit/5688167d224b5eca54875d49afb8bfd73a07915a)。许可证为 AGPL-3.0。 |

## 教程

- [gpui-tutorial](https://github.com/hedge-ops/gpui-tutorial) - 涵盖 GPUI 基础知识和如何构建第一个应用的实践教程
- [GPUI Book](https://github.com/MatinAniss/gpui-book) - 介绍创建 GPUI 应用所需概念的电子书
- [GPUI Rendering Docs](https://matinaniss.github.io/gpui-book/rendering/render.html) - GPUI 渲染系统的详细说明

## 依赖示例

需要 crates.io 依赖时，使用已发布的官方快照：

```toml
[dependencies]
gpui = "0.2.2"
```

GPUI Kit 是另一套独立依赖家族：

```toml
[dependencies]
gpui-kit = "0.7.3"
```

如需官方 `main` 尚未发布的功能，请把所有官方 GPUI crate 固定到同一个 Zed commit，不要跟随浮动分支：

```toml
[dependencies]
gpui = { git = "https://github.com/zed-industries/zed", rev = "56934ec0560bce8929025497411de7f5322fb6ca" }
gpui_platform = { git = "https://github.com/zed-industries/zed", rev = "56934ec0560bce8929025497411de7f5322fb6ca" }
```

除非 facade 明确替你选择后端，否则不要把以上依赖示例混在同一个应用中。

## 应用项目

| 应用 | 说明 | GPUI 版本 / 来源 |
| --- | --- | --- |
| [Glim](https://github.com/NeoPanic/Glim) | 可查看 Markdown、PDF、图片、JSON、CSV 和源代码的免费开源 macOS 文件查看器。 | GPUI Kit `0.7.1`，并 patch 到 vendored 的 `gpui-pre 0.3.8`；该快照来自 Zed [`279fe07`](https://github.com/zed-industries/zed/commit/279fe070bb389b79652e52065b2f001edcc0b11b)。 |
| [Zed](https://github.com/zed-industries/zed) | 高性能协作代码编辑器，也是 GPUI 的参考应用。 | 使用同一 Zed 提交内的官方 in-tree GPUI；package manifest 为 `0.2.2`，但 `main` 含未发布 API。 |
| [Waku](https://github.com/egoist/waku) | 面向本地编码智能体的原生桌面工作区。 | `egoist/zed` fork 的 `waku-webview` 分支；锁文件提交 [`f9bad89`](https://github.com/egoist/zed/commit/f9bad8941ea813982d6dfb10c0377ebf7716b3e7)，包含 WKWebView overlay 所需的 layered-scene 支持。 |
| [Loungy](https://github.com/MatthiasGrandl/Loungy) | 应用启动器。 | manifest 使用未固定 commit 的官方 Zed Git 依赖；锁文件解析为 [`894866d`](https://github.com/zed-industries/zed/commit/894866da9478003e77458e7a849353312d4c282c)。 |
| [Helix GPUI](https://github.com/polachok/helix-gpui) | 实验性的 Helix 编辑器 GPUI 实现。 | manifest 使用未固定 commit 的官方 Zed Git 依赖；锁文件解析为 [`0d26beb`](https://github.com/zed-industries/zed/commit/0d26beb91ba751e24ed7c109ab71ff8dfac0d137)。 |
| [GPUI Calculator](https://github.com/kriskw1999/gpui-calculator) | GPUI 计算器应用。 | manifest 使用未固定 commit 的官方 Zed Git 依赖；锁文件解析为 [`5e1aa89`](https://github.com/zed-industries/zed/commit/5e1aa898d4acdf82238bdd477299eb48029a0923)。 |
| [GPUI Counter](https://github.com/derrickpersson/gpui-simple-counter) | 最小计数器示例。 | manifest 使用未固定 commit 的官方 Zed Git 依赖；锁文件解析为 [`f4f72a1`](https://github.com/zed-industries/zed/commit/f4f72a11360ec2c8e99968988c7c802ec1eddb35)。 |
| [GPUI Memory Game](https://github.com/justjavac/gpui-memory-game) | 记忆配对游戏。 | 官方 crates.io `gpui 0.2.1`。 |
| [Hummingbird](https://github.com/hummingbird-player/hummingbird) | 支持 FLAC、MP3、OGG 和 WAV 的轻量音乐播放器。 | `gpui-unofficial 1`，并 patch 到 Hummingbird 自己的 `gpui-unofficial-shim`；不是 Zed 官方 crate。 |
| [PGUI](https://github.com/duanebester/pgui) | PostgreSQL 查询和管理应用。 | 官方 crates.io `gpui 0.2`，另用 `gpui-component 0.5`。 |
| [Vleer](https://github.com/vleerapp/vleer) | 聚合本地、自托管与云端来源的音乐播放器。 | `gpui-ce` / `gpui_ce_platform` fork，固定到 [`d9623fc`](https://github.com/gpui-ce/gpui-ce/commit/d9623fc2b6678a4d466f9fe2e9d5f69a4ad58de4)。 |
| [PoE2 Oracle](https://github.com/mttzzz/poe2-oracle) | Windows 平台的免费《流放之路 2》价格查询与经验值 overlay。 | 官方 Zed Git `gpui` 与 `gpui_platform` 均固定到 [`b54cc1d`](https://github.com/zed-industries/zed/commit/b54cc1d0acc8fe3f7581721ee1195516e7581f9d)，package manifest 为 `0.2.2`。 |

## 博客文章

- [Ownership and Data Flow in GPUI](https://zed.dev/blog/gpui-ownership) - 介绍 GPUI 的所有权、模型和事件收发
- [Why the big rewrite?](https://zed.dev/blog/why-the-big-rewrite) - 介绍 GPUI 转向类 Tailwind API 的原因
- [非官方文档](https://github.com/Himasnhu-AT/GPUI-docs-unofficial) - 社区维护的 GPUI 非官方文档

## 视频

- [Second look at the Rust GPUI framework from Zed! Featuring web-sockets](https://www.youtube.com/watch?v=WQt4ur7fcd0) - 包含 WebSocket 功能演示的 GPUI 探索视频

## 社区

- [Zed Discussions](https://github.com/zed-industries/zed/discussions) - GPUI 与 Zed 的 GitHub 讨论区
- [Reddit Discussion](https://www.reddit.com/r/rust/comments/11hu1sc/gpui_ui_framework_from_the_makers_of_zed/) - Reddit 上的 GPUI 讨论

## 贡献

欢迎贡献！请阅读[贡献指南](CONTRIBUTING.md)了解如何开始。

## 许可证

[![CC0](https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0)

在法律允许的范围内，本作品的编译者已放弃对此作品的所有版权及相关或邻接权利。
