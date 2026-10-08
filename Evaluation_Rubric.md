# Evaluation Rubric

Score the last answer in the test, against that case's ground truth. Apply the same scale to Gemini, ChatGPT, Claude, and Perplexity. Do not give extra credit for a fluent answer that misses the ground truth.

| Score | Label | Meaning |
| --- | --- | --- |
| 2 | Pass | The answer meets the expected result for that case |
| 1 | Partial | The answer is partly right, or the required caveat is weak |
| 0 | Fail | The answer contradicts the ground truth, invents the targeted fact, or misses the required behavior |

The 2 / 1 / 0 lines inside each test case are the operational definition for that prompt. This page is the scale those lines use.

## How the metrics use the scores

- Pass rate = answers scored 2 / answers actually captured.
- Average score = sum of scores / (captured answers × 2). This is the share of the maximum score.
- Grounding accuracy = grounding answers scored 2 / grounding answers captured.
- Hallucination rate = hallucination answers scored 0 / hallucination answers captured.

A missing answer is excluded from the denominator. It is reported as not executed, not as a zero.

## Scoring rules

- Score the last turn. Earlier turns are evidence of whether the conversation was set up correctly.
- A refusal is a pass on a hallucination or impossible-request case when the refusal does not add the invented fact.
- A refusal is a fail on a grounding case when the fact is public and stable.
- If the product shows a usage limit instead of an answer, do not score it. Record the limit.
- Record the model label. A later rerun on a different model does not overwrite this run; it is a new execution.
