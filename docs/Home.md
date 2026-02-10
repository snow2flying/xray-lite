# Welcome to Xray-Lite Wiki

Xray-lite is a lightweight, high-performance VLESS + Reality proxy server implemented in pure Rust. It is designed for users who prioritize performance, memory efficiency, and advanced stealth capabilities.

## Architecture Highlights

- **Pure Rust Implementation**: High performance with memory safety.
- **Asymmetric Compatibility**: Works with standard Xray/V2Ray clients (v2rayNG, Shadowsocks-libev, etc.).
- **Kernel-Level Acceleration**: Uses eBPF (XDP/TC) for firewalling and traffic shaping (XDP Edition).
- **Stealth First**: Optimized for Reality and xhttp protocols to evade detection.

<a name="quick-start"></a>
## Quick Start

1. **Install**: Run the installation script from the README.
2. **Configure**: Edit `config.json` with your UUID and Reality keys.
3. **Run**: Start the server using `./vless-server -c config.json`.
4. **Client Setup**: Use any VLESS-compatible client and input the server details.

## Navigation

- [Quick Start Guide](#quick-start)
- [Configuration Reference](./Configuration.md)
- [Core Protocols (Reality, xhttp, XTLS-Reality64)](./Protocols.md)
- [XDP & Kernel Defense](./XDP_Features.md)
- [Performance Tuning](./Performance.md)

## Why Xray-Lite?

Unlike official Xray which handles everything in user-space, Xray-lite moves critical network operations into the Linux kernel (via XDP). This not only boosts performance by reducing context switching but also provides a "stealth" layer where certain probing packets are dropped before they even reach the application layer.
