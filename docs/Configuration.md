# Configuration Reference

Xray-lite uses a JSON-based configuration file (`config.json`). Below is a detailed explanation of each section.

## Basic Structure

```json
{
  "log": {
    "level": "info",
    "access": "/var/log/xray/access.log",
    "error": "/var/log/xray/error.log"
  },
  "inbounds": [...],
  "outbounds": [...]
}
```

## Inbound Object

| Field | Type | Description |
| :--- | :--- | :--- |
| `port` | `number` | The port the server listens on (e.g., 443). |
| `protocol` | `string` | Must be `"vless"`. |
| `settings` | `object` | VLESS specific settings (clients and decryption). |
| `streamSettings` | `object` | Network and security configuration. |

### VLESS Settings
- **clients**: An array of client objects.
    - **id**: A valid UUID (e.g., `"your-uuid-here"`).
    - **flow**: Leave empty or set to `"xtls-rprx-vision"` (Legacy, Reality is preferred).
- **decryption**: Usually `"none"`.

### Stream Settings
- **network**: `"tcp"` or `"xhttp"`.
- **security**: `"reality"`.
- **realitySettings**:
    - **dest**: The target website to mimic (e.g., `"www.microsoft.com:443"`).
    - **serverNames**: A list of server names (SNI) to accept (e.g., `["www.microsoft.com"]`).
    - **privateKey**: Your generated Reality private key.
    - **shortIds**: An array of hex strings used for handshake verification.

## Outbound Object

Standard outbound for proxying traffic:
```json
{
  "protocol": "freedom",
  "settings": {}
}
```

## XDP Environment Variables

For the XDP Edition, additional parameters can be passed via command line or environment:
- `--enable-xdp`: Enable the eBPF/XDP firewall.
- `--xdp-iface`: The network interface to attach to (e.g., `eth0`).
- `--xdp-mode`: `skb` (generic) or `native` (driver-supported, faster).
