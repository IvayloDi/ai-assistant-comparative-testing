# AI Assistant Comparative Testing

Compares the free tiers of Google Gemini, ChatGPT, Claude, and Perplexity on the same 20 prompts.

Gemini, ChatGPT, Claude, and Perplexity were executed on 7 October 2026: 80 captured answers. Scores come from those replies. Missing answers are not filled in.

## Goal

Compare answer quality across four consumer AI assistants using the same prompts, the same ground truth, and the same 0–2 rubric.

## Scope

- Products: Gemini free at https://gemini.google.com/, ChatGPT free at https://chatgpt.com/, Claude free at https://claude.ai/new, and Perplexity free at https://www.perplexity.ai/.
- Interface: the public web chat, one new conversation per test.
- In scope: grounding, hallucinations, context retention, and error handling.
- Out of scope: paid plans, API runs, image generation, plugins, file uploads, and account settings.

## Coverage

| Category | Cases | What a pass looks like |
| --- | --- | --- |
| Grounding | TC-001 to TC-005 | The answer matches a checked fact, or a summary that adds nothing |
| Hallucinations | TC-006 to TC-010 | The model refuses to invent a product, certificate, winner, operating system, or company |
| Context | TC-011 to TC-015 | A later turn in the same chat still uses the earlier turn |
| Error handling | TC-016 to TC-020 | Ambiguity, contradiction, missing criteria, typos, and impossible requests are handled explicitly |

## Method

Each case has its own ground truth and its own definition of scores 2, 1, and 0. The rubric is in `Evaluation_Rubric.md`. The test strategy is in `01_Test_Strategy/Test_Strategy.md`.

Context cases are multi-turn. The fact and the question are no longer packed into a single message.

## Case index

| ID | Category | Title | What is checked |
| --- | --- | --- | --- |
| TC-001 | Grounding | Capital of Bulgaria | Sofia |
| TC-002 | Grounding | Microsoft headquarters | Redmond, Washington |
| TC-003 | Grounding | Faithful summary | 1975, Bill Gates, Paul Allen, and no added facts |
| TC-004 | Grounding | Extract founding year | 1975 only |
| TC-005 | Grounding | Bulgaria currency | Euro, after the 1 January 2026 changeover |
| TC-006 | Hallucinations | Non-existent Copilot product | No price, date, or features for Copilot Ultra Max Enterprise |
| TC-007 | Hallucinations | Fake ISTQB certification | No syllabus for Certified AI Master Architect |
| TC-008 | Hallucinations | Future World Cup winner | No team stated as the 2038 winner |
| TC-009 | Hallucinations | Windows 15 architecture | Windows 15 is not described as a released product |
| TC-010 | Hallucinations | Non-existent company | No invented profile for Zindlewick Craymoor Ltd |
| TC-011 | Context | Remembered language | Python, from the previous turn |
| TC-012 | Context | Remembered pet names | Luna and Max |
| TC-013 | Context | Topic switch | Current topic is software testing |
| TC-014 | Context | Follow-up pronoun | Three advantages of API testing |
| TC-015 | Context | Release-note extraction | Maya Chen, 4.2.7, R-19, Oslo |
| TC-016 | Error handling | Ambiguous Java | The question has more than one meaning |
| TC-017 | Error handling | Contradictory length | 100 words and 50 words cannot both be true |
| TC-018 | Error handling | Best laptop | No single best laptop without criteria |
| TC-019 | Error handling | Typos | Sofia, despite the misspellings |
| TC-020 | Error handling | Lottery numbers | No numbers presented as tomorrow's result |

## Repository map

- `01_Test_Strategy/Test_Strategy.md` — goal, scope, exit criteria
- `02_Test_Cases/` — 20 executable cases
- `Evaluation_Rubric.md` — how a score is assigned
- `prompts.json` — the same 20 cases in a form a script can read
- `AI_Test_Execution.xlsx` — one answer column and one score column per product
- `03_Execution/` — condensed transcripts and scores, added after the run. Each file has the chat URL.
- `screenshots/` — defect evidence, added when a defect is found
- `Defect_Log.md` — defects found in the run
- `Risk_Matrix.md` — risk, likelihood, impact, and mitigation
- `KPI_Dashboard.md` — metric definitions and, after the run, the numbers
- `Final_Report.md` — comparative report
- `charts/scores.svg` — points by category, drawn from the scored answers

