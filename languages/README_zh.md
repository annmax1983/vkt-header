# vkt-header
[English](../README.md) | 中文 | [Español](README_es.md) | [Deutsch](README_de.md) | [日本語](README_ja.md) | [Français](README_fr.md)

按**域名**匹配的全局 HTTP 请求头修改工具。规则只看 URL 的**域名**（忽略大小写、忽略路径），并且对**所有标签页**生效——没有标签页隔离，也不需要按标签页管理状态。

> Chromium · Manifest V3 · 会话规则 · 域名匹配 · 全局生效

---

## 为什么选择 vkt-header？

多数请求头修改器要么全局乱改、要么要求繁琐的按标签页管理。vkt-header 的做法很简单：规则按请求 URL 的**域名**匹配，启用后就在所有标签页生效。

| 优势 | 说明 |
|---|---|
| 🌐 **域名匹配** | 规则只按域名匹配，忽略大小写，忽略路径 |
| 🔗 **任意标签页** | 规则对所有标签页生效，不与任何标签页绑定 |
| 🌍 **全局规则** | Match URL 留空，则该规则对**所有请求**生效 |
| 🧹 **自动恢复** | 浏览器重启后会话规则自动清空，vkt-header 会在浏览器启动时自动重新应用所有已启用规则 |
| ⚡ **内联编辑** | 直接在侧边栏添加/编辑 header，无需单独编辑器 |
| 🎯 **预设** | 一键添加：iPhone、Android、iPad、Googlebot、Referer、X-Forwarded-For |

---

## 核心功能：域名匹配

每条规则有一个 **Match URL** 字段，但匹配时**只使用其中的域名部分**：

- 匹配**忽略大小写**（`EXAMPLE.COM` = `example.com`）
- 路径被忽略（`https://example.com/api` 与 `example.com` 效果完全一样）
- 开头的 `www.` 是可选的——`https://www.cnblogs.com/` 与 `https://cnblogs.com/` 视为同一个规则
- **其它子域名**（`pic.cnblogs.com`、`blog.cnblogs.com` 等）**不会**匹配
- 可选的**包含子域名**开关：勾选后 `example.com` 会同时匹配其所有子域名（`pic.example.com`、`api.example.com` 等）
- 规则在**所有标签页**生效，只要请求的域名匹配
- **Match URL 留空** = 该规则对**所有请求**生效

| 你填写的内容 | 实际生效域名 | 生效范围 |
|---|---|---|
| `example.com` | example.com | example.com 与 www.example.com，任意路径 |
| `HTTPS://EXAMPLE.COM/api` | example.com | 同上——路径被忽略 |
| `https://www.cnblogs.com/` | cnblogs.com | cnblogs.com 与 www.cnblogs.com |
| `pic.cnblogs.com` | pic.cnblogs.com | 仅 pic.cnblogs.com 与 www.pic.cnblogs.com |
| *(留空)* | — | **所有请求** |

在侧边栏中用每条规则自己的开关启用/停用；顶部的总开关可以一键暂停或恢复全部规则。

---

## 功能特性

| 功能 | 说明 |
|---|---|
| 🔧 **set / append / remove** | 覆盖、追加（Cookie、X-Forwarded-For 等）或移除 header |
| 📥📤 **请求头 & 响应头** | 每条规则可独立修改请求头或响应头 |
| ✏️ **内联编辑** | 直接在侧边栏编辑 header，无需弹窗 |
| 📋 **规则系统** | 保存多套 header 配置 |
| 🌐 **域名绑定** | 规则绑定域名（忽略大小写、忽略路径） |
| 🔽 **包含子域名** | 可选开关：`*.example.com` 匹配全部子域名 |
| 🎯 **Method 过滤** | 可将规则限定为单一 HTTP 方法（GET、POST 等），默认全部 |
| 🌍 **全局规则** | Match URL 留空 → 对所有请求生效 |
| 🏷️ **URL 标签** | 点击当前页面的域名自动填入 |
| 🔘 **规则开关** | 每条规则独立启用/停用；顶部总开关一键全部停止 |
| 🔗 **任意标签页** | 规则全局生效，无标签页隔离 |
| 🧹 **会话规则** | 浏览器重启自动清空，启动时自动重新应用 |
| 📥📤 **导入导出** | JSON 备份恢复（高级版功能） |

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
| 规则数量 | 最多 5 个 | 无限制 |
| 每条规则 Header 数 | 最多 5 条 | 无限制 |
| 域名匹配 | ✅ | ✅ |
| 全局规则（URL 留空） | ✅ | ✅ |
| 导入导出 | ❌ 仅高级版 | ✅ |
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
3. 点击 **"添加到 Chrome"** / **"添加到 Edge"**
4. 点击工具栏中的 🔧 vkt-header 图标，打开侧边栏

> ⚠️ 请勿从第三方网站安装。未授权版本可能危及数据安全。

---

## 隐私保护

vkt-header 遵循隐私优先原则：

- ✅ 全部规则存储在 `chrome.storage.local` — **不上传任何服务器**
- ✅ 会话规则在浏览器重启后自动清空，浏览器启动时自动重新应用已启用规则
- ✅ 无分析追踪、无Cookie
- ✅ 部分请求头（Host、Origin 等）受浏览器保护，无法修改
- ✅ 仅限开发调试使用

### 权限说明

| 权限 | 用途 |
|------|------|
| `storage` | 本地保存请求头规则和设置 |
| `activeTab` | 访问当前标签页（如读取其 URL） |
| `sidePanel` | 显示扩展侧边栏界面 |
| `declarativeNetRequestWithHostAccess` | 修改HTTP请求头 |
| `tabs` | 读取当前标签页 URL（域名标签功能） |

- [完整隐私条款](https://annmax1983.github.io/vkt-header/privacy-policy.html)

---

## 常见问题

1. **启用规则后请求头没有生效？**
   请刷新页面。DNR 会话规则仅对新请求生效，不影响已加载的资源。

2. **重启浏览器后规则消失？**
   这是设计行为。vkt-header 仅使用会话规则，浏览器重启自动清空；浏览器启动时 vkt-header 会自动重新应用所有已启用规则。

3. **部分请求头无法修改？**
   浏览器保护的请求头（Host、Origin等）无法被扩展修改，这是浏览器安全限制而非bug。

4. **如何将规则迁移到其他设备？**
   打开设置 → 导出下载JSON备份，然后在另一台设备上导入。

5. **打开首页/首次导航时请求头没生效？**
   DNR 规则不会修改浏览器缓存命中的请求。启用规则后请强制刷新（Ctrl+Shift+R）或重新打开页面，导航请求就会带上自定义头；缓存的子资源同理。

6. **浏览器刚启动时请求头没生效？**
   Service Worker 是懒加载的：浏览器启动后的最初几个请求，可能在 vkt-header 重新应用会话规则之前就已发出。刷新或重试即可——之后的导航都会正常携带自定义头。这只影响浏览器刚启动的一小段时间，不影响正常浏览。

---

## 版权声明

1. 本扩展仅用于开发调试目的修改HTTP请求头。所访问网站的内容和服务归其所有者所有。
2. 用户不得使用本扩展绕过网站安全限制、访问未授权内容或从事任何非法活动。
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
