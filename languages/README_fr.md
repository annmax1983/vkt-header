# vkt-header
[English](../README.md) | [中文](README_zh.md) | [Español](README_es.md) | [Deutsch](README_de.md) | [日本語](README_ja.md) | Français

Modificateur d'en-têtes HTTP isolé par onglet avec URL matching pour navigateurs Chromium.

> Chromium · Manifest V3 · Règles de session · Isolation par onglet · URL Matching

---

## Fonctionnalité principale : URL Matching

Chaque profil a un champ **Match URL**. À l'ouverture du panneau latéral, les profils correspondants sont détectés automatiquement.

**Priorité de correspondance :**

| Priorité | Profil MatchURL | URL de page | Score |
|---|---|---|---|
| 🥇 Exacte | `https://api.example.com/v1/users` | `https://api.example.com/v1/users` | 1000 |
| 🥈 Préfixe chemin | `https://api.example.com/v1` | `https://api.example.com/v1/users` | 500+ |
| 🥉 Domaine seul | `https://api.example.com/` | `https://api.example.com/v1/users` | 100 |

- Correspondance de domaine **insensible à la casse**
- URLs plus longues/spécifiques = priorité plus élevée
- Barre verte de **suggestion** avec application en un clic

---

## Fonctionnalités

| Fonction | Description |
|---|---|
| 🔧 **set / remove** | Définir ou supprimer des en-têtes |
| ✏️ **Éditeur inline** | Modifier directement dans le panneau latéral |
| 📋 **Système de profils** | Sauvegarder plusieurs configurations |
| 🔗 **Liaison URL** | Lier des profils à des URLs |
| 🏷️ **URL Tags** | Clic sur domaine/chemin pour auto-remplir |
| 🎯 **Suggestion** | Détection automatique des profils |
| ⚡ **Presets** | iPhone, Android, iPad, Googlebot, Referer, XFF |
| 🔒 **Isolation** | Strictement par tabId |
| 🧹 **Règles de session** | Effacées au redémarrage |
| 📥📤 **Import/Export** | Backup JSON |

---

---

## Avis sur le code source

> ⚠️ **Ce dépôt ne publie pas le code source.** Il contient uniquement la documentation d'utilisation, les notes de mise à jour et les ressources d'assistance. L'extension est distribuée exclusivement via le Chrome Web Store. Aucun package d'installation hors ligne ni code source pour les utilisateurs finaux n'est fourni.


## ❤️ Soutien

**[👉 Soutenir vkt-header](https://annmax1983.github.io/vkt-header/)**
