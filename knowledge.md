# Post-Training & Alignment: Knowledge Guide

> A comprehensive reference for LLM post-training roles at Tier-0 labs (DeepMind, Anthropic, OpenAI).

---

## 🧱 Pillar 0: Foundations

*Focus: Core building blocks every candidate must understand deeply.*

### Transformer Architecture
- **Self-Attention**: Query-Key-Value mechanics, softmax normalization, multi-head attention
- **Positional Encodings**: Sinusoidal vs. learned vs. RoPE (Rotary Position Embeddings)
- **Layer Normalization**: Pre-norm vs. post-norm architectures

### Training Fundamentals
- **Loss Functions**: Cross-entropy, KL divergence, policy gradient objectives
- **Optimization**: AdamW, learning rate schedules, gradient clipping
- **Tokenization**: BPE, SentencePiece, vocabulary construction tradeoffs

### Key Interview Topics
- Implement attention from scratch (NumPy or PyTorch)
- Explain why we use softmax temperature in sampling
- Derive the gradient of cross-entropy loss

→ *Hands-on: See Stage 0 in [handson.md](./handson.md#stage-0)*

---

## 🏗️ Pillar 1: Alignment Methodologies

*Focus: Algorithms that modify model behavior and reasoning.*

### SFT (Supervised Fine-Tuning) 2.0
- **Cold-Start Bootstrapping**: The critical first phase — curating reasoning traces that RL can score
  - Quality of reasoning data directly determines RL success
  - Focus on long-form Chain-of-Thought (CoT) with `<think>...</think>` formatting
- **Instruction Backtranslation**: Reverse-engineering instructions from raw web documents
- **Chat Templates**: Proper formatting with system/user/assistant roles

### Preference Optimization
- **DPO (Direct Preference Optimization)**: Policy optimization without explicit reward models
  - Key insight: Reparameterizes RLHF objective — **RM-free** (no separate reward model needed)
  - Derives optimal policy directly from preference pairs
- **SafeDPO**: Integrating safety constraints into the loss function
- **IPO / KTO**: Alternatives that address DPO's distribution shift issues
- **ORPO**: Odds-ratio preference optimization (no reference model needed)

### Reinforcement Learning for Reasoning
- **GRPO (Group Relative Policy Optimization)**: 🔥 The 2026 differentiator
  - Eliminates the Critic model → **50% VRAM savings** vs PPO
  - Uses **group average** for advantage estimation instead of learned value function
  - Powers DeepSeek-R1's multi-step reasoning capabilities
- **PPO (Proximal Policy Optimization)**: Actor-Critic with clipped surrogate objective
- **REINFORCE with baseline**: Simpler alternative for reward-based learning
- **Reward Models**: Training verifiers for outcome and process supervision

### Safety & Constitutional AI
- **RLHF vs RLAIF**: Human feedback vs. AI-generated feedback for alignment
- **Constitutional AI**: Self-critique + revision with principle-based feedback
- **Red-teaming integration**: Iterative safety training from adversarial prompts

### Key Interview Topics
- Derive the DPO loss from the RLHF objective (explain why RM-free)
- **Explain GRPO**: How does eliminating the Critic save 50% VRAM? What's group-relative advantage?
- When to use DPO vs. PPO vs. GRPO?
- Compare RLHF vs RLAIF: tradeoffs and use cases
- How do process reward models differ from outcome reward models?

→ *Hands-on: See Stages 1-3 in [handson.md](./handson.md#stage-1)*

---

## 🧪 Pillar 2: Synthetic Data & Data Flywheels

*Focus: Building self-improving systems to overcome data scarcity.*

### Generation Techniques
- **Self-Instruct / Evol-Instruct**: Using teacher models to evolve instruction complexity
- **Chain-of-Thought Curation**: Formatting `<think>...</think>` tags for reasoning models
- **Persona-based generation**: Creating diverse synthetic personas for coverage

### Filtering & Verification
- **Rejection Sampling (RFT)**: Generate N candidates, keep only verifiably correct answers
- **Distillation**: Transfer reasoning traces from large models (GPT-4/Claude) to smaller models
- **Decontamination**: Ensuring training data doesn't overlap with benchmarks

### Key Interview Topics
- Design a data flywheel for improving math reasoning
- How do you verify synthetic data quality at scale?
- Tradeoffs between distillation and RL-based reasoning

→ *Hands-on: See Stage 1 data curation in [handson.md](./handson.md#stage-1)*

---

## 🛠️ Pillar 3: Infrastructure & Tooling

*Focus: Efficiently training and serving specialization-heavy models.*

### Fine-Tuning Frameworks
- **Unsloth**: 2x faster LoRA/QLoRA with 70% VRAM savings
- **Axolotl**: YAML-driven training pipelines with extensive config options
- **LLaMA-Factory**: Web UI and CLI for production fine-tuning
- **TRL**: HuggingFace library for SFT, DPO, PPO, GRPO

### Parameter-Efficient Fine-Tuning (PEFT)
- **LoRA / QLoRA**: Low-rank adaptation of attention matrices
- **DoRA**: Weight-decomposed low-rank adaptation
- **Adapter layers**: Bottleneck modules between transformer layers
- **Model Merging**: TIES, DARE, SLERP for combining multiple adapters

### Training Optimizations
- **Flash Attention**: Memory-efficient attention (O(N) instead of O(N²))
- **Gradient Checkpointing**: Trade compute for memory during backprop
- **Mixed Precision (BF16/FP16)**: Faster training with lower memory
- **DeepSpeed / FSDP**: Distributed training across multiple GPUs

### Inference & Serving
- **vLLM & PagedAttention**: Dynamic KV cache management for long contexts
- **S-LoRA (Multi-Tenant)**: Serve thousands of private LoRA adapters per customer
  - Key insight: Unified paging for adapter weights + isolation between tenants
- **Speculative Decoding**: Use small draft model to speed up large model inference
- **Quantization**: AWQ, GPTQ, GGUF for efficient deployment
- **Continuous Batching**: Maximize GPU utilization with dynamic batching

### Agentic Context Engineering (ACE)
- **The survival path**: Static prompt engineering is a "depreciating asset"
- **Generator**: Surfaces reasoning trajectories and strategies
- **Reflector**: Extracts concrete "lessons" from successes and failures  
- **Curator**: Applies incremental "delta updates" to the context playbook
- **Key insight**: Design systems where context evolves as a self-improving "playbook"

### Key Interview Topics
- Explain how LoRA reduces memory requirements
- How does PagedAttention improve throughput?
- Design a multi-tenant system serving 1000 private LoRA adapters
- Explain the tradeoffs of speculative decoding
- How does Flash Attention achieve O(N) memory?
- **Design an ACE loop**: How would you build a self-improving context system?

→ *Hands-on: See infra setup in [handson.md](./handson.md#stage-4)*

---

## ⚖️ Pillar 4: Evaluation & Benchmarking

*Focus: Quantifying model performance rigorously.*

### Evaluation Frameworks
- **LLM-as-a-Judge**: Automated scoring with rubric-based critiques
- **BFCL (Berkeley Function Calling)**: Tool-use and schema compliance benchmarks
- **MMLU / GSM8K / HumanEval**: Standard capability benchmarks

### Safety & Alignment Evaluation
- **Red-teaming**: Adversarial testing for jailbreaks and harmful outputs
- **Refusal rate analysis**: Measuring over/under-refusal on sensitive topics
- **Reward hacking detection**: Identifying when models game the reward

### Observability
- **Ragas & DeepEval**: Metrics for RAG systems (retrieval relevancy, faithfulness)
- **Training curves**: Loss, gradient norms, activation statistics

### Key Interview Topics
- Design an evaluation suite for a customer service agent
- How do you detect reward hacking?
- Limitations of LLM-as-a-Judge

→ *Hands-on: See evaluation lab in [handson.md](./handson.md#stage-5)*

---

## 💼 Pillar 5: Interview Preparation

*Focus: Navigating Tier-0 lab recruitment (DeepMind, Anthropic, OpenAI).*

### ML System Design
- Designing million-token context training systems
- Optimizing for agentic feedback loops and "aha moment" reasoning
- Distributed training: FSDP, DeepSpeed, pipeline parallelism

### Coding & Algorithms
- Hand-write: Attention mechanism, Top-K sampling, beam search
- Implement: Custom reward functions (regex matching, code execution)
- Debug: Gradient issues, training instabilities, NaN losses

### Portfolio Strategy
- Move from "Wrappers" → "Reasoning Engines" in your projects
- Demonstrate data curation expertise, not just prompt engineering
- Open-source contributions to training frameworks (Unsloth, Axolotl, vLLM)

### Recommended Study Plan
1. **Weeks 1-2**: Foundations + Stage 0 hands-on
2. **Weeks 3-4**: SFT deep-dive + Stage 1 hands-on
3. **Weeks 5-6**: DPO/GRPO + Stages 2-3 hands-on
4. **Weeks 7-8**: Eval + Tool-use + Stage 4 hands-on
5. **Weeks 9+**: Mock interviews + portfolio projects
