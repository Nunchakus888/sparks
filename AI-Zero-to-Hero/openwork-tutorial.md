# OpenWork 完整教程

## 目录
1. [什么是 OpenWork](#什么是-openwork)
2. [安装步骤](#安装步骤)
3. [配置 API](#配置-api)
4. [首次使用](#首次使用)
5. [实战案例](#实战案例)
6. [进阶技巧](#进阶技巧)
7. [常见问题](#常见问题)

---

## 什么是 OpenWork

OpenWork 是 Claude Cowork / Codex 的开源替代品（桌面应用），帮助你运行 AI Agent、Skills 和 MCP。

**官方仓库**：https://github.com/different-ai/openwork
**Discord 社区**：https://discord.gg/VEhNQXxYMB
**协议**：MIT 开源

### 核心理念

- **本地优先**：在你自己的电脑上运行，一键启动，数据不上传
- **可组合**：桌面应用、WhatsApp/Slack/Telegram 连接器、或服务端，按需使用，不绑定
- **可导出**：底层基于 OpenCode，OpenCode 能做的事 OpenWork 都能做
- **可共享**：单人起步，然后共享。一个命令即可启动可共享的实例

### 主要功能

- **Host 模式**：在本地运行 OpenCode
- **Client 模式**：连接到远程 OpenCode 服务器
- **会话管理**：创建/选择会话，发送任务
- **实时更新**：SSE 事件订阅，实时查看执行进度
- **执行计划**：以时间线展示 AI 的执行步骤
- **权限控制**：对敏感操作进行权限确认（允许/拒绝）
- **模板系统**：保存和复用常用工作流
- **Skills 管理**：安装和管理技能插件

### 与官方版本对比

| 特性 | OpenWork | Claude Cowork 官方 |
|------|----------|-------------------|
| 价格 | 免费 + API 费用 | $20-100/月 |
| 开源 | MIT 开源 | 闭源 |
| 模型选择 | 多种（含国内模型） | 仅 Claude |
| 科学上网 | 不需要（用国内模型） | 需要 |
| 扩展性 | Skills + MCP + 插件 | 有限 |
| 部署方式 | 本地/远程/多端 | 仅桌面 |

---

## 安装步骤

### 方法 1：下载安装包（推荐）

最简单的方式，适合所有用户：

1. 访问 [GitHub Releases](https://github.com/different-ai/openwork/releases)
2. 下载最新版本的 `.dmg` 文件（macOS）
3. 双击安装，将应用拖入 `Applications` 文件夹
4. 首次打开：右键点击应用 → 选择"打开"

> 如果提示"无法打开"，在终端执行：
> ```bash
> xattr -cr /Applications/OpenWork.app
> ```

### 方法 2：从源码构建（开发者）

需要预先安装：Node.js + pnpm、Rust 工具链、OpenCode CLI

```bash
git clone https://github.com/different-ai/openwork.git
cd openwork
git checkout dev
pnpm install

# 启动桌面应用
pnpm dev

# 或仅启动 Web UI
pnpm dev:ui
```

### 方法 3：命令行模式（无桌面 UI）

通过 OpenWork Orchestrator 运行，不需要桌面界面：

```bash
npm install -g openwork-orchestrator
openwork start --workspace /path/to/workspace --approval auto
```

---

## 配置 API

启动 OpenWork 后，需要配置 AI 模型。根据你的情况选择：

### 国内用户推荐（无需科学上网）

| 模型 | 注册地址 | 新用户福利 | 成本 |
|------|---------|-----------|------|
| **智谱 GLM-4**（推荐） | [open.bigmodel.cn](https://open.bigmodel.cn) | 送 ¥100 | ¥0.1/1K tokens |
| Kimi | [platform.moonshot.cn](https://platform.moonshot.cn) | 送 ¥15 | ¥0.12/1K tokens |
| DeepSeek | [platform.deepseek.com](https://platform.deepseek.com) | 无 | ¥0.001/1K tokens |

### 国际用户

| 模型 | 注册地址 | 成本 |
|------|---------|------|
| Claude (Anthropic) | [console.anthropic.com](https://console.anthropic.com) | $15/1M tokens |
| OpenAI | [platform.openai.com](https://platform.openai.com) | 按模型计费 |

### 配置步骤

1. 注册上述任一模型账号，获取 API Key
2. 在 OpenWork 界面中进入"设置"
3. 选择模型提供商，粘贴 API Key
4. 点击"测试连接"确认配置正确
5. 选择工作目录（AI 只能访问此目录内的文件）

---

## 首次使用

### 第一个任务：创建待办清单

在 OpenWork 对话区输入：

```
帮我创建一个待办事项清单，包含今天要做的 5 件事，保存为 todo.txt
```

你会看到 AI 实时执行：分析任务 → 创建文件 → 写入内容 → 完成。

打开工作目录下的 `todo.txt` 即可查看结果。

### 第二个任务：文件整理

```
扫描当前目录中的所有文件，按文件类型（图片、文档、视频）分类列出
```

### 理解 AI 的工作方式

观察 OpenWork 的执行日志，你会看到：
- **任务分解**：AI 将大任务拆分为小步骤
- **文件操作**：AI 读取和创建文件
- **权限请求**：敏感操作会弹出确认（允许/拒绝）
- **结果验证**：AI 检查任务完成情况

---

## 实战案例

### 案例 1：批量重命名文件

```
帮我批量重命名 photos 文件夹中的所有 JPG 文件：
- 格式：2026-03-10_photo_序号.jpg
- 序号保持三位数（001, 002, ...）
- 重命名前先列出所有文件让我确认
```

### 案例 2：数据分析

```
分析 sales.csv 文件：
1. 计算总销售额
2. 找出最畅销的产品
3. 按日期统计每日销售额
4. 生成分析报告，保存为 sales_report.md
```

### 案例 3：会议纪要

```
根据 meeting_transcript.txt 生成会议纪要：
1. 提取会议主题
2. 列出参会人员
3. 总结讨论要点
4. 提取行动项（谁负责什么，截止日期）
5. 保存为 meeting_minutes.md
```

---

## 进阶技巧

### 编写高质量 Prompt

**差的 Prompt：**
```
处理这些文件
```

**好的 Prompt：**
```
批量处理 documents 文件夹中的所有 PDF 文件：
1. 提取每个 PDF 的文本内容
2. 生成摘要（不超过 200 字）
3. 保存为 Markdown 格式，文件名为 原文件名_summary.md
4. 创建一个索引文件 index.md，列出所有摘要
```

**Prompt 结构建议：**
```
[背景] 我是一名市场经理
[目标] 分析客户反馈数据
[输入] feedback.csv 文件
[处理] 提取关键问题，按优先级排序
[输出] Markdown 表格，包含问题、频次、优先级
[约束] 只保留前 10 个问题
```

### 使用模板

把常用任务保存为模板文件，复用时直接引用：

```
按照 templates/weekly_report.txt 的模板，生成本周周报
```

### Skills 管理

OpenWork 支持通过 Skills 扩展功能：
- 在 Skills 标签页查看已安装的技能
- 通过 OpenPackage 安装新技能：`opkg install <package>`
- 导入本地技能文件夹

### MCP 工具集成

通过 MCP (Model Context Protocol) 连接外部工具，如浏览器自动化、数据库查询等。

---

## 常见问题

### Q1: 首次打开提示"无法打开"？

macOS 安全限制，执行：
```bash
xattr -cr /Applications/OpenWork.app
```

### Q2: API Key 无效？

检查清单：
1. 确认 API Key 复制完整（无多余空格）
2. 检查账户有可用额度
3. 尝试重新生成 API Key

### Q3: AI 无法访问文件？

文件必须在你设置的工作目录内。将文件移入工作目录，或在设置中更改工作目录。

### Q4: Linux 上启动崩溃（Wayland）？

设置环境变量后启动：
```bash
WEBKIT_DISABLE_DMABUF_RENDERER=1 openwork
```

---

## 参考资源

- [OpenWork GitHub](https://github.com/different-ai/openwork)
- [Discord 社区](https://discord.gg/VEhNQXxYMB)
- [智谱 GLM API 文档](https://open.bigmodel.cn/dev/api)
- [Kimi API 文档](https://platform.moonshot.cn/docs)
- [DeepSeek API 文档](https://platform.deepseek.com/api-docs)

---

**祝你使用愉快！如有问题，欢迎在 [GitHub Issues](https://github.com/different-ai/openwork/issues) 或 [Discord](https://discord.gg/VEhNQXxYMB) 提问。**
