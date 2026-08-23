# vkt-header
[English](../README.md) | [中文](README_zh.md) | [Español](README_es.md) | Deutsch | [日本語](README_ja.md) | [Français](README_fr.md)

Globaler HTTP-Header-Modifier für Chromium-Browser. Regeln werden nur nach **Domain** abgeglichen (ohne Groß-/Kleinschreibung, Pfade werden ignoriert) und gelten in **jedem Tab** — keine Tab-Isolierung, kein tab-abhängiger Zustand.

> Chromium · Manifest V3 · Session-Regeln · Domain-Matching · Global

---

## Kernfunktion: Domain-Matching

Jede Regel hat ein **Match-URL**-Feld, aber nur der **Domain-Teil** wird verwendet:

- Abgleich **ohne Berücksichtigung von Groß-/Kleinschreibung** (`EXAMPLE.COM` = `example.com`)
- Pfade werden ignoriert (`https://example.com/api` verhält sich wie `example.com`)
- Ein führendes `www.` ist optional — `https://www.cnblogs.com/` und `https://cnblogs.com/` matchen dieselbe Regel
- Andere Subdomains (`pic.cnblogs.com`, `blog.cnblogs.com`, …) matchen **nicht**
- Die Regel gilt in **jedem Tab** für alle Anfragen mit passender Domain
- **Leeres Match-URL** = die Regel gilt für **alle Anfragen**

| Eingabe | Effektive Domain | Gilt für |
|---|---|---|
| `example.com` | example.com | alle Anfragen an example.com, jeder Pfad |
| `HTTPS://EXAMPLE.COM/api` | example.com | gleich — Pfad wird ignoriert |
| *(leer)* | — | **alle Anfragen** |

Aktivieren Sie jede Regel über ihren Schalter im Seitenpanel. Der Hauptschalter oben stoppt bzw. setzt alle Regeln fort.

---

## Funktionen

| Funktion | Beschreibung |
|---|---|
| 🔧 **set / remove** | Header setzen/überschreiben oder entfernen |
| ✏️ **Inline-Editor** | Direkt in der Seitenleiste bearbeiten |
| 📋 **Regel-System** | Mehrere Header-Konfigurationen speichern |
| 🌐 **Domain-Bindung** | Regeln an Domains binden (ohne Groß-/Kleinschreibung, Pfade ignoriert) |
| 🌍 **Globale Regeln** | Leeres Match-URL → gilt für alle Anfragen |
| 🏷️ **Domain-Tags** | Klick auf die aktuelle Domain zum Auto-Ausfüllen |
| 🔘 **Regel-Schalter** | Jede Regel einzeln aktivieren/deaktivieren; Hauptschalter stoppt alles |
| 🔗 **Jeder Tab** | Regeln sind global — keine Tab-Isolierung |
| 🧹 **Session-Regeln** | Beim Browser-Neustart gelöscht und beim Start automatisch neu angewendet |
| 📥📤 **Import/Export** | JSON-Backup |

---

## Hinweis zum Quellcode

> ⚠️ **Dieses Repository veröffentlicht keinen Quellcode.** Es enthält nur Nutzerdokumentation, Versionshinweise und Support-Ressourcen. Die Erweiterung wird ausschließlich über den Chrome Web Store vertrieben. Es werden keine Offline-Installationspakete oder Quellcodes für Endbenutzer bereitgestellt.


## ❤️ Unterstützung

**[👉 vkt-header unterstützen](https://annmax1983.github.io/vkt-header/)**
