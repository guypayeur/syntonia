# The Neuron Density Treasure Hunt 🔍✨

## Executive Summary

After analyzing **23 state-of-the-art language models**, we discovered fascinating architectural patterns that maximize neuron count relative to parameter budget. The champion is **ERNIE 4.5-21B-A3B** with an astounding **225 million neurons per billion parameters** - nearly **2.3× the average** across all models analyzed.

---

## 🏆 The Champions: Top 10 Neuron-Dense Models

| Rank | Model | Neurons/B | d_model | Layers | Experts | Total Params |
|------|-------|-----------|---------|--------|---------|--------------|
| 🥇 1 | **ERNIE 4.5-21B-A3B** | **225M** | 2048 | 48 | 128 | 21B |
| 🥈 2 | **Ling-mini-beta A0.8B** | **169M** | 2048 | 20 | 384 | 17.5B |
| 🥉 3 | **LFM2-8B-A1B** | **166M** | 2048 | 24 | 32 | 8.3B |
| 4 | Qwen3-30B-A3B | 157M | 2048 | 48 | 128 | 30B |
| 5 | Tongyi DeepResearch 30B | 157M | 2048 | 48 | 128 | 30B |
| 6 | Qwen3-Next-80B-A3B | 157M | 2048 | 48 | 512 | 80B |
| 7 | ERNIE 4.5-300B-A47B | 140M | 4096 | 80 | 256 | 300B |
| 8 | Ring-flash-linear-2.0 | 140M | 4096 | 32 | 256 | 60B |
| 9 | GPT-OSS-120B | 113M | 2880 | 36 | 128 | 117B |
| 10 | GPT-OSS-20B | 105M | 2880 | 24 | 32 | 21B |

---

## 🎯 The Three Pillars of Neuron Density

### 1. **Narrow Residual Stream (d_model ≤ 3000)**

**Why it works:** Smaller hidden dimensions minimize parameter overhead in attention mechanisms, embeddings, and layer norms. This frees up the parameter budget for MLP neurons.

**Top performers:**
- ERNIE 4.5-21B-A3B: d_model=2048 → 225M neurons/B
- Ling-mini-beta: d_model=2048 → 169M neurons/B  
- All Qwen3 30B variants: d_model=2048 → 157M neurons/B

**The pattern:** Models with d_model=2048 dominate the top 6 positions!

### 2. **Many Experts (E ≥ 256)**

**Why it works:** High expert counts create massive neuron pools. Even with sparse activation, the *total* neuron count (what we're measuring) scales with E × d_ffn,expert × L.

**Top performers:**
- Qwen3-Next-80B: 512 experts → 157M neurons/B
- Ling-mini-beta: 384 experts → 169M neurons/B
- ERNIE 4.5-300B: 256 experts → 140M neurons/B
- Ring-flash-linear-2.0: 256 experts → 140M neurons/B

**The sweet spot:** 256-512 experts with small expert size (512-2048 hidden units)

### 3. **Deep Architecture (L ≥ 60)**

**Why it works:** Neuron count scales linearly with depth. More layers = more neurons, without proportionally increasing parameters if combined with narrow residual streams.

**Top performers:**
- ERNIE 4.5-300B: 80 layers → 140M neurons/B
- Qwen3 VL 235B: 94 layers → 79M neurons/B
- GLM 4.6: 92 layers → 63M neurons/B

---

## 🔬 The Magic Formula

The highest neuron density comes from **combining all three patterns**:

```
High Neuron Density = Narrow d_model + Many Experts + Deep Layers
```

**ERNIE 4.5-21B-A3B** exemplifies this perfectly:
- d_model = 2048 (narrow ✓)
- E = 128 experts (many ✓)
- L = 48 layers (deep ✓)
- Result: **4.72 billion neurons** from just **21 billion parameters**

---

## 📊 Key Statistics

- **Total models analyzed:** 23
- **Average neuron density:** 96M neurons/B
- **Highest neuron density:** 225M neurons/B (ERNIE 4.5-21B-A3B)
- **Models with d_model ≤ 2500:** 6 (all in top 10!)
- **Models with E ≥ 256:** 8
- **Neuron density range:** 17M - 225M neurons/B (13× variation!)

---

## 🎨 Architectural Signatures

The ASCII art reveals visual patterns:

**Narrow-Deep-Many (Champion Pattern):**
```
╔════════════════════╗  ← Narrow (d_model=2048)
║████████████████████║  ← Many experts (E=512)
║████████████████████║
║████████████████████║  ← Deep (L=48+)
║████████████████████║
║████████████████████║
╚════════════════════╝
```

**Wide-Shallow-Few (Low Density):**
```
╔═══════════════════════════════════════╗  ← Wide (d_model=16384)
║█████████████████████████████████████████║
║█████████████████████████████████████████║  ← Shallow (L=126 but dense)
╚═══════════════════════════════════════╝
```

---

## 💡 How to Find More Neuron-Dense Models

### Search Strategy:

1. **Filter by d_model:**
   - Look for models with `hidden_size` or `d_model` ≤ 3000
   - Check config.json files on HuggingFace

2. **Check expert count:**
   - Look for `num_experts` or `n_routed_experts` ≥ 256
   - MoE models are your best bet

3. **Verify depth:**
   - Check `num_hidden_layers` ≥ 48
   - Deeper is better (if narrow!)

4. **Calculate the ratio:**
   ```python
   N_MLP = L × E × d_ffn_expert  # Total neurons (millions)
   P_total = total_parameters / 1e9  # Total params (billions)
   Neurons_per_B = N_MLP / P_total
   ```

5. **Look for these patterns:**
   - "A3B" or "A0.8B" in model names (indicates small active params)
   - Chinese models (Qwen, ERNIE, Tongyi, Hunyuan) - they love narrow-deep!
   - Recent MoE releases (2025+)

---

## 🌟 Surprising Discoveries

1. **ERNIE beats Tongyi!** Despite Tongyi being our original champion, ERNIE 4.5-21B-A3B has 43% higher neuron density (225M vs 157M).

2. **Ling-mini-beta is incredible:** Only 17.5B total parameters, but 169M neurons/B with 384 experts!

3. **The d_model=2048 sweet spot:** Six different models with d_model=2048 all achieve >150M neurons/B.

4. **Dense models can't compete:** The highest-ranking dense model (Qwen3 VL 8B) has only 55M neurons/B - less than 1/4 of ERNIE's density.

5. **More experts ≠ always better:** Ling-mini (384 experts) beats Qwen3-Next (512 experts) because of better overall architecture balance.

---

## 🚀 Next Steps

Want to explore further? Try:

1. **Chat with the champions** to see if neuron density affects reasoning style
2. **Benchmark performance** on tasks requiring broad knowledge (where more neurons might help)
3. **Analyze activation patterns** - do narrow-deep models activate differently?
4. **Search for extreme cases** - can we find d_model < 1500? E > 512?

---

*Analysis completed: October 20, 2025*  
*Models analyzed: 23 state-of-the-art LLMs*  
*Tools: Python, pandas, HuggingFace config files*

