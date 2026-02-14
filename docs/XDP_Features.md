# XDP & Kernel Defense (Advanced)

[The XDP Edition of Xray-lite](https://github.com/undead-undead/xray-lite/tree/feature/dynamic-xdp) leverages Linux eBPF technology to move security logic into the kernel. This provides a "Hardware-like" defense that is invisible to most scanners.


Reduce latency:

• Traditional path: Network adapter driver -> Software interrupt handling -> IP layer resolution -> TCP/UDP state machine handling -> User-mode switching -> VLESS program identification.

• XDP path: Network adapter driver -> XDP program (your code) -> Discard directly or pass to the application.

## Dual-Stack XDP Firewall

Xray-lite includes a custom eBPF program that runs on the network card driver layer.

### Key Capabilities:
- **SYN Flood Protection**: Rate-limits incoming SYN packets at the driver level.
- **UDP Filter**: Instantly drops unsolicited UDP packets, effectively neutralising UDP-based active probing.
- **Malicious Flag Filtering**: Drops packets with illegal TCP flags (e.g., NULL scans or Xmas scans) before they reach the OS TCP stack.
- **Port Masking**: Only the ports configured in `config.json` are exposed to the eBPF filter; all other traffic passes normally, ensuring your SSH or other services remain accessible.



## Synergy with xhttp: The Ultimate Stealth Combo

When the **XDP Edition** is used in conjunction with the **xhttp** protocol, it creates a multi-layered defense system that is significantly more effective than traditional proxy setups.

### 1. Zero-Noise Active Probing Defense
While `xhttp` mimics a standard Web server at the application layer, XDP provides a **silent shield** at the kernel layer. Malicious probing packets are dropped silently by XDP before they ever touch the `xhttp` engine. To a scanner, your server appears to have **stealth ports** that simply don't respond to anything but legitimate TLS handshakes.

### 2. Deep Packet-Length Obfuscation (Shredder)
- **Layer 7 (xhttp Shredder)**: Randomly chunks and pads segments to eliminate packet-length fingerprints.
This ensures that the **structure** and **size** of your traffic are perfectly camouflaged, making it indistinguishable from organic modern Web traffic (like video streaming or high-concurrency API calls).

### 3. Resource-Aware Mimicry
XDP filters out high-volume malicious noise (like UDP floods) with near-zero CPU cost. This preserves your CPU cycles for `xhttp`'s advanced H2 encryption and chameleon header generation, allowing even low-spec VPS servers to maintain ultra-high stealth without sacrificing throughput.

## Requirements
- **Linux Kernel 5.4+**: Required for BPF_MAP_TYPE_HASH and XDP support.
- **Root Privileges**: Required to load eBPF programs and attach them to interfaces.
- **Supported Architectures**: x86_64, arm64.
