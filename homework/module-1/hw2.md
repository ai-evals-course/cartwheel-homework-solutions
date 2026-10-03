# HW2 selected references

**Assignment:** [HW2 handout](https://github.com/ai-evals-course/cartwheel-homeworks/blob/main/homework/module-1/hw2.md)

HW2 develops trace-based debugging, controlled comparisons, and evidence about tool use and authorization behavior.

## Marcus Streips

- **Walkthrough:** [Watch the video](https://www.loom.com/share/15a359c6266b439ca625974bf33d1cea)

### Why it was selected

Marcus clearly separates trusted identity from claims in a user request, then walks from simple to more complex refund traces. His prompt comparison keeps the test conditions controlled, which makes the effect of the change easier to interpret.

### What to study

- Reading identity and authorization from trusted state
- Increasing scenario difficulty while preserving a clear hypothesis
- Comparing prompt versions under the same conditions

## Angela Pap

- **Walkthrough:** [Watch the video](https://www.loom.com/share/e6cea12dbdda46679d6b92172501d8ab)

### Why it was selected

Angela combines exploratory traces, authorization cases, allowed and denied operations, and a custom trace viewer. The result shows how interface design can support debugging across both successful and failing paths.

### What to study

- Including allowed and denied cases in an authorization evaluation
- Using trace evidence to debug prompt-version behavior
- Designing a viewer around the decisions the reviewer repeatedly makes

## Madhoolika

- **Walkthrough:** [Watch the video](https://www.loom.com/share/62e6801c13bd4f57ad9270e35a27b087)

### Why it was selected

Madhoolika investigates irrelevant tool paths, changes the prompt, reruns the behavior, and uses ClickHouse span counts to quantify the effect. This connects qualitative trace reading with a simple operational measure.

### What to study

- Detecting unnecessary tool use in a trace
- Rerunning the same behavior after a prompt change
- Using span counts as supporting evidence rather than as a substitute for trace review
