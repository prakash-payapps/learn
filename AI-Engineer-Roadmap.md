# Applied AI Engineer Roadmap – Complete Syllabus

---

## **MODULE 0: FIRST PRINCIPLES** (1-2 weeks)
*Foundational concepts before diving into LLM specifics*

### 0.1 Machine Learning Foundations (Intuition Only)
- **Supervised learning**: input → label mapping; training on examples
- **Unsupervised learning**: find structure without labels (clustering, dimensionality reduction)
- **Self-supervised learning**: learn from data itself (predict next word, masked tokens)
- **Loss functions**: measure error; training minimizes loss
- **Gradient descent**: iteratively adjust parameters to reduce loss
- **Overfitting vs generalization**: memorizing training data vs performing on new data
- **Train/validation/test splits**: why separate data matters

### 0.2 Neural Network Fundamentals
- **Neurons**: weighted sum of inputs + activation function
- **Layers**: stacking neurons for hierarchical features
- **Feedforward networks**: input → hidden → output (no loops)
- **Backpropagation**: compute gradients layer-by-layer to update weights
- **Activation functions**: ReLU, GELU, sigmoid, softmax—introducing non-linearity
- **Parameters vs hyperparameters**: learned weights vs tunable settings (learning rate, layers)
- **Batch size, epochs, learning rate**: training dynamics basics

### 0.3 Sequence Modeling Evolution
- **Why sequences matter**: language, time-series, audio are ordered
- **RNNs**: process sequences step-by-step, hidden state carries context (vanishing gradient problem)
- **LSTMs/GRUs**: gates to preserve long-range dependencies
- **Seq2seq**: encoder-decoder for translation, summarization
- **Attention mechanism**: let model focus on relevant parts of input, not just final hidden state
- **Self-attention**: each position attends to all positions (foundation of Transformers)

### 0.4 The Transformer Architecture
- **Why Transformers won**: parallelizable, scales with compute, handles long-range dependencies
- **Encoder-only**: BERT-style, bidirectional, good for classification/embeddings
- **Decoder-only**: GPT-style, autoregressive, good for generation
- **Encoder-decoder**: T5-style, good for seq2seq tasks
- **Multi-head attention**: multiple parallel attention computations for different relationships
- **Positional encoding**: inject sequence order (sinusoidal or learned)
- **Layer normalization**: stabilize training, applied pre/post attention
- **Feed-forward networks**: per-position MLP after attention
- **Residual connections**: skip connections to ease gradient flow

### 0.5 Language Model Pretraining
- **Causal language modeling (CLM)**: predict next token; GPT-style
- **Masked language modeling (MLM)**: predict masked tokens; BERT-style
- **Pretraining objective**: learn general language understanding from massive corpora
- **Transfer learning**: pretrained model → fine-tune on specific task
- **Emergent abilities**: capabilities that appear at scale (reasoning, in-context learning)
- **Scaling laws**: more data + compute + parameters → better performance (with diminishing returns)

### 0.6 Tokenization Deep Dive
- **Why tokenize**: convert text to numeric IDs model can process
- **Subword tokenization**: balance vocabulary size vs sequence length
- **BPE (Byte-Pair Encoding)**: merge frequent character pairs iteratively
- **WordPiece**: similar to BPE, used in BERT
- **SentencePiece/Unigram**: language-agnostic, handles unknown scripts
- **Token vocabulary size**: tradeoffs (50K–200K typical)
- **Special tokens**: `<|endoftext|>`, `[CLS]`, `[SEP]`, `<|im_start|>`
- **Token healing**: handle tokenization artifacts at prompt boundaries

### 0.7 Embeddings First Principles
- **Distributed representations**: meaning encoded in dense vectors, not one-hot
- **Word embeddings (Word2Vec, GloVe)**: static word vectors, context-independent
- **Contextual embeddings**: same word, different vectors based on context (BERT, GPT)
- **Embedding dimensions**: 384, 768, 1536, 3072—quality vs compute tradeoffs
- **Semantic similarity**: cosine distance measures meaning closeness
- **Embedding space geometry**: similar concepts cluster together

### 0.8 Inference & Generation
- **Autoregressive generation**: generate one token, feed back, repeat
- **Logits**: raw model outputs before softmax
- **Softmax**: convert logits to probability distribution
- **Sampling strategies**: greedy (argmax), top-k, top-p (nucleus), temperature
- **Temperature**: lower = more deterministic, higher = more random
- **Beam search**: explore multiple candidate sequences in parallel
- **Stop conditions**: max tokens, stop sequences, EOS token
- **KV cache**: store key/value pairs to avoid recomputation during generation

### 0.9 Fine-Tuning Fundamentals
- **Full fine-tuning**: update all model parameters on task data
- **Instruction tuning**: train on (instruction, response) pairs for chat/assistant behavior
- **RLHF (Reinforcement Learning from Human Feedback)**: reward model + PPO to align outputs
- **DPO (Direct Preference Optimization)**: simpler alternative to RLHF, no reward model
- **LoRA (Low-Rank Adaptation)**: train small adapter matrices, freeze base weights
- **QLoRA**: LoRA + quantized base model for memory efficiency
- **Catastrophic forgetting**: fine-tuning can degrade general capabilities
- **Overfitting on small datasets**: regularization, early stopping, validation monitoring

### 0.10 Quantization & Efficiency
- **FP32 → FP16 → BF16**: reduce precision for speed/memory, minimal quality loss
- **INT8/INT4 quantization**: further compression, some quality tradeoff
- **GGUF/GPTQ/AWQ**: popular quantization formats for local inference
- **Memory requirements**: ~2 bytes per parameter at FP16; 70B model ≈ 140GB
- **Inference optimization**: batching, speculative decoding, continuous batching
- **Mixture of Experts (MoE)**: route tokens to subset of parameters, scale efficiently

### 0.11 Information Retrieval Foundations
- **Inverted index**: map terms → documents containing them
- **TF-IDF**: term frequency × inverse document frequency for relevance scoring
- **BM25**: probabilistic ranking, still strong baseline for keyword search
- **Precision**: relevant retrieved / total retrieved
- **Recall**: relevant retrieved / total relevant
- **F1**: harmonic mean of precision and recall
- **NDCG/MRR/MAP**: rank-aware evaluation metrics

### 0.12 Vector Search Foundations
- **Dense retrieval**: embed query and docs, find nearest neighbors
- **Exact nearest neighbor**: brute force, O(n), accurate but slow
- **Approximate nearest neighbor (ANN)**: trade accuracy for speed
- **HNSW**: hierarchical navigable small world graphs, fast and accurate
- **IVF**: inverted file index, cluster-based search
- **Product quantization**: compress vectors, approximate distance
- **Hybrid search**: combine sparse (BM25) + dense (embeddings) for best results

### 0.13 Probability & Statistics Essentials
- **Probability distributions**: discrete (softmax output), continuous (embeddings)
- **Conditional probability**: P(A|B), foundation of autoregressive generation
- **Bayes' theorem**: update beliefs with evidence
- **Cross-entropy loss**: standard loss for next-token prediction
- **Perplexity**: exponentiated cross-entropy, measures model quality
- **Sampling from distributions**: temperature, top-k, top-p manipulate output distribution
- **Confidence calibration**: are predicted probabilities reliable?

### 0.14 Systems Thinking for AI
- **Latency vs throughput**: response time vs requests per second
- **Batching**: group requests for GPU efficiency
- **Caching**: reuse computations (prompt prefix, embeddings, responses)
- **Async vs sync**: non-blocking for I/O-bound operations
- **Horizontal vs vertical scaling**: more machines vs bigger machines
- **Cost model**: input tokens + output tokens + compute time + storage
- **Failure modes**: API timeouts, rate limits, model errors, data quality issues

---

## **MODULE 1: LLM FUNDAMENTALS** (2-3 weeks)

### 1.1 How LLMs Work (Conceptual, No Math)
- Tokenization: how text → numbers
- Context windows: token limits, implications for long docs
- Attention & generative behavior (intuition only, no formulas)
- Temperature, top-p, top-k: output behavior controls
- Model sizes: 7B, 13B, 70B, 405B tradeoffs (latency vs quality)
- Instruction tuning vs base models

### 1.2 LLM Providers & APIs (2026 State)
- **OpenAI**: GPT-5.5, o1/o3/o4 reasoning models, Responses API, structured outputs, Codex CLI, token counting
- **Anthropic**: Claude Opus 4.8, Sonnet 4, Haiku 4, Mythos Preview (highest capability), extended thinking, effort control (low/medium/high/extra/max), batch API, dynamic workflows
- **Google**: Gemini 3.5 Flash, Gemini 3.1 Pro, Vertex AI integration
- **DeepSeek**: R1/V3 models, locally hosted and API-based reasoning
- **Open Source**: Llama 4, Mistral Large, Phi-4, OLMo, Mellum2 (JetBrains 12B MoE), Nemotron-Labs Diffusion LMs
- **AWS**: Bedrock (multi-model), Nova models, Converse API, Agents/AgentCore, Knowledge Bases, Guardrails, pricing tiers
- **Azure**: OpenAI Service, Microsoft Foundry, OpenAI on Your Data
- **Provider abstraction**: SDK wrappers, model gateways, failover across vendors, LiteLLM for unified API

### 1.3 API Essentials
- Authentication: API keys, rotating secrets, env variables
- Rate limiting: quota management, backoff strategies
- Error handling: token exceeded, context length, rate limits, timeouts
- Token counting: libraries & estimation before API calls
- Streaming vs non-streaming responses, SSE handling
- Cost calculation: input/output tokens, batch pricing
- **Mid-conversation system updates**: system entries in messages array (update permissions, budgets, context mid-task without breaking cache)
- **Fast mode**: 2-3× speed at higher cost for latency-sensitive tasks

### 1.4 Prompt Engineering Fundamentals
- **System prompts**: context, persona, guardrails, tone
- **Few-shot learning**: examples in prompt, when to use (2-5 examples typical)
- **Chain-of-thought (CoT)**: "think step by step"
- **Zero-shot vs few-shot trade-offs**
- **Prompt templates**: dynamic variable injection, escape sequences
- **Persona patterns**: expert mode, Socratic questioning
- **Structured output prompts**: JSON, XML schemas
- **Negative prompts**: what NOT to do (less effective than positive)
- **Reasoning model prompting**: don't add "think step-by-step" (model reasons internally); avoid explicit CoT examples in few-shot; use short, direct instructions; set thinking budget (low/medium/high/budget_tokens param); expect latency increase proportional to reasoning depth

### 1.5 Model Selection & Routing
- **Task-model fit**: use small models for extraction/classification, stronger models for reasoning
- **Reasoning effort**: tune low/medium/high reasoning for cost vs quality
- **Model snapshots**: pin production versions, test before upgrades
- **Routing policies**: choose model by task type, latency, cost, risk, region
- **Fallbacks**: retry with backup provider/model on outage or quality failure
- **Long-context vs RAG**: know when to stuff context vs retrieve selectively

### 1.6 Context & Conversation Management
- **Conversation state**: previous response IDs, stored history, resumable sessions
- **Context compaction**: summarize old turns, keep durable facts
- **Instruction hierarchy**: system/developer/user/tool priority
- **Prompt caching**: reuse stable prompt prefixes to reduce cost/latency
- **Context budget**: allocate tokens across instructions, history, tools, retrieval, output

---

## **MODULE 2: EMBEDDINGS & VECTOR SEARCH** (2 weeks)

### 2.1 Embeddings Basics
- What embeddings are: dense vectors representing semantic meaning
- Embedding models: text-embedding-3-small, -large, Voyage, Cohere
- Dimensions: 384, 768, 1536, 3072—quality vs storage/latency
- Cosine similarity: measuring vector distance
- Embedding APIs: batch vs streaming, costs per 1M tokens

### 2.2 Vector Databases
- **Postgres pgvector**: native, ACID, good for <10M vectors
- **Pinecone**: managed, serverless, metadata filtering
- **Weaviate**: hybrid search, GraphQL interface
- **Milvus**: open-source, deployment options
- **Qdrant**: fast, Rust-based
- **Opensearch**: built on Elasticsearch, AWS native
- **Chroma**: lightweight, SQLite backend for local dev
- **Redis Stack**: in-memory, fast retrieval

### 2.3 Vector Search Patterns
- Exact nearest-neighbor search (slow, accurate)
- Approximate nearest-neighbor (ANN): IVF, HNSW, product quantization
- Metadata filtering: hybrid filtering + vector search
- Dense + sparse search: keyword + semantic combined
- Reranking: retrieve 100, rerank top 10 for quality
- MMR (maximum marginal relevance): diverse results

### 2.4 Chunking & Embedding Strategies
- Chunk size: 256–1024 tokens typical, overlap 50–100 tokens
- Hierarchical chunking: summaries of summaries
- Semantic chunking: chunks from logical boundaries
- Sliding windows: overlapping for context
- Metadata extraction: docs → {text, source, date, category}
- Embedding refresh: stale vs fresh data

### 2.5 Search Relevance Tuning
- Query normalization: spelling, abbreviations, synonyms
- Filter-first vs vector-first retrieval tradeoffs
- Domain-specific synonyms and taxonomy mapping
- Relevance feedback: clicks, accepted answers, user corrections
- Index lifecycle: rebuilds, migrations, blue-green index swaps
- PII-aware indexing: redact or tokenize sensitive fields before embedding

---

## **MODULE 3: RETRIEVAL-AUGMENTED GENERATION (RAG)** (3 weeks)

### 3.1 RAG Architecture
- **Basic RAG**: query → retrieve docs → augment prompt → generate
- **Phases**: indexing, retrieval, generation
- **Naive RAG**: simple retriever + LLM (baseline to improve)
- **Advanced RAG**: multi-hop, fusion, decomposition
- **Modular RAG**: pluggable retrieval strategies

### 3.2 Indexing Pipelines
- Document ingestion: PDF, Word, HTML, Markdown parsing
- Extractors: PyPDF2, pdfplumber, unstructured, LangChain loaders
- Text cleaning: remove headers/footers, normalize whitespace
- Chunking strategies: fixed-size, semantic, hierarchical, rolling window
- Metadata attachment: source, page number, timestamps, categories
- De-duplication: hash-based, semantic clustering
- Incremental indexing: batch vs real-time updates

### 3.3 Retrieval Strategies
- **BM25** (keyword search): statistical ranking, baseline
- **Vector search**: semantic similarity via embeddings
- **Hybrid search**: combine BM25 + vector, weighted ensemble
- **Query expansion**: paraphrase, multi-hop decomposition
- **Query rewriting**: correct typos, expand abbreviations
- **Contextual retrieval**: use conversation history for better queries
- **Retrieval fusion**: RRF (reciprocal rank fusion), weighted voting
- **Re-ranking**: LLMRank, cross-encoder models, ColBERT

### 3.4 Augmentation Techniques
- **In-context learning**: few-shot examples + retrieved docs in prompt
- **Chunk formatting**: organize retrieved chunks, cite sources
- **Context window optimization**: fit max docs in limited tokens
- **Prompt structure**: separate instructions, context, query
- **Prompt reduction**: summarize retrieved docs before inclusion

### 3.5 Evaluation & Iteration
- **Retrieval quality**: precision, recall, NDCG, MRR
- **Generation quality**: BLEU, ROUGE, METEOR (not ideal for LLMs)
- **User satisfaction**: coherence, relevance, hallucination metrics
- **RAG benchmarks**: TREC, MS MARCO, Natural Questions
- **A/B testing**: baseline vs new retrieval strategy
- **Feedback loops**: user corrections → retraining signals

### 3.6 Advanced RAG Patterns
- **Multi-hop reasoning**: chain retrievals for complex queries
- **Recursive retrieval**: top result → refine query → retrieve again
- **Iterative refinement**: loop: generate query → retrieve → judge relevance → continue
- **Query routing**: classify query type → route to specialist retrievers
- **Fusion RAG**: combine multiple retrievers (web, local docs, knowledge base)
- **Self-RAG**: LLM decides when to retrieve mid-generation
- **Corrective RAG (CRAG)**: evaluate retrieval quality, re-retrieve if needed

### 3.7 RAG Governance & Freshness
- Source authority: rank official/internal sources over weak sources
- Freshness policy: expire outdated chunks, re-crawl changed documents
- Citation verification: ensure answer claims map to retrieved source text
- Access control: enforce document permissions before retrieval and generation
- Multi-tenant isolation: separate indexes, metadata filters, tenant keys
- Grounded refusal: answer "not found" when sources do not support answer

---

## **MODULE 4: AGENTIC SYSTEMS & ORCHESTRATION** (3-4 weeks)

### 4.1 Agent Fundamentals
- **Agents vs chains**: agents have decision-making, chains are linear
- **Agent loop**: sense → reason → act → observe
- **Agent types**: simple (fixed workflow), complex (dynamic planning)
- **Planning strategies**: ReAct (reason + act), tree-of-thought, graph-based
- **Tool calling**: LLM selects from available tools, gets results
- **Memory types**: short-term (session), long-term (vector DB), episodic
- **Named workflow patterns** (Anthropic canonical):
  - *Prompt chaining*: sequential LLM calls, each processes previous output
  - *Routing*: classify input → dispatch to specialized handler
  - *Parallelization*: sectioning (subtasks in parallel) + voting (same task N times)
  - *Orchestrator-workers*: central LLM breaks task → delegates to worker LLMs → synthesizes
  - *Evaluator-optimizer*: generator LLM + evaluator LLM in a refinement loop
- **Agent-computer interface (ACI)**: design tools with the same care as HCI—clear descriptions, unambiguous params, example usage, poka-yoke inputs
- **When NOT to use agents**: single-step tasks, latency-sensitive paths, deterministic workflows—start simple

### 4.2 Tool Design
- **Tool definitions**: name, description, parameters (JSON schema)
- **Tool execution**: error handling, input validation, timeout
- **Observability**: log tool calls, timing, success/failure rates
- **Parallel tool calling**: execute multiple tools simultaneously
- **Tool composition**: tools that invoke other tools
- **Custom tools**: wrap APIs, databases, internal services
- **Built-in tool categories**: search, calculation, code execution, database queries

### 4.3 Agent Frameworks & Libraries
- **LangChain/LangGraph**: Agent executor, tool binding, memory management, graph-based orchestration
- **LlamaIndex**: agent builder with RAG integration
- **AutoGPT patterns**: open-ended task completion, checkpoint recovery
- **Crew AI**: multi-agent teams with roles
- **OpenAI Assistants API**: persistent state, file handling, retrieval
- **MCP (Model Context Protocol)**: standard tool/data connector protocol
- **Bedrock Agents/AgentCore**: AWS-native managed agent runtime patterns
- **Strands Agents SDK**: AWS open-source agent SDK, model-agnostic, built-in tools
- **Claude Agent SDK**: Anthropic SDK for building Claude-backed agents
- **Claude Code**: AI coding agent with dynamic workflows, parallel subagents, codebase-scale migrations
- **Claude Cowork**: collaborative AI work environment
- **Claude Design (Anthropic Labs)**: visual design, prototypes, slides, one-pagers
- **Custom orchestration**: build agents with raw API calls

### 4.4 Multi-Agent Systems
- **Agent teams**: divvy up tasks (researcher, analyst, writer)
- **Agent communication**: message queues, shared state
- **Coordination patterns**: sequential, hierarchical, consensus-based
- **Debate/discussion**: agents argue viewpoints, LLM judges winner
- **Specialization**: different agents for different domains/skills
- **Scaling**: agent pool management, workload distribution

### 4.5 Memory Management
- **Conversation history**: store all turns, summarize old turns
- **Semantic memory**: embeddings of facts, retrieve relevant facts
- **Episodic memory**: events, timestamps, replay for planning
- **Procedural memory**: learned workflows, tried-and-failed paths
- **Memory pruning**: forget irrelevant details, keep core facts
- **Vector DB for long-term memory**: embedding conversations, querying by topic

### 4.6 Planning & Reasoning
- **ReAct pattern**: interleave thought + action, observe results
- **Tree-of-thought**: explore multiple reasoning paths
- **Self-correction**: generate answer → check → revise if wrong
- **Chain-of-thought prompting**: "think step-by-step"
- **Decomposition**: split complex task into subtasks
- **Backward chaining**: start with goal, work backward to subgoals

### 4.7 Agent State Management
- **Persistence**: save/restore agent state across sessions
- **Checkpoint recovery**: resume after failures
- **Rollback mechanisms**: undo failed actions
- **Conversation context**: maintain context across tool calls
- **State serialization**: JSON/pickle for storage

### 4.8 Human-in-the-Loop Agents
- **Approval gates**: require human approval before external actions
- **Interrupt/resume**: pause workflows for clarification or review
- **Escalation paths**: route low-confidence or risky tasks to people
- **Auditability**: record plan, tool calls, approvals, outputs
- **Bounded autonomy**: budget, time, tool, permission, and scope limits

---

## **MODULE 5: STRUCTURED OUTPUTS & FUNCTION CALLING** (2 weeks)

### 5.1 Structured Output Formats
- **JSON mode**: force valid JSON output
- **XML output**: structured markup
- **Schema enforcement**: JSON Schema, Pydantic models
- **CSV/TSV**: tabular data extraction
- **Key-value pairs**: attribute extraction

### 5.2 Function Calling (Tool Use)
- **Function definitions**: name, description, parameters, parameter types
- **Parameter validation**: required vs optional, enums, defaults
- **Function calling flow**: generate function calls → execute → feed results
- **Parallel function calls**: invoke multiple functions in one turn
- **Nested function calls**: functions that call other functions
- **Error handling**: invalid args, execution failures, timeouts
- **Cost of function calls**: token overhead for definitions
- **Idempotency**: avoid duplicate side effects on retry
- **Tool permissions**: read-only vs write-capable tool boundaries
- **Dry-run mode**: preview actions before execution

### 5.3 Extraction & Classification
- **Entity extraction**: find people, places, dates in text
- **Classification**: assign categories, labels, sentiment
- **Information extraction**: structured data from unstructured text
- **Relationship extraction**: connections between entities
- **Slot filling**: populate forms from text
- **Validation**: ensure extracted data matches schema

### 5.4 Pydantic & Schema Definition
- **Pydantic models**: Python-native schema validation
- **Field types**: str, int, float, bool, Enum, List, Dict
- **Constraints**: min/max, regex patterns, custom validators
- **Nested models**: hierarchical schemas
- **Optional vs required**: default values
- **JSON schema generation**: from Pydantic → JSON Schema

---

## **MODULE 6: LLM APPLICATIONS PATTERNS** (3 weeks)

### 6.1 Question-Answering Systems
- **Open-domain QA**: answer any question using retrieval
- **Closed-domain QA**: answer questions about specific docs
- **Multi-turn QA**: follow-up questions, context preservation
- **Conversational QA**: chatbot-style interactions
- **Fact verification**: check if answer is grounded in retrieved docs
- **Attribution**: cite sources for claims

### 6.2 Content Generation
- **Document generation**: reports, summaries, analyses
- **Code generation**: write code from requirements, fix bugs
- **Email/message drafting**: personalized communication
- **Article writing**: long-form content with outline → draft → polish
- **Creative writing**: stories, poetry, scenarios
- **Localization**: translate content, cultural adaptation
- **Style transfer**: rewrite in different tones/styles

### 6.3 Summarization
- **Extractive**: select key sentences from source
- **Abstractive**: generate summary from understanding
- **Multi-document**: combine info from multiple sources
- **Query-focused**: summarize with specific question in mind
- **Hierarchical**: summary of summaries for very long docs
- **Temporal**: evolving summaries as more data arrives

### 6.4 Classification & Tagging
- **Text classification**: category assignment (topic, sentiment, intent)
- **Multi-label classification**: multiple tags per item
- **Fine-grained classification**: many categories (200+), hierarchical
- **Zero-shot classification**: classify with no training examples
- **Few-shot classification**: use examples in prompt
- **Confidence scores**: how sure is the model?
- **Class imbalance**: handle skewed category distributions

### 6.5 Semantic Search & Matching
- **Document search**: find similar docs
- **Passage ranking**: rank documents by relevance
- **Cross-lingual retrieval**: search in different languages
- **Multimodal matching**: text query → image results (or vice versa)
- **Typo tolerance**: fuzzy matching
- **Faceted search**: filter by metadata + semantic relevance

### 6.6 Named Entity Recognition (NER)
- **Entity extraction**: find people, places, orgs, dates, money
- **Entity linking**: connect mentions to canonical entities (Wikipedia)
- **Custom entities**: domain-specific entities (drug names, codes)
- **Nested entities**: entities within entities
- **Coreference resolution**: which "it" refers to which entity?

### 6.7 Information Extraction
- **Slot filling**: extract specific fields from text
- **Fact extraction**: triples (subject, relation, object)
- **Event extraction**: who did what, when, where, why
- **Structured data generation**: convert text → JSON/CSV
- **Table extraction**: parse tables from text/images

### 6.8 Recommendation Systems
- **Content-based**: recommend similar items
- **Collaborative**: recommend based on user history
- **Hybrid**: combine content + collaborative
- **Context-aware**: recs based on current state
- **Explanation generation**: why this recommendation?

### 6.9 Code Tasks
- **Code generation**: write functions, scripts from requirements
- **Code explanation**: explain what code does
- **Bug detection**: find logical/performance bugs
- **Code review**: provide feedback on code
- **Refactoring**: improve code quality
- **Documentation generation**: docstrings, README
- **Debugging assistance**: help fix errors

### 6.10 Chatbots & Conversational AI
- **Intent detection**: understand what user wants
- **Slot filling**: extract parameters from user input
- **Dialog management**: track conversation state, next actions
- **Context awareness**: use previous turns
- **Fallback handling**: "I don't know, let me escalate"
- **Personalization**: remember user preferences
- **Tone management**: empathy, professionalism

### 6.11 Voice, Realtime & Multimodal Apps
- **Speech-to-text**: transcribe calls, meetings, voice commands
- **Text-to-speech**: generate natural voice responses
- **Realtime APIs**: low-latency bidirectional audio/text sessions
- **Vision input**: screenshots, diagrams, invoices, forms, photos
- **Image/video generation**: produce visual assets, storyboards, short clips
- **OCR + LLM**: extract and reason over scanned documents

### 6.12 AI-Native UX Patterns
- **Progressive disclosure**: show intermediate progress for slow tasks
- **Citations and confidence**: make uncertainty visible without clutter
- **Editable outputs**: let users correct, regenerate, refine
- **Conversation recovery**: resume interrupted sessions
- **Explainable actions**: show what tool/action changed user data
- **Trust boundaries**: label generated content and source-backed content

---

## **MODULE 7: DEPLOYMENT & INFRASTRUCTURE** (3-4 weeks)

### 7.1 AWS Services for AI
- **Bedrock**: managed LLM service, multi-model, no infra overhead
- **Bedrock Knowledge Bases**: managed RAG over enterprise data
- **Bedrock Guardrails**: safety filters, denied topics, sensitive data controls
- **Bedrock Agents/AgentCore**: managed agent orchestration and tool execution
- **SageMaker**: full ML platform (hosting, training, inference)
- **Lambda**: serverless functions, invoke LLM APIs
- **API Gateway**: expose Lambda via HTTP
- **DynamoDB**: NoSQL, good for conversation history
- **RDS/Aurora**: relational DB for structured data
- **ElastiCache/MemoryDB**: in-memory caching, vector DB-lite
- **S3**: document storage, retrieval source
- **CloudFront**: CDN for static assets
- **EventBridge**: trigger workflows, event-driven architecture
- **SQS/SNS**: async messaging, notifications
- **Step Functions**: orchestrate multi-step workflows
- **Secrets Manager**: API key rotation
- **VPC/Security Groups**: network isolation

### 7.2 Containerization
- **Docker**: package apps with dependencies
- **Dockerfile**: build images, multi-stage builds
- **ECR (Elastic Container Registry)**: AWS image repository
- **Container optimization**: layer caching, size reduction
- **Image scanning**: vulnerability checks
- **Container registries**: DockerHub, Quay, ECR

### 7.3 Orchestration & Scaling
- **ECS**: Docker orchestration on AWS
- **EKS**: Kubernetes on AWS (overkill for most AI apps)
- **Auto-scaling**: scale based on demand (CPU, custom metrics)
- **Load balancing**: ALB/NLB distribute traffic
- **Health checks**: monitor service health, auto-restart
- **Blue-green deployment**: zero-downtime updates
- **Canary deployment**: roll out to subset first

### 7.4 Serverless Deployment
- **Lambda**: stateless, event-driven, cost-per-invocation
- **Function configuration**: memory, timeout, environment vars
- **Cold starts**: first invocation latency, optimization
- **Concurrency limits**: concurrent execution caps
- **Package size**: code + dependencies < 250MB
- **Layers**: shared code across functions
- **API Gateway**: REST API on top of Lambda

### 7.5 Databases for AI Applications
- **Conversation history**: DynamoDB (partition key: user_id, sort key: timestamp)
- **Vector storage**: Postgres pgvector, Pinecone, Weaviate (covered in Module 2)
- **Metadata**: RDS (MySQL/Postgres) for structured data
- **Caching**: Redis/ElastiCache for hot data
- **Audit logs**: CloudWatch Logs, S3 for archive
- **Real-time analytics**: Kinesis, DynamoDB Streams

### 7.6 API Design for AI
- **REST principles**: resources, methods, status codes
- **Request structure**: input format, parameters, authentication
- **Response format**: JSON payload, error messages
- **Versioning**: /v1/chat, /v2/chat for backward compat
- **Rate limiting**: requests per second/minute, quota per user
- **Pagination**: cursor-based for large result sets
- **Caching headers**: ETag, Last-Modified for efficiency
- **CORS**: cross-origin resource sharing for web clients

### 7.7 Configuration Management
- **Environment variables**: API keys, model selection, feature flags
- **Config files**: YAML/JSON, environment-specific
- **Secrets rotation**: periodic key updates
- **Feature flags**: enable/disable features without deployment
- **A/B testing**: route users to variants
- **Deployment strategies**: rolling, blue-green, canary

### 7.8 Infrastructure as Code
- **Terraform/CDK/CloudFormation**: reproducible AI infrastructure
- **Environment parity**: dev/stage/prod consistency
- **Policy as code**: IAM, networking, encryption, guardrail config
- **Secrets wiring**: least-privilege access from app to model provider
- **Drift detection**: detect manual infrastructure changes

### 7.9 Model Serving & Local Inference
- **vLLM/TGI/Ollama/llama.cpp**: serve open-weight models locally or in VPC
- **Quantization**: reduce memory/cost with acceptable quality loss
- **GPU sizing**: match model size, context length, concurrency
- **Autoscaling inference**: scale by queue depth, latency, GPU utilization
- **Private endpoints**: keep inference traffic inside VPC where required

---

## **MODULE 8: MONITORING, OBSERVABILITY & LOGGING** (2-3 weeks)

### 8.1 Metrics & Monitoring
- **Key metrics**: latency (p50, p99), throughput, error rate, cost per request
- **Model-specific**: token count, response quality, hallucination rate
- **Business metrics**: user satisfaction, task completion rate
- **Infrastructure**: CPU, memory, network, disk usage
- **CloudWatch**: AWS native monitoring, dashboards, alarms
- **Alerting**: PagerDuty, OpsGenie for on-call

### 8.2 Logging Best Practices
- **Log levels**: DEBUG, INFO, WARNING, ERROR, CRITICAL
- **Structured logging**: JSON logs for parsing
- **Correlation IDs**: track requests across services
- **PII redaction**: remove sensitive data from logs
- **Log retention**: S3 archive after 90 days
- **Log analysis**: CloudWatch Insights, DataDog, Splunk

### 8.3 Distributed Tracing
- **Span creation**: start/end times for operations
- **Trace propagation**: pass trace IDs across services
- **LLM trace tools**: LangChain tracing, LlamaIndex callbacks
- **AWS X-Ray**: distributed tracing for AWS services
- **Jaeger/Zipkin**: open-source tracing systems
- **Sampling**: trace every request or sample (1 in 100)

### 8.4 LLM-Specific Observability
- **Prompt tracking**: log prompts, model, temperature
- **Output quality**: flag hallucinations, off-topic responses
- **Token efficiency**: track token usage, cost per query
- **Latency breakdown**: time in LLM API vs retrieval vs overhead
- **Cost analysis**: spend per user, per feature, trend over time
- **Model changes**: measure impact of switching models
- **Feedback collection**: user thumbs up/down, corrections
- **Langfuse**: open-source LLMOps platform — tracing, prompt management, evals, cost, self-hostable
- **Arize/Phoenix**: LLM observability with embedding drift detection and hallucination scoring
- **Helicone**: lightweight proxy-based tracing and cost monitoring, zero code change
- **LiteLLM**: unified LLM proxy — single API across 100+ models, with logging and spend controls

### 8.5 Debugging & Troubleshooting
- **Request replay**: re-run failed requests with same inputs
- **Log inspection**: examine full flow for a request
- **Breakpoints**: debug mode with interactive inspection
- **Synthetic tests**: monitor critical paths 24/7
- **Error categorization**: group errors, find patterns
- **Root cause analysis**: trace error to source

### 8.6 Performance Optimization Monitoring
- **Slow query detection**: identify slow LLM calls, retrievals
- **Cost anomalies**: detect unusual spend spikes
- **Token usage patterns**: which queries are expensive?
- **Cache hit rates**: how often do we reuse results?
- **Retrieval quality**: are we getting good documents?

### 8.7 Prompt & Agent Tracing
- **Prompt lineage**: prompt version, variables, retrieved chunks, model snapshot
- **Agent traces**: plan steps, tool calls, observations, retries
- **Tool-level metrics**: success rate, error type, latency, side effects
- **Eval trace replay**: replay production traces against new prompts/models
- **Privacy controls**: scrub secrets and PII before storing traces

---

## **MODULE 9: SECURITY & COMPLIANCE** (2-3 weeks)

### 9.1 API Security
- **Authentication**: API keys, OAuth 2.0, OIDC
- **Authorization**: role-based access control (RBAC), scopes
- **Rate limiting**: prevent abuse, DDoS mitigation
- **IP whitelisting**: restrict to known IPs
- **HTTPS/TLS**: encrypt in-transit
- **Request signing**: AWS Signature Version 4 for AWS APIs
- **Token expiration**: short-lived tokens, refresh tokens

### 9.2 Data Privacy
- **Data classification**: public, internal, confidential, restricted
- **PII handling**: redact, encrypt, minimize collection
- **Data retention**: delete after period (30/90/365 days)
- **GDPR compliance**: right to be forgotten, data portability
- **Data residency**: keep data in specific regions
- **Cross-border data transfer**: compliance with regulations
- **Audit logging**: who accessed what data, when

### 9.3 LLM Security
- **Prompt injection**: prevent users from jailbreaking model
- **Indirect prompt injection**: malicious instructions hidden in retrieved docs/web pages
- **Input validation**: sanitize user input
- **Output filtering**: block harmful content
- **Confidentiality**: don't leak sensitive data in responses
- **Model poisoning**: prevent malicious fine-tuning
- **API key exposure**: rotate exposed keys immediately
- **Model versioning**: track which version produced output
- **Tool misuse**: restrict write tools, shell tools, browsers, email, payments
- **Data exfiltration**: block prompts that try to reveal secrets or hidden context

### 9.4 Compliance Frameworks
- **SOC 2 Type II**: security, availability, processing integrity
- **HIPAA**: healthcare data protection (if handling health data)
- **PCI-DSS**: payment card data protection
- **FedRAMP**: federal government cloud requirements
- **ISO 27001**: information security management
- **NIST**: cybersecurity framework

### 9.5 Infrastructure Security
- **VPC isolation**: private subnets, security groups
- **Encryption at rest**: S3, RDS encryption, KMS keys
- **Encryption in-transit**: TLS, AWS PrivateLink
- **IAM policies**: least privilege, service roles
- **Secrets management**: AWS Secrets Manager, HashiCorp Vault
- **Vulnerability scanning**: ECR image scans, dependency checks
- **Intrusion detection**: CloudTrail for audit logs

### 9.6 Secure Coding
- **Input validation**: sanitize all user inputs
- **Output encoding**: prevent injection attacks
- **Error messages**: don't reveal system details
- **Dependencies**: keep packages updated
- **Code review**: peer review before merge
- **Security testing**: SAST, DAST tools

### 9.7 AI Guardrails & Red Teaming
- **OWASP Top 10 for LLM Apps 2025** (LLM01–LLM10): prompt injection, sensitive info disclosure, supply chain vulnerabilities, data/model poisoning, improper output handling, excessive agency, system prompt leakage, vector/embedding weaknesses, misinformation, unbounded consumption
- **Agent Governance**: execution sandboxing, zero-trust identity (e.g., Microsoft Agent Governance Toolkit)
- **Content moderation**: safety classifiers before/after generation
- **Policy checks**: deny topics, regulated advice, brand/legal restrictions
- **Adversarial testing**: jailbreaks, unsafe tool calls, malicious documents
- **Abuse monitoring**: suspicious usage, credential stuffing, scraping
- **Guardrail bypass testing**: verify filters fail closed where needed

### 9.8 Responsible AI & Governance
- **Risk classification**: low/medium/high-risk AI use cases
- **Human oversight**: required review for high-impact decisions
- **Transparency**: disclose AI use where appropriate
- **Bias testing**: check disparate impact across user groups
- **Data consent**: track rights for training, retrieval, logging
- **AI inventory**: catalogue models, prompts, datasets, owners, risks

---

## **MODULE 10: EVALUATION & QUALITY ASSURANCE** (2-3 weeks)

### 10.1 LLM Output Quality Metrics
- **Relevance**: does output answer the question?
- **Factuality**: are claims supported by sources?
- **Coherence**: does output make sense, flow well?
- **Completeness**: did it cover all aspects?
- **Tone appropriateness**: formal, casual, empathetic?
- **Hallucination detection**: flag made-up facts
- **Citation accuracy**: sources actually support claims

### 10.2 Evaluation Frameworks
- **BLEU/ROUGE/METEOR**: token-level metrics (weak for LLMs)
- **Human evaluation**: expert judges rate outputs
- **Pairwise comparison**: which output is better?
- **Rubrics**: detailed scoring criteria per dimension
- **Inter-rater agreement**: kappa, correlation between judges
- **Automated metrics**: LLM-as-judge (use strong model to evaluate)
- **Evals as code**: version eval datasets, rubrics, scorers, thresholds
- **Golden datasets**: curated examples for regression testing

### 10.3 Retrieval Evaluation
- **Precision**: % of retrieved docs that are relevant
- **Recall**: % of relevant docs that are retrieved
- **NDCG (Normalized Discounted Cumulative Gain)**: rank-aware metric
- **MRR (Mean Reciprocal Rank)**: position of first relevant result
- **MAP (Mean Average Precision)**: average precision at each position
- **Benchmarks**: MS MARCO, TREC, SQuAD for comparison

### 10.4 End-to-End Testing
- **Unit tests**: test individual functions, helpers
- **Integration tests**: test components together
- **Regression tests**: ensure changes don't break existing features
- **Smoke tests**: basic sanity checks after deployment
- **Load testing**: behavior under high traffic
- **Stress testing**: push to breaking point
- **Chaos testing**: inject failures, verify resilience

### 10.5 A/B Testing
- **Control vs treatment**: compare two versions
- **Metrics selection**: what to measure?
- **Sample size**: statistical power calculation
- **Randomization**: unbiased assignment
- **Statistical significance**: p-value < 0.05
- **Minimum detectable effect**: smallest meaningful difference
- **Multi-armed bandit**: adaptive allocation to better variant

### 10.6 User Feedback Loops
- **Thumbs up/down**: simple preference signal
- **Corrections**: user fixes LLM mistakes
- **Annotations**: label data for evaluation
- **Surveys**: structured feedback collection
- **Session replay**: understand user interaction
- **Churn analysis**: why did users leave?

### 10.7 Benchmarking
- **Public benchmarks**: compare to baseline, competitors
- **Custom benchmarks**: tailored to your use case
- **Regression testing**: track performance over time
- **Model comparison**: closed-source vs open-weight vs managed cloud models
- **Cost vs quality**: throughput, latency trade-offs

### 10.8 Agent & Tool Evaluation
- **Task success rate**: did the agent complete objective?
- **Step efficiency**: number of tool calls, retries, wasted actions
- **Tool correctness**: right tool, right parameters, right timing
- **Safety violations**: unauthorized writes, policy breaches, risky actions
- **Trajectory grading**: evaluate full reasoning/action path, not final answer only
- **Human approval metrics**: approval rate, rejection reasons, escalation rate

### 10.9 Prompt Testing
- **Prompt unit tests**: expected structure, required fields, refusal behavior
- **Snapshot tests**: detect output drift after model/prompt change
- **Metamorphic tests**: same meaning with varied wording should behave similarly
- **Adversarial prompt tests**: injection, contradiction, ambiguous instructions
- **Canary prompts**: quick smoke tests before deployment

---

## **MODULE 11: COST OPTIMIZATION & EFFICIENCY** (2 weeks)

### 11.1 Token Economics
- **Token pricing**: input tokens cheaper than output
- **Token counting**: estimate before API call
- **Batch API**: 50% discount for non-time-sensitive requests
- **Token compression**: more efficient prompting
- **Caching**: avoid re-processing same inputs
- **Model selection**: smaller models for simple tasks
- **Reasoning tokens**: hidden reasoning budget can affect cost/latency

### 11.2 Cost Optimization Techniques
- **Prompt optimization**: shorter prompts = fewer tokens
- **Few-shot learning**: examples in prompt vs fine-tuning
- **Summarization**: compress long docs before processing
- **Context compression**: token optimization for RAG payloads and extensive context windows (e.g. headroom)
- **Filtering**: don't process irrelevant data
- **Batch processing**: accumulate requests, process in bulk
- **Local models**: run small models locally to save API costs
- **Fallback models**: use cheaper models first, upgrade on failure
- **Semantic cache**: reuse answers for similar questions, not exact matches only
- **Prompt prefix cache**: keep stable instructions/context at prompt front
- **Model cascade**: small model tries first, strong model handles hard cases

### 11.3 Latency Optimization
- **Parallel retrieval**: retrieve multiple docs simultaneously
- **Asynchronous processing**: don't block on LLM response
- **Caching**: cache frequently-used results
- **Compression**: reduce network payload
- **Connection pooling**: reuse HTTP connections
- **Model selection**: faster models for real-time use cases
- **Regional endpoints**: serve from nearest region

### 11.4 Infrastructure Optimization
- **Reserved instances**: pre-purchase capacity at discount
- **Spot instances**: cheap transient resources
- **Auto-scaling**: scale down when idle
- **Resource right-sizing**: don't over-provision
- **Database optimization**: indexing, query efficiency
- **Storage optimization**: delete old data, compress
- **Network optimization**: minimize data transfer

### 11.5 Monitoring Costs
- **Cost per request**: track spending by feature, user, model
- **Cost trends**: identify sudden spikes
- **Budget alerts**: notify when spending exceeds threshold
- **Cost attribution**: allocate to cost centers
- **ROI analysis**: revenue per feature vs cost
- **Forecasting**: predict future spending

### 11.6 Quotas & Spend Controls
- **Per-user quotas**: daily/monthly request and token limits
- **Per-tenant budgets**: stop noisy customers from consuming shared budget
- **Circuit breakers**: stop traffic during cost spikes or provider incidents
- **Cost allocation tags**: team, product, environment, tenant, feature
- **Usage dashboards**: self-service visibility for engineering/product teams

---

## **MODULE 12: PRODUCTION PATTERNS & ARCHITECTURE** (3-4 weeks)

### 12.1 Reference Architectures
- **Simple chatbot**: Lambda + Bedrock + DynamoDB
- **RAG system**: Lambda + Bedrock + RDS + Pinecone
- **Multi-agent**: ECS + Lambda + SQS + RDS
- **High-throughput**: Bedrock + SageMaker + Aurora
- **Async processing**: EventBridge + Lambda + S3 + SNS
- **Realtime assistant**: WebSocket/WebRTC + streaming model API + session store
- **Enterprise assistant**: SSO + RBAC + RAG + audit logs + guardrails

### 12.2 Error Handling & Resilience
- **Retry logic**: exponential backoff, max retries
- **Circuit breaker**: stop calling failing service temporarily
- **Fallback strategy**: use backup model, local response
- **Timeout handling**: define max wait time per operation
- **Graceful degradation**: partial results better than failure
- **Dead letter queues**: capture failed messages for inspection
- **Request deduplication**: avoid processing same request twice

### 12.3 State Management
- **Session state**: remember user context
- **Conversation history**: store turns for context
- **Agent state**: checkpoints for resuming work
- **Persistence layer**: database for durability
- **Cache invalidation**: know when to refresh state
- **Distributed state**: coordination across instances

### 12.4 Versioning & Rollout
- **Model versioning**: track which model produced output
- **Prompt versioning**: version control for prompts
- **API versioning**: /v1/, /v2/ endpoints
- **Blue-green deployment**: switch traffic between versions
- **Canary deployment**: roll out to small % first
- **Rollback capability**: revert to previous version quickly
- **Shadow traffic**: test new version on copy of production traffic

### 12.5 High Availability
- **Multi-region**: deploy to multiple AWS regions
- **Multi-AZ**: spread across availability zones
- **Load balancing**: distribute traffic
- **Failover**: automatic switchover on failure
- **Data replication**: copies in multiple locations
- **RPO/RTO**: recovery point & time objectives

### 12.6 Workflow Orchestration
- **Step Functions**: visual workflow editor, error handling
- **Conditional logic**: route based on criteria
- **Parallel execution**: fan out to multiple branches
- **Sequential steps**: dependencies between tasks
- **Retries & backoff**: handle transient failures
- **Dead-letter queues**: capture failures

### 12.7 Integration Patterns
- **Synchronous**: request/response, real-time
- **Asynchronous**: fire-and-forget, eventually consistent
- **Pub/sub**: broadcast to multiple subscribers
- **Request/reply**: message queue with correlation ID
- **Webhooks**: external systems notify your service
- **Polling**: periodic checks for updates
- **Event-driven**: react to events in real-time

### 12.8 AI Platform Architecture
- **Model gateway**: one internal API for all providers/models
- **Prompt registry**: version prompts, owners, rollout state
- **Eval service**: run offline/online evals automatically
- **Tool registry**: catalog tools, permissions, schemas, owners
- **Policy engine**: central rules for data, safety, spend, approvals
- **Shared observability**: traces, costs, quality, feedback in one place

### 12.9 Change Management
- **Model deprecations**: track provider shutdown dates and migrations
- **Compatibility tests**: verify new model behavior before rollout
- **Release notes review**: monitor provider changes and new capabilities
- **Incident playbooks**: provider outage, bad outputs, runaway costs
- **Kill switches**: disable models, tools, prompts, features quickly

---

## **MODULE 13: DATA ENGINEERING FOR AI** (2-3 weeks)

### 13.1 Data Collection
- **Sources**: APIs, databases, web scraping, user events
- **Batch collection**: scheduled jobs (daily, hourly)
- **Stream collection**: real-time data ingestion
- **Data quality checks**: detect anomalies, missing values
- **PII handling**: redact, encrypt sensitive data
- **Data validation**: schema enforcement, type checking

### 13.2 Data Processing & Transformation
- **ETL pipelines**: extract, transform, load
- **Normalization**: standardize formats, units
- **Deduplication**: remove duplicates
- **Aggregation**: combine data points
- **Enrichment**: add context (geographic, demographic)
- **Feature engineering**: create useful attributes
- **Missing value imputation**: handle gaps

### 13.3 Data Storage
- **Data lakes**: raw data storage (S3)
- **Data warehouses**: structured, queryable (Redshift, Athena)
- **Feature stores**: pre-computed features (Tecton, Feast)
- **Time-series databases**: data with timestamps (InfluxDB, TimescaleDB)
- **Document stores**: JSON docs (DynamoDB, MongoDB)
- **Vector stores**: embeddings (Pinecone, Weaviate)

### 13.4 Data Pipelines
- **Airflow**: orchestrate complex workflows
- **Lambda**: event-driven processing
- **Glue**: ETL managed service (AWS)
- **Spark**: distributed data processing
- **Snowflake**: cloud data warehouse
- **Kafka**: event streaming
- **Data Quality**: validate at each stage

### 13.5 Feature Management
- **Feature definition**: what is a feature?
- **Feature computation**: batch vs real-time
- **Feature serving**: low-latency access for inference
- **Feature drift**: monitor for data distribution changes
- **Feature versioning**: track feature definitions
- **Lineage**: understand feature dependencies

### 13.6 Data Governance
- **Data catalog**: inventory of datasets
- **Data lineage**: track data flow through pipelines
- **Access control**: who can see what data?
- **Audit logging**: record all data access
- **Retention policies**: delete old data
- **Data quality metrics**: define standards

### 13.7 Data Contracts for AI
- **Schema contracts**: expected fields, types, allowed values
- **Source contracts**: who owns each data source and SLA
- **Embedding contracts**: model version, chunking method, metadata fields
- **Retrieval contracts**: permissions, freshness, relevance thresholds
- **Change notification**: alert AI app owners when upstream data changes
- **Dataset versioning**: reproduce eval and fine-tuning runs

---

## **MODULE 14: FINE-TUNING & CUSTOM MODELS** (2 weeks)
*Note: You may not need this immediately, but good to know options exist*

### 14.1 When to Fine-Tune
- **Cost reduction**: cheaper custom model vs expensive API
- **Latency**: local model faster than API
- **Privacy**: keep data on-premises
- **Control**: exact behavior vs generic model
- **Specialization**: domain-specific knowledge
- **Token efficiency**: shorter responses, better formatting

### 14.2 Fine-Tuning Options
- **OpenAI fine-tuning**: GPT-3.5, easy but limited
- **Anthropic**: limited fine-tuning, mostly prompt engineering
- **Open-source**: Llama, Mistral, can fine-tune on your data
- **AWS SageMaker JumpStart**: managed fine-tuning
- **Hugging Face**: open-source model hub, training examples
- **LoRA/QLoRA adapters**: cheaper fine-tuning for open-weight models
- **Distillation**: transfer strong-model behavior to cheaper model

### 14.3 Data Preparation
- **Data format**: conversation format (system, user, assistant)
- **Data cleaning**: fix errors, remove duplicates
- **Data size**: need 100+ examples typically
- **Validation set**: hold out 10-20% for evaluation
- **Balanced data**: roughly equal examples per class

### 14.4 Fine-Tuning Process
- **Training**: teach model on your data
- **Validation**: monitor performance on held-out data
- **Hyperparameters**: learning rate, batch size, epochs
- **Convergence**: training loss decreasing
- **Evaluation**: compare to baseline model
- **Deployment**: serve fine-tuned model

### 14.5 Evaluation & Validation
- **Benchmark**: compare fine-tuned vs base model
- **Human evaluation**: does output meet expectations?
- **Cost-benefit**: is improvement worth cost?
- **Overfitting**: does model memorize data?
- **Generalization**: does it work on new data?

### 14.6 Model Customization Without Training
- **Prompt tuning**: improve behavior through instructions/examples
- **RAG tuning**: improve retrieval before considering training
- **Tool tuning**: add deterministic tools instead of asking model to guess
- **Output constraints**: schema and validators instead of fine-tuning format
- **Preference examples**: few-shot examples for tone/style/format

---

## **MODULE 15: EMERGING TECHNIQUES & RESEARCH** (2 weeks)
*Latest patterns as of June 2026*

### 15.1 Advanced Agentic Patterns
- **Graph of thoughts**: visualize reasoning paths
- **Mixture of experts (MoE)**: route tokens to specialized sub-networks (Mellum2, Mixtral)
- **Ensembling**: combine outputs from multiple models
- **Debate frameworks**: agents argue, arbiter decides
- **Self-play**: agents train against each other
- **Constitutional AI**: define values, have model self-align
- **Dynamic workflows**: orchestrator spawns hundreds of parallel subagents, verifies outputs (Claude Code)
- **Effort control**: tune reasoning depth (low → max) per task
- **Agentic RL (TITO)**: Token-In, Token-Out reinforcement learning for agent training

### 15.2 Multimodal AI
- **Vision + Language**: analyze images, generate descriptions
- **Audio + Language**: transcription, voice understanding
- **Video**: temporal reasoning about sequences
- **Cross-modal retrieval**: search images with text queries
- **Models**: GPT-5.5, Claude Opus 4.8, Gemini 3.5, Llama 4 multimodal, NVIDIA Cosmos 3
- **Physical AI**: NVIDIA Cosmos 3 for robotics reasoning and action

### 15.3 Real-Time Systems
- **Streaming responses**: return partial results as generated
- **Real-time retrieval**: fetch fresh information during generation
- **Live updates**: modify response as new data arrives
- **Low-latency inference**: fast mode (2.5× speed), speculative decoding
- **Concurrent requests**: handle many users simultaneously
- **WebRTC/WebSocket**: bidirectional audio/video AI sessions

### 15.4 Advanced Retrieval
- **Reranking models**: cross-encoders, ColBERT, Ettin Reranker family
- **Semantic routing**: classify queries → specialized retriever
- **Adaptive retrieval**: decide whether to retrieve mid-generation
- **Long-context models**: 128K–1M+ context windows, stuff entire documents
- **Fusion search**: combine keyword + semantic + knowledge graph signals
- **Late interaction**: ColBERT-style efficient dense retrieval

### 15.5 Synthetic Data Generation
- **Data augmentation**: generate variations of examples
- **Bootstrapping**: create training data synthetically
- **Simulation**: generate realistic scenarios
- **Adversarial examples**: edge cases to test robustness
- **Privacy-preserving**: synthetic data instead of real PII
- **Distillation datasets**: strong model generates training data for smaller model

### 15.6 Continual Learning
- **Online learning**: update model as new data arrives
- **Catastrophic forgetting**: avoid losing old knowledge
- **Knowledge distillation**: compress large models
- **Incremental fine-tuning**: adapt to new domains gradually
- **Federated learning**: train on distributed data

### 15.7 Computer Use & Browser Agents
- **Computer-use agents**: interact with GUIs through screenshots/actions (Holo3.1, Claude)
- **Browser automation**: navigate websites, forms, dashboards
- **Stealth automation**: headless browsers designed to bypass bot detection for seamless agent scraping
- **Sandboxing**: isolate risky actions and untrusted pages
- **Permission gates**: human approval before purchase, submit, delete, send
- **Visual verification**: compare screen state before/after actions
- **Online-Mind2Web benchmark**: 84%+ scores on web navigation tasks

### 15.8 Deep Research & Background Workflows
- **Long-running tasks**: background jobs with checkpoints and resumability
- **Research planning**: decompose question, gather sources, synthesize answer
- **Local execute**: running multi-engine searches (arXiv, PubMed, local docs) fully locally for privacy (e.g. Local Deep Research)
- **Source quality grading**: prefer primary/authoritative evidence
- **Contradiction handling**: compare conflicting sources explicitly
- **Final report generation**: cited summary, assumptions, confidence, gaps

### 15.9 Diffusion Language Models
- **Non-autoregressive generation**: generate all tokens in parallel, refine iteratively
- **Nemotron-Labs Diffusion LMs**: NVIDIA's approach to speed-of-light text generation
- **Benefits**: faster generation, global coherence, controllable editing
- **Tradeoffs**: early-stage, smaller scale, different failure modes
- **Use cases**: structured output, constrained generation, batch text

### 15.10 State Space Models (SSMs)
- **Mamba architecture**: linear-time sequence modeling, alternative to attention
- **Benefits**: O(n) vs O(n²) for long sequences, memory efficient
- **Hybrid architectures**: combine SSM layers with attention layers
- **Use cases**: very long documents, code, genomics, time-series
- **Tradeoffs**: less mature tooling, some tasks still favor transformers

### 15.11 Agent Evaluation & Benchmarks
- **ITBench-AA**: Enterprise IT agentic task benchmark (frontier models <50%)
- **Terminal-Bench**: coding agent evaluation
- **OSWorld-Verified**: computer use evaluation
- **Super-Agent benchmark**: end-to-end complex task completion
- **CursorBench**: IDE coding agent evaluation
- **Legal Agent Benchmark**: legal work automation accuracy
- **Finance Agent v2**: financial document workflow evaluation
- **Trajectory evaluation**: grade full action path, not just final answer

### 15.12 Security & Safety Advances (2026)
- **Project Glasswing**: cross-industry initiative (AWS, Anthropic, Apple, Google, Microsoft, NVIDIA, etc.) to secure critical software
- **Mythos-class safety**: stronger cyber safeguards for highest-capability models
- **AI-enabled cyber threat mapping**: MITRE ATT&CK integration
- **Agent governance toolkits**: Microsoft Agent Governance, execution sandboxing
- **Alignment improvements**: 4× reduction in unremarked code flaws (Opus 4.8)
- **Honesty training**: models flag uncertainties, avoid unsupported claims

### 15.13 Robotics & Embodied AI
- **LeRobot Humanoid**: open-source, low-cost, 3D-printed humanoid for robot learning
- **MCP tools for robotics**: adding Model Context Protocol to physical robots (Reachy Mini)
- **Driving foundation models**: Alpamayo for autonomous vehicles
- **Physical AI reasoning**: NVIDIA Cosmos 3 for embodied intelligence
- **Sim-to-real transfer**: train in simulation, deploy on hardware

---

## **MODULE 16: DOMAIN-SPECIFIC APPLICATIONS** (3-4 weeks)

### 16.1 Customer Support
- **Ticket triage**: classify by urgency, category
- **Automated responses**: handle common questions
- **Escalation**: route complex issues to humans
- **Knowledge base integration**: search internal docs
- **Sentiment analysis**: detect customer frustration
- **Quality scoring**: measure response quality
- **Multi-language support**: support global customers

### 16.2 Enterprise Knowledge Management
- **Document Q&A**: search internal policies, procedures
- **Onboarding**: help new employees learn policies
- **Compliance**: verify actions against policies
- **Decision support**: provide recommendations
- **Knowledge graph**: connect related information
- **Search**: semantically find relevant docs

### 16.3 Sales & Marketing
- **Lead scoring**: prioritize high-value prospects
- **Email generation**: personalized outreach at scale
- **Product recommendations**: suggest relevant products
- **Competitor analysis**: monitor competitor activity
- **Content creation**: generate marketing copy
- **Customer segmentation**: group by behavior/characteristics

### 16.4 Code Development
- **Code completion**: suggest next lines
- **Code generation**: write functions from requirements
- **Bug detection**: find logical errors
- **Refactoring**: improve code quality
- **Documentation**: generate docstrings, README
- **Test generation**: write test cases
- **Commit messages**: suggest meaningful messages

### 16.5 Data Analysis & Reporting
- **SQL generation**: convert questions to queries
- **Chart generation**: create visualizations from data
- **Insight generation**: find patterns, anomalies
- **Report generation**: create summaries, presentations
- **Forecast**: predict future values
- **Root cause analysis**: explain why metric changed

### 16.6 Legal & Compliance
- **Contract review**: identify risks, unusual clauses
- **Compliance checking**: verify adherence to regulations
- **Legal research**: find relevant precedents, cases
- **Document generation**: create standardized agreements
- **Due diligence**: assess companies/investments
- **Risk assessment**: identify potential issues

### 16.7 Healthcare (if relevant)
- **Patient Q&A**: answer common health questions
- **Clinical decision support**: assist diagnosis
- **Medical coding**: assign billing codes
- **Literature search**: find relevant research papers
- **Clinical notes**: automated documentation
- **Privacy**: HIPAA compliance for health data

### 16.8 Finance
- **Financial analysis**: analyze quarterly earnings
- **Risk assessment**: evaluate investment risks
- **Fraud detection**: identify anomalous transactions
- **Portfolio management**: optimize asset allocation
- **Regulatory compliance**: track financial regulations
- **Reporting**: generate financial statements

---

## **MODULE 17: ADVANCED OPERATIONS** (2-3 weeks)

### 17.1 Model Operations (MLOps)
- **Model registry**: version and track models
- **A/B testing**: compare model versions
- **Model monitoring**: track performance degradation
- **Drift detection**: when model performance decays
- **Retraining pipelines**: automated model updates
- **Model cards**: documentation of model, limitations

### 17.2 CI/CD for AI Systems
- **Unit tests**: test functions, utilities
- **Prompt tests**: test LLM outputs, quality
- **Integration tests**: test end-to-end flows
- **Automated deployment**: push to production automatically
- **Rollback**: quick revert to previous version
- **Staging environment**: test before production

### 17.3 Capacity Planning
- **Forecast demand**: expected usage growth
- **Provision infrastructure**: enough capacity for load
- **Cost projections**: budget planning
- **Scaling strategy**: how to handle growth
- **Resource allocation**: prioritize high-value features

### 17.4 Disaster Recovery
- **Backup strategy**: regular backups, test restoration
- **Failover**: automatic switchover on failure
- **Data replication**: across regions, availability zones
- **RTO/RPO goals**: how fast/fresh recovery target
- **Incident response**: procedures for major outages
- **Post-incident review**: learn from failures

### 17.5 Vendor Management
- **Multi-vendor strategy**: don't depend on single provider
- **Fallback models**: alternatives if primary unavailable
- **Cost management**: negotiate volume discounts
- **SLA monitoring**: track uptime guarantees
- **Rate limit management**: work within API quotas
- **Vendor risk**: assess long-term viability

---

## **MODULE 18: SOFT SKILLS & BEST PRACTICES** (ongoing)

### 18.1 Documentation
- **Architecture diagrams**: system design, data flow
- **Runbooks**: step-by-step operational procedures
- **API documentation**: endpoint descriptions, examples
- **Configuration guides**: how to set up system
- **Troubleshooting guides**: common problems, solutions
- **Lessons learned**: post-mortems, improvements

### 18.2 Collaboration
- **Cross-functional teams**: work with product, design, infra
- **Code review**: peer feedback, knowledge sharing
- **Design review**: validate architecture before building
- **Incident coordination**: joint response to outages
- **Knowledge transfer**: document, mentor others
- **Communication**: clear explanation of technical decisions

### 18.3 Problem Solving
- **Root cause analysis**: find underlying issue
- **Systems thinking**: understand interactions, dependencies
- **Trade-off analysis**: pros/cons of different approaches
- **Prototype early**: test ideas quickly
- **Incremental delivery**: start small, iterate
- **Learning from failures**: mistakes as opportunities

### 18.4 Project Management
- **Estimation**: how long will this take?
- **Prioritization**: which features first?
- **Roadmap planning**: quarterly/annual goals
- **Stakeholder management**: align expectations
- **Status tracking**: progress updates
- **Retrospectives**: team improvement

### 18.5 Industry Knowledge
- **Stay current**: read blogs, papers, Twitter/X
- **Attend conferences**: networking, learning
- **Experiment**: try new tools, frameworks
- **Community**: contribute to open-source
- **Certifications**: AWS, LLM certificates (if useful)

---

## **MODULE 19: PORTFOLIO & JOB READINESS** (ongoing)

### 19.1 Portfolio Projects
- **RAG app**: document ingestion, vector search, citations, evals
- **Agent app**: tools, approvals, trace logs, retry handling
- **Voice/realtime app**: streaming input/output, low-latency UX
- **Enterprise AI platform slice**: model gateway, prompt registry, cost dashboard
- **Security demo**: prompt injection tests, guardrails, audit logs

### 19.2 Engineering Artefacts
- **Architecture diagram**: components, data flow, threat boundaries
- **Runbook**: deploy, rollback, incident response, cost spike response
- **Eval report**: dataset, metrics, pass/fail thresholds, model comparison
- **Cost report**: per-request cost, monthly forecast, optimization plan
- **Security review**: data handling, permissions, guardrails, residual risk

### 19.3 Interview Preparation
- **System design**: design RAG, chatbot, agent, model gateway, eval platform
- **Debugging stories**: hallucination, bad retrieval, high latency, cost spike
- **Tradeoff answers**: RAG vs long context, API vs local model, agent vs workflow
- **AWS mapping**: explain Bedrock/Lambda/S3/DynamoDB/Step Functions architecture
- **Demo readiness**: 5-minute walkthrough of one production-style project

---

## **LEARNING PATH TIMELINE**

### Week 1-2: First Principles
- Module 0: First Principles (transformers, attention, embeddings, inference, retrieval basics)
- **Quick exercise**: Visualize attention weights, understand tokenization artifacts

### Month 1-2: Foundation
- Module 1: LLM Fundamentals
- Module 2: Embeddings & Vector Search
- **Quick project**: Build simple Q&A bot with OpenAI API + pinecone

### Month 3-4: RAG & Applications
- Module 3: RAG Deep Dive
- Module 6.1-6.3: QA, Content Gen, Summarization
- **Project**: Document QA system with RAG on AWS

### Month 5-6: Agents & Orchestration
- Module 4: Agentic Systems
- Module 5: Structured Outputs
- **Project**: Multi-step agent for research/writing task

### Month 7: Deployment & Infrastructure
- Module 7: AWS Deployment
- Module 12: Production Patterns
- **Project**: Production-grade RAG app on AWS Bedrock

### Month 8-9: Quality & Cost
- Module 10: Evaluation
- Module 11: Cost Optimization
- Module 9: Security & Compliance
- **Project**: Cost-optimized system with monitoring

### Month 10-12: Advanced Topics & Specialization
- Module 13: Data Engineering
- Module 15: Emerging Techniques
- Module 16: Domain Applications (pick 2-3 relevant to you)
- Module 17: MLOps/Advanced Operations
- Module 19: Portfolio & Job Readiness
- **Capstone**: Build production system combining everything

---

## **LEVERAGE YOUR DEVOPS/AWS BACKGROUND**

- **DevOps skills → AI DevOps**: containerization, CI/CD, infrastructure, monitoring apply directly
- **AWS expertise**: Bedrock, Lambda, SageMaker, DynamoDB skills immediately useful
- **Architecture experience**: design scalable, resilient AI systems
- **Security knowledge**: apply to LLM API keys, data protection, compliance
- **Performance mindset**: optimize token usage, latency, cost

---

## **TOOLS & TECHNOLOGIES CHEAT SHEET** (June 2026)

**LLM APIs & Gateways**: OpenAI Responses API (GPT-5.5, o4), Anthropic Claude API (Opus 4.8, Mythos), AWS Bedrock Converse API (Nova), Google Gemini/Vertex AI (Gemini 3.5), LiteLLM (multi-provider proxy)
**Frameworks**: LangChain, LangGraph, LlamaIndex, CrewAI, Semantic Kernel, Strands Agents SDK (AWS), Claude Agent SDK, Claude Code
**Vector DBs**: Pinecone, Weaviate, Qdrant, Postgres pgvector, Chroma, Milvus
**Rerankers**: ColBERT, Cohere Rerank, Ettin Reranker, cross-encoders
**Agent Integration**: MCP, function calling, tool registries, approval workflows, dynamic workflows
**AWS Services**: Bedrock, Bedrock Knowledge Bases, Bedrock Guardrails, AgentCore, Lambda, SageMaker, DynamoDB, RDS, S3, EventBridge, Step Functions
**Local Inference**: vLLM, TGI, Ollama, llama.cpp, GGUF/GPTQ/AWQ quantization
**Observability**: Langfuse, Arize/Phoenix, Helicone, LangSmith, CloudWatch, DataDog, OpenTelemetry
**Testing/Evals**: pytest, promptfoo, RAGAS, DeepEval, Braintrust, ITBench-AA, custom eval harnesses
**Computer Use**: Playwright, Puppeteer, Holo3.1, Claude computer use, browser sandboxing
**Deployment**: Docker, ECR, ECS, EKS, Lambda, Terraform/CDK
**Monitoring**: CloudWatch, X-Ray, custom dashboards, cost dashboards
**AI Products**: Claude Code, Claude Cowork, Claude Design, Cursor, GitHub Copilot, Devin

---

## **WHAT YOU DON'T NEED**

- Deep learning math (backpropagation, linear algebra)
- ML training infrastructure (GPUs, distributed training)
- Transformer architecture papers (nice to know, not required)
- Statistics courses (intuition is enough)
- Computer vision (unless building multimodal apps)
- NLP research knowledge (applied engineering, not research)
