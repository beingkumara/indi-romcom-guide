---
title: How this was checked
weight: 8
---

Before this site was published, everything in the earlier explanation and issue list was re-checked against the paper.

## Method

1. **Text check.** Every claim was compared with the paper's full extracted text (arXiv 2606.30790v1, main text and appendix), quote by quote.
2. **Arithmetic.** All numbers in Tables 4, 6, 7, 11, 13 and 14 were typed in and recomputed with a script:
   - performance gaps (English minus each mixed level),
   - Table 13 minus Table 6 for every cell,
   - RDR averages and whether each row rises,
   - the κ and ChrF averages in Table 3,
   - the fine-tuning sizes and averages in Table 14.
3. **Outside facts.** Dataset language coverage and citation sources were checked against the IndicXTREME and IndicLLMSuite papers.
4. **PDF check.** Every point that depended on how a table cell, a non-Latin script or a figure came out of the text extraction was then checked against the PDF itself, page by page, including Figures 3, 4 and 5.

## What changed from the first read

| Item | Change |
|---|---|
| Human check (explanation) | Annotators rated **naturalness** only. "Fidelity" is the automatic ChrF score, not a human rating. |
| C4: toxicity example vs B.5 | **Withdrawn.** The romanized Hindi input may be the original sentence, so it doesn't prove B.5 wrong. |
| C8: few-shot shift | Range corrected from "6.3–6.8" to **5.5–7.3**. Added the exactly constant Gemma rows. |
| E1: Hindi math example | The problem is English; the **solution is mixed**. |
| M10: romanization | Softened to "scheme is unstated" instead of "diacritics by default". |
| W4: Table 6 bold | Checked in the PDF: no bold values, so the caption is wrong. **Confirmed.** |
| "Indi-RomCoMbenchmark" | Present in the PDF itself. **Confirmed**, moved to W3. |
| PG column mismatches of ±0.1 | Checked: rounding, **not** an issue. |
| Table 3 κ average 0.615 | Checked: correct when computed from Table 11. Not an issue, but it shows the κ values are averages of 0s and 1s. |

## Withdrawn after checking the PDF

These came from the text extraction, not from the paper:

| Earlier point | What the PDF shows |
|---|---|
| Hindi ChrF listed as 69.00 in Table 3 | Table 3 says **62.00**, matching Table 11 and the 67.00 average. |
| CAT-0 written as `<<alc>>` | Printed correctly as `<<calc>>`. |
| Hindi "is" given as plural हैं | Printed as **है**, which is correct. |
| Bengali "hence" and "however" look wrong | "hence" is **எனவே** (correct Tamil); "however" is **তবে** (correct Bengali). |
| "ble 4 reports" | Printed as "Table 4 reports". |
| "75%-CM)CM)" | Not in the PDF. |

## Issues added during validation

- **C2:** the generation prompt is NLI-specific.
- **C6:** a perfect 25%-mixed reply would count as "English"; the separate label and explanation RDR are never reported.
- **C9:** 98.5% and 98.7% on GSM8K after fine-tuning; the "Overall" EM matches no simple average.
- **C10:** Table 3 κ values are means of 0/1 agreements.
- **M7:** the authors' own Tamil paraphrase translations aren't validated.
- **E5** (from the PDF): the math example's `<<expr=result>>` annotations are corrupted.
- **M12** (from Figure 4): sentiment, not math, scores highest.
- **M4** (from Figure 4): 6 of 10 models sit at exactly 50% on paraphrase.
- **W5** (from Figure 4): the caption mentions dashed lines that aren't drawn.

## What was not checked

- **Figures 1, 2 and 6** were not examined in detail. Nothing on this site depends on them.
- The Hugging Face dataset pages could not be opened from this environment. Language coverage on the [Telugu page](/docs/telugu.html) comes from the dataset papers and should be confirmed.
