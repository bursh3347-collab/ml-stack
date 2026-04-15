# Fine-Tuning Best Practices

> Patterns for efficient model customization, extracted from HF Transformers and PyTorch ecosystem.

*Sources: huggingface/transformers (159k⭐), pytorch/pytorch (99k⭐)*

## When to Fine-Tune vs. RAG vs. Prompt Engineering

| Approach | Best For | Cost | Time | Quality |
|----------|---------|------|------|---------|
| **Prompt Engineering** | Quick iteration, general tasks | Free | Minutes | Good |
| **RAG** | Domain knowledge, up-to-date info | Low | Hours | Very Good |
| **Fine-Tuning** | Specific behavior, style, format | Medium | Hours-Days | Excellent |
| **Pre-Training** | New language, specialized domain | Very High | Weeks | — |

**Rule of thumb**: Start with prompt engineering → Add RAG → Fine-tune only if needed.

## Fine-Tuning Methods

### 1. LoRA (Low-Rank Adaptation)
- Train only small adapter matrices (0.1-1% of parameters)
- Original weights frozen → no catastrophic forgetting
- Can swap adapters for different tasks
- **Recommended for most use cases**

### 2. QLoRA (Quantized LoRA)
- Load base model in 4-bit, train LoRA adapters in FP16
- Fits 70B model on single 48GB GPU
- Slight quality trade-off vs full LoRA
- **Best for resource-constrained setups**

### 3. Full Fine-Tuning
- Update all parameters
- Requires large GPU memory (8× model size)
- Risk of catastrophic forgetting
- **Only for large companies with dedicated compute**

## HF Transformers Fine-Tuning Recipe

```python
from transformers import AutoModelForCausalLM, AutoTokenizer, TrainingArguments
from peft import LoraConfig, get_peft_model
from trl import SFTTrainer

# 1. Load model + tokenizer
model = AutoModelForCausalLM.from_pretrained("meta-llama/Llama-3-8B")
tokenizer = AutoTokenizer.from_pretrained("meta-llama/Llama-3-8B")

# 2. Configure LoRA
lora_config = LoraConfig(
    r=16,              # Rank (8-64, higher = more params)
    lora_alpha=32,     # Scaling factor
    target_modules=["q_proj", "v_proj"],  # Which layers to adapt
    lora_dropout=0.05,
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
        num_train_epochs=3,
        learning_rate=2e-4,
        fp16=True,
    ),
)
trainer.train()
```

## Data Preparation Checklist

- [ ] Minimum 100 high-quality examples (ideally 1000+)
- [ ] Consistent format (instruction-response pairs)
- [ ] Deduplicated and cleaned
- [ ] Train/validation split (90/10)
- [ ] Balanced across categories
- [ ] No PII or sensitive data

## Common Mistakes

| Mistake | Impact | Solution |
|---------|--------|----------|
| Too little data | Overfitting | Get 1000+ examples |
| No validation set | Can't detect overfitting | Always hold out 10% |
| Too high learning rate | Catastrophic forgetting | Start with 2e-4 |
| Wrong LoRA rank | Under/overfitting | Start with r=16 |
| Training too long | Overfitting | Use early stopping |
| No base model eval | Can't measure improvement | Benchmark before and after |

## Cost Estimation

| Model Size | Method | GPU | Time | Cloud Cost |
|-----------|--------|-----|------|------------|
| 7B | LoRA | 1× A100 40GB | 2-4h | ~$8-16 |
| 7B | QLoRA | 1× T4 16GB | 4-8h | ~$4-8 |
| 70B | QLoRA | 1× A100 80GB | 8-24h | ~$32-96 |
| 70B | Full FT | 8× A100 80GB | 24-72h | ~$800-2400 |

**天子 Recommendation**: QLoRA on 7B models is the sweet spot for a one-person operation. Use Ollama for local testing, deploy fine-tuned model via vLLM.
