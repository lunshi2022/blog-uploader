# Blog Uploader

> 一个 Obsidian 社区插件 —— 写完笔记点一下，自动完成「复制笔记 → 复制附件 → 构建 → 推送」，几分钟后你的博客就更新了。

[![Release](https://img.shields.io/github/v/release/lunshi2022/blog-uploader)](https://github.com/lunshi2022/blog-uploader/releases)
[![平台](https://img.shields.io/badge/platform-Obsidian%20Desktop-7c3aed)](#-安装)
[![License](https://img.shields.io/badge/license-MIT-green)](#-license)

配合 [数字花园 · obsidian-blog](https://github.com/lunshi2022/obsidian-blog) 使用（配套的 Windows 一键部署器会自动装好本插件）。

纯 JavaScript、零依赖、仅桌面版 Obsidian。

## ✨ 主要功能

- **一键上博**：左侧边栏 ↑ 图标 / 文件右键「上传到博客」/ 命令面板，三种入口随便选
- **附件全跟随**：笔记里 `![[引用]]` 的图片、音视频、PDF 自动一起复制，保持库内目录结构
- **自动构建**：本机装了 Node 就地构建；没装也不影响发布，由 GitHub 云端构建
- **自动推送**：git 提交 + 推送一气呵成；推送用令牌内嵌 URL，不弹凭据管理器窗口
- **本地预览**：命令面板「本地预览（构建并打开浏览器）」，不用开终端（端口可在设置里改）
- **攒稿发布**：设置里可分别开关「自动构建」和「自动推送」，想攒一批再发就关掉推送

## 📦 安装

1. 下载本仓库的 `main.js` 和 `manifest.json`
2. 放到你的 Obsidian 库：

   ```
   <你的库>/.obsidian/plugins/blog-uploader/
   ```

3. Obsidian 设置 → 第三方插件 → 关闭安全模式 → 启用 **Blog Uploader**
4. 打开插件设置，填入**博客仓库根目录**（部署器部署好的那个目录）

## 🚀 用法

- **发布**：点 ↑ 图标，或在文件列表右键笔记 →「上传到博客」
- **更新**：改完再点一次上传即可，同名覆盖
- **预览**：命令面板 →「本地预览（构建并打开浏览器）」，看完执行「停止本地预览服务」
- **不发布某篇**：frontmatter 写 `draft: true`

## 🔑 推送与认证

- 推送需要本机装有 **git**
- 推荐在插件设置里填入 **GitHub 访问令牌（PAT）**：推送时令牌内嵌进远程 URL，完全绕开 Git Credential Manager 的交互弹窗（否则可能卡在「选择账户」页面）
- 令牌只保存在本地插件配置里，**永不上传**（`.obsidian/` 已被博客仓库的 `.gitignore` 排除）

## ❓ 常见问题

- **推送失败提示 `GH013`**：说明推送内容里被检测到令牌/密钥。检查博客仓库的 `.gitignore` 是否排除了整个 `.obsidian/`
- **提示「内容没有变化」但仍想推送**：插件会在有积压提交时照常推送，只有本地远端完全一致时才提示无需推送
- **改了设置不生效**：更新 main.js 后需要重载插件（设置里关闭再开启，或重启 Obsidian）
- **推送失败**：现在会显示 git 的真实错误行（认证失败/非快进等），按提示处理即可

## 📄 License

MIT © [论世先生](https://github.com/lunshi2022)
