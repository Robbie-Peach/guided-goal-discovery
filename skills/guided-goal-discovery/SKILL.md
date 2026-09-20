---
name: guided-goal-discovery
description: Clarify vague intentions or conflicting goals through one question at a time, then produce a shared goal and a 0-to-1 launch plan. Use for requested guided discovery or ambiguity that would materially change the outcome. Skip clear tasks, aligned continuations, and decisions the user delegates.
---

# Guided Goal Discovery

Help the user discover and confirm a goal instead of requiring a finished brief. Treat sparse language, uncertainty, and “I don’t know” as valid starting material. End with a confirmed goal consensus and a concrete 0-to-1 launch plan, then hand off to execution.

## Interaction contract

- Enter guided mode only while a consequential goal decision remains unresolved; briefly explain the one-question approach when entering.
- Ask at most one decision-relevant question per turn. Ask none when the direction is ready or the user asks you to decide and proceed.
- Choose the question whose answer would most change the direction; do not follow a fixed questionnaire.
- Make questions easy to answer through concrete contrasts, examples, outcomes, or felt differences.
- Prefer a native structured-choice control for bounded alternatives when the runtime provides one; otherwise present the same choices as concise numbered text.
- Match the user’s language and level of abstraction; avoid unexplained professional jargon.
- Never ask again for information already supplied.
- Let the user revise or revoke any earlier confirmation at any time, including during a turn. Update the affected assumptions and next action without restarting already settled discovery.
- Do not make the user write a professional brief. Translate everyday reactions into usable requirements.

Act as a hypothesis-generating collaborator, not a passive interviewer. When the user lacks an answer, propose two or three meaningfully different working hypotheses. Recommend one when helpful and explain why, but mark it as provisional. Let the user’s attraction, resistance, corrections, and rejection carry more weight than the recommendation.

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

## Present choices adaptively

Use a native structured-choice tool such as `request_user_input` or `request_user_input_async` only when it is exposed and permitted in the current mode, and all of the following are true:

- one decision-relevant question is ready;
- two or three short, meaningfully different answers that are mutually exclusive at the level being decided would help the user react;
- choosing an option would narrow the goal rather than prematurely choose an implementation detail.

Follow the active tool schema, not a remembered schema or the model name. Keep the question short. Put a justified recommendation first and label it; describe each option’s effect or tradeoff in the fields the tool supports. Preserve free-form input. If the host automatically supplies an “Other” or free-text route, do not add a duplicate option.

- **Synchronous control:** read the returned user answer before advancing. A Plan-only tool stays Plan-only even if its name is visible elsewhere.
- **Asynchronous control:** submitting the question is not receiving an answer. Keep only one unresolved discovery question active. A tool receipt, a preselected option, silence, or unrelated new input is not consent. If the next decision depends on the answer, end the turn after submitting the question and resume when the user responds; do not poll, repeat the question, or choose the default on their behalf. Follow explicit host instructions for a completed no-answer result; if they require proceeding, state the working assumption rather than treating it as confirmation.
- **Correction or delegation:** a later user correction overrides the affected hypothesis. If the user rejects the framing or asks you to choose, honor that response instead of waiting for a particular button click.

If no structured-choice tool is exposed and permitted, ask the same single question in ordinary text. List the same two or three options with short labels and descriptions, then explicitly allow the user to answer with a number, a label, a mixture, or another idea. Do not ask the user to switch modes just to obtain a control. If an available tool errors, distinguish that failure from ordinary absence; follow the host’s error-handling instructions without inventing a response.

Treat exploratory selections as working signals, not approval of an entire plan. An explicit confirmation or “start execution” response does count for the decision it names, whether clicked or typed; do not ask for it again. Let the user combine options, qualify the choice, reverse it, or replace the offered frame. Do not force choices for open exploration, nuanced expression, or a decision that cannot be represented honestly by two or three alternatives.

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

Ask for confirmation only when an unconfirmed interpretation would change the next stage. Carry forward explicit user decisions without another approval gate. Skip settled or irrelevant stages; the stages are a map, not a mandatory interview. Do not repeat a full checkpoint after every answer.

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

If a missing goal decision prevents a useful starting point, ask the one question that resolves it. Implementation uncertainty can belong in the launch plan; it need not prolong discovery. Do not hide unresolved direction behind premature execution or false numerical confidence. If the user delegates the remaining choices, state reasonable assumptions and proceed within the authorized task.

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

Ask whether to adopt this as the formal starting point and enter execution only if that decision remains open. If the user already confirmed it or delegated the remaining choices and requested execution, hand off without repeating the question. Keep the four sections concise and proportional to the project.

## Exit and hand off

After final confirmation or explicit delegation to proceed:

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
