<div align="center">

# 🔓 TikTok iOS SSL Pinning Bypass

### Intercept, capture & analyze TikTok's HTTPS traffic on iPhone & iPad — no jailbreak · 2026

<br>

[![Download IPA](https://img.shields.io/badge/⬇_DOWNLOAD_IPA_v46.4.0-ff0050?style=for-the-badge&logo=tiktok&logoColor=white)](../../releases/latest)
[![Telegram](https://img.shields.io/badge/Chat_on_Telegram-26A5E4?style=for-the-badge&logo=telegram&logoColor=white)](https://t.me/MUH4MM4DSH4KIB)

![iOS](https://img.shields.io/badge/iOS_14.0+-000000?style=flat-square&logo=apple&logoColor=white)
![ARM64](https://img.shields.io/badge/arm64-blue?style=flat-square)
![Version](https://img.shields.io/badge/TikTok-v46.4.0-ff0050?style=flat-square&logo=tiktok&logoColor=white)
![Build](https://img.shields.io/badge/Build-464038-555555?style=flat-square)
![Updated](https://img.shields.io/badge/Updated-Regularly-brightgreen?style=flat-square)

🔓 Pinning defeated&nbsp;&nbsp;·&nbsp;&nbsp;🔐 Login & OTP&nbsp;&nbsp;·&nbsp;&nbsp;🧬 x-argus / x-gorgon&nbsp;&nbsp;·&nbsp;&nbsp;🎬 Video CDN&nbsp;&nbsp;·&nbsp;&nbsp;🛒 TikTok Shop

<img width="1073" height="710" alt="TikTok iOS SSL Pinning Bypass PoC – Login & Passport Traffic Captured" src="https://github.com/user-attachments/assets/72bab04f-e798-4eab-aa79-65fe59913869" />

_Live capture — TikTok iOS `passport/email/send_code/` intercepted in cleartext. v46.4.0 on iPhone / iOS 26.6._

</div>

> [!TIP]
> **Download the patched IPA** from the **[Releases](../../releases/latest)** section — or message me on **[Telegram](https://t.me/MUH4MM4DSH4KIB)** for the newest build or another version.

---

## ✨ Why This Build

| | |
|:--|:--|
| 🔓 **Full pinning bypass** | Cronet/TTNet **and** libvcn video-CDN pinning both defeated |
| 🔐 **Login flow works** | Passport / OTP / registration captured in cleartext |
| 🧬 **Signing headers in the clear** | `x-argus`, `x-gorgon`, `x-ladon`, `x-khronos` visible unencrypted |
| 🎬 **Everything else too** | Feed, upload, search, live, analytics, TikTok Shop |
| 📱 **Non-jailbroken** | Runs on a stock iPhone/iPad, iOS 14.0+ |

---

## 📦 Build

| App | Bundle ID | Version | Build | Arch |
|:----|:----------|:-------:|:-----:|:----:|
| **TikTok for iOS** | `com.zhiliaoapp.musically` | `46.4.0` | `464038` | `arm64` |

---

## 🎯 What You Can Capture

Full visibility into ByteDance's entire API surface:

| Surface | Exposed in cleartext |
|:--------|:---------------------|
| 🔐 **Login & auth** | `passport/email/send_code/`, `passport/auth/available_ways/`, OTP, session tokens |
| 🧬 **Signing headers** | `x-argus`, `x-gorgon`, `x-ladon`, `x-khronos` encryption parameters |
| 🎟️ **Ticket Guard** | `tt-ticket-guard` public keys, client data, signature payloads |
| 🛡️ **Device Guard** | `tt-device-guard` device-token signing and integrity payloads |
| 🎯 **For You feed** | the API requests behind the recommendation algorithm |
| 🎬 **Video delivery** | CDN URLs, quality negotiation (Cronet/TTNet), caching |
| 🔍 **Search & discovery** | search queries, hashtag lookups, trending endpoints |
| ⬆️ **Upload pipeline** | video upload, metadata submission, processing callbacks |
| 📊 **Analytics & telemetry** | Pigeon session tracking, device telemetry, A/B assignments |
| 🛒 **TikTok Shop** | product listings, cart, checkout flow |
| 📡 **Live streaming** | webcast config, stream-key delivery, chat endpoints |

---

## ⚙️ Requirements & Signing

**iOS 14.0+**, plus a MITM proxy — [Burp Suite](https://portswigger.net/burp), [mitmproxy](https://mitmproxy.org/), [Reqable](https://reqable.com), or [Proxypin](https://proxypin.com).

> [!IMPORTANT]
> **How you install decides whether login capture works.** TikTok's device registration needs a keychain-access-group entitlement (`…com.chainlogin`). If your signing method strips it, `device_register` fails and you hit **"maximum login attempts."**

| Install / signing method | Login & OTP | Notes |
|:--|:---:|:--|
| [**TrollStore**](https://github.com/opa334/TrollStore) | ✅ Works | 🏆 Best. iOS 14.0 – 16.6.1 / 17.0. Installs the IPA unmodified — entitlements intact, permanent, no re-sign. |
| **KravaSign** / paid **Apple Developer** cert | ✅ Works | For devices TrollStore can't cover (iOS 17.1+, 18, 26). Signs with a profile that keeps the entitlements. |
| [**Sideloadly**](https://sideloadly.io/) / [**AltStore**](https://altstore.io/) + **free Apple ID** | ❌ Max attempts | Free-account signing **strips** the entitlement → login fails. Browsing/feed still capture fine, but you can't log in. Only use with a paid/KravaSign cert. |

> [!TIP]
> **TL;DR** — TrollStore device → TrollStore. Newer iOS → KravaSign or a paid cert. **Never a free Apple ID** if you need login capture.

---

## 🚀 Setup

1. **Download** the patched IPA from [Releases](../../releases/latest).
2. **Install it** — *TrollStore:* open TrollStore → **+** → select the IPA → **Install**. *Newer iOS:* sign with **KravaSign** or a **paid cert** (not a free Apple ID) and trust the profile under **Settings → General → VPN & Device Management**. *(Uninstall the official TikTok app first — signatures conflict.)*
3. **Trust your proxy CA** — install the `.crt`/`.pem` via **Settings → General → VPN & Device Management → Install Profile**, then enable it under **Settings → General → About → Certificate Trust Settings**.
4. **Set the Wi-Fi proxy** — **Settings → Wi-Fi → (network) → Configure Proxy → Manual**.
5. **Launch TikTok** — log in, browse, upload, or go live, and watch decrypted HTTPS stream into your proxy in real time.

> [!WARNING]
> You need **both** the CA installed **and** full trust enabled. Skip either and HTTPS decryption fails silently.

---

<div align="center">

## 💼 Need a Custom Bypass?

**Custom SSL pinning bypass · automated patching scripts · full reverse-engineering projects** — for any iOS or Android app.

[![Request Custom Work](https://img.shields.io/badge/Message_me_on_Telegram-26A5E4?style=for-the-badge&logo=telegram&logoColor=white)](https://t.me/MUH4MM4DSH4KIB)

</div>

---

> [!NOTE]
> **Disclaimer** — For educational and security-research purposes only. Not affiliated with, endorsed by, or connected to TikTok or ByteDance. All trademarks belong to their respective owners. Only analyze traffic on accounts and devices you own or are authorized to test. Provided "as is", without warranty of any kind.

---

## 🔗 Related Projects

| App | Platform | Repository |
|-----|----------|------------|
| TikTok | Android | [TikTok SSL Pinning Bypass](https://github.com/0xSHAK1B/TIKTOK-SSL-Pinning-Bypass) |
| Facebook | iOS | [Facebook iOS SSL Pinning Bypass](https://github.com/0xSHAK1B/Facebook-iOS-SSL-Pinning-Bypass) |
| Instagram | iOS | [Instagram iOS SSL Pinning Bypass](https://github.com/0xSHAK1B/Instagram-iOS-SSL-Pinning-Bypass) |
| Threads | iOS | [Threads iOS SSL Pinning Bypass](https://github.com/0xSHAK1B/Threads-iOS-SSL-Pinning-Bypass) |
| Edits | iOS | [Edits iOS SSL Pinning Bypass](https://github.com/0xSHAK1B/Edits-iOS-SSL-Pinning-Bypass) |
| Instants | iOS | [Instants iOS SSL Pinning Bypass](https://github.com/0xSHAK1B/Instants-iOS-SSL-Pinning-Bypass) |
| Facebook | Android | [Facebook SSL Pinning Bypass](https://github.com/0xSHAK1B/Facebook-SSL-Pinning-Bypass) |
| Instagram | Android | [Instagram SSL Pinning Bypass](https://github.com/0xSHAK1B/Instagram-SSL-Pinning-Bypass) |
| Meta Business Suite | Android | [Meta Business Suite SSL Pinning Bypass](https://github.com/0xSHAK1B/Meta-Business-Suite-SSL-Pinning-Bypass) |
| X (Twitter) | Android | [Twitter SSL Pinning Bypass](https://github.com/0xSHAK1B/Twitter-SSL-Pinning-Bypass) |

---

<div align="center">

## 💖 Support This Project

If this saved you time or helped your research, please **⭐ star the repo** — it helps others find it and keeps the builds coming.

| Currency | Address |
|:---------|:--------|
| **BTC** | `131NaAJooX2XYq5QUFmKsTuLQXcGNayYPJ` |
| **ETH** | `0xea9a566a5123c3a1b8d60f8bdd845835716668f0` |
| **USDT (TRC-20)** | `THssAZhUQEEsw15211rAaRLGRjSWXMX4PW` |

<br>

**📬 Newest builds · support · custom work**

[![Telegram](https://img.shields.io/badge/@MUH4MM4DSH4KIB-26A5E4?style=for-the-badge&logo=telegram&logoColor=white)](https://t.me/MUH4MM4DSH4KIB)

⭐ **Star the repo if it helped your research!**

</div>

