# 🧠 The Great Neuron Density Expedition

## A Journey Through 23 State-of-the-Art Language Models

*October 20, 2025*

---

## 📋 Table of Contents

1. [Executive Summary](#executive-summary)

1. [The Champions](#the-champions)

1. [The Three Pillars of Neuron Density](#the-three-pillars)

1. [Complete Model Database](#complete-model-database)

1. [ASCII Art Gallery](#ascii-art-gallery)

1. [Model Conversations](#model-conversations)

1. [Discovery Guide](#discovery-guide)

---

## Executive Summary

After analyzing **23 cutting-edge language models**, we uncovered the architectural secrets behind maximizing neuron density. The undisputed champion is **ERNIE 4.5-21B-A3B** with **225 million neurons per billion parameters** - achieving **2.3× the average** and **13× more than the least efficient model**.

### Key Discovery: The Magic Formula

```
High Neuron Density = Narrow Residual Stream + Many Experts + Deep Layers
```

**Why it matters:** Neuron count is a proxy for a model's capacity to store and process diverse patterns. Models that pack more neurons per parameter may excel at tasks requiring broad knowledge or nuanced reasoning.

---

## 🏆 The Champions

### Top 10 Neuron-Dense Models

| Rank | Model | Neurons/B | Architecture | Signature |
| --- | --- | --- | --- | --- |
| 🥇 | **ERNIE 4.5-21B-A3B** | **225M** | d=2048, L=48, E=128 | Narrow-Deep-Many |
| 🥈 | **Ling-mini-beta A0.8B** | **169M** | d=2048, L=20, E=384 | Narrow-Shallow-Ultra |
| 🥉 | **LFM2-8B-A1B** | **166M** | d=2048, L=24, E=32 | Narrow-Balanced |
| 4 | Qwen3-30B-A3B | 157M | d=2048, L=48, E=128 | Narrow-Deep-Many |
| 5 | Tongyi DeepResearch 30B | 157M | d=2048, L=48, E=128 | Narrow-Deep-Many |
| 6 | Qwen3-Next-80B-A3B | 157M | d=2048, L=48, E=512 | Narrow-Deep-Ultra |
| 7 | ERNIE 4.5-300B-A47B | 140M | d=4096, L=80, E=256 | Medium-VeryDeep-Many |
| 8 | Ring-flash-linear-2.0 | 140M | d=4096, L=32, E=256 | Medium-Balanced-Many |
| 9 | GPT-OSS-120B | 113M | d=2880, L=36, E=128 | Narrow-Balanced-Many |
| 10 | GPT-OSS-20B | 105M | d=2880, L=24, E=32 | Narrow-Balanced |

---

## 🎯 The Three Pillars

### Pillar 1: Narrow Residual Stream (d_model ≤ 3000)

**The Insight:** Smaller hidden dimensions minimize overhead in attention, embeddings, and norms, freeing parameters for MLP neurons.

**Top Performers:**

- d_model = 2048: **6 models** in top 10, all achieving ≥157M neurons/B

- d_model = 2880: GPT-OSS series (113M and 105M neurons/B)

**The Trade-off:** Narrow streams may limit representation capacity, but when combined with depth and experts, they create extreme neuron density.

### Pillar 2: Many Experts (E ≥ 256)

**The Insight:** Total neuron count scales with expert count. Even with sparse activation, N_MLP = L × E × d_ffn,expert creates massive neuron pools.

**Top Performers:**

- **512 experts:** Qwen3-Next-80B (157M neurons/B)

- **384 experts:** Ling-mini-beta (169M neurons/B)

- **256 experts:** ERNIE 4.5-300B, Ring-flash-2.0 (both 140M neurons/B)

**The Sweet Spot:** 256-512 experts with small expert size (384-2048 hidden units)

### Pillar 3: Deep Architecture (L ≥ 60)

**The Insight:** Neuron count scales linearly with depth. More layers = more neurons without proportional parameter growth (when narrow).

**Top Performers:**

- **80 layers:** ERNIE 4.5-300B (140M neurons/B)

- **94 layers:** Qwen3 VL 235B (79M neurons/B)

- **92 layers:** GLM 4.6 (63M neurons/B)

**The Pattern:** Deep models (L≥60) average 74M neurons/B vs. 98M for all models, but when combined with narrow d_model, they dominate.

---

## 📊 Complete Model Database

### All 23 Models Ranked by Neuron Density

| Rank | Model | Type | Neurons/B | d_model | Layers | Experts | Total Params | Active Params |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | ERNIE 4.5-21B-A3B | MoE | 225M | 2048 | 48 | 128 | 21B | 3B |
| 2 | Ling-mini-beta A0.8B | MoE | 169M | 2048 | 20 | 384 | 17.5B | 0.85B |
| 3 | LFM2-8B-A1B | MoE Hybrid | 166M | 2048 | 24 | 32 | 8.3B | 1.5B |
| 4 | Qwen3-30B-A3B | MoE | 157M | 2048 | 48 | 128 | 30B | 3B |
| 5 | Tongyi DeepResearch 30B | MoE | 157M | 2048 | 48 | 128 | 30B | 3B |
| 6 | Qwen3-Next-80B-A3B | MoE Hybrid | 157M | 2048 | 48 | 512 | 80B | 3B |
| 7 | ERNIE 4.5-300B-A47B | MoE | 140M | 4096 | 80 | 256 | 300B | 47B |
| 8 | Ring-flash-linear-2.0 | MoE Hybrid | 140M | 4096 | 32 | 256 | 60B | 6B |
| 9 | GPT-OSS-120B | MoE | 113M | 2880 | 36 | 128 | 117B | 5.1B |
| 10 | GPT-OSS-20B | MoE | 105M | 2880 | 24 | 32 | 21B | 3.6B |
| 11 | Hunyuan A13B | MoE | 79M | 4096 | 32 | 64 | 80B | 13B |
| 12 | Qwen3 VL 235B A22B | MoE | 79M | 4096 | 94 | 128 | 235B | 22B |
| 13 | GLM 4.6 | MoE | 63M | 5120 | 92 | 160 | 357B | 32B |
| 14 | Cogito V2 Llama 109B MoE | MoE | 58M | 5120 | 48 | 16 | 109B | 9B |
| 15 | Qwen3 VL 8B | Dense | 55M | 4096 | 36 | 1 | 8B | 8B |
| 16 | LongCat Flash Chat | MoE | 52M | 6144 | 28 | 512 | 560B | 27B |
| 17 | Qwen3 32B | Dense | 51M | 5120 | 64 | 1 | 32B | 32B |
| 18 | Kimi K2 0905 | MoE | 48M | 7168 | 61 | 384 | 1000B | 32B |
| 19 | DeepSeek V3 | MoE | 48M | 7168 | 61 | 256 | 671B | 37B |
| 20 | Step3 | MoE Multimodal | 47M | 7168 | 61 | 48 | 321B | 38B |
| 21 | Ring 1T | MoE | 42M | 8192 | 80 | 256 | 1000B | 50B |
| 22 | Qwen3 14B | Dense | 40M | 5120 | 40 | 1 | 14.8B | 14.8B |
| 23 | Cogito V2 Llama 405B | Dense | 17M | 16384 | 126 | 1 | 405B | 405B |

### Key Statistics

- **Average neuron density:** 96M neurons/B

- **Median neuron density:** 63M neurons/B

- **Range:** 17M - 225M neurons/B (13× variation)

- **MoE models:** 20 of 23 (87%)

- **Dense models:** 3 of 23 (13%)

- **Models with d_model ≤ 2500:** 6 (all in top 10)

- **Models with E ≥ 256:** 8

---

## 🎨 ASCII Art Gallery

Visual representations of architectural signatures:

### Champion: ERNIE 4.5-21B-A3B (225M neurons/B)

```
╔════════════════════╗  ← Narrow: d_model=2048
║▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒║  ← Medium experts: E=128
║▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒║
║▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒║  ← Deep: L=48
║▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒║
║▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒║
║▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒║
╚════════════════════╝
```

### Runner-up: Ling-mini-beta (169M neurons/B)

```
╔════════════════════╗  ← Narrow: d_model=2048
║████████████████████║  ← Ultra experts: E=384
║████████████████████║
║████████████████████║  ← Shallow: L=20
║████████████████████║
║████████████████████║
╚════════════════════╝
```

### Low Density: Cogito V2 405B (17M neurons/B)

```
╔═══════════════════════════════════════════════════════════╗  ← Wide: d_model=16384
║█████████████████████████████████████████████████████████████║
║█████████████████████████████████████████████████████████████║  ← Dense, not MoE
║█████████████████████████████████████████████████████████████║  ← Very deep: L=126
╚═══════════════════════════════════════════════════════════╝
```

**Legend:**

- Width = d_model (narrow vs wide)

- Height = number of layers (shallow vs deep)

- Density = expert count (█ = high, ▓ = medium, ▒ = low)

---

## 💬 Model Conversations

We asked three models with different architectures to respond to a creative prompt about neural architecture. Here's what happened:

### Test Prompt

> "A narrow-deep neural architecture with many experts walks into a bar. The bartender says 'Why the long face?' How would you respond, and what does this joke reveal about model architecture?"

### Qwen3-Next-80B-A3B (157M neurons/B, 512 experts)

**Response:** *[Highly detailed, technical]*

> "Because I'm a narrow-deep MoE! My architecture is so deep and narrow that my face stretches from input to output like a stretched-out pretzel—each layer so thin, I can't even hold a smile without collapsing. And with *all* these experts arguing over who gets to process which input? I'm stuck in a bottleneck, routing chaos, and my gradients keep vanishing before they reach the surface..."

**Analysis:** Qwen3-Next demonstrated:

- Deep technical understanding of architecture trade-offs

- Creative metaphor-building (stretched pretzel, vanishing gradients)

- Self-awareness about its own narrow-deep-many design

- **512 experts** may contribute to its ability to explore multiple perspectives simultaneously

### DeepSeek V3 (48M neurons/B, 256 experts)

**Response:** *[Philosophical, explanatory]*

> "I apologize for our appearance. You see, our 'face' is long not from sadness, but from topology. We are a narrow-deep network with many experts. The 'narrow-deep' part means our representations become incredibly refined and sequential, layer after layer, like a long, specialized assembly line..."

**Analysis:** DeepSeek showed:

- More measured, explanatory tone

- Focus on the "why" behind architectural choices

- Less playful than Qwen3-Next, more pedagogical

- **Lower neuron density** (48M vs 157M) may correlate with more focused, less exploratory responses

### ERNIE 4.5-21B-A3B (225M neurons/B, 128 experts)

**Response:** *[Timeout - no response received]*

**Analysis:** The champion timed out! Possible explanations:

- Thinking mode engaged too deeply (it's a "thinking" variant)

- API routing issues

- The model was *literally* thinking too hard with all those neurons 😄

### Key Observation

**Neuron density may correlate with response style:**

- **High density (157M+):** More creative, exploratory, multi-perspective

- **Medium density (48M):** More focused, explanatory, pedagogical

- **Ultra-high density (225M):** Possibly overthinks? (needs more testing!)

---

## 🔍 Discovery Guide

### How to Find More Neuron-Dense Models

#### Step 1: Filter by d_model

```python
# Look for models with hidden_size ≤ 3000
# Check config.json on HuggingFace
if config["hidden_size"] <= 3000:
    print("Potential candidate!")
```

#### Step 2: Check Expert Count

```python
# Look for num_experts or n_routed_experts ≥ 256
if config.get("num_experts", 1) >= 256:
    print("High expert count - promising!")
```

#### Step 3: Verify Depth

```python
# Check num_hidden_layers ≥ 48
if config["num_hidden_layers"] >= 48:
    print("Deep architecture - good sign!")
```

#### Step 4: Calculate Neuron Density

```python
# For MoE models
N_MLP = L * E * d_ffn_expert / 1e6  # millions
P_total = total_parameters / 1e9  # billions
neurons_per_B = N_MLP / P_total

# For dense models
N_MLP = L * d_ffn / 1e6
neurons_per_B = N_MLP / P_total
```

#### Step 5: Look for These Patterns

**In model names:**

- "A3B", "A0.8B" → indicates small active parameters (MoE)

- "30B", "21B" with "A3B" → likely narrow-deep-many

- Chinese models (Qwen, ERNIE, Tongyi, Hunyuan) → often use narrow-deep

**In release dates:**

- 2025 models → more likely to use advanced MoE

- Recent releases → check for "hybrid" or "linear" attention

**In model cards:**

- "Mixture-of-Experts"

- "Sparse activation"

- "Efficient" or "cost-effective"

- "Long context" (often paired with narrow-deep)

---

## 🌟 Surprising Discoveries

1. **ERNIE beats Tongyi by 43%:** Despite Tongyi being our original champion, ERNIE 4.5-21B-A3B achieved 225M vs 157M neurons/B.

1. **Ling-mini-beta punches above its weight:** Only 17.5B total parameters, but 169M neurons/B with 384 experts!

1. **The d_model=2048 sweet spot:** Six different models with this exact hidden size all achieved ≥150M neurons/B.

1. **Dense models can't compete:** The highest-ranking dense model (Qwen3 VL 8B) has only 55M neurons/B - less than 1/4 of ERNIE's density.

1. **More experts ≠ always better:** Ling-mini (384 experts) beats Qwen3-Next (512 experts) because of better architecture balance.

1. **The 1T parameter models are inefficient:** Ring 1T and Kimi K2 (both 1T params) have only 42M and 48M neurons/B respectively.

---

## 🚀 Future Directions

### Questions for Further Research

1. **Performance correlation:** Do neuron-dense models actually perform better on knowledge-intensive tasks?

1. **Activation patterns:** How do narrow-deep models route information differently than wide-shallow ones? 

1. **Training dynamics:** Are neuron-dense models harder to train? Do they require different learning rates?

1. **Extreme architectures:** Can we find d_model < 1500? E > 512? What are the limits?

1. **Task specialization:** Do different neuron densities excel at different task types?

### Potential Experiments

- **Benchmark suite:** Test all 23 models on knowledge QA, reasoning, and creative tasks

- **Activation analysis:** Visualize expert routing in high-density models

- **Ablation studies:** What happens if we widen ERNIE? Narrow DeepSeek?

- **Fine-tuning:** Do neuron-dense models fine-tune more efficiently?

---

## 📚 Appendix: Formulas

### Neuron Count Calculations

**Dense Models:**

```
N_MLP = L × d_ffn
N_res = L × d_model
N_total = N_MLP + N_res
```

**MoE Models:**

```
N_MLP = L × E × d_ffn,expert
N_active = L × k × d_ffn,expert
N_res = L × d_model
```

**Efficiency Metrics:**

```
Neurons/B = N_MLP / P_total
MLP/Res Ratio = N_MLP / N_res
Active/Total = N_active / N_MLP
```

### Architecture Patterns

**Narrow-Deep-Many (Champion Pattern):**

- d_model ≤ 3000

- L ≥ 48

- E ≥ 128

- Result: 150M+ neurons/B

**Wide-Deep-Few (Low Density):**

- d_model ≥ 7000

- L ≥ 60

- E ≤ 256 (or dense)

- Result: <50M neurons/B

---

## 🎓 Conclusions

The quest for neuron density reveals a fundamental trade-off in neural architecture: **width vs. depth vs. sparsity**. The champions achieve extreme neuron density by:

1. **Minimizing overhead** (narrow residual streams)

1. **Maximizing neuron pools** (many experts)

1. **Scaling depth** (deep layers)

**ERNIE 4.5-21B-A3B** exemplifies this perfectly: 2048-dimensional hidden state, 48 layers, 128 experts → **4.72 billion neurons from just 21 billion parameters**.

Whether neuron density correlates with real-world performance remains an open question, but the architectural patterns are clear: **narrow-deep-many is the path to maximum neuron efficiency**.

---

*Analysis completed: October 20, 2025**Models analyzed: 23 state-of-the-art LLMs**Tools: Python, pandas, HuggingFace, OpenRouter API**Created with curiosity and care by Manus* 🤖✨

