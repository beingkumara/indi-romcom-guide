---
title: Your Telugu work
weight: 6
---

Prof. Verma's message: the benchmark is being **expanded with Kannada, Malayalam and Telugu**, and **issues in the existing Hindi, Bengali, Gujarati and Tamil data are being fixed**. You will likely own **Telugu**.

## What Telugu brings

- **Dravidian, like Tamil.** Verb at the end (SOV), and words are built by stacking suffixes (*agglutinative*). Tamil's handling in the paper is your closest template.
- **Mixing happens inside words.** English words take Telugu suffixes: *exam**-ki***, *phone**-lo***, *office**-ki** velthunna*.
- **English verb + Telugu "do".** A very common pattern is an English verb followed by *cheyyi/chesanu*: *download chey*, *cancel chesanu*, *submit chesava?* The paper's taxonomy has no category for this, so you should raise it.
- **Spelling varies a lot.** *ledu / ledhu*, *chesanu / chesaanu*, *em / emi*, *vaadu / vadu*. Decide early how much of this to keep.

## Where each task's Telugu data comes from

| Task | Source has Telugu? | What you do |
|---|---|---|
| Word analogy | No (English only) | Translate → refine → check |
| Question decomposition | No (English only) | Translate → refine → check |
| Math (GSM8K) | No (English only) | Translate → refine → check |
| Paraphrase | Yes. IndicXParaphrase covers 10 languages including Telugu, but not Tamil | Use directly |
| Sentiment | Yes. IndicSentiment covers 13 languages including Telugu | Use directly |
| Inference (NLI) | Yes. IndicXNLI covers 11 languages including Telugu | Use directly. **Check the label mapping** |
| Toxicity | Likely. Toxic Matrix was generated in English and translated into 14 Indian languages | Confirm Telugu on Hugging Face |

{{< callout type="info" >}}
The language lists above come from the IndicXTREME and IndicLLMSuite papers. Confirm them on the Hugging Face dataset pages before you plan the work around them.
{{< /callout >}}

## What the mixing levels could look like in Telugu

These are **my illustrative drafts** to show the idea. Check them yourself, because you are the native speaker.

| Level | Sentiment instruction, Telugu-English |
|---|---|
| 25% | Classify the *bhaavana* of the following product review as positive (1), neutral (0), or negative (−1). |
| 50% | Ee product review yokka *bhaavana* positive (1), neutral (0), *leda* negative (−1) ani classify cheyyandi. |
| 75% | Kindi product review lo unna *bhaavana*-ni positive (1), neutral (0), *leda* negative (−1) ga *vargeekarinchandi*. |

Notice how the 75% version needs *classify cheyyandi* → *vargeekarinchandi*. Real Telugu speakers would usually keep *classify chey*. That gap between "more Telugu words" and "more natural" is exactly what naturalness ratings should catch.

## Your likely jobs

{{% steps %}}

### Build the native-language version
Translate the three English-only tasks and pull Telugu from the four AI4Bharat datasets.

### Generate the three mixing levels
Run the taxonomy-guided prompt and keep the swap logs.

### Romanize
Use IndicXlit / Aksharamukha. Agree on a romanization scheme first (see below).

### Validate as a native speaker
This is probably why you were picked. Rate naturalness, and catch broken output like the paper's garbled Tamil example ([E2](/docs/issues/examples.html#e2-tamil-decomposition-example-is-garbled)).

### Possibly run the models
Compute accuracy and RDR for Telugu.

{{% /steps %}}

## Agree on these before generating anything

Telugu will inherit the paper's problems unless these get fixed first:

1. **One category taxonomy.** The paper has two incompatible versions ([C1](/docs/issues/critical.html#c1-the-mixing-rules-contradict-each-other)). Pick one, and add a category for English verb + *cheyyi* constructions.
2. **Mixing targets that the output actually reaches** ([C3](/docs/issues/critical.html#c3-the-data-misses-its-own-mixing-targets)). Measure CMI on each batch and regenerate items that miss.
3. **A task-specific prompt.** The current prompt asks for "premise" and "hypothesis" CMI even for math ([C2](/docs/issues/critical.html#c2-the-generation-prompt-is-written-for-nli-only)).
4. **The NLI label mapping** ([C5](/docs/issues/critical.html#c5-nli-labels-are-mapped-two-different-ways)). Use IndicXNLI's own: 0 = entailment, 1 = neutral, 2 = contradiction.
5. **A romanization scheme.** For example, no diacritics, with long vowels written as double letters (*aa*, *ee*) or not. Write it down.
6. **A fixed RDR definition** that doesn't count correct romanized replies as English ([C6](/docs/issues/critical.html#c6-the-reply-in-english-metric-is-defined-two-ways)).
7. **A validation protocol:** how many items per task and level, two raters each, and reporting the **mean naturalness score**, not only agreement ([C10](/docs/issues/critical.html#c10-human-validation-is-very-thin)).
8. **A held-out test set** that never enters fine-tuning data ([C9](/docs/issues/critical.html#c9-fine-tuning-setup-is-inconsistent-and-may-leak-test-data)).

## Questions for the next meeting

- Which taxonomy is the real one: Table 9 or the B.3 prompt?
- Are the Mistral-7B / Qwen2.5-7B / Qwen3.5-9B results re-run, or were they placeholders?
- Was the NLI gold data scored with 0 = entailment or 1 = entailment?
- Who validates Telugu besides me? The paper needs two raters per language.
- Will Telugu be evaluated on all 19 models, or a subset?
- Should the fine-tuning ablation be redone with the test items removed?
