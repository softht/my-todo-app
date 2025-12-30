# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

这是一个极简的待办事项（Todo）应用，采用纯前端技术栈实现。所有代码（HTML、CSS、JavaScript）都包含在单个 `index.html` 文件中。

## Running the Application

由于是纯静态 HTML 应用，不需要构建过程：

```bash
# 直接在浏览器中打开即可
# Windows:
start index.html

# macOS:
open index.html

# Linux:
xdg-open index.html
```

或者使用任何本地开发服务器：
```bash
# 使用 Python
python -m http.server 8000

# 使用 Node.js (如果安装了 http-server)
npx http-server
```

## Architecture

### 单文件结构

整个应用采用 MVC 模式的简化版本：

- **Model**: `tasks` 数组存储任务数据，每个任务包含 `{ id, text, completed }` 结构
- **View**: HTML DOM 结构和 CSS 样式
- **Controller**: JavaScript 函数处理用户交互（`addTask()`, `toggleTask()`, `deleteTask()`, `renderTasks()`）

### 核心功能模块

| 函数 | 职责 |
|------|------|
| `addTask()` | 添加新任务到数组并重新渲染 |
| `toggleTask(id)` | 切换指定任务的完成状态 |
| `deleteTask(id)` | 从数组中删除指定任务 |
| `renderTasks()` | 根据当前 tasks 数组重新渲染 DOM |
| `escapeHtml(str)` | XSS 防护，转义 HTML 特殊字符 |

### 数据存储

- 当前使用**内存存储**（页面刷新数据丢失）
- 任务 ID 通过简单计数器生成

### 安全特性

代码包含 `escapeHtml()` 函数用于 XSS 防护，在渲染用户输入时进行 HTML 转义处理。

## Technology Stack

- **纯 HTML5** + **CSS3** + **原生 JavaScript** (ES6+)
- 无任何框架或构建工具依赖
- 响应式设计（使用 Flexbox 和媒体查询）
