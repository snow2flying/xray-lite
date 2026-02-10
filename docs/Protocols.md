# Core Protocols & Stealth

Xray-lite focuses on the most robust protocol combinations to ensure long-term availability in restrictive environments.

## VLESS + Reality

Reality is the industry standard for camouflaging proxy traffic behind legitimate websites. It eliminates the need for personal TLS certificates by borrowing the security credentials of major websites (like Microsoft or Apple).

### Reality Handshake (XTLS-Reality64)
In Xray-lite, we implement a specialized handshake logic often referred to as **XTLS-Reality64**:
- **Initial Window**: The server defaults to a conservative **64KB** initial window size to mimic the handshake behavior of common web servers.
- **Dynamic Upgrade**: Once the Reality authentication is successful, the server dynamically increases the window size to **5MB** to allow for high-speed data transfer.

## xhttp (Next-Gen Transport)

The `xhttp` protocol in Xray-lite is enhanced with a **Mimicry Defense Engine** that provides superior resistance to traffic analysis and active probing.

### Core Features:

- **H2 Ping-Pong Noise / 随机心跳混淆**:
    - Periodically sends randomized H2 PING frames (every 15-45s).
    - Forces bi-directional background noise that masks connection timing and interferes with statistical analysis.
- **Adaptive Traffic Shaping (Shredder) / 自适应流量整形**:
    - **Random Chunking**: Splits data streams into randomly sized blocks (8KB - 16KB) to eliminate predictable packet length patterns.
    - **Adaptive Padding**: Injects dynamic padding in HTTP headers that adjusts its size based on real-time traffic volume (Security-priority for low traffic, Performance-priority for high traffic).
- **Chameleon Headers / 拟态请求头**:
    - Mimics standard **Nginx 1.26.0** response headers (`Cache-Control`, `Server`).
    - Injects randomized `x-padding` alphanumeric noise to evade header-length-based fingerprinting.

---

## Security Advantages

- **Zero-Copy Relay**: Data is relayed between the inbound and outbound with minimal copying, reducing the processing time.
- **TLS Fingerprint Shuffling**: Xray-lite randomizes the order of TLS extensions in the `ServerHello` message. This prevents GFW from identifying the server based on fixed extension patterns common in Go-based or simple Rust-based implementations.
