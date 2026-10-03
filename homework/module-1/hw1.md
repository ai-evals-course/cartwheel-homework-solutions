# HW1 selected references

**Assignment:** [HW1 handout](https://github.com/ai-evals-course/cartwheel-homeworks/blob/main/homework/module-1/hw1.md)

HW1 introduces evidence-based failure analysis and small, testable improvements to an agent. These references emphasize different parts of that loop.

## Aastha Singh

- **Walkthrough:** [Watch the video](https://www.youtube.com/watch?v=z01el2MfEaE)

### Why it was selected

Aastha presents a strong end-to-end failure analysis. She groups failures into meaningful categories, reasons about severity, makes narrow prompt changes, and checks that the change does not damage behavior that already worked.

### What to study

- Moving from individual bad traces to reusable failure categories
- Prioritizing failures by impact instead of treating every issue equally
- Testing a targeted change against both the failure and existing behavior
- The early connection between error analysis and the failure taxonomies used later in the course

## Glenn

- **Walkthrough:** [Watch the video](https://www.loom.com/share/9f64c309e9e94d66870e113fbd89c77f)

### Why it was selected

Glenn notices a subtle issue: the agent reaches a plausible answer without first retrieving and citing the relevant store policy. The final answer alone looks reasonable, but the trace reveals that the process is not grounded in the required evidence.

He also builds a small `show.py` viewer to make trace inspection faster.

### What to study

- Evaluating the path the agent took, not only its final response
- Distinguishing a lucky correct answer from a reliably grounded answer
- Building a small inspection tool when the default interface slows down analysis

## Madhoolika

- **Walkthrough:** [Watch the video](https://www.loom.com/share/02bf67cadfdc417290e076ded790684f)

### Why it was selected

Madhoolika identifies a capability gap rather than treating every failure as a prompting problem. She adds a store-information tool so the agent can retrieve store-specific return windows and then tests it across multiple stores.

### What to study

- Recognizing when the agent lacks required information or capability
- Choosing a tool change when prompting cannot supply missing facts
- Testing the new capability across more than one store or policy value
