# Xray-Lite

A lightweight, high-performance VLESS + Reality + XTLS-Reality64 proxy server implemented in pure Rust. Fully compatible with all Xray/V2Ray clients.

一个轻量级、高性能的纯 Rust 实现的 VLESS + Reality + xhttp 代理服务器。完全兼容所有 Xray/V2Ray 客户端。

[Documentation](./docs/Home.md) | [x-ui-lite Panel](https://github.com/undead-undead/x-ui-lite) | [Report Bug](https://github.com/undead-undead/xray-lite/issues)



## Quick Installation / 快速安装

> **Note**: This is a **static compilation version** that works perfectly on **any Linux system** (Debian, Ubuntu, CentOS, Alpine, etc.) without dependency issues.
>
> **注意**：此为**静态编译版本**，完美适配**任何 Linux 系统** (Debian, Ubuntu, CentOS, Alpine 等)，无需担心依赖问题。

### 1. Standard Installation (Recommended) / 标准版安装（推荐）

> **Current Version: v0.4.6**

```bash
bash <(curl -fsSL https://raw.githubusercontent.com/undead-undead/xray-lite/main/install.sh)
```

### 2. XDP Installation (Performance Enhanced) / XDP 版安装（性能增强版）

> **Current Version: v0.6.0-xdp (Rate Limit)**
> 
> **Requirements**: Linux Kernel ≥ 5.4 (AMD64 only), Root privileges.

```bash
bash <(curl -fsSL https://raw.githubusercontent.com/undead-undead/xray-lite/feature/dynamic-xdp/install.sh)
```





If you think the project is good, you can support the developers.
https://buymeacoffee.com/undeadundead


crypto:

Sol: 9QFKQ3jpBSuNPLZQH1uq5GrJm4RDKue82zeVaXwazcmj


Base：0x4cf0b79aea1c229dfb1df9e2b40ea5dd04f37969


## Contributing / 贡献

We welcome all kinds of contributions! Please verify that `cargo test` passes before submitting a PR.
欢迎各种形式的贡献！提交 PR 前请确保通过 `cargo test`。

## License / 许可证

[MPL-2.0](LICENSE)
