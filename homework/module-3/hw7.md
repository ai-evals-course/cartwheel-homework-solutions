# HW7 selected references

**Assignment:** [HW7 handout](https://github.com/ai-evals-course/cartwheel-homeworks/blob/main/homework/module-3/hw7.md)

HW7 asks students to take a judge validated in HW5 and use it for post-deployment monitoring. The assignment covers comparing two runs of the same 50 scenarios, estimating the prevalence of one failure mode, correcting that estimate for judge error, inspecting risk groups, publishing scores to Langfuse, and scheduling the monitor in GitHub Actions.

After reviewing the HW7 submissions, we selected Alex G's work because it was the most aligned with the assignment requirements. The submission follows the required sampling design, uses a validated frozen judge, keeps the random sample separate from the risk groups, and interprets the results without claiming more than the evidence supports.

## Alex G

- **Code and analysis:** [View the submitted commit](https://github.com/alexgsm/cartwheel-homeworks/commit/54426aa)
- **Repository:** [Browse the HW7 branch](https://github.com/alexgsm/cartwheel-homeworks/tree/hw7)
- **Monitor evidence:** [View the successful manual workflow run](https://github.com/alexgsm/cartwheel-homeworks/actions/runs/36922604087)

### Why it was selected

Alex first establishes whether the measurement instrument is usable. His own HW5 judge for ungrounded claims had performed poorly on its held-out test set, so he does not use it to make a production claim. He uses the validated frozen reference judge for `unsupported_policy_claim` and keeps its prompt, model, inputs, and parser fixed.

Both monitoring periods contain the same 50 scenarios and use `anthropic/claude-haiku-4-5`. A seeded 20% random sample provides 10 conversations for estimating prevalence, while the `policy_lookup` and `write_action` groups supply additional traces for targeted inspection. The risk-group verdicts remain separate from the random estimate.

| Period | Random flags | Raw rate | Corrected rate | 95% interval |
|---|---:|---:|---:|---:|
| Before | 3 of 10 | 0.30 | 0.3169 | 0.0000–0.7640 |
| After | 4 of 10 | 0.40 | 0.4449 | 0.0607–0.9309 |

The corrected estimate increases, but Alex does not treat that movement as proof that the agent became worse. The intervals overlap substantially, and the same 10 scenarios were sampled in both periods. Three scenarios were flagged in both periods; the entire observed difference comes from one additional after-period flag, `support-0174`. This makes the effect of a small sample concrete.

Both estimates cross the precommitted 0.15 threshold. Alex treats the crossing as a trigger for human error analysis, beginning with persistent flags and write-action cases. Confirmed failures would become regression cases in the HW6 suite. This preserves the distinction between a judge flag, a human-confirmed failure, and an estimate of population prevalence.

### What to study

- Rejecting a judge that is too weak for the monitoring decision
- Keeping the random sample separate from targeted risk groups
- Applying judge-error correction to the random-sample flag rate
- Explaining an aggregate change through the scenarios that produced it
- Interpreting overlapping intervals without claiming an unsupported trend
- Turning a threshold crossing into human review and new HW6 regression cases
- Using stable Langfuse score IDs so repeated monitor runs update existing scores
