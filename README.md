# Awesome GPUI [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of GPUI resources, libraries, tutorials and tools

English | [中文](README_CN.md)

[GPUI](https://www.gpui.rs/) is a hybrid immediate- and retained-mode, GPU-accelerated UI framework for Rust developed by the creators of [Zed](https://zed.dev/).

## Contents

- [Official Resources](#official-resources)
- [Development Tools](#development-tools)
- [Component Libraries](#component-libraries)
- [Tutorials](#tutorials)
- [Examples](#examples)
- [Projects](#projects)
- [Blog Posts](#blog-posts)
- [Videos](#videos)
- [Community](#community)

## Official Resources

- [GPUI](https://github.com/zed-industries/zed/tree/main/crates/gpui) - The core repository of the GPUI framework, located within the Zed repository
- [Official Website](https://www.gpui.rs/) - The official website of GPUI

## Development Tools

- [create-gpui-app](https://github.com/brscrt/create-gpui-app) - Scaffold a new GPUI application with one command
  ```bash
  cargo install create-gpui-app
  create-gpui-app --name my-app
  ```

## Component Libraries

- [gpui-component](https://github.com/longbridge/gpui-component) - A growing library of UI components (Accordion, Button, DatePicker, Calendar, Modal, Table, etc.) for building desktop apps with GPUI

## Tutorials

- [gpui-tutorial](https://github.com/hedge-ops/gpui-tutorial) - Hands-on walkthrough covering GPUI basics and how to build your first app
- [GPUI Book](https://github.com/MatinAniss/gpui-book) - A book teaching you the concepts you need to create your own GPUI application
- [GPUI Rendering Docs](https://matinaniss.github.io/gpui-book/rendering/render.html) - Detailed explanation of the GPUI rendering system

## Examples

Add dependencies directly from Git while the ecosystem matures:

```toml
[dependencies]
gpui = { git = "https://github.com/zed-industries/zed", branch = "main" }
gpui-component = { git = "https://github.com/longbridge/gpui-component.git" }
```

Rust code example:

```rust
use gpui::prelude::*;
use gpui_component::DatePicker;

fn main() {
    // Initialize GPUI app and open a window...
    DatePicker::new()
        .locale("en-US")
        .on_select(|date| println!("Selected: {:?}", date));
}
```

## Projects

- [zed](https://github.com/zed-industries/zed) - A high-performance, multiplayer code editor built with GPUI
- [Loungy](https://github.com/MatthiasGrandl/Loungy) - An application launcher built with GPUI
- [Helix GPUI](https://github.com/polachok/helix-gpui) - Helix editor implementation using GPUI
- [GPUI Calculator](https://github.com/kriskw1999/gpui-calculator) - A calculator app built with GPUI
- [GPUI Counter](https://github.com/derrickpersson/gpui-simple-counter) - A simple GPUI counter example
- [GPUI Memory Game](https://github.com/justjavac/gpui-memory-game) - A memory matching game built with Rust and GPUI
- [Hummingbird](https://github.com/143mailliw/hummingbird) - A modern music player written in Rust using GPUI, designed to be performant and lightweight with FLAC, MP3, OGG and WAV playback support
- [PGUI](https://github.com/duanebester/pgui) - A GUI app to query and manage Postgres databases built with GPUI

## Blog Posts

- [Ownership and Data Flow in GPUI](https://zed.dev/blog/gpui-ownership) - In-depth description of how ownership works in GPUI using models, including how to emit and consume events
- [Why the big rewrite?](https://zed.dev/blog/why-th·e-big-rewrite) - Blog post on the reasons for going to the tailwind-inspired API
- [Unofficial Documentation](https://github.com/Himasnhu-AT/GPUI-docs-unofficial) - An attempt at unofficial documentation for GPUI

## Videos

- [Second look at the Rust GPUI framework from Zed! Featuring web-sockets](https://www.youtube.com/watch?v=WQt4ur7fcd0) - A second exploration of the Rust GPUI framework from Zed, featuring WebSocket functionality demonstration

## Community

- [Zed Discussions](https://github.com/zed-industries/zed/discussions) - GitHub discussions about GPUI and Zed
- [Reddit Discussion](https://www.reddit.com/r/rust/comments/11hu1sc/gpui_ui_framework_from_the_makers_of_zed/) - Reddit discussion about GPUI

## Contributing

Contributions are welcome! Please read the [contribution guidelines](CONTRIBUTING_EN.md) to get started.

## License

[![CC0](https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0)

To the extent possible under law, the compiler of this work has waived all copyright and related or neighboring rights to this work.
