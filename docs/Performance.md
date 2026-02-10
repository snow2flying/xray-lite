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
On a Quad-Core VPS with 4GB RAM:
- **Idle**: < 10MB RAM.
- **1Gbps Throughput**: ~15% CPU (Standard), ~8% CPU (XDP Native).
