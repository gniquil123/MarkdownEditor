# MD Editor - Markdown 编辑器

一个简洁、优雅的 Markdown 编辑器，专为本地离线使用而设计。纯前端实现，无需后端服务器，直接在浏览器中打开即可使用。

## 功能特性

### 📝 Markdown 编辑与预览
- **实时预览**：编辑时即时渲染 Markdown，所见即所得
- **深色主题**：护眼配色方案，适合长时间编辑
- **分屏模式**：横屏时自动开启左右分屏，编辑和预览并排显示

### 🎨 代码高亮
- 集成 highlight.js 语法高亮
- 支持多种编程语言
- Atom One Dark 主题配色

### ↩️ 撤销与恢复
- **撤销** (Ctrl+Z)：撤销上一步操作
- **恢复** (Ctrl+Y / Ctrl+Shift+Z)：恢复被撤销的操作
- 支持最多 100 步操作历史
- 格式化操作后自动保存状态

### 💾 文件操作
- **新建文件**：创建空白文档
- **打开文件**：支持 .md、.markdown、.txt 格式
- **保存** (Ctrl+S)：覆盖原文件（支持 File System Access API 的浏览器）
- **另存为**：保存到新文件位置

### 📱 响应式设计
- 移动端友好，支持触摸操作
- 横屏自动分屏模式
- 浮动操作按钮，方便单手操作

### 🔌 离线使用
- 无需网络连接
- 需要 `md-editor-assets` 目录包含以下依赖文件：
  - `markdown-it.min.js` - Markdown 解析器
  - `highlight.min.js` - 代码高亮库
  - `atom-one-dark.min.css` - 代码高亮主题

## 使用说明

### 快速开始

1. 确保 `markdown-editor.html` 和 `md-editor-assets/` 目录在同一文件夹下
2. 双击 `markdown-editor.html` 在浏览器中打开
3. 开始编写 Markdown 文档！

### 工具栏按钮说明

| 按钮 | 功能 | 快捷键 |
|------|------|--------|
| ↩️ | 撤销 | Ctrl+Z |
| ↪️ | 恢复 | Ctrl+Y |
| **B** | 加粗文字 | - |
| *I* | 斜体文字 | - |
| ~~S~~ | 删除线 | - |
| H1 | 一级标题 | - |
| H2 | 二级标题 | - |
| • | 无序列表 | - |
| 1. | 有序列表 | - |
| ❝ | 引用 | - |
| `</>` | 代码块 | - |
| `` | 行内代码 | - |
| 🔗 | 链接 | - |
| 🖼️ | 图片 | - |
| ─ | 分割线 | - |
| 👁️ | 切换预览 | - |

### 浮动操作按钮

位于右下角，包含以下功能：
- **+** 新建文件
- **↗️** 打开文件
- **💾** 保存文件 (Ctrl+S)
- **⬇️** 另存为

### 快捷键

| 快捷键 | 功能 |
|--------|------|
| Ctrl+Z | 撤销 |
| Ctrl+Y | 恢复 |
| Ctrl+Shift+Z | 恢复 |
| Ctrl+S | 保存 |
| Tab | 插入 4 个空格 |

## 离线使用说明

为确保完全离线使用，需要准备以下文件结构：

```
workspace/
├── markdown-editor.html    # 主程序
└── md-editor-assets/       # 依赖资源目录
    ├── markdown-it.min.js
    ├── highlight.min.js
    └── atom-one-dark.min.css
```

### 下载依赖资源

如果你还没有这些文件，可以从以下 CDN 下载：

```bash
# 创建资源目录
mkdir md-editor-assets

# 下载 markdown-it
curl -L -o md-editor-assets/markdown-it.min.js https://cdn.jsdelivr.net/npm/markdown-it@13.0.1/dist/markdown-it.min.js

# 下载 highlight.js
curl -L -o md-editor-assets/highlight.min.js https://cdn.jsdelivr.net/gh/highlightjs/cdn-release@11.7.0/build/highlight.min.js

# 下载 highlight.js 主题
curl -L -o md-editor-assets/atom-one-dark.min.css https://cdn.jsdelivr.net/gh/highlightjs/cdn-release@11.7.0/build/styles/atom-one-dark.min.css
```

## 技术信息

### 核心技术栈

- **markdown-it**：高性能 Markdown 解析器，支持 CommonMark 规范
- **highlight.js**：自动语言检测的语法高亮库
- **File System Access API**：现代浏览器的本地文件操作接口

### 浏览器兼容性

| 功能 | 支持浏览器 |
|------|-----------|
| 基础编辑预览 | 所有现代浏览器 |
| 文件系统 API | Chrome 86+, Edge 86+, Opera 72+ |
| 离线使用 | 所有支持 Service Worker 的浏览器 |

**注意**：在不支持 File System Access API 的浏览器（如 Firefox、Safari）中，保存功能将降级为文件下载方式。

### 支持的 Markdown 语法

- 标题 (H1-H6)
- 粗体、斜体、删除线
- 无序列表、有序列表、任务列表
- 代码块（带语法高亮）
- 行内代码
- 链接和图片
- 引用块
- 表格
- 水平分割线

## 许可证

MIT License

---

**提示**：首次使用建议尝试编辑默认的示例文档，熟悉各种 Markdown 语法和编辑功能。
