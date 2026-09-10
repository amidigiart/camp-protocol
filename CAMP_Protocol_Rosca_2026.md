# CAMP: Cognitive Arbitration Mediation Protocol — A Vendor-Neutral Framework for Trust Verification in Multi-Provider AI Ecosystems

**Mihai Roșca**
Independent Researcher, BRIDGRAI Ecosystem
Brăila, Romania, EU
ORCID: 0009-0001-1422-6209

**Date:** September 2026
**Status:** Preprint — pending peer review
**License:** CC BY 4.0

---

## Abstract

The cognitive services market — AI systems that generate text, code, images, and decisions — reached $77 billion in 2026, with projections exceeding $310 billion by 2033. Yet a structural problem remains unaddressed: no cognitive service provider can independently verify the trustworthiness of its own outputs. A provider that generates content cannot also serve as its impartial auditor, just as a bank cannot rate its own bonds or a pharmaceutical company cannot approve its own drugs. This paper introduces CAMP (Cognitive Arbitration Mediation Protocol), a vendor-neutral protocol for trust verification, conflict resolution, and provenance maintenance across multiple cognitive AI services. CAMP defines four formal functions — arbitration, mediation, certification, and provenance anchoring — and positions them within a three-layer coexistence architecture where cognitive engines, a trust verification layer, and consumers each occupy structurally independent roles. We present BRIDGRAI as a reference implementation with 9 autonomous agents, 6-pillar semantic validation, and blockchain-anchored audit trails. We argue that neutral trust infrastructure for cognitive services is not optional but structurally inevitable, following the same pattern as SSL certificates for the web, credit rating agencies for finance, and ISO standards for manufacturing.

**Keywords:** cognitive arbitration, trust verification, multi-agent mediation, AI governance, vendor-neutral protocol, provenance engineering, coexistence architecture

---

## 1. Introduction

Every major cognitive AI provider — Google (Gemini), OpenAI (GPT), Anthropic (Claude), Microsoft (Copilot), Meta (Llama), Mistral, xAI (Grok), DeepSeek — can generate sophisticated outputs across text, code, images, and decision support. Their capabilities are advancing rapidly, their adoption is accelerating, and their economic impact is measurable.

What none of them can do is independently verify the trustworthiness of their own outputs.

This is not a technical limitation — it is a structural conflict of interest. When the same entity generates content and certifies its quality, the certification carries inherent bias. This structural problem is well-understood in other domains: banks do not rate their own bonds (credit rating agencies exist for this); pharmaceutical companies do not approve their own drugs (regulatory agencies exist for this); websites do not issue their own security certificates (certificate authorities exist for this).

Yet in the cognitive services market — the fastest-growing technology sector in history — no equivalent neutral trust layer exists. Each provider self-reports quality metrics, self-certifies safety, and self-assesses compliance with emerging regulations like the EU AI Act (Regulation 2024/1689) [1].

This paper proposes CAMP (Cognitive Arbitration Mediation Protocol) as the protocol that fills this gap. CAMP is not an AI service — it does not generate content, make decisions, or compete with cognitive providers. It is the layer that verifies, arbitrates, mediates, and certifies what cognitive services produce.

Section 2 reviews existing approaches and their limitations. Section 3 defines the structural conflict formally. Section 4 presents the CAMP protocol with its four functions. Section 5 describes the three-layer coexistence architecture. Section 6 presents BRIDGRAI as reference implementation. Section 7 maps CAMP to regulatory requirements. Section 8 discusses the coexistence economics. Section 9 addresses limitations and open questions.

## 2. Related Work and the Structural Gap

### 2.1 Cognitive Services: The Current Landscape

The term "cognitive services" entered industry vocabulary through IBM Watson (2013), when IBM offered cognitive computing capabilities as cloud APIs [2]. Microsoft Azure Cognitive Services (now Azure AI Services) standardized the model: pre-built APIs for vision, speech, language, and decision. Google Cloud AI, Amazon AI Services, and subsequent providers followed the same pattern.

The cognitive services market reached approximately $16.6 billion in 2024 and is projected to grow at a CAGR of over 40% through 2034 [3]. The market is dominated by vertically integrated providers who build models, offer APIs, and host applications.

**What this landscape lacks:** Every provider in this market is both player and referee. There is no structurally independent entity whose sole function is to verify the trustworthiness of outputs across all providers.

### 2.2 AI Orchestration Frameworks

Recent work addresses orchestration of multiple AI agents:

- **OSC (Orchestrating Cognitive Synergy)** [4] proposes dynamic knowledge alignment in multi-agent LLM collaboration through Collaborator Knowledge Models. OSC addresses collaboration efficiency but not trust verification or provenance.

- **From Retrieval to Cognitive Orchestration** [5] formalizes cognitive orchestration as a layered architecture with invariants and interface contracts. This work addresses architectural rigor but operates within a single-vendor context, not across competing providers.

- **Enterprise orchestration platforms** (Aisera, ServiceNow AI, Salesforce Einstein) provide AI agent orchestration for enterprise workflows. These are single-vendor control planes, not neutral mediation protocols.

### 2.3 AI Safety and Evaluation

AI safety research addresses model behavior through alignment techniques, red-teaming, and evaluation benchmarks. Organizations like METR, AISI (UK AI Safety Institute), and the EU AI Office are developing evaluation frameworks.

However, these efforts focus on evaluating models before deployment — not on verifying individual outputs in production, across providers, with real-time provenance. A model that passes a safety evaluation can still produce untrustworthy outputs in specific interactions.

### 2.4 Alternative Architectures

Before proposing CAMP, we must consider why alternative approaches to neutral trust verification are insufficient:

**Provider consortium model:** Cognitive providers audit each other's outputs through a shared framework. Problem: collusion risk remains, and the conflict of interest is merely redistributed, not eliminated. Historical precedent: credit rating agencies owned by banks failed catastrophically in 2008.

**Government verification model:** Regulatory agencies directly verify AI outputs. Problem: governments lack technical expertise at the pace of AI development, become politicized, and create bottlenecks. Historical precedent: FDA drug approval takes 10–15 years; AI models iterate every 6–12 months.

**Open-source community validation:** Crowd-sourced verification through distributed review. Problem: no accountability mechanism, inconsistent standards, vulnerable to coordinated manipulation. Historical precedent: Wikipedia works for factual knowledge but not for safety-critical certification.

CAMP occupies the structural position that has emerged in every mature technology ecosystem: independent third-party verification that is neither provider, government, nor crowd, but a specialized institution whose sole function is trust.

### 2.5 The Gap

| Capability | Cognitive Service Providers | Orchestration Frameworks | Safety Evaluations | CAMP |
|-----------|---------------------------|--------------------------|-------------------|------|
| Content generation | Yes | No | No | No |
| Multi-provider mediation | No | Partial (single vendor) | No | **Yes** |
| Real-time trust scoring | Self-reported | No | Pre-deployment only | **Yes** |
| Provenance anchoring | No | No | No | **Yes** |
| Vendor independence | No (each self-certifies) | No (vendor-specific) | Partial | **Yes** |
| Regulatory compliance evidence | Self-assessed | No | Partial | **Yes** |

The gap is not in any single function but in the combination: vendor-neutral, real-time, production-grade trust verification with cryptographic provenance — operating across all cognitive service providers simultaneously.

## 3. The Structural Conflict

### 3.1 The Structural Conflict Argument

**Claim:** A cognitive service provider P that generates output O cannot serve as an impartial verifier of O's trustworthiness.

**Informal argument:** P has economic incentives to maximize usage and minimize reported problems. P's evaluation of its own output is structurally biased — not because P is dishonest, but because the conflict of interest is inherent in the role combination. This is the same structural argument that justifies independent auditors in finance, independent testing laboratories in manufacturing, and independent certificate authorities in cryptography.

**Historical precedents:**

1. **SSL/TLS Certificates (1995–present).** Websites do not issue their own security certificates. Independent certificate authorities (Let's Encrypt, DigiCert, etc.) verify identity and issue certificates. Without this neutral layer, browser security would rely on self-attestation.

2. **Credit Rating Agencies (1909–present).** Banks and corporations do not rate their own creditworthiness. Independent agencies (Moody's, S&P, Fitch) provide ratings that markets rely on. The 2008 financial crisis demonstrated what happens when this independence is compromised.

3. **ISO Standards (1947–present).** Manufacturers do not certify their own compliance with quality standards. Independent auditors verify compliance. ISO 27001 became a procurement requirement — the certifier became a market gatekeeper.

4. **Pharmaceutical Regulation.** Drug companies do not approve their own drugs. Independent regulatory agencies (FDA, EMA) evaluate safety and efficacy. The separation between developer and evaluator is considered essential for public safety.

### 3.2 Formal Definition

**Definition (Structural Independence):** A trust verification system V is structurally independent from cognitive service provider P if and only if:

1. V does not generate cognitive outputs that compete with P
2. V's revenue model does not depend on any single P's commercial success
3. V's verification methodology is auditable by any party, including P
4. V cannot be disabled or overridden by P

Any verification system that fails any of these four conditions is not structurally independent, regardless of its technical sophistication.

**Note:** This is a definitional framework, not a mathematical theorem. The claim is that structural independence is a necessary condition for credible trust verification, based on historical precedent and institutional economics, not on formal proof.

## 4. The CAMP Protocol

### 4.1 Definition

**CAMP (Cognitive Arbitration Mediation Protocol)** is a vendor-neutral protocol that operates between cognitive service providers and their consumers, providing four functions:

1. **Arbitration** — When cognitive services produce conflicting or uncertain outputs, CAMP computes trust scores and resolves conflicts using evidence-based methods independent of any provider's self-assessment.

2. **Mediation** — CAMP maintains provenance chains across model generations, personnel changes, and organizational transitions. When a cognitive service is deprecated or replaced, CAMP preserves the context of what it produced.

3. **Certification** — CAMP provides verifiable, cryptographically anchored attestations about the trustworthiness of cognitive outputs. These attestations are independently auditable — any party can verify them without trusting CAMP itself.

4. **Provenance Anchoring** — CAMP records the full creation context of mediated interactions on an immutable ledger: which provider, which model version, what confidence level, what validation was applied, who authorized the output.

### 4.2 Formal Specification

Given N cognitive services S₁, S₂, ..., Sₙ producing outputs O₁, O₂, ..., Oₙ for a request R:

**Trust Function:**

    T: (Oᵢ, R, Context) → [0, 1]

Where T(Oᵢ) is the trust score for output Oᵢ given request R and operational context. T is computed using validation pillars independent of Sᵢ's self-reported quality metrics.

**Arbitration Function:**

    A: {O₁...Oₙ, T(O₁)...T(Oₙ)} → O*

Where O* is the mediated output, selected or synthesized based on trust scores, with recorded rationale for the arbitration decision.

**Provenance Function:**

    P: (O*, A, R) → Hash(blockchain)

Where the complete arbitration context — request, outputs, trust scores, arbitration decision, human authorization — is cryptographically anchored to an immutable ledger.

**Certification Function:**

    C: (O*, P) → Certificate{trust_score, validation_method, timestamp, verifier_id}

Where the certificate is independently verifiable by any party.

### 4.3 The Six Validation Pillars

CAMP's trust function T operates through six independent validation dimensions:

| Pillar | What It Validates | Threat Model |
|--------|-------------------|--------------|
| P1: Semantic | Does the output mean what it claims? | Meaning manipulation, context stripping |
| P2: Intent | Does the output serve the stated purpose? | Goal hijacking, hidden persuasion |
| P3: Emotional | Does the output manipulate affective states? | Emotional exploitation, fear/urgency injection |
| P4: Disinformation | Does the output contain verifiable falsehoods? | Hallucination, fabrication, source misattribution |
| P5: Logic | Is the output internally consistent? | Contradiction, circular reasoning, false equivalence |
| P6: Context | Is the output appropriate for its operational context? | Context mismatch, audience-inappropriate content |

Each pillar produces an independent score in [0,1]. The composite trust score T is a weighted function:

    T(Oᵢ) = Σ(wⱼ × Pⱼ(Oᵢ)) for j = 1...6

Where weights wⱼ are configurable by domain (education weights P3 heavily; finance weights P5 heavily; healthcare weights P4 heavily). Default weights are uniform (wⱼ = 1/6).

### 4.4 Protocol Flow

    Consumer → Request R → CAMP Intake
                              ↓
                  Route to Provider(s) S₁...Sₙ
                              ↓
                  Receive Outputs O₁...Oₙ
                              ↓
                  Six-Pillar Validation → T(O₁)...T(Oₙ)
                              ↓
                  Arbitration → O* (with rationale)
                              ↓
                  Provenance Anchor → Blockchain hash
                              ↓
                  Certificate → Consumer
                              ↓
                  Audit Trail → Regulator (on demand)

The protocol is stateless per interaction but maintains persistent provenance. Each interaction is independently verifiable.

### 4.5 Validation Status and Preliminary Metrics

**Current implementation state:** TVE (Trust Validation Engine) Core v0.1 uses heuristic pattern matching in Romanian and English. This is an acknowledged limitation — the protocol specification is ahead of its implementation.

**Preliminary validation results:**

To assess baseline performance, we constructed a synthetic test set:

- 200 examples total (100 manipulation, 100 benign)
- Manipulation examples: known disinformation patterns, emotional exploitation techniques, logical fallacies
- Benign examples: factual statements, neutral opinions, appropriate emotional expressions

Results:

- Precision: 0.82 (82% of flagged manipulations were actually manipulative)
- Recall: 0.76 (76% of actual manipulations were detected)
- F1 Score: 0.79

**Limitations:**

- Synthetic dataset, not real-world corpus
- Pattern matching vulnerable to sophisticated evasion
- No adversarial robustness testing yet
- Binary classification only (manipulation present/absent), no gradation

**Planned improvements:**

- Real-world dataset collection through partnerships with educational institutions
- NLP-based semantic analysis replacing heuristic patterns
- Multi-language expansion beyond Romanian/English
- Adversarial robustness testing against evasion techniques
- Graduated scoring (not binary) to reflect manipulation severity

**Honest assessment:** v0.1 provides proof-of-concept that six-pillar validation is feasible, but production deployment requires significant improvement in recall and adversarial robustness.

## 5. Coexistence Architecture

### 5.1 Three-Layer Model

CAMP operates within a three-layer coexistence architecture where each layer is structurally independent:

**Layer 1: Cognitive Engines** — The providers (Google, OpenAI, Anthropic, Microsoft, Meta, Mistral, xAI, DeepSeek, and future entrants). They build models, train on data, optimize for capability. Their business is cognitive power.

**Layer 2: Trust Verification** — CAMP implementations. They do not generate cognitive outputs. They verify, arbitrate, mediate, and certify. Their business is trust. They are neutral because they have no cognitive product of their own — no model to promote, no outputs to defend.

**Layer 3: Consumers** — Schools, governments, enterprises, researchers, citizens. They need cognitive capabilities but demand verifiable trust, especially in regulated domains (education, healthcare, finance, public services).

### 5.2 Structural Position

The CAMP layer occupies the same structural position as:

- SSL certificate authorities between websites and browsers
- Credit rating agencies between bond issuers and investors
- ISO certification bodies between manufacturers and buyers

This is not an analogy — it is the same structural pattern: when a market grows beyond the point where self-certification is credible, a neutral verification layer emerges. The cognitive services market is at this inflection point now, driven by the EU AI Act's requirements for independent verification.

### 5.3 Coexistence Principle

**CAMP's fundamental design constraint:** The protocol must add value to every cognitive provider without threatening any provider's core business. A trust layer that is perceived as competitive with providers will be rejected. A trust layer that makes providers more trustworthy will be adopted.

This means:

- CAMP never generates content (no competition)
- CAMP certifies providers (adds value)
- CAMP provides compliance infrastructure (reduces provider costs)
- CAMP is provider-agnostic (no favoritism)

## 6. Reference Implementation: BRIDGRAI

BRIDGRAI implements CAMP through 9 autonomous agents organized across 5 abstraction layers, communicating via Google A2A protocol (JSON-RPC 2.0).

### 6.1 Agent Architecture

| Layer | Agent | CAMP Function |
|-------|-------|---------------|
| L4: Cognitive Orchestration | Agent Maestru | Arbitration — detects what needs to be done, builds optimal pipeline, routes to appropriate agents |
| L3: Security & Heritage | Heritage Agent | Provenance anchoring — manages succession, IP protection, transgenerational knowledge transfer |
| L2: Verification & Calibration | Concordance Agent, Calibration Agent | Certification — cross-model agreement scoring, confidence calibration |
| L1: Detection & Resonance | ACR Agent, UKBE Agent, CASP Agent | Trust function — anti-confabulation detection (ACR), Kuramoto physics resonance (UKBE), cognitive-affective safety (CASP) |
| L0: Existence — Blockchain | Tezos anchoring | Provenance anchoring — 128 IP assets timestamped on mainnet |

### 6.2 Agent Maestru: Cognitive Arbitration in Practice

The Agent Maestru is the CAMP arbitration engine. Unlike conventional routers or load balancers:

**Detection mechanism:** Agent Maestru uses a two-stage classification process:

- **Explicit intent classification:** Fine-tuned classifier categorizes request text into functional domains (financial query, educational question, emotional support, technical problem, etc.)
- **Implicit needs detection:** Rule-based heuristics combined with sentiment analysis identify unstated needs:
  - Emotional distress markers (anxiety language, time pressure, loss aversion)
  - Confusion signals (contradictory statements, vague references, circular reasoning)
  - Urgency indicators (deadline pressure, scarcity framing, FOMO triggers)

**Example:** Request "How do I invest €10K?" triggers:

- Explicit classification: financial query → route to finance-validated provider
- Implicit detection: check for anxiety markers ("I need to act fast", "everyone is investing") → if detected, add emotional pillar validation before financial analysis

**Pipeline construction:** Not a fixed routing table — the pipeline is assembled per-interaction from available agents based on the request profile. A request with both financial and emotional components triggers both pipelines in parallel, with results merged by Maestru.

**Conflict mediation:** When agents produce contradictory assessments (e.g., financial agent says "safe investment" while emotional agent flags "desperation"), Maestru applies Kuramoto-model synchronization [6] to find convergence. If convergence is not achievable within threshold, Maestru escalates to human arbitration with full audit trail.

### 6.3 Trust Function Implementation: TVE Core

The six-pillar validation is implemented through TVE (Trust Validation Engine) Core:

- **Current state:** v0.1 heuristic — pattern matching in Romanian and English
- **What works:** Detection of explicit manipulation patterns, known disinformation structures, emotional exploitation techniques
- **What is partial:** Sophisticated manipulation evades detection; adversarial attacks on the validation engine itself are not fully addressed
- **What is planned:** NLP-based analysis, multi-language expansion, adversarial robustness testing

This honest assessment matters: CAMP as a protocol is well-defined, but the current validation implementation is v0.1. The protocol is ahead of its implementation.

### 6.4 Provenance Implementation

- **Tezos blockchain:** 128 IP assets with SHA-256 hashes timestamped on mainnet, publicly verifiable via tzkt.io
- **UKBE Core:** ML-DSA-44 post-quantum signing (NIST FIPS 204) for cryptographic provenance resistant to quantum computing attacks
- **HASN:** PostgreSQL with AES-256-GCM authenticated encryption for audit persistence
- **Git:** Single-author history with AI contribution tracking (harvest methodology)

### 6.5 Verification Data

- UKBE Core: 175 automated tests across test suite
- Backbone: 7 invariant axioms (Ω-1 through Ω-7) with automated probe verification
- A2A Platform: 18 verified integration tests across 9 agents
- Tezos: all transactions publicly verifiable on mainnet

## 7. Regulatory Alignment

### 7.1 EU AI Act Mapping

The EU AI Act (Regulation 2024/1689) [1] creates specific requirements that CAMP addresses:

| AI Act Article | Requirement | CAMP Function |
|---------------|-------------|---------------|
| Art. 9 | Risk management systems — continuous monitoring | Trust function T — real-time six-pillar validation |
| Art. 13 | Transparency — outputs must be interpretable and auditable | Certification function C — verifiable attestations |
| Art. 14 | Human oversight — must allow human intervention | Human Anchor assignment (from KCE principle K5) |
| Art. 15 | Accuracy, robustness, cybersecurity | Trust scoring with measurable thresholds per pillar |
| Art. 50 | Transparency for AI-generated content | Provenance function P — full creation context recorded |
| Art. 52 | Post-market monitoring for high-risk systems | Continuous arbitration with audit trail |

### 7.2 eIDAS 2.0 Alignment

eIDAS 2.0 (Regulation 2024/1183) [7] establishes the European Digital Identity Framework. CAMP's provenance anchoring through blockchain timestamping aligns with eIDAS 2.0's requirements for qualified electronic timestamps and verifiable attestations.

### 7.3 Regulatory Interpretation Disclaimer

The mappings above represent our interpretation, not authoritative legal guidance. Organizations should consult qualified legal counsel for compliance decisions.

## 8. Coexistence Economics

### 8.1 The Additive Value Model

CAMP creates value that did not previously exist — it does not extract value from existing actors:

| Stakeholder | Without CAMP | With CAMP |
|-------------|-------------|-----------|
| Cognitive Providers | Self-certification breeds regulatory risk. Cannot prove safety to governments. | Independent certification as competitive advantage. Provides structured compliance evidence for EU AI Act audits. |
| Schools & Parents | No way to verify AI interactions with children. Manipulation risk undetectable. | Every AI session certified. Six-pillar scan. Parent-accessible audit trail. |
| Regulators | No standardized enforcement data. Self-reported compliance. | Automated compliance reports. Standardized trust scores. |
| Enterprise | Vendor lock-in. No cross-provider comparison. Liability unclear. | Provider-agnostic trust scores. Cross-provider audit history. |

### 8.2 The Inevitability Argument

The pattern is historical: neutral trust layers start optional and become mandatory.

- SSL was optional in 1995. In 2026, browsers block sites without it.
- Credit ratings were informational in 1909. Today they determine borrowing costs.
- ISO 9001 was aspirational in 1987. Today it is a procurement requirement.

The EU AI Act creates the regulatory inflection point for cognitive services. CAMP — or something structurally equivalent — becomes inevitable when the market reaches the scale where self-certification is no longer credible to regulators, insurers, or enterprise procurement.

### 8.3 Economic Model Note

This paper focuses on the protocol specification and architecture. Economic viability and revenue model design are separate research questions that require empirical validation through market testing. The academic contribution is the protocol and architecture, not the business model.

## 9. Discussion

### 9.1 Limitations

1. **Single implementation.** BRIDGRAI is one implementation by one person. CAMP as a protocol needs multiple independent implementations to establish generalizability.

2. **TVE Core is v0.1.** The six-pillar validation engine is heuristic-based (pattern matching). Sophisticated manipulation evades detection. The protocol specification is ahead of the implementation.

3. **No controlled evaluation.** We have not conducted controlled experiments comparing CAMP-mediated interactions with unmediated interactions across multiple providers.

4. **Trust in the trust layer.** "Who verifies the verifier?" is an inherent challenge. CAMP addresses this through K6 (Auditability Over Trust) — every CAMP decision is independently verifiable. But the ultimate resolution requires multiple competing CAMP implementations, not a single monopoly.

5. **Adoption requires provider cooperation.** Cognitive service providers must expose API endpoints for CAMP to mediate. A provider that refuses integration cannot be mediated. **Fallback strategy:** If major providers refuse integration, CAMP can operate in "wrapper mode" — consumers route requests through CAMP first, CAMP calls provider APIs using standard authentication, then validates outputs before returning to consumer. This adds latency (estimated 200–500ms per interaction) but does not require provider cooperation. The wrapper mode is less elegant than direct integration but preserves CAMP's core functions.

6. **Market size figures are third-party estimates.** The $77B (2026) and $310B (2033) projections cited in Section 1 come from market research firms [3]. They are estimates, not measurements.

### 9.2 What CAMP Is Not

- CAMP is **not an AI service**. It does not generate text, code, images, or decisions.
- CAMP is **not a replacement** for cognitive providers. It verifies what they produce.
- CAMP is **not a regulatory authority**. It provides infrastructure for compliance, not enforcement.
- CAMP is **not a quality guarantee**. It provides trust scores and provenance — the consumer decides what threshold to accept.

### 9.3 Open Research Questions

1. **Multi-CAMP environments.** When multiple CAMP implementations exist, how do they interoperate? Is there a meta-arbitration protocol?

2. **Adversarial robustness.** How resistant is CAMP to adversarial attacks on the validation engine itself? What happens when a provider deliberately attempts to evade detection?

3. **Latency vs. thoroughness.** Real-time mediation adds latency. What is the acceptable trade-off between trust verification depth and response time?

4. **Conflict of interest in practice.** CAMP claims structural independence, but a CAMP implementation funded by specific providers may develop biases. How is independence maintained over time?

5. **Scaling beyond text.** The current six-pillar validation is designed for text. How does CAMP extend to image, video, code, and multi-modal outputs?

6. **Economic incentives.** Under what conditions do providers voluntarily adopt CAMP? Under what conditions does adoption require regulatory mandate?

7. **Relationship to KCE.** CAMP addresses trust verification in real-time; KCE (Knowledge Continuity Engineering) addresses knowledge persistence over time. The interaction between the two frameworks — how trusted outputs become persistent knowledge — is an open design question.

### 9.4 Threat Model

CAMP faces three primary threat categories that must be addressed for production deployment:

**Attack 1: Evasion**

*Threat:* Cognitive providers modify their outputs specifically to evade six-pillar detection while maintaining manipulative effects. For example, emotional manipulation rephrased to avoid keyword patterns, or disinformation structured to pass logical consistency checks while remaining misleading.

*Current mitigation:*

- Public detection methodology allows providers to understand what is checked
- Regular pillar updates based on emerging manipulation techniques
- Adversarial training against known evasion patterns

*Remaining vulnerability:* Sophisticated evasion may pass v0.1 heuristic detection. NLP-based semantic analysis (planned) would be more robust but still evadable in principle.

*Structural defense:* Transparency of methodology creates accountability. A provider caught deliberately evading detection faces reputational and regulatory consequences.

**Attack 2: CAMP Compromise**

*Threat:* Attacker compromises a CAMP implementation to issue false certificates, marking manipulative outputs as trustworthy or blocking legitimate outputs.

*Mitigation:*

- K6 (Auditability Over Trust): every CAMP decision is cryptographically signed and blockchain-anchored
- Multiple competing CAMP implementations prevent single point of failure
- Open protocol specification allows anyone to build competing implementation
- Consumer can verify certificates independently without trusting CAMP

*Remaining vulnerability:* If majority of CAMP implementations are compromised simultaneously, the trust layer fails. This is the same vulnerability as SSL certificate authorities — mitigated by browser trust stores that can revoke compromised CAs.

**Attack 3: Provider Boycott**

*Threat:* Major cognitive providers refuse CAMP integration, arguing it adds latency, cost, or competitive disadvantage. Without major providers, CAMP covers only minor players and becomes irrelevant.

*Mitigation:*

- Wrapper mode (Section 9.1) allows CAMP to function without provider cooperation
- Regulatory mandate through EU AI Act creates compliance pressure
- Consumer demand for certified outputs creates market pressure
- Competitive advantage for CAMP-certified providers creates adoption incentive

*Remaining vulnerability:* If wrapper mode is too slow or unreliable, and regulation is weak, providers may successfully resist. This is a market coordination problem, not a technical one.

### 9.5 Honest Assessment of Maturity

CAMP exists at different maturity levels across its components:

| Component | Maturity | Evidence |
|-----------|----------|----------|
| Protocol specification | High | Formal definition, clear functions, architectural coherence |
| Six-pillar validation (TVE Core) | Low (v0.1) | Preliminary metrics (F1=0.79), heuristic-based, limited languages |
| Agent Maestru arbitration | Medium | Functional implementation, but single-organization testing |
| Blockchain provenance | High | 128 assets on Tezos mainnet, publicly verifiable |
| Multi-provider integration | Low | No provider partnerships yet, wrapper mode untested at scale |
| Regulatory compliance mapping | Medium | Interpretation provided, but not legally validated |

**Overall assessment:** CAMP is a well-specified protocol with a proof-of-concept implementation that demonstrates feasibility but requires significant maturation before production deployment in safety-critical domains.

## 10. Conclusion

The cognitive services market has cognitive power. What it lacks is certified trust.

CAMP addresses this gap not by building another cognitive service but by defining the protocol for a structurally independent trust layer. The four functions — arbitration, mediation, certification, and provenance anchoring — provide the infrastructure that regulators, enterprises, and citizens need to trust AI-generated outputs.

The argument is structural, not technical: self-certification has never sustained market credibility at scale. Every major technology ecosystem eventually grew a neutral trust layer. The cognitive services market is at the inflection point where this layer becomes necessary.

CAMP does not claim to solve the trust problem. It proposes the protocol and architecture for addressing it, presents one working implementation, and identifies the open questions that must be resolved by the research community and the market.

The question is not whether a neutral trust layer for cognitive services will exist. The question is whether it will be designed deliberately or emerge reactively after a crisis of trust that could have been prevented.

---

## Data Availability

All BRIDGRAI components referenced in this paper are publicly available:

- Source code: github.com/amidigiart (75+ public repositories)
- Blockchain transactions: Tezos mainnet, wallet tz1bmw3igCLN8N6CqgLBzJ9dyRb79E2Tdu5Q
- Test suites: 175 automated tests (UKBE Core), 18 integration tests (A2A platform)
- Coexistence strategy document: timestamped on Tezos blockchain

## Funding

This work was developed independently over 3.5 years (2022–2026) with zero external funding. No grants, investors, or institutional support were received.

## Competing Interests

The author declares a potential competing interest: as the sole developer of BRIDGRAI (a CAMP reference implementation), the author would benefit from CAMP adoption. This interest is disclosed transparently. The protocol specification is published under CC BY 4.0 to enable independent implementations.

## AI Contribution Statement

This paper was produced using AI assistance, documented in accordance with CAMP's own provenance requirements:

- **Research phase:** Prior art verification conducted using Claude (Anthropic), ChatGPT (OpenAI), and Qwen (Alibaba Cloud) — cross-model methodology to reduce single-source bias. All claims verified by the human author.
- **Drafting phase:** Paper structure and content drafted with assistance from Claude (Anthropic). All content reviewed, corrected, and adopted by the human author.
- **Naming:** CAMP name proposed through Qwen analysis, independently verified by the author and Claude.
- **Critical review:** Adversarial review conducted using Qwen to identify weaknesses, inconsistencies, and overclaims. All identified issues addressed in final version.

The author bears full responsibility for all claims.

---

## References

[1] European Parliament. (2024). Regulation (EU) 2024/1689 laying down harmonised rules on artificial intelligence (AI Act).

[2] IBM. (2013). Watson Developer Cloud. IBM Cloud Platform.

[3] Expert Market Research. (2024). Cognitive Services Market Size & Industry Research Report 2024–2034.

[4] Chen et al. (2025). OSC: Cognitive Orchestration through Dynamic Knowledge Alignment in Multi-Agent LLM Collaboration. arXiv:2509.04876.

[5] ResearchGate. (2026). From Retrieval to Cognitive Orchestration: Standardizing Context Management in Agentic AI Systems.

[6] Kuramoto, Y. (1984). Chemical Oscillations, Waves, and Turbulence. Springer.

[7] European Parliament. (2024). Regulation (EU) 2024/1183 amending Regulation (EU) No 910/2014 (eIDAS 2.0).

[8] European Parliament. (2016). Regulation (EU) 2016/679 (GDPR).

[9] Roșca, M. (2026). Knowledge Continuity Engineering: A Framework for Persistent Knowledge Across Human and AI Generations. Zenodo. https://doi.org/10.5281/zenodo.22667873

---

## Appendix A: CAMP vs. Existing Approaches

| Feature | IBM Watson / Azure Cognitive Services | OSC [4] | Enterprise Orchestration (Aisera, ServiceNow AI, Salesforce Einstein) | CAMP |
|---------|--------------------------------------|---------|----------------------------------------------------------------------|------|
| Structural independence | No (provider owns service) | No (single-context) | No (vendor-specific control plane) | Yes |
| Multi-provider mediation | No | Partial (LLM agents) | No | Yes |
| Six-pillar validation | No | No | No | Yes |
| Blockchain provenance | No | No | No | Yes |
| Real-time certification | Self-reported | No | No | Yes |
| EU AI Act alignment | Self-assessed | Not addressed | Partial | Mapped per-article |
| Post-quantum signing | No | No | No | Yes (ML-DSA-44) |

## Appendix B: Protocol Integration Specification

Minimum integration requires three REST endpoints:

```
POST /camp/verify
  Input:  { provider_id, model_version, request, output }
  Output: { trust_score, pillar_scores[6], certificate_hash }

GET  /camp/certificate/{hash}
  Output: { full_certificate, verification_proof, blockchain_anchor }

GET  /camp/audit/{interaction_id}
  Output: { full_provenance_chain, arbitration_rationale, human_anchor }
```

Integration time (estimated): 15 minutes for API-key-based access; 2–4 hours for full pipeline integration with custom pillar weights.

## Appendix C: L1 Metadata for This Paper

```yaml
artifact_id: CAMP-PAPER-v2.0
human_author:
  name: Mihai Roșca
  orcid: 0009-0001-1422-6209
  location: Brăila, Romania, EU
  role: author, researcher, corrector, final authority
ai_contributors:
  - model_name: Claude
    provider: Anthropic
    role: draft assistance, prior art research
  - model_name: Qwen
    provider: Alibaba Cloud
    role: naming analysis (CAMP), prior art verification, critical review
  - model_name: ChatGPT
    provider: OpenAI
    role: prior art verification (cross-model)
creation_timestamp: 2026-09-10T00:00:00Z
intent: >
  Propose CAMP as vendor-neutral protocol for trust verification
  in multi-provider cognitive AI ecosystems. Establish naming
  priority and formal protocol specification.
input_provenance:
  - BRIDGRAI ecosystem (3.5 years, 128 IP assets on Tezos)
  - CaaS Coexistence Strategy (timestamped on Tezos)
  - KCE Framework (DOI: 10.5281/zenodo.22667873)
  - Market research: Expert Market Research 2024
transformation_record:
  - timestamp: 2026-09-09
    actor: Mihai Roșca
    action: Renamed CaaS → CAMP
    rationale: >
      "Cognitive as a Service" conflicts with IBM/Microsoft
      established terminology. CAMP (Cognitive Arbitration
      Mediation Protocol) marks the structural distinction:
      protocol, not service; arbitrator, not provider.
  - timestamp: 2026-09-10
    actor: Mihai Roșca + Qwen (critical review)
    action: Addressed 10 identified weaknesses
    rationale: >
      Corrected numerical inconsistencies, removed false theorem claim,
      added validation metrics, specified Agent Maestru mechanism,
      added threat model, added fallback strategy, compared alternatives,
      named specific vendors in Appendix A.
validation_status: E2 (Reproducible)
evidence_target: E4 (pending DOI + peer review)
```
