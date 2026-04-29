# CAROL  
**Chain-based Adaptive Reconfiguration Over Lattices for Hallucination Reduction**

<p align="center">
  <img src="figures/figure1.png" width="85%">
</p>

---

## 🔍 Overview

**CAROL** is a test-time framework for reducing hallucinations in Large Language Models (LLMs) by modeling generation as a structured process over a **lattice of semantic sequences**.

Instead of relying on token-level uncertainty, CAROL introduces a **semantic entropy** measure that captures how well generated responses align with a trusted context $\Gamma$. This enables principled **accept–reject decisions** during generation, improving reliability without modifying model weights.

---

## 🧠 Key Idea

CAROL treats generation as a **Markov chain over $\ell$-grams**, where each candidate sequence is evaluated based on its **semantic consistency** with a trusted reference set.

- **Dense semantic agreement → low entropy → accepted responses**
- **Sparse / inconsistent semantics → high entropy → rejected responses**

This provides a robust mechanism to detect hallucinations at the **semantic level**, rather than relying on token probabilities.

---

## ⚙️ Method

1. **Context Construction ($\Gamma$)**  
   Retrieve or define trusted semantic references (e.g., documents, facts).

2. **Generation (LLM)**  
   Produce candidate $\ell$-grams from the model.

3. **Semantic Clustering**  
   Group sequences using exemplar-based clustering (e.g., k-Medoids).

4. **Semantic Entropy Computation**  
   Measure agreement between generated sequences and $\Gamma$.

5. **Acceptance–Rejection Step**  
   Accept outputs with low entropy (high semantic consistency).

---

## 📊 Properties

- ✅ **Temperature-free** (no softmax sensitivity)
- ✅ **Interpretable** (clusters are real sequences, not centroids)
- ✅ **Stable** (robust across runs and sampling variations)
- ✅ **Plug-and-play** (no fine-tuning required)

---

## 📈 Example Insight

CAROL captures a key phenomenon:

> Dense semantic clusters indicate strong agreement and yield **low entropy**,  
> while sparse partitions reflect disagreement and result in **high entropy**,  
> signaling an increased likelihood of hallucination.

---

## 🧪 Experiments

The repository includes experiments showing:

- Robustness of **k-Medoids vs. soft k-Means**
- Effect of **temperature on clustering stability**
- Relationship between **semantic density and hallucination**
- PCA visualizations of semantic agreement

---

## 🚀 Getting Started

```bash
pip install sentence-transformers scikit-learn matplotlib numpy
