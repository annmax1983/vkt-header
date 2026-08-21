# vkt-header
[English](../README.md) | [中文](README_zh.md) | [Español](README_es.md) | [Deutsch](README_de.md) | 日本語 | [Français](README_fr.md)

タブ分離型 HTTPリクエストヘッダー変更ツール。タブ単位でヘッダー変更、URLマッチング対応。

> Chromium · Manifest V3 · セッションルール · タブ分離 · URLマッチング

---

## コア機能：URLマッチング

各プロフィールに **Match URL** を設定。サイドパネル開時に現在ページのマッチするプロフィールを自動検出。

**マッチ優先度：**

| 優先度 | プロフィール MatchURL | ページURL | スコア |
|---|---|---|---|
| 🥇 完全一致 | `https://api.example.com/v1/users` | `https://api.example.com/v1/users` | 1000 |
| 🥈 パス前方一致 | `https://api.example.com/v1` | `https://api.example.com/v1/users` | 500+ |
| 🥉 ドメイン一致 | `https://api.example.com/` | `https://api.example.com/v1/users` | 100 |

- ドメインは**大文字小文字区別なし**
- URLが長いほど優先度が高い
- マッチ時に緑色のヒントバー表示、ワンクリック適用

---

## 機能

| 機能 | 説明 |
|---|---|
| 🔧 **set / remove** | ヘッダーの上書き/追加と削除 |
| ✏️ **インライン編集** | サイドパネルで直接編集 |
| 📋 **プロフィール** | 複数のヘッダー設定を保存 |
| 🔗 **URLバインド** | プロフィールにURLをバインド |
| 🏷️ **URLタグ** | 現在のドメイン/パスをクリックで自動入力 |
| 🎯 **マッチヒント** | マッチするプロフィールを自動検出 |
| ⚡ **プリセット** | iPhone、Android、iPad、Googlebot、Referer、XFF |
| 🔒 **タブ分離** | tabIdに厳密にバインド |
| 🧹 **セッションルール** | ブラウザ再起動で自動消去 |
| 📥📤 **インポート/エクスポート** | JSONバックアップ |

---

---

## ソースコードについて

> ⚠️ **このリポジトリではソースコードは公開していません。** 使用方法のドキュメント、リリースノート、サポート情報のみを含みます。拡張機能はChrome Web Storeを通じてのみ配布されます。オフラインインストールパッケージやエンドユーザー向けソースコードは提供されません。


## ❤️ サポート

**[👉 vkt-headerをサポート](https://annmax1983.github.io/vkt-header/)**
