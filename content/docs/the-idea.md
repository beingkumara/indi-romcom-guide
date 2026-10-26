---
title: What the paper is about
weight: 2
---

## The core idea

People rarely type pure Telugu script or pure English. On phones and chat apps they mix both and write everything in English letters. The paper calls this **Romanized Code-Mixing (RCM)**.

| Style | Example |
|---|---|
| English | I have to prepare for the exam, but there is no time. |
| Telugu script | నేను పరీక్షకు సిద్ధం కావాలి, కానీ సమయం లేదు. |
| **Romanized code-mixed** | **Nenu exam ki prepare avvali, but time ledu.** |

The authors give three reasons people write this way: character limits, typing by sound on a phone keyboard, and convenience.

## The question

LLMs score well on English benchmarks and on native-script Indian-language benchmarks. The paper asks a narrower question: **do they still follow instructions and reason correctly when the instruction is romanized and code-mixed?**

The paper's Figure 1 shows an instruction-tuned LLaMA model failing on a simple "Tanglish" (Tamil-English) request.

## Why existing benchmarks didn't answer it

| Benchmark | Script | Gap the authors point to |
|---|---|---|
| GLUECoS, LinCE | Native script | Word-level labelling only (e.g. part-of-speech), no reasoning |
| CodeMixBench | Native script | Generative, but misses the spelling variation of romanized text |
| IndicDB | Native + romanized | Text-to-SQL only |
| RomanSetu | Romanized | Translation only |
| **Indi-RomCoM** | Native + romanized | Classification, generation and instruction following, at **controlled mixing levels** |

The new thing is the last column of the paper's Table 1: **mixing density**. Other benchmarks don't test how performance changes as more of the sentence switches to the Indian language.

## The main findings, in plain words

- **Every model got worse on mixed text.** Claude Opus 4.6 dropped from 68.7% (English) to 61.2% (75% mixed). Sarvam-30B, which was trained on Indian languages, dropped from 64.2% to 56.1%.
- **Models often switch back to English.** Asked to reply in the same mixed style, most open models answered in English almost every time. Only Indian-language models (Airavata, TamilLLaMA, Sarvam) mostly stayed in the mixed style.
- **Toxicity detection is weak.** Most models scored below 50% on harmful content framed in mixed language.
- **Hindi was easiest, Gujarati hardest**, roughly matching how much of each language is on the internet.
- **Three examples per prompt helped a bit** (about 6–7 points), mainly by getting models to answer in the right format.
- **Fine-tuning on mixed data helped a lot**, according to the paper. The [issues page](/docs/issues/critical.html#c9-fine-tuning-setup-is-inconsistent-and-may-leak-test-data) explains why that result needs checking.

{{< callout type="warning" >}}
Several of these findings are weaker than the paper says. See [Claims that go beyond the evidence](/docs/issues/claims.html).
{{< /callout >}}
