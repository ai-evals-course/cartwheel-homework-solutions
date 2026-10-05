# HW6 selected references

**Assignment:** [HW6 handout](https://github.com/ai-evals-course/cartwheel-homeworks/blob/main/homework/module-3/hw6.md)

HW6 asks students to turn reviewed failures into repeatable evaluation cases, classify cases from baseline runs, and run the suite in continuous integration. Students also implement `pass@k` and `pass^k`, demonstrate an intentional regression and its reversal, and examine how estimates change as more trials are collected.

## Ankur Bhatia

- **Walkthrough:** [Watch the video](https://www.loom.com/share/8ff5c00286aa4ed6bd1160f68e57325c)
- **Code and analysis:** [View pull request #12](https://github.com/ankurbhatia28/cartwheel-homeworks/pull/12)

### Why it was selected

Ankur builds 12 evaluation cases from six HW4 failure modes. The suite covers unsupported outcome promises, inaccessible records, inconsistent records, missed escalation, exposed internal identifiers, and incomplete status answers. This gives students a concrete example of carrying a broad human failure taxonomy into executable checks.

The evaluator choice follows the evidence available in each case. Semantic claims about completed actions use the frozen HW5 judge, while authorization, record state, writes, escalation, and literal identifiers use code checks. The submission also records mistakes discovered while baselining the cases, showing that writing an evaluation case is itself an iterative process.

For the CI exercise, the selected case fails all five trials after an intentional change and passes all five after the change is reverted. The trace-level assertion is useful for seeing how a changed tool path can be detected even when the final response appears safe. The 15-run capability analysis records 12 successful trials and shows how the estimates evolve with additional evidence.

### What to study

- Converting several HW4 failure modes into a varied evaluation suite
- Choosing between code checks and an LLM judge based on observable evidence
- Connecting assertions to tool calls, tool results, database state, and final replies
- Recording and correcting case-design errors found during baseline runs
- Configuring Harbor conservatively when CI runner resources are limited

## Luca Pazzi

- **Walkthrough:** [Watch the video](https://www.loom.com/share/9cbef0dda4cc4bcbaafeb30b895b124a)
- **Code and analysis:** [View pull request #7](https://github.com/mrpozzi/cartwheel-homeworks/pull/7)

### Why it was selected

Luca builds 16 evaluation cases across three failure modes: policy claims without citations, raw record fields in replies, and unsupported assertions. Exact checks handle citation identifiers and raw fields, while the accepted frozen HW5 judge evaluates whether a claim is supported by the trace. Dedicated adapter tests verify that Harbor passes the expected trace data into each evaluator.

The submission preserves genuine failures rather than rerunning until the whole suite turns green. After the intentional regression is reverted, the selected case returns to five successful trials, while two other regression cases each fail once. This is a useful example of why a five-run baseline is evidence for classification rather than a guarantee of future behavior.

The 15-run capability case succeeds in 8 of 15 trials. Its prefix results make the sample-size lesson visible: conclusions drawn from five trials can shift as more runs arrive.

### What to study

- Combining exact code checks with a semantic judge in one suite
- Testing the adapter that prepares judge input from Harbor results
- Preserving and interpreting failures that occur during a CI demonstration
- Using repeated trials to classify regression and capability cases
- Reading changes in `pass@k` and `pass^k` as the sample grows

## Jeff Arnold

- **Walkthrough:** [Watch the video](https://www.loom.com/share/5db773310ffc4f77b0487bf583dc2e9f)
- **Code and analysis:** [View pull request #15](https://github.com/jrnold/cartwheel-homeworks/pull/15)

### Why it was selected

Jeff builds 12 evaluation cases for two HW4 failure modes and keeps provenance back to the reviewed traces and scenarios. A custom code evaluator checks for exposed internal identifiers, while the frozen HW5 judge evaluates narration and over-explanation. This makes the boundary between deterministic and judgment-based checks easy to inspect.

The intentional regression moves the selected case from three successes in five trials back to five in five after the change is reverted. For the sample-size exercise, the submission evaluates three capability cases over 15 runs, providing several reliability profiles rather than a single example.

Jeff also adds optional statistical analysis around the required point estimates, including bootstrap and exact confidence intervals, plus a generated report. These additions are extensions to the core homework, but they are useful for students who want to study how uncertainty can be communicated when the number of trials is small.

### What to study

- Preserving trace and scenario provenance for every evaluation case
- Implementing a focused code evaluator for an exact output property
- Reserving an LLM judge for a semantic failure mode
- Comparing reliability patterns across several capability cases
- Adding uncertainty estimates without replacing the required `pass@k` and `pass^k` calculations
