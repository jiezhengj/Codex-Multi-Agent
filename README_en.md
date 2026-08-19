[English](README_en.md) | [中文](README_zh.md)

# Project Overview

This repository provides a comprehensive guide and configuration blueprint for **dynamic task orchestration and model routing** within OpenAI Codex's native Multi-Agent architecture.

Using minimal, configuration-driven setup (`.codex/config.toml` + `AGENTS.md`), it enables intelligent subtask delegation across models (Sol / Terra / Luna), context isolation, and bounded parallelism.

# Documentation Navigation

Complete technical memos and configuration guides are available in both English and Chinese:

- **English Guide**: [Codex Multi-Agent Dynamic Orchestration Memo (English)](Codex%20Multi-Agent%20动态编排备忘录_en.md)
- **Chinese Guide**: [Codex Multi-Agent 动态编排备忘录 (Chinese)](Codex%20Multi-Agent%20动态编排备忘录_zh.md)
- **Chinese README**: [中文 README](README_zh.md)

# Core Design Principles

1. **Native Dynamic Routing**: Deprecate hardcoded subagent setups (such as `luna_worker.toml`) in favor of dynamic model selection based on task properties.
2. **Model Specialization**:
   - **GPT-5.6 Luna**: Narrow, well-defined, repetitive, high-throughput checks, and latency-sensitive lookup tasks.
   - **GPT-5.6 Terra**: Broad codebase exploration, read-heavy scans, and technical investigations.
   - **GPT-5.6 Sol**: Complex multi-step reasoning, architectural decisions, and high-stakes validation.
3. **Context Isolation**: Subagents absorb raw search results, logs, and stack traces, returning only condensed, evidence-backed conclusions to the main thread.
4. **Bounded Parallelism**: Aggressive parallelism for independent read-heavy tasks; strict single ownership for overlapping write-heavy modifications.

# Quick Setup

Maintain only two files in your target project root:

```text
your-project/
├── AGENTS.md
└── .codex/
    └── config.toml
```

For full configuration templates and rollback instructions, see the [Dynamic Orchestration Memo](Codex%20Multi-Agent%20动态编排备忘录_en.md).
