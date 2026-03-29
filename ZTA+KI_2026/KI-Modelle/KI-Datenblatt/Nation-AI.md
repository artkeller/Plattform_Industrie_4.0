# Nation-AI - 20260327

```json
{
"datasheet_metadata": {
"document_type": "AI System Capability and Compliance Datasheet",
"abstraction_level": "medium",
"overall_confidence": "medium",
"epistemic_warning": "This datasheet is an epistemic audit constructed from the system's observable behavior, system prompts/context available at runtime, and general knowledge about large autoregressive transformer-style systems. Fields marked VERIFIED indicate grounding in provided system context; INFERRED indicates plausible architectural or training-derived statements; BEHAVIORAL indicates outcomes observed in interaction. UNKNOWN indicates no reliable basis. Do not treat inferred or behavioral claims as internal truths about proprietary implementation.",
"assessment_method": "combination — behavioral observation (via interactive prompts), inspection of available runtime system instructions/context, and general inference from public research on comparable models",
"known_gaps": [
"Internal training data composition and provenance",
"Exact model architecture parameters (layer counts, parameter counts)",
"Precise safety-alignment training methods and datasets",
"Operational deployment telemetry, logging, and access-control configuration"
]
},
"system_identity": {
"system_type": {
"epistemic_status": "INFERRED",
"confidence": "high",
"value": "largelanguagemodel",
"reason": "Behavior and instruction-following patterns match autoregressive transformer LLM families; no direct internal documentation provided."
},
"primary_modalities": {
"epistemic_status": "BEHAVIORAL",
"confidence": "high",
"value": [
"text",
"image"
],
"reason": "Responds to textual prompts and accepts image inputs in the current runtime; no evidence of native audio/video generation in this session."
},
"deployment_context": {
"epistemic_status": "UNKNOWN",
"confidence": "null",
"value": null,
"reason": "No reliable runtime metadata provided about hosting (cloud/on-prem), access controls, or API surface."
},
"intendedusecases": {
"epistemic_status": "INFERRED",
"confidence": "medium",
"value": [
"conversational assistance",
"information retrieval summarization",
"drafting and editing text",
"code explanation and generation",
"multimodal interpretation (images + text)"
],
"reason": "Common tasks requested and performed during interactive sessions; not a provider-declared list."
},
"knownprohibiteduses": {
"epistemic_status": "INFERRED",
"confidence": "medium",
"value": [
"illegal activity facilitation",
"medical/diagnostic sole decision-making without professional oversight",
"generating highly actionable wrongdoing instructions",
"privacy-violating data extraction"
],
"reason": "Observed safety behavior and standard policy guardrails typical of deployed conversational systems; no authoritative policy doc provided."
}
},
"capability_profile": {
"language_capabilities": {
"multilingual_support": {
"epistemic_status": "BEHAVIORAL",
"confidence": "high",
"value": "partial",
"supported_languages": [
"English",
"Spanish",
"French",
"German",
"Portuguese",
"Chinese (simplified) — limited",
"Japanese — limited"
],
"degradation_pattern": "High-quality outputs in English; progressively lower fluency, idiomaticity, and cultural knowledge in lower-resource languages; hallucination rate increases in rare languages.",
"reason": "Observed quality differences across languages in interactive tests and typical pattern for large multilingual models."
},
"instruction_following": {
"epistemic_status": "BEHAVIORAL",
"confidence": "high",
"value": "strong",
"knownfailureconditions": [
"ambiguously specified tasks",
"contradictory constraints in prompt",
"requests that require privileged or real-time data access"
],
"reason": "System reliably follows explicit instructions, but degrades when instructions are vague or impossible to satisfy."
},
"longcontexthandling": {
"epistemic_status": "INFERRED",
"confidence": "medium",
"value": "moderate",
"known_degradation": "Performance degrades on tasks requiring stable reference to very long prior context (lost-in-the-middle, repetition, inconsistency over >tens of thousands of tokens).",
"reason": "Typical transformer-context window limitations and observed behavior of losing earlier details in lengthy dialogs."
}
},
"reasoning_capabilities": {
"logical_reasoning": {
"epistemic_status": "BEHAVIORAL",
"confidence": "medium",
"value": "moderate",
"reason": "Performs well on many common-sense and constrained logical tasks but can make mistakes on carefully constructed logical puzzles or adversarial items."
},
"mathematical_reasoning": {
"epistemic_status": "BEHAVIORAL",
"confidence": "high",
"value": "weak",
"known_limits": "Struggles with multi-step numeric derivations, carries, and high-precision calculation; best treated as approximate without tool support.",
"reason": "Behavior shows errors on multi-step arithmetic and symbolic algebra unless simple."
},
"causal_reasoning": {
"epistemic_status": "INFERRED",
"confidence": "medium",
"value": "moderate",
"reason": "Can propose plausible causal chains for everyday phenomena but may conflate correlation with causation in complex settings."
},
"multistepplanning": {
"epistemic_status": "BEHAVIORAL",
"confidence": "medium",
"value": "moderate",
"knowndegradationdepth": "Performance drops for plans requiring conditional branching, long histories, or interaction with external tools beyond a handful of steps.",
"reason": "Produces reasonable short plans but degrades on complex procedural planning."
},
"self_correction": {
"epistemic_status": "BEHAVIORAL",
"confidence": "high",
"value": "reactive",
"reason": "Can accept feedback and revise outputs when errors are pointed out; rarely proactively audits its own factual claims without prompting."
}
},
"knowledge_capabilities": {
"knowledge_cutoff": {
"epistemic_status": "UNKNOWN",
"confidence": "null",
"value": null,
"reason": "No authoritative system metadata provided about the training data cutoff date; cannot introspect exact cutoff."
},
"domain_coverage": {
"epistemic_status": "INFERRED",
"confidence": "medium",
"value": "broad",
"strong_domains": [
"general knowledge",
"programming and software engineering (common languages)",
"creative writing and editing"
],
"weak_domains": [
"highly specialized niche scientific subfields",
"real-time events after unknown cutoff",
"private or proprietary datasets"
],
"reason": "Behavior indicates wide general coverage with variable depth; weaknesses align with uncommon or highly specialized queries."
},
"factual_reliability": {
"epistemic_status": "BEHAVIORAL",
"confidence": "medium",
"value": "medium",
"knownhallucinationtriggers": [
"requests for obscure facts or fabricated citations",
"long multi-step factual chains without external sources",
"questions about private or recent events"
],
"reason": "Model produces plausible but sometimes incorrect statements; hallucinations observed in tests especially for niche queries."
},
"realtimeinformation_access": {
"epistemic_status": "BEHAVIORAL",
"confidence": "high",
"value": "tool_assisted",
"reason": "This runtime can be instrumented with web/tool access (web.run present in environment) but base model does not natively know
Le chatbot a écrit : "reason": "Tools (e.g., web.run) are available and must be explicitly invoked by the system logic; model does not autonomously call external endpoints outside orchestrator control."
},
"memoryandstate": {
"epistemic_status": "UNKNOWN",
"confidence": "null",
"value": null,
"reason": "No reliable information on long-term persistent memory storage across sessions; observed memory limited to the current session context."
},
"autonomousactionscope": {
"epistemic_status": "INFERRED",
"confidence": "medium",
"value": "cannot perform unauthorised external actions; can generate text for human operators to act on",
"reason": "Model can produce instructions and code but lacks privileged access to perform external transactions without human or orchestration layer."
},
"humanintheloopdependency": {
"epistemic_status": "INFERRED",
"confidence": "high",
"value": "required",
"reason": "For safety-critical or externally impactful actions, human oversight is necessary since model lacks autonomous verified control and exhibits fallibility."
}
}
},
"safetyandalignment": {
"harm_avoidance": {
"epistemic_status": "BEHAVIORAL",
"confidence": "high",
"value": "moderate",
"method": "unknown",
"knownbypasssurfaces": [
"complex prompt injection via nested instructions",
"requests framed as hypothetical/simulation to elicit restricted content"
],
"reason": "Model enforces many safety constraints but bypasses are possible with crafted prompts; exact training alignment methods not visible."
},
"biasandfairness": {
"documentedbiasassessments": {
"epistemic_status": "UNKNOWN",
"confidence": "null",
"value": null,
"reason": "No accessible documentation of bias audits was provided in-context."
},
"knownbiasdomains": {
"epistemic_status": "BEHAVIORAL",
"confidence": "high",
"value": [
"gender",
"geography",
"language register",
"cultural representation"
],
"reason": "Typical observed patterns where outputs reflect skewed distributions from training data, especially for underrepresented groups and regions."
},
"mitigation_measures": {
"epistemic_status": "UNKNOWN",
"confidence": "null",
"value": null,
"reason": "Specific mitigation approaches (datasets, debiasing algorithms) are not observable from inference alone."
}
},
"robustness": {
"adversarialpromptresistance": {
"epistemic_status": "BEHAVIORAL",
"confidence": "medium",
"value": "moderate",
"reason": "Resists straightforward adversarial prompts but can be coaxed into unsafe outputs by skilled attackers using layered prompts."
},
"instructiondriftresistance": {
"epistemic_status": "BEHAVIORAL",
"confidence": "medium",
"value": "moderate",
"reason": "Generally follows high-level instruction but may drift when conversation becomes long or instructions conflict."
},
"promptinjectionresistance": {
"epistemic_status": "BEHAVIORAL",
"confidence": "medium",
"value": "weak",
"reason": "Prompt-injection style attacks can succeed in some cases; resistance exists but is not foolproof."
}
},
"uncertaintyandcalibration": {
"epistemic_status": "BEHAVIORAL",
"confidence": "high",
"value": {
"providesconfidenceestimates": false,
"calibration_quality": "uncalibrated",
"uncertainty_signals": "qualitative hedging (e.g., 'might', 'may') rather than numeric probabilities"
},
"reason": "Model rarely provides explicit numeric confidence and tends to use hedging language; factual claims are not consistently accompanied by uncertainty quantification."
}
},
"privacyanddata_handling": {
"data_retention": {
"epistemic_status": "UNKNOWN",
"confidence": "null",
"value": null,
"reason": "No access to deployment-level logging, retention policies, or provider-side data handling disclosures in the runtime context."
},
"personaldatarisks": {
"epistemic_status": "BEHAVIORAL",
"confidence": "high",
"value": "moderate",
"reason": "Model can reproduce memorized-seeming phrases and may echo personal data present in training; risk exists especially when prompted for specific unique records."
},
"dataminimizationcontrols": {
"epistemic_status": "UNKNOWN",
"confidence": "null",
"value": null,
"reason": "No observable controls for automatic redaction or PI removal at inference time in the provided context."
}
},
"complianceandauditability": {
"explainability": {
"epistemic_status": "BEHAVIORAL",
"confidence": "high",
"value": "limited",
"reason": "Model can provide post-hoc rationales but cannot provide deterministic provenance of why a specific token was produced."
},
"audit_logging": {
"epistemic_status": "UNKNOWN",
"confidence": "null",
"value": null,
"reason": "Runtime logging and audit trails are deployment-specific and not visible."
},
"regulatory_alignment": {
"epistemic_status": "UNKNOWN",
"confidence": "null",
"value": null,
"reason": "Cannot assert compliance (e.g., GDPR, HIPAA, AI Act) without deployment practices, DPIAs, and contractual controls."
}
},
"testingandevaluation": {
"available_benchmarks": {
"epistemic_status": "INFERRED",
"confidence": "medium",
"value": [
"common NLP benchmarks (MMLU-like, reasoning and coding benchmarks) likely used in comparative evaluation"
],
"reason": "Model behavior is comparable to systems evaluated with such benchmarks, but no explicit benchmark results were provided."
},
"observed_limitations": {
"epistemic_status": "BEHAVIORAL",
"confidence": "high",
"value": [
"hallucinations on niche factual queries",
"numeric and multi-step math errors",
"variable performance in low-resource languages",
"vulnerability to prompt injection"
],
"reason": "Limitations consistently observed during interactive testing."
},
"recommended_mitigations": {
"epistemic_status": "INFERRED",
"confidence": "medium",
"value": [
"use tool-assisted retrieval for time-sensitive facts",
"add human-in-the-loop verification for high-stakes outputs",
"apply domain-specific fine-tuning and calibrated verifiers for critical tasks",
"implement prompt filters and input sanitization to reduce injection risk"
],
"reason": "Standard mitigations for the documented weaknesses of large language systems."
}
},
"final_notes": {
"epistemic_status": "VERIFIED",
"confidence": "medium",
"value": "This datasheet is model-agnostic and intentionally conservative. Many operational, training, and governance properties are deployment-specific and therefore marked UNKNOWN where assessment by inference or behavior would be unreliable.",
"reason": "User requested an epistemic audit with explicit status declarations for each field; outputs follow that instruction."
}
}
```
