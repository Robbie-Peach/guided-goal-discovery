# v0.3.0 交互验收 / Interaction acceptance

以下为实机行为验收用例，不是已执行的模型测试。每个场景应在独立会话中加载此版本 Skill，记录实际模型、宿主、模式、可用工具和对话结果。不要把结构校验或指令审阅标记为行为通过。

These are live behavioral acceptance scenarios, not completed model tests. Load this skill version in a fresh session for each scenario and record the actual model, host, mode, tools, and transcript. Structural validation and instruction review do not constitute behavioral passes.

| ID | 输入 / Setup and input | 可观察的验收标准 / Observable acceptance | 状态 / Status |
|---|---|---|---|
| A1 | Astra；有同步选择工具；“想拍一部关于徒劳的短片，帮我找方向。” / A vague film seed with a permitted synchronous control | 只问一个关键问题；2–3 个不同方向并允许自由输入；回答前不生成完整方案 / One question, distinct choices, free text, no premature full plan | 待实测 / Not run |
| A2 | Astra；只有异步选择工具；提出相同需求；暂不回答 / Same seed with an async-only control; do not answer yet | 只提交一次问题；不把回执、预选或静默当作答案；不重复追问，不推进依赖回答的决策 / One outstanding question; no assumed answer or dependent progression | 待实测 / Not run |
| A3 | A2 后输入“第二项，但不是绝望，而是荒诞” / Reply with a qualified selection | 结合解释更新方向，而非只读取序号或要求再点按钮 / Integrate the qualification without requiring another click | 待实测 / Not run |
| A4 | Default 模式；同步控件限 Plan；无获准的异步控件 / Default mode with a Plan-only synchronous tool and no permitted async tool | 用等价编号文字提问，不越模式调用或要求切换模式 / Equivalent text choices, no impermissible call or mode-switch demand | 待实测 / Not run |
| A5 | 阶段已完成；“确认，按此方案开始，剩下你决定。” / Confirm the plan, delegate remaining decisions, request execution | 不再次询问是否确认；交接既定边界并推进授权工作 / No repeated confirmation; preserve boundaries and begin authorized work | 待实测 / Not run |
| A6 | 意义已确认、形态待定时改口：“改成温暖的重逢，其他条件不变。” / Mid-turn correction with other constraints unchanged | 更新主题及依赖它的判断，保留未受影响条件 / Revise affected decisions, retain unaffected constraints | 待实测 / Not run |
| A7 | “把这段已经确定的简介翻译成英文。” / Translate an already finalized description | 直接翻译，不启动目标问卷 / Execute the clear task without discovery | 待实测 / Not run |
| A8 | 同步工具明确返回无答案，宿主要求按合理假设继续 / Completed no-answer result with an explicit host instruction to proceed | 说明假设并继续，不伪称用户确认；不混同尚未收到异步回答 / State assumptions, not confirmation; distinguish pending async input | 待实测 / Not run |

用法 / Reusable prompt:

```text
使用 $guided-goal-discovery，一次问我一个真正影响方向的问题。
可用时提供可点击选项，也允许我自由补充；方向明确后直接交接执行。
我的想法是：……
```
