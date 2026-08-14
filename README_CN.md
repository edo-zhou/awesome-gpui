# Awesome GPUI [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> 精选的GPUI资源、库、教程和工具列表

[English](README_EN.md) | 中文

[GPUI](https://www.gpui.rs/) 是由 [Zed](https://zed.dev/) 创建者开发的一款混合即时模式和保留模式、GPU加速的Rust UI框架。

## 目录

- [官方资源](#官方资源)
- [开发工具](#开发工具)
- [组件库](#组件库)
- [教程](#教程)
- [示例](#示例)
- [项目案例](#项目案例)
- [博客文章](#博客文章)
- [视频](#视频)
- [社区](#社区)

## 官方资源

- [GPUI](https://github.com/zed-industries/zed/tree/main/crates/gpui) - GPUI框架的核心代码库，位于Zed代码仓库内
- [官方网站](https://www.gpui.rs/) - GPUI的官方网站

## 开发工具

- [create-gpui-app](https://github.com/brscrt/create-gpui-app) - 一键脚手架生成GPUI应用程序
  ```bash
  cargo install create-gpui-app
  create-gpui-app --name my-app
  ```

## 组件库

- [gpui-component](https://github.com/longbridge/gpui-component) - 一个不断增长的UI组件库，包含Accordion、Button、DatePicker、Calendar、Modal、Table等组件，用于使用GPUI构建桌面应用

## 教程

- [gpui-tutorial](https://github.com/hedge-ops/gpui-tutorial) - 涵盖GPUI基础知识和如何构建第一个应用程序的实践教程
- [GPUI Book](https://github.com/MatinAniss/gpui-book) - 教授创建GPUI应用所需概念的电子书

## 示例

将依赖项直接从Git添加（生态系统成熟前）:

```toml
[dependencies]
gpui = { git = "https://github.com/zed-industries/zed", branch = "main" }
gpui-component = { git = "https://github.com/longbridge/gpui-component.git" }
```

Rust代码示例:

```rust
use gpui::prelude::*;
use gpui_component::DatePicker;

fn main() {
    // 初始化GPUI应用并打开窗口...
    DatePicker::new()
        .locale("zh-CN")
        .on_select(|date| println!("已选择: {:?}", date));
}
```

## 项目案例

- [zed](https://github.com/zed-industries/zed) - 使用GPUI构建的高性能、多人协作代码编辑器
- [Waku](https://github.com/egoist/waku) - 使用Rust和GPUI构建、面向本地编码智能体的快速原生桌面应用
- [Loungy](https://github.com/MatthiasGrandl/Loungy) - 基于GPUI的应用启动器
- [Helix GPUI](https://github.com/polachok/helix-gpui) - 使用GPUI实现的Helix编辑器
- [GPUI Calculator](https://github.com/kriskw1999/gpui-calculator) - 使用GPUI构建的计算器应用
- [GPUI Counter](https://github.com/derrickpersson/gpui-simple-counter) - 简单的GPUI计数器示例
- [GPUI Memory Game](https://github.com/justjavac/gpui-memory-game) - 使用Rust和GPUI构建的记忆匹配游戏
- [Hummingbird](https://github.com/143mailliw/hummingbird) - 使用Rust和GPUI构建的现代音乐播放器，设计轻量且高性能，支持FLAC、MP3、OGG和WAV播放
- [PGUI](https://github.com/duanebester/pgui) - 使用GPUI构建的Postgres数据库查询和管理GUI应用

## 博客文章

- [Ownership and Data Flow in GPUI](https://zed.dev/blog/gpui-ownership) - 深入描述GPUI中使用模型的所有权工作原理，包括如何发射和消费事件
- [Why the big rewrite?](https://zed.dev/blog/why-the-big-rewrite) - 关于转向类Tailwind API的原因的博客文章
- [非官方文档](https://github.com/Himasnhu-AT/GPUI-docs-unofficial) - 对GPUI的非官方文档尝试

## 视频

- [Second look at the Rust GPUI framework from Zed! Featuring web-sockets](https://www.youtube.com/watch?v=WQt4ur7fcd0) - 关于Zed的Rust GPUI框架的第二次探索，包含WebSocket功能演示

## 社区

- [Zed讨论](https://github.com/zed-industries/zed/discussions) - GPUI和Zed相关的GitHub讨论
- [Reddit讨论](https://www.reddit.com/r/rust/comments/11hu1sc/gpui_ui_framework_from_the_makers_of_zed/) - 关于GPUI的Reddit讨论

## 贡献

欢迎贡献！请阅读[贡献指南](CONTRIBUTING.md)了解如何开始。

## 许可证

[![CC0](https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0)

在法律允许的范围内，本作品的编译者已放弃对此作品的所有版权和相关或邻接权利。
