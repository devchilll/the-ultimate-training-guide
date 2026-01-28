# Post-Training & Alignment Interview Prep Guide

> **Goal**: Prepare for LLM post-training/alignment roles at Tier-0 labs (DeepMind, Anthropic, OpenAI, xAI).

This guide covers the fundamental building blocks and hands-on experience needed for roles in model alignment, RLHF, and post-training optimization.

---

## 📚 Guide Structure

| Document | Purpose |
|----------|---------|
| [**knowledge.md**](./knowledge.md) | Conceptual foundations—what you need to *understand* |
| [**handson.md**](./handson.md) | Practical labs—what you need to *build* |
| [**resources.md**](./resources.md) | Curated links—papers, tools, courses, blogs |

---

## 🎯 Core Topics Covered

### Knowledge (6 Pillars)
| # | Pillar | Topics |
|---|--------|--------|
| 0 | **Foundations** | Attention, loss functions, tokenization |
| 1 | **Alignment Methodologies** | SFT, DPO, GRPO, PPO |
| 2 | **Synthetic Data** | Self-Instruct, distillation, rejection sampling |
| 3 | **Infrastructure** | LoRA, vLLM, quantization |
| 4 | **Evaluation** | LLM-as-Judge, red-teaming, benchmarks |
| 5 | **Interview Prep** | System design, coding, portfolio strategy |

### Hands-On (6 Stages)
| # | Stage | Timeline | Compute |
|---|-------|----------|---------|
| 0 | Pre-training fundamentals | Week 1 | Colab Free |
| 1 | SFT with LoRA | Weeks 2-3 | Colab Free/Pro |
| 2 | DPO preference alignment | Weeks 4-5 | Colab Pro |
| 3 | GRPO reasoning RL | Weeks 6-8 | Colab Pro+ / Local |
| 4 | Tool use & function calling | Weeks 9-10 | Colab Pro+ / Local |
| 5 | Evaluation & red-teaming | Weeks 11-12 | Colab Free + API |

---

## 🗓️ Suggested Study Timeline

| Phase | Duration | Focus |
|-------|----------|-------|
| **Foundations** | 2 weeks | Pillar 0 + Stages 0-1 |
| **Alignment** | 4 weeks | Pillars 1-2 + Stages 2-3 |
| **Production** | 4 weeks | Pillars 3-4 + Stages 4-5 |
| **Interview Prep** | 2+ weeks | Mock interviews + portfolio |

**Total: ~12 weeks** for comprehensive preparation.

---

## 💻 Compute Requirements

Most labs can run on **Colab Free/Pro**:
- **Stages 0-1**: Colab Free (T4) — 1B-3B models with 4-bit quantization
- **Stages 2-5**: Colab Pro (A100) or local GPU (RTX 3090/4090) — 7B+ models

---

## 🚀 Getting Started

1. **Read** [knowledge.md](./knowledge.md) Pillar 0 (Foundations)
2. **Watch** Karpathy's ["Let's build GPT"](https://www.youtube.com/watch?v=kCc8FmEb1nY) lecture
3. **Complete** [handson.md](./handson.md) Stage 0 (train nanoGPT)
4. **Progress** through each pillar + corresponding stage
5. **Build** portfolio projects demonstrating deeper expertise

---

## 📖 Key Resources

Start with these essentials from [resources.md](./resources.md):

| Category | Top Pick |
|----------|----------|
| **Playbook** | [Smol Training Playbook](https://huggingface.co/spaces/HuggingFaceTB/smol-training-playbook) |
| **RLHF Deep Dive** | [RLHF Book](https://rlhfbook.com/) by Nathan Lambert |
| **Hands-On Code** | [nanoGPT](https://github.com/karpathy/nanoGPT) by Karpathy |
| **Framework** | [Unsloth](https://github.com/unslothai/unsloth) for efficient fine-tuning |
| **Community** | [r/LocalLLaMA](https://reddit.com/r/LocalLLaMA) |
