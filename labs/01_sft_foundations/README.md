# Stage 1: SFT Foundations — Cold-Start Data Curation

> **Goal**: Master data curation for reasoning models, not just run LoRA scripts.

## The Key Insight

🔥 **Cold-Start SFT is the bottleneck**: The quality of reasoning data you curate directly determines how well RL (GRPO) will work. Focus on *data curation* over the training mechanics.

## Labs in this directory

| File | Description |
|------|-------------|
| `unsloth_sft_tutorial.ipynb` | 4-bit LoRA fine-tuning with Unsloth |
| `data_formatting.py` | Chat template utilities |
| `cot_data_curation.py` | **NEW**: Chain-of-thought formatting with `<think>` tags |

## Getting Started

1. Install [Unsloth](https://github.com/unslothai/unsloth)
2. **Focus on data**: Curate 500-1000 examples with long-form reasoning traces
3. Format with `<think>...</think>` tags for reasoning steps
4. Fine-tune Llama-3.2-1B on your curated dataset

## Data Curation Checklist

- [ ] Each example has detailed step-by-step reasoning
- [ ] Reasoning is wrapped in `<think>...</think>` tags
- [ ] Final answers are clearly separated from reasoning
- [ ] Examples cover diverse problem types
- [ ] Quality over quantity — 500 great examples > 5000 mediocre ones

## Success Criteria

- [ ] Created a curated CoT dataset with proper `<think>` formatting
- [ ] Fine-tuned model produces reasoning traces in your format
- [ ] Can explain LoRA's memory savings mathematically
- [ ] Understand why data quality determines RL success (Cold-Start principle)
