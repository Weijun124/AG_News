# AG_News

PEFT with LoRA of RoBERTa model

# Parameter-Efficient Fine-Tuning of RoBERTa Using LoRA

This project explores the use of **Low-Rank Adaptation (LoRA)**, a parameter-efficient fine-tuning (PEFT) method, to adapt the pre-trained **RoBERTa-base** language model for text classification on the **AG News** dataset.

## 📌 Objective

Reduce training cost by fine-tuning **< 1%** of the model parameters while maintaining high classification accuracy across 4 news categories:

- World
- Sports
- Business
- Science/Technology

---

## 🧪 Experiments

We tested:

- Different **LoRA ranks**: `3`, `4`, `6`
- Various **target modules**: `query`, `key`, `value`, and their combinations
- With and without LoRA **bias**
- Several **scaling factors** (alpha): `4`, `6`, `12`, `18`, `24`

### 🔍 Key Findings:

- Using `[query, key, value]` with **alpha = 18** gave the highest accuracy (`0.939`)
- Using only the `value` module achieved comparable results with fewer trainable parameters
- Lower ranks worked better for single modules; higher ranks performed better for multi-module configurations

---

## ⚙️ Setup & Training

- **Model**: RoBERTa-base (from Hugging Face)
- **PEFT Method**: LoRA (via `peft` library)
- **Optimizer**: `adamw_bnb_8bit`
- **Training epochs**: 3
- **Batch size**: 64
- **Evaluation strategy**: per epoch
