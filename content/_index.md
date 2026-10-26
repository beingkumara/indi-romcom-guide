---
title: Indi-RomCoM Guide
layout: hextra-home
---

{{< hextra/hero-badge link="https://arxiv.org/abs/2606.30790" >}}
  <span>arXiv 2606.30790 · preliminary version</span>
  {{< icon name="arrow-circle-right" attributes="height=14" >}}
{{< /hextra/hero-badge >}}

<div class="hx:mt-6 hx:mb-6">
{{< hextra/hero-headline >}}
  Can LLMs read&nbsp;<br class="hx:sm:block hx:hidden" />"Nenu exam ki prepare avvali"?
{{< /hextra/hero-headline >}}
</div>

<div class="hx:mb-12">
{{< hextra/hero-subtitle >}}
  A plain-language guide to the Indi-RomCoM benchmark: what it tests,&nbsp;<br class="hx:sm:block hx:hidden" />how its data is built, what it found, what is wrong with it, and how Telugu gets added.
{{< /hextra/hero-subtitle >}}
</div>

<div class="hx:mb-6">
{{< hextra/hero-button text="Start reading" link="/docs/index.html" >}}
</div>

<div class="hx:mt-6"></div>

{{< hextra/feature-grid >}}
  {{< hextra/feature-card
    title="What the paper is about"
    subtitle="Romanized code-mixing in one page: the problem, the benchmark, and the main finding."
    link="/docs/the-idea.html"
  >}}
  {{< hextra/feature-card
    title="How the data is built"
    subtitle="The four-phase pipeline: translate, pick words to swap, mix at 25/50/75%, romanize."
    link="/docs/pipeline.html"
  >}}
  {{< hextra/feature-card
    title="Results"
    subtitle="19 models, 4 metrics, zero-shot and few-shot, plus the fine-tuning ablation."
    link="/docs/results.html"
  >}}
  {{< hextra/feature-card
    title="Issues found"
    subtitle="Every problem found in the paper, checked against the text and ranked by how much it matters."
    link="/docs/issues/index.html"
  >}}
  {{< hextra/feature-card
    title="Your Telugu work"
    subtitle="Which source datasets already have Telugu, what to fix first, and questions for the next meeting."
    link="/docs/telugu.html"
  >}}
  {{< hextra/feature-card
    title="How this was checked"
    subtitle="The validation log: what was recomputed, what changed from the first read, and what still needs the PDF."
    link="/docs/validation.html"
  >}}
{{< /hextra/feature-grid >}}
