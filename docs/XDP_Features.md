# XDP & Kernel Defense (Advanced)

The XDP Edition of Xray-lite leverages Linux eBPF technology to move security logic into the kernel. This provides a "Hardware-like" defense that is invisible to most scanners.

## Dual-Stack XDP Firewall

Xray-lite includes a custom eBPF program that runs on the network card driver layer.

### Key Capabilities:
- **SYN Flood Protection**: Rate-limits incoming SYN packets at the driver level.
- **UDP Filter**: Instantly drops unsolicited UDP packets, effectively neutralising UDP-based active probing.
- **Malicious Flag Filtering**: Drops packets with illegal TCP flags (e.g., NULL scans or Xmas scans) before they reach the OS TCP stack.
- **Port Masking**: Only the ports configured in `config.json` are exposed to the eBPF filter; all other traffic passes normally, ensuring your SSH or other services remain accessible.

## Adaptive Egress Pacing (TC eBPF)

One of the most detectable traits of a proxy is "Proxy Burst" — the sudden transmission of large amounts of data at the maximum link speed.

### How Pacing Works:
1. **Traffic Smoothing**: Xray-lite uses a Traffic Control (TC) BPF program to enforce a minimum interval between outgoing packets.
2. **Microsecond Precision**: Unlike standard user-space rate limits, TC-BPF operates with microsecond precision.
3. **Random Jitter**: The pacing logic introduces a small, random delay (jitter) to each packet, mimicking the "noisy" nature of standard residential or server-to-server internet traffic.
4. **Resilience**: This makes it nearly impossible for statistical analysis models to differentiate proxy traffic from standard HTTPS traffic.

## Requirements
- **Linux Kernel 5.4+**: Required for BPF_MAP_TYPE_HASH and XDP support.
- **Root Privileges**: Required to load eBPF programs and attach them to interfaces.
- **Supported Architectures**: x86_64, arm64.
