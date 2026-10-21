<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0E7490,100:2563EB&height=200&section=header&text=Learn%20Agent&fontSize=62&fontColor=ffffff&fontAlignY=34&desc=VS%20Code%20Plugin%20%C2%B7%20Teach%2C%20don%27t%20write%20for%20me&descSize=17&descAlignY=58" width="100%" alt="Learning Agent"/>

<h1>编程学习辅助 AI Agent · VS Code 插件</h1>

<p>
<b>装进 VS Code 的学习型编程伴读 —— 不替你写代码，教你看懂代码</b><br/>
原理 → 流程 → 易错点，每一条结论都锚定到你能点回去的行号
</p>

<p>
  <img src="https://img.shields.io/badge/状态-MVP_设计中-f59e0b?style=for-the-badge" alt="status"/>
  <img src="https://img.shields.io/badge/平台-VS_Code-007ACC?style=for-the-badge&logo=visualstudiocode&logoColor=white" alt="VSCode"/>
  <img src="https://img.shields.io/badge/许可-MIT-22C55E?style=for-the-badge" alt="license"/>
  <img src="https://img.shields.io/badge/代码-尚未提交-9CA3AF?style=for-the-badge" alt="code"/>
</p>

<p>
  <a href="#-为什么做">为什么做</a> ·
  <a href="#-功能">功能</a> ·
  <a href="#-技术栈">技术栈</a> ·
  <a href="#-架构">架构</a> ·
  <a href="#-指标">指标</a> ·
  <a href="#-路线图">路线图</a>
</p>

</div>

> [!IMPORTANT]
> **当前状态：MVP 设计中。** 本仓库尚未提交可运行的插件工程代码。
> 下方所有功能与指标均为**设计目标**，不代表已实现的现状。首个可安装版本将随 MVP 里程碑一同提交。

---

## 💡 为什么做

Copilot、CodeGeeX 这类工具把「写代码」变成了复制粘贴。效率上去了，但不少计算机专业学生因此失去了**读懂代码、独立排错、复盘思路**的能力。

本项目是一个跑在 VS Code 里的**学习型**编程 Agent，刻意与生成式工具错位竞争：

| | GitHub Copilot / CodeGeeX | 🎓 本项目 |
|:--|:--|:--|
| 核心价值 | 生成代码、提升开发效率 | 拆解代码、建立编程思维 |
| 目标用户 | 职场开发者 | 计算机专业学生 |
| 输出内容 | 可直接使用的成品代码 | 原理讲解、执行流程、易错点 |
| 幻觉治理 | 提示词工程 | 结构化输入约束 + 可验证引用 |

技术主张一句话：**用本地静态解析产出确定的语法事实，让模型的推理建立在事实之上，而不是让它先猜再自我校验。**

---

## ✨ 功能

| 模块 | 能力 |
|:--|:--|
| 🖥️ **侧边交互面板** | 独立 Webview 侧边栏，常驻 IDE，支持对话渲染、模型切换、会话清空 |
| 👁️ **项目级上下文感知** | 监听文件增删改与编辑器选区，实时感知当前项目结构 |
| 🌳 **静态语法解析** | 基于 web-tree-sitter（WASM）在本地解析语法树，脱离大模型也能拆出函数、循环、变量结构 |
| 🧭 **任务规划引擎** | 规则优先 + 模型兜底的两级路由，区分语法解析、逻辑流程、知识点、排错分析四类场景 |
| 🎯 **三路融合上下文** | 语法树提供骨架、语义检索补齐跨文件片段、LSP 提供类型与引用事实 |
| 🧠 **多层会话记忆** | 会话级窗口压缩、项目级结构化存储、长期向量检索，配套指代消解 |
| 🧑‍🏫 **学习者输出策略** | 强制「原理 → 流程 → 案例」顺序，逐行拆解、标注易错点、结论携带行号引用 |
| 🔗 **反向代码定位** | 讲解中的行号可点击，编辑器自动滚动并高亮对应行 |
| 🔌 **多模型适配** | 可插拔适配层，兼容 DeepSeek / 通义千问 / GPT 等云端 API 与 Ollama 本地模型 |
| 📦 **标准化发布** | VSIX 打包，可上架插件市场，日志与健康自检完备 |

---

## 🛠️ 技术栈

<h3 align="center">运行时与解析</h3>

<p align="center">
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript"/>
  <img src="https://img.shields.io/badge/Node.js-5FA04E?style=for-the-badge&logo=nodedotjs&logoColor=white" alt="Node.js"/>
  <img src="https://img.shields.io/badge/web--tree--sitter-WASM-0E7490?style=for-the-badge" alt="tree-sitter"/>
  <img src="https://img.shields.io/badge/LSP-类型与引用-2563EB?style=for-the-badge" alt="LSP"/>
</p>

<h3 align="center">存储与发布</h3>

<p align="center">
  <img src="https://img.shields.io/badge/SQLite-项目级记忆-003B57?style=for-the-badge&logo=sqlite&logoColor=white" alt="SQLite"/>
  <img src="https://img.shields.io/badge/Ollama-本地模型-000000?style=for-the-badge&logo=ollama&logoColor=white" alt="Ollama"/>
  <img src="https://img.shields.io/badge/VSIX-打包发布-007ACC?style=for-the-badge&logo=visualstudiocode&logoColor=white" alt="VSIX"/>
  <img src="https://img.shields.io/badge/Git-发布链路-F05032?style=for-the-badge&logo=git&logoColor=white" alt="Git"/>
</p>

<sub align="center">解析器运行在扩展宿主内，因此业务逻辑用 TypeScript 而非 Python；首发版本仅支持 Python 语言解析，其余语言按需下载语法包。</sub>

---

## 🏗️ 架构

四层解耦，自上而下职责递减：

```
┌──────────────────────────────────────────────────────────┐
│  ① 视图交互层    Webview 侧边栏 · 选区监听 · 行号反查高亮  │
├──────────────────────────────────────────────────────────┤
│  ② 插件调度层    Extension API · 事件分发 · 生命周期管理   │
├──────────────────────────────────────────────────────────┤
│  ③ Agent 业务层  任务规划 · 上下文优化 · 多层记忆 · 输出策略│
├──────────────────────────────────────────────────────────┤
│  ④ 能力支撑层    Tree-sitter · LSP · 语义检索 · 模型适配层 │
└──────────────────────────────────────────────────────────┘
```

**两个关键工程决策：**

- **用 WASM 而不是 Python 子进程** —— 扩展运行在 Node.js / Electron 扩展宿主里，选 sidecar 方案会要求用户机器上有 Python，直接破坏「安装即用」。代价是语法包需按需分包，以控制首包体积 < 10MB。
- **存储边界严格划分** —— 用户项目目录**只读**，所有记忆、索引、缓存只写入 `context.globalStorageUri`。读服务不持有写入句柄，从设计上杜绝误写项目文件。

### 🔄 一次解读请求的完整链路

```
选中代码 ─▶ 调度层捕获上下文 ─▶ Tree-sitter 解析语法树
                                      │
                        语义检索召回跨文件片段 ◀─┤
                        LSP 查询类型与引用    ◀─┘
                                      ▼
                        任务路由（规则优先 → 模型兜底）
                                      ▼
                        上下文裁剪 / 分片 / 拼接记忆
                                      ▼
                              大模型推理（流式）
                                      ▼
                        输出策略格式化 + 行号引用校验
                                      ▼
                        面板渲染 ─▶ 点击行号反向高亮代码
```

---

## 📊 设计指标

以下均为**设计值，尚未实测**：

| 指标 | 定义 | 目标值 |
|:--|:--|:--|
| 🪙 Token 节省率 | 相对全量投喂的输入 token 降幅 | ≥ 60% |
| 🎯 检索 Recall@5 | 答案片段被召回进上下文的比例 | ≥ 85% |
| ✅ 讲解事实准确率 | 讲解中事实陈述正确的比例 | ≥ 90% |
| 👻 幻觉率 | 相对纯 LLM 基线的降幅 | ≥ 30% |
| ⚡ 首 Token 延迟 | 提交问题到首个 token | P95 < 2500ms |
| 🚀 冷启动耗时 | 插件激活到面板可用 | P95 < 1500ms |

配套设计了一组**单盲对照实验**：50 段学生代码，A 组全量投喂、B 组走三路上下文管线，同一模型同一温度，3 名评分者独立打分。
结论无论正负都会公开——把「我认为有效」变成「我验证过是否有效」。

---

## 🚀 快速开始

> 插件尚未发布。以下为 MVP 交付后的预期流程，仅供参考。

```bash
# 1. 克隆仓库
git clone git@github.com:Keith-hq/Programming-Assisted-Learning-AI-Agent-VS-Code-Plugin.git

# 2. 安装依赖并编译
npm install
npm run compile

# 3. 打包为可安装插件
npx vsce package

# 4. 在 VS Code 中安装生成的 .vsix
code --install-extension programming-learning-agent-*.vsix
```

首次使用需在设置中填入**云端模型 API Key**，或先启动本地模型：

```bash
ollama serve
ollama run qwen2.5-coder
```

---

## 🧭 路线图

- [x] 架构设计与技术选型
- [ ] **第一阶段 · MVP**：Python 单语言 + 代码解读任务 + 单云端模型 + 会话级记忆
- [ ] 第二阶段：语义检索通路、项目级记忆
- [ ] 第三阶段：多语言语法包、Ollama 适配、模型切换
- [ ] 第四阶段：学习报告、错题本、知识点关联、大样本效果实验

---

## ⚖️ 使用边界

本项目定位是**理解代码**，不是完成作业。插件内不提供「一键生成完整可提交作业」的入口，对索取成品的请求会转为引导式回答。请在你所在学校的规定范围内使用。

代码默认仅上传构造后的上下文片段，不上传整文件或整个项目；上传前会扫描疑似密钥、令牌并提示。

---

## 📄 License

[MIT](LICENSE)

<div align="center">

<sub>让 AI 教你怎么想，而不是替你写完。</sub>

</div>
