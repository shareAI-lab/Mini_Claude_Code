# Mini Claude Code

**从零开始构建你自己的编程 Agent。**

[English](./README.md)

<img height="400" alt="demo" src="https://github.com/user-attachments/assets/0e1e31f8-064f-4908-92ce-121e2eb8d453" />

## 这是什么？

一个渐进式教程，揭开 Claude Code、Cursor Agent、Codex CLI 等 AI 编程 Agent 的神秘面纱。

**4 个版本，总共约 1000 行，每个版本只添加一个概念：**

| 版本 | 行数 | 新增内容 | 核心洞察 |
|------|------|---------|---------|
| [v0](./v0_bash_agent.py) | ~50 | 1 个 bash 工具 | Bash 就是一切 |
| [v1](./v1_basic_agent.py) | ~200 | 4 个核心工具 | 模型即代理 |
| [v2](./v2_todo_agent.py) | ~300 | Todo 追踪 | 显式规划 |
| [v3](./v3_subagent.py) | ~450 | 子代理 | 分而治之 |

## 快速开始

```bash
pip install anthropic

# 编辑任意文件设置 API key，然后：
python v0_bash_agent.py  # 极简版
python v1_basic_agent.py # 核心 Agent 循环
python v2_todo_agent.py  # + Todo 规划
python v3_subagent.py    # + 子代理
```

## 核心模式

每个编程 Agent 都只是这个循环：

```python
while True:
    response = model(messages, tools)
    if response.stop_reason != "tool_use":
        return response.text
    results = execute(response.tool_calls)
    messages.append(results)
```

就这样。模型持续调用工具直到完成。其他一切都是精化。

## 文件结构

```
mini-claude-code/
├── v0_bash_agent.py       # ~50 行: 1 个工具，递归子代理
├── v0_bash_agent_mini.py  # ~16 行: 极限压缩
├── v1_basic_agent.py      # ~200 行: 4 个工具，核心循环
├── v2_todo_agent.py       # ~300 行: + TodoManager
├── v3_subagent.py         # ~450 行: + Task 工具，代理注册表
└── docs/                  # 详细文档 (中英双语)
```

## 核心概念

### v0: Bash 就是一切
一个工具。递归自调用实现子代理。证明核心是极小的。

### v1: 模型即代理
4 个工具 (bash, read, write, edit)。完整 Agent 在一个函数里。

### v2: 结构化规划
Todo 工具让计划显式化。约束赋能复杂任务。

### v3: 子代理机制
Task 工具生成隔离的子代理。上下文保持干净。

## 深入阅读

**技术教程 (docs/):**

| English | 中文 |
|---------|------|
| [v0: Bash is All You Need](./docs/v0-bash-is-all-you-need.md) | [v0: Bash 就是一切](./docs/v0-Bash就是一切.md) |
| [v1: Model as Agent](./docs/v1-model-as-agent.md) | [v1: 模型即代理](./docs/v1-模型即代理.md) |
| [v2: Structured Planning](./docs/v2-structured-planning.md) | [v2: 结构化规划](./docs/v2-结构化规划.md) |
| [v3: Subagent Mechanism](./docs/v3-subagent-mechanism.md) | [v3: 子代理机制](./docs/v3-子代理机制.md) |

**原创文章 (articles/) - 公众号风格:**
- [v0文章](./articles/v0文章.md) | [v1文章](./articles/v1文章.md) | [v2文章](./articles/v2文章.md) | [v3文章](./articles/v3文章.md)

## 生产版本

这是学习用的。生产环境请使用：

**[Kode](https://github.com/anthropics/kode)** - 全功能开源 Claude Code

## 设计哲学

> 模型是 80%，代码是 20%。

Claude Code 能工作，不是因为巧妙的工程，而是因为模型被训练成了 Agent。我们的工作就是给它工具，然后闪开。

## License

MIT

---

**模型即代理。这就是全部秘密。**

[@baicai003](https://x.com/baicai003)
