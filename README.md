# Xray-Lite (XDP Edition)

> Lightweight, Kernel-Accelerated VLESS Proxy in Rust.  
> 基于 Rust 实现的轻量级内核加速 VLESS 代理。

[Quick Install](#install) | [English](#english) | [中文](#chinese) | [Русский](#russian) | [فارسی](#persian)

---

<a name="install"></a>
## Quick Install / 快速安装

```bash
# XDP Edition (Stealth & Kernel Protection)
bash <(curl -fsSL https://raw.githubusercontent.com/undead-undead/xray-lite/feature/dynamic-xdp/install.sh)
```

---

<a name="english"></a>
## English

Xray-lite is a high-performance proxy server built for ultra-stealth and network resilience. Unlike the official Xray implementation, Xray-lite utilizes Linux kernel eBPF (XDP/TC) technology to process traffic at the NIC driver level, providing unmatched protection and efficiency.

### Key Features
- **Kernel-Level Defense (XDP)**: Automatically drops UDP Floods, SYN Floods, and Malicious Probes at the network driver layer.
- **Adaptive Egress Pacing**: Smooths outbound traffic using TC eBPF with microsecond precision and random jitter to defeat traffic analysis.
- **Ultra-Lightweight**: Written in pure Rust with an asynchronous core, consuming minimal CPU and RAM.
- **Asymmetric Compatibility**: Fully compatible with any official Xray/V2Ray client (e.g., v2rayNG, Shadowsocks-libev) while providing superior server-side protection.
- **Stealth Protocols**: Specifically optimized for **VLESS + Reality + XHTTP**.

### Why Xray-Lite?
Official Xray operates entirely in user space. Xray-lite moves critical security and performance logic into the Linux kernel using eBPF, making it nearly invisible to network scanning tools and significantly harder to analyze.

---

<a name="chinese"></a>
## 中文

Xray-lite 是一款专为极致隐蔽和网络抗性设计的轻量级代理服务器。与官方 Xray 不同，Xray-lite 利用 Linux 内核 eBPF (XDP/TC) 技术在网卡驱动层处理流量，提供无与伦比的防护和效率。

### 核心特性
- **内核级防御 (XDP)**：在网卡驱动层自动丢弃 UDP 洪水、SYN 洪水和恶意扫描探测。
- **自适应出站整形**：利用 TC eBPF 实现微秒级精度的出站流量平滑，引入随机抖动，有效抹除代理流量指纹特征。
- **极致轻量**：纯 Rust 实现，异步并发核心，占用极低的 CPU 和 内存资源。
- **非对称兼容**：完美兼容任何原版 Xray/V2Ray 客户端（如 v2rayNG），无需特殊客户端即可享受内核级服务端加固。
- **精选协议支持**：专注于最强防封组合：**VLESS + Reality + XHTTP**。

---

<a name="russian"></a>
## Русский

Xray-lite — это высокопроизводительный прокси-сервер, созданный для максимальной скрытности и устойчивости сети. В отличие от официальной реализации Xray, Xray-lite использует технологию eBPF (XDP/TC) ядра Linux для обработки трафика на уровне драйвера сетевой карты, обеспечивая непревзойденную защиту и эффективность.

### Основные характеристики
- **Защита на уровне ядра (XDP)**: Автоматически сбрасывает UDP-флуд, SYN-флуд и вредоносные сканирования на уровне сетевого драйвера.
- **Адаптивное формирование трафика**: Сглаживает исходящий трафик с помощью TC eBPF с микросекундной точностью и случайным джиттером для обхода анализа трафика.
- **Сверхлегкий**: Написан на чистом Rust с асинхронным ядром, потребляя минимум ресурсов процессора и оперативной памяти.
- **Асимметричная совместимость**: Полностью совместим с любым официальным клиентом Xray/V2Ray (например, v2rayNG), обеспечивая при этом превосходную защиту на стороне сервера.
- **Протоколы**: Оптимизирован для **VLESS + Reality + XHTTP**.

---

<a name="persian"></a>
## فارسی

Xray-lite یک سرور پروکسی با کارایی بالا است که برای پنهان‌کاری فوق‌اعاده و مقاومت شبکه ساخته شده است. برخلاف پیاده‌سازی رسمی Xray، Xray-lite از فناوری eBPF (XDP/TC) هسته لینوکس برای پردازش ترافیک در سطح درایور کارت شبکه استفاده می‌کند که محافظت و کارایی بی‌نظیری را فراهم می‌کند.

### ویژگی های کلیدی
- **دفاع در سطح هسته (XDP)**: به طور خودکار حملات UDP Flood، SYN Flood و اسکن‌های مخرب را در لایه درایور شبکه مسدود می‌کند.
- **تنظیم ترافیک تطبیقی**: ترافیک خروجی را با استفاده از TC eBPF با دقت میکروثانیه و لرزش تصادفی (jitter) برای شکست دادن تحلیل ترافیک، هموار می‌کند.
- **فوق‌العاده سبک**: نوشته شده با Rust خالص با هسته ناهمگام، که حداقل CPU و RAM را مصرف می‌کند.
- **سازگاری نامتقارن**: کاملاً با هر کلاینت رسمی Xray/V2Ray (مانند v2rayNG) سازگار است در حالی که محافظت برتر سمت سرور را فراهم می‌کند.
- **پروتکل‌ها**: بهینه‌سازی شده برای **VLESS + Reality + XHTTP**.

---

## Configuration Example / 配置示例

```json
{
  "inbounds": [{
    "port": 443,
    "protocol": "vless",
    "settings": {
      "clients": [{ "id": "uuid-here" }],
      "decryption": "none"
    },
    "streamSettings": {
      "network": "tcp",
      "security": "reality",
      "realitySettings": {
        "dest": "www.apple.com:443",
        "serverNames": ["www.apple.com"],
        "privateKey": "your-private-key",
        "shortIds": ["0123456789abcdef"]
      }
    }
  }]
}
```

## License
MIT
