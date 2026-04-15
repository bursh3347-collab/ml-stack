# Best Practices: Fine-Tuning

> Extracted from HuggingFace Transformers, PyTorch, and production fine-tuning workflows

## Overview

Fine-tuning adapts pre-trained models to specific tasks or domains. With PEFT (Parameter-Efficient Fine-Tuning), it's now accessible to individual developers with limited GPU resources.

## Pattern 1: LoRA Fine-Tuning (from HuggingFace PEFT)

**Source**: HuggingFace Transformers (159k⭐, Apache-2.0) + PEFT library

**Why LoRA**: Train only 0.1-1% of parameters. A 7B model fine-tune fits on a single consumer GPU (24GB VRAM).

```python
from transformers import AutoModelForCausalLM, AutoTokenizer, TrainingArguments
from peft import LoraConfig, get_peft_model
from trl import SFTTrainer

# 1. Load base model
model = AutoModelForCausalLM.from_pretrained("meta-llama/Llama-3-8B")
tokenizer = AutoTokenizer.from_pretrained("meta-llama/Llama-3-8B")

# 2. Configure LoRA
lora_config = LoraConfig(
    r=16,              # Rank — higher = more capacity, more VRAM
    lora_alpha=32,     # Scaling factor
    target_modules=["q_proj", "v_proj"],  # Which layers to adapt
    lora_dropout=0.05,
    task_type="CAUSAL_LM"
)
model = get_peft_model(model, lora_config)

# 3. Train
trainer = SFTTrainer(
    model=model,
    train_dataset=dataset,
    args=TrainingArguments(
        output_dir="./output",
        per_device_train_batch_size=4,
        gradient_accumulation_steps=4,
        learning_rate=2e-4,
        num_train_epochs=3,
        fp16=True,
    )
)
trainer.train()

# 4. Save adapter (tiny file, ~50MB vs 15GB full model)
model.save_pretrained("./my-adapter")
```

## Pattern 2: QLoRA (4-bit Quantized LoRA)

**When to Use**: GPU VRAM < 24GB, or fine-tuning larger models (13B+)

**Key Addition**: Load base model in 4-bit quantization, then apply LoRA on top.

```python
from transformers import BitsAndBytesConfig

quant_config = BitsAndBytesConfig(
    load_in_4bit=True,
    bnb_4bit_quant_type="nf4",
    bnb_4bit_compute_dtype=torch.bfloat16
)
model = AutoModelForCausalLM.from_pretrained(
    "meta-llama/Llama-3-8B",
    quantization_config=quant_config
)
```

**VRAM Requirements**:
| Model Size | Full FT | LoRA | QLoRA |
|-----------|---------|------|-------|
| 7B | 60GB+ | 24GB | 12GB |
| 13B | 120GB+ | 48GB | 24GB |
| 70B | 600GB+ | 160GB | 48GB |

## Pattern 3: Dataset Preparation

**Chat Format** (recommended for instruction-tuning):
```json
{
  "messages": [
    {"role": "system", "content": "You are a helpful assistant."},
    {"role": "user", "content": "What is the return policy?"},
    {"role": "assistant", "content": "Our return policy allows..."}
  ]
}
```

**Data Quality Rules**:
1. **Quality > Quantity**: 1,000 high-quality examples > 100,000 noisy ones
2. **Diverse examples**: Cover edge cases and different phrasings
3. **Consistent format**: All examples should follow the same template
4. **No data leakage**: Ensure test set has no overlap with training data

## Pattern 4: Evaluation Pipeline

```
Base Model → Evaluate → Fine-Tune → Evaluate → Compare → Deploy
                ↑                        ↑
           Benchmark set            Same benchmark
```

**Key Metrics**:
- Task-specific accuracy (domain questions)
- Perplexity (language quality)
- Human evaluation (for production readiness)
- Regression testing (did fine-tuning break other capabilities?)

## When NOT to Fine-Tune

| Situation | Better Alternative |
|-----------|-------------------|
| Need current info | RAG (LlamaIndex) |
| Simple formatting | Prompt engineering |
| Few-shot learning works | In-context examples |
| <100 training examples | Few-shot or RAG |
| Budget < $50/month | Use larger API model |

## Anti-Patterns

1. **Fine-tuning for facts**: Use RAG instead — facts change, fine-tuning is expensive to update
2. **Over-training**: Watch for catastrophic forgetting — the model loses general capabilities
3. **No baseline**: Always measure the base model's performance first
4. **Skipping eval**: Fine-tuning without evaluation is flying blind
5. **Ignoring cost**: Cloud fine-tuning can cost $100+ per run — start with QLoRA locally
