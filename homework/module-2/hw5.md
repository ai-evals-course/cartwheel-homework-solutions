# HW5 selected references

**Assignment:** [HW5 handout](https://github.com/ai-evals-course/cartwheel-homeworks/blob/main/homework/module-2/hw5.md)

HW5 asks students to turn one HW4 failure mode into an LLM judge, create a labeled development set, improve the rubric through error analysis, and report held-out performance.

## Ankur Bhatia

- **Walkthrough:** [Watch the video](https://cap.so/s/n1kw5p3d1cz80bt)
- **Code and analysis:** [View pull request #11](https://github.com/ankurbhatia28/cartwheel-homeworks/pull/11)

### Why it was selected

Ankur builds a judge for unsupported outcome promises: cases where the agent tells a user that a refund or similar action is completed even though the tool evidence does not establish that outcome.

A particularly useful decision is the way he creates additional traces. Instead of searching broadly for vaguely related conversations, he generates scenarios at the refund policy boundary, especially around the over-$100 approval path where unsupported promises are most likely to appear. This concentrates annotation effort on informative positives and close negatives.

His reported held-out results for the required `gpt-4o-mini` judge are 80.9% true-positive rate and 80.0% true-negative rate.

### What to study

- Translating a human-readable failure mode into a judge rubric
- Generating data at the actual policy boundary
- Using tool evidence to distinguish a completed action from a submitted or pending one
- Examining false positives and false negatives separately while revising the rubric
- Reporting held-out TPR and TNR without treating one number as universal proof of quality

## Conor

- **Walkthrough:** [Watch the video](https://www.youtube.com/watch?v=SdXwVW3cDzs)
- **Code and analysis:** [View the commit](https://github.com/conor10/cartwheel-homeworks/commit/a20acae28cda3f929fc734a4ddecbf1709ad68e5)

### Why it was selected

Conor builds a judge for irrelevant response detail and puts strong controls around the evaluation process: deduplication, immutable inputs, provenance tracking, explicit disagreement review, and gates that prevent weak results from being presented as production-ready.

The required `gpt-4o-mini` judge performs poorly on the held-out set, with a reported 46.2% true-positive rate and 55.0% true-negative rate. Conor treats that as the result rather than hiding it or tuning on the test set. His stronger-model experiments are clearly marked as exploratory.

### What to study

- Preserving a clean held-out test set
- Tracking where examples and labels came from
- Reviewing human–judge disagreements instead of optimizing only an aggregate score
- Recognizing when a failure mode is too subjective or context-dependent for the chosen judge
- Reporting a negative result and declining to use an unreliable judge as a gate
