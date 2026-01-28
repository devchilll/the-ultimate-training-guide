# Post-Training & Alignment Interview Prep Guide

> **Goal**: Prepare for LLM post-training/alignment roles at Tier-0 labs (DeepMind, Anthropic, OpenAI, xAI).

This guide covers the fundamental building blocks and hands-on experience needed for roles in model alignment, RLHF, and post-training optimization.

---

## 📚 Structure

| Document | Purpose |
|----------|---------|
| [**knowledge.md**](./knowledge.md) | Conceptual foundations—what you need to *understand* |
| [**handson.md**](./handson.md) | Practical labs—what you need to *build* |

---

## 🎯 Core Topics Covered

### Knowledge (6 Pillars)
0. **Foundations** — Attention, loss functions, tokenization
1. **Alignment Methodologies** — SFT, DPO, GRPO, PPO
2. **Synthetic Data** — Self-Instruct, distillation, rejection sampling
3. **Infrastructure** — LoRA, vLLM, quantization
4. **Evaluation** — LLM-as-Judge, red-teaming, benchmarks
5. **Interview Prep** — System design, coding, portfolio strategy

### Hands-On (6 Stages)
0. **Pre-training Fundamentals** — Train a tiny LM from scratch
1. **SFT Foundations** — LoRA fine-tuning with Unsloth
2. **Preference Alignment** — DPO implementation
3. **Reasoning RL** — GRPO for math/logic tasks
4. **Tool Use** — Function calling & multi-LoRA serving
5. **Evaluation** — Build a comprehensive eval suite

---

## 🗓️ Suggested Timeline

| Phase | Duration | Focus |
|-------|----------|-------|
| Foundations | 2 weeks | Pillar 0 + Stage 0-1 |
| Alignment | 4 weeks | Pillars 1-2 + Stages 2-3 |
| Production | 4 weeks | Pillars 3-4 + Stages 4-5 |
| Interview Prep | 2+ weeks | Mock interviews + portfolio |

**Total: ~12 weeks** for comprehensive preparation.

---

## 💻 Compute Requirements

Most labs can run on **Colab Free/Pro**:
- Stages 0-1: Colab Free (T4)
- Stages 2-5: Colab Pro (A100) or local GPU (RTX 3090/4090)

---

## 🚀 Getting Started

1. Read [knowledge.md](./knowledge.md) Pillar 0 (Foundations)
2. Complete [handson.md](./handson.md) Stage 0 (nanoGPT)
3. Progress through each pillar + corresponding stage
4. Build portfolio projects demonstrating deeper expertise
