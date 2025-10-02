# LLM-Scratch-109M
A 109 M-parameter GPT-2-style transformer trained from scratch with Hugging Face transformers.

## Overview
Educational repo that reproduces the full pre-training loop for a small decoder-only LLM:
+ 109 M params (12 layer, 768 dim, 12 heads)
+ Trained from random init on 513 M tokens of OpenWebText
+ Single-node, 31hr on 1×T4 (fp16, AdamW)
+ Final val loss 3.45 (see loss_curve.png)
+ Generates Web article style text, keeps grammar, maintains some context over 2-3 sentences, hallucinates—exactly what you expect from an under-trained base model.

## What you’ll see
✅ Mostly grammatical sentences
❌ Context drift, repetition, fake facts
→ Normal for a 109 M model stopped at ~4 ep.

## Limitations
+ No downstream eval, no alignment, no safety filter.
+ Not production-ready; for engineering demo only.
+ 
## Future ideas
+ Keep training to 1 B tokens & plot perplexity vs. compute.
+ Add LoRA fine-tune on Wiki-medical or Stack-exchange.
+ Plug in a tiny retrieval index to curb hallucinations.
