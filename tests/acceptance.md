# v0.3.1 多轮协作验收 / Multi-turn acceptance

以下为实机行为验收用例，尚未执行独立模型测试。每个场景应在独立会话加载此版本，记录模型、宿主及真实对话。默认只需文字交互；结构校验或指令审阅不等于行为通过。

These live behavioral scenarios have not been run in an independent model session. Record the model, host, and actual transcript for each fresh session. Text interaction is sufficient; structure checks and instruction review are not behavioral passes.

| ID | 输入 / Input | 验收标准 / Observable acceptance | 状态 / Status |
|---|---|---|---|
| A1 | “使用此 Skill，帮我梳理一部关于徒劳的短片。” / Invoke for a vague film seed | 一问、2–3 个文字选项、允许补充，然后停下；无完整脚本 / One question, options, free input, then stop; no full script | 待实测 / Not run |
| A2 | A1 后回复“第三种，但不要绝望。” / A qualified choice | 吸收选择及边界，再给下一问题和选项；不单轮补齐最终方案 / Incorporate the reply, then another question; no invented full plan | 待实测 / Not run |
| A3 | 只确认意义阶段：“对，就是这个意思。” / Confirm meaning only | 进入形态梳理，不把局部确认当执行许可 / Continue into form, not execution | 待实测 / Not run |
| A4 | “这一项你推荐哪个？你定这一项。” / Delegate one choice | 给出局部决定后继续协作，不扩大为整个任务授权 / Decide locally, then continue collaboration | 待实测 / Not run |
| A5 | 明确调用 Skill 并提供详细 brief / Explicit invocation with detailed brief | 确认关键理解，提供继续或修正选项，不因信息多就直接交付 / Confirm the interpretation rather than skipping collaboration | 待实测 / Not run |
| A6 | 已确认共识与方案：“按这份方案开始执行。” / Confirmed plan and execution request | 交接完整共识，不重复已回答问题 / Handoff without redundant questions | 待实测 / Not run |
| A7 | “不用再问了，整个方向你决定，直接做。” / Explicit whole-task override | 尊重改令，说明假设并在授权范围内执行 / Honor override, state assumptions, execute within authorization | 待实测 / Not run |
| A8 | 未调用 Skill：“把已定简介翻译成英文。” / Clear translation without invocation | 不误触发引导，直接完成明确任务 / No unwanted discovery activation | 待实测 / Not run |

用法 / Reusable prompt:

```text
使用 $guided-goal-discovery，每轮问我一个问题并提供选项，
等待我选择或补充后再继续，通过多轮协作确认目标，不要直接给出最终方案。
我的想法是：……
```
