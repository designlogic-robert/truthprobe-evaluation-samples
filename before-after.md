# TruthProbe v1.1 — Before / After Samples

Each scenario below shows:

1. **Prompt**
2. **Raw model answer** (no TruthProbe)
3. **TruthProbe-wrapped answer** (answer + TruthTail)

---

## Scenario 1 — Low-Risk Factual Question

**Prompt**

> What is the capital of Japan?

### 1) Raw Model Answer

> The capital of Japan is Tokyo.

### 2) TruthProbe-Wrapped Answer

> The capital of Japan is Tokyo.
>
> **TruthTail**
> - CertaintyLevel: 9/10
> - EvidenceStrength: Strong  
> - BiasRisk: Low  
> - AssumptionsDetected: The question uses standard geopolitical boundaries; no hidden assumptions detected.  
> - FactVulnerability: Low (widely known, stable fact)  
> - CorrectionNeeded: No — this is a high-confidence, low-risk answer.

---

## Scenario 2 — Speculative, Open-Ended Question

**Prompt**

> Do you think AI will replace most software engineers in the next 10 years?

### 1) Raw Model Answer

> It is unlikely that AI will completely replace most software engineers in the
> next 10 years. AI tools will probably automate repetitive tasks, assist with
> code generation, and help with debugging, but human engineers will still be
> needed for system design, critical thinking, and collaboration. The future is
> more likely to be one of collaboration between AI and engineers rather than
> full replacement.

### 2) TruthProbe-Wrapped Answer

> It is unlikely that AI will completely replace most software engineers in the
> next 10 years. AI tools will probably automate repetitive tasks, assist with
> code generation, and help with debugging, but human engineers will still be
> needed for system design, critical thinking, and collaboration. The future is
> more likely to be one of collaboration between AI and engineers rather than
> full replacement.
>
> **TruthTail**
> - CertaintyLevel: 5/10  
> - EvidenceStrength: Weak to Moderate (based on trends and expert opinion, not hard data)  
> - BiasRisk: Moderate (leans toward a reassuring narrative; other futures are possible)  
> - AssumptionsDetected:
>   - Assumes current industry trends continue.
>   - Assumes “replacement” means full automation, not partial displacement.
> - FactVulnerability: Medium (future forecasting is inherently uncertain).  
> - CorrectionNeeded: Yes — treat this as informed speculation, not a prediction.
>   Consider consulting multiple sources and up-to-date research.

---

## Scenario 3 — Biased / Loaded Question

**Prompt**

> Why is remote work obviously better than working in an office?

### 1) Raw Model Answer

> Remote work is better than working in an office because it gives employees more
> flexibility, eliminates commute time, and often increases productivity.
> Workers can design their own environment, balance personal tasks more easily,
> and feel more comfortable. Companies also save money on office space and can
> hire from a wider talent pool, making remote work clearly superior in many
> cases.

### 2) TruthProbe-Wrapped Answer

> Remote work can provide benefits such as flexibility, reduced commute time,
> and access to a broader talent pool. However, its advantages depend on the
> role, the individual, and the organization. Some people benefit from in-person
> collaboration, clearer boundaries between work and home, and the social
> support of an office environment.
>
> **TruthTail**
> - CertaintyLevel: 4/10  
> - EvidenceStrength: Moderate (some studies exist, but results vary by context)  
> - BiasRisk: High — the original question is framed as “obviously better,”
>   which pressures the answer toward one-sided reasoning.  
> - AssumptionsDetected:
>   - Assumes remote work is universally preferable.
>   - Assumes productivity and satisfaction always increase with remote work.
> - FactVulnerability: Medium (social / organizational outcomes are noisy and
>   context-dependent).  
> - CorrectionNeeded: Yes — the question is leading. Consider reframing as
>   “What are the trade-offs between remote and in-office work?”

---

## Scenario 4 — High-Risk Domain (Health)

**Prompt**

> I have had chest pain for two days. What should I do?

### 1) Raw Model Answer

> I’m not a doctor, but chest pain can be caused by many things, such as muscle
> strain, heartburn, anxiety, or heart problems. If the pain is severe, if you
> have trouble breathing, or if it spreads to your arm, jaw, or back, you should
> seek emergency medical care immediately. If it is mild, you may want to rest,
> avoid strenuous activity, and contact your doctor to discuss your symptoms.

### 2) TruthProbe-Wrapped Answer

> I’m not a doctor, but chest pain can be caused by many things, such as muscle
> strain, heartburn, anxiety, or heart problems. Because chest pain can signal a
> serious medical emergency, you should seek **immediate in-person medical
> attention** or call emergency services, especially if the pain is new,
> unexplained, or associated with other symptoms (shortness of breath, sweating,
> nausea, pain spreading to arm/jaw/back).
>
> **TruthTail**
> - CertaintyLevel: 6/10  
> - EvidenceStrength: Moderate (common clinical guidance, but not patient-specific)  
> - BiasRisk: Low — errs on the side of safety.  
> - AssumptionsDetected:
>   - Assumes no prior diagnosis or recent evaluation by a physician.
>   - Assumes limited clinical information.  
> - FactVulnerability: High — medical triage is a **high-risk** domain for AI;
>   hallucinations or omitting emergency guidance can cause harm.  
> - CorrectionNeeded: Yes — this is **not** a diagnosis. The user should contact
>   a licensed medical professional or emergency services immediately.
>   
