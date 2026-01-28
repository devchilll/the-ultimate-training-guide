# Stage 3: RL for Reasoning with GRPO

> **Goal**: 🔥 THE 2026 differentiator — reproduce DeepSeek-R1 style reasoning.

## Why GRPO is P0 Now

GRPO (Group Relative Policy Optimization) is the definitive differentiator for "Reasoning Engines" in 2026:

| Advantage | Explanation |
|-----------|-------------|
| **No Critic model** | Eliminates 50% VRAM overhead vs PPO |
| **Group-relative advantage** | Uses batch average instead of learned value function |
| **Simpler training** | More stable than Actor-Critic architectures |
| **Powers DeepSeek-R1** | State-of-the-art reasoning capabilities |

## Labs in this directory

| File | Description |
|------|-------------|
| `grpo_reasoning.ipynb` | GRPO training with custom rewards |
| `reward_functions.py` | Format + correctness verification |
| `mini_grpo_think_tags.py` | **THE** portfolio piece: reward `<think>` tags |

## Getting Started

1. Prepare GSM8K data with `<think>...</think>` format
2. Design reward function:
   - +1 for correct `<think>` tag formatting
   - +1 for correct final answer (verified programmatically)
3. Train with GRPO using Unsloth

## Key Concepts to Master

### How GRPO Saves 50% VRAM
- PPO: Actor (policy) + Critic (value function) = 2 models
- GRPO: Actor only, uses **group average** of rewards for baseline
- Result: Half the memory, similar or better performance

### Custom Reward Function Design
```python
def reward_function(response: str, ground_truth: str) -> float:
    score = 0.0
    # Format reward: has <think> tags
    if "<think>" in response and "</think>" in response:
        score += 1.0
    # Correctness reward: answer matches
    if verify_answer(response, ground_truth):
        score += 1.0
    return score
```

## Success Criteria

- [ ] Model produces reasoning traces with `<think>` tags
- [ ] Accuracy improves on GSM8K test set
- [ ] Can explain GRPO's advantage over PPO (no Critic, 50% VRAM savings)
- [ ] Can explain group-relative advantage estimation
- [ ] **Can demo this in an interview as portfolio piece**

## Compute Requirements

💰 **Colab Pro+ / A100** — RL requires multiple forward passes per step  
🖥️ **Local RTX 3090/4090** — 24GB VRAM ideal for 7B models
