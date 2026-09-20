# Guided Goal Discovery

[简体中文](README.md)

**Current version: v0.3.1 | GPT-6 Astra multi-turn collaboration**

A Codex skill that turns vague intentions, sparse ideas, and conflicting preferences into a shared goal and a concrete 0-to-1 launch plan through one decision-relevant question at a time.

It does not require the user to arrive with a complete brief, and it avoids producing a polished solution before the direction is understood. The skill first clarifies why the project should exist, who it is for, and what should change; it then defines the current deliverable, boundaries, judgment criteria, and the first milestone that makes execution genuinely begin.

Each round defaults to two or three numbered text options, waits for the user's selection or explanation, and uses that response to shape the next round. Users can blend directions, offer another idea, or overturn earlier choices. Clickable controls are optional, not a prerequisite; model confidence never substitutes for user confirmation.

**Inputs:** vague intentions, sparse creative seeds, conflicting preferences, uncertainty about where to begin, or requests whose outcome would change fundamentally under different interpretations.

**Outputs:** a confirmed meaning consensus, project form, judgment criteria, 0-to-1 launch plan, and a lossless handoff to execution.

## Features

- Treats “I don't know,” a lack of ideas, and difficulty articulating a goal as valid starting material.
- Asks only one high-value question per turn instead of presenting an intake form.
- Proposes two or three meaningfully different working hypotheses so users can discover direction through attraction, resistance, and correction.
- Separates the goal, current deliverable, and implementation method instead of treating the first requested format as the true purpose.
- Moves through Meaning, Form, and Judgment, confirming only consequential interpretations that remain unresolved.
- Uses eight internal dimensions: purpose, recipient and context, experience, deliverable, scope, boundaries, success evidence, and tradeoffs.
- Defaults to numbered text choices and waits for a reply; native clickable controls are optional.
- Preserves free-form input and reversibility; exploratory selections are provisional, while explicit confirmation or execution instructions count.
- Produces a Goal Consensus + 0-to-1 Launch Plan and hands all confirmed boundaries and priorities to execution.
- Avoids interrupting clear requests, factual questions, diagnostics, revisions, or aligned continuation work.

## Method principles

| Principle | Implementation |
|---|---|
| One question at a time | Ask only the single question whose answer would materially change the direction; do not use a fixed questionnaire |
| Meaning before method | Clarify why the work should exist, for whom, and with what intended experience before discussing medium, format, or tools |
| Active hypotheses | When the user cannot answer, propose two or three genuinely different working interpretations instead of returning the creative burden |
| Options and waiting | Offer two or three numbered alternatives and free-form input; wait for the user's response before the next round |
| Free correction | Always allow “Other,” blended directions, added conditions, reversals, or replacement of the proposed frame |
| Three-layer separation | Keep the goal, current deliverable, and implementation method distinct throughout discovery |
| Three-stage progression | Collaborate through Meaning → Form → Judgment; user confirmations, not model inferences, settle consequential interpretations |
| Eight-dimension map | Internally check purpose, recipient and context, experience, deliverable, scope, boundaries, success evidence, and tradeoffs |
| Transparent state | Separate confirmed facts, working interpretations, excluded directions, and items that still need confirmation |
| Recognizable success | Define non-negotiables, excluded directions, priority conflicts, and observable success evidence before launch |
| Lossless handoff | Deliver a complete goal consensus and 0-to-1 plan so execution does not ask the user to restate the request |

## Options and multi-turn collaboration

v0.3.1 defaults to text options → user reply → updated understanding → next round:

- Ask one key question with two or three concrete directions and short explanations.
- Allow a number, a blend, or free-form input, then stop and wait.
- Continue exploring unresolved dimensions after each reply instead of immediately producing a full result.
- A checkpoint confirmation settles that stage only; delegating one choice does not delegate the whole collaboration.
- Synthesize the confirmed goal into a launch plan and execute when requested; honor an explicit instruction to stop discovery and decide/proceed for the whole task.

No custom GUI is bundled. Suitable host controls may optionally present the same choices; a tool receipt or preselected option is not a user answer.

## GPT-6 Astra support

v0.3.1 draws on [OpenAI’s Astra skill migration guidance](https://developers.openai.com/blog/rethinking-skills-and-prompts-for-gpt-6-astra) to clarify invocation while preserving the user's requested multi-turn collaboration, rather than letting the model infer every decision and deliver immediately. The skill does not pin a model or change global settings. Select **GPT-6 Astra** in the host and invoke this skill. Other skill-compatible models can still use it.

| Adaptation | Implementation |
|---|---|
| Correct invocation | Enter guided collaboration when invoked or requested; do not interrupt ordinary clear execution tasks automatically |
| Options each round | Ask one key question with two or three concrete directions and free expression; no clickable UI required |
| Real user replies | Stop after the question and continue from the actual answer; never simulate replies or choose defaults on the user's behalf |
| No premature result | Model confidence, a local choice, or checkpoint approval does not authorize an immediate final solution |
| Multi-turn collaboration | Explore meaning, form, and judgment through shared confirmation; allow corrections without imposing a fixed round count |
| Explicit handoff | Synthesize the confirmed goal into a launch plan and execute when requested; honor an explicit instruction to stop discovery |

This update focuses on invocation and collaborative behavior, not mandatory clickable interactions. Structural validation is not a model behavior test. Live multi-turn acceptance scenarios are documented in the [acceptance checklist](tests/acceptance.md).

## Installation

Copy `skills/guided-goal-discovery` into the Codex skills directory.

### PowerShell

```powershell
$skillsRoot = Join-Path $env:USERPROFILE ".codex\skills"
Copy-Item -Recurse -Force .\skills\guided-goal-discovery $skillsRoot
```

### macOS or Linux

```bash
cp -R skills/guided-goal-discovery ~/.codex/skills/
```

Restart or refresh Codex if the skill does not appear immediately.

## Usage

Invoke the skill explicitly:

```text
Use $guided-goal-discovery to ask one question with options each round. Wait for my choice or explanation before continuing, and clarify the goal together over multiple turns instead of giving the final plan immediately.
```

For a vague creative seed:

```text
Use $guided-goal-discovery to help me find what this visual idea truly wants to express before choosing its form.
```

For an undefined project:

```text
Use $guided-goal-discovery to turn these fragments into a shared goal and a concrete 0-to-1 starting plan.
```

## Core output

The final output contains four parts:

1. **Meaning consensus:** the core goal, why it matters, recipient and context, and intended experience or change.
2. **Project form:** the current deliverable, scope, and what remains outside this phase.
3. **Judgment criteria:** non-negotiables, excluded directions, tradeoff priorities, and success evidence.
4. **0-to-1 launch plan:** the first milestone, required inputs and resources, recommended execution path, and handoff target.

## Repository structure

```text
guided-goal-discovery/
├── README.md
├── README.en.md
├── LICENSE
├── tests/
│   └── acceptance.md
└── skills/
    └── guided-goal-discovery/
        ├── SKILL.md
        └── agents/
            └── openai.yaml
```

Repository-level documentation and licensing stay outside the skill directory so the installable package remains minimal.

## Validation

Use the `skill-creator` validator to check the skill structure:

```bash
python -X utf8 /path/to/skill-creator/scripts/quick_validate.py skills/guided-goal-discovery
```

## License

[MIT License](LICENSE)
