# Hands-On Labs: Post-Training Practical Roadmap

> Build technical intuition through progressive experiments—from training a tiny model to deploying a specialized agent.

---

## 📍 Stage 0: Pre-Training Fundamentals (Week 1)

*Focus: Understanding training dynamics from scratch.*

### Core Lab
Train a **character-level language model** from scratch using [nanoGPT](https://github.com/karpathy/nanoGPT) or minGPT.

### Dataset
- Shakespeare text (~1MB) or TinyStories for simpler patterns
- Tokenize at character level (no BPE complexity)

### Key Skills
- Implementing attention and feedforward layers in PyTorch
- Understanding loss curves: what does "good" training look like?
- Hyperparameter sensitivity: learning rate, batch size, context length

### Success Criteria
✅ Model generates coherent (if nonsensical) text after 1000 steps  
✅ You can explain every line of the training loop  
✅ Loss decreases smoothly without NaN/explosion  

### Compute Requirements
🖥️ **Colab Free Tier** — CPU/T4 sufficient for character-level models

---

## 📍 Stage 1: SFT Foundations (Weeks 2-3)

*Focus: Mastering the Supervised Fine-Tuning loop.*

### Core Lab
Fine-tune **Llama-3.2-1B** or **Qwen2.5-1.5B** using **Unsloth** for efficient training.

### Dataset
- `yahma/alpaca-cleaned` — standard instruction-following
- Or create your own: 500-1000 high-quality examples in a specific domain

### Key Skills
- Loading 4-bit quantized models with `bitsandbytes`
- LoRA configuration: rank, alpha, target modules
- Formatting chat templates correctly (system/user/assistant)
- Monitoring loss curves and identifying overfitting

### Success Criteria
✅ Fine-tuned model follows instructions in your target format  
✅ You can explain LoRA's memory savings mathematically  
✅ Loss plateaus appropriately (not memorizing, not underfitting)  

### Compute Requirements
🖥️ **Colab Free Tier (T4)** — 1B models fit comfortably with 4-bit quantization  
💰 **Colab Pro (A100)** — for 7B+ models or faster iteration

---

## 📍 Stage 2: Preference Alignment with DPO (Weeks 4-5)

*Focus: Learning from comparisons without explicit reward models.*

### Core Lab
Implement **Direct Preference Optimization (DPO)** to align a model with a specific persona or safety profile.

### Dataset
- Build preference triplets: `(prompt, chosen_response, rejected_response)`
- Sources: [Anthropic HH-RLHF](https://huggingface.co/datasets/Anthropic/hh-rlhf), or create 200+ pairs manually

### Key Skills
- Understanding the DPO loss derivation from RLHF
- Creating high-quality preference data
- Measuring "win-rate" vs. base model using LLM-as-Judge
- Implementing SafeDPO for jailbreak resistance

### Success Criteria
✅ Aligned model shows measurable style/behavior shift  
✅ Win-rate vs. base model >60% on held-out prompts  
✅ You can derive the DPO loss from scratch  

### Compute Requirements
🖥️ **Colab Pro (A100)** — DPO requires reference model inference  
💡 Use gradient checkpointing to fit on T4 with smaller models

---

## 📍 Stage 3: RL for Reasoning with GRPO (Weeks 6-8)

*Focus: Reproducing DeepSeek-R1 style reasoning.*

### Core Lab
Train a reasoning model on math/logic tasks using **Group Relative Policy Optimization (GRPO)** with Unsloth.

### Dataset
- **GSM8K**: Grade-school math with chain-of-thought
- **MATH**: Competition-level problems (harder)
- Format with `<think>...</think>` tags for reasoning traces

### Key Skills
- Designing custom reward functions (format + correctness verification)
- The "Cold Start" problem: bootstrapping RL with SFT on high-quality traces
- Understanding group-relative advantage estimation
- Debugging RL instabilities (reward hacking, mode collapse)

### Success Criteria
✅ Model produces reasoning traces with `<think>` tags  
✅ Accuracy improves on GSM8K test set  
✅ You can explain GRPO's advantage over PPO for this setting  

### Compute Requirements
💰 **Colab Pro+ / A100** — RL requires multiple forward passes per step  
🖥️ **Local RTX 3090/4090** — 24GB VRAM ideal for 7B models

---

## 📍 Stage 4: Tool Use & Function Calling (Weeks 9-10)

*Focus: Building a production-ready specialist agent.*

### Core Lab
Fine-tune a **Qwen2.5-7B** or **Llama-3.1-8B** for structured **function calling** and tool use.

### Dataset
- [Berkeley Function Calling Leaderboard (BFCL)](https://gorilla.cs.berkeley.edu/leaderboard.html) data
- Or create domain-specific tool schemas (weather, calendar, database)

### Key Skills
- Schema-aware fine-tuning for JSON function calls
- Achieving >90% accuracy on specific APIs
- Multi-LoRA serving: dynamically swap domain adapters on vLLM
- LLM-as-Judge evaluation for tool-use quality

### Success Criteria
✅ Model correctly calls functions with proper arguments  
✅ Outperforms base model on your domain's tool schemas  
✅ Deploy with vLLM and hot-swap between LoRA adapters  

### Compute Requirements
💰 **Colab Pro+ / A100** — 7B+ models need significant VRAM  
🖥️ **Local GPU** — vLLM serving benefits from dedicated hardware

---

## 📍 Stage 5: Evaluation & Red-Teaming (Weeks 11-12)

*Focus: Rigorous testing before claiming success.*

### Core Lab
Build a comprehensive **evaluation suite** for your fine-tuned models.

### Components
- **Automated benchmarks**: GSM8K, MMLU subset, HumanEval
- **LLM-as-Judge pipeline**: Rubric-based scoring with GPT-4/Claude
- **Red-teaming**: Test for jailbreaks, prompt injections, refusal calibration

### Key Skills
- Designing evaluation rubrics that correlate with human preference
- Statistical significance testing (is improvement real?)
- Identifying reward hacking and distributional shift

### Success Criteria
✅ Eval suite runs end-to-end with clear metrics  
✅ You can explain limitations of your metrics  
✅ Red-teaming reveals no critical safety failures  

### Compute Requirements
🖥️ **Colab Free Tier** — evaluation is mostly inference  
💰 **API costs** — if using GPT-4/Claude as judges

---

## 📁 Suggested Repository Structure

```
/labs
├── 00_pretraining_fundamentals/
│   ├── nanogpt_from_scratch.ipynb    # Train tiny LM
│   └── attention_implementation.py   # Hand-coded attention
├── 01_sft_foundations/
│   ├── unsloth_sft_tutorial.ipynb    # 4-bit LoRA fine-tuning
│   └── data_formatting.py            # Chat template utilities
├── 02_preference_alignment/
│   ├── dpo_training.ipynb            # DPO implementation
│   └── preference_data_creation.py   # Building triplet datasets
├── 03_reasoning_rl/
│   ├── grpo_reasoning.ipynb          # GRPO with custom rewards
│   └── reward_functions.py           # Format + correctness rewards
├── 04_tool_use/
│   ├── function_calling_sft.ipynb    # Schema-aware fine-tuning
│   └── vllm_multi_lora.py            # Multi-adapter serving
└── 05_evaluation/
    ├── eval_suite.py                 # Automated benchmarking
    └── llm_judge.py                  # Rubric-based evaluation

/infra
├── vllm_config.yaml                  # Serving configuration
├── quantization_guide.md             # AWQ/GPTQ/GGUF exports
└── colab_setup.md                    # Environment setup tips
```

---

## 🗓️ Timeline Summary

| Stage | Focus | Duration | Compute |
|-------|-------|----------|---------|
| 0 | Pre-training fundamentals | 1 week | Colab Free |
| 1 | SFT with LoRA | 2 weeks | Colab Free/Pro |
| 2 | DPO preference alignment | 2 weeks | Colab Pro |
| 3 | GRPO reasoning RL | 3 weeks | Colab Pro+ / Local |
| 4 | Tool use & function calling | 2 weeks | Colab Pro+ / Local |
| 5 | Evaluation & red-teaming | 2 weeks | Colab Free + API |

**Total: ~12 weeks** to build comprehensive hands-on experience.