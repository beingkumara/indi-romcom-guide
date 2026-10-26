---
title: Citation errors
weight: 4
---

## R1. The Indic datasets are cited three different ways

<span class="st st-ok">Confirmed</span>

IndicXParaphrase and IndicSentiment are cited as:

- Kunchukuttan et al., 2020 (the IndicNLP corpus paper) in Section 3.1 and Table 2,
- Khan et al., 2024 and Gala et al., 2024 (the Airavata paper) in Section 3.2,
- Gala et al., 2024 in Appendix A.1.

Both datasets were introduced in **IndicXTREME**: Doddapaneni et al., *Towards Leaving No Indic Language Behind*, ACL 2023.

## R2. IndicAlign-Toxic is cited two ways

<span class="st st-ok">Confirmed</span>

It is cited as Chitale et al., 2025 (the UPDESH paper) in Section 3.1, and as Khan et al., 2024 (IndicLLMSuite, the correct source) in Appendix A.1.

## R3. Core methods cite the wrong source

<span class="st st-ok">Confirmed</span>

| What | Cited as | Should be |
|---|---|---|
| Cohen's κ | Cohen 2013 (*Statistical Power Analysis*, a book about effect sizes) | Cohen 1960 |
| ChrF | Chitale et al., 2025 | Popović 2015 |
| Code-Mixing Index | Srivastava & Singh 2021 (a paper *criticising* CMI) | Das & Gambäck 2014 / Gambäck & Das 2016 |
| Matrix Language Frame | Myers-Scotton 1993, *Social Motivations for Codeswitching* | Myers-Scotton 1993, *Duelling Languages* |
| Equivalence Constraint | Poplack 2001 (encyclopedia entry) | Poplack 1980 |

The paper's own CMI ("proportion of English tokens replaced") also isn't the standard CMI formula, which is based on the share of the *dominant* language.

## R4. Model citations don't match the models used

<span class="st st-ok">Confirmed</span>

- **Sarvam-1** (a 2B model) is cited, but **Sarvam-30B** is evaluated.
- The **Gemma 4** models cite the original **Gemma 1** paper (arXiv 2403.08295).
- Every Qwen version (2.5, 3, 3.5) cites the Qwen3 report.
- Figure 1 uses "LLaMa-7B-Instruct", which isn't among the evaluated models.
- Section 4.1 and Appendix C.1 mention **"Gemma-2-7B"**. Gemma 2 was released in 2B, 9B and 27B sizes, so that model doesn't exist.

## R5. Unrelated citations

<span class="st st-ok">Confirmed</span>

**LongBench** and **M4LE**, both long-context benchmarks, are cited to justify balanced label distributions. They don't address that point.

## R6. Duplicate and garbled references

<span class="st st-ok">Confirmed</span>

- Yang & Chai 2025a and 2025b are the same paper. So are Khan 2024a and 2024b, and Khanuja 2020a and 2020b.
- LoRA's venue is printed as **"Ictr, 1(2):3"** instead of ICLR 2022.
