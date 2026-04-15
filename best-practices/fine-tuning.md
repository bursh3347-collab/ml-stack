# Fine-Tuning Best Practices

> Patterns extracted from HuggingFace, PyTorch, and production fine-tuning workflows.

## When to Fine-Tune vs. RAG vs. Prompt Engineering

```
Prompt Engineering (cheapest, fastest)
├── Works? → Done ✅
└── Not enough? ↓

RAG (moderate cost)
├── Works? → Done ✅
└── Not enough? ↓

Fine-Tuning (most expensive, most powerful)
└── Last resort, but sometimes necessary
```

**Fine-tune when**:
- You need consistent output format/style
- Domain-specific knowledge that RAG can't handle
- Latency requirements (can't afford retrieval step)
- Cost optimization (smaller fine-tuned model replaces larger general model)

## Pattern 1: LoRA Fine-Tuning (Parameter Efficient)

```python
from peft import LoraConfig, get_peft_model

config = LoraConfig(
    r=16,               # Rank (lower = fewer params, less capacity)
    lora_alpha=32,       # Scaling factor
    target_modules=["q_proj", "v_proj"],  # Which layers to adapt
    lora_dropout=0.1,
    task_type="CAUSAL_LM",
)

model = get_peft_model(base_model, config)
# Only 0.1-1% of parameters are trainable!
```

**LoRA vs Full Fine-Tuning**:
| | LoRA | Full Fine-Tuning |
|---|------|------------------|
| GPU Memory | 1 GPU (16GB) | 4-8 GPUs |
| Training Time | Hours | Days |
| Quality | 90-95% of full | 100% |
| Cost | $10-100 | $1,000-10,000 |
| **Verdict** | 🏆 Default choice | Only if LoRA insufficient |

## Pattern 2: Data Preparation

```json
// Instruction-following format (most common)
{
  "instruction": "Summarize this article",
  "input": "The article text...",
  "output": "The summary..."
}

// Chat format (for chat models)
{
  "messages": [
    {"role": "system", "content": "You are a helpful assistant."},
    {"role": "user", "content": "Question"},
    {"role": "assistant", "content": "Answer"}
  ]
}
```

**Data quality rules**:
- 100-1000 high-quality examples > 10,000 noisy examples
- Diverse examples covering edge cases
- Consistent format across all examples
- Review examples manually before training

## Pattern 3: Training Configuration

```python
training_args = {
    'num_train_epochs': 3,          # 2-5 epochs usually sufficient
    'per_device_train_batch_size': 4,
    'gradient_accumulation_steps': 4, # Effective batch = 16
    'learning_rate': 2e-4,           # Lower for larger models
    'warmup_ratio': 0.1,             # 10% warmup
    'lr_scheduler_type': 'cosine',
    'fp16': True,                    # Mixed precision
    'logging_steps': 10,
    'eval_strategy': 'steps',
    'eval_steps': 50,
    'save_strategy': 'steps',
    'save_steps': 100,
}
```

## Pattern 4: Evaluation

1. **Hold-out test set** (10-20% of data, never seen during training)
2. **Task-specific metrics** (BLEU, ROUGE, F1, exact match)
3. **Human evaluation** (essential for quality assessment)
4. **A/B testing** (compare fine-tuned vs base model on real traffic)

## Anti-Patterns

1. **Fine-tuning without trying RAG first** — RAG is cheaper and often sufficient
2. **Too few examples** — Minimum 50-100 high-quality examples
3. **No evaluation set** — Can't measure improvement without held-out data
4. **Overfitting** — Watch training loss diverge from eval loss
5. **Ignoring base model quality** — Start with the best base model you can afford
