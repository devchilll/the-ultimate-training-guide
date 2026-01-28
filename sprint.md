# 🚀 2-3 Week Sprint Guide

> **Priority Levels**: P0 = Must know (interview critical) | P1 = Important (likely to come up) | P2 = Good to know (differentiator)

For a 2-3 week prep, focus on **P0 items only**. If you have extra time, add P1.

---

## 📚 Knowledge Priorities

### Pillar 0: Foundations

| Topic | Priority | Why |
|-------|----------|-----|
| Self-Attention (QKV, softmax, multi-head) | **P0** | Asked in every coding interview |
| Cross-entropy loss | **P0** | Must understand gradient flow |
| Temperature vs Top-P tradeoffs | **P0** | Critical for reasoning: high temp aids RL exploration, low temp for verification |
| PagedAttention (vLLM) | **P0** | Solution for memory fragmentation in agentic workflows |
| AdamW optimizer | **P1** | Know the basics, not derivation |
| Tokenization (BPE) | **P1** | Understand tradeoffs |
| Positional encodings (RoPE) | **P2** | Nice to know details |

---

### Pillar 1: Alignment Methodologies

| Topic | Priority | Why |
|-------|----------|-----|
| **Cold-Start SFT** (reasoning data curation) | **P0** | The quality of reasoning data bootstraps RL success |
| **DPO loss derivation** (why RM-free) | **P0** | Must explain why it eliminates reward model vs PPO |
| **GRPO** (DeepSeek-R1 style) | **P0** | 🔥 THE differentiator for 2026 — eliminates Critic, 50% VRAM savings |
| **RLHF pipeline** (reward model → PPO) | **P0** | Must understand the classic approach |
| Chat templates | **P0** | Practical, easy to mess up |
| PPO advantage estimation | **P1** | Know conceptually, less likely to derive |
| KTO / IPO / ORPO | **P2** | Alternatives, mention if asked |
| SafeDPO | **P2** | Niche safety topic |

---

### Pillar 2: Synthetic Data

| Topic | Priority | Why |
|-------|----------|-----|
| **Rejection Sampling (RFT)** | **P0** | Core technique for quality filtering |
| **Distillation** | **P0** | How smaller models learn from larger |
| **Chain-of-thought formatting** | **P0** | Essential for reasoning traces (`<think>` tags) |
| Self-Instruct / Evol-Instruct | **P1** | Know the concepts |
| Decontamination | **P2** | Important but rarely deep-dived |

---

### Pillar 3: Infrastructure

| Topic | Priority | Why |
|-------|----------|-----|
| **LoRA math** (why low-rank works) | **P0** | Frequently asked, derive memory savings |
| **Flash Attention** (why O(N) memory) | **P0** | Common systems question |
| **PagedAttention** (vLLM) | **P0** | Memory fragmentation solution for agents |
| **ACE Framework** (Generator/Reflector/Curator) | **P0** | Self-improving context loops for agentic systems |
| Quantization basics (4-bit, 8-bit) | **P1** | Know tradeoffs |
| Gradient checkpointing | **P1** | Practical for training |
| S-LoRA / Multi-tenant | **P2** | Advanced serving topic |
| Speculative decoding | **P2** | Nice to mention |
| Model merging (TIES, DARE) | **P2** | Niche |

---

### Pillar 4: Evaluation

| Topic | Priority | Why |
|-------|----------|-----|
| **LLM-as-a-Judge** | **P0** | Standard eval method |
| **Reward hacking** | **P0** | Critical alignment concept |
| Standard benchmarks (GSM8K, MMLU) | **P1** | Know what they measure |
| Red-teaming basics | **P1** | Safety interviews |
| Refusal calibration | **P2** | Anthropic-specific |

---

### Pillar 5: Interview Skills

| Topic | Priority | Why |
|-------|----------|-----|
| **Implement attention from scratch** | **P0** | Coding round staple |
| **Top-K / Top-P sampling** | **P0** | Common implementation question |
| **Explain GRPO vs PPO tradeoffs** | **P0** | The 2026 differentiator question |
| Custom reward functions | **P1** | For reasoning model interviews |
| Debugging NaN losses | **P1** | Practical debugging |
| System design (distributed training) | **P2** | Senior roles only |

---

## 🧪 Hands-On Priorities

| Stage | Priority | Time | Rationale |
|-------|----------|------|-----------|
| **Stage 0: nanoGPT** | **P0** | 3-4 days | Builds core intuition, coding interview prep |
| **Stage 1: Cold-Start Data Curation** | **P0** | 4-5 days | Curate CoT reasoning data, not just run LoRA scripts |
| **Stage 3: Mini-GRPO** | **P0** | 3-4 days | 🔥 THE wow factor — reward `<think>` tags with Unsloth |
| Stage 2: DPO | P1 | 2-3 days | Style/safety alignment, less critical than GRPO |
| Stage 4: Tool Use | P2 | — | Skip for 2-3 week sprint |
| Stage 5: Eval | P1 | 2 days | At least build simple LLM-as-Judge |

---

## 📅 Recommended 2-3 Week Schedule

### Week 1: Foundations + Data Curation
| Day | Focus | Hands-On |
|-----|-------|----------|
| 1-2 | Attention, loss functions, sampling tradeoffs | Implement attention from scratch |
| 3-4 | Train nanoGPT | Stage 0 complete |
| 5-7 | Cold-Start SFT, CoT data formatting | Curate reasoning dataset with `<think>` tags |

### Week 2: GRPO + Core Concepts
| Day | Focus | Hands-On |
|-----|-------|----------|
| 1-2 | GRPO deep-dive: group averages, no Critic | Read DeepSeek-R1 paper |
| 3-4 | Mini-GRPO lab | Reward `<think>` tags with Unsloth |
| 5-6 | DPO derivation (why RM-free), Flash Attention | Practice explanations |
| 7 | LLM-as-Judge, reward hacking | — |

### Week 3 (if available): Polish + ACE
| Day | Focus | Hands-On |
|-----|-------|----------|
| 1-2 | ACE Framework (Generator/Reflector/Curator) | Design self-improving context loop |
| 3-4 | PagedAttention, LoRA memory math | Practice system design explanations |
| 5-7 | Mock interviews, weak areas | — |

---

## ⚡ P0 Checklist (Must Complete)

### Core Concepts
- [ ] Can implement multi-head attention from scratch
- [ ] Can derive DPO loss from RLHF objective (and explain why it's RM-free)
- [ ] Can explain LoRA memory savings mathematically
- [ ] Can explain Flash Attention's memory efficiency
- [ ] Can explain PagedAttention for agentic memory management
- [ ] Know RLHF pipeline: SFT → Reward Model → PPO

### 🔥 Reasoning Model Concepts (2026 Critical)
- [ ] Can explain GRPO: eliminates Critic (50% VRAM savings), uses group average for advantage
- [ ] Understand Cold-Start SFT: curating reasoning data that RL can score
- [ ] Know Temperature vs Top-P tradeoffs for reasoning (exploration vs verification)
- [ ] Can explain ACE Framework for self-improving context

### Hands-On
- [ ] Trained nanoGPT from scratch (Stage 0)
- [ ] Curated CoT dataset with `<think>` tags (Stage 1)
- [ ] Ran mini-GRPO rewarding reasoning traces (Stage 3)
- [ ] Can explain every line of a training loop

### Paper Deep-Dives
- [ ] DPO paper (derive the math, understand RM-free insight)
- [ ] DeepSeek-R1 paper (**deep dive** — GRPO is P0 now)
- [ ] LoRA paper (understand rank selection)
