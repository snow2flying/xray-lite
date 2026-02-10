# Performance Tuning

Xray-lite is built for high-performance out of the box, but certain system-level tweaks can further enhance stability and throughput.

## System Limits (`ulimit`)

Ensure your server can handle high numbers of concurrent connections:
```bash
ulimit -n 65535
```
Or add to `/etc/security/limits.conf`:
```text
* soft nofile 65535
* hard nofile 65535
```

## Buffer Optimization

In the Standard Edition (v0.4.6+), we use a **512KB** duplex buffer and **8KB+** chunk sizes. This is mathematically balanced to minimize CPU wake-ups while avoiding excessive RAM usage.

## XDP Native Mode

If your network card driver supports it, always use `native` mode for XDP:
```bash
./vless-server -c config.json --enable-xdp --xdp-iface eth0 --xdp-mode native
```
This avoids cloning the packet into an SKB (Socket Buffer), allowing the kernel to handle it directly in the driver receive ring.

## Resource Consumption

Xray-lite is extremely lightweight and is optimized for entry-level VPS servers (e.g., **1 vCPU / 512MB - 1GB RAM**).

| Metric | Performance (1 vCPU / 1GB RAM) |
| :--- | :--- |
| **Idle Memory Usage** | **< 6MB RAM** |
| **Active Memory (Heavy Load)** | **< 20MB RAM** (due to Zero-copy) |
| **1Gbps Throughput (Standard)** | ~25% CPU usage |
| **1Gbps Throughput (XDP Native)** | **~10% CPU usage** |

> **Note**: These benchmarks show that even the cheapest "nano" instances can handle full gigabit speeds with minimal overhead.
