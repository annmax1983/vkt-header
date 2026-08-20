# vkt-header

English | [中文](languages/README_zh.md) | [Español](languages/README_es.md) | [Deutsch](languages/README_de.md) | [日本語](languages/README_ja.md) | [Français](languages/README_fr.md)

Tab-isolated HTTP header modifier for Chromium browsers. Save header snapshot templates, apply per-tab. Session rules auto-clear on browser close.

> Chromium-based · Manifest V3 · No tracking · Fully Local Processing

## Features

- **Tab isolation** — Header rules only affect the target tab, not global
- **Auto cleanup** — Close a tab or restart browser, all rules vanish
- **Template system** — Save multiple header configs, reuse with one click
- **URL binding** — Optionally bind templates to specific URLs
- **Session rules** — Uses `declarativeNetRequest` session rules (MV3)
- **6 languages** — Auto-detected from browser settings

## Build

```bash
npm install
npm run build
```

Output: `publish/vkt-header-v{version}.zip`
