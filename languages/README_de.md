# vkt-header

[English](../README.md) | [中文](README_zh.md) | [Español](README_es.md) | Deutsch | [日本語](README_ja.md) | [Français](README_fr.md)

Globaler HTTP-Request-Header-Modifier für Chromium-Browser. Regeln werden nur nach **Domain** gematcht (Groß-/Kleinschreibung irrelevant, Pfad ignoriert) und gelten für **jeden Tab** — es gibt keine Tab-Isolation und keinen Zustand pro Tab.

> Chromium · Manifest V3 · Session Rules · Domain-Matching · Global

---

## Warum vkt-header?

Die meisten Header-Modifier ändern Header global oder erfordern umständlichen Zustand pro Tab. vkt-header hält es einfach: Eine Regel wird nach der **Domain** der angeforderten URL gematcht und gilt überall, in jedem Tab, sobald sie aktiviert ist.

| Vorteil | Details |
|---------|---------|
| 🌐 **Domain-Matching** | Regeln matchen nur die Domain, Groß-/Kleinschreibung irrelevant. Pfade werden ignoriert. |
| 🔗 **Jeder Tab** | Eine Regel gilt in jedem Tab — nichts ist an einen bestimmten Tab gebunden. |
| 🌍 **Globale Regeln** | Match-URL leer lassen und die Regel gilt für **alle Anfragen**. |
| 🧹 **Auto-Neuanwendung** | Session Rules verschwinden beim Browser-Neustart; vkt-header wendet alle aktivierten Regeln beim Browser-Start automatisch wieder an. |
| ⚡ **Inline-Editing** | Header direkt im Side Panel hinzufügen/bearbeiten. Kein separater Editor. |
| 🎯 **Voreinstellungen** | Ein-Klick-Presets: iPhone, Android, iPad, Googlebot, Referer, X-Forwarded-For. |

---

## Kernfunktion: Domain-Matching

Jede Regel hat ein **Match-URL**-Feld, aber nur der **Domain**-Teil wird verwendet:

- Matching ist **groß-/kleinschreibungsunabhängig** (`EXAMPLE.COM` = `example.com`)
- Pfade werden ignoriert (`https://example.com/api` verhält sich genau wie `example.com`)
- Ein führendes `www.` ist optional — `https://www.cnblogs.com/` und `https://cnblogs.com/` matchen dieselbe Regel
- Andere Subdomains (`pic.cnblogs.com`, `blog.cnblogs.com`, …) werden **nicht** gematcht
- Optionaler **Subdomains einschließen**-Schalter: wenn aktiviert, matcht `example.com` auch jede Subdomain (`pic.example.com`, `api.example.com`, …)
- Die Regel gilt in **jedem Tab**, für jede Anfrage deren Domain matched
- **Leere Match-URL** = die Regel gilt für **alle Anfragen**

| Was du eingibst | Effektive Domain | Gilt für |
|---|---|---|
| `example.com` | example.com | example.com und www.example.com, jeder Pfad |
| `HTTPS://EXAMPLE.COM/api` | example.com | gleich — Pfad wird ignoriert |
| `https://www.cnblogs.com/` | cnblogs.com | cnblogs.com und www.cnblogs.com |
| `pic.cnblogs.com` | pic.cnblogs.com | nur pic.cnblogs.com und www.pic.cnblogs.com |
| *(leer)* | — | **alle Anfragen** |

Aktiviere eine Regel mit dem Schalter im Side Panel. Der Hauptschalter oben stoppt oder setzt alle Regeln gleichzeitig fort.

---

## Funktionen

| Funktion | Beschreibung |
|----------|--------------|
| **Header setzen / anhängen / entfernen** | Überschreiben, anhängen (Cookie, X-Forwarded-For…) oder beliebigen Header löschen |
| **Request- & Response-Header** | Request-Header und Response-Header unabhängig pro Regel bearbeiten |
| **Inline-Editor** | Header direkt im Side Panel bearbeiten — kein Popup/Panel-Wechsel |
| **Regelsystem** | Mehrere Header-Konfigurationen als Regeln speichern |
| **Domain-Bindung** | Regeln an eine Domain binden (groß-/kleinschreibungsunabhängig, Pfad ignoriert) |
| **Subdomains einschließen** | Optionaler Schalter: jede Subdomain matchen (`*.example.com`) |
| **Methodenfilter** | Eine Regel auf eine HTTP-Methode beschränken (GET, POST, …) oder offen lassen |
| **Globale Regeln** | Leere Match-URL → gilt für alle Anfragen |
| **URL-Tags** | Auf die Domain der aktuellen Seite klicken, um die Match-URL automatisch auszufüllen |
| **Regelschalter** | Jede Regel unabhängig aktivieren/deaktivieren; Hauptschalter stoppt alles |
| **Voreinstellungen** | Schnell hinzufügen: Mobile UA, Bot UA, Referer, XFF |
| **Jeder Tab** | Regeln sind global — keine Tab-Isolation, kein Umschalten pro Tab |
| **Session Rules** | `declarativeNetRequest` Session Rules — werden beim Neustart automatisch gelöscht und beim Browser-Start wieder angewendet |
| **Import / Export** | JSON-Backup und Wiederherstellung aller Regeln *(Premium)* |

---

## Anwendungsfälle

| Szenario | Vorgehensweise |
|----------|---------------|
| **Mobile Tests** | iPhone/Android/iPad UA-Preset anwenden, um mobile Geräte zu simulieren |
| **API-Debugging** | Authorization, X-Custom-Header für REST/GraphQL-Anfragen setzen |
| **Referer-Tests** | Referer-Header ändern, um Hotlink-Schutz zu testen |
| **Geo-Tests** | X-Forwarded-For setzen, um verschiedene Client-IPs zu simulieren |
| **CORS-Tests** | Origin-Header ändern, um Cross-Origin-Richtlinien zu testen |
| **Bot-Simulation** | Googlebot UA anwenden, um zu sehen, wie Seiten auf Crawler reagieren |

---

## Kostenlos vs. Premium

| | Kostenlos | Premium |
|---|---|---|
| Regeln | max. 5 | Unbegrenzt |
| Header pro Regel | max. 5 | Unbegrenzt |
| Domain-Matching | ✅ | ✅ |
| Globale Regeln (leere URL) | ✅ | ✅ |
| Import / Export | ❌ Nur Premium | ✅ |
| Voreinstellungen | ✅ | ✅ |

---

## Vorschau

<p align="center">
  <img src="screenshot/preview.png" alt="vkt-header Vorschau" width="640">
</p>

---

## Unterstützte Browser

| Browser | Status | Mindestversion |
|---------|--------|----------------|
| Google Chrome | ✅ Vollständig unterstützt | Chrome 114+ (SidePanel API) |
| Microsoft Edge | ✅ Vollständig unterstützt | Edge 114+ |
| Andere Chromium-basierte Browser | ⚠️ Grundlegend kompatibel | Muss SidePanel API unterstützen |

---

## Installation

Zu deiner Sicherheit: Installiere vkt-header ausschließlich über offizielle Browser-Erweiterungsstores:

1. Öffne den **Chrome Web Store** oder **Microsoft Edge Add-ons**
2. Suche: `vkt-header`
3. Klicke auf **„Zu Chrome hinzufügen"** / **„Zu Edge hinzufügen"**
4. Klicke auf das 🔧 vkt-header-Symbol in deiner Toolbar, um das Side Panel zu öffnen

> ⚠️ Nicht von Drittanbieter-Websites installieren. Nicht autorisierte Versionen können deine Datensicherheit gefährden.

---

## Datenschutz

vkt-header folgt den Prinzipien von Privacy-by-Design:

- ✅ Alle Regeln in `chrome.storage.local` gespeichert — **keine Daten werden auf einen Server hochgeladen**
- ✅ Session Rules werden beim Browser-Neustart automatisch gelöscht und beim Browser-Start wieder angewendet
- ✅ Keine Analytik, kein Tracking, keine Cookies
- ✅ Einige Header (Host, Origin) sind browser-geschützt und können nicht verändert werden
- ✅ Nur für Entwicklungs- und Debugging-Zwecke

### Berechtigungen

| Berechtigung | Grund |
|--------------|-------|
| `storage` | Header-Regeln und Einstellungen lokal speichern |
| `activeTab` | Zugriff auf den aktuellen Tab (z.B. zum Lesen der URL im Side Panel) |
| `sidePanel` | Erweiterungs-UI im Side Panel anzeigen |
| `declarativeNetRequestWithHostAccess` | HTTP-Request-Header modifizieren |
| `tabs` | URL des aktiven Tabs für die Domain-Tag-Funktion lesen |

- [Vollständige Datenschutzerklärung](https://annmax1983.github.io/vkt-header/privacy-policy.html)

---

## FAQ

1. **Header greifen nicht nach Aktivierung einer Regel?**
   Versuche die Seite zu aktualisieren. DNR Session Rules gelten für neue Anfragen, nicht für bereits geladene Ressourcen.

2. **Regeln verschwinden nach Browser-Neustart?**
   Session Rules werden beim Neustart designbedingt gelöscht, und vkt-header wendet alle aktivierten Regeln beim Browser-Start automatisch wieder an.

3. **Manche Header können nicht verändert werden?**
   Browser-geschützte Header (Host, Origin usw.) können von Erweiterungen nicht verändert werden. Das ist eine Browser-Sicherheitsbeschränkung, kein Bug.

4. **Wie übertrage ich Regeln auf ein anderes Gerät?**
   Einstellungen → Exportieren, um ein JSON-Backup herunterzuladen, dann auf dem anderen Gerät importieren.

5. **Die Startseite / erste Navigation zeigt den Header nicht?**
   DNR-Regeln gelten nicht für Anfragen aus dem Browser-Cache. Nach Aktivierung einer Regel die Seite hard-refreshen (Strg+Umschalt+R) oder erneut öffnen — die Navigationsanfrage trägt dann den Header. Cached Sub-Ressourcen verhalten sich ebenso.

6. **Header fehlen direkt nach dem Browser-Start?**
   Der Service Worker wacht träge auf: Die allerersten Anfragen können abgehen, bevor vkt-header seine Session Rules wieder angewendet hat. Erneut versuchen oder aktualisieren — jede folgende Navigation trägt die Header. Dies betrifft nur die ersten Momente nach dem Browser-Start, nicht das normale Browsen.

---

## Urheberrechtshinweis

1. Diese Erweiterung modifiziert HTTP-Request-Header ausschließlich für Entwicklungs- und Debugging-Zwecke. Alle Inhalte und Dienste der besuchten Websites gehören deren jeweiligen Eigentümern.
2. Nutzer dürfen diese Erweiterung nicht verwenden, um Website-Sicherheitsbeschränkungen zu umgehen, nicht autorisierte Inhalte zu erreichen oder rechtswidrige Handlungen durchzuführen.
3. Nutzer haben bei der Verwendung dieser Erweiterung lokale Gesetze und Plattform-Nutzungsbedingungen einzuhalten.

---

## Quellcode-Hinweis

> ⚠️ **Dieses Repository veröffentlicht keinen Quellcode.** Es enthält nur Nutzerdokumentation, Versionshinweise und Support-Ressourcen. Die Erweiterung wird ausschließlich über den Chrome Web Store vertrieben. Es werden keine Offline-Installationspakete oder Endbenutzer-Quellcodes bereitgestellt.

---

## Lizenz

Copyright © 2026 vkt-header. Alle Rechte vorbehalten.

Diese Software ist Closed-Source-Proprietärsoftware. Ohne offizielle schriftliche Genehmigung ist Folgendes strengstens untersagt:
- Dekompilieren, Knacken oder Modifizieren des Programmcodes
- Umpacken, Weiterverbreitung, Weitergabe oder kommerzieller Wiederverkauf
- Einbetten des Programms in andere Software zur gebündelten Distribution

---

## ❤️ Support

Wenn dir vkt-header hilft, kannst du dem Entwickler gerne einen Kaffee ausgeben!

**[👉 Hier unterstützen](https://ko-fi.com/annmax?buyACoffee=true&ref=vkt-header)**
