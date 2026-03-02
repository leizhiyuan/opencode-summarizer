# OpenCode Summarizer

一个 Chrome 浏览器扩展，利用本地运行的 [OpenCode](https://opencode.ai) 服务器对网页内容和 Bilibili 视频进行 AI 摘要总结。

## 功能

- **网页摘要** — 智能提取页面正文内容，发送给 AI 生成摘要
- **Bilibili 视频总结** — 自动获取 Bilibili 视频字幕并生成总结
- **预设提示词** — 核心要点、一句话总结、整理菜谱、详细总结
- **自定义提示词** — 支持自由输入提示词
- **流式输出** — 实时 SSE 流式显示 AI 回复
- **多语言输出** — 支持中文、英文、跟随原文语言
- **可配置** — 服务器地址和输出语言均可自定义

## 安装

### 1. 启动 OpenCode 服务器

```bash
opencode serve --cors chrome-extension://
```

`--cors` 参数需要允许扩展的 origin。默认服务器地址为 `http://localhost:4096`。

### 2. 加载扩展

1. 打开 Chrome，访问 `chrome://extensions/`
2. 开启右上角「开发者模式」
3. 点击「加载已解压的扩展程序」，选择本项目目录

### 3. 使用

点击浏览器工具栏中的扩展图标，选择预设提示词或输入自定义提示词，点击「运行」即可。

## 项目结构

```
opencode-summarizer/
├── manifest.json   # 扩展清单 (Manifest V3)
├── popup.html      # 弹出窗口 UI
├── popup.css       # 样式
├── popup.js        # 主逻辑：设置、API 通信、SSE 流式处理、Bilibili 字幕获取
├── content.js      # 内容脚本：注入页面提取正文内容
└── icons/          # 扩展图标
```

## 技术栈

- Chrome Extension Manifest V3
- 原生 JavaScript，无需构建工具
- CSS 自定义属性（暗色主题）
- OpenCode REST API + SSE
- Bilibili Web API（字幕获取）

## 配置

点击扩展弹窗中的齿轮图标进入设置：

- **服务器地址** — 默认 `http://localhost:4096`
- **输出语言** — 中文（默认）/ 英文 / 跟随原文

配置保存在 `chrome.storage.local` 中。

## License

MIT
