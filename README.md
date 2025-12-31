Semantic Spotter
RAG-based Insurance Policy Intelligence System
Overview
Semantic Spotter is an end-to-end Retrieval-Augmented Generation (RAG) system designed to enable accurate, context-aware, and explainable querying of insurance policy documents.

Insurance documents are typically long, complex, and difficult for users to interpret. This system bridges that gap by allowing users to ask natural-language questions and receive grounded answers strictly derived from relevant policy sections.

The solution is built using LlamaIndex for document ingestion and semantic retrieval and OpenAI’s GPT-3.5-turbo for response generation. A disk-based caching layer is incorporated to improve performance for frequently asked questions.

Why RAG and LlamaIndex?
A standalone LLM approach is unsuitable for enterprise documents due to:

Hallucination risks
Lack of grounding in source data
Limited explainability
Retrieval-Augmented Generation (RAG) ensures responses are generated only from retrieved, relevant document context, improving accuracy, transparency, and trust.

LlamaIndex is chosen because it provides:

Efficient document ingestion and chunking
Vector-based semantic retrieval
Modular query pipelines
Seamless LLM integration
Production-ready abstractions with minimal boilerplate
Dataset Description
The dataset consists of multiple insurance policy documents in .pdf and .docx formats, including:

Policy terms and conditions
Coverage details and exclusions
Claim procedures
Nominee and beneficiary clauses
These documents collectively form the knowledge base for semantic search and question answering.

System Architecture (High-Level)
The system follows a layered RAG architecture:

Ingestion Layer

Loads documents using SimpleDirectoryReader
Preprocessing Layer

Cleans and splits documents into semantically meaningful chunks
Embedding Layer

Converts chunks into vector embeddings using OpenAI embeddings
Vector Index Layer

Stores embeddings using VectorStoreIndex
Retrieval Layer

Retrieves top-K relevant chunks based on semantic similarity
Reranking Layer (Optional Enhancement)

Improves retrieval precision using semantic reranking
Generation Layer

GPT-3.5-turbo generates answers using retrieved context and custom prompts
Caching Layer

Diskcache stores frequent queries and responses to reduce latency
Methodology
Step 1: Data Loading and Preprocessing
Documents are loaded using SimpleDirectoryReader
Text is cleaned and chunked to preserve semantic meaning
Step 2: Indexing
Chunks are embedded and indexed using VectorStoreIndex
Step 3: Query Processing
User queries are first checked against the disk cache
If not cached, semantic retrieval is performed
Step 4: Response Generation
Retrieved document chunks are passed to GPT-3.5-turbo
Custom prompts ensure accurate and context-grounded answers
Step 5: Metadata Attribution
Responses include document references and similarity scores
Evaluation and Results
The system was tested using real-world insurance queries such as:

“What are the exclusions for accidental death coverage?”
“Who can be nominated as a beneficiary?”
“What documents are required for claim settlement?”
Results:

Accurate and context-aware responses
Reduced response latency for repeated queries due to caching
Improved user trust through source attribution
Challenges Faced
GPTCache compatibility issues, resolved using Diskcache
Handling long documents without losing semantic context
Prompt design to minimize hallucinations
Lessons Learned
Proper chunking significantly improves retrieval quality
Prompt engineering plays a critical role in response accuracy
Caching greatly enhances system performance
Metadata improves transparency and user confidence
Dependencies
llama-index
openai
diskcache
Conclusion
Semantic Spotter demonstrates a production-ready RAG system for intelligent document querying.
The architecture is modular and extensible, making it suitable for other enterprise domains such as legal, healthcare, and government documents.
