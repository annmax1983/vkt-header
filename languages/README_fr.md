# vkt-header
[English](../README.md) | [中文](README_zh.md) | [Español](README_es.md) | [Deutsch](README_de.md) | [日本語](README_ja.md) | Français

Modificateur global d'en-têtes HTTP pour navigateurs Chromium. Les règles correspondent uniquement au **domaine** (insensible à la casse, chemins ignorés) et s'appliquent dans **chaque onglet** — pas d'isolation par onglet ni d'état par onglet.

> Chromium · Manifest V3 · Règles de session · Correspondance par domaine · Global

---

## Fonctionnalité principale : correspondance par domaine

Chaque règle a un champ **Match URL**, mais seule la partie **domaine** est utilisée :

- Correspondance **insensible à la casse** (`EXAMPLE.COM` = `example.com`)
- Les chemins sont ignorés (`https://example.com/api` se comporte comme `example.com`)
- Le `www.` initial est optionnel — `https://www.cnblogs.com/` et `https://cnblogs.com/` correspondent à la même règle
- Les autres sous-domaines (`pic.cnblogs.com`, `blog.cnblogs.com`, …) ne correspondent **pas**
- La règle s'applique dans **chaque onglet** à toute requête dont le domaine correspond
- **Match URL vide** = la règle s'applique à **toutes les requêtes**

| Ce que vous saisissez | Domaine effectif | S'applique à |
|---|---|---|
| `example.com` | example.com | toutes les requêtes vers example.com, tout chemin |
| `HTTPS://EXAMPLE.COM/api` | example.com | identique — le chemin est ignoré |
| *(vide)* | — | **toutes les requêtes** |

Activez chaque règle avec son interrupteur dans le panneau latéral. L'interrupteur principal arrête ou reprend toutes les règles.

---

## Fonctionnalités

| Fonction | Description |
|---|---|
| 🔧 **set / remove** | Définir ou supprimer des en-têtes |
| ✏️ **Éditeur inline** | Modifier directement dans le panneau latéral |
| 📋 **Système de règles** | Sauvegarder plusieurs configurations |
| 🌐 **Liaison par domaine** | Lier des règles à des domaines (sans casse, chemins ignorés) |
| 🌍 **Règles globales** | Match URL vide → s'applique à toutes les requêtes |
| 🏷️ **Étiquettes de domaine** | Clic sur le domaine actuel pour auto-remplir |
| 🔘 **Interrupteurs** | Activer/désactiver chaque règle ; l'interrupteur principal arrête tout |
| 🔗 **Chaque onglet** | Règles globales — pas d'isolation par onglet |
| 🧹 **Règles de session** | Effacées au redémarrage et réappliquées au démarrage |
| 📥📤 **Import/Export** | Backup JSON |

---

## Avis sur le code source

> ⚠️ **Ce dépôt ne publie pas le code source.** Il contient uniquement la documentation d'utilisation, les notes de mise à jour et les ressources d'assistance. L'extension est distribuée exclusivement via le Chrome Web Store. Aucun package d'installation hors ligne ni code source pour les utilisateurs finaux n'est fourni.


## ❤️ Soutien

**[👉 Soutenir vkt-header](https://annmax1983.github.io/vkt-header/)**
