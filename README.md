# vkt-header

English | [中文](languages/README_zh.md) | [Español](languages/README_es.md) | [Deutsch](languages/README_de.md) | [日本語](languages/README_ja.md) | [Français](languages/README_fr.md)

Global HTTP request header modifier for Chromium browsers. Rules are matched by **domain only** (case-insensitive, path ignored) and apply to **every tab** — there is no tab isolation and no per-tab state.

> Chromium · Manifest V3 · Session Rules · Domain Matching · Global

---

## Why vkt-header?

Most header modifiers change headers globally, or require fiddly per-tab state. vkt-header keeps it simple: a rule is matched by the **domain** of the requested URL and applies everywhere, in every tab, the moment it is enabled.

| Advantage | Detail |
|-----------|--------|
| 🌐 **Domain Matching** | Rules match the domain only, case-insensitively. Paths are ignored. |
| 🔗 **Any Tab** | A rule applies in every tab — nothing is bound to a specific tab. |
| 🌍 **Global Rules** | Leave the Match URL empty and the rule applies to **all requests**. |
| 🧹 **Auto Re-apply** | Session rules vanish on browser restart; vkt-header re-applies all enabled rules automatically when the browser starts. |
| ⚡ **Inline Editing** | Add/edit headers directly in the side panel. No separate editor. |
| 🎯 **Presets** | One-click presets: iPhone, Android, iPad, Googlebot, Referer, X-Forwarded-For. |

---

## Core Feature: Domain Matching

Each rule has a **Match URL** field, but only the **domain** part is used:

- Matching is **case-insensitive** (`EXAMPLE.COM` = `example.com`)
- Paths are ignored (`https://example.com/api` behaves exactly like `example.com`)
- A leading `www.` is optional — `https://www.cnblogs.com/` and `https://cnblogs.com/` match the same rule
- Other subdomains (`pic.cnblogs.com`, `blog.cnblogs.com`, …) do **not** match
- The rule applies in **every tab**, to any request whose domain matches
- **Empty Match URL** = the rule applies to **all requests**

| What you type | Effective domain | Applies to |
|---|---|---|
| `example.com` | example.com | example.com and www.example.com, any path |
| `HTTPS://EXAMPLE.COM/api` | example.com | same — path is ignored |
| `https://www.cnblogs.com/` | cnblogs.com | cnblogs.com and www.cnblogs.com |
| `pic.cnblogs.com` | pic.cnblogs.com | pic.cnblogs.com and www.pic.cnblogs.com only |
| *(empty)* | — | **all requests** |

Enable a rule with its switch in the side panel. The master switch at the top stops or resumes all rules at once.

---

## Features

| Feature | Description |
|---------|-------------|
| **Set / Remove headers** | Add, overwrite, or remove any HTTP request header |
| **Inline editor** | Edit headers directly in the side panel — no popup/panel switching |
| **Rule system** | Save multiple header configurations as rules |
| **Domain binding** | Bind rules to a domain (case-insensitive, path ignored) |
| **Global rules** | Empty Match URL → applies to all requests |
| **URL tags** | Click the current page's domain to auto-fill the Match URL |
| **Per-rule switches** | Enable/disable each rule independently; master switch stops everything |
| **Presets** | Quick-add common headers: Mobile UA, Bot UA, Referer, XFF |
| **Any tab** | Rules are global — no tab isolation, no per-tab toggling |
| **Session rules** | `declarativeNetRequest` session rules — auto-clear on restart, auto-re-apply on browser start |
| **Import / Export** | JSON backup and restore of all rules |

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
| Rules | 5 max | Unlimited |
| Headers per rule | 5 max | Unlimited |
| Domain matching | ✅ | ✅ |
| Global rules (empty URL) | ✅ | ✅ |
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

- ✅ All rules stored in `chrome.storage.local` — **no data is uploaded to any server**
- ✅ Session rules auto-clear on browser restart and re-apply automatically on browser start
- ✅ No analytics, no tracking, no cookies
- ✅ Some headers (Host, Origin) are browser-protected and cannot be modified
- ✅ For development and debugging purposes only

### Permissions

| Permission | Reason |
|------------|--------|
| `storage` | Save header rules and settings locally |
| `activeTab` | Access the current tab (e.g. to read its URL in the side panel) |
| `sidePanel` | Display the extension UI in a side panel |
| `declarativeNetRequestWithHostAccess` | Modify HTTP request headers |
| `tabs` | Read the active tab's URL for the domain tag feature |

- [Full Privacy Policy](https://annmax1983.github.io/vkt-header/privacy-policy.html)

---

## FAQ

1. **Headers don't take effect after enabling a rule?**
   Try refreshing the page. DNR session rules apply to new requests, not already-loaded resources.

2. **Rules disappear after restarting the browser?**
   Session rules are cleared on restart by design, and vkt-header automatically re-applies all enabled rules when the browser starts.

3. **Some headers can't be modified?**
   Browser-protected headers (Host, Origin, etc.) cannot be modified by extensions. This is a browser security restriction, not a bug.

4. **How do I transfer rules to another device?**
   Open Settings → Export to download a JSON backup, then Import it on the other device.

5. **The homepage / first navigation doesn't show the header?**
   DNR rules don't apply to requests served from the browser cache. After enabling a rule, hard-refresh the page (Ctrl+Shift+R) or reopen it — the navigation request will then carry the header. Cached sub-resources behave the same way.

---

## Copyright Disclaimer

1. This extension modifies HTTP request headers for development and debugging purposes only. All content and services of accessed websites belong to their respective owners.
2. Users shall not use this extension to bypass website security restrictions, access unauthorized content, or engage in any illegal activities.
3. Users shall comply with local laws and platform service terms when using this extension.

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
