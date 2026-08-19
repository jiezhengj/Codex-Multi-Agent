[English](README_en.md) | [中文](README_zh.md)

# 项目概述

本项目提供了针对 OpenAI Codex 原生 Multi-Agent 架构的**动态任务编排与模型路由指南**。

旨在通过轻量化配置（`.codex/config.toml` + `AGENTS.md`），实现主 Agent 与子 Agent（SubAgent）之间的智能任务分发，充分发挥不同模型（Sol / Terra / Luna）的优势，并达成上下文隔离与高效协作。

# 文档导航

本项目包含中英双语的完整技术备忘与配置指南：

- **中文版指南**：[Codex Multi-Agent 动态编排备忘录 (中文)](Codex%20Multi-Agent%20动态编排备忘录_zh.md)
- **英文版指南**：[Codex Multi-Agent Dynamic Orchestration Memo (English)](Codex%20Multi-Agent%20动态编排备忘录_en.md)
- **英文版 README**：[English README](README_en.md)

# 核心设计原则

1. **原生动态路由**：放弃传统的固定 SubAgent 配置（如 `luna_worker.toml`），交由 Codex 根据子任务特征动态选择最适合的模型。
2. **多模型协同分工**：
   - **GPT-5.6 Luna**：适用于窄范围、明确、高吞吐、重复性查询与低延迟任务。
   - **GPT-5.6 Terra**：适用于大范围代码库探索、Read-heavy 扫描与技术调查。
   - **GPT-5.6 Sol**：适用于复杂多步骤推理、架构决策与高风险验证。
3. **上下文隔离（Context Isolation）**：由 SubAgent 消化繁杂的搜索输出、日志和调用栈，向主线程（Main Thread）返回精炼的高信息密度结论。
4. **受控并行**：Read-heavy 任务积极并行，Overlapping Write-heavy 任务严格保持单一 Owner。

# 快速配置

在项目根目录下仅需维护两个文件：

```text
your-project/
├── AGENTS.md
└── .codex/
    └── config.toml
```

详细规则配置与还原方法请参阅完整的[动态编排备忘录](Codex%20Multi-Agent%20动态编排备忘录_zh.md)。
