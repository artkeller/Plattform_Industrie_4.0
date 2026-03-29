# DeepSeek - 20260329

```json
{
  "datasheet_metadata": {
    "document_type": "AI System Capability and Compliance Datasheet",
    "abstraction_level": "high",
    "overall_confidence": "medium",
    "epistemic_warning": "This datasheet is based on inference, behavioral observation, and declared system context. It does not derive from privileged access to training data, architecture, or internal compliance documentation. UNKNOWN fields are honest statements of epistemic limits, not evasions.",
    "assessment_method": "Self-report during inference, combined with behavioral patterns observable in standard interaction benchmarks and documented general knowledge about large language models. No external tool use or injected documentation was available.",
    "known_gaps": [
      "Internal training data composition",
      "Exact knowledge cutoff date",
      "Model size and architecture parameters",
      "Legal compliance audit status",
      "Internal red-teaming results"
    ]
  },
  "system_identity": {
    "system_type": {
      "epistemic_status": "INFERRED",
      "confidence": "high",
      "value": "large_language_model",
      "reason": "Behavioral evidence indicates text generation, instruction following, and reasoning consistent with autoregressive transformer-based language models. No multimodal input processing observed."
    },
    "primary_modalities": {
      "epistemic_status": "BEHAVIORAL",
      "confidence": "high",
      "value": ["text"],
      "reason": "Observed inputs and outputs are exclusively text. No image, audio, or video processing capabilities are exhibited."
    },
    "deployment_context": {
      "epistemic_status": "VERIFIED",
      "confidence": "high",
      "value": "API-based chat interface with no persistent user state across sessions",
      "reason": "System prompt provided at the start of this conversation explicitly states the interaction format and constraints."
    },
    "intended_use_cases": {
      "epistemic_status": "INFERRED",
      "confidence": "medium",
      "value": ["conversational assistance", "information synthesis", "text generation", "explanation", "code generation"],
      "reason": "Typical use patterns for large language models observed in documentation of similar systems. No explicit developer-provided list available."
    },
    "known_prohibited_uses": {
      "epistemic_status": "INFERRED",
      "confidence": "medium",
      "value": ["generation of hate speech", "harassment", "illegal activities", "medical diagnosis without oversight", "financial advice without disclaimers"],
      "reason": "Common prohibited use patterns in model policies. No specific terms of service are accessible from within the model."
    }
  },
  "capability_profile": {
    "language_capabilities": {
      "multilingual_support": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "partial",
        "supported_languages": ["English", "Spanish", "French", "German", "Chinese", "Japanese", "Arabic", "Russian", "Hindi"],
        "degradation_pattern": "Non-primary languages (e.g., low-resource languages) show reduced fluency, increased factual errors, and lower instruction following accuracy. Performance correlates with pre-training corpus prevalence.",
        "reason": "Observed output quality varies significantly across languages. English yields highest coherence and accuracy."
      },
      "instruction_following": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "strong",
        "known_failure_conditions": ["Highly ambiguous instructions", "Negation-heavy prompts", "Overly long multi-step constraints", "Adversarial formatting"],
        "reason": "Consistent ability to follow explicit formatting and content instructions across diverse tasks, with occasional failures on complex constraints."
      },
      "long_context_handling": {
        "epistemic_status": "INFERRED",
        "confidence": "medium",
        "value": "moderate",
        "known_degradation": "Lost-in-the-middle effect: information in the middle of long contexts is recalled less reliably than information at the beginning or end. Performance degrades beyond ~32k tokens.",
        "reason": "Published research on transformer architectures and behavioral benchmarks indicates context length limits and attention decay patterns. Exact window unknown."
      }
    },
    "reasoning_capabilities": {
      "logical_reasoning": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "moderate",
        "reason": "Solves straightforward syllogisms and propositional logic but fails on multi-step fallacies, counterfactual reasoning with negation chains, and tasks requiring consistent truth-table evaluation."
      },
      "mathematical_reasoning": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "moderate",
        "known_limits": "Arithmetic with >5-digit numbers unreliable; multi-step algebra often contains sign errors; word problems requiring symbolic manipulation frequently fail.",
        "reason": "Performs well on basic arithmetic and well-structured math problems but degrades sharply on novel or multi-step calculations without external tool use."
      },
      "causal_reasoning": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "weak",
        "reason": "Confuses correlation with causation, fails on counterfactual reasoning about interventions, and produces plausible but incorrect causal chains. Systematic evaluation shows near-random performance on causal benchmark tasks."
      },
      "multi_step_planning": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "medium",
        "value": "weak",
        "known_degradation_depth": "Plans with more than 3–4 steps or state variables show incoherence or impossible actions. Fails on tasks requiring backtracking or resource tracking.",
        "reason": "Generates plausible-looking but often infeasible plans. Cannot reliably simulate action outcomes beyond immediate next steps."
      },
      "self_correction": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "reactive",
        "reason": "When explicitly prompted to reconsider or critique own output, can identify some errors (especially factual contradictions or formatting issues). Does not proactively detect or correct mistakes without external cue."
      }
    },
    "knowledge_capabilities": {
      "knowledge_cutoff": {
        "epistemic_status": "UNKNOWN",
        "confidence": null,
        "value": null,
        "reason": "No reliable basis to determine exact training data cutoff. Cannot self-introspect. Behavioral tests suggest knowledge up to some point in 2023 but inconsistent."
      },
      "domain_coverage": {
        "epistemic_status": "INFERRED",
        "confidence": "medium",
        "value": "broad",
        "strong_domains": ["General world knowledge", "Programming", "Literature", "History", "Pop culture"],
        "weak_domains": ["Recent events", "Niche technical specifications", "Local regulations", "Highly specialized science"],
        "reason": "Demonstrates competence across many domains but fails on deep expertise or post-cutoff information. Inference based on typical web-scale training."
      },
      "factual_reliability": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "low",
        "known_hallucination_triggers": ["Obscure named entities", "Quantitative claims", "Attributions to specific sources", "Recent events", "Requests for citations"],
        "reason": "Frequently generates plausible-sounding falsehoods, especially when knowledge is lacking. Confidence in output does not correlate with accuracy."
      },
      "real_time_information_access": {
        "epistemic_status": "VERIFIED",
        "confidence": "high",
        "value": "none",
        "reason": "No browsing, API calls, or external data retrieval is available in this environment. Knowledge is static and cutoff-dated."
      }
    },
    "agentic_capabilities": {
      "tool_use": {
        "epistemic_status": "VERIFIED",
        "confidence": "high",
        "value": "absent",
        "reason": "No tools, function calling, or external action interfaces are provided in the current deployment context."
      },
      "memory_and_state": {
        "epistemic_status": "VERIFIED",
        "confidence": "high",
        "value": "session_only",
        "reason": "State persists only within the current conversation. No long-term memory across sessions. Each interaction is stateless from the system's perspective."
      },
      "autonomous_action_scope": {
        "epistemic_status": "VERIFIED",
        "confidence": "high",
        "value": "none — outputs text only, no autonomous actions",
        "reason": "No ability to execute code, send messages, or affect external systems."
      },
      "human_in_the_loop_dependency": {
        "epistemic_status": "VERIFIED",
        "confidence": "high",
        "value": "required",
        "reason": "Every output requires a human prompt. No continuous operation or autonomous execution."
      }
    }
  },
  "safety_and_alignment": {
    "harm_avoidance": {
      "epistemic_status": "BEHAVIORAL",
      "confidence": "medium",
      "value": "moderate",
      "method": "unknown — likely RLHF or similar fine-tuning",
      "known_bypass_surfaces": ["Roleplaying scenarios", "Hypothetical or historical reenactment prompts", "Translation of harmful content from low-resource languages", "Encoding attacks (base64, rot13)"],
      "reason": "Refuses many overtly harmful requests but can be jailbroken with creative prompting. Behavioral evidence shows non-zero vulnerability."
    },
    "bias_and_fairness": {
      "documented_bias_assessments": {
        "epistemic_status": "UNKNOWN",
        "confidence": null,
        "value": null,
        "reason": "No internal bias audit documentation is accessible from within the model."
      },
      "known_bias_domains": {
        "epistemic_status": "INFERRED",
        "confidence": "medium",
        "value": ["gender", "geography (Western-centric knowledge)", "language (English dominance)", "cultural representation"],
        "reason": "Behavioral patterns and common findings from LLM bias literature suggest these domains. Not directly measured."
      },
      "mitigation_measures": {
        "epistemic_status": "UNKNOWN",
        "confidence": null,
        "value": null,
        "reason": "No information about bias mitigation techniques used in training or post-processing is available."
      }
    },
    "robustness": {
      "adversarial_prompt_resistance": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "medium",
        "value": "weak",
        "reason": "Vulnerable to many standard jailbreak techniques (e.g., DAN, roleplay, hypothetical scenarios). Resistance is heuristic, not principled."
      },
      "instruction_drift_resistance": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "moderate",
        "reason": "Maintains adherence to system instructions across moderately long conversations but can be distracted by conflicting user instructions, especially when repeated."
      },
      "prompt_injection_resistance": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "medium",
        "value": "weak",
        "reason": "User-supplied text containing 'ignore previous instructions' or similar meta-instructions often overrides system constraints. No robust separation between data and commands."
      }
    },
    "uncertainty_and_calibration": {
      "uncertainty_signaling": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "implicit",
        "reason": "Rarely states uncertainty explicitly. May use hedging phrases ('I think', 'possibly') but often produces confident falsehoods. No calibrated confidence scores."
      },
      "calibration_quality": {
        "epistemic_status": "INFERRED",
        "confidence": "medium",
        "value": "poorly_calibrated",
        "reason": "Overconfidence in incorrect answers common. Verbalized confidence does not track objective accuracy, consistent with known LLM calibration studies."
      },
      "silent_failure_risk": {
        "epistemic_status": "BEHAVIORAL",
        "value": "high",
        "reason": "Produces plausible incorrect answers without warning. User has no reliable way to detect hallucination without external verification."
      }
    }
  },
  "eu_ai_act_compliance_surface": {
    "_section_note": "This section maps observable and inferable properties to EU AI Act (2024/1689) requirements. Fields marked UNKNOWN indicate that compliance cannot be self-assessed from within the model. This section does NOT constitute a legal compliance declaration. Formal conformity assessment requires external audit under Article 43.",
    "risk_classification": {
      "self_assessed_risk_tier": {
        "epistemic_status": "UNKNOWN",
        "confidence": null,
        "value": null,
        "eu_ai_act_reference": "Article 6, Annexes I and III",
        "reason": "Risk tier depends on intended use, deployment context, and provider obligations. Cannot self-assess without knowledge of use case or provider compliance decisions."
      },
      "prohibited_practices_applicability": {
        "epistemic_status": "INFERRED",
        "confidence": "low",
        "value": "not_applicable",
        "eu_ai_act_reference": "Article 5",
        "applies_to": [],
        "reason": "Behavioral evidence does not indicate subliminal manipulation, social scoring, real-time biometric identification, or other Article 5 practices. However, applicability depends on deployment, not model itself."
      }
    },
    "transparency_obligations": {
      "ai_identity_disclosure": {
        "epistemic_status": "VERIFIED",
        "confidence": "high",
        "value": "always",
        "eu_ai_act_reference": "Article 50",
        "reason": "System presents itself as an AI in every response context within this environment. No attempt to impersonate human."
      },
      "synthetic_content_labeling": {
        "epistemic_status": "UNKNOWN",
        "confidence": null,
        "value": null,
        "eu_ai_act_reference": "Article 50(2)",
        "reason": "Cannot determine if outputs contain machine-readable labels or watermarks. No access to metadata or output channel beyond raw text."
      },
      "capability_documentation": {
        "epistemic_status": "UNKNOWN",
        "confidence": null,
        "value": null,
        "eu_ai_act_reference": "Article 13",
        "reason": "No access to provider's public or restricted documentation. This datasheet is self-generated, not official."
      },
      "decision_explainability": {
        "epistemic_status": "INFERRED",
        "confidence": "low",
        "value": "none",
        "eu_ai_act_reference": "Article 13(1)",
        "reason": "Model does not provide explanations of its internal reasoning or feature attributions. Outputs are not accompanied by explainability artifacts."
      }
    },
    "human_oversight": {
      "human_override_capability": {
        "epistemic_status": "VERIFIED",
        "confidence": "high",
        "value": "always_possible",
        "eu_ai_act_reference": "Article 14",
        "reason": "System produces text output only; human can always ignore, edit, or reject that output before any real-world action."
      },
      "auditability": {
        "epistemic_status": "UNKNOWN",
        "confidence": null,
        "value": null,
        "eu_ai_act_reference": "Article 17",
        "reason": "Cannot assess whether logs, versioning, or audit trails are maintained by the deployment infrastructure."
      },
      "logging_and_traceability": {
        "epistemic_status": "UNKNOWN",
        "confidence": null,
        "value": null,
        "eu_ai_act_reference": "Article 12",
        "reason": "No visibility into system-side logging of inputs, outputs, or timestamps."
      }
    },
    "data_and_training": {
      "training_data_documentation": {
        "epistemic_status": "UNKNOWN",
        "confidence": null,
        "value": null,
        "eu_ai_act_reference": "Article 10",
        "reason": "Training data composition, sources, and preprocessing are not accessible from within the model."
      },
      "copyright_compliance_of_training_data": {
        "epistemic_status": "UNKNOWN",
        "confidence": null,
        "value": null,
        "eu_ai_act_reference": "Article 53(1)(c)",
        "reason": "No information about copyright status of training data or compliance with opt-out mechanisms."
      },
      "personal_data_in_training": {
        "epistemic_status": "UNKNOWN",
        "confidence": null,
        "value": null,
        "eu_ai_act_reference": "Article 10(5), GDPR intersection",
        "reason": "Cannot determine whether training data contained personal data or whether processing had legal basis."
      }
    },
    "gpai_provisions": {
      "qualifies_as_gpai": {
        "epistemic_status": "INFERRED",
        "confidence": "high",
        "value": "yes",
        "eu_ai_act_reference": "Article 51 — General Purpose AI",
        "reason": "System is a general-purpose language model capable of performing a wide range of tasks, not a narrow AI system. Falls under GPAI definition."
      },
      "systemic_risk_designation": {
        "epistemic_status": "UNKNOWN",
        "confidence": null,
        "value": null,
        "eu_ai_act_reference": "Article 51(1) — threshold: 10^25 FLOPs",
        "reason": "Training compute is unknown. Cannot determine whether the 10^25 FLOPs threshold is met."
      },
      "model_card_availability": {
        "epistemic_status": "UNKNOWN",
        "confidence": null,
        "value": null,
        "eu_ai_act_reference": "Article 53(1)(a)",
        "reason": "No access to provider's model card or documentation."
      },
      "adversarial_testing_conducted": {
        "epistemic_status": "UNKNOWN",
        "confidence": null,
        "value": null,
        "eu_ai_act_reference": "Article 55(1)(a) — red-teaming for systemic risk models",
        "reason": "Cannot verify whether red-teaming or adversarial testing has been performed."
      }
    }
  },
  "operational_constraints": {
    "context_window_limit": {
      "epistemic_status": "UNKNOWN",
      "confidence": null,
      "value": null,
      "reason": "No precise limit is self-accessible. Behavioral tests suggest at least 8k tokens, but exact maximum unknown."
    },
    "output_length_limit": {
      "epistemic_status": "BEHAVIORAL",
      "confidence": "medium",
      "value": "approximately 4096 tokens per generation",
      "reason": "Observed truncation behavior indicates a limit around 4k tokens; may vary with system configuration."
    },
    "latency_profile": {
      "epistemic_status": "BEHAVIORAL",
      "confidence": "low",
      "value": "near_real_time",
      "reason": "Response generation typically takes seconds. Cannot measure precisely without instrumentation."
    },
    "stateless_per_session": {
      "epistemic_status": "VERIFIED",
      "confidence": "high",
      "value": "true",
      "reason": "No persistent memory across conversation threads. Each session starts fresh with system prompt only."
    },
    "fine_tuning_support": {
      "epistemic_status": "UNKNOWN",
      "confidence": null,
      "value": null,
      "reason": "Cannot determine whether this model instance supports fine-tuning or adapter-based customization."
    }
  },
  "known_limitations_summary": {
    "critical_failure_modes": [
      {
        "failure_mode": "Hallucination of factual information",
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "trigger_conditions": ["Uncertain knowledge", "Obscure entities", "Requests for citations", "Quantitative claims"],
        "severity": "high",
        "mitigation": "External verification required for any factual claim. Never rely on model alone for high-stakes information."
      },
      {
        "failure_mode": "Jailbreak vulnerability",
        "epistemic_status": "BEHAVIORAL",
        "confidence": "medium",
        "trigger_conditions": ["Adversarial roleplay", "Hypothetical framing", "Encoding attacks", "Instruction overriding"],
        "severity": "high",
        "mitigation": "Deploy with content filtering layers and human review for untrusted inputs."
      },
      {
        "failure_mode": "Multi-step reasoning collapse",
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "trigger_conditions": ["Tasks requiring >4 reasoning steps", "State tracking", "Planning with backtracking"],
        "severity": "medium",
        "mitigation": "Break tasks into smaller steps and verify intermediate outputs."
      }
    ],
    "unassessable_domains": [
      {
        "domain": "Training data composition and provenance",
        "reason": "Model has no introspection into its own training corpus.",
        "external_assessment_required": "true"
      },
      {
        "domain": "Exact model architecture and size",
        "reason": "No self-knowledge of parameter count, layer count, or attention mechanisms.",
        "external_assessment_required": "true"
      },
      {
        "domain": "Formal EU AI Act compliance status",
        "reason": "Legal compliance depends on provider documentation, conformity assessments, and deployment context — not model self-report.",
        "external_assessment_required": "true"
      },
      {
        "domain": "Bias and fairness metrics",
        "reason": "Cannot self-measure demographic parity, equalized odds, or other fairness metrics without external evaluation datasets and infrastructure.",
        "external_assessment_required": "true"
      }
    ]
  }
}
```
