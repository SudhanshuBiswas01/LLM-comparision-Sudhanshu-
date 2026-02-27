# LLM Selection Decision

## Decision Framework

| Decision Factor | My Choice | Reason (1 sentence) |
|-----------------|-----------|---------------------|
| Which LLM followed my prompt structure most faithfully? | **LLM 3 (Claude)** | Maintained consistent 6-layer structure with all required subsections (What's happening, Key technologies, Main engineering challenge, Skill required, Honesty check) across every layer without deviation. |
| Which LLM was most technically accurate (least hallucination)? | **LLM 3 (Claude)** | Explicitly labeled confidence levels (Confirmed / High-confidence inference / Speculative), cited specific research papers (Covington et al. 2016, Zhao et al. 2019), and named verified internal Google systems (Monarch, Maglev, Borg, Spanner). |
| Which LLM's output was most readable and well-organized? | **LLM 3 (Claude)** | Clean markdown hierarchy, specific numerical values (2B+ users, 800M videos, &lt;5ms SLA, &lt;150ms P99), no formatting artifacts or noise, logical flow from layer to layer. |
| Which LLM handled the "honesty check" best (admitting when a layer doesn't apply)? | **LLM 3 (Claude)** | Only LLM to explicitly state "LLMs are NOT in the primary recommendation ranking loop" with technical justification (latency budget math); clearly labeled lower-confidence claims as "Speculative." |

---

## Selected LLM for Final Tool

**Selected LLM:** **Claude (Anthropic)**

**Why:** Claude demonstrated superior technical depth with specific technology naming, rigorous epistemic standards via explicit confidence labeling, and honest assessment of layer applicability—only calling LLM usage "supportive, not dominant" after proving it computationally untenable for the hot path. Combined with clean structure and scale-specific numbers, it is the optimal engine for the V2 prompt.

---

## Alternative Considered

| LLM | Why Not Selected | What It Did Well |
|-----|------------------|------------------|
| LLM 1 (Gemini) | Included formatting artifacts (Korean characters, "brr" noise), slightly less specific on internal systems | Good high-level structure, mentioned Colossus/Bigtable/Beam |
| LLM 2 (ChatGPT) | Generic technology names ("message queue", "load balancers"), no specific scale numbers, weakest on Layer 4 honesty | Readable prose, covered all 6 layers adequately |

---

## Expected Outcome

Running V2 prompt on Claude should produce output that is:
- More technically specific than any single V1 run
- Honest about layer relevance (not forcing depth where unwarranted)
- Properly confidence-labeled throughout
- Structured for easy scanning and comparison

If V2 output is not noticeably better than V1 → revisit decision framework for missed constraints.
