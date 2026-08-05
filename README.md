# 英文论文最小化降 AI 痕迹编辑

这是一个面向英文论文、学位论文和学术写作的 Agent Skill，用于在尽量保留作者原始表达的前提下降低文本中明显的 AI 写作痕迹和 AI rate。

它不会把整段文字重新润色成过于流畅的“标准答案”，而是优先处理模板化连接词、过度正式的词语、重复的解释结构和过于整齐的句子节奏。它还支持先提取关键句并翻译成中文，由作者自己决定逻辑顺序，再对英文进行有限整理。

需要注意，AI 检测工具可能产生误判，本 Skill 不保证任何检测分数，也不用于伪造作者身份。它更适合帮助作者保留自己的写作逻辑，并减少过度模板化的表达。

## 使用声明

本 Skill 仅作实验用途，仅应在 AI 辅助写作场景下使用。它用于帮助作者检查和修改自己已经完成的英文内容，不建议将 AI 作为投机取巧完成论文的主要工具。论文的研究、论证、数据和最终文字责任应由作者本人承担。

## 主要功能

- 每句话通常只修改一个明显问题
- 保留引用、LaTeX 命令、数字、事实和技术术语
- 避免不必要的高级词、连接词和总结句
- 支持把关键句编号并翻译成中文后重新排序
- 对作者自己的英文粗稿只做必要的语法修正
- 当反复改写无效时，停止整段重写并回到作者主导的写作流程

## 安装

### 通过提示词让 Agent 自动安装

如果当前 Agent 能够联网、执行 Git 命令并写入个人技能目录，可以直接发送下面这段提示词：

```text
请从 https://github.com/Rico00121/minimal-ai-editing 安装 minimal-ai-editing Skill。
先识别当前 Agent 使用的个人 Skills 目录，再将仓库克隆到该目录下的 minimal-ai-editing 文件夹。
不要修改仓库中的 SKILL.md。如果目标文件夹已经存在，不要直接覆盖，先检查现有安装并告诉我当前状态。
安装后确认 SKILL.md 存在，并告诉我实际安装路径以及如何在对话中调用 $minimal-ai-editing。
```

Agent 应根据自身环境选择技能目录，例如 Codex 使用 `~/.codex/skills`，Claude Code 使用 `~/.claude/skills`，采用通用 Agent Skills 目录的平台可以使用 `~/.agents/skills`。如果 Agent 没有联网、终端执行或目录写入权限，这种方式无法自动完成安装，需要改用下面的手动安装命令。

### 样例对话

**用户：**

```text
请从 https://github.com/Rico00121/minimal-ai-editing 安装 minimal-ai-editing Skill。
安装前先检查目标目录，不要覆盖已有内容。完成后告诉我安装路径和调用方法。
```

**Agent：**

```text
当前环境使用 ~/.codex/skills 作为个人 Skills 目录。
目标目录 minimal-ai-editing 不存在，仓库已经克隆到 ~/.codex/skills/minimal-ai-editing。
我已确认 SKILL.md 存在。你可以在对话中使用 $minimal-ai-editing 调用它。
```

**用户：**

```text
请使用 $minimal-ai-editing 检查下面的英文论文段落。
只修改明显的 AI 表达，每句话最多修改一个问题，并保留引用和 LaTeX。
```

**Agent：**

```text
请发送需要检查的英文段落。我会先给出最小化修改后的文本，再简短列出替换点。
```

实际安装路径和 Agent 回复可能因运行环境而不同。

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
