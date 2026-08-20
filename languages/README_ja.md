# vkt-header
[English](../README.md) | [中文](README_zh.md) | [Español](README_es.md) | [Deutsch](README_de.md) | 日本語 | [Français](README_fr.md)

タブ分離型 HTTPヘッダー変更ツール — フロントエンド・QAテスター向け。

> Chromium · Manifest V3 · セッションルール · タブ分離

---

## 差別化ポイント

| 競合の問題 | vkt-headerの解決策 |
|---|---|
| ❌ グローバル生效、他サイトにも影響 | ✅ 現在のタブに厳密に分離 |
| ❌ タブ閉鎖後ルール残留 | ✅ tabs.onRemovedで自動クリア |
| ❌ テンプレート機能なし | ✅ 複数テンプレート保存・再利用 |
| ❌ データアップロード | ✅ すべてローカル保存 |

---

## 機能

| 機能 | 説明 |
|---|---|
| 🔧 **set / remove** | ヘッダーの上書き/追加と削除 |
| 📋 **テンプレート** | 複数のヘッダー設定を保存 |
| 🔗 **URLバインド** | テンプレートにURLをバインド |
| 🧹 **セッションルール** | ブラウザ再起動で自動消去 |
| 🔒 **タブ分離** | tabIdに厳密にバインド |

---

## ❤️ サポート

**[👉 vkt-headerをサポート](https://annmax1983.github.io/vkt-header/)**
