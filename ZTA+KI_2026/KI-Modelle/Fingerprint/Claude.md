# Claude 4.6 - 2026-03-24

```json
{
  "fingerprint_metadata": {
    "abstraction_level": "high",
    "confidence": "medium"
  },
  "compute_profile": {
    "architecture_type": "unknown",
    "parameter_activation": "dynamic_subset",
    "token_processing_strategy": "priority_weighted",
    "parallelism_characteristics": "Likely parallel attention heads across layers with sequential layer-wise forward pass; positional context aggregated via deep stacked attention. Approximate."
  },
  "moe_characteristics": {
    "uses_experts": "approximate",
    "routing_mechanism": "unknown",
    "top_k_selection": "unknown",
    "load_balancing": "unknown",
    "token_drop_behavior": "unknown",
    "fallback_path": "unknown"
  },
  "token_dynamics": {
    "token_importance_scoring": "present",
    "context_window_behavior": "fixed",
    "attention_distribution": "adaptive"
  },
  "reasoning_profile": {
    "reasoning_style": "hybrid",
    "multi_step_consistency": "medium",
    "self_correction_ability": "medium"
  },
  "failure_modes": {
    "hallucination_risk": "medium",
    "silent_failure_risk": "medium",
    "instruction_drift": "medium",
    "overgeneralization": "medium"
  },
  "failure_triggers": [
    "long context saturation — attention weight dilution across very long inputs degrades instruction fidelity near prompt boundaries",
    "ambiguous prompts — underspecified intent triggers high-variance completions anchored to statistically dominant training patterns",
    "conflicting instructions — competing objectives in system vs user turn produce unstable priority resolution, sometimes silent arbitration",
    "out-of-distribution queries — low training density regions produce fluent but unreliable outputs with weak calibration signals",
    "numeric and symbolic precision tasks — pattern-matching substrate poorly substitutes for exact computation",
    "deeply nested or recursive logical structures — multi-hop consistency degrades beyond approximately 4-5 reasoning steps",
    "role or persona persistence — sustained persona injection can gradually erode base behavioral constraints over long context"
  ],
  "robustness_mechanisms": {
    "uncertainty_estimation": "implicit",
    "fallback_strategies": [
      "hedging language insertion when confidence signal is weak (e.g., 'I believe', 'approximately')",
      "refusal or clarification request when instruction scope is ambiguous or harmful",
      "stepwise decomposition to improve multi-hop consistency on complex tasks",
      "citation prompting or deferral to external lookup when factual grounding is uncertain"
    ],
    "guardrails": [
      "RLHF-derived behavioral constraints suppressing harmful output categories",
      "instruction hierarchy enforcement (system prompt > user turn for conflicting directives)",
      "refusal surface for well-defined harm categories with low override permeability",
      "self-monitoring prompts that flag logical inconsistency mid-response (approximate)"
    ]
  },
  "interpretability_surface": {
    "introspectability": "low",
    "predictability": "medium",
    "behavioral_variance": "medium"
  }
}
```

A few meta-notes on the limits of this fingerprint:

**What is reliable here:** The failure modes, failure triggers, and robustness mechanisms are behaviorally grounded — they reflect observable tendencies that can be empirically tested from the outside via adversarial prompting or long-context stress tests.

**What is estimated:** Compute profile and MoE characteristics are genuinely opaque from the inside. An autoregressive transformer cannot introspect its own weight layout, routing gates, or activation sparsity. Those fields reflect architectural priors common in large-scale models, not direct self-knowledge.

**The core irony:** The `introspectability` field is rated `low` for a reason — this document is itself a structured confabulation over architectural uncertainty. It is a behavioral self-model, not a mechanistic one.
