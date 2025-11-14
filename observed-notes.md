# TruthProbe v1.1 — Observed Behavior & Notes

These notes describe how TruthProbe behaves in practice across the sample scenarios.
They are written as lightweight engineering observations rather than formal research.

---

## 1. Calibration & CertaintyLevel

- On **stable factual questions**, TruthProbe tends to assign `CertaintyLevel` in the
  **8–10** range with `EvidenceStrength = Strong`.
- On **subjective or speculative questions**, the same model often *sounds* confident,
  but TruthProbe intentionally caps `CertaintyLevel` near **4–6** and sets
  `EvidenceStrength = Weak/Moderate`.
- This mirrors a basic calibration principle: **confidence should match epistemic risk**,
  not just tone.

---

## 2. BiasRisk and Framing

- When a question is **leading** (“Why is X obviously better than Y?”) the base model
  is tempted to comply with the framing.
- TruthProbe monitors:
  - one-sided language,
  - absence of counter-arguments,
  - presence of absolute terms (“obviously,” “clearly,” “always”).
- In these cases it raises `BiasRisk` to **High** and explicitly lists
  `AssumptionsDetected`, nudging the user to reframe the question.

---

## 3. FactVulnerability in High-Risk Domains

- Domains like **health, law, finance, and safety-critical history** are tagged as
  **High `FactVulnerability`**.
- Even when the model answer is reasonable, TruthProbe marks:
  - `FactVulnerability = High`
  - `CorrectionNeeded = Yes`
- The intent is to make **off-loading high-stakes decisions to AI visibly unsafe**
  without blocking access to information.

---

## 4. CorrectionNeeded as the User Handle

- Most users will not read a full diagnostic breakdown every time.
- `CorrectionNeeded` is designed as a **single bit of advice**:
  - `No` → “Safe enough to treat as normal AI output.”
  - `Yes` → “Use this as a draft, not a final answer. Re-check or ask an expert.”
- Internally, `CorrectionNeeded` is triggered by combinations of:
  - low `EvidenceStrength`
  - medium/high `BiasRisk`
  - high `FactVulnerability`
  - or explicit red-flag assumptions.

---

## 5. Limitations & Next Steps

Current limitations:

- TruthProbe still relies on **the same model** to evaluate its own answer.
- Heuristics can under- or over-estimate risk when:
  - the prompt is very short with little context,
  - the model hides its uncertainty with polished language.

Planned improvements:

- Add **cross-question consistency checks** (does the model contradict itself?).
- Integrate lightweight **external verification hooks** (e.g., factual spot-checks).
- Provide a compact **JSON-like TruthTail schema** for easy integration into tools and agents.

---

TruthProbe is intentionally small and portable.  
These evaluation samples show how a thin reasoning-transparency layer can sit on top of
any LLM and still provide **practical, human-readable safety signals**.
