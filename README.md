# Awesome GPUI [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of GPUI resources, libraries, tutorials, tools, and applications

English | [中文](README_CN.md)

[GPUI](https://www.gpui.rs/) is a hybrid immediate- and retained-mode, GPU-accelerated UI framework for Rust developed by the creators of [Zed](https://zed.dev/).

## Contents

- [Version and source notes](#version-and-source-notes)
- [Official resources](#official-resources)
- [Development tools](#development-tools)
- [Frameworks and component libraries](#frameworks-and-component-libraries)
- [Application infrastructure and platforms](#application-infrastructure-and-platforms)
- [Tutorials](#tutorials)
- [Dependency examples](#dependency-examples)
- [Applications](#applications)
- [Blog posts](#blog-posts)
- [Videos](#videos)
- [Community](#community)

## Version and source notes

Dependency baselines below were checked against each project's default-branch `Cargo.toml`, lockfile, or package manifest on **2026-10-19**.

GPUI is pre-1.0 and its Rust types are source-specific. The official `gpui` crate and alternative families such as `gpui-pre`, `gpui-fast`, `bezel-gpui`, `adabraka-gpui`, and `gpui-ce` are not interchangeable even when their APIs look similar. Keep one GPUI core family in an application's dependency graph, and pin Git dependencies to a commit when reproducibility matters.

## Official resources

| Resource | Description | Version / GPUI source |
| --- | --- | --- |
| [GPUI](https://github.com/zed-industries/zed/tree/main/crates/gpui) | The official framework source inside the Zed repository. | crates.io [`0.2.2`](https://crates.io/crates/gpui/0.2.2); Zed `main` still declares `0.2.2` but contains substantial unreleased and breaking changes. |
| [Official website](https://www.gpui.rs/) | GPUI's official website and introductory documentation. | Documents official GPUI; some examples lag behind current Zed `main`. |
| [embedded_gpui](https://github.com/zed-industries/embedded_gpui) | Official experimental host for sandboxed `wasm32-wasip2` GPUI components, with typed capabilities and an optional QuickJS layer. | No release; workspace `0.1.0`. Uses Zed branch `gpui-embedded-in-gpui`, resolved to [`7bc1c05`](https://github.com/zed-industries/zed/commit/7bc1c05d8b30db2b5bd1855847ba5e3b5899863a). |

## Development tools

| Project | Description | Version / GPUI source |
| --- | --- | --- |
| [create-gpui-app](https://github.com/zed-industries/create-gpui-app) | Official CLI that scaffolds a GPUI application. | CLI `0.1.5`; generated projects use an **unpinned** official Zed Git dependency. Last repository update: 2025-04-13. |
| [gpui-devtools](https://github.com/joris-gallot/gpui-devtools) | Runtime element picker, box-model inspector, computed styles, and temporary style editing. | [`0.5.1`](https://github.com/joris-gallot/gpui-devtools/releases/tag/v0.5.1); `gpui-pre 0.3.6` with the `inspector` feature. |
| [GPUI Storybook](https://github.com/stayhydated/gpui-storybook) | Component gallery, typed controls, scenarios, visual baselines, frame budgets, and MCP-driven live sessions. | [`0.7.1`](https://github.com/stayhydated/gpui-storybook/releases/tag/gpui-storybook-v0.7.1); pins `gpui-pre 0.3.9` and GPUI Kit `0.7.3`. Requires Rust 1.99. |
| [GPUI Kit Canvas](https://github.com/JetSquirrel/gpui-kit-canvas) | Browser-based drag-and-drop designer that exports implementation prompts for GPUI Kit. | Private npm package `0.1.0`; **no GPUI runtime dependency**. Targets GPUI Kit's component API and validates names against a local Kit checkout. |

Install the scaffold CLI with:

```bash
cargo install create-gpui-app
create-gpui-app --name my-app
```

## Frameworks and component libraries

| Project | Description | Version / GPUI source |
| --- | --- | --- |
| [GPUI Kit](https://github.com/longbridge/gpui-kit) | Longbridge's layered application framework: `gpui-base`, 75+ styled `gpui-component` components, the `gpui-kit` facade, and the experimental `gpui-shell`. Formerly published from `longbridge/gpui-component`. | [`0.7.3`](https://github.com/longbridge/gpui-kit/releases/tag/v0.7.3); pins the `gpui-pre` family to `0.3.9`. Optional `fast` feature uses `gpui-fast 0.1.7`. |
| [gpui-fast](https://github.com/longbridge/gpui-fast) | Experimental Longbridge GPUI fork/extraction with retained rendering, scroll-layer GPU tile caching, and native window composition. | [`0.1.9`](https://github.com/longbridge/gpui-fast/releases/tag/v0.1.9); its own `gpui-fast-*` type universe. GPUI Kit `0.7.3` currently selects `0.1.7`, not `0.1.9`. |
| [gpui-toolkit](https://github.com/pierreaubert/gpui-toolkit) | Cross-platform UI and visualization toolkit spanning desktop, mobile, WASM, Python scene wrappers, charts, and 3D primitives. | Latest release [`0.10.33`](https://github.com/pierreaubert/gpui-toolkit/releases/tag/v0.10.33); current `main` manifests are mostly `0.10.44`. Uses the vendored `sotf-gpui-toolkit-gpui 0.2.3` fork family. |
| [Bezel](https://github.com/crabtalk/bezel) | Fast-moving, SwiftUI-lean component framework with editors, terminal, charts, WebView, canvas, and environment-driven styling. | Latest release `0.2.12`; current `main` is `0.2.17` and uses its own `bezel-gpui 0.3.19` fork family. |
| [adabraka-ui](https://github.com/Augani/adabraka-ui) | shadcn-inspired desktop component library with 80+ components. The upstream ecosystem currently marks it dormant. | `adabraka-ui 0.3.9`; depends on the `adabraka-gpui 0.5` fork (lockfile resolves `0.5.1`). |
| [GPUIX](https://github.com/remorses/gpuix) | React and Solid renderers for GPUI through Node-API, without Electron or a WebView. | `@gpuix/react`, `@gpuix/solid`, and native package `0.10.0`; uses the `remorses/zed` `gpuix` submodule at [`2565b8a`](https://github.com/remorses/zed/commit/2565b8a3e33537c3d3f56d0d45f11e50a17e512d). Adapter and native package versions must match. |

## Application infrastructure and platforms

| Project | Description | Version / GPUI source |
| --- | --- | --- |
| [gpui-router](https://github.com/justjavac/gpui-router) | Nested, dynamic, wildcard, and per-window routing inspired by React Router. | [`0.7.0`](https://github.com/justjavac/gpui-router/releases/tag/v0.7.0); defaults to official `gpui 0.2.1`, or optionally `gpui-pre 0.3.6`. Select exactly one backend. |
| [gpui-mobile](https://github.com/itsbalamurali/gpui-mobile) | Experimental iOS and Android implementation of `gpui::Platform`. | No release; crate `0.1.0`. Pins official Zed GPUI to [`5688167`](https://github.com/zed-industries/zed/commit/5688167d224b5eca54875d49afb8bfd73a07915a). AGPL-3.0 licensed. |

## Tutorials

- [gpui-tutorial](https://github.com/hedge-ops/gpui-tutorial) - Hands-on walkthrough covering GPUI basics and how to build your first app
- [GPUI Book](https://github.com/MatinAniss/gpui-book) - A book teaching the concepts needed to create a GPUI application
- [GPUI Rendering Docs](https://matinaniss.github.io/gpui-book/rendering/render.html) - Detailed explanation of GPUI's rendering system

## Dependency examples

Use the published official snapshot when you want a registry dependency:

```toml
[dependencies]
gpui = "0.2.2"
```

Use GPUI Kit as a separate dependency family:

```toml
[dependencies]
gpui-kit = "0.7.3"
```

For unreleased official `main` features, pin every official GPUI crate to the same Zed commit rather than following a floating branch:

```toml
[dependencies]
gpui = { git = "https://github.com/zed-industries/zed", rev = "56934ec0560bce8929025497411de7f5322fb6ca" }
gpui_platform = { git = "https://github.com/zed-industries/zed", rev = "56934ec0560bce8929025497411de7f5322fb6ca" }
```

Do not combine these examples in one application unless a facade explicitly selects the backend for you.

## Applications

| Application | Description | GPUI version / source |
| --- | --- | --- |
| [Glim](https://github.com/NeoPanic/Glim) | Free, open-source macOS file viewer for Markdown, PDFs, images, JSON, CSV, and source code. | GPUI Kit `0.7.1`, patched to a vendored `gpui-pre 0.3.8` snapshot of Zed [`279fe07`](https://github.com/zed-industries/zed/commit/279fe070bb389b79652e52065b2f001edcc0b11b). |
| [Zed](https://github.com/zed-industries/zed) | High-performance collaborative code editor and GPUI's reference application. | Official in-tree GPUI at the same Zed commit; package manifest `0.2.2`, with unreleased `main` APIs. |
| [Waku](https://github.com/egoist/waku) | Native desktop workspace for local coding agents. | `egoist/zed` fork, branch `waku-webview`; lockfile commit [`f9bad89`](https://github.com/egoist/zed/commit/f9bad8941ea813982d6dfb10c0377ebf7716b3e7), carrying layered-scene support for WKWebView overlays. |
| [Loungy](https://github.com/MatthiasGrandl/Loungy) | Application launcher. | Unpinned official Zed Git dependency; lockfile resolves [`894866d`](https://github.com/zed-industries/zed/commit/894866da9478003e77458e7a849353312d4c282c). |
| [Helix GPUI](https://github.com/polachok/helix-gpui) | Experimental Helix editor implementation. | Unpinned official Zed Git dependency; lockfile resolves [`0d26beb`](https://github.com/zed-industries/zed/commit/0d26beb91ba751e24ed7c109ab71ff8dfac0d137). |
| [GPUI Calculator](https://github.com/kriskw1999/gpui-calculator) | Calculator application. | Unpinned official Zed Git dependency; lockfile resolves [`5e1aa89`](https://github.com/zed-industries/zed/commit/5e1aa898d4acdf82238bdd477299eb48029a0923). |
| [GPUI Counter](https://github.com/derrickpersson/gpui-simple-counter) | Minimal counter example. | Unpinned official Zed Git dependency; lockfile resolves [`f4f72a1`](https://github.com/zed-industries/zed/commit/f4f72a11360ec2c8e99968988c7c802ec1eddb35). |
| [GPUI Memory Game](https://github.com/justjavac/gpui-memory-game) | Memory-matching game. | Official crates.io `gpui 0.2.1`. |
| [Hummingbird](https://github.com/hummingbird-player/hummingbird) | Lightweight music player supporting FLAC, MP3, OGG, and WAV. | `gpui-unofficial 1`, patched to Hummingbird's `gpui-unofficial-shim`; not the official Zed crate. |
| [PGUI](https://github.com/duanebester/pgui) | PostgreSQL database query and management application. | Official crates.io `gpui 0.2` plus `gpui-component 0.5`. |
| [Vleer](https://github.com/vleerapp/vleer) | Music player that connects local, self-hosted, and cloud sources. | `gpui-ce` / `gpui_ce_platform` fork at revision [`d9623fc`](https://github.com/gpui-ce/gpui-ce/commit/d9623fc2b6678a4d466f9fe2e9d5f69a4ad58de4). |
| [PoE2 Oracle](https://github.com/mttzzz/poe2-oracle) | Free price checker and XP overlay for Path of Exile 2 on Windows. | Official Zed Git `gpui` and `gpui_platform`, both pinned to [`b54cc1d`](https://github.com/zed-industries/zed/commit/b54cc1d0acc8fe3f7581721ee1195516e7581f9d); package manifest `0.2.2`. |
| [SQLly](https://sqlly.app/) | Cross-platform SQL client with IntelliSense and schema intelligence for PostgreSQL, MySQL, MariaDB, SQL Server, SQLite, DuckDB, Redis and more. | Published crates.io [`gpui-pre 0.3.9`](https://crates.io/crates/gpui-pre/0.3.9) plus `gpui-component 0.7`; closed source. |

## Blog posts

- [Ownership and Data Flow in GPUI](https://zed.dev/blog/gpui-ownership) - How GPUI ownership, models, and event emission and consumption work
- [Why the big rewrite?](https://zed.dev/blog/why-the-big-rewrite) - Why GPUI moved to its Tailwind-inspired API
- [Unofficial Documentation](https://github.com/Himasnhu-AT/GPUI-docs-unofficial) - Community-maintained unofficial GPUI documentation

## Videos

- [Second look at the Rust GPUI framework from Zed! Featuring web-sockets](https://www.youtube.com/watch?v=WQt4ur7fcd0) - A GPUI exploration featuring WebSocket functionality

## Community

- [Zed Discussions](https://github.com/zed-industries/zed/discussions) - GitHub discussions about GPUI and Zed
- [Reddit Discussion](https://www.reddit.com/r/rust/comments/11hu1sc/gpui_ui_framework_from_the_makers_of_zed/) - Reddit discussion about GPUI

## Contributing

Contributions are welcome! Please read the [contribution guidelines](CONTRIBUTING_EN.md) to get started.

## License

[![CC0](https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0)

To the extent possible under law, the compiler of this work has waived all copyright and related or neighboring rights to this work.
