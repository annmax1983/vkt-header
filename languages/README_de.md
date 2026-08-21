# vkt-header
[English](../README.md) | [中文](README_zh.md) | [Español](README_es.md) | Deutsch | [日本語](README_ja.md) | [Français](README_fr.md)

Tab-isolierter HTTP-Header-Modifier mit URL-Matching für Chromium-Browser.

> Chromium · Manifest V3 · Session-Regeln · Tab-Isolierung · URL-Matching

---

## Kernfunktion: URL-Matching

Jedes Profil hat ein **Match-URL**-Feld. Beim Öffnen der Seitenleiste werden passende Profile automatisch erkannt.

**Match-Priorität:**

| Priorität | Profil MatchURL | Seiten-URL | Score |
|---|---|---|---|
| 🥇 Exakt | `https://api.example.com/v1/users` | `https://api.example.com/v1/users` | 1000 |
| 🥈 Pfad-Präfix | `https://api.example.com/v1` | `https://api.example.com/v1/users` | 500+ |
| 🥉 Nur Domain | `https://api.example.com/` | `https://api.example.com/v1/users` | 100 |

- Domain-Matching **ohne Berücksichtigung von Groß-/Kleinschreibung**
- Längere/spezifischere URLs haben höhere Priorität
- Grüner **Match-Hinweis** mit One-Click-Anwendung

---

## Funktionen

| Funktion | Beschreibung |
|---|---|
| 🔧 **set / remove** | Header setzen/überschreiben oder entfernen |
| ✏️ **Inline-Editor** | Direkt in der Seitenleiste bearbeiten |
| 📋 **Profil-System** | Mehrere Header-Konfigurationen speichern |
| 🔗 **URL-Bindung** | Profile an URLs binden |
| 🏷️ **URL-Tags** | Klickbare Domain/Path-Auswahl |
| 🎯 **Match-Hinweis** | Automatische Profil-Erkennung |
| ⚡ **Presets** | iPhone, Android, iPad, Googlebot, Referer, XFF |
| 🔒 **Tab-Isolierung** | Streng an tabId gebunden |
| 🧹 **Session-Regeln** | Beim Browser-Neustart gelöscht |
| 📥📤 **Import/Export** | JSON-Backup |

---

---

## Hinweis zum Quellcode

> ⚠️ **Dieses Repository veröffentlicht keinen Quellcode.** Es enthält nur Nutzerdokumentation, Versionshinweise und Support-Ressourcen. Die Erweiterung wird ausschließlich über den Chrome Web Store vertrieben. Es werden keine Offline-Installationspakete oder Quellcodes für Endbenutzer bereitgestellt.


## ❤️ Unterstützung

**[👉 vkt-header unterstützen](https://annmax1983.github.io/vkt-header/)**
