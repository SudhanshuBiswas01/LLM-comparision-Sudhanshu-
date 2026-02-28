# Reflection

## Question 1: Which of the 6 layers surprised you the most in terms of complexity for the product you chose? Why?

**Answer:** Layer 4 (LLM/Generative AI) surprised me most—not because it was complex, but because Claude correctly identified it as **minimal for IRCTC** despite the current AI hype. I expected all LLMs to force-fit generative AI into every product, but the V2 prompt's explicit "layer honesty" constraint worked. Claude's technical justification was rigorous: LLM inference cost is unjustified for deterministic booking logic, and government audit trails favor rule-based systems. This revealed that good teardowns require **subtractive judgment**—knowing when NOT to apply a technology—is as important as additive analysis.

## Question 2: What was the single biggest difference you noticed between the LLMs you tested? Not just "one was better"—what specifically did one do that the others couldn't?

**Answer:** **Epistemic rigor.** Claude explicitly labeled confidence levels (Confirmed / High-confidence inference / Speculative) and cited specific research papers (Covington et al. 2016, Zhao et al. 2019). When uncertain, it said so: "Speculative (lower confidence): YouTube may be experimenting with LLM-powered conversational discovery." Gemini and ChatGPT stated everything with uniform confidence, making it impossible to distinguish verified facts from educated guesses. This "honesty check" pattern—explicitly marking uncertainty—is critical for technical credibility, especially when interviewing at senior levels where overclaiming is a red flag.
