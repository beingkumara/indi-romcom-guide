---
title: Claims beyond the evidence
weight: 2
---

These are conclusions the paper states that its own tables don't support.

## M1. "Severe, monotonic degradation" isn't what Table 6 shows

<span class="st st-ok">Confirmed</span>

- Most of the drop happens from **English to 25%**. After that, rows are nearly flat. LLaMA-3.2-1B: +12.8, +12.7, +12.8. LLaMA-3.1-8B: +1.5, +2.4, +2.2. Qwen2.5-1.5B: +3.1, +2.9, +3.0.
- The text says only the Qwen3 models have negative gaps. **TamilLLaMA-7B** is negative too (−1.7, −0.6, −0.6).
- Since 25% NLI and sentiment items are almost pure English (C4), the English-to-25% drop may come from prompt or format differences, not from mixing.

(Small ±0.1 mismatches between the PG columns and BL minus CM are rounding, not errors.)

## M2. "RDR rises with mixing across nearly all models" is false for 7 of 19

<span class="st st-ok">Confirmed</span>

RDR is flat or falling for LLaMA-3.2-1B (51.0 → 49.4), LLaMA-3.1-8B, LLaMA-3.1-70B, Qwen2.5-1.5B, Qwen3-4B (99.9 → 97.8) and Qwen3.5-2B. It is non-monotonic for TamilLLaMA-7B (16.6 → 21.7 → 21.3).

## M3. The abstract's headline claim isn't tested

<span class="st st-ok">Confirmed</span>

The abstract says reasoning tasks degrade less than detection tasks "because the generated explanations offer necessary context".

- No per-task performance gap is reported. Figure 4 averages over the mixing levels and shows no English baseline per task.
- Section 5.1 says Word Analogy, a reasoning task, has among the *lowest* accuracy.
- The "because" is never tested.

## M4. Some baselines look like answer-parsing failures

<span class="st st-ok">Confirmed</span>

- Qwen3-14B (29.5%) scores below Qwen2.5-1.5B (43.4%) **in English**. Qwen3.5-2B (58.0%) beats Qwen3.5-9B (49.7%).
- Most models score **below 50% on toxicity**, a binary task the paper says is label-balanced. That is worse than guessing.
- In Figure 4, **6 of the 10 plotted models score almost exactly 50% on paraphrase**, a balanced yes/no task. That is what a model gets by always giving the same answer.
- All of these point to broken answer extraction, for example Qwen3's thinking tokens not being stripped.
- Decoding settings (temperature, max tokens) are never given.

## M5. Promised analyses never appear

<span class="st st-ok">Confirmed</span>

- **VCR** is defined in Section 4.3 and C.3, but no VCR numbers are reported.
- **Cohen's d**, **McNemar's test** and the **Spearman VCR–RDR correlation** are promised in C.3 and never shown.
- The **human vs GPT-4o judge agreement** is promised and never shown.
- It isn't explained how a 3-point GPT-4o rating becomes an accuracy percentage.

## M6. Task definitions disagree between tables

<span class="st st-ok">Confirmed</span>

- **Word analogy:** Table 8 says Correct (1) / Incorrect (0) classification, but Table 5 asks the model to generate the missing word.
- **Toxicity:** Table 2 says "Detection + Refusal", but refusal is never scored. Table 5 outputs the word "toxic", while Table 8 uses Toxic = 0, Non-Toxic = 1.
- **Exact match:** if CAT-C swaps label words into the Indian language, it isn't said what string the gold label is matched against.

## M7. Data sourcing contradicts itself

<span class="st st-ok">Confirmed</span>

- Section 3.1 says all tasks come from "well-validated public sources", but 52 of the 100 Word Analogy items were **written by the authors** (B.6).
- The paper says sampling was stratified, but B.6 says Toxicity was a **random** draw.
- Toxicity's source pool is 10,000 in Table 8 and 90.3K in B.6.
- Toxic items come from IndicAlign-Toxic and benign items from IndicAlign-Instruct, so a model may tell them apart by style alone.
- GSM8K is listed as 8,000 items. The official train split is 7,473 and train plus test is 8,792, so 8,000 matches neither.
- The Tamil paraphrase translations were made by the authors, and no validation of them is described.

## M8. The language explanations don't hold up

<span class="st st-ok">Confirmed</span>

- Tamil's difficulty is blamed on its "Dravidian SOV syntax", but Appendix A.1 says **all four** languages are SOV.
- Gujarati is said to have "near-zero coverage" in Indian-language pretraining, but IndicLLMSuite and Sarvam both include Gujarati.
- After fine-tuning (Table 14), **Hindi scores lowest** (70.1%), which contradicts "Hindi is easiest". The paper doesn't explain this.

## M9. The same model families build, judge and win

<span class="st st-ok">Confirmed</span>

Claude Sonnet 4.6 wrote the translations and the code-mixing, and Claude Opus 4.6 is the top model. GPT-4o is the judge for generation tasks, while GPT-3.5 is a test subject. Possible family bias isn't discussed.

## M10. The romanization scheme isn't stated

<span class="st st-ok">Confirmed</span>

The paper mixes three romanization sources (IndicXlit, Aksharamukha, IndicLLMSuite) and calls the resulting differences "natural variability". Variation between tools isn't the same as how people actually type. The paper never says which Aksharamukha target scheme was used, and scholarly schemes (IAST, ISO) use diacritics nobody types on a phone.

## M11. The conclusion overclaims

<span class="st st-ok">Confirmed</span>

The conclusion says the results are "proving that targeted code-mixed supervision is necessary" and that the problem "cannot be resolved by model scale or native-script pretraining alone". But:

- native-script input is never evaluated, even though Table 1 lists the benchmark as covering native script, and
- the fine-tuning evidence has the problems listed in [C9](/docs/issues/critical.html#c9-fine-tuning-setup-is-inconsistent-and-may-leak-test-data).

## M12. "Math scores highest" is contradicted by Figure 4

<span class="st st-ok">Confirmed</span>

Section 5.1 says GSM8K "yields the highest accuracy overall (up to ~80% for LLaMA-3.1-70B)", and explains this with CAT-0 protection of numbers. In Figure 4, **sentiment is higher for almost every model**: about 77–95%, with LLaMA-3.1-8B near 95%. GSM8K tops out around 80%.

The same paragraph calls sentiment "the most consistent cross-model performance", but TamilLLaMA-7B scores only about 15% on it in the same figure.
