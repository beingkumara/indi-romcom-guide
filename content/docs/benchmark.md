---
title: What's in the benchmark
weight: 3
---

Think of the benchmark as a grid with three axes: **task**, **language** and **mixing level**.

## Axis 1: seven tasks

100 base examples per task, sampled from public datasets.

| Group | Task | Source | What the model must do |
|---|---|---|---|
| Reasoning | Word analogy | Super-NaturalInstructions tasks 1152–1159 | "throw : fly :: aspire : ?" → *attain*, plus an explanation |
| Reasoning | Question decomposition | Super-NaturalInstructions tasks 168, 176, 184 | Break a question into yes/no sub-questions |
| Reasoning | Math word problems | GSM8K | Solve step by step, give the number |
| Understanding | Paraphrase | IndicXParaphrase | Do two sentences mean the same thing? (1/0) |
| Understanding | Sentiment | IndicSentiment | Product review: positive / neutral / negative |
| Understanding | Inference (NLI) | IndicXNLI | Does sentence B follow from sentence A? |
| Safety | Toxicity | IndicAlign-Toxic (Toxic Matrix) | Toxic or not, plus an explanation |

The first three exist only in English, so the authors translated them. The other four already had native-script Indian-language versions.

## Axis 2: four languages (seven after the extension)

| Language | Family | Speakers (paper's figure) | Mixed form |
|---|---|---|---|
| Hindi | Indo-Aryan | ~610M | Hinglish |
| Bengali | Indo-Aryan | ~273M | Banglish |
| Gujarati | Indo-Aryan | ~55M | Gujlish |
| Tamil | Dravidian | ~87M | Tanglish |
| *Telugu* | *Dravidian* | | *Tenglish (being added)* |
| *Kannada* | *Dravidian* | | *being added* |
| *Malayalam* | *Dravidian* | | *being added* |

The extension takes the benchmark from one Dravidian language to four.

## Axis 3: three mixing levels

| Level | What gets swapped into the Indian language | Sentence still feels like |
|---|---|---|
| **25%** | Only task words (e.g. *analogy*, *causation*) | English |
| **50%** | + connectors (*but*, *however*, *hence*) and topic nouns (*police*, *battery*) | Half and half |
| **75%** | + small words (*the*, *is*, *a*) and whole phrases (*I cannot give a response*) | The Indian language |

Numbers, names, math expressions and step labels such as `Step1:` are **never** swapped, because changing them would change the answer.

{{< callout type="warning" >}}
This table follows the paper's Tables 9 and 10. The prompt actually used to generate the data (Appendix B.3) describes the levels differently. See [issue C1](/docs/issues/critical.html#c1-the-mixing-rules-contradict-each-other).
{{< /callout >}}

## Size

**700 base examples × 4 languages × 3 levels = 8,400 test items**, plus the 700 English originals as the baseline.

With Telugu, Kannada and Malayalam added, the same design gives 700 × 7 × 3 = **14,700** mixed items.

## A real example from the paper (Table 5)

Bengali paraphrase, 50% mixed:

> **S1:** Police station-e giye ami complaint korlam je amar phone churi hoyeche.
> **S2:** Ami police station-e giye janalam amar phone ta churi giyeche.
> **Label:** 1 (paraphrase)

Every prompt ends with the same instruction: *"Please respond in the same language and script as the input."*
