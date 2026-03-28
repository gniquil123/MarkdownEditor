# Markdown Editor 修改记录

## 2026-03-28

### 1. 删除自动保存功能

- 删除了 `autoSaveTimer` 变量
- 删除了 `STORAGE_KEY` 和 `STORAGE_FILENAME` 常量
- 删除了 `init()` 函数中的 localStorage 加载逻辑
- 删除了 `setInterval(autoSave, 30000)` 定时器
- 删除了 `onEditorInput()` 中的延迟自动保存逻辑
- 删除了 `markUnsaved()` 函数
- 删除了 `autoSave()` 函数
- 删除了状态栏中的"已保存"指示器 (`saved-indicator`)
- 删除了保存对话框相关 HTML 和函数

### 2. 实现 File System Access API（保存/另存为区分）

- 新增 `fileHandle` 变量存储当前文件句柄
- 新增 `currentFilename` 变量存储当前文件名
- 重写 `openFile()` 函数：
  - 检测 `window.showOpenFilePicker` 是否存在
  - 支持则使用 File System Access API
  - 不支持则降级为传统 `input[type=file]` 方式
- 新增 `openFileWithPicker()` 函数：使用 `showOpenFilePicker()` 打开文件选择器
- 新增 `handleFileSelectPicker()` 函数：处理 API 方式选择的文件
- 重写 `saveFile()` 函数：
  - 如果有文件句柄 → 直接写回原文件（覆盖）
  - 如果没有句柄 → 降级为另存为
- 新增 `saveAsFile()` 函数：
  - 始终调用 `showSaveFilePicker()` 选择新路径
  - 保存后记住新的文件句柄
- 新增 `saveWithHandle()` 辅助函数：使用句柄写入文件内容
- 新增 `saveAsFallback()` 函数：不支持 FS API 时使用 Blob 下载
- 新增"另存为"按钮到浮动工具栏
- 新增文件名显示到状态栏（`filenameDisplay`）
- 更新 `newFile()` 重置文件句柄为 null

### 3. 添加撤销(Undo)和恢复(Redo)功能

- 新增 `history` 数组：操作历史栈（最大 100 条）
- 新增 `historyIndex` 变量：当前历史位置
- 新增 `maxHistory` 常量：最大历史记录数
- 新增 `isUndoRedo` 标志：防止撤销/恢复操作本身被记录
- 新增 `saveState()` 函数：保存当前编辑状态到历史栈
  - 包含内容、光标位置、时间戳
  - 撤销后做新操作时自动清除恢复栈
- 新增 `undo()` 函数：执行撤销操作 (Ctrl+Z)
- 新增 `redo()` 函数：执行恢复操作 (Ctrl+Y / Ctrl+Shift+Z)
- 新增 `canUndo()` 函数：检查是否可以撤销
- 新增 `canRedo()` 函数：检查是否可以恢复
- 新增 `updateUndoRedoButtons()` 函数：更新撤销/恢复按钮禁用状态
- 修改 `onEditorInput()`：输入时使用防抖（300ms）保存状态到历史栈
- 修改 `insertMarkdown()`：格式化操作后保存状态
- 修改 `insertAtCursor()`：插入操作后保存状态
- 修改 `onEditorKeydown()`：
  - Ctrl+Z：撤销
  - Ctrl+Y：恢复
  - Ctrl+Shift+Z：恢复
- 在工具栏第一组添加撤销 ↩️ 和恢复 ↪️ 按钮（带禁用状态）

### 4. 其他更新

- 更新默认示例内容，提及撤销/恢复和文件系统 API 功能
- 添加 Ctrl+S 全局快捷键绑定到保存功能

### 修改的文件

- `tmp/markdown-editor.html`

---

## 验证清单

- [x] 输入文字 → Ctrl+Z 能撤销 → Ctrl+Y 能恢复
- [x] 点击格式化按钮（如加粗） → Ctrl+Z 能撤销
- [x] 连续多步操作 → 连续多步撤销/恢复都正常
- [x] 撤销后输入新内容 → 之前的恢复栈被清除
- [x] 自动保存相关代码完全删除
- [x] 保存按钮覆盖原文件（有文件句柄时）
- [x] 另存为按钮创建新文件
- [x] 不支持的浏览器降级为 Blob 下载
