# LLM Fine-Tuning Methods
| Type | Methods |
| --- | --- |
| Supervised Fine-Tuning (SFT) strategies | FFT, LoRA, QLoRA |
| Preference optimization | DPO, ORPO |
| RL algorithms | PPO, GRPO |
| Output-selection / data refinement | RFT |

### FFT — Full Fine-Tuning

A training method where all model parameters are updated during training. It provides the highest adaptation capability but requires very high GPU memory and compute resources.

---

### LoRA — Low-Rank Adaptation

A parameter-efficient fine-tuning (PEFT) method that freezes the original model weights and trains small low-rank matrices instead, greatly reducing training cost.

---

### QLoRA — Quantized Low-Rank Adaptation

An improved version of LoRA that uses low-bit (usually 4-bit) quantization to reduce VRAM usage, allowing large models to be fine-tuned on smaller GPUs.

---

### DPO — Direct Preference Optimization

A preference-learning method that directly trains on preferred vs rejected responses without needing a separate reward model or reinforcement learning loop.

---

### ORPO — Odds Ratio Preference Optimization

A simplified preference optimization method that combines supervised learning and preference alignment into a single objective using odds-ratio based optimization.

---

### PPO — Proximal Policy Optimization

A reinforcement learning optimization algorithm widely used in RLHF. It stabilizes policy updates and helps prevent destructive training steps during optimization.

---

### GRPO — Group Relative Policy Optimization

A modern RL optimization technique where multiple generated outputs are compared relatively within groups instead of using absolute reward scores. Popular in reasoning-focused LLM training.

---

### RFT — Rejection Fine-Tuning

A training method where multiple outputs are generated, low-quality responses are rejected, and the model is fine-tuned only on the best responses to improve reasoning and output quality.

Current SOTA Stack (2026):

```jsx
Continued Pretraining (optional)
        ↓
SFT (FFT / LoRA / QLoRA)
        ↓
Preference Alignment
   ├── DPO
   ├── ORPO
   └── RLHF (PPO/GRPO/etc.)
        ↓
Reasoning RL / RLVR
        ↓
Inference Optimization
```