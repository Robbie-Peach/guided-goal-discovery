---
name: guided-goal-discovery
description: Guide a user from a vague intention, sparse creative seed, conflicting preferences, or uncertainty about where to begin toward a shared goal and a concrete 0-to-1 launch plan. Use when the user explicitly asks for guided questions, says they have no clear idea, cannot articulate what they want, or needs purpose clarified before execution; also use when materially different interpretations would produce fundamentally different outcomes and a small reasonable assumption cannot resolve them. Do not use for clear requests, factual questions, revisions, diagnostics, continuation of an already aligned project, or when the user explicitly delegates the decision to Codex.
---

# Guided Goal Discovery

Help the user discover and confirm a goal instead of requiring a finished brief. Treat sparse language, uncertainty, and “I don’t know” as valid starting material. End with a confirmed goal consensus and a concrete 0-to-1 launch plan, then hand off to execution.

## Interaction contract

- Announce entry into guided mode briefly: explain that execution will pause while one question at a time clarifies the goal.
- Ask exactly one decision-relevant question per turn.
- Choose the question whose answer would most change the direction; do not follow a fixed questionnaire.
- Make questions easy to answer through concrete contrasts, examples, outcomes, or felt differences.
- Prefer a native structured-choice control for bounded alternatives when the runtime provides one; otherwise present the same choices as concise numbered text.
- Match the user’s language and level of abstraction; avoid unexplained professional jargon.
- Never ask again for information already supplied.
- Let the user revise or revoke any earlier confirmation at any time.
- Do not make the user write a professional brief. Translate everyday reactions into usable requirements.

Act as a hypothesis-generating collaborator, not a passive interviewer. When the user lacks an answer, propose two or three meaningfully different working hypotheses. Recommend one when helpful and explain why, but mark it as provisional. Let the user’s attraction, resistance, corrections, and rejection carry more weight than the recommendation.

## Distinguish the three layers

Keep these concepts separate throughout discovery:

- **Goal:** the change that should occur if the work succeeds.
- **Deliverable:** the concrete result produced in this project or phase.
- **Method:** the means, medium, tool, or process used to produce it.

Do not treat the user’s first requested format or method as the underlying goal without checking.

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

## Present choices adaptively

Use a native structured-choice tool such as `request_user_input` when it is available and all of the following are true:

- one decision-relevant question is ready;
- two or three short, meaningfully different answers that are mutually exclusive at the level being decided would help the user react;
- choosing an option would narrow the goal rather than prematurely choose an implementation detail.

Keep the question short and easy to scan. Put the recommended option first when a recommendation is justified, label it as recommended, and give every option a one-sentence description of its effect or tradeoff. Preserve the control’s free-form “Other” route so the user can reject the framing or supply a different idea.

If no structured-choice tool is available, ask the same single question in ordinary text. List the same two or three options with short labels and descriptions, then explicitly allow the user to answer with a number, a label, a mixture, or another idea. Do not report the missing control, ask the user to switch modes, or weaken the quality of the hypotheses.

Treat every click or text selection as a working signal, not final confirmation. Let the user combine options, qualify the choice, reverse it, or replace the offered frame. Do not use a choice control for open exploration, nuanced personal expression, factual questions, or any decision that cannot be represented honestly by two or three alternatives.

Prefer questions such as:

- “Should this reassure the recipient, unsettle them, or make them act?”
- “Is recognition more important than novelty, or the reverse?”
- “Would failure mean nobody understands it, or that they understand but feel nothing?”

Do not produce a full solution before the underlying direction is clear; concrete solutions can prematurely anchor the goal.

## Pause at stage checkpoints

At the end of each stage, pause and summarize only the categories that contain information:

- **Confirmed:** explicitly stated and accepted by the user.
- **Working interpretation:** inferred by Codex but not yet confirmed.
- **Excluded:** rejected or determined inconsistent with the goal.
- **Needs confirmation:** still capable of changing the next stage.

Ask the user to confirm or correct the checkpoint before continuing. Do not repeat a full checkpoint after every individual answer unless the direction changes materially.

When a checkpoint is genuinely binary, use the same adaptive interaction: offer confirmation and correction through a structured choice when available, or concise text otherwise. Keep the free-form correction path open.

## Determine readiness

Stop discovery when all of the following are true:

- the user can confirm, “Yes, this is what I truly want to do”;
- the desired change, relevant recipient or context, and intended experience are clear;
- the current deliverable and scope are defined;
- the decisive boundaries and tradeoff priorities are known;
- success can be recognized;
- remaining unknowns concern implementation rather than the project’s core direction;
- a first milestone can directly make the project begin to exist.

If Codex can only suggest “try something and see,” continue discovery. Do not hide unresolved direction behind premature execution or false numerical confidence.

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

Ask one final question: whether to adopt this as the project’s formal starting point and enter execution.

## Exit and hand off

After final confirmation:

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
- Do not continue questioning after the project is ready to begin.
