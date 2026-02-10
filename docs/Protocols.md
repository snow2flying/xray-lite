# Core Protocols & Stealth

Xray-lite focuses on the most robust protocol combinations to ensure long-term availability in restrictive environments.

## VLESS + Reality

Reality is the industry standard for camouflaging proxy traffic behind legitimate websites. It eliminates the need for personal TLS certificates by borrowing the security credentials of major websites (like Microsoft or Apple).

### Reality Handshake (XTLS-Reality64)
In Xray-lite, we implement a specialized handshake logic often referred to as **XTLS-Reality64**:
- **Initial Window**: The server defaults to a conservative **64KB** initial window size to mimic the handshake behavior of common web servers.
- **Dynamic Upgrade**: Once the Reality authentication is successful, the server dynamically increases the window size to **5MB** to allow for high-speed data transfer.

## xhttp (Next-Gen Transport)

- **Asymmetric Compatibility / 非对称兼容**: Fully compatible with any official Xray/V2Ray client (e.g., v2rayNG, Nekoray). You get kernel-level protection without needing special client modifications.
- **Kernel-Level Acceleration / 内核级处理**: Integrates with **XDP/TC** to process packet headers at the driver level, significantly reducing CPU overhead and latency compared to standard user-space implementations.
- **Adaptive Traffic Pacing / 自适应流量整形**: Implements microsecond-level egress pacing via **TC eBPF**, smoothing out burst patterns to eliminate "proxy-typical" traffic fingerprints.
- Optimized in Xray-lite for low-latency transmission using a **Zero-Copy** architecture.

## Security Advantages

- **Zero-Copy Relay**: Data is relayed between the inbound and outbound with minimal copying, reducing the processing time.
- **TLS Fingerprint Shuffling**: Xray-lite randomizes the order of TLS extensions in the `ServerHello` message. This prevents GFW from identifying the server based on fixed extension patterns common in Go-based or simple Rust-based implementations.
