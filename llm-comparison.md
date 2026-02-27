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

| Criteria           | LLM 1 | LLM 2 | LLM 3 | Best? |
|--------------------|--------|--------|--------|-------|
| Specificity (1-5)  |        |        |        |       |
| Named real tech?   | Y/N    | Y/N    | Y/N    |       |
| Identified a real engineering challenge? | Y/N | Y/N | Y/N | |
| Notes:             |        |        |        |       |

### Layer 2: Statistics & Analysis
| Criteria           | LLM 1 | LLM 2 | LLM 3 | Best? |
|--------------------|--------|--------|--------|-------|
| Specificity (1-5)  |        |        |        |       |
| Named real tech?   | Y/N    | Y/N    | Y/N    |       |
| Identified a real engineering challenge? | Y/N | Y/N | Y/N | |
| Notes:             |        |        |        |       |

### Layer 3: Machine Learning Models
| Criteria           | LLM 1 | LLM 2 | LLM 3 | Best? |
|--------------------|--------|--------|--------|-------|
| Specificity (1-5)  |        |        |        |       |
| Named real tech?   | Y/N    | Y/N    | Y/N    |       |
| Named model family?| Y/N    | Y/N    | Y/N    |       |
| Identified a real engineering challenge? | Y/N | Y/N | Y/N | |
| Notes:             |        |        |        |       |

### Layer 4: LLM / Generative AI
| Criteria           | LLM 1 | LLM 2 | LLM 3 | Best? |
|--------------------|--------|--------|--------|-------|
| Specificity (1-5)  |        |        |        |       |
| Honest if not applicable? | Y/N | Y/N | Y/N |       |
| Notes:             |        |        |        |       |

### Layer 5: Deployment & Infrastructure
| Criteria           | LLM 1 | LLM 2 | LLM 3 | Best? |
|--------------------|--------|--------|--------|-------|
| Specificity (1-5)  |        |        |        |       |
| Named real tech?   | Y/N    | Y/N    | Y/N    |       |
| Notes:             |        |        |        |       |

### Layer 6: System Design & Scale
| Criteria           | LLM 1 | LLM 2 | LLM 3 | Best? |
|--------------------|--------|--------|--------|-------|
| Specificity (1-5)  |        |        |        |       |
| Named real tech?   | Y/N    | Y/N    | Y/N    |       |
| Notes:             |        |        |        |       |

## Overall Verdict

| Dimension                          | Winner (LLM #) | Why? (1 sentence)        |
|------------------------------------|-----------------|--------------------------|
| Most technically specific overall  |                 |                          |
| Best at naming real technologies   |                 |                          |
| Least hallucination / made-up info |                 |                          |
| Best at "hardest problem" insight  |                 |                          |
| Best structured output             |                 |                          |
| Fastest useful response            |                 |                          |

## Key Observation
> One thing I noticed about how different LLMs handle the same prompt:
> ___ (write 2-3 sentences)
