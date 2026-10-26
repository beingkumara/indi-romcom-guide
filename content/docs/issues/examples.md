---
title: Broken examples
weight: 3
---

These are problems in the paper's own example items (Table 5 and Table 9). They matter because they are the clearest sign of what the generated data looks like.

## E1. The "50%" math problem has no mixing

<span class="st st-fix">Corrected</span>

In the Hindi GSM8K example, the **problem** text is entirely English: *"At the bake sale, Tamara makes $32 from brownies…"*. Only the **solution** is mixed: *"Tamara ke paas 2×8 = 16 tukde the…"*.

*Correction:* my first list said the whole example was English. The solution is mixed; the problem is not.

## E2. Tamil decomposition example is garbled

<span class="st st-ok">Confirmed</span>

The example is labelled 50% mixed, but its steps are all English, and its explanation reads: *"This is a strategic vivaribhbhu into 3 ubha-ghelvi(ghal). Each bhadhi isolates a jharibharghghaghghudhiya unmai…"*. That looks like broken transliteration or model hallucination. *ubha-ghelvi(ghal)* is probably a mangled Tamil word for "sub-questions".

## E3. Tamil word inside a Gujarati example

<span class="st st-ok">Confirmed</span>

The Gujarati word-analogy explanation says *"Aa, aa **uvamai** pramane…"*. *Uvamai* (உவமை) is the **Tamil** word for analogy, and Table 9 lists it as the Tamil example. This is cross-language contamination.

## E4. Tamil "50%" sentiment example has one Tamil word

<span class="st st-ok">Confirmed</span>

*"Foldable type of microphone with mic **marrum** micro sd card slot."* The only Tamil word is *marrum* ("and"), nowhere near 50% mixing.

## E5. The math example breaks its own protected format

<span class="st st-new">New</span>

The math prompt requires every step to be written as `<<expr=result>>` (GSM8K's format), and the paper says these annotations are CAT-0: never touched. The Hindi example's solution reads:

> Tamara ke paas 2×8=`<<16>>`16 tukde the. Har ek ki qeemat $32/16=$`<<2>>`2 thi.

The expressions inside the brackets are gone (`<<16>>` instead of `<<2*8=16>>`). The protected tokens were damaged during mixing, which is exactly what CAT-0 was supposed to prevent. If other items look like this, answer extraction for GSM8K may also be affected.
