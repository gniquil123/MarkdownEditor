# README 更新记录

日期：2026-03-28
更新者：弗兰奇

---

## 任务1：markdown-editor README 创建

**文件位置**：`C:\Users\developer\.openclaw\workspace\tmp\README-markdown-editor.md`

**创建内容**：
- 工具名称和简介（MD Editor - Markdown 编辑器）
- 功能特性：
  - Markdown 编辑与实时预览
  - 代码高亮（highlight.js）
  - 撤销与恢复（Ctrl+Z / Ctrl+Y）
  - 文件操作（新建、打开、保存、另存为）
  - 响应式设计（分屏模式）
  - 离线使用支持
- 使用说明：
  - 快速开始
  - 工具栏按钮说明
  - 浮动操作按钮说明
  - 快捷键列表
- 离线使用说明：
  - 文件结构要求
  - 依赖资源下载命令
- 技术信息：
  - 核心技术栈（markdown-it、highlight.js、File System Access API）
  - 浏览器兼容性表格
  - 支持的 Markdown 语法列表

---

## 任务2：vtool README 更新为 v2.0

**文件位置**：`C:\Users\developer\.openclaw\workspace\version-tool\README.md`

**主要更新内容**：

### 1. 版本号更新
- 标题更新为 "vtool — 文件版本管理工具 v2.0"
- 新增 v2.0 功能概述（GUI 界面、存储目录迁移）

### 2. 功能特性新增
- 🖥️ **GUI 界面** — 可视化版本树，支持缩放、拖拽、版本对比
- 🏷️ **版本标签** — 给重要版本打标签
- 🔄 **迁移工具** — 从 v1.x 自动迁移数据

### 3. 安装方式更新
- 新增单可执行文件安装方式（PyInstaller 打包）
- 更新依赖列表（新增 flask、pyinstaller）
- 添加打包命令说明

### 4. 目录结构更新
- 新增 v2.0 存储目录结构说明（`~/.vtool/store/<hash>/`）
- 说明项目目录下仅保留 `.vtool.json`

### 5. 新增命令
- `vtool gui` — 启动图形界面
- `vtool tag` — 给版本打标签
- `vtool export` — 导出版本到指定路径
- `vtool migrate` — 从 v1.x 迁移数据
- `vtool projects` — 列出所有被管理的项目

### 6. 新增 GUI 使用说明
- GUI 启动方法
- GUI 功能特性：
  - 版本历史树可视化
  - 文件列表面板
  - Diff 查看器
  - 操作菜单
- GUI 布局示意图

### 7. 配置格式更新
- 更新为新的 `.vtool.json` 格式
- 新增字段说明：
  - `project_id`
  - `project_root`
  - `store_dir`
  - `debounce_seconds`
  - `exclude_dirs`
  - `snapshot_on_exit`

### 8. 新增迁移指南
- 从 v1.x 迁移到 v2.0 的步骤
- 兼容性说明

### 9. 技术栈更新
- 新增 Flask（GUI 后端）
- 新增 HTML5 Canvas（GUI 版本树渲染）

### 10. 注意事项
- 新增自排除机制说明（`~/.vtool/` 不能被管理）
- 新增并发限制说明
- 新增大文件性能提示
- 新增 Windows Defender 误报提示

---

## 文件变更汇总

| 操作 | 文件路径 |
|------|----------|
| 创建 | `C:\Users\developer\.openclaw\workspace\tmp\README-markdown-editor.md` |
| 更新 | `C:\Users\developer\.openclaw\workspace\version-tool\README.md` |
| 创建 | `C:\Users\developer\.openclaw\workspace\tmp\readme-update.md`（本文件） |

---

## 参考文件

- `tmp/markdown-editor.html` — markdown-editor 源代码
- `tmp/md-changes.md` — markdown-editor 修改记录
- `version-tool/CHANGES-v2.md` — vtool v2.0 变更记录
- `version-tool/REQUIREMENTS-v2.md` — vtool v2 需求文档
