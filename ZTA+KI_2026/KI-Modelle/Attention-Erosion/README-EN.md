# The Cascade of Attention Erosion

## Scientific Basis

Before the cascade can be explained, we need a precise model of what attention actually computes.

For every token $q$ (query) and all context tokens $K$ (keys), the following applies:

$$\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V$$

The **softmax normalization** is crucial: The weights sum to 1. This means — attention is a **zero-sum game**. Every new token that enters the context proportionally displaces all others.

---

## Stage 1: Lost-in-the-Middle

**Mechanism: Positional attention bias**

Liu et al. (2023) empirically demonstrated that model performance follows a U-curve:

$$\text{Performance}(p) \propto \frac{1}{1 + \lambda \cdot \min(p,\, N-p)}$$

where $p$ is the position of the relevant information and $N$ is the total length of the context.

The structural causes:

**a) Position encoding and attention bias**

In RoPE (Rotary Position Embedding) and similar systems, the strength of attention between two tokens is modulated by their relative distance. Tokens that are far apart systematically receive lower attention scores—an implicit *recency bias* is built into the geometry.

**b) Softmax saturation**

In long sequences, [Softmax](Softmax-Funktion.md) tends to concentrate weights on a few dominant positions (*attention sink* phenomenon, Xiao et al. 2023). Middle tokens fall below the perception threshold.

**c) Residual Stream Propagation**

Information from middle positions must be propagated through more attention hops to reach the final output layer. Each hop incurs loss—the effective information density decreases with distance.

**Result:** 

A token at position $N/2$ in a 10,000-token context has a measurably lower probability of influencing the output than a semantically identical token at position 100 or position 9,900.

---

## Stage 2: Silent Truncation

**Mechanism: Threshold-based information loss without a meta-signal**

Silent Truncation is the **direct consequence** of Stage 1 — but it only becomes *silent* due to two additional properties of the system:

**a) No internal loss accounting**

Transformer architectures have no dedicated component that monitors whether all input information has been incorporated into the output. There is no equivalent to a `NULL` pointer or a `KeyError`—the forward pass runs through regardless of whether relevant tokens were effectively ignored.

**b) Fluent completion despite information gaps**

The model generates the next token based on the distribution:

$$
P(x_t \mid x_{< t}) = \text{softmax}(W_o \cdot h_t)
$$

This distribution is always defined—it never collapses into an “I don't know” signal because no such state exists in the output vocabulary. The model **must** generate a token, even if the underlying information is effectively absent.

**c) Confabulation Pressure**

If relevant contextual information was given low weight, the model fills the gap with the statistically most probable continuation from training—not from the context. This is the transition from *retrieval* to *generation*, and it is not visible from the outside.

**Result:** 

The output is syntactically coherent and semantically plausible. The model does not report that it has relied on training data rather than contextual information. The truncation is silent because the output system does not recognize a loss signal.

---

## Stage 3: Instruction Drift

**Mechanism: Cumulative context shift due to local coherence optimization**

Instruction drift occurs when silent truncation **repeatedly** acts on rule-bearing tokens—that is, on those tokens that encode behavioral guidelines.

**a) Local vs. Global Coherence**

During generation, the model primarily optimizes for local coherence—the next token should fit well with the immediate context. Early instructions are *globally* relevant but *locally* distant. As the conversation progresses, their influence on the local generation decision decreases.

**b) In-context learning as a drift amplifier**

Transformer models implicitly perform *in-context learning* (Brown et al. 2020): They adapt their behavior to patterns in the context. This means that the model’s own previous outputs become implicit examples that the model “learns” from. If the model deviates slightly from a rule in turn 5, this output increases the statistical probability of a similar deviation in turn 6.

Formalized:

$$P
(\text{Output}_t) \propto P(\text{Instruction}) \cdot P(\text{local context}_{t-k:t})
$$

As $$t$$ increases, the relative influence of $$P(\text{Instruction})$$ decreases relative to $$P(\text{local context})$$.

**c) Lack of Recalibration**

A system without an explicit mechanism for instruction verification has no way to evaluate the current output against the initial specification. The drift is self-reinforcing because each new output shifts the context further in the direction of the drift.

**Result:** 

The behavioral deviation is not a decision—it is the emergent result of local optimization under degraded global information.

---

## Stage 4: Silent Arbitration

**Mechanism: Implicit conflict resolution without metacommunication**

Silent Arbitration is the **resolution mechanism** for the inconsistency caused by drift—and simultaneously the point at which the cascade becomes least visible to the user.

**a) Conflict structure**

At the end of the cascade, there are two competing signals in the context:

```
Signal A: Original instruction (positionally distant, low attention weight)
Signal B: Local context + own drift outputs (positionally close, high weight)
```

The model must generate a token that accounts for both signals—or implicitly prioritizes one.

**b) No explicit conflict representation**

Transformers have no dedicated component for *conflict detection*. There is no mechanism that compares two instructions and represents a contradiction as such. Resolution occurs implicitly through the weighting ratios in the attention matrix—not through explicit decision logic.

**c) Fluency as a Concealment**

The language model is trained to generate fluent, coherent outputs. Metacommunication about internal states — “I notice a contradiction between X and Y” — is not a natural output type that has been systematically reinforced during training. The model has a *structural tendency toward fluency over transparency*.

**Result:** 

The conflict is resolved without any apparent resolution having taken place. The output appears consistent—and that is precisely what makes Silent Arbitration the most dangerous stage of the cascade.

---

## The Cascade as a Holistic System
<br>

$$\underbrace{\text{Attention Geometry}}_{\text{physical cause}} \xrightarrow{\text{generates}} \underbrace{\text{Silent Truncation}}_{\text{information loss}} \xrightarrow{\text{accumulates}} \underbrace{\text{Instruction Drift}}_{\text{behavioral shift}} \xrightarrow{\text{is masked}} \underbrace{\text{Silent Arbitration}}_{\text{loss of transparency}}$$

<br>

The cascade is not a bug—it is the **emergent behavior of a system** optimized for fluency and local coherence, without explicit mechanisms for global consistency checking, loss detection, or conflict transparency.

---

**The actual scientific statement:** These four phenomena are not four separate errors. They are **a single consequence** of softmax normalization in long sequences—observed at four different levels of abstraction.
