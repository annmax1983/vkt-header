# vkt-header
[English](../README.md) | 中文 | [Español](README_es.md) | [Deutsch](README_de.md) | [日本語](README_ja.md) | [Français](README_fr.md)

标签页隔离式 HTTP 请求头修改工具。按标签页修改请求头，支持 URL 匹配绑定，关闭自动清除。

> Chromium · Manifest V3 · 会话规则 · 标签页隔离 · URL 匹配

---

## 核心功能：URL 匹配

每个 Profile 可绑定一个 **Match URL**。打开侧边栏时，自动检测当前页面是否有匹配的 Profile。

**匹配优先级（从高到低）：**

| 优先级 | Profile MatchURL | 页面 URL | 分数 |
|---|---|---|---|
| 🥇 精确匹配 | `https://api.example.com/v1/users` | `https://api.example.com/v1/users` | 1000 |
| 🥈 路径前缀 | `https://api.example.com/v1` | `https://api.example.com/v1/users` | 500+ |
| 🥉 域名匹配 | `https://api.example.com/` | `https://api.example.com/v1/users` | 100 |
| ❌ 不匹配 | `https://other.com/` | `https://api.example.com/v1/users` | 0 |

- 域名匹配**忽略大小写**
- URL 越长越精确，优先级越高
- 匹配成功时显示绿色**匹配提示条**，一键应用

---

## 为什么选择 vkt-header？

| 竞品痛点 | vkt-header 方案 |
|---|---|
| ❌ 规则全局生效，切换网站依然篡改 | ✅ 严格绑定当前标签页，不影响其他页面 |
| ❌ 关闭标签页后规则残留 | ✅ 监听 tabs.onRemoved，自动清除 |
| ❌ 需要手动切换配置 | ✅ URL 自动匹配，打开页面即提示 |
| ❌ 数据上传、隐私风险 | ✅ 全部配置存储在浏览器本地 |

---

## 功能特性

| 功能 | 说明 |
|---|---|
| 🔧 **set / remove** | 覆盖新增或移除请求头 |
| ✏️ **内联编辑** | 直接在侧边栏编辑 header，无需弹窗 |
| 📋 **Profile 系统** | 保存多套 header 配置 |
| 🔗 **URL 绑定** | Profile 绑定 URL，自动匹配 |
| 🏷️ **URL 标签** | 点击当前页面域名/路径自动填入 |
| 🎯 **匹配提示** | 打开侧边栏自动检测匹配的 Profile |
| ⚡ **预设** | 一键添加：iPhone、Android、iPad、Googlebot、Referer、XFF |
| 🔒 **标签隔离** | 规则严格绑定 tabId |
| 🧹 **会话规则** | 浏览器重启自动清除 |
| 📥📤 **导入导出** | JSON 备份恢复 |
| 🌍 **6 种语言** | 自动匹配浏览器语言 |

---

## 使用场景

| 场景 | 做法 |
|---|---|
| 移动端测试 | 应用 iPhone/Android/iPad UA 预设 |
| API 调试 | 设置 Authorization、自定义 Header |
| Referer 测试 | 修改 Referer 测试防盗链 |
| IP 模拟 | 设置 X-Forwarded-For |
| CORS 测试 | 修改 Origin 测试跨域策略 |
| 爬虫模拟 | 应用 Googlebot UA |

---

## 免费版 vs 高级版

| | 免费版 | 高级版 |
|---|---|---|
| Profile 数量 | 最多 5 个 | 无限制 |
| 每套 Header 数 | 最多 5 条 | 无限制 |
| URL 匹配 | ✅ | ✅ |
| 标签隔离 | ✅ | ✅ |
| 导入导出 | ✅ | ✅ |
| 预设 | ✅ | ✅ |

---

## 预览

<p align="center">
  <img src="../screenshot/preview.png" alt="vkt-header 预览" width="640">
</p>

---

## 支持的浏览器

| 浏览器 | 状态 | 最低版本 |
|--------|------|----------|
| Google Chrome | ✅ 完全支持 | Chrome 114+（SidePanel API） |
| Microsoft Edge | ✅ 完全支持 | Edge 114+ |
| 其他Chromium浏览器 | ⚠️ 基本兼容 | 需支持SidePanel API |

---

## 安装方式

为安全起见，请仅通过官方浏览器扩展商店安装：

1. 打开 **Chrome Web Store** 或 **Microsoft Edge Add-ons**
2. 搜索：`vkt-header`
3. 点击 **“添加到 Chrome”** / **“添加到 Edge”**
4. 点击工具栏中的 🔧 vkt-header 图标，打开侧边栏

> ⚠️ 请勿从第三方网站安装。未授权版本可能危及数据安全。

---

## 隐私保护

vkt-header 遵循隐私优先原则：

- ✅ 全部配置存储在 `chrome.storage.local` — **不上传任何服务器**
- ✅ 会话规则在浏览器重启后自动清除 — 无持久化修改
- ✅ 无分析追踪、无Cookie
- ✅ 部分请求头（Host、Origin 等）受浏览器保护，无法修改
- ✅ 仅限开发调试使用

### 权限说明

| 权限 | 用途 |
|------|------|
| `storage` | 本地保存请求头模板和设置 |
| `activeTab` | 用户点击应用时访问当前标签页 |
| `sidePanel` | 显示扩展侧边栏界面 |
| `declarativeNetRequestWithHostAccess` | 按标签页修改HTTP请求头 |
| `tabs` | 监听标签页关闭，自动清除规则 |

- [完整隐私条款](https://annmax1983.github.io/vkt-header/privacy-policy.html)

---

## 常见问题

1. **应用请求头后没有生效？**
   请刷新页面。DNR会话规则仅对新请求生效，不影响已加载的资源。

2. **关闭浏览器后规则消失？**
   这是设计行为。vkt-header 仅使用会话规则，浏览器重启自动清除，确保安全。

3. **部分请求头无法修改？**
   浏览器保护的请求头（Host、Origin等）无法被扩展修改，这是浏览器安全限制而非bug。

4. **如何将Profile迁移到其他设备？**
   打开设置 → 导出下载JSON备份，然后在另一台设备上导入。

---

## 版权声明

1. 本扩展仅用于开发调试目的修改HTTP请求头。所访问网站的内容和服务归其所有者所有。
2. 用户不得使用本扩展绕过网站安全限制、访问未授权内容或从事任何违法活动。
3. 用户使用本扩展时应遵守当地法律和平台服务条款。

---

## 源码说明

> ⚠️ **本仓库不公开源代码。** 仅包含使用文档、更新日志和支持资源。扩展仅通过 Chrome Web Store 分发，不提供离线安装包或终端用户源代码。

---

## 许可证

Copyright © 2026 vkt-header. 保留所有权利。

本软件为闭源专有软件。未经官方书面授权，严禁以下行为：
- 反编译、破解或修改程序代码
- 重新打包、再分发、共享或商业转售
- 将程序嵌入其他软件进行捆绑分发

---

## ❤️ 支持

如果你觉得 vkt-header 有帮助，欢迎请开发者喝杯咖啡！

**[👉 点击支持](https://ko-fi.com/annmax?buyACoffee=true&ref=vkt-header)**
