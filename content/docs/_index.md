---
title: Start here
weight: 1
sidebar:
  open: true
---

**Indi-RomCoM** is a test set (a *benchmark*) for checking how well large language models handle the way many Indians actually type: their own language mixed with English, all written in English letters.

> *"Yeh loan ke liye mujhe kya karna padega?"* is Hindi-English.
> *"Nenu exam ki prepare avvali, but time ledu."* is Telugu-English.

The preliminary paper covers **Hindi, Bengali, Gujarati and Tamil**. The next version adds **Kannada, Malayalam and Telugu** and fixes problems in the existing data.

{{< callout type="info" >}}
**Paper:** *Indi-RomCoM: Code-Mixed Benchmark for Evaluating LLMs on Romanized Indic-English Instructions*, by Avisha Das, Mihir Parmar, Mohana Ramnath and Pulkit Verma (arXiv 2606.30790v1, 29 June 2026). [Abstract](https://arxiv.org/abs/2606.30790) · [PDF](https://arxiv.org/pdf/2606.30790v1)
{{< /callout >}}

## The project in three sentences

1. LLMs do well on clean English and on native-script Indian languages, but nobody had tested them properly on **romanized code-mixed** text.
2. The authors built 8,400 test items: **7 tasks × 4 languages × 3 mixing levels** (25%, 50%, 75%), each from 100 base examples per task.
3. Every model they tried got worse on mixed text, models often answered in plain English when asked to answer in the mixed style, and fine-tuning on mixed data seemed to help.

## How to read this site

{{< cards >}}
  {{< card link="/docs/the-idea.html" title="1. The idea" icon="light-bulb" subtitle="What code-mixing is and why it matters." >}}
  {{< card link="/docs/benchmark.html" title="2. The benchmark" icon="table" subtitle="Tasks, languages and mixing levels." >}}
  {{< card link="/docs/pipeline.html" title="3. The pipeline" icon="cog" subtitle="How each test item is made." >}}
  {{< card link="/docs/results.html" title="4. Results" icon="chart-bar" subtitle="What the models did." >}}
  {{< card link="/docs/telugu.html" title="5. Telugu" icon="user" subtitle="Your part of the extension." >}}
  {{< card link="/docs/issues/index.html" title="6. Issues" icon="exclamation" subtitle="What is wrong with the paper." >}}
{{< /cards >}}

The [glossary](/docs/glossary.html) explains every term (CMI, RDR, ChrF, κ and so on) in one line each.
