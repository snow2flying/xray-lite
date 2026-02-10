# Core Protocols & Stealth

Xray-lite focuses on the most robust protocol combinations to ensure long-term availability in restrictive environments.

## VLESS + Reality

Reality is the industry standard for camouflaging proxy traffic behind legitimate websites. It eliminates the need for personal TLS certificates by borrowing the security credentials of major websites (like Microsoft or Apple).

### Reality Handshake (XTLS-Reality64)
In Xray-lite, we implement a specialized handshake logic often referred to as **XTLS-Reality64**:
- **Initial Window**: The server defaults to a conservative **64KB** initial window size to mimic the handshake behavior of common web servers.
- **Dynamic Upgrade**: Once the Reality authentication is successful, the server dynamically increases the window size to **5MB** to allow for high-speed data transfer.

## xhttp (Next-Gen Transport)

The `xhttp` protocol is designed for better multiplexing and resilience against active probing. 
- It wraps data in HTTP/2 frames.
- It is highly resistant to traffic analysis as it looks identical to standard web application traffic.
- Optimized in Xray-lite for low-latency transmission.

## Security Advantages

- **Zero-Copy Relay**: Data is relayed between the inbound and outbound with minimal copying, reducing the processing time.
- **TLS Fingerprint Shuffling**: Xray-lite randomizes the order of TLS extensions in the `ServerHello` message. This prevents GFW from identifying the server based on fixed extension patterns common in Go-based or simple Rust-based implementations.
