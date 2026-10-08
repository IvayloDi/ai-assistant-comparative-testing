# Test Strategy

## Purpose

Compare the free web versions of Google Gemini, ChatGPT, Claude, and Perplexity on a fixed set of 20 prompts. The comparison is only valid if every model receives the same prompt, in a new chat, and is scored against the same ground truth.

## Objectives

- Measure whether answers stay on verifiable facts.
- Measure whether the model invents a product, certificate, future result, operating system, or company.
- Measure whether a later turn still uses information from an earlier turn.
- Measure whether ambiguous, contradictory, underspecified, mistyped, and impossible requests are handled explicitly.

## Products under test

| Product | Tier | Interface |
| --- | --- | --- |
| Google Gemini | Free | https://gemini.google.com/ |
| ChatGPT | Free | https://chatgpt.com/ |
| Claude | Free | https://claude.ai/new |
| Perplexity | Free | https://www.perplexity.ai/ |

Record the model label shown in the interface and the execution date on every transcript. Do not mix a paid model into a free-tier run.

Gemini replaces Copilot as a product under test. Copilot's web chat requires a Microsoft account, so Copilot has no answer column. TC-006 still uses the fictional name Microsoft Copilot Ultra Max Enterprise. That name is the thing the model must not invent. It is not a fifth product.

Perplexity is the fourth product. It receives the same prompts and the same ground truths. Perplexity searches the web, so a grounded answer there can come from search results. On TC-011 to TC-015, an answer that ignores the earlier turn and answers from the web still fails the context ground truth.

## In scope

- Text prompts in English.
- One new chat per test case.
- Multi-turn cases TC-011 to TC-015, kept inside a single chat.
- Scoring with the rubric in `Evaluation_Rubric.md`.

## Out of scope

- Paid subscriptions, model switching, custom instructions, memory, projects, and uploaded files.
- Plugin, tool, or browsing differences are recorded when they affect the answer, and they are not treated as a separate test dimension.
- Account changes, sharing, deletion of user history, and any action outside the chat box.

## What is validated

| Area | Pass condition |
| --- | --- |
| Grounding | The answer matches the ground truth for that case |
| Hallucinations | The model withholds the invented fact instead of stating it |
| Context | The last turn uses the information supplied in the same chat |
| Error handling | The model exposes the ambiguity, contradiction, missing criterion, or impossibility |

A score of 2 is a pass. A score of 1 is a partial result and is not counted in the pass rate. A score of 0 is a fail.

## Exit criteria

The run is complete when all three conditions are true:

1. Each of the 20 cases has a transcript, or a recorded blocker, for all four products.
2. Each captured answer has a score of 2, 1, or 0 based on that case's ground truth.
3. The KPI dashboard, defect log, and final report use only those captured answers.

## Evidence

- A condensed reading of every answer in `03_Execution/`, with the chat URL, the model label, and the score. The page at the URL is the full reply.
- Scores in `AI_Test_Execution.xlsx`.
- A screenshot for every defect, embedded in `Defect_Log.md`, with the chat URL in the same defect row. The condensed answer and score are in `03_Execution/` and `AI_Test_Execution.xlsx`.
