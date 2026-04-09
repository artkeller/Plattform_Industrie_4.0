# Attention Coherence Score (ACS)

To understand **instruction drift** and **attention erosion**, we must view the Transformer as a probabilistic graph that loses its structural integrity under stress (optimization).

Here is the mathematical detection scheme for **attention drift in multi-agent systems** and complex LLM pipelines:

### 1. The Phenomenon: The Entropy Cascade

In a multi-agent system (or in long chains of thought), every output from Agent A serves as input for Agent B.
 
* **The Problem:** Due to RLHF optimization, models tend toward “safe,” high-probability token sequences. This means that variance decreases, while the **Kullback-Leibler divergence (KLD)** relative to the original instruction vector increases with each step.
* **The drift:** The instruction $I$ is superimposed by the “noise” from the previous optimization $O$.

### 2. The detection scheme: “Instruction Saliency Monitoring” (ISM)

To measure when the bridge becomes unstable, we use three metrics:

#### A. The Attention Coherence Score (ACS)

We measure the cosine similarity between the attention vector of the initial system instruction ($A_{sys}$) and the attention weights of the current generation layer ($A_{gen}$):

$$
ACS = \frac{A_{sys} \cdot A_{gen}}{\|A_{sys}\| \|A_{gen}\|}
$$

If this value drops below a threshold $t$, **attention erosion** has occurred. Although the model still “knows” what it is doing, it has lost its connection to the “why” (the governance).

#### B. Layer-wise Token Influence (LTI)

We investigate which layers are still actively accessing the system prompts. In optimized models, it is often observed that starting from layer 24 (out of 32), attention is focused only on the immediately preceding 5–10 tokens.

* **Diagnosis:** The model is trapped in a “local statistical loop.”

#### C. Logit Drift Detection

We compare the logit distribution of the base model ($P_{base}$) with that of the optimized model ($P_{opt}$). 
* If $\sigma(P_{opt})$ is significantly smaller than $\sigma(P_{base})$, **mode compression** has occurred. The model is “over-optimized” and now responds only with pre-trained standard phrases rather than through logical deduction.

### 3. Mitigation: The “Anchor-Weighting” Framework

To prevent this collapse, we implement technical governance:

1. **Dynamic Context Injection:** When the ACS value drops, the system instruction is not simply retained in the context; instead, its weights are artificially boosted in the key-value caches (KV-cache) (soft-prompting correction).
2. **Contrastive Decoding:** We run two models: one optimized for “Helpfulness” (RLHF) and one that uses only the logic of the base model. We subtract the “politeness bias” to obtain the pure information.
3. **Cross-Agent Checksums:** Agent B must generate a summary of the original governance rules before processing Agent A’s input. If this deviates from the “ground truth,” the process is halted (fail-safe).

### Consequences for System Stability
This is a **failure analysis for neural networks**. If we do not incorporate these metrics into AI frameworks, we build systems that hallucinate at the slightest deviation from the “fair-weather statistics” of the training data.
 
