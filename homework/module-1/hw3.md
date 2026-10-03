# HW3 selected references

**Assignment:** [HW3 handout](https://github.com/ai-evals-course/cartwheel-homeworks/blob/main/homework/module-1/hw3.md)

HW3 focuses on generating scenario datasets while keeping generation, application execution, criticism, and human review distinct.

## Aastha Singh

- **Walkthrough:** [Watch the video](https://youtu.be/mBfP0WS0FSY)
- **Code:** [View the commit](https://github.com/aastha0208/cartwheel-support-agent/commit/d1d06fff7b536f9306735f46456fe5a64218f9e3)

### Why it was selected

Aastha builds a structured scenario set from pilot failures and explicit coverage goals. She uses critic review and human review to improve the dataset instead of treating generated cases as automatically valid.

### What to study

- Turning pilot observations into intentional coverage and challenge cases
- Keeping generation separate from execution
- Using criticism and human review as quality controls
- Recording why each scenario belongs in the dataset

## Jeffrey Arnold

- **Walkthrough:** [Watch the video](https://www.loom.com/share/8ab85b7ad28745cb84907089247cb290)

### Why it was selected

Jeffrey creates a review and annotation interface that brings trace context, expected behavior, database records, and labels into one place. His date-handling example shows how an application can accidentally use the real runtime date instead of the scenario’s simulated world date.

### What to study

- Giving a reviewer enough context to make a defensible label
- Separating scenario time from wall-clock time
- Treating the review interface as part of dataset quality

## Diana Pfeil

- **Walkthrough:** [Watch the video](https://www.loom.com/share/409c47235055464ea502c192d12e2eaf)

### Why it was selected

Diana connects scenario design to concrete failure hypotheses: missed escalation under inconsistent dates, incorrect entity resolution and tool order, and product questions that require catalog search.

### What to study

- Writing scenarios around an observable failure hypothesis
- Testing entity resolution and tool sequencing
- Ensuring the agent retrieves the right source for product questions
