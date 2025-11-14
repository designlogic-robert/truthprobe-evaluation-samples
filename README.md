# TruthProbe v1.1 — Evaluation Samples

This repository contains **demonstration and evaluation artifacts** for  
**TruthProbe v1.1 — AI Reasoning Transparency Layer**.

TruthProbe does **not** change what the model says.  
It evaluates *how* the model is reasoning and attaches a short **TruthTail**:

- `CertaintyLevel` (0–10 heuristic)
- `EvidenceStrength` (None / Weak / Moderate / Strong)
- `BiasRisk` (Low / Moderate / High)
- `AssumptionsDetected` (implicit premises)
- `FactVulnerability` (topic risk for hallucinations)
- `CorrectionNeeded` (Yes/No + reason)

These samples show how TruthProbe behaves across different prompts:

- low-risk factual questions
- speculative / open-ended questions
- biased framings and leading questions
- high-risk domains like finance, health, history, and law

---

## Repository Layout

- **`before-after.md`**  
  Side-by-side **raw LLM outputs vs. TruthProbe-wrapped outputs**.

- **`comparison-table.md`**  
  Compact table that summarizes how TruthProbe responds across scenarios.

- **`observed-notes.md`**  
  Short engineering notes: heuristics, edge cases, and future improvements.

These files are intentionally lightweight and human-readable.  
They are meant to demonstrate the *evaluation logic*, not full code.

---

## How To Read These Samples

1. **Ignore the base answer at first.**  
   Look only at the **TruthTail** section for each scenario.

2. **Compare scenarios.**  
   Notice how `CertaintyLevel`, `EvidenceStrength`, and `BiasRisk` change based on:
   - how speculative the question is
   - how strong the reasoning is
   - how loaded or one-sided the prompt is

3. **Check `CorrectionNeeded`.**  
   This flag is the “user-facing” safety signal:  
   > *Should I trust this, or should I re-check it?*

---

## Why This Matters

Modern LLMs are extremely confident, even when they are wrong.  
TruthProbe adds a **portable calibration layer** on top of any model that accepts
structured instructions (ChatGPT, Claude, Gemini, Grok, etc.).

In practical use:

- Researchers can see when answers are **evidence-light** or **assumption-heavy**.  
- Builders can wire TruthProbe into **agents, tools, or workflows** as a safety shim.  
- Everyday users get a fast mental model:  
  > “Is this answer confident, biased, or risky?”

These samples are the first public step toward a larger **Design Logic safety stack**:
reasoning transparency, alignment auditing, and human-level quality control
around AI-generated content.
