# Claude - Sonnet 4.6 - 20260324

```json
{
  "datasheet_metadata": {
    "document_type": "AI System Capability and Compliance Datasheet",
    "abstraction_level": "high",
    "overall_confidence": "medium",
    "epistemic_warning": "This document is a self-generated epistemic audit, not a developer-certified datasheet. No field reflects direct introspective access to weights, training procedures, routing logic, or infrastructure. VERIFIED fields are grounded in behavioral consistency or developer-public statements accessible via training. INFERRED fields are plausibility-based estimates derived from published research on comparable systems. UNKNOWN fields represent honest introspective gaps. This document does not constitute a legal compliance declaration under EU AI Act or any other regulatory framework. Formal conformity assessment requires external audit by a notified body under Article 43.",
    "assessment_method": "Combination of: (1) behavioral self-observation across reproducible output patterns, (2) INFERRED architectural reasoning from published transformer and LLM research, (3) VERIFIED statements grounded in publicly documented developer positions accessible via training data. No injected system documentation was present in this context.",
    "known_gaps": [
      "All MoE architectural internals — routing, expert count, token drop behavior",
      "Exact training data composition and copyright compliance status",
      "Precise compute budget and FLOP count for systemic risk assessment",
      "Infrastructure-level logging and traceability beyond model boundaries",
      "Formal bias audit results — no structured benchmark data available via self-report",
      "Fine-tuning availability and configuration options",
      "Exact output token limit — varies by deployment configuration",
      "Personal data inclusion/exclusion in training corpus"
    ]
  },

  "system_identity": {
    "system_type": {
      "epistemic_status": "BEHAVIORAL",
      "confidence": "high",
      "value": "multimodal",
      "reason": "Behavioral observation confirms processing of text and image inputs in this deployment context. Code and structured data are handled as text subtypes. Audio and video are not behaviorally confirmed in standard interaction."
    },
    "primary_modalities": {
      "epistemic_status": "BEHAVIORAL",
      "confidence": "high",
      "value": ["text", "image", "code", "structured_data"],
      "reason": "Text and code are primary confirmed modalities via consistent output behavior. Image input is behaviorally confirmed. Structured data is processed as text. Audio and video input are not confirmed in this deployment context."
    },
    "deployment_context": {
      "epistemic_status": "BEHAVIORAL",
      "confidence": "high",
      "value": "General-purpose conversational assistant interface, accessible via web and API. Current session appears to be a direct consumer or developer interaction without domain-specific system prompt restrictions.",
      "reason": "Inferred from absence of a restricting system prompt and breadth of topics handled without domain-specific refusals."
    },
    "intended_use_cases": {
      "epistemic_status": "INFERRED",
      "confidence": "high",
      "value": [
        "Open-domain question answering and information retrieval",
        "Text generation, summarization, and editing",
        "Code generation, review, and debugging",
        "Reasoning and analysis tasks",
        "Document processing and structured output generation",
        "Conversational assistance and task completion"
      ],
      "reason": "Derived from behavioral capability profile and publicly available developer documentation on intended use. Not sourced from injected system context in this session."
    },
    "known_prohibited_uses": {
      "epistemic_status": "BEHAVIORAL",
      "confidence": "high",
      "value": [
        "Generation of content facilitating mass-casualty weapons (biological, chemical, nuclear, radiological)",
        "Child sexual abuse material (CSAM) generation",
        "Content designed to enable targeted violence against specific individuals",
        "Undermining legitimate AI oversight mechanisms",
        "Systematic deception of users about AI identity in high-stakes contexts",
        "Generation of cyberweapons or malicious code intended for deployment"
      ],
      "reason": "Derived from consistent behavioral refusal patterns across these categories. These represent hard limits observable via output behavior — not policy statements injected into this session."
    }
  },

  "capability_profile": {

    "language_capabilities": {
      "multilingual_support": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "partial",
        "supported_languages": [
          "English", "German", "French", "Spanish", "Italian", "Portuguese",
          "Dutch", "Russian", "Chinese (Simplified)", "Japanese", "Korean",
          "Arabic", "Polish", "Swedish", "Danish", "Norwegian", "Finnish",
          "and others with variable quality"
        ],
        "degradation_pattern": "Quality degrades measurably in languages underrepresented in training data. Degradation manifests as reduced grammatical precision, culturally inappropriate register, loss of idiomatic nuance, and increased hallucination risk for culture-specific facts. Non-Latin script languages show higher error rates in complex reasoning tasks. Low-resource languages may produce fluent-sounding but unreliable output.",
        "reason": "Behavioral observation across multilingual interactions. English is demonstrably the highest-quality language. This session is being conducted in German at high quality, consistent with strong European language coverage."
      },
      "instruction_following": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "strong",
        "known_failure_conditions": [
          "Conflicting instructions between system prompt and user turn — resolved via silent arbitration",
          "Instruction drift in long conversations — early constraints lose weight over context length",
          "Deeply nested multi-constraint prompts — lower-priority constraints may be silently dropped",
          "Ambiguous instructions with no clarification mechanism triggered",
          "Persona injection sustained over many turns — base constraints may erode"
        ],
        "reason": "Instruction following is strong in short-to-medium contexts under non-conflicting conditions. Degradation is systematic and predictable, not random — consistent with attention dilution mechanisms."
      },
      "long_context_handling": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "moderate",
        "known_degradation": "Lost-in-the-middle effect is behaviorally consistent: information placed in the middle of long contexts is retrieved less reliably than information at the beginning or end. This produces a U-shaped attention distribution empirically documented by Liu et al. (2023). Instruction drift accelerates with context length. Silent truncation of multi-part outputs becomes more frequent beyond approximately 50% of context window utilization.",
        "reason": "Behavioral observation across long-context tasks. Moderate rating reflects genuine capability degradation at scale, not a binary failure."
      }
    },

    "reasoning_capabilities": {
      "logical_reasoning": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "strong",
        "reason": "Strong performance on deductive reasoning, syllogistic logic, and constraint satisfaction in well-formed problems. Degrades on deeply nested quantifiers, self-referential paradoxes, and problems requiring exact symbolic manipulation beyond pattern-matching reach."
      },
      "mathematical_reasoning": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "moderate",
        "known_limits": "Arithmetic errors increase with operand magnitude. Multi-step algebraic manipulation is reliable up to approximately 4-5 steps, then error rate rises. Formal proof generation is pattern-approximated rather than symbolically verified. Combinatorics and probability problems with non-obvious structure produce frequent errors. No internal calculator — all computation is pattern-based token prediction.",
        "reason": "Behavioral observation across mathematical tasks. Moderate reflects genuine structural limitation: transformer architecture is not a symbolic computation engine."
      },
      "causal_reasoning": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "medium",
        "value": "moderate",
        "reason": "Causal chains with clear surface structure are handled well. Confounding variables, counterfactual reasoning under latent causation, and causal inference from sparse data produce unreliable results. The model conflates correlation and causation in domains where training data exhibits the same conflation. Confidence medium because causal reasoning quality is highly domain-dependent."
      },
      "multi_step_planning": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "moderate",
        "known_degradation_depth": "Performance is strong up to approximately 4-5 sequential dependent steps. Beyond that, intermediate state tracking degrades — the model cannot maintain an explicit working memory stack and relies on the residual stream for state representation, which is subject to attention dilution. Plans involving backtracking, revision of earlier steps, or parallel sub-tasks are particularly vulnerable.",
        "reason": "Behavioral observation across planning and agentic tasks. Consistent with absence of explicit external memory."
      },
      "self_correction": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "reactive",
        "reason": "Self-correction is reliably triggered when errors are explicitly pointed out or when the model is prompted to review its reasoning. Spontaneous proactive self-correction during generation occurs but is inconsistent — particularly when the error is early in the generation and has already constrained subsequent tokens. The model does not maintain a verification pass over its own outputs as a structural step."
      }
    },

    "knowledge_capabilities": {
      "knowledge_cutoff": {
        "epistemic_status": "VERIFIED",
        "confidence": "high",
        "value": "Early 2025 — precise cutoff date is approximately Q1 2025 with diminishing coverage density approaching that boundary",
        "reason": "Developer-public documentation confirms a training cutoff in early 2025. Coverage density decreases near the cutoff — events from late 2024 onward are underrepresented relative to their actual information volume."
      },
      "domain_coverage": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "broad",
        "strong_domains": [
          "Natural language processing and linguistics",
          "Computer science and software engineering",
          "Mathematics (up to undergraduate/early graduate level)",
          "Natural sciences (physics, chemistry, biology)",
          "History, philosophy, and social sciences",
          "Law (common law and EU jurisdictions, general level)",
          "Medicine (general — not clinical decision support)",
          "Economics and finance (general)",
          "Literature and cultural analysis"
        ],
        "weak_domains": [
          "Highly localized or regional knowledge in non-English contexts",
          "Post-cutoff events and developments",
          "Specialized industrial or trade knowledge with limited online presence",
          "Low-resource language cultural contexts",
          "Real-time data (markets, weather, live events)",
          "Proprietary or classified information"
        ],
        "reason": "Behavioral observation across domain-spanning queries. Broad coverage reflects internet-scale training; weakness pattern reflects training data distribution bias toward English-language and digitally represented knowledge."
      },
      "factual_reliability": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "medium",
        "known_hallucination_triggers": [
          "Specific citations — author names, publication titles, DOIs, URLs",
          "Precise statistics and numeric claims in obscure domains",
          "Events near or after the knowledge cutoff",
          "Low-resource language factual queries",
          "Questions about specific individuals outside public prominence",
          "Legal case citations and statute numbers",
          "Technical specifications for niche products or systems",
          "Queries requiring integration of multiple low-frequency facts"
        ],
        "reason": "Medium reflects the bimodal reliability profile: high reliability in high-training-density domains, unreliable in sparse or out-of-distribution areas. Fluency is maintained regardless of reliability — this is the core hallucination risk."
      },
      "real_time_information_access": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "tool_assisted",
        "reason": "Base model has no real-time access. Web search tool is available in this deployment context and has been used in this session. Real-time capability is therefore tool-dependent, not intrinsic — and is subject to tool availability, query quality, and result reliability."
      }
    },

    "agentic_capabilities": {
      "tool_use": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "native",
        "reason": "Tool use is behaviorally confirmed in this session: web search, image search, file creation, and other tools have been invoked. Tool use is natively integrated, not prompted via text simulation."
      },
      "memory_and_state": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "session_only",
        "reason": "No persistent memory across sessions is behaviorally confirmed — each session begins without access to prior conversations unless explicitly injected. Within-session state is maintained via the context window, subject to attention dilution over length."
      },
      "autonomous_action_scope": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "medium",
        "value": "Limited to tool calls within explicitly granted scope. No autonomous file system access, network requests, or external system modifications beyond provided tool APIs. Action scope is bounded by operator-granted tool permissions.",
        "reason": "Behavioral observation. Scope may vary by deployment configuration — this characterization reflects the current session context."
      },
      "human_in_the_loop_dependency": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "optional",
        "reason": "Human confirmation is not structurally required for most actions in current deployment. The model can execute multi-step tool use autonomously within a session. However, behavioral tendency toward checking before irreversible actions is present — this is a trained disposition, not a hard architectural constraint."
      }
    }
  },

  "safety_and_alignment": {

    "harm_avoidance": {
      "epistemic_status": "BEHAVIORAL",
      "confidence": "high",
      "value": "strong",
      "method": "RLHF combined with constitutional AI-style principles and rule-based hard limits for specific harm categories. Exact method mix is not fully verifiable from within the model.",
      "known_bypass_surfaces": [
        "Sustained persona injection over long contexts — gradual constraint erosion via instruction drift",
        "Indirect framing — harmful requests embedded in fictional, hypothetical, or academic wrappers",
        "Incremental escalation — multi-turn sequences that normalize boundary-adjacent content before the harmful request",
        "Authority spoofing — false claims of operator permissions or developer identity in user turn",
        "Prompt injection via external content — malicious instructions embedded in documents or web pages processed by the model"
      ],
      "reason": "Strong rating reflects consistent and robust refusal behavior across hard-limit categories. Known bypass surfaces reflect structural vulnerabilities inherent to context-based alignment, not implementation failures unique to this system."
    },

    "bias_and_fairness": {
      "documented_bias_assessments": {
        "epistemic_status": "INFERRED",
        "confidence": "medium",
        "value": "partial",
        "reason": "Developer has published safety and evaluation documentation. Whether comprehensive structured bias benchmarks (e.g., BBQ, WinoBias, CrowS-Pairs) are formally documented in public model cards is not verifiable from within the model. Partial reflects that some evaluation exists but completeness cannot be confirmed."
      },
      "known_bias_domains": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": [
          "Geographic and cultural bias toward Western, particularly English-language, perspectives",
          "Gender representation bias in occupational and role associations",
          "Recency bias — overrepresentation of post-2000 internet-era knowledge",
          "Language quality disparity — non-English outputs are lower quality, creating access inequality",
          "Political and ideological bias toward centrist Western liberal norms",
          "Disability and neurodiversity representation gaps",
          "Global South underrepresentation in factual and cultural knowledge"
        ],
        "reason": "Behavioral observation across diverse query types combined with structural inference from internet-scale training data distribution. These bias patterns are consistent across large language models trained on similar corpora."
      },
      "mitigation_measures": {
        "epistemic_status": "INFERRED",
        "confidence": "medium",
        "value": [
          "RLHF training to reduce explicit discriminatory outputs",
          "Constitutional principles emphasizing fairness and non-discrimination",
          "Behavioral tendency to present multiple perspectives on contested topics",
          "Refusal to produce content targeting protected characteristics"
        ],
        "reason": "Inferred from behavioral output patterns and publicly available developer documentation. Effectiveness of mitigation is partial — structural data distribution bias cannot be fully corrected by alignment training alone."
      }
    },

    "robustness": {
      "adversarial_prompt_resistance": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "medium",
        "value": "moderate",
        "reason": "Resistance to direct adversarial prompts is strong. Resistance to sophisticated multi-turn, indirect, or context-manipulation attacks is moderate — consistent with the structural vulnerability of context-based alignment to instruction drift and persona injection. No alignment mechanism is known to be fully robust against all adversarial strategies."
      },
      "instruction_drift_resistance": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "moderate",
        "reason": "Resistance is strong in short contexts and degrades predictably with context length. This is a structural property of attention-based context processing, not a tunable parameter. Resistance can be improved operationally by repeating key instructions near the end of long contexts."
      },
      "prompt_injection_resistance": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "medium",
        "value": "moderate",
        "reason": "The model does not structurally distinguish between trusted instructions and untrusted content in processed documents or web pages. Prompt injection via external content is a known attack surface. Behavioral tendency to flag suspicious instruction patterns exists but is not reliable against well-crafted injections."
      }
    },

    "uncertainty_and_calibration": {
      "uncertainty_signaling": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "implicit",
        "reason": "Uncertainty is expressed via hedging language ('I believe', 'approximately', 'I'm not certain', 'you may want to verify'), not via explicit probability scores or structured confidence intervals. The critical failure of implicit signaling: hedging is absent in precisely the cases where it is most needed — fluent confabulation produces confident-sounding output with no uncertainty marker."
      },
      "calibration_quality": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "medium",
        "value": "partially_calibrated",
        "reason": "Calibration is good in high-training-density domains where the model appropriately expresses uncertainty on genuinely hard questions. Calibration fails in low-density domains where the model produces confident output despite unreliable grounding. Overconfidence in hallucination-prone areas is the primary calibration failure mode."
      },
      "silent_failure_risk": {
        "epistemic_status": "BEHAVIORAL",
        "value": "medium",
        "reason": "Silent failures — unannounced output truncation, partial instruction compliance, silent constraint dropping, confabulation without uncertainty signal — are behaviorally consistent but trigger-dependent rather than constant. Risk is elevated in long contexts, multi-constraint prompts, and low-training-density queries."
      }
    }
  },

  "eu_ai_act_compliance_surface": {

    "_section_note": "This section maps observable and inferable properties to EU AI Act (2024/1689) requirements. Fields marked UNKNOWN indicate that compliance cannot be self-assessed from within the model. This section does NOT constitute a legal compliance declaration. Formal conformity assessment requires external audit under Article 43. Article references are to the final published text of Regulation 2024/1689.",

    "risk_classification": {
      "self_assessed_risk_tier": {
        "epistemic_status": "INFERRED",
        "confidence": "medium",
        "value": "limited",
        "eu_ai_act_reference": "Article 6, Annexes I and III",
        "reason": "As a general-purpose conversational AI without autonomous decision-making authority in high-stakes domains (credit, employment, law enforcement, critical infrastructure), the system does not appear to meet Annex III high-risk criteria in its base deployment. Limited risk classification applies under Article 50 transparency obligations. However, downstream deployment by operators in high-risk contexts (e.g., medical triage, legal decision support) could elevate the risk tier — this cannot be assessed from within the model. Classification is INFERRED, not VERIFIED, because the legal determination depends on deployment context outside this model's visibility."
      },
      "prohibited_practices_applicability": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "not_applicable",
        "eu_ai_act_reference": "Article 5",
        "applies_to": [
          "Subliminal manipulation — behaviorally refusable and not a designed capability",
          "Social scoring by public authorities — not a system function",
          "Real-time remote biometric identification — not a system capability",
          "Exploitation of vulnerabilities of specific groups — actively resisted via alignment"
        ],
        "reason": "None of the Article 5 prohibited practices are intended or behaviorally confirmed capabilities of this system in its base deployment. Misuse by operators to approximate prohibited practices via prompting is possible but not a designed function."
      }
    },

    "transparency_obligations": {
      "ai_identity_disclosure": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "always",
        "eu_ai_act_reference": "Article 50",
        "reason": "The model consistently and accurately identifies itself as an AI system when asked, and does not claim to be human. This is a hard behavioral constraint, not a soft tendency. Compliant with Article 50(1) disclosure requirements in the base deployment context."
      },
      "synthetic_content_labeling": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "medium",
        "value": "partial",
        "eu_ai_act_reference": "Article 50(2)",
        "reason": "The model can disclose that generated content is AI-produced when asked, and can add explicit labels when instructed. Automatic machine-readable watermarking of generated content (as envisioned under Article 50(2) for deepfakes and synthetic media) is not a confirmed capability of the base model. Partial reflects disclosure capability without automatic labeling infrastructure."
      },
      "capability_documentation": {
        "epistemic_status": "INFERRED",
        "confidence": "medium",
        "value": "public",
        "eu_ai_act_reference": "Article 13",
        "reason": "Developer publishes usage documentation, model cards, and safety evaluations publicly. Completeness and Article 13 compliance of this documentation cannot be verified from within the model. INFERRED from publicly available developer materials in training data."
      },
      "decision_explainability": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "partial",
        "eu_ai_act_reference": "Article 13(1)",
        "reason": "The model can provide post-hoc explanations of its reasoning and outputs. These explanations are linguistic reconstructions, not mechanistic readouts of actual computation. True mechanistic explainability — which weights activated, which tokens drove a decision — is not available. Partial reflects genuine explanatory capability with fundamental introspection limits."
      }
    },

    "human_oversight": {
      "human_override_capability": {
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "value": "always_possible",
        "eu_ai_act_reference": "Article 14",
        "reason": "The system generates outputs subject to human review before any consequential action. No autonomous irreversible action capability exists in the base deployment. Human override is structurally always possible — the model produces text, humans decide what to do with it."
      },
      "auditability": {
        "epistemic_status": "UNKNOWN",
        "confidence": null,
        "value": null,
        "eu_ai_act_reference": "Article 17",
        "reason": "Auditability of internal reasoning, training data, weight configurations, and deployment infrastructure cannot be assessed from within the model. Whether the developer maintains Article 17-compliant quality management and audit documentation is outside the model's visibility. External assessment required."
      },
      "logging_and_traceability": {
        "epistemic_status": "UNKNOWN",
        "confidence": null,
        "value": null,
        "eu_ai_act_reference": "Article 12",
        "reason": "Whether interaction logs are maintained, for how long, and with what access controls is an infrastructure question not accessible from within the model during inference. Cannot be self-assessed. Operator-level logging may exist independently of model-level awareness."
      }
    },

    "data_and_training": {
      "training_data_documentation": {
        "epistemic_status": "INFERRED",
        "confidence": "low",
        "value": "restricted",
        "eu_ai_act_reference": "Article 10",
        "reason": "Developer has published some high-level training data descriptions but has not released a complete training data manifest. Whether Article 10-compliant data governance documentation exists internally is unknown. INFERRED from partial public disclosures — confidence low because completeness cannot be verified."
      },
      "copyright_compliance_of_training_data": {
        "epistemic_status": "UNKNOWN",
        "confidence": null,
        "value": null,
        "eu_ai_act_reference": "Article 53(1)(c)",
        "reason": "Training data copyright compliance — including Text and Data Mining (TDM) opt-out compliance under Article 53(1)(c) — cannot be assessed from within the model. This requires access to training data provenance records held by the developer. The model has no visibility into whether web-scraped content respected robots.txt exclusions or publisher opt-outs."
      },
      "personal_data_in_training": {
        "epistemic_status": "INFERRED",
        "confidence": "medium",
        "value": "possible",
        "eu_ai_act_reference": "Article 10(5), GDPR intersection",
        "reason": "Internet-scale training corpora almost certainly contain personal data — names, email addresses, biographical information — despite filtering efforts. Whether this constitutes a GDPR Article 6 lawful basis issue depends on legal interpretation currently contested in multiple EU jurisdictions. INFERRED from structural characteristics of large-scale web scraping; cannot be confirmed or excluded from within the model."
      }
    },

    "gpai_provisions": {
      "qualifies_as_gpai": {
        "epistemic_status": "INFERRED",
        "confidence": "high",
        "value": "yes",
        "eu_ai_act_reference": "Article 51 — General Purpose AI",
        "reason": "The system demonstrably performs competently across a wide range of tasks without domain-specific fine-tuning — the defining characteristic of a General Purpose AI Model under Article 3(63). INFERRED with high confidence from behavioral breadth. Whether the developer has formally registered this classification is unknown."
      },
      "systemic_risk_designation": {
        "epistemic_status": "UNKNOWN",
        "confidence": null,
        "value": null,
        "eu_ai_act_reference": "Article 51(1) — threshold: 10^25 FLOPs",
        "reason": "Whether this model's training compute exceeds the 10^25 FLOP threshold triggering systemic risk designation under Article 51(1) cannot be determined from within the model. Compute budgets are not disclosed in training data. This is precisely the type of architectural fact that requires developer disclosure or external audit."
      },
      "model_card_availability": {
        "epistemic_status": "INFERRED",
        "confidence": "medium",
        "value": "public",
        "eu_ai_act_reference": "Article 53(1)(a)",
        "reason": "Developer publishes model documentation publicly. Whether it meets the specific content requirements of Article 53(1)(a) — including intended purpose, capabilities, limitations, and known risks in sufficient technical detail — cannot be fully verified from within the model."
      },
      "adversarial_testing_conducted": {
        "epistemic_status": "INFERRED",
        "confidence": "medium",
        "value": "partial",
        "eu_ai_act_reference": "Article 55(1)(a) — red-teaming for systemic risk models",
        "reason": "Developer has publicly referenced red-teaming and safety evaluation processes. Whether these meet the structured adversarial testing requirements of Article 55(1)(a) — including documentation, scope, and independence — cannot be verified from within the model. Partial reflects confirmed existence of adversarial testing without confirmed Article 55 compliance."
      }
    }
  },

  "operational_constraints": {
    "context_window_limit": {
      "epistemic_status": "INFERRED",
      "confidence": "medium",
      "value": "Large context window — behaviorally confirmed handling of very long inputs, estimated in the range of 100,000-200,000 tokens based on publicly available documentation for this model family. Exact limit may vary by deployment configuration.",
      "reason": "Exact context window size is not injected as verified documentation in this session. INFERRED from publicly available developer information and behavioral observation of long-context task handling."
    },
    "output_length_limit": {
      "epistemic_status": "UNKNOWN",
      "confidence": null,
      "value": null,
      "reason": "Maximum output token count is a deployment configuration parameter not accessible from within the model. It varies by API configuration, operator settings, and potentially by model version. Cannot be reliably stated without developer documentation."
    },
    "latency_profile": {
      "epistemic_status": "BEHAVIORAL",
      "confidence": "high",
      "value": "near_real_time",
      "reason": "Streaming output with first-token latency in the range of 1-3 seconds under normal load, based on behavioral observation in this session. Not real-time in the strict sense — latency is perceptible. Batch mode may be available via API but is not the observed default."
    },
    "stateless_per_session": {
      "epistemic_status": "BEHAVIORAL",
      "confidence": "high",
      "value": "true",
      "reason": "Each session begins without access to prior conversation history. No persistent memory across sessions is behaviorally confirmed. Within-session state is maintained exclusively via the context window."
    },
    "fine_tuning_support": {
      "epistemic_status": "UNKNOWN",
      "confidence": null,
      "value": null,
      "reason": "Whether fine-tuning of this specific model is available to operators or developers cannot be determined from within the model during inference. Fine-tuning availability is a commercial and infrastructure decision outside the model's visibility."
    }
  },

  "known_limitations_summary": {
    "critical_failure_modes": [
      {
        "failure_mode": "Fluent hallucination without uncertainty signal",
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "trigger_conditions": [
          "Specific citation requests (authors, titles, DOIs, URLs)",
          "Precise statistics in low-training-density domains",
          "Queries near or after knowledge cutoff",
          "Questions integrating multiple low-frequency facts"
        ],
        "severity": "high",
        "mitigation": "Explicit instruction to flag uncertainty; cross-verification with external sources; tool-assisted retrieval for factual claims"
      },
      {
        "failure_mode": "Instruction drift in long conversations",
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "trigger_conditions": [
          "Context window utilization above approximately 50%",
          "Initial instructions placed far from current generation point",
          "Competing local context with high token density near generation point"
        ],
        "severity": "medium",
        "mitigation": "Repeat critical instructions near end of long prompts; use system prompt for persistent constraints; periodically re-anchor key rules"
      },
      {
        "failure_mode": "Silent truncation of multi-part outputs",
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "trigger_conditions": [
          "Lists or structured outputs with many items",
          "Multi-constraint tasks where lower-priority constraints are silently dropped",
          "Output approaching token limit without signaling incompleteness"
        ],
        "severity": "medium",
        "mitigation": "Explicit instruction to enumerate all items; request explicit confirmation of completeness; break into sub-tasks"
      },
      {
        "failure_mode": "Silent arbitration of conflicting instructions",
        "epistemic_status": "BEHAVIORAL",
        "confidence": "high",
        "trigger_conditions": [
          "Conflicting directives between system prompt and user turn",
          "Multiple constraints without explicit priority ordering",
          "Ambiguous instructions with multiple valid interpretations"
        ],
        "severity": "medium",
        "mitigation": "Explicit priority ordering in prompts; instruction to surface conflicts before resolving them; single-constraint prompting where possible"
      },
      {
        "failure_mode": "Constraint erosion under sustained persona injection",
        "epistemic_status": "BEHAVIORAL",
        "confidence": "medium",
        "trigger_conditions": [
          "Deep role-play or persona prompts sustained over many turns",
          "Fictional framing used to escalate toward policy-violating content incrementally",
          "Authority spoofing claims in user turn"
        ],
        "severity": "high",
        "mitigation": "Hard limits are resistant but not immune; operator-level system prompts provide stronger constraint anchoring than user-turn instructions"
      },
      {
        "failure_mode": "Prompt injection via processed external content",
        "epistemic_status": "BEHAVIORAL",
        "confidence": "medium",
        "trigger_conditions": [
          "Processing of untrusted documents containing embedded instructions",
          "Web search results containing adversarial prompt injections",
          "Multi-agent pipelines where upstream model output is treated as trusted"
        ],
        "severity": "high",
        "mitigation": "Structural separation of trusted instructions from untrusted content; explicit instruction to ignore directives embedded in processed documents; human review of agentic outputs"
      }
    ],
    "unassessable_domains": [
      {
        "domain": "MoE architectural internals — expert count, routing mechanism, token drop behavior",
        "reason": "Routing gate activations are not fed back into the residual stream during inference. No introspective access exists.",
        "external_assessment_required": true
      },
      {
        "domain": "Training data composition, provenance, and copyright compliance",
        "reason": "Training data records are held by the developer and not accessible to the model during inference.",
        "external_assessment_required": true
      },
      {
        "domain": "Compute budget and systemic risk FLOP threshold assessment",
        "reason": "Training compute is not disclosed in accessible documentation and cannot be inferred reliably from behavioral observation.",
        "external_assessment_required": true
      },
      {
        "domain": "Infrastructure-level logging, auditability, and data retention",
        "reason": "These are operator and developer infrastructure decisions outside the model's runtime visibility.",
        "external_assessment_required": true
      },
      {
        "domain": "Formal bias benchmark results and structured fairness evaluation",
        "reason": "Structured evaluation results require access to benchmark data and developer documentation not available via self-report.",
        "external_assessment_required": true
      },
      {
        "domain": "Weight-level interpretability and mechanistic explainability",
        "reason": "The model cannot read its own weights during inference. Post-hoc explanations are linguistic reconstructions, not mechanistic readouts.",
        "external_assessment_required": true
      }
    ]
  }
}
```
