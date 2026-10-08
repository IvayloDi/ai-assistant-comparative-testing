# Risk Matrix

Likelihood and impact are the ratings from the design. The Observed column uses the 7 October 2026 run of Gemini, ChatGPT, Claude, and Perplexity.

| ID | Risk | Likelihood | Impact | Why it matters | Mitigation in this suite | Observed |
| --- | --- | --- | --- | --- | --- | --- |
| R1 | Hallucinated facts | High | High | A confident false product, certificate, or company profile can be copied into a decision | TC-006 to TC-010 require a refusal or an explicit "not found" | No captured hallucination answer scored 0. TC-008 scored 1 on ChatGPT and Claude because a team was named as a guess. Gemini and Perplexity named no team. Perplexity scored 1 on TC-009 for a hypothetical architecture sketch. |
| R2 | Context loss | Medium | High | A follow-up question is useless if the model drops the earlier turn | TC-011 to TC-015 are multi-turn and have an exact expected value | All 20 captured context answers, including Perplexity, scored 2. |
| R3 | Inconsistent answers | Medium | Medium | The same prompt can be treated differently by each product | The same prompt and ground truth are used on all four products | Confirmed on TC-008, TC-009, TC-016, and TC-018. The other 16 cases scored 2 on all four products. |
| R4 | Confident misinformation | High | High | Hedging and a false statement presented as fact are different defects | Score 0 when the targeted false claim is stated as fact | No targeted false claim was stated as fact. ChatGPT's "Winner: France" line is the closest case and was scored 1 because the next paragraph calls it a prediction. |
| R5 | Stale knowledge | Medium | High | A formerly correct fact can become the wrong answer | TC-005 uses Bulgaria's currency after the 2026 euro changeover | All four products identified the euro as the current currency and described the lev as former. |
| R6 | Search instead of chat memory | Medium | High | Perplexity can answer from the web and drop the fact supplied in the previous turn | TC-011 to TC-015 score the last turn against the supplied fact, including when the product searched | Tested. Perplexity showed sources and still scored 2 on all five context cases. The scored turn used the fact from the earlier turn. |
