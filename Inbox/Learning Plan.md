

17-06-2026 14:21

Status: 

Tags:

# Learning Plan

## 3-Month Practical and Theoretical ML/LLM Learning Plan

**Main structure:** practical + theoretical topics, 15 minutes daily, with optional extra time on implementation days.

## Learning Unit Structure

| Unit | Duration |
|---|---:|
| Micro-topic | 1 day |
| Topic block | 3–7 days |
| Paper-inspired block | 1–3 weeks |
| Monthly theme | 4 weeks |

---

# Month 1 — Reliability, Uncertainty, and Drift

## Week 1 — Calibration

| Day | Topic / Sub-topic               | Type     | Practical Output                        |
| --: | ------------------------------- | -------- | --------------------------------------- |
|   1 | What is model calibration?      | Theory   | Define confidence vs accuracy           |
|   2 | Expected Calibration Error, ECE | Theory   | Understand bin-based calibration error  |
|   3 | Reliability diagrams            | Practice | Plot confidence vs empirical accuracy   |
|   4 | Maximum Calibration Error, MCE  | Theory   | Compare ECE vs worst-bin error          |
|   5 | Brier score                     | Theory   | Compare Brier score vs cross-entropy    |
|   6 | Temperature scaling             | Theory   | Understand logit scaling                |
|   7 | Implement temperature scaling   | Practice | Fit one scalar `T` on validation logits |

## Week 2 — Selective Prediction and Uncertainty

| Day | Topic / Sub-topic | Type | Practical Output |
|---:|---|---|---|
| 8 | Aleatoric vs epistemic uncertainty | Theory | Distinguish data noise from model uncertainty |
| 9 | Monte Carlo dropout | Practice | Run repeated stochastic predictions |
| 10 | Deep ensembles | Theory | Understand ensemble-based uncertainty |
| 11 | Ensemble variance | Practice | Compare prediction disagreement across models |
| 12 | Selective prediction | Theory | Learn risk-coverage tradeoff |
| 13 | Abstention threshold | Practice | Reject uncertain predictions |
| 14 | Risk-coverage curve | Practice | Plot accuracy vs retained samples |

## Week 3 — Conformal Prediction

| Day | Topic / Sub-topic | Type | Practical Output |
|---:|---|---|---|
| 15 | What is conformal prediction? | Theory | Understand distribution-free coverage |
| 16 | Nonconformity scores | Theory | Define “how strange” a prediction is |
| 17 | Split conformal prediction | Theory | Understand calibration-set logic |
| 18 | Implement split conformal regression | Practice | Produce prediction intervals |
| 19 | Conformal classification sets | Theory | Understand set-valued predictions |
| 20 | Implement conformal classification | Practice | Output prediction sets |
| 21 | Coverage vs efficiency | Mixed | Compare empirical coverage and set size |

## Week 4 — Distribution Shift and Monitoring

| Day | Topic / Sub-topic | Type | Practical Output |
|---:|---|---|---|
| 22 | Covariate shift vs label shift | Theory | Distinguish `P(x)` shift from `P(y)` shift |
| 23 | Concept drift | Theory | Understand change in `P(y | x)` |
| 24 | Population Stability Index | Practice | Compute PSI for one feature |
| 25 | KL divergence / Jensen-Shannon divergence | Theory | Compare distribution distances |
| 26 | Wasserstein distance | Practice | Measure drift between distributions |
| 27 | Embedding drift | Practice | Track embedding norm and cosine distribution |
| 28 | Monitoring checklist | Mixed | Build a practical drift-monitoring checklist |

---

# Month 2 — Embeddings, Retrieval, and Representation Learning

## Week 5 — Embedding Geometry

| Day | Topic / Sub-topic | Type | Practical Output |
|---:|---|---|---|
| 29 | What makes a good embedding? | Theory | Define neighborhood preservation |
| 30 | Cosine similarity vs Euclidean distance | Practice | Compare nearest neighbors |
| 31 | Embedding norms | Practice | Inspect norm distribution |
| 32 | Embedding anisotropy | Theory | Understand directional collapse |
| 33 | Measure anisotropy | Practice | Plot cosine similarity distribution |
| 34 | Whitening embeddings | Theory | Understand covariance normalization |
| 35 | Apply embedding whitening | Practice | Compare similarity before/after whitening |

## Week 6 — Contrastive Learning

| Day | Topic / Sub-topic | Type | Practical Output |
|---:|---|---|---|
| 36 | Metric learning | Theory | Understand learning by distance |
| 37 | Triplet loss | Theory | Anchor, positive, negative |
| 38 | Triplet loss failure modes | Theory | Bad negatives, easy negatives, collapse |
| 39 | Hard negative mining | Practice | Select hardest negatives in a batch |
| 40 | InfoNCE loss | Theory | Contrastive classification view |
| 41 | Implement InfoNCE | Practice | Build similarity matrix and loss |
| 42 | Temperature in contrastive learning | Practice | Test different temperature values |

## Week 7 — Retrieval Systems

| Day | Topic / Sub-topic | Type | Practical Output |
|---:|---|---|---|
| 43 | Sparse retrieval | Theory | Understand lexical matching |
| 44 | BM25 | Theory | Learn term frequency, document frequency, length normalization |
| 45 | Implement BM25 search | Practice | Rank small document set |
| 46 | Dense retrieval | Theory | Retrieval using embeddings |
| 47 | Bi-encoder retrieval | Practice | Encode queries and documents |
| 48 | Cross-encoder re-ranking | Theory | Understand accuracy/latency tradeoff |
| 49 | Two-stage retrieval pipeline | Practice | Retrieve top-`k`, then re-rank |

## Week 8 — Retrieval Evaluation and ANN

| Day | Topic / Sub-topic | Type | Practical Output |
|---:|---|---|---|
| 50 | Recall@K | Theory | Understand retrieval recall |
| 51 | MRR | Theory | Mean reciprocal rank |
| 52 | NDCG | Theory | Ranking with graded relevance |
| 53 | Implement retrieval metrics | Practice | Compute Recall@K, MRR, NDCG |
| 54 | Approximate nearest-neighbor search | Theory | Exact vs approximate search |
| 55 | HNSW intuition | Theory | Graph-based vector search |
| 56 | HNSW experiment | Practice | Compare speed vs recall |

---

# Month 3 — LLM Systems, Transformer Internals, and Efficient Adaptation

## Week 9 — Practical LLM Systems

| Day | Topic / Sub-topic | Type | Practical Output |
|---:|---|---|---|
| 57 | Prompt templates | Practice | Build reusable prompt with variables |
| 58 | Few-shot prompting | Practice | Compare zero-shot vs few-shot |
| 59 | Structured output | Practice | Force JSON/schema output |
| 60 | Function calling / tool calling | Theory | Understand LLM as controller |
| 61 | Tool-calling workflow | Practice | Design a simple tool-call flow |
| 62 | Hallucination reduction | Theory | Grounding, constraints, refusal logic |
| 63 | LLM evaluation mini-set | Practice | Build 10 test cases and scoring rules |

## Week 10 — RAG

| Day | Topic / Sub-topic | Type | Practical Output |
|---:|---|---|---|
| 64 | RAG pipeline overview | Theory | Query → retrieve → generate |
| 65 | Chunking strategies | Theory | Fixed, recursive, semantic chunking |
| 66 | Chunking experiment | Practice | Compare retrieval quality by chunk size |
| 67 | Embedding model selection | Practice | Compare two embedding models |
| 68 | Retrieval grounding | Theory | How retrieved context constrains generation |
| 69 | RAG failure modes | Theory | Missing context, wrong context, weak synthesis |
| 70 | RAG evaluation | Practice | Evaluate answer correctness and citation grounding |

## Week 11 — Transformer and LLM Internals

| Day | Topic / Sub-topic | Type | Practical Output |
|---:|---|---|---|
| 71 | Causal language modeling | Theory | Understand next-token prediction |
| 72 | Tokenization: BPE / SentencePiece | Theory | Understand text-to-token conversion |
| 73 | Attention masking | Theory | Causal mask vs padding mask |
| 74 | Implement masked attention toy example | Practice | Verify blocked future positions |
| 75 | KV cache | Theory | Understand faster autoregressive decoding |
| 76 | Grouped-query attention | Theory | Reduce inference memory bandwidth |
| 77 | FlashAttention intuition | Theory | Avoid materializing full attention matrix |

## Week 12 — Low-Rank Adaptation and Compression

| Day | Topic / Sub-topic | Type | Practical Output |
|---:|---|---|---|
| 78 | Low-rank adaptation motivation | Theory | Why not full fine-tuning? |
| 79 | LoRA equation: `W' = W + BA` | Theory | Understand low-rank update |
| 80 | LoRA parameter count | Practice | Compare full update vs LoRA update |
| 81 | Implement minimal LoRA linear layer | Practice | Build toy `LoRALinear` |
| 82 | LoRA target modules | Theory | `q_proj`, `v_proj`, `o_proj`, MLP layers |
| 83 | QLoRA | Theory | Quantized base model + LoRA adapters |
| 84 | Knowledge distillation | Theory | Teacher-student compression |

---

# Optional Weekly Review Format

Use this every 7th day or during the weekend.

| Question | Purpose |
|---|---|
| What did I learn this week? | Consolidation |
| Which equation or mechanism matters most? | Mathematical memory |
| What did I implement or test? | Practical retention |
| Where would I use this at work? | Application |
| What still feels unclear? | Next step |

---

# Priority Order

If you do not want to follow all 84 days, prioritize these blocks.

| Priority | Block |
|---:|---|
| 1 | Calibration and uncertainty |
| 2 | Conformal prediction |
| 3 | Embedding geometry |
| 4 | Contrastive learning |
| 5 | Retrieval systems |
| 6 | RAG |
| 7 | LLM evaluation |
| 8 | KV cache / attention efficiency |
| 9 | LoRA / QLoRA |
| 10 | Drift monitoring |

---

# Daily Session Template

Use this fixed format for a normal 15-minute session.

| Minute | Activity |
|---:|---|
| 0–5 | Define the concept precisely |
| 5–10 | Study one equation, mechanism, or code snippet |
| 10–15 | Write three bullets: what it means, why it matters, where it is used |
| 15–30, optional | Implementation, paper detail, or deeper notes |



## My Questions


## References

