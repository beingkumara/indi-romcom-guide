---
title: Issues found
weight: 7
sidebar:
  open: true
---

This section lists every problem found in the preliminary version (arXiv 2606.30790v1), ordered by how much it matters. Every item was re-checked against the paper's PDF, including tables and figures, and every number was recomputed. The [validation log](/docs/validation.html) shows how.

## Status labels

| Label | Meaning |
|---|---|
| <span class="st st-ok">Confirmed</span> | Re-checked against the text; holds as stated |
| <span class="st st-fix">Corrected</span> | Earlier version of this point was partly wrong; now fixed |
| <span class="st st-new">New</span> | Found during validation; wasn't in the first list |
| <span class="st st-pdf">Withdrawn</span> | Turned out to be a text-extraction glitch; listed on the [validation page](/docs/validation.html) only |

## Summary

{{< cards >}}
  {{< card link="/docs/issues/critical.html" title="Critical (11)" icon="exclamation-circle" subtitle="Problems that can change whether the results are valid: taxonomy, labels, metric definitions, duplicate rows, leakage." >}}
  {{< card link="/docs/issues/claims.html" title="Claims beyond the evidence (12)" icon="scale" subtitle="Conclusions the tables don't support." >}}
  {{< card link="/docs/issues/examples.html" title="Broken examples (5)" icon="document-text" subtitle="Problems inside the paper's own example items." >}}
  {{< card link="/docs/issues/citations.html" title="Citation errors (6)" icon="book-open" subtitle="Wrong or inconsistent references." >}}
  {{< card link="/docs/issues/writing.html" title="Writing and presentation (5)" icon="pencil" subtitle="Counts, typos, broken references." >}}
{{< /cards >}}

## If you only read five

1. [C1](/docs/issues/critical.html#c1-the-mixing-rules-contradict-each-other): the paper has two incompatible definitions of the mixing categories and levels.
2. [C5](/docs/issues/critical.html#c5-nli-labels-are-mapped-two-different-ways): NLI labels are mapped differently in the prompt and in the data.
3. [C6](/docs/issues/critical.html#c6-the-reply-in-english-metric-is-defined-two-ways): the "reply in English" metric would flag correct 25%-mixed replies as wrong.
4. [C7](/docs/issues/critical.html#c7-three-different-models-have-identical-results): three different models have identical results in three tables.
5. [C9](/docs/issues/critical.html#c9-fine-tuning-setup-is-inconsistent-and-may-leak-test-data): the fine-tuning setup contradicts itself and may train on test items.
