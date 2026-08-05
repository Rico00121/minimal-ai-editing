# 英文论文最小化降 AI 痕迹编辑

这是一个面向英文论文、学位论文和学术写作的 Agent Skill，用于在尽量保留作者原始表达的前提下降低文本中明显的 AI 写作痕迹和 AI rate。

它不会把整段文字重新润色成过于流畅的“标准答案”，而是优先处理模板化连接词、过度正式的词语、重复的解释结构和过于整齐的句子节奏。它还支持先提取关键句并翻译成中文，由作者自己决定逻辑顺序，再对英文进行有限整理。

需要注意，AI 检测工具可能产生误判，本 Skill 不保证任何检测分数，也不用于伪造作者身份。它更适合帮助作者保留自己的写作逻辑，并减少过度模板化的表达。

## 主要功能

- 每句话通常只修改一个明显问题
- 保留引用、LaTeX 命令、数字、事实和技术术语
- 避免不必要的高级词、连接词和总结句
- 支持把关键句编号并翻译成中文后重新排序
- 对作者自己的英文粗稿只做必要的语法修正
- 当反复改写无效时，停止整段重写并回到作者主导的写作流程

## 安装

### Codex

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/Rico00121/minimal-ai-editing.git ~/.codex/skills/minimal-ai-editing
```

### Claude Code

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/Rico00121/minimal-ai-editing.git ~/.claude/skills/minimal-ai-editing
```

### 使用通用 Agent Skills 目录的 Agent

```bash
mkdir -p ~/.agents/skills
git clone https://github.com/Rico00121/minimal-ai-editing.git ~/.agents/skills/minimal-ai-editing
```

其他支持 `SKILL.md` 的 Agent，可以把本仓库克隆到该平台配置的技能目录中。仓库根目录本身就是完整的 Skill，不需要复制其中的文件。

## 使用

在对话中直接指定：

```text
请使用 $minimal-ai-editing 对下面的英文论文段落做最小化修改。
每句话最多修改一个明显的 AI 表达，保留引用和 LaTeX。
```

需要自己调整逻辑顺序时：

```text
请先使用 $minimal-ai-editing 提取关键句，编号并翻译成中文。
我给出顺序后，你再整理英文。
```

## 维护原则

本仓库只维护一份 `SKILL.md`。不同 Agent 直接使用同一个文件，避免多平台副本之间出现规则不一致。
