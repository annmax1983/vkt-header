# vkt-header

English | [中文](languages/README_zh.md) | [Español](languages/README_es.md) | [Deutsch](languages/README_de.md) | [日本語](languages/README_ja.md) | [Français](languages/README_fr.md)

Tab-isolated HTTP request header modifier for Chromium browsers. Modify headers per-tab, save profiles with URL matching, auto-cleanup when done.

> Chromium · Manifest V3 · Session Rules · Tab Isolated · URL Matching

---

## Why vkt-header?

Most header modifiers change headers globally — once set, every tab and every request is affected. vkt-header is different: **rules are strictly bound to the current tab**, and **profiles can be bound to specific URLs** for automatic matching.

| Advantage | Detail |
|-----------|--------|
| 🔒 **Tab Isolation** | Rules only affect the target tab. Closing the tab removes all rules instantly. |
| 🔗 **URL Matching** | Bind profiles to URLs. 3-level priority: exact match → path prefix → domain. |
| 🧹 **Auto Cleanup** | Session rules vanish on browser restart. No persistent modifications. |
| ⚡ **Inline Editing** | Add/edit headers directly in the side panel. No separate editor. |
| 🎯 **Presets** | One-click presets: iPhone, Android, iPad, Googlebot, Referer, X-Forwarded-For. |
| 🌍 **6 Languages** | English, 中文, 日本語, Deutsch, Español, Français. |

---

## Core Feature: URL Matching

Each profile has a **Match URL** field. When you open the side panel on a page, vkt-header automatically finds matching profiles.

**Matching priority (highest first):**

| Priority | Example Profile MatchURL | Page URL | Score |
|----------|--------------------------|----------|-------|
| 🥇 Exact | `https://api.example.com/v1/users` | `https://api.example.com/v1/users` | 1000 |
| 🥈 Path prefix | `https://api.example.com/v1` | `https://api.example.com/v1/users` | 500+ |
| 🥉 Domain only | `https://api.example.com/` | `https://api.example.com/v1/users` | 100 |
| ❌ No match | `https://other.com/` | `https://api.example.com/v1/users` | 0 |

- Domain matching is **case-insensitive**
- Longer/more specific URLs have higher priority
- A green **Match Hint** bar appears when a matching profile is found — one click to apply

---

## Features

| Feature | Description |
|---------|-------------|
| **Set / Remove headers** | Add, overwrite, or remove any HTTP request header |
| **Inline editor** | Edit headers directly in the side panel — no popup/panel switching |
| **Profile system** | Save multiple header configurations as profiles |
| **URL binding** | Bind profiles to URLs for automatic matching |
| **URL tags** | Click current page domain/path to auto-fill Match URL |
| **Match hint** | Auto-detect matching profiles when opening side panel |
| **Presets** | Quick-add common headers: Mobile UA, Bot UA, Referer, XFF |
| **Tab isolation** | Rules strictly bound to tabId — no cross-tab contamination |
| **Session rules** | `declarativeNetRequest` session rules — auto-clear on browser restart |
| **Import / Export** | JSON backup and restore of all profiles |
| **6 languages** | Auto-detected from browser language settings |

---

## Use Cases

| Scenario | How |
|----------|-----|
| **Mobile testing** | Apply iPhone/Android/iPad UA preset to simulate mobile devices |
| **API debugging** | Set Authorization, X-Custom-Header for REST/GraphQL requests |
| **Referer testing** | Modify Referer header to test hotlink protection |
| **Geo testing** | Set X-Forwarded-For to simulate different client IPs |
| **CORS testing** | Modify Origin header to test cross-origin policies |
| **Bot simulation** | Apply Googlebot UA to see how sites respond to crawlers |

---

## Free vs Premium

| | Free | Premium |
|---|---|---|
| Profiles | 5 max | Unlimited |
| Headers per profile | 5 max | Unlimited |
| URL matching | ✅ | ✅ |
| Tab isolation | ✅ | ✅ |
| Import / Export | ✅ | ✅ |
| Presets | ✅ | ✅ |

---

## Preview

<p align="center">
  <img src="screenshot/preview.png" alt="vkt-header Preview" width="640">
</p>

---

## Supported Browsers

| Browser | Status | Minimum Version |
|---------|--------|------------------|
| Google Chrome | ✅ Fully supported | Chrome 114+ (SidePanel API) |
| Microsoft Edge | ✅ Fully supported | Edge 114+ |
| Other Chromium-based browsers | ⚠️ Basic compatible | Must support SidePanel API |

---

## Installation

For your safety, only install vkt-header through official browser extension stores:

1. Open **Chrome Web Store** or **Microsoft Edge Add-ons**
2. Search: `vkt-header`
3. Click **"Add to Chrome"** / **"Add to Edge"**
4. Click the 🔧 vkt-header icon in your toolbar to open the side panel

> ⚠️ Do not install from third-party websites. Unauthorized versions may compromise your data security.

---

## Privacy

vkt-header follows privacy-by-design principles:

- ✅ All profiles stored in `chrome.storage.local` — **no data is uploaded to any server**
- ✅ Session rules auto-clear on browser restart — no persistent modifications
- ✅ No analytics, no tracking, no cookies
- ✅ Some headers (Host, Origin) are browser-protected and cannot be modified
- ✅ For development and debugging purposes only

### Permissions

| Permission | Reason |
|------------|--------|
| `storage` | Save header templates and settings locally |
| `activeTab` | Access current tab when user clicks apply |
| `sidePanel` | Display the extension UI in a side panel |
| `declarativeNetRequestWithHostAccess` | Modify HTTP request headers per tab |
| `tabs` | Detect tab close for automatic rule cleanup |

- [Full Privacy Policy](https://annmax1983.github.io/vkt-header/privacy-policy.html)

---

## FAQ

1. **Headers don't take effect after applying?**
   Try refreshing the page. DNR session rules apply to new requests, not already-loaded resources.

2. **Rules disappear after closing the browser?**
   This is by design. vkt-header uses session rules only — they auto-clear on browser restart for safety.

3. **Some headers can't be modified?**
   Browser-protected headers (Host, Origin, etc.) cannot be modified by extensions. This is a browser security restriction, not a bug.

4. **How do I transfer profiles to another device?**
   Open Settings → Export to download a JSON backup, then Import it on the other device.

---

## Copyright Disclaimer

1. This extension modifies HTTP request headers for development and debugging purposes only. All content and services of accessed websites belong to their respective owners.
2. Users shall not use this extension to bypass website security restrictions, access unauthorized content, or engage in any illegal activities.
3. Users shall comply with local laws and platform terms of service when using this extension.

---

## Source Code Notice

> ⚠️ **This repository does not publish source code.** It contains only usage documentation, release notes, and support resources. The extension is distributed exclusively through the Chrome Web Store. No offline installation packages or end-user source code are provided.

---

## License

Copyright © 2026 vkt-header. All rights reserved.

This software is closed-source proprietary software. Without official written authorization, the following are strictly prohibited:
- Decompiling, cracking, or modifying the program code
- Repackaging, redistribution, sharing, or commercial resale
- Embedding the program into other software for bundled distribution

---

## ❤️ Support

If you find vkt-header helpful, consider buying the developer a coffee!

**[👉 Click here to support](https://ko-fi.com/annmax?buyACoffee=true&ref=vkt-header)**
