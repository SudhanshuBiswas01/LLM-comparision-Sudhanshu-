# LLM Comparison — Product Teardown: Youtube Recommendation system.

## Models Used
| # | LLM Name  | Mode (Fast/Standard/Thinking) | Response Time (approx) |
|---|---------- |-------------------------------|----------------------|
| 1 |Chat GPT   |    Chat GPT 5.2             |          15sec       |
| 2 |Gemnin     |    Gemini 3 Fast            |          30sec       |
| 3 |Claud      |    sonnet 4.6               |          20sec       |

## Layer-by-Layer Comparison

### Layer 1: Data Foundation
| Criteria                                 | LLM 1 (Gemini)                                  | LLM 2 (ChatGPT)                               | LLM 3 (Claude)                                                            | Best?                                                                                                                                                                                |
| ---------------------------------------- | ----------------------------------------------  | --------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Specificity (1-5)                        | 4                                               | 3                                             | 5                                                                         | **LLM 3**                                                                                                                                                                            |
| Named real tech?                         | Y                                               | Y                                             | Y                                                                         | Tie                                                                                                                                                                                  |
| Identified a real engineering challenge? | Y                                               | Y                                             | Y                                                                         | Tie                                                                                                                                                                                  |
| Notes:                                   | Named Colossus, Bigtable, Apache Beam, Protobuf;| Named Apache Kafka/PubSub, BigQuery, GFS,     | Named Google Pub/Sub, Apache Beam, Bigtable, Spanner, BigQuery, Colossus; | Claude provides most specific technical details including internal Google technologies (Spanner, Colossus) and precise engineering challenge (watermarking, exactly-once processing) |
|                                          |mentioned "Data Drift" and "Selection Bias"      |Apache Beam; mentioned petabyte-scale freshness|detailed "signal freshness vs. consistency tradeoff" with watermarking     |

### Layer 2: Statistics & Analysis

| Criteria           | LLM 1 | LLM 2 | LLM 3 | Best? |
|--------------------|--------|--------|--------|-------|
| Specificity (1-5)  |    4   |    3   |   5    |LLM3   |
| Named real tech?   | Y      |  Y     | Y      |TIE    |
| Identified a real engineering challenge? | Y | Y | Y |TIE|
Notes:    
LLM 1 -   Named Google Vizier, Chi-squared tests, T-tests; mentioned "viral vs. breaking algorithm" distinction
LLM 2 - Mentioned A/B testing, Bayesian optimization, hypothesis testing—generic
LLM3 - Named Monarch, interleaved evaluation frameworks, bootstrap confidence intervals, BigQuery; detailed "metric design" as hardest problem with specific examples (watch time pathologies, radicalization)
Best - TIE  - Claude cites specific internal tools (Monarch), specific statistical methods (interleaving, bootstrap), and deeply analyzes metric design challenges with concrete examples


### Layer 3: Machine Learning Models
| Criteria           | LLM 1 | LLM 2 | LLM 3 | Best? |
|--------------------|--------|--------|--------|-------|
| Specificity (1-5)  | 4      | 3      | 5      |Tie       |
| Named real tech?   | Y      | Y      | Y      |Tie       |
| Named model family?| Y      | Y      | Y      |Tie       |
| Identified a real engineering challenge? | Y | Y | Y   |
| Notes:          
LMM1 - Named TensorFlow, Two-Tower Models, DNN, Wide & Deep, Transformer; mentioned "Cold Start
LLM 2 - Named deep neural networks, two-tower models, TensorFlow, gradient-boosted trees—generic
LLM 3 - Named TensorFlow/JAX, ScaNN, TPU pods, Parameter Server, DTensor, TFX; specified Two-Tower DNN, DCN (Deep & Cross Network), MMoE (Mixture-of-Experts); detailed "training data bias" with IPS correction
best - Claude provides exhaustive architecture details (3-stage pipeline), specific Google technologies (ScaNN, JAX, DTensor), and deeply technical challenge (position/exposure bias, inverse propensity scoring)



### Layer 4: LLM / Generative AI
| Criteria           | LLM 1 | LLM 2 | LLM 3 | Best? |
|--------------------|--------|--------|--------|-------|
| Specificity (1-5)  |  4     | 3      |  5     |LLM3   |
| Named real tech?   | Y      | Y      | Y      |Tie    |
| Notes:             
LLM 1 -  Named Gemini/PaLM API, Vertex AI, ScaNN; noted "Inference Cost vs. Value" tradeoff	LLM 2 -  Vague on LLM usage; mentioned "transformer-based language models" generically	
LLM 3 -  Explicitly states "LLMs are NOT in the ranking hot path" with detailed latency justification (P99 ~100ms); names BERT-family, speculates on conversational discovery with clear confidence labeling; explains why LLMs are precomputed features only
Best - Claude is most honest about limitations, provides technical reasoning (latency budget math), and clearly labels speculation vs. confirmed information

### Layer 5: Deployment & Infrastructure
| Criteria           | LLM 1 | LLM 2 | LLM 3 | Best? |
|--------------------|--------|--------|--------|-------|
| Specificity (1-5)  |   3    |    4   |  5     | LLM 3 |
| Named real tech?   | Y      | Y      | Y      | Tie   |
| Notes:             
LLM 1 - Named TPU v4/v5, Kubernetes (Borg), gRPC, Redis/Memcached; mentioned sub-100ms latency
LLM 2 - Named TensorFlow Serving, containerized microservices, load balancers—generic
LLM 3 - Named TF Serving/Vertex AI, Bigtable, Borg/Kubernetes, Monarch, Spanner; specified <5ms SLA for features, <150ms P99 total pipeline, canary deployment, shadow deployment
Best - Claude provides specific SLA numbers, internal Google tools (Monarch, Borg), and detailed latency budgets with fallback mechanisms

### Layer 6: System Design & Scale
| Criteria           | LLM 1 | LLM 2 | LLM 3 | Best? |
|--------------------|--------|--------|--------|-------|
| Specificity (1-5)  |   4    |    3   |  5     | LLM 3 |
| Named real tech?   | Y      | Y      | Y      |Tie    |
| Notes:             
LLM 1 - Mentioned multi-region load balancing, Sharded Bigtable, Pub/Sub; "Global State Consistency" challenge
LLM 2 -Mentioned distributed caching, approximate nearest neighbor, fault-tolerant architectures—generic
LLM 3 - Named Maglev (Google's load balancer), Redis/Memcached, Bigtable autoscaling, Chaos engineering; specified 2B+ users, 800M videos, cold start subsystems, circuit breakers, explore/exploit policies
Best - Claude provides specific scale numbers, Google's proprietary tech (Maglev), and detailed cold start engineering with concrete video corpus size


## Overall Verdict

| Dimension                          | Winner (LLM #)     | Why? (1 sentence)                                                                                                                                                                                                            |
| ---------------------------------- | ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Most technically specific overall  | **LLM 3 (Claude)** | Provides granular technical details across all layers including specific internal Google technologies (Spanner, Monarch, Maglev, ScaNN, DTensor), precise latency budgets, and architectural patterns from published papers. |
| Best at naming real technologies   | **LLM 3 (Claude)** | Cites 15+ specific technologies including Google's proprietary internal systems (Borg, Monarch, Maglev, Colossus, Spanner) versus generic industry terms.                                                                    |
| Least hallucination / made-up info | **LLM 3 (Claude)** | Explicitly labels speculative claims ("Speculative (lower confidence)"), distinguishes confirmed from inferred information, and acknowledges uncertainty where others state confidently.                                     |
| Best at "hardest problem" insight  | **LLM 3 (Claude)** | Identifies "feedback loop debiasing at 2B-user scale" and "metric design" as core challenges with sophisticated technical solutions (IPS, counterfactual learning, interleaving) rather than generic statements.             |
| Best structured output             | **LLM 3 (Claude)** | Most consistent formatting, clearest hierarchy, explicit "Honesty check" sections, and systematic confidence labeling throughout.                                                                                            |
| Fastest useful response            | **N/A**            | Cannot determine from documents provided; no timestamps or response time metrics included.                                                                                                                                   |


## Key Observation
> One thing I noticed about how different LLMs handle the same prompt:
LLM 3 (Claude) significantly outperforms the others in technical depth, specificity, and intellectual honesty. It demonstrates:
Deep familiarity with Google's published research (Covington et al. 2016, Zhao et al. 2019)
Understanding of internal Google infrastructure (Borg, Monarch, Maglev, Spanner, Colossus)
Sophisticated ML engineering knowledge (MMoE, DCN, ScaNN, IPS correction)
Rigorous epistemic standards (explicit confidence labeling, distinguishing inference from speculation)
LLM 1 (Gemini) is competent but occasionally vague and includes some seemingly fabricated formatting artifacts (Korean characters, "brr" noises).
LLM 2 (ChatGPT) provides the most generic response, relying on industry-standard terms without the specific technical depth or internal system knowledge demonstrated by Claude.

