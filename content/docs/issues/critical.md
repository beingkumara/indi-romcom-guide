---
title: Critical issues
weight: 1
---

These affect whether the benchmark's data and numbers can be trusted.

## C1. The mixing rules contradict each other

<span class="st st-ok">Confirmed</span>

The paper defines the mixing categories and levels twice, and the two versions don't match.

| | Table 9 and Table 10 (main text) | Generation prompt (Appendix B.3) |
|---|---|---|
| CAT-A | Function words (*the*, *is*, *a*) | Connectors (*so*, *but*, *because*) |
| CAT-B | Connectors | Function words |
| CAT-C | Task and domain terms | Content words (*office*, *time*, *woman*) |
| CAT-D | Concrete topic nouns | Domain terms |
| CAT-E | Whole clauses | **Does not exist** |
| 25% uses | C | A, B (1–3 words per sentence) |
| 50% uses | B, C, D | A, B, C (3–6 words) |
| 75% uses | A–E | A–D (6–10 words) |

Section B.7 then analyses the data with the Table 9 labels: "all 6,925 substitutions at 25% are CAT-C", and CAT-E makes up 6.8% at 75%. Under the prompt that produced the data, neither is possible.

**Why it matters:** Figure 3 and the whole category analysis rest on labels whose meaning changed between the paper and the pipeline.

## C2. The generation prompt is written for NLI only

<span class="st st-ok">Confirmed</span>

The B.3 prompt is presented as the prompt for all tasks and languages, but its annotation format asks for `CMI_premise={score} CMI_hypothesis={score}`. Only the NLI task has a premise and a hypothesis. Either different prompts were used for other tasks (not shown), or math and analogy items were generated with a prompt that doesn't fit them.

## C3. The data misses its own mixing targets

<span class="st st-ok">Confirmed</span>

| Level | Target CMI (Table 10) | Measured mean (Table 4) | Inside target? |
|---|---|---|---|
| 25% | 0.15–0.35 | 0.249 | Yes |
| 50% | 0.35–0.60 | 0.294 | **No**, below |
| 75% | 0.60–0.85 | 0.360 | **No**, far below |

The "75%" data is about 36% mixed on the paper's own measure. The level names don't describe the data.

## C4. Per-task mixing values don't make sense

<span class="st st-ok">Confirmed</span>

- At 25%, **NLI has CMI 0.004** and **Sentiment 0.028**. That is essentially unmixed English.
- **Toxicity** has CMI 0.851 → 0.805 → 0.981. It is the highest of any task, and it *falls* from 25% to 50%, against the "rises monotonically" claim.
- Appendix B.5 says the toxic input is **never code-mixed**. So the high CMI must come from the label and explanation, which means the toxicity task doesn't test understanding of mixed *input* at all.

## C5. NLI labels are mapped two different ways

<span class="st st-ok">Confirmed</span>

| Where | Entailment | Neutral | Contradiction |
|---|---|---|---|
| Prompt (Table 5) | **1** | **0** | 2 |
| Data (Table 8) and IndicXNLI's own mapping | **0** | **1** | 2 |

Table 5's own example: *"These were the three U2 pilots who were in General May's office with President Kennedy"* → *"General May and the pilots had a good time in the office"* is labelled **1**. That pair is clearly *neutral*, which is correct under the data's mapping and wrong under the prompt's.

**Why it matters:** if models were told 1 = entailment and scored against gold labels where 1 = neutral, NLI accuracy is invalid.

## C6. The "reply in English" metric is defined two ways

<span class="st st-ok">Confirmed</span>

- **Appendix C.3:** language is detected *per token* with IndicLID, and a reply counts as English if more than 70% of its tokens are English. IndicLID is a sentence-level language identifier, not a token tagger.
- **Table 14:** a reply counts as English if more than 70% of its tokens are **ASCII**. Every romanized reply is ASCII, which is why the fine-tuned models score 99.9%. The paper admits this.
- Even with the C.3 definition, a 25%-mixed input is about 75% English (mean CMI 0.249). A *perfect* reply in that style would be over 70% English and would count as a failure.
- C.3 says RDR is computed separately for labels and explanations. Only one RDR is ever reported.
- An Indian-language model that replies in **native script** would get a low (good) RDR, even though that also breaks the "same script" instruction.

**Why it matters:** Table 7 and the claim that "Indic pretraining drives register adherence" can't be read reliably.

## C7. Three different models have identical results

<span class="st st-ok">Confirmed</span>

Mistral-7B, Qwen2.5-7B and Qwen3.5-9B have exactly the same numbers in:

- Table 6: 49.7 / 44.3 / 43.6 / 43.3, with identical standard deviations
- Table 7: 60.6 / 64.7 / 65.1 / 63.5
- Table 13: 56.2 / 51.5 / 50.8 / 50.4

Three different models can't match to one decimal across 8,400 items. This looks like copy-pasted or placeholder rows.

## C8. The few-shot table looks derived, not run

<span class="st st-ok">Confirmed</span>

Recomputing Table 13 minus Table 6 cell by cell:

- Every one of the 76 cells is between **+5.5 and +7.3** points. That includes the English baseline, which gets English examples.
- **Gemma-E2B is exactly +6.3 in all four columns. Gemma-E4B is exactly +6.6 in all four.**
- The caption says "approximately 7–8% higher", but most cells are 6–7.
- The section heading says few-shot prompting "helps close the performance gap", while the text below it says the gaps "remain largely unchanged".

Ask whether Table 13 was actually run.

## C9. Fine-tuning setup is inconsistent and may leak test data

<span class="st st-ok">Confirmed</span>

| | Appendix C.1 | Section 5.2 and Table 14 |
|---|---|---|
| Method | LoRA | QLoRA, 4-bit |
| Models | 3 (incl. "Gemma-2-7B") | 2 |
| Data | All 3 levels, 80/20 split | 50% level only, 90/10 split |
| Size | 395,076 training items | 14,848 eval items |

- Neither size fits the source data. 32,077 source items × 4 languages × 3 levels = 384,924, and 50% only would be 128,308.
- Appendix A.1 says **all** source instances were kept for training. Nothing says the 700 test items were removed.
- The scores are implausibly high: 100% on question decomposition, 99.6% on NLI, 100% on paraphrase, and **98.7% on GSM8K for an 8B model and 98.5% for a 3B model** (new). Those math scores are far above what models of this size normally reach.
- The "Overall" exact match (86.3%) equals neither the mean of the language rows (85.4%) nor the mean of the task columns (90.0%) (new). The weighting may explain this, but it isn't stated.
- Table 14 tests on its own split, not the benchmark, and shows no base-model numbers. So "fine-tuned models outperform larger baselines" is never actually shown.
- Appendix D.2 says gains hold "across all seven tasks", but Table 14 shows five.

## C10. Human validation is very thin

<span class="st st-ok">Confirmed</span>

- The paper says there were **four annotators** (one per language) and also **two per language**. Two per language would need eight.
- The number of items rated is never given.
- **The actual naturalness ratings are never reported.** Only agreement (κ) is shown.
- Every κ in Table 11 is exactly **0.00 or 1.00**, which only happens with one or very few items per cell.
- The per-language κ in Table 3 (0.52, 0.48, 0.56, 0.91) is just the mean of those 0s and 1s across tasks. For example, Gujarati: (1+1+0.33+1+1+1+1)/7 = 0.905.
- κ = 0 means agreement no better than chance. That is what Word Analogy and GSM8K get in three of four languages, yet the data is called "validated".

## C11. ChrF is used the wrong way

<span class="st st-ok">Confirmed</span>

- ChrF is an automatic metric, but Section 3.3 lists it as one of the two **human** rating aspects.
- It compares romanized mixed text with the **English** source, so it mostly measures how much English is left. The paper itself says Bengali and Tamil score higher because "denser preserved English structure".
- Table 11 repeats the same ChrF value for every task within a language, so the "averaged across all seven tasks" values were never computed per task.
