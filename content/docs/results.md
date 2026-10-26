---
title: Evaluation and results
weight: 5
---

## Models tested

The introduction says 19 models; the conclusion says 17. The results tables list 19.

| Group | Models |
|---|---|
| Closed | GPT-3.5-Turbo, Claude Opus 4.6, Gemini 3.5 Flash |
| LLaMA | LLaMA-3.2-1B, LLaMA-3.1-8B, LLaMA-3.1-70B |
| Mistral | Mistral-3B, Mistral-7B |
| Qwen | Qwen2.5-1.5B, Qwen2.5-7B, Qwen3-4B, Qwen3-14B, Qwen3.5-2B, Qwen3.5-9B |
| Gemma | Gemma-E2B, Gemma-E4B |
| Indic | Airavata-7B, TamilLLaMA-7B, Sarvam-30B |

Each model is tested **zero-shot** (no examples) and **3-shot** (three examples in the same mixed style).

## The four metrics

| Metric | Meaning | Better is |
|---|---|---|
| **Accuracy (ACC)** | Exact label match for classification; task rubrics, with GPT-4o as judge, for generation tasks | Higher |
| **Register Defection Rate (RDR)** | Share of replies that fall back to English when asked to reply in the mixed style | Lower |
| **Vocabulary Coverage Rate (VCR)** | Share of the swapped Indian words that the model's tokenizer has as whole tokens | Higher |
| **Performance Gap (PG)** | English accuracy minus mixed accuracy | Lower |

VCR is defined but no VCR numbers appear anywhere in the paper.

## Zero-shot accuracy (paper's Table 6)

Average over 7 tasks and 4 languages. BL = English baseline.

| Model | BL | 25% | 50% | 75% | PG-25 | PG-50 | PG-75 |
|---|---|---|---|---|---|---|---|
| GPT-3.5-Turbo | 52.3 | 46.1 | 44.8 | 44.3 | +6.2 | +7.5 | +8.0 |
| Claude Opus 4.6 | 68.7 | 63.4 | 61.9 | 61.2 | +5.3 | +6.8 | +7.5 |
| Gemini 3.5 Flash | 61.4 | 56.2 | 54.8 | 54.1 | +5.2 | +6.6 | +7.3 |
| LLaMA-3.2-1B | 24.3 | 11.5 | 11.6 | 11.6 | +12.8 | +12.7 | +12.8 |
| LLaMA-3.1-8B | 50.1 | 48.6 | 47.8 | 47.9 | +1.5 | +2.4 | +2.2 |
| LLaMA-3.1-70B | 54.6 | 51.5 | 50.6 | 50.5 | +3.0 | +4.0 | +4.0 |
| Mistral-3B | 37.2 | 24.8 | 22.1 | 19.7 | +12.4 | +15.1 | +17.5 |
| Mistral-7B ⚠ | 49.7 | 44.3 | 43.6 | 43.3 | +5.4 | +6.1 | +6.4 |
| Qwen2.5-1.5B | 43.4 | 40.4 | 40.5 | 40.4 | +3.1 | +2.9 | +3.0 |
| Qwen2.5-7B ⚠ | 49.7 | 44.3 | 43.6 | 43.3 | +5.4 | +6.1 | +6.4 |
| Qwen3-4B | 32.3 | 34.4 | 33.3 | 32.9 | −2.1 | −1.0 | −0.6 |
| Qwen3-14B | 29.5 | 34.7 | 34.0 | 33.8 | −5.2 | −4.5 | −4.3 |
| Qwen3.5-2B | 58.0 | 51.1 | 51.6 | 51.4 | +7.0 | +6.4 | +6.6 |
| Qwen3.5-9B ⚠ | 49.7 | 44.3 | 43.6 | 43.3 | +5.4 | +6.1 | +6.4 |
| Gemma-E2B | 43.0 | 42.0 | 40.9 | 40.7 | +1.1 | +2.1 | +2.3 |
| Gemma-E4B | 48.0 | 46.1 | 44.6 | 44.5 | +2.0 | +3.4 | +3.6 |
| Airavata-7B | 38.6 | 36.4 | 33.6 | 32.9 | +2.1 | +5.0 | +5.7 |
| TamilLLaMA-7B | 26.9 | 28.6 | 27.4 | 27.4 | −1.7 | −0.6 | −0.6 |
| Sarvam-30B | 64.2 | 59.8 | 57.3 | 56.1 | +4.4 | +6.9 | +8.1 |

⚠ These three rows are identical to the decimal, which three different models can't produce. See [issue C7](/docs/issues/critical.html#c7-three-different-models-have-identical-results).

**How to read it:** the biggest drop is usually from English to 25% mixed. After that, most rows barely move.

## Replying in English (paper's Table 7)

RDR is the share of replies that came back in English. Lower is better.

| Model | 25% | 50% | 75% | Avg |
|---|---|---|---|---|
| GPT-3.5-Turbo | 48.3 | 53.7 | 61.2 | 54.4 |
| Claude Opus 4.6 | 31.4 | 35.8 | 40.6 | 35.9 |
| Gemini 3.5 Flash | 39.2 | 44.1 | 50.3 | 44.5 |
| LLaMA-3.2-1B | 51.0 | 49.6 | 49.4 | 50.0 |
| LLaMA-3.1-8B | 99.8 | 99.7 | 99.7 | 99.7 |
| LLaMA-3.1-70B | 97.6 | 97.5 | 97.5 | 97.5 |
| Mistral-3B | 77.8 | 89.3 | 91.7 | 86.3 |
| Mistral-7B ⚠ | 60.6 | 64.7 | 65.1 | 63.5 |
| Qwen2.5-1.5B | 99.8 | 99.8 | 99.8 | 99.8 |
| Qwen2.5-7B ⚠ | 60.6 | 64.7 | 65.1 | 63.5 |
| Qwen3-4B | 99.9 | 98.7 | 97.8 | 98.8 |
| Qwen3-14B | 89.7 | 91.3 | 95.1 | 92.0 |
| Qwen3.5-2B | 99.6 | 99.6 | 99.6 | 99.6 |
| Qwen3.5-9B ⚠ | 60.6 | 64.7 | 65.1 | 63.5 |
| Gemma-E2B | 78.3 | 82.7 | 93.5 | 84.8 |
| Gemma-E4B | 74.8 | 81.3 | 84.3 | 80.1 |
| Airavata-7B | 10.4 | 18.4 | 20.7 | 16.5 |
| TamilLLaMA-7B | 16.6 | 21.7 | 21.3 | 19.9 |
| Sarvam-30B | 22.4 | 26.8 | 29.1 | 26.1 |

The paper's reading: Indian-language pretraining keeps models in the mixed style. The [RDR issue](/docs/issues/critical.html#c6-the-reply-in-english-metric-is-defined-two-ways) explains why this metric needs a closer look.

## Other findings

- **By task:** the paper says math (GSM8K) scores highest, up to about 80% for LLaMA-3.1-70B. Its own Figure 4 shows sentiment higher, at about 77–95% for most models ([M12](/docs/issues/claims.html#m12-math-scores-highest-is-contradicted-by-figure-4)). Word analogy and toxicity score lowest, and most models fall below 50% on toxicity.
- **By language:** Hindi is best, then Bengali, then Tamil. Gujarati is worst.
- **Few-shot (Table 13):** every cell is 5.5–7.3 points higher than zero-shot, but the gap between English and mixed stays about the same. The paper says the examples teach the output style, not better understanding.
- **Fine-tuning (Table 14):** LLaMA-3.2-3B and LLaMA-3.1-8B fine-tuned with QLoRA on 50%-mixed data both reach about 86% exact match. The paper concludes that mixed-language training data is necessary.
