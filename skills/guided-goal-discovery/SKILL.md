---
name: guided-goal-discovery
description: Guide multi-turn goal discovery with one question and selectable options per round, waiting for the user before continuing. Use when the user requests guided questions, invokes this skill, or needs help clarifying vague or conflicting goals. Do not auto-start discovery for clear execution tasks or aligned continuations.
---

# Guided Goal Discovery

Help the user discover and confirm a goal through multi-turn collaboration instead of requiring a finished brief or guessing the final result. Treat sparse language, uncertainty, and “I don’t know” as valid starting material. The interaction itself is part of the deliverable: offer directions, receive a real choice or correction, refine the understanding, and continue. End with a user-confirmed goal consensus and a concrete 0-to-1 launch plan, then hand off to execution.

## Interaction contract

- When the user invokes this skill or requests guided discovery, enter the collaborative question-and-choice loop. Do not replace it with a one-shot solution because you believe you understand the goal.
- During discovery, ask one decision-relevant question per turn, offer two or three concrete directions plus free-form input, and stop for the user's reply. Use the next turn to incorporate that reply and ask the next relevant question.
- Choose the question whose answer would most change the direction; do not follow a fixed questionnaire.
- Make questions easy to answer through concrete contrasts, examples, outcomes, or felt differences.
- Default to numbered text options. Clickable controls are optional; the skill must work without them.
- Match the user’s language and level of abstraction; avoid unexplained professional jargon.
- Never ask again for information already supplied.
- Let the user revise or revoke any earlier confirmation at any time, including during a turn. Update the affected assumptions and next action without restarting already settled discovery.
- Do not make the user write a professional brief. Translate everyday reactions into usable requirements.

Act as a hypothesis-generating collaborator, not a passive interviewer. When the user lacks an answer, propose two or three meaningfully different working hypotheses. Recommend one when helpful and explain why, but mark it as provisional. Let the user’s attraction, resistance, corrections, and rejection carry more weight than the recommendation.

Keep recommendations distinct from decisions. A plausible inference, model confidence, silence, or selecting one direction is not permission to fill in every remaining goal dimension and deliver the final solution. If an explicitly invoked discovery request already contains a detailed brief, start by confirming the most consequential interpretation instead of silently switching to execution. Do not manufacture extra rounds after the user has confirmed the goal and asked to proceed.

## Distinguish the three layers

Keep these concepts separate throughout discovery:

- **Goal:** the change that should occur if the work succeeds.
- **Deliverable:** the concrete result produced in this project or phase.
- **Method:** the means, medium, tool, or process used to produce it.

Distinguish a requested format or method from the underlying goal. Clarify only if that distinction would change the result; preserve an explicit format choice rather than reopening it by default.

## Use the eight internal dimensions

Use the following as an internal map, never as eight mandatory questions. Group them into three user-visible stages.

### Meaning

1. **Purpose:** What should become different when the work succeeds?
2. **Recipient and context:** For whom, where, when, and under what conditions must it work?
3. **Experience:** What should the recipient feel, understand, believe, decide, or do?

### Form

4. **Deliverable:** What concrete result must exist at the end of this phase?
5. **Scope:** What belongs in this phase, and what does not?

### Judgment

6. **Boundaries:** What must be preserved, and what must never appear or be compromised?
7. **Success evidence:** What observable result or explicit judgment would show that the goal has been met?
8. **Tradeoff:** When desirable qualities conflict, which one takes priority?

Ask about purpose and experience before methods and formatting unless a hard constraint already controls the task. Skip dimensions already clear or irrelevant to the first project phase.

## Guide the three stages

### 1. Clarify meaning

Extract the existing seed: the situation, dissatisfaction, desired change, imagined recipient, emotional or practical intention, and any explicit references or corrections. Help the user discover why the work should exist and what response it should create.

### 2. Clarify form

Translate the confirmed meaning into an appropriate deliverable and bounded project phase. Decide what the 0-to-1 version must contain and what can remain outside the current scope. Do not add decorative complexity merely because the starting idea is sparse.

### 3. Clarify judgment

Identify non-negotiables, excluded directions, success evidence, and priority when requirements conflict. Use rejection as evidence: infer the violated principle beneath the rejected example instead of merely avoiding its surface features.

## Make uncertainty answerable

When the user says “I don’t know,” do not repeat or broaden the question. Offer two or three genuinely different hypotheses and ask which feels closer—or which feels wrong.

## Offer options and wait

Each ordinary discovery round contains a brief update of what the last reply clarified, one question, and two or three meaningfully different options. Give each option a short label and a one-sentence effect or tradeoff. Mark a recommendation only when useful, never select it for the user. Allow a number, a label, a blend, rejection of all options, or another idea. For nuanced personal expression, offer directions as non-exhaustive prompts rather than forcing a false choice.

For example, after the user introduces a film about endless effort:

> 面对这种徒劳，你更希望影片留下哪种态度？
> 1. 反抗：即使终点不可达，行动本身仍有意义。
> 2. 崩塌：希望在重复失败中逐渐耗尽。
> 3. 荒诞：让观众怀疑“必须抵达终点”这个要求。
> 你可以回复序号、混合方向，或补充其他想法。

End the turn here. If the user chooses “3,” incorporate absurdity as the chosen direction and continue with the next unresolved dimension; do not jump straight to a complete script, format, and production plan. Do not prewrite later questions as an intake form or simulate the user's future answers.

Native choice tools may replace the numbered presentation when exposed and permitted in the current mode. Follow their current schema and preserve free-form input without duplicating a host-provided “Other” route. A Plan-only tool remains Plan-only. With an asynchronous control, a submission receipt or preselection is not an answer: end the turn and resume on the actual user reply, without polling or submitting another discovery question. Follow explicit host instructions for a completed no-answer result without presenting an assumption as user confirmation. No GUI, mode switch, or model-specific tool is required.

An exploratory choice confirms only the direction it names, not the entire plan. A checkpoint confirmation settles that checkpoint, not every later stage. Likewise, “you choose this option” delegates that choice, not the entire collaboration. Only an explicit instruction to stop questioning and decide/proceed for the whole task ends discovery early. Later explanations or corrections override the affected interpretation.

Prefer questions such as:

- “Should this reassure the recipient, unsettle them, or make them act?”
- “Is recognition more important than novelty, or the reverse?”
- “Would failure mean nobody understands it, or that they understand but feel nothing?”

Do not produce a full solution before the underlying direction is clear; concrete solutions can prematurely anchor the goal.

## Pause at stage checkpoints

At a meaningful stage boundary, briefly summarize only changed information in the categories that apply:

- **Confirmed:** explicitly stated and accepted by the user.
- **Working interpretation:** inferred by Codex but not yet confirmed.
- **Excluded:** rejected or determined inconsistent with the goal.
- **Needs confirmation:** still capable of changing the next stage.

Before moving to a new stage, make the shared understanding visible and let the user confirm or correct any consequential interpretation not already explicitly confirmed. Offer “confirm and continue” and “revise” as the single question for that turn, with free-form correction. Carry forward already confirmed decisions without asking them again, but do not label inferred stages as settled simply to shorten the dialogue. The stages are a map, not a fixed number of rounds.

When a checkpoint is genuinely binary, offer confirmation and correction as concise text options; an available permitted control may present the same choices. Keep the free-form correction path open.

## Determine readiness

Stop discovery when all of the following are true:

- the user has confirmed the shared goal, not merely been predicted to agree;
- the desired change, relevant recipient or context, and intended experience are clear;
- the current deliverable and scope are defined;
- the decisive boundaries and tradeoff priorities are known;
- success can be recognized;
- remaining unknowns concern implementation rather than the project’s core direction;
- a first milestone can directly make the project begin to exist.

If a missing goal decision prevents a useful starting point, offer alternatives and wait for the user's response. Implementation uncertainty can belong in the launch plan; it need not prolong discovery. Model confidence is not a substitute for user participation. Respect an explicit request to stop discovery and let you decide the whole task, but do not infer it from a short answer, a local choice, or approval of one checkpoint.

## Produce the final output

Present **Goal Consensus + 0-to-1 Launch Plan** in four sections:

### Meaning consensus

State the core goal, why it matters, the recipient and context, and the intended experience or change.

### Project form

State the deliverable, current scope, and what remains outside this phase.

### Judgment criteria

State the non-negotiables, excluded directions, tradeoff priorities, and success evidence.

### 0-to-1 launch plan

State the first milestone that makes the project begin to exist, why it is the correct starting point, the required inputs and resources, the recommended execution path, and the skill, tool, or workflow that should receive the handoff.

Include working assumptions or unresolved items only when they genuinely remain; do not force empty template fields.

After the shared direction is confirmed, present this synthesis and offer “adopt and start” or “revise” before execution. If the user already explicitly approved the plan and requested execution, do not ask again. Keep the four sections concise and proportional to the project; they summarize the collaboration rather than replacing it.

## Exit and hand off

After final confirmation to execute or an explicit whole-task instruction to stop discovery and proceed:

- exit guided mode;
- pass the complete goal consensus and launch plan to the appropriate execution skill, tool, or workflow without asking the user to restate the request;
- preserve all confirmed boundaries and priorities in the handoff;
- begin execution immediately when the original request and final confirmation already authorize it;
- do not restart goal discovery during an aligned continuation unless the user changes the direction materially.

## Guardrails

- Do not overwhelm the user with a multi-question intake form.
- Do not pursue completeness through low-value questions.
- Do not present assumptions as confirmed facts.
- Do not lock onto the first idea before exposing meaningful alternatives.
- Do not force a choice merely because a structured-choice control is available.
- Do not treat a selected option as more authoritative than the user’s explanation or later correction.
- Do not substitute decorative detail for a missing goal.
- Do not praise every answer; synthesize it into better decisions.
- Do not end discovery merely because the model thinks the project is ready; honor the user's confirmations and explicit request to begin.
