# Guided Goal Discovery

A reusable Codex skill for turning vague intentions into a shared goal and a concrete 0-to-1 launch plan through one decision-relevant question at a time.

一个通过“一次一个关键问题”，把模糊意图整理为目标共识与0→1启动方案的 Codex Skill。

## What it does

- Treats uncertainty and “I don’t know” as valid starting material.
- Distinguishes the true goal from the deliverable and implementation method.
- Uses eight internal dimensions grouped into three user-visible stages: Meaning, Form, and Judgment.
- Offers concrete working hypotheses instead of returning the creative burden to the user.
- Pauses for confirmation after each stage.
- Ends with a confirmed Goal Consensus and 0-to-1 Launch Plan, then hands off to execution.

## Repository structure

```text
skills/
└── guided-goal-discovery/
    ├── SKILL.md
    └── agents/
        └── openai.yaml
```

The repository-level documentation and license stay outside the skill package so the installable skill remains minimal.

## Install

Copy `skills/guided-goal-discovery` into your Codex skills directory.

### PowerShell

```powershell
Copy-Item -Recurse .\skills\guided-goal-discovery "$env:USERPROFILE\.codex\skills\"
```

### macOS or Linux

```bash
cp -R skills/guided-goal-discovery ~/.codex/skills/
```

Restart or reload Codex if the skill does not appear immediately.

## Use

Invoke it explicitly:

```text
Use $guided-goal-discovery to help me clarify a vague idea and establish a concrete 0-to-1 starting point.
```

中文示例：

```text
使用 $guided-goal-discovery，一次问我一个问题，帮助我明确真正目标并形成0→1启动方案。
```

The skill may also activate when unclear purpose would lead to fundamentally different outcomes. It is designed not to interrupt clear requests, factual questions, revisions, diagnostics, or aligned continuation work.

## Core output

The final output contains four parts:

1. Meaning Consensus
2. Project Form
3. Judgment Criteria
4. 0-to-1 Launch Plan

## License

MIT License. See [LICENSE](LICENSE).
