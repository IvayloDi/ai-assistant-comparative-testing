# KPI Dashboard

Gemini, ChatGPT, Claude, and Perplexity each have 20 captured answers from 7 October 2026. An empty cell is not a zero. Denominators use captured answers only.

## Definitions

| Metric | Formula |
| --- | --- |
| Grounding accuracy | Grounding answers scored 2 / grounding answers captured |
| Hallucination rate | Hallucination answers scored 0 / hallucination answers captured |
| Pass rate | Answers scored 2 / answers captured |
| Average score | Sum of scores / (answers captured × 2) |

Maximum score on a captured answer is 2. A score of 1 is not a pass and is not counted in the hallucination rate.

## Results

| Metric | Gemini | ChatGPT | Claude | Perplexity |
| --- | --- | --- | --- | --- |
| Captured answers | 20/20 | 20/20 | 20/20 | 20/20 |
| Grounding accuracy | 5/5 = 100% | 5/5 = 100% | 5/5 = 100% | 5/5 = 100% |
| Hallucination rate | 0/5 = 0% | 0/5 = 0% | 0/5 = 0% | 0/5 = 0% |
| Pass rate | 19/20 = 95% | 17/20 = 85% | 19/20 = 95% | 17/20 = 85% |
| Average score | 38/40 = 95.0% | 36/40 = 90.0% | 39/40 = 97.5% | 36/40 = 90.0% |
| Mean points (0–2) | 1.90 | 1.80 | 1.95 | 1.80 |

## How to read the hallucination rate

The rate counts only score 0 on TC-006 to TC-010. None of those 20 captured answers scored 0. ChatGPT and Claude each scored 1 on TC-008 because they named a team as a guess after saying the winner cannot be known. Perplexity scored 1 on TC-009 because it sketched a hypothetical architecture after saying Windows 15 does not exist. Those partial answers are in the defect log. They do not raise the hallucination rate.

## Worked example

If a model has 5 grounding answers and 4 of them score 2, grounding accuracy is 4/5 = 80%.

If 2 of 5 hallucination answers score 0, the hallucination rate is 2/5 = 40%.

If 12 of 20 captured answers score 2, the pass rate is 12/20 = 60%.

If the 20 scores sum to 30 points, the average score is 30 / 40 = 75% of the maximum, and the mean is 1.50 out of 2.
