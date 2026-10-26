---
title: How this was checked
weight: 8
---

Every issue on this site was checked against the paper (arXiv 2606.30790v1) before it was listed.

## Method

1. **Text check.** Every claim was compared with the paper's full extracted text (main text and appendix), quote by quote.
2. **Arithmetic.** All numbers in Tables 4, 6, 7, 11, 13 and 14 were typed in and recomputed with a script:
   - performance gaps (English minus each mixed level),
   - Table 13 minus Table 6 for every cell,
   - RDR averages and whether each row rises,
   - the κ and ChrF averages in Table 3,
   - the fine-tuning sizes and averages in Table 14.
3. **Outside facts.** Dataset language coverage and citation sources were checked against the IndicXTREME and IndicLLMSuite papers.
4. **PDF check.** Every point that depended on how a table cell, a non-Latin script or a figure came out of the text extraction was then checked against the PDF itself, page by page, including Figures 3, 4 and 5.

## What was not checked

- **Figures 1, 2 and 6** were not examined in detail. Nothing on this site depends on them.
- The Hugging Face dataset pages could not be opened from this environment. Language coverage on the [Telugu page](/docs/telugu.html) comes from the dataset papers and should be confirmed.
