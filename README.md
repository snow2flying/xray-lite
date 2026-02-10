# Xray-Lite (XDP Edition)

> Lightweight, Kernel-Accelerated Proxy in Rust.  
> 基于 Rust 实现的轻量级内核加速代理。

[Quick Install](#quick-install) | [English](#english) | [中文](#chinese) | [Русский](#russian) | [فارسی](#persian)

---

## Quick Install / 快速安装

```bash
# XDP Edition (Stealth & Kernel Protection)
bash <(curl -fsSL https://raw.githubusercontent.com/undead-undead/xray-lite/feature/dynamic-xdp/install.sh)
```

---

<a name="english"></a>
## English

Xray-lite is a high-performance proxy server specifically designed for ultra-stealth and network resilience using Linux kernel-level acceleration.

### How it differs from Official Xray
1. **Kernel driver processing**: Official Xray works globally in user-space. Xray-lite uses **eBPF (XDP/TC)** to process packets directly at the network interface driver layer, making it significantly faster and invisible to many scanning tools.
2. **Advanced Traffic Pacing**: Implements kernel-level **Adaptive Egress Pacing** with microsecond precision and random jitter, smoothing outbound traffic to eliminate "proxy burst" fingerprints.
3. **Asymmetric Compatibility**: Unlike other modified versions, Xray-lite is designed to be **fully compatible** with any official Xray/V2Ray client (e.g., v2rayNG, Necore, Streisand) while providing superior server-side protection.
4. **Protocols**: Focusing exclusively on the strongest anti-censorship combo: **VLESS + Reality + XHTTP**.
5. **Lightweight**: Pure Rust implementation with zero-copy architecture, resulting in minimal CPU/RAM footprint.

---

<a name="chinese"></a>
## 中文

Xray-lite 是一款专为极致隐蔽和网络抗性而设计的轻量级内核加速代理服务器。

### 与官方 Xray 的区别
1. **内核级处理**：官方 Xray 完全运行在用户态，而 Xray-lite 利用 **eBPF (XDP/TC)** 技术直接在网卡驱动层处理报文，实现极高的处理效率，并对诸多扫描探测工具实现“隐身”。
2. **自适应流量整形**：在内核层实现**自适应出站整形 (Egress Pacing)**，支持微秒级精度和随机抖动，平滑流量曲线，有效抹除典型的“代理突发流量”指纹。
3. **非对称兼容**：与市面上某些魔改版不同，Xray-lite 完美**非对称兼容**任何原版 Xray/V2Ray 客户端（如 v2rayNG, Necore），您无需更换客户端即可享受内核级加固。
4. **协议精选**：仅支持最强防封组合：**VLESS + Reality + XHTTP**。
5. **极致轻量**：纯 Rust 实现，零拷贝架构，极低的 CPU/内存资源消耗。

---

<a name="russian"></a>
## Русский

Xray-lite — это высокопроизводительный прокси-сервер, специально разработанный для максимальной скрытности с использованием ускорения на уровне ядра Linux.

### Чем отличается от официального Xray
1. **Обработка в ядре**: Официальный Xray работает полностью в пространстве пользователя. Xray-lite использует **eBPF (XDP/TC)** для обработки пакетов непосредственно на уровне драйвера сетевого интерфейса, что делает его значительно быстрее и невидимым для многих инструментов сканирования.
2. **Адаптивное формирование трафика**: Реализует **Adaptive Egress Pacing** на уровне ядра с микросекундной точностью и случайным джиттером, сглаживая исходящий трафик для устранения отпечатков «прокси-всплесков».
3. **Асимметричная совместимость**: В отличие от других модифицированных версий, Xray-lite **полностью совместим** с любым официальным клиентом Xray/V2Ray (например, v2rayNG, Necore), обеспечивая при этом превосходную защиту на стороне сервера.
4. **Протоколы**: Ориентирован исключительно на самую мощную комбинацию: **VLESS + Reality + XHTTP**.
5. **Сверхлегкий**: Реализация на чистом Rust с архитектурой без копирования, что обеспечивает минимальное потребление ресурсов CPU/RAM.

---

<a name="persian"></a>
## فارسی

Xray-lite یک سرور پروکسی با کارایی بالا است که به طور اختصاصی برای پنهان‌کاری فوق‌العاده و مقاومت شبکه با استفاده از شتاب‌دهنده سطح هسته لینوکس طراحی شده است.

### تفاوت با Xray رسمی
۱. **پردازش در سطح هسته**: Xray رسمی به طور کامل در فضای کاربر (user-space) کار می‌کند. Xray-lite از **eBPF (XDP/TC)** برای پردازش بسته‌ها مستقیماً در لایه درایور رابط شبکه استفاده می‌کند که آن را به مراتب سریع‌تر و در برابر بسیاری از ابزارهای اسکن نامرئی می‌کند.
۲. **تنظیم ترافیک تطبیقی**: قابلیت **Adaptive Egress Pacing** را در سطح هسته با دقت میکروثانیه و لرزش تصادفی (jitter) پیاده‌سازی می‌کند تا با هموار کردن ترافیک خروجی، ردپای "ترافیک انفجاری پروکسی" را از بین ببرد.
۳. **سازگاری نامتقارن**: برخلاف سایر نسخه‌های تغییر یافته، Xray-lite برای **سازگاری کامل** با هر کلاینت رسمی Xray/V2Ray (مانند v2rayNG، Necore) طراحی شده است و در عین حال محافظت برتر سمت سرور را فراهم می‌کند.
۴. **پروتکل‌ها**: تمرکز انحصاری بر قوی‌ترین ترکیب ضد سانسور: **VLESS + Reality + XHTTP**.
۵. **فوق‌العاده سبک**: پیاده‌سازی خالص Rust با معماری zero-copy، که منجر به حداقل استفاده از CPU/RAM می‌شود.

---

## Support the Developer / 支持开发者

If you find this project useful, consider supporting the developers:

- **BTC**: `3Gf...` (Please add your real address here)
- **Solana**: `9QFKQ3jpBSuNPLZQH1uq5GrJm4RDKue82zeVaXwazcmj`
- **Base (ETH/USDC)**: `0x4cf0b79aea1c229dfb1df9e2b40ea5dd04f37969`
- **Buy Me a Coffee**: [buymeacoffee.com/undeadundead](https://buymeacoffee.com/undeadundead)

## License
[MPL-2.0](LICENSE)
业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业务逻辑精准对齐与 XDP 修复业
