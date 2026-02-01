# Post-Training & Alignment Prep Guide

> [!NOTE]
> This guide was created with the help of publicly available LLMs and curated resources. It is intended as a learning reference, not professional career advice. Always verify information and do your own research.

---

**Goal**: Prepare for LLM post-training/alignment roles at Tier-0 labs (DeepMind, Anthropic, OpenAI, xAI).

This guide covers the fundamental building blocks and hands-on experience needed for roles in model alignment, RLHF, and post-training optimization.

---

## 📚 Guide Structure

| Document | Purpose |
|----------|---------|
| [**knowledge.md**](./knowledge.md) | Conceptual foundations—what you need to *understand* |
| [**handson.md**](./handson.md) | Practical labs—what you need to *build* |
| [**resources.md**](./resources.md) | Curated links—papers, tools, courses, blogs |
| [**sprint.md**](./sprint.md) | ⚡ **2-3 week sprint** with P0/P1/P2 priorities |

### 📁 Lab Directories

```
labs/
├── 00_pretraining_fundamentals/   # nanoGPT from scratch
├── 01_sft_foundations/            # LoRA fine-tuning
├── 02_preference_alignment/       # DPO training
├── 03_reasoning_rl/               # GRPO implementation
├── 04_tool_use/                   # Function calling + S-LoRA
└── 05_evaluation/                 # LLM-as-Judge + red-teaming

infra/                             # vLLM configs, quantization guides
```

---

## 🎯 Core Topics Covered

### Knowledge (6 Pillars)
| # | Pillar | Key Topics |
|---|--------|------------|
| 0 | **Foundations** | Attention, cross-entropy, tokenization |
| 1 | **Alignment** | SFT, DPO, GRPO, PPO, RLHF vs RLAIF |
| 2 | **Synthetic Data** | Distillation, rejection sampling, Self-Instruct |
| 3 | **Infrastructure** | LoRA, Flash Attention, vLLM, S-LoRA, quantization |
| 4 | **Evaluation** | LLM-as-Judge, reward hacking, red-teaming |
| 5 | **Interview Prep** | System design, coding, portfolio strategy |

### Hands-On (6 Stages)
| # | Stage | Timeline | Compute |
|---|-------|----------|---------|
| 0 | Pre-training (nanoGPT) | Week 1 | Colab Free |
| 1 | SFT with LoRA | Weeks 2-3 | Colab Free/Pro |
| 2 | DPO preference alignment | Weeks 4-5 | Colab Pro |
| 3 | GRPO reasoning RL | Weeks 6-8 | Colab Pro+ / Local |
| 4 | Tool use & S-LoRA | Weeks 9-10 | Colab Pro+ / Local |
| 5 | Evaluation & red-teaming | Weeks 11-12 | Colab Free + API |

---

## ⚡ Short on Time? Use Sprint Mode

**Only have 2-3 weeks?** See [**sprint.md**](./sprint.md) for:
- P0/P1/P2 priority ratings for every topic
- Day-by-day schedule for 2-3 weeks
- Must-complete checklist

### P0 Essentials (2 weeks minimum)
| Concept | Hands-On |
|---------|----------|
| Attention mechanism | nanoGPT (Stage 0) |
| DPO loss derivation | SFT with Unsloth (Stage 1) |
| LoRA memory math | — |
| Flash Attention | — |

---

## 🗓️ Full Study Timeline (12 weeks)

| Phase | Duration | Focus |
|-------|----------|-------|
| **Foundations** | 2 weeks | Pillar 0 + Stages 0-1 |
| **Alignment** | 4 weeks | Pillars 1-2 + Stages 2-3 |
| **Production** | 4 weeks | Pillars 3-4 + Stages 4-5 |
| **Interview Prep** | 2+ weeks | Mock interviews + portfolio |

---

## 💻 Compute Requirements

| Stage | Hardware |
|-------|----------|
| 0-1 | Colab Free (T4) — 1B-3B models with 4-bit |
| 2-5 | Colab Pro (A100) or local RTX 3090/4090 |

---

## 🚀 Getting Started

1. **Read** [knowledge.md](./knowledge.md) Pillar 0 (Foundations)
2. **Watch** Karpathy's ["Let's build GPT"](https://www.youtube.com/watch?v=kCc8FmEb1nY) (2hr)
3. **Complete** [labs/00_pretraining_fundamentals](./labs/00_pretraining_fundamentals/)
4. **Progress** through each pillar + corresponding lab
5. **Build** portfolio projects demonstrating depth

---

## 📖 Key Resources

From [resources.md](./resources.md):

| Category | Top Pick |
|----------|----------|
| **Playbook** | [Smol Training Playbook](https://huggingface.co/spaces/HuggingFaceTB/smol-training-playbook) |
| **RLHF** | [RLHF Book](https://rlhfbook.com/) by Nathan Lambert |
| **Code** | [nanoGPT](https://github.com/karpathy/nanoGPT) |
| **Framework** | [Unsloth](https://github.com/unslothai/unsloth) |
| **Papers** | DPO, LoRA, DeepSeek-R1, Flash Attention |
