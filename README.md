# Bili UP Extension

<div align="center">

**一个现代化的浏览器扩展，用于保存 YouTube 和 Bilibili 视频 URL 及字幕**

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![WXT](https://img.shields.io/badge/WXT-0.20.11-orange.svg)](https://wxt.dev/)
[![React](https://img.shields.io/badge/React-19-61dafb.svg)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.9-blue.svg)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-3.0-38bdf8.svg)](https://tailwindcss.com/)

</div>

## ✨ 特性

- 🎯 **一键保存** - 快速保存视频 URL 和字幕
- ⌨️ **快捷键支持** - Ctrl/Cmd + Shift + S/T 快速操作
- 🎨 **现代化 UI** - 使用 React + Tailwind CSS 构建的美观界面
- 📦 **本地存储** - 自动保存到浏览器本地，随时查看
- 🌐 **后端同步** - 可选将数据提交到后端服务器
- 🔄 **实时字幕获取** - 自动获取 YouTube 视频字幕
- 🎬 **双平台支持** - YouTube 和 Bilibili 双平台兼容
- 🛡️ **类型安全** - 完整的 TypeScript 类型支持
- 🔐 **扫码登录** - 支持 Bilibili 扫码登录
- ⚙️ **DeepSeek 集成** - 配置 DeepSeek API 密钥进行 AI 翻译
- 🌐 **Web 管理** - 通过外部 Web 页面管理视频和查看详情

## 🚀 快速开始

## 📦 安装到浏览器 Chrome / Edge

1. 打开浏览器扩展管理页面：
   - Chrome: `chrome://extensions/`
   - Edge: `edge://extensions/`

2. 启用右上角的 **"开发者模式"**

3. 点击 **"加载已解压的扩展程序"**

4. 选择项目的 `dist/chrome-mv3` 目录

5. 扩展安装完成！图标会出现在浏览器工具栏

### Firefox

1. 打开 `about:debugging#/runtime/this-firefox`

2. 点击 **"临时载入附加组件"**

3. 选择 `dist/firefox-mv2/manifest.json` 文件

4. 扩展安装完成！

## 🎮 使用指南

### 基本操作

#### 1. 保存视频 URL

**方法一：使用浮动按钮**
1. 访问 YouTube 或 Bilibili 视频页面
2. 点击页面右下角的蓝色浮动按钮
3. 选择 **"保存当前 URL"**
4. 看到成功通知即表示保存完成

**方法二：使用快捷键**
- 按下 `Ctrl + Shift + S` (Windows/Linux)
- 或 `Cmd + Shift + S` (macOS)

#### 2. 保存视频字幕

**方法一：使用浮动按钮**
1. 访问有字幕的 YouTube 视频
2. 点击页面右下角的浮动按钮
3. 选择 **"保存字幕"**
4. 字幕会自动下载为 `.srt` 文件

**方法二：使用快捷键**
- 按下 `Ctrl + Shift + T` (Windows/Linux)
- 或 `Cmd + Shift + T` (macOS)

#### 3. 管理保存的内容

1. 点击浏览器工具栏中的扩展图标
2. 在弹出的窗口中切换标签页：
   - **"保存的 URL"** - 查看所有保存的视频链接
   - **"保存的字幕"** - 查看所有保存的字幕
3. 可以执行的操作：
   - 📥 下载字幕文件
   - 🔗 打开原始视频链接
   - 🗑️ 删除单个项目
   - 🧹 清空所有数据

#### 4. 管理视频和查看详情

1. 在扩展 Popup 中，点击标题下方的 **"扩展设置"** 链接
2. 自动在新标签页打开 Web 管理页面（`http://127.0.0.1:8096`）
3. 在 Web 页面中可以：
   - 📊 查看所有已提交视频的列表
   - 🔍 查看视频详细信息和处理进度
   - 📝 查看任务步骤和执行状态
   - 📁 下载相关文件（视频、字幕、封面等）
   - 🔄 重试失败的处理步骤
   - ⚙️ 管理更多高级设置

#### 5. 设置和配置

1. 右键点击扩展图标，选择 **"选项"**（或从扩展管理页面进入）
2. 在设置页面中，您可以：

**常规设置标签：**
- 配置 **DeepSeek API 密钥** - 用于 AI 翻译功能
- 设置 **后端服务器地址** - 默认为 `http://localhost:8096/api/v1`
- 启用/禁用 **自动保存字幕** 功能

**账户设置标签：**
- 使用 **Bilibili 扫码登录** 功能
- 查看当前登录状态和用户信息
- 退出登录

**关于标签：**
- 查看扩展版本和信息
- 访问项目主页和文档

## 🛠️ 技术栈

- **[WXT](https://wxt.dev/)** - 下一代 Web 扩展开发框架
- **[React 19](https://react.dev/)** - 用户界面库
- **[TypeScript 5.9](https://www.typescriptlang.org/)** - 类型安全的 JavaScript
- **[Tailwind CSS 3](https://tailwindcss.com/)** - 实用优先的 CSS 框架
- **[Vite 7](https://vitejs.dev/)** - 极速构建工具

### 后端 API 格式

扩展会向后端发送以下格式的 POST 请求：

```json
{
  "url": "https://www.youtube.com/watch?v=xxxxx",
  "title": "视频标题",
  "description": "视频描述",
  "operationType": "translation",  // "translation" 或 "download"
  "status": "pending",
  "playlistId": "playlist_001",
  "subtitles": [
    {
      "text": "字幕文本内容",
      "duration": 3.5,
      "offset": 0.0,
      "lang": "en"
    }
  ],
  "timestamp": "2025-10-13T12:00:00.000Z"
}
```


### 字幕无法获取

- ✅ 确认视频有可用字幕或自动字幕
- ✅ 检查浏览器控制台是否有错误
- ✅ 尝试刷新页面重新加载扩展

### 后端提交失败

- ✅ 确认后端服务器正在运行
- ✅ 检查 `BACKEND_URL` 配置是否正确
- ✅ 查看浏览器控制台的网络请求日志
- ✅ 确认后端 API 接口格式匹配

### 扩展无法加载

- ✅ 确认已启用开发者模式
- ✅ 检查 `dist/` 目录是否存在
- ✅ 尝试重新构建：`yarn build`
- ✅ 查看浏览器扩展管理页面的错误信息

## 📝 核心功能说明

### pot 参数拦截

扩展使用双重机制捕获 YouTube 字幕请求中的 `pot` 参数：

1. **页面拦截器** (`public/page-interceptor.js`)
   - 在页面上下文中拦截 fetch 和 XHR 请求
   - 通过 postMessage 将参数传递给 content script

2. **webRequest API** (`entrypoints/background.ts`)
   - 在后台拦截网络请求
   - 直接从 URL 中提取 pot 参数

### 字幕获取流程

1. 用户触发保存字幕操作
2. content script 注入页面拦截器
3. 拦截器捕获 pot 参数并缓存
4. 使用 pot 参数请求字幕 API
5. 解析 JSON3 或 XML 格式字幕
6. 转换为 SRT 格式并下载
7. 同时保存到本地存储和后端服务器


## 🤝 贡献指南

欢迎提交 Issue 和 Pull Request！

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启 Pull Request

## 📄 许可证

本项目采用 MIT 许可证 - 详见 [LICENSE](LICENSE) 文件

## 🙏 致谢

- [WXT](https://wxt.dev/) - 优秀的扩展开发框架
- [React](https://react.dev/) - 强大的 UI 库
- [Tailwind CSS](https://tailwindcss.com/) - 实用的 CSS 框架

## 📧 联系方式

如有问题或建议，请提交 Issue 或联系维护者。

---

<div align="center">
Made with ❤️ using WXT + React + TypeScript
</div>

