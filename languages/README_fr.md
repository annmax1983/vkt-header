# vkt-header

[English](../README.md) | [中文](README_zh.md) | [Español](README_es.md) | [Deutsch](README_de.md) | [日本語](README_ja.md) | Français

Modificateur global d'en-têtes de requêtes HTTP pour navigateurs Chromium. Les règles sont matchées par **domaine uniquement** (insensible à la casse, le chemin est ignoré) et s'appliquent à **chaque onglet** — il n'y a pas d'isolation par onglet ni d'état par onglet.

> Chromium · Manifest V3 · Session Rules · Correspondance par domaine · Global

---

## Pourquoi vkt-header ?

La plupart des modificateurs d'en-têtes changent les en-têtes globalement, ou nécessitent une gestion fastidieuse par onglet. vkt-header garde les choses simples : une règle est matchée par le **domaine** de l'URL demandée et s'applique partout, dans chaque onglet, dès qu'elle est activée.

| Avantage | Détail |
|-----------|--------|
| 🌐 **Correspondance par domaine** | Les règles matchent le domaine uniquement, insensiblement à la casse. Les chemins sont ignorés. |
| 🔗 **Tout onglet** | Une règle s'applique dans chaque onglet — rien n'est lié à un onglet spécifique. |
| 🌍 **Règles globales** | Laissez l'URL de correspondance vide et la règle s'applique à **toutes les requêtes**. |
| 🧹 **Réapplication automatique** | Les session rules disparaissent au redémarrage du navigateur ; vkt-header réapplique toutes les règles activées automatiquement au démarrage. |
| ⚡ **Édition en ligne** | Ajoutez/modifiez les en-têtes directement dans le panneau latéral. Pas d'éditeur séparé. |
| 🎯 **Préréglages** | Préréglages en un clic : iPhone, Android, iPad, Googlebot, Referer, X-Forwarded-For. |

---

## Fonctionnalité principale : correspondance par domaine

Chaque règle possède un champ **URL de correspondance**, mais seul le **domaine** est utilisé :

- La correspondance est **insensible à la casse** (`EXAMPLE.COM` = `example.com`)
- Les chemins sont ignorés (`https://example.com/api` se comporte exactement comme `example.com`)
- Le `www.` initial est optionnel — `https://www.cnblogs.com/` et `https://cnblogs.com/` matchent la même règle
- Les autres sous-domaines (`pic.cnblogs.com`, `blog.cnblogs.com`, …) ne matchent **pas**
- Bascule optionnelle **Inclure les sous-domaines** : quand activée, `example.com` matche aussi chaque sous-domaine (`pic.example.com`, `api.example.com`, …)
- La règle s'applique dans **chaque onglet**, pour toute requête dont le domaine correspond
- **URL de correspondance vide** = la règle s'applique à **toutes les requêtes**

| Ce que vous saisissez | Domaine effectif | S'applique à |
|---|---|---|
| `example.com` | example.com | example.com et www.example.com, tout chemin |
| `HTTPS://EXAMPLE.COM/api` | example.com | idem — le chemin est ignoré |
| `https://www.cnblogs.com/` | cnblogs.com | cnblogs.com et www.cnblogs.com |
| `pic.cnblogs.com` | pic.cnblogs.com | pic.cnblogs.com et www.pic.cnblogs.com uniquement |
| *(vide)* | — | **toutes les requêtes** |

Activez une règle avec son commutateur dans le panneau latéral. Le commutateur principal en haut arrête ou reprend toutes les règles d'un coup.

---

## Fonctionnalités

| Fonctionnalité | Description |
|---------|-------------|
| **Définir / Ajouter / Supprimer des en-têtes** | Écrasez, ajoutez à (Cookie, X-Forwarded-For…) ou supprimez n'importe quel en-tête |
| **En-têtes de requête et de réponse** | Modifiez les en-têtes de requête et de réponse indépendamment par règle |
| **Éditeur en ligne** | Modifiez les en-têtes directement dans le panneau latéral — pas de bascule popup/panneau |
| **Système de règles** | Enregistrez plusieurs configurations d'en-têtes sous forme de règles |
| **Liaison par domaine** | Liez les règles à un domaine (insensible à la casse, chemin ignoré) |
| **Inclure les sous-domaines** | Bascule optionnelle : matche chaque sous-domaine (`*.example.com`) |
| **Filtre par méthode** | Limitez une règle à une méthode HTTP (GET, POST, …) ou laissez-la ouverte |
| **Règles globales** | URL de correspondance vide → s'applique à toutes les requêtes |
| **Tags d'URL** | Cliquez sur le domaine de la page courante pour remplir automatiquement l'URL de correspondance |
| **Commutateurs par règle** | Activez/désactivez chaque règle indépendamment ; le commutateur principal arrête tout |
| **Préréglages** | Ajout rapide d'en-têtes courants : UA mobile, UA bot, Referer, XFF |
| **Tout onglet** | Les règles sont globales — pas d'isolation par onglet, pas de bascule par onglet |
| **Session rules** | Règles de session `declarativeNetRequest` — effacement auto au redémarrage, réapplication auto au démarrage |
| **Import / Export** | Sauvegarde et restauration JSON de toutes les règles *(Premium)* |

---

## Cas d'utilisation

| Scénario | Comment |
|----------|-----|
| **Test mobile** | Appliquez le préréglage UA iPhone/Android/iPad pour simuler des appareils mobiles |
| **Débogage API** | Définissez Authorization, X-Custom-Header pour les requêtes REST/GraphQL |
| **Test de Referer** | Modifiez l'en-tête Referer pour tester la protection anti-hotlink |
| **Test géographique** | Définissez X-Forwarded-For pour simuler différentes IP client |
| **Test CORS** | Modifiez l'en-tête Origin pour tester les politiques cross-origin |
| **Simulation de bot** | Appliquez le UA Googlebot pour voir comment les sites répondent aux crawlers |

---

## Gratuit vs Premium

| | Gratuit | Premium |
|---|---|---|
| Règles | 5 max | Illimité |
| En-têtes par règle | 5 max | Illimité |
| Correspondance par domaine | ✅ | ✅ |
| Règles globales (URL vide) | ✅ | ✅ |
| Import / Export | ❌ Premium uniquement | ✅ |
| Préréglages | ✅ | ✅ |

---

## Aperçu

<p align="center">
  <img src="screenshot/preview.png" alt="Aperçu vkt-header" width="640">
</p>

---

## Navigateurs compatibles

| Navigateur | Statut | Version minimum |
|---------|--------|------------------|
| Google Chrome | ✅ Entièrement pris en charge | Chrome 114+ (API SidePanel) |
| Microsoft Edge | ✅ Entièrement pris en charge | Edge 114+ |
| Autres navigateurs basés sur Chromium | ⚠️ Compatibilité de base | Doit supporter l'API SidePanel |

---

## Installation

Pour votre sécurité, n'installez vkt-header que via les boutiques officielles d'extensions :

1. Ouvrez le **Chrome Web Store** ou **Microsoft Edge Add-ons**
2. Recherchez : `vkt-header`
3. Cliquez sur **« Ajouter à Chrome »** / **« Ajouter à Edge »**
4. Cliquez sur l'icône 🔧 vkt-header dans votre barre d'outils pour ouvrir le panneau latéral

> ⚠️ N'installez pas depuis des sites tiers. Les versions non autorisées peuvent compromettre la sécurité de vos données.

---

## Confidentialité

vkt-header respecte les principes de confidentialité dès la conception :

- ✅ Toutes les règles stockées dans `chrome.storage.local` — **aucune donnée n'est envoyée à un serveur**
- ✅ Les session rules s'effacent automatiquement au redémarrage et se réappliquent au démarrage
- ✅ Pas d'analytics, pas de suivi, pas de cookies
- ✅ Certains en-têtes (Host, Origin) sont protégés par le navigateur et ne peuvent pas être modifiés
- ✅ Uniquement à des fins de développement et de débogage

### Permissions

| Permission | Raison |
|------------|--------|
| `storage` | Sauvegarder les règles d'en-têtes et les paramètres en local |
| `activeTab` | Accéder à l'onglet actif (ex. pour lire son URL dans le panneau latéral) |
| `sidePanel` | Afficher l'interface de l'extension dans un panneau latéral |
| `declarativeNetRequestWithHostAccess` | Modifier les en-têtes de requêtes HTTP |
| `tabs` | Lire l'URL de l'onglet actif pour la fonctionnalité de tag de domaine |

- [Politique de confidentialité complète](https://annmax1983.github.io/vkt-header/privacy-policy.html)

---

## FAQ

1. **Les en-têtes ne s'appliquent pas après l'activation d'une règle ?**
   Essayez de rafraîchir la page. Les session rules DNR s'appliquent aux nouvelles requêtes, pas aux ressources déjà chargées.

2. **Les règles disparaissent après le redémarrage du navigateur ?**
   Les session rules sont effacées au redémarrage par conception, et vkt-header réapplique automatiquement toutes les règles activées au démarrage.

3. **Certains en-têtes ne peuvent pas être modifiés ?**
   Les en-têtes protégés par le navigateur (Host, Origin, etc.) ne peuvent pas être modifiés par les extensions. C'est une restriction de sécurité du navigateur, pas un bug.

4. **Comment transférer des règles vers un autre appareil ?**
   Ouvrez les Paramètres → Exporter pour télécharger une sauvegarde JSON, puis importez-la sur l'autre appareil.

5. **La page d'accueil / la première navigation n'affiche pas l'en-tête ?**
   Les règles DNR ne s'appliquent pas aux requêtes servies depuis le cache du navigateur. Après avoir activé une règle, forcez le rafraîchissement (Ctrl+Shift+R) ou rouvrez la page — la requête de navigation portera alors l'en-tête. Les sous-ressources en cache se comportent de la même façon.

6. **En-têtes manquants juste après le démarrage du navigateur ?**
   Le service worker se réveille paresseusement : les toutes premières requêtes peuvent se déclencher avant que vkt-header ait réappliqué ses session rules. Réessayez ou rafraîchissez — chaque navigation suivante portera les en-têtes. Cela n'affecte que les premiers instants après le démarrage, pas la navigation normale.

---

## Avertissement relatif au droit d'auteur

1. Cette extension modifie les en-têtes de requêtes HTTP uniquement à des fins de développement et de débogage. Tous les contenus et services des sites web consultés appartiennent à leurs propriétaires respectifs.
2. Les utilisateurs ne doivent pas utiliser cette extension pour contourner les restrictions de sécurité des sites web, accéder à du contenu non autorisé ou se livrer à des activités illégales.
3. Les utilisateurs doivent se conformer aux lois locales et aux conditions d'utilisation des plateformes lors de l'utilisation de cette extension.

---

## Avis sur le code source

> ⚠️ **Ce dépôt ne publie pas le code source.** Il contient uniquement la documentation d'utilisation, les notes de version et les ressources d'assistance. L'extension est distribuée exclusivement via le Chrome Web Store. Aucun package d'installation hors ligne ni code source destiné aux utilisateurs finaux n'est fourni.

---

## Licence

Copyright © 2026 vkt-header. Tous droits réservés.

Ce logiciel est un logiciel propriétaire fermé. Sans autorisation écrite officielle, les actions suivantes sont strictement interdites :
- Décompiler, cracker ou modifier le code du programme
- Reconditionner, redistribuer, partager ou revendre commercialement
- Intégrer le programme dans d'autres logiciels pour une distribution groupée

---

## ❤️ Soutenir

Si vkt-header vous est utile, offrez un café au développeur !

**[👉 Cliquez ici pour soutenir](https://ko-fi.com/annmax?buyACoffee=true&ref=vkt-header)**
