# OpenWork 完整教程

## 目录
1. [什么是 OpenWork](#什么是-openwork)
2. [安装前准备](#安装前准备)
3. [安装步骤](#安装步骤)
4. [配置 API](#配置-api)
5. [首次使用](#首次使用)
6. [实战案例](#实战案例)
7. [常见问题](#常见问题)
8. [进阶技巧](#进阶技巧)

---

## 什么是 OpenWork

OpenWork 是一个开源的 AI 协作工具，让你用自然语言指挥 AI 完成工作。

**官方文档**：https://github.com/different-ai/openwork

### 核心特点
OpenWork 是 Claude Cowork 的开源替代品，提供：

- ✅ **图形界面**：无需命令行知识，点击操作
- ✅ **完全免费**：开源软件，无订阅费用
- ✅ **多模型支持**：Claude、OpenAI、国内模型（GLM、Kimi、DeepSeek）
- ✅ **安全沙箱**：VM 级别隔离（macOS 使用 Lima）
- ✅ **本地运行**：数据不上传，隐私安全
- ✅ **一键安装**：无需编程知识

### 与官方版本对比

| 特性 | OpenWork | Claude Cowork 官方 |
|------|-------------------|-------------------|
| 价格 | 免费 + API 费用 | $20-100/月 |
| 模型选择 | 多种（含国内模型） | 仅 Claude |
| 科学上网 | 不需要（用国内模型） | 需要 |
| 稳定性 | 社区维护 | 官方支持 |
| 功能完整度 | 核心功能齐全 | 功能最全 |

---

## 安装前准备

### 系统要求
- **操作系统**：macOS 12.0+ (Monterey 或更高)
- **硬件**：
  - Apple Silicon (M1/M2/M3) 或 Intel 芯片
  - 至少 8GB RAM（推荐 16GB+）
  - 至少 5GB 可用磁盘空间
- **网络**：稳定的互联网连接

### 需要准备的账号

根据你选择的模型，至少准备一个：

#### 选项 1：Claude API（推荐，能力最强）
- 访问：https://console.anthropic.com
- 注册账号（需要科学上网）
- 获取 API Key
- 费用：按量付费，约 $15/100万 tokens

#### 选项 2：智谱 GLM（国内，无需科学上网）
- 访问：https://open.bigmodel.cn
- 注册账号（支持手机号）
- 获取 API Key
- 费用：GLM-4 约 ¥0.1/1000 tokens（约 $0.014）
- **新用户送 ¥100 额度**

#### 选项 3：Kimi（国内，长上下文）
- 访问：https://platform.moonshot.cn
- 注册账号
- 获取 API Key
- 费用：约 ¥0.12/1000 tokens
- **新用户送 ¥15 额度**

#### 选项 4：DeepSeek（国内，性价比高）
- 访问：https://platform.deepseek.com
- 注册账号
- 获取 API Key
- 费用：约 ¥0.001/1000 tokens（非常便宜）

---

## 安装步骤

### 方法 1：下载安装包（推荐）

#### Step 1: 下载
访问 GitHub Release 页面：
```
https://github.com/different-ai/openwork/releases
```

下载最新版本的 macOS 安装包：
- Apple Silicon (M1/M2/M3): `OpenWork-macOS-arm64.dmg`
- Intel 芯片: `OpenWork-macOS-x64.dmg`

#### Step 2: 安装
1. 双击下载的 `.dmg` 文件
2. 将 `Open Cowork` 拖到 `Applications` 文件夹
3. 首次打开时，右键点击 → 选择"打开"（绕过安全检查）
4. 如果提示"无法打开"，执行：
   ```bash
   xattr -cr /Applications/Open\ Cowork.app
   ```

#### Step 3: 首次启动
1. 打开 `Open Cowork` 应用
2. 系统会提示安装 Lima（虚拟机环境）
3. 点击"安装"，等待完成（约 2-5 分钟）
4. 安装完成后，应用会自动重启

---

### 方法 2：从源码构建（开发者）

```bash
# 1. 克隆仓库
git clone https://github.com/different-ai/openwork.git
cd open-cowork

# 2. 安装依赖
npm install

# 3. 构建应用
npm run build

# 4. 启动
npm run start
```

---

## 配置 API

### 首次配置向导

启动应用后，会看到配置界面：

#### Step 1: 选择模型提供商

界面会显示：
```
选择你的 AI 模型提供商：
○ Claude (Anthropic)
○ 智谱 GLM
○ Kimi (Moonshot)
○ DeepSeek
○ OpenAI
○ 自定义 API
```

**推荐选择：**
- **预算充足 + 能科学上网** → Claude (Anthropic)
- **国内用户 + 追求性价比** → 智谱 GLM 或 DeepSeek
- **需要长上下文处理** → Kimi

#### Step 2: 输入 API Key

根据选择的提供商，输入对应的 API Key：

**示例：配置智谱 GLM**
```
API Key: [粘贴你的 API Key]
模型选择: glm-4-plus (推荐)
```

**示例：配置 Claude**
```
API Key: sk-ant-xxxxx
模型选择: claude-opus-4-6 (最强)
```

#### Step 3: 测试连接

点击"测试连接"按钮，确认配置正确：
```
✅ 连接成功！
模型: glm-4-plus
可用额度: ¥98.50
```

#### Step 4: 设置工作目录

选择一个文件夹作为 AI 的工作空间：
```
推荐路径: ~/AI-Workspace
```

**重要**：AI 只能访问这个文件夹内的文件，保证安全性。

---

## 首次使用

### 界面介绍

启动后，你会看到：

```
┌─────────────────────────────────────────┐
│  Open Cowork                      [设置] │
├─────────────────────────────────────────┤
│                                         │
│  工作目录: ~/AI-Workspace               │
│  模型: glm-4-plus                       │
│  状态: ✅ 就绪                          │
│                                         │
├─────────────────────────────────────────┤
│  对话区域                               │
│                                         │
│  你: [输入你的任务...]                  │
│                                         │
├─────────────────────────────────────────┤
│  执行日志 (实时显示 AI 的操作)          │
│  □ 读取文件: data.csv                   │
│  □ 分析数据...                          │
│  □ 生成报告: report.md                  │
└─────────────────────────────────────────┘
```

### 第一个任务：创建待办清单

**输入：**
```
帮我创建一个待办事项清单，包含今天要做的 5 件事，保存为 todo.txt
```

**AI 执行过程：**
```
🤔 理解任务: 创建待办清单文件
📝 执行步骤:
  1. 创建 todo.txt 文件
  2. 写入示例待办事项
  3. 保存文件

✅ 任务完成！
```

**查看结果：**
打开 `~/AI-Workspace/todo.txt`，内容如下：
```
# 今日待办事项

1. [ ] 回复客户邮件
2. [ ] 完成项目报告
3. [ ] 参加下午 3 点会议
4. [ ] 整理本周工作总结
5. [ ] 预约明天的牙医
```

---

## 实战案例

### 案例 1：批量重命名文件

**场景**：你有 50 张照片，文件名是 `IMG_001.jpg` 到 `IMG_050.jpg`，想改为 `2026-03-03_photo_001.jpg` 格式。

**操作步骤：**

1. 将照片放到 `~/AI-Workspace/photos/` 文件夹
2. 在 Open Cowork 中输入：

```
帮我批量重命名 photos 文件夹中的所有 JPG 文件：
- 格式：2026-03-03_photo_序号.jpg
- 序号保持三位数（001, 002, ...）
- 重命名前先列出所有文件让我确认
```

**AI 执行：**
```
🔍 扫描文件夹...
找到 50 个 JPG 文件

📋 重命名预览:
  IMG_001.jpg → 2026-03-03_photo_001.jpg
  IMG_002.jpg → 2026-03-03_photo_002.jpg
  ...
  IMG_050.jpg → 2026-03-03_photo_050.jpg

❓ 确认执行重命名？(y/n)
```

3. 输入 `y` 确认
4. AI 执行重命名，完成后显示：

```
✅ 已重命名 50 个文件
```

---

### 案例 2：数据分析

**场景**：你有一个销售数据 CSV 文件，想分析销售趋势。

**准备数据：**
创建 `sales.csv`：
```csv
日期,产品,销售额
2026-01-01,产品A,1200
2026-01-01,产品B,800
2026-01-02,产品A,1500
2026-01-02,产品B,900
...
```

**输入任务：**
```
分析 sales.csv 文件：
1. 计算总销售额
2. 找出最畅销的产品
3. 按日期统计每日销售额
4. 生成分析报告，保存为 sales_report.md
```

**AI 执行：**
```
📊 读取数据: sales.csv (100 行)
🔢 计算统计数据...
📝 生成报告...

✅ 报告已生成: sales_report.md
```

**查看报告：**
```markdown
# 销售数据分析报告

## 总体概况
- 总销售额: ¥125,000
- 订单数量: 100
- 平均订单金额: ¥1,250

## 产品排行
1. 产品A: ¥65,000 (52%)
2. 产品B: ¥40,000 (32%)
3. 产品C: ¥20,000 (16%)

## 每日销售趋势
| 日期 | 销售额 |
|------|--------|
| 2026-01-01 | ¥2,000 |
| 2026-01-02 | ¥2,400 |
...
```

---

### 案例 3：文档生成

**场景**：根据会议录音转录文本，生成会议纪要。

**输入：**
```
根据 meeting_transcript.txt 生成会议纪要：
1. 提取会议主题
2. 列出参会人员
3. 总结讨论要点
4. 提取行动项（谁负责什么，截止日期）
5. 保存为 meeting_minutes.md
```

**AI 执行：**
```
📖 读取转录文本...
🧠 分析内容...
📝 生成纪要...

✅ 会议纪要已生成: meeting_minutes.md
```

---

### 案例 4：批量文本处理

**场景**：合并多个文本文件，生成目录索引。

**输入：**
```
将 notes 文件夹中的所有 .txt 文件合并：
1. 按文件名排序
2. 每个文件前添加标题（文件名）
3. 生成目录索引
4. 保存为 combined_notes.md
```

**AI 执行：**
```
🔍 扫描 notes 文件夹...
找到 15 个 .txt 文件

📚 合并文件...
📋 生成目录...

✅ 已生成: combined_notes.md
```

---

## 常见问题

### Q1: 安装 Lima 失败怎么办？

**错误信息：**
```
Failed to install Lima
```

**解决方案：**
```bash
# 手动安装 Lima
brew install lima

# 验证安装
limactl --version

# 重启 Open Cowork
```

---

### Q2: API Key 无效

**错误信息：**
```
❌ API Key 验证失败
```

**检查清单：**
1. 确认 API Key 复制完整（无多余空格）
2. 检查 API Key 是否过期
3. 确认账户有可用额度
4. 尝试重新生成 API Key

**智谱 GLM 示例：**
```bash
# 测试 API Key
curl -X POST https://open.bigmodel.cn/api/paas/v4/chat/completions \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "glm-4",
    "messages": [{"role": "user", "content": "你好"}]
  }'
```

---

### Q3: AI 无法访问文件

**错误信息：**
```
❌ 无法读取文件: /Users/xxx/Documents/file.txt
```

**原因**：文件不在工作目录内。

**解决方案：**
1. 将文件移动到 `~/AI-Workspace/`
2. 或者在设置中更改工作目录

---

### Q4: 执行速度慢

**可能原因：**
- 网络延迟
- 模型响应慢
- 任务复杂度高

**优化建议：**
1. 切换到更快的模型（如 GLM-4-Flash）
2. 拆分大任务为小任务
3. 检查网络连接

---

### Q5: 如何切换模型？

**步骤：**
1. 点击右上角"设置"
2. 选择"模型配置"
3. 选择新的模型提供商
4. 输入对应的 API Key
5. 保存并重启

---

## 进阶技巧

### 技巧 1：编写高质量 Prompt

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

**Prompt 结构：**
```
[背景] 我是一名市场经理
[目标] 分析客户反馈数据
[输入] feedback.csv 文件
[处理] 提取关键问题，按优先级排序
[输出] Markdown 表格，包含问题、频次、优先级
[约束] 只保留前 10 个问题
```

---

### 技巧 2：使用模板

创建常用任务模板，提高效率。

**示例：周报生成模板**
```
根据 work_log.txt 生成本周工作周报：

## 格式要求
- 标题：[姓名] 第 X 周工作周报
- 日期范围：YYYY-MM-DD 至 YYYY-MM-DD

## 内容结构
1. 本周工作总结（3-5 条）
2. 遇到的问题（如有）
3. 下周计划（3-5 条）
4. 需要支持（如有）

## 输出
保存为 weekly_report_YYYYMMDD.md
```

保存为 `templates/weekly_report.txt`，每次使用时：
```
按照 templates/weekly_report.txt 的模板，生成本周周报
```

---

### 技巧 3：链式任务

将复杂任务拆分为多个步骤，逐步执行。

**示例：数据处理流程**
```
任务 1: 清洗数据
- 读取 raw_data.csv
- 删除重复行
- 填充缺失值
- 保存为 cleaned_data.csv

任务 2: 数据分析
- 读取 cleaned_data.csv
- 计算统计指标
- 生成图表数据
- 保存为 analysis_result.json

任务 3: 生成报告
- 读取 analysis_result.json
- 生成 Markdown 报告
- 包含图表和结论
- 保存为 final_report.md
```

---

### 技巧 4：自定义 Skills

创建自己的技能库，复用常见操作。

**示例：创建"邮件分类"Skill**

1. 创建 `skills/email_classifier.md`：
```markdown
# 邮件分类 Skill

## 输入
- 邮件文本文件（.txt 或 .eml）

## 处理逻辑
1. 读取邮件内容
2. 分析邮件类型：
   - 紧急：需要立即处理
   - 重要：需要今天处理
   - 一般：可以稍后处理
   - 垃圾：可以忽略
3. 提取关键信息：
   - 发件人
   - 主题
   - 关键词
   - 行动项

## 输出
- 分类结果（JSON 格式）
- 保存为 email_classification.json
```

2. 使用 Skill：
```
使用 skills/email_classifier.md 处理 inbox 文件夹中的所有邮件
```

---

### 技巧 5：集成外部工具

通过 MCP (Model Context Protocol) 连接外部工具。

**示例：连接浏览器**

1. 安装 Playwright MCP Server：
```bash
npm install -g @modelcontextprotocol/server-playwright
```

2. 在 Open Cowork 设置中添加 MCP 配置：
```json
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-playwright"]
    }
  }
}
```

3. 使用浏览器自动化：
```
使用浏览器访问 https://example.com/products
提取所有产品名称和价格
保存为 products.csv
```

---

## 最佳实践

### 1. 文件组织
```
~/AI-Workspace/
├── inbox/          # 待处理文件
├── processed/      # 已处理文件
├── templates/      # 任务模板
├── skills/         # 自定义技能
├── output/         # 输出结果
└── archive/        # 归档文件
```

### 2. 任务记录
创建 `task_log.md` 记录所有任务：
```markdown
# 任务日志

## 2026-03-03
- [x] 批量重命名照片（50 张）
- [x] 分析销售数据
- [ ] 生成月度报告

## 2026-03-02
- [x] 整理文档
- [x] 邮件分类
```

### 3. 定期备份
```bash
# 备份工作目录
cp -r ~/AI-Workspace ~/AI-Workspace-backup-$(date +%Y%m%d)
```

### 4. 监控 API 使用
定期检查 API 费用：
- 智谱 GLM: https://open.bigmodel.cn/usercenter/apikeys
- Kimi: https://platform.moonshot.cn/console/account
- DeepSeek: https://platform.deepseek.com/usage

---

## 下一步学习

完成本教程后，你可以：

1. **深入学习 Prompt Engineering**
   - 阅读：[Anthropic Prompt Engineering Guide](https://docs.anthropic.com/claude/docs/prompt-engineering)
   - 练习：尝试不同的 Prompt 结构

2. **探索 MCP 工具集成**
   - 浏览器自动化
   - 数据库连接
   - API 集成

3. **过渡到 Claude Code CLI**
   - 学习命令行基础
   - 掌握更强大的编程能力

4. **加入社区**
   - GitHub Discussions: https://github.com/different-ai/openwork/discussions
   - Discord: [链接待补充]

---

## 参考资源

### 官方文档
- [OpenWork GitHub](https://github.com/different-ai/openwork)
- [智谱 GLM API 文档](https://open.bigmodel.cn/dev/api)
- [Kimi API 文档](https://platform.moonshot.cn/docs)
- [DeepSeek API 文档](https://platform.deepseek.com/api-docs)

### 社区资源
- [Claude Cowork 官方指南](https://support.claude.com/en/articles/13345190-get-started-with-cowork)
- [Awesome AI Coding Tools](https://github.com/sourcegraph/awesome-code-ai)

### 视频教程
- [待补充]

---

## 更新日志

- **2026-03-03**: 初始版本发布
- 后续更新将在此记录

---

**祝你使用愉快！如有问题，欢迎在 GitHub Issues 提问。**
