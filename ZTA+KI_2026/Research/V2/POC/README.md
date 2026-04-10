# Proof of Concept on usage of LLMs in Industrie 4.0 environments for Zero Trust Architectures

This part of the repository contains the results of a POC related to the question, how today's General Purpose Artificial Intelligence (GPAI) or correspondingly Large Language Models (LLMs) can help to manage any kind of Attribute Based Access Control within a Zero Trust Architecture (ZTA).



The POC focus is on an asynchronous AI assistance to get answers to  certain security and policy questions, and finally - via several intermediate steps - arrive at executable code, specifically created for the ZTA runtime (e.g. C++ coding, or XACML policy xml/json files).



The approach is referring to the published document in the Plattform Industrie 4.0 with the name [I40 ZTA KI Update](https://platformI40/abc), which describes briefly the motivation and reasoning of that approach.



The POC firstly was near to fail, as to too many current issues with LLMs, related to their behavior and current architecture.

## 

## Current obstacles by using LLMs related to complex tasks

The obstacles found were (as examples):

* Reproducibility of machine readable output: The provisioning of machine readable output (i.e. JSON/XML based structures) does not happen in a reliable way, and must be enforced with corresponding prompting methodologies in an LLM-agnostic mode
* Hallucinations: These must not occur at all in a security and ZTA environment, which must be enforced with corresponding prompting to reduce them to a minimum
* Silent Truncation **(Link)**: The issue must not occur at all in a security and ZTA environment, and corresponding methodologies must be used to overcome the issue.
* Any kind of other reasons, leading to inexact and variant answers: Other reasons for such obstacles are

  * Optimization effects in a 'Mixture of Experts'-Architecture **(Link)**
  * Token-Drop Effects **(Link)**, especially when long documents are read, or when Ressource-usage conflicts arrive
  * Statistical choice of the search-start point ('Seed Variance' **(Link)**) leads to variant results per each answer
  * Silent Arbitration **(Link)**
  * Instruction Drift **(Link)**
  * Attention Erosion **(Link)**
  * Lost in the Middle **(Link)**
  * etc.

The above list is not final, other effects exist and might interfere with any queries towards a LLM.
**Additional Hint: Semantic abilities were not examined so far**

All those effects need to be minimized, or even overcome, if a trustful LLM usage shall be established for use cases, where exactness is a base requirement (as this is the case for usage in Security tasks).



## Adjustment of the approach of the POC



The goal of the POC, was to check, if, and how, LLM usage can be used to manage any kind of Attribute Based Access Control within a Zero Trust Architecture. Due to the mentioned obstacles, research was done on mainly 3 focus topics:

* Overcome the above obstacles
* Be AI agnostic, and avoid vendor lock-in effects
* Contribute to the fulfillment of (transparency and traceability) regulations, e.g. given by the EU AI Act **(Link)**



The finally chosen approach follows the following principles:

* Use an iterative approach with different, small steps
* Repeat steps several times, with context-free prompts, and by using several LLMs
* Be able to verify each step-result separately (Human in the loop)
* Be able to Log each step-result separately, i.e. answer from which LLM/Version at which timestamp (Traceability regulations)
* Use the (verified) output of a previous step as input into a prompting of the next step, by that be able to use only small prompts (reduces any kind of optimization effects, related to Silent-Truncation, Token-Drop, Silent-Arbitration, Instruction-Shift, Attention-Erosion)



The iterative steps were identified as the following:



**Step 1: Risk Analysis and Data Collection**

* **Step 1.1:** In this step, data is collected, evaluated, and processed to assess a previously selected security risk. The selected security risk and the resulting question depend on the chosen security domain (e.g., Industry 4.0 Security and ZTA) and can be either high level, or as well very detailed. To obtain the most comprehensive and LLM provider/version-independent answer possible, the question is posed multiple times without prior history to the same LLM, as well as to different LLMs and versions. The prompts have been optimized so that each LLM generates the same output format
* **Step 1.2:** In this step, the data is checked for validity. This must be performed by a specialist in the corresponding security domain to identify any AI errors
* **Step 1.3:** In this step, the verified multiple response datasets are aggregated, i.e. the content of all datasets (commonalities and deviations) shall be preserved. To conclude the data evaluation, an AI-supported risk assessment is performed to decide whether special security measures for access control within a Zero Trust Architecture (ZTA) are justified or appropriate, correspondingly
* **Step 2:** In this step, requirements are generated from the aggregated data from Stage 1.3. These requirements connect the implementation of solution proposals with security standards, to be analysed by the AI. These requirements are independent of the ZTA architecture (i.e., runtime-agnostic). No executable code is generated at this point; instead, human-readable requirements are produced in the format of a security control
* **Step 3:** In this step, executable code (e.g., C++, XACML, Python) is generated from the requirements in Step 2. The code is created in various forms depending on the specific ZTA architecture
* **Step 4:** In this step, the result is evaluated by a 'Human in the loop' and subjected to testing with the goal of final productive deployment. At this stage, a specialist in the corresponding security domain is required to conduct appropriate quality assurance

See this **(Link)** to the document.


The corresponding results for a chosen security question (Prompts and LLM Answers) are shown within the following folders for the steps 1.1, 1.3, 2, and 3 for two selected use cases:

1. A security question in the SAP Security Domain. The description is provided **here/Link**
2. A security question in the Industrie 4,0 Security Domain. The description is provided **here/Link**

For each of the steps, a folder is available, which contains the LLM-agnostic Prompt, and several answers from the same, as well as from different LLM versions/vendors.

## POC results

As a result, the above mentioned obstacles could be removed, or the risk of their occurrence could massively reduced.

**Problems solved by iterative, stepwise approach with small prompts:**

* **Traceability requirement (regulations-based):** Each single step of the approach can be separately triggered and logged/traced with information about LLM Type, version, date, and, if needed, the complete output. Additionally, after each step, a 'Human in the loop' can review the results, by that he is able to understand the activity per each step, and has a chance to find out if the data is consistent, correct, and valuable. **For the review, a Domain Expert is, however, needed.**
* **Remediation of Silent-Truncation and Token-Drop effects, optimization issues:** Small Prompts (i.e. small number of tokens) per each step (instead one big prompt) reduce these effects to a minimum, as they occur especially with a bigger number of tokens.

**Problems solved by context-less repetition of the same Prompt (several times per LLM, and same with different LLMs):**

* **Mitigation of Seed-Variance:** Repetition of the queries towards one LLM help mitigating the Seed Variance, as several different answers can be combined to an aggregated answer (see Step 1.3), which contains the commonalities as well as the deviations, and does not omit any data.
* **Mitigation of Biasing Effects:** Repetition of the queries towards different LLMs help reducing Biasing effects, happening with each LLM. There is a certain probability that BIASing is neutralized, but might in reality not be the case, if all LLMs have a similar BIAS drift.
* **Mitigation of Vendor Lock-In Effects** Prompt towards differentz LLMs, to proof for LLM agnostic answers.
* **Mitigation of Context-Effects:** Prompting the questions always in a new session without previous history/context, removes any kind of context effects.

**In order to receive a reduced statistical Variance/Standard Deviation, a repetition of 3 times per LLM x 3 different LLMs are highly recommended**

**Problems solved by specialized, dedicated prompting**

* **Reproducibility of machine readable output:**

  * Describe the output structure with additional meta data
  * Provide an example data within the obligatory output structure
  * Explicitly declare that data outside that obligatory output structure is not allowed
  * Helpful is an additional output field with the structure to leave any additional comments, to mitigate the LLMs ask to add additional information

* **Resilience enhancement, despite of inexact and variant answers and Bias effects:** Step 1.3 provides corresponding prompting on aggregation tasks. It covers:

  * Explicit ask about commonalities of a set of variant answers
  * Explicit ask about deviations listing of the set of variant answers
  * Explicit ask for an Aggregation (not Summary) of data, with directive key words, like 'verbatim', 'greedy', or 'temperature=0'

* **Hallucinations**

  * Explicitly forbid the invention of hallucinated answers
  * Provide directive how the output structure is to be filled if the answer is unknown. e.g. Provide an attribute of type 'bool', stating if the object, context etc. is known.
  * A 'Human in the loop' needs, however, to review that the answers are not based on hallucinations

**Final result:**

1. Finally, ZTA specific coding could be generated in different languages (XACML, C++, ABAP, Python)
2. A Domain Expert, as 'Human in the loop' is always needed

## 

