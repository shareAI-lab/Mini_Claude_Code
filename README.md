# Mini Claude Code

**Build your own coding agent from scratch.**

[中文文档](./README_zh.md)

<img height="400" alt="demo" src="https://github.com/user-attachments/assets/0e1e31f8-064f-4908-92ce-121e2eb8d453" />

## What is this?

A progressive tutorial that demystifies AI coding agents like Claude Code, Cursor Agent, and Codex CLI.

**4 versions, ~1000 lines total, each adding one concept:**

| Version | Lines | What it adds | Core insight |
|---------|-------|--------------|--------------|
| [v0](./v0_bash_agent.py) | ~50 | 1 bash tool | Bash is all you need |
| [v1](./v1_basic_agent.py) | ~200 | 4 core tools | Model as Agent |
| [v2](./v2_todo_agent.py) | ~300 | Todo tracking | Explicit planning |
| [v3](./v3_subagent.py) | ~450 | Subagents | Divide and conquer |

## Quick Start

```bash
pip install anthropic

# Edit any file to set your API key, then:
python v0_bash_agent.py  # Minimal
python v1_basic_agent.py # Core agent loop
python v2_todo_agent.py  # + Todo planning
python v3_subagent.py    # + Subagents
```

## The Core Pattern

Every coding agent is just this loop:

```python
while True:
    response = model(messages, tools)
    if response.stop_reason != "tool_use":
        return response.text
    results = execute(response.tool_calls)
    messages.append(results)
```

That's it. The model calls tools until done. Everything else is refinement.

## File Structure

```
mini-claude-code/
├── v0_bash_agent.py       # ~50 lines: 1 tool, recursive subagents
├── v0_bash_agent_mini.py  # ~16 lines: extreme compression
├── v1_basic_agent.py      # ~200 lines: 4 tools, core loop
├── v2_todo_agent.py       # ~300 lines: + TodoManager
├── v3_subagent.py         # ~450 lines: + Task tool, agent registry
└── docs/                  # Detailed explanations (EN + ZH)
```

## Key Concepts

### v0: Bash is All You Need
One tool. Recursive self-calls for subagents. Proves the core is tiny.

### v1: Model as Agent
4 tools (bash, read, write, edit). The complete agent in one function.

### v2: Structured Planning
Todo tool makes plans explicit. Constraints enable complex tasks.

### v3: Subagent Mechanism
Task tool spawns isolated child agents. Context stays clean.

## Deep Dives

**Technical tutorials (docs/):**

| English | 中文 |
|---------|------|
| [v0: Bash is All You Need](./docs/v0-bash-is-all-you-need.md) | [v0: Bash 就是一切](./docs/v0-Bash就是一切.md) |
| [v1: Model as Agent](./docs/v1-model-as-agent.md) | [v1: 模型即代理](./docs/v1-模型即代理.md) |
| [v2: Structured Planning](./docs/v2-structured-planning.md) | [v2: 结构化规划](./docs/v2-结构化规划.md) |
| [v3: Subagent Mechanism](./docs/v3-subagent-mechanism.md) | [v3: 子代理机制](./docs/v3-子代理机制.md) |

**Original articles (articles/) - Chinese only, social media style:**
- [v0文章](./articles/v0文章.md) | [v1文章](./articles/v1文章.md) | [v2文章](./articles/v2文章.md) | [v3文章](./articles/v3文章.md)

## Production Version

This is for learning. For production use:

**[Kode](https://github.com/anthropics/kode)** - Full-featured open source Claude Code

## Philosophy

> The model is 80%. Code is 20%.

Claude Code works not because of clever engineering, but because the model is trained to be an agent. Our job is to give it tools and stay out of the way.

## License

MIT

---

**Model as Agent. That's the whole secret.**

[@baicai003](https://x.com/baicai003)
