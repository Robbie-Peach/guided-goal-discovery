# Guided Goal Discovery

[简体中文](README.md)

**Current version: v0.3.0 | GPT-6 Astra adaptation**

A Codex skill that turns vague intentions, sparse ideas, and conflicting preferences into a shared goal and a concrete 0-to-1 launch plan through one decision-relevant question at a time.

It does not require the user to arrive with a complete brief, and it avoids producing a polished solution before the direction is understood. The skill first clarifies why the project should exist, who it is for, and what should change; it then defines the current deliverable, boundaries, judgment criteria, and the first milestone that makes execution genuinely begin.

When a direction can be represented by a small set of working hypotheses, the skill prefers native clickable choices supplied by the host. When that control is unavailable, it falls back to the same alternatives as concise numbered text. Users can always choose “Other,” combine directions, explain a reaction, or overturn an earlier selection.

**Inputs:** vague intentions, sparse creative seeds, conflicting preferences, uncertainty about where to begin, or requests whose outcome would change fundamentally under different interpretations.

**Outputs:** a confirmed meaning consensus, project form, judgment criteria, 0-to-1 launch plan, and a lossless handoff to execution.

## Features

- Treats “I don't know,” a lack of ideas, and difficulty articulating a goal as valid starting material.
- Asks only one high-value question per turn instead of presenting an intake form.
- Proposes two or three meaningfully different working hypotheses so users can discover direction through attraction, resistance, and correction.
- Separates the goal, current deliverable, and implementation method instead of treating the first requested format as the true purpose.
- Moves through Meaning, Form, and Judgment, confirming only consequential interpretations that remain unresolved.
- Uses eight internal dimensions: purpose, recipient and context, experience, deliverable, scope, boundaries, success evidence, and tradeoffs.
- Provides native clickable choices when available and equivalent numbered text everywhere else.
- Preserves free-form input and reversibility; exploratory selections are provisional, while explicit confirmation or execution instructions count.
- Produces a Goal Consensus + 0-to-1 Launch Plan and hands all confirmed boundaries and priorities to execution.
- Avoids interrupting clear requests, factual questions, diagnostics, revisions, or aligned continuation work.

## Method principles

| Principle | Implementation |
|---|---|
| One question at a time | Ask only the single question whose answer would materially change the direction; do not use a fixed questionnaire |
| Meaning before method | Clarify why the work should exist, for whom, and with what intended experience before discussing medium, format, or tools |
| Active hypotheses | When the user cannot answer, propose two or three genuinely different working interpretations instead of returning the creative burden |
| Adaptive choices | Use a native structured-choice control when available; otherwise present the same alternatives as concise numbered text |
| Free correction | Always allow “Other,” blended directions, added conditions, reversals, or replacement of the proposed frame |
| Three-layer separation | Keep the goal, current deliverable, and implementation method distinct throughout discovery |
| Three-stage progression | Use Meaning → Form → Judgment as a map; skip settled stages and avoid repeated approval gates |
| Eight-dimension map | Internally check purpose, recipient and context, experience, deliverable, scope, boundaries, success evidence, and tradeoffs |
| Transparent state | Separate confirmed facts, working interpretations, excluded directions, and items that still need confirmation |
| Recognizable success | Define non-negotiables, excluded directions, priority conflicts, and observable success evidence before launch |
| Lossless handoff | Deliver a complete goal consensus and 0-to-1 plan so execution does not ask the user to restate the request |

## Adaptive choice interaction

Since v0.2.0, the skill prefers a host-provided native structured-choice control when one key question can be represented honestly by two or three mutually exclusive directions:

- put the recommended option first when a recommendation is justified and label it clearly;
- describe the effect or tradeoff of every option in one sentence;
- preserve the free-form “Other” route;
- treat exploratory clicks as working interpretations; explicit confirmation or execution choices count, and later corrections still take precedence.

If the current environment exposes no compatible control, the skill presents the same labels and descriptions in text and lets the user answer with a number, a label, a mixture, or a different idea. The repository deliberately bundles no custom GUI, keeping the skill portable across Codex environments.

## GPT-6 Astra support

v0.3.0 follows [OpenAI’s Astra skill migration guidance](https://developers.openai.com/blog/rethinking-skills-and-prompts-for-gpt-6-astra) by shortening the trigger description and removing redundant confirmation gates while preserving one-question discovery and the goal-consensus output. This skill supplies workflow instructions: it does not pin a model or change global Codex settings. Select **GPT-6 Astra** in the host’s model picker. Other skill-compatible models can still use it.

| Adaptation | Implementation |
|---|---|
| Host-aware controls | Use only tools and parameters permitted in the current mode; the model name does not imply GUI availability |
| Synchronous choices | Use permitted controls such as `request_user_input`; do not invoke a Plan-only tool in another mode |
| Asynchronous choices | Handle host-provided `request_user_input_async`; wait for an actual reply rather than treating a receipt or preselected option as an answer |
| Free-form input | Preserve qualifications and blended directions; do not duplicate a host-provided free-text route with another “Other” option |
| Mid-turn correction | Update affected interpretations when the user changes direction without restarting settled discovery |
| Timely execution | Stop mechanical questioning once the direction is confirmed or the user delegates the remaining decisions |

Clickable choices depend on host tools, not on Astra alone. This is an instruction and packaging compatibility update; structural validation is not a model behavior test. Live multi-turn acceptance scenarios are documented in the [acceptance checklist](tests/acceptance.md).

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
Use $guided-goal-discovery to clarify my true goal one question at a time. Offer clickable choices when available, and always let me enter a different idea.
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
