

### Question 1
What is the fundamental problem that RAG solves compared to traditional search engines?

A) Search engines are too slow to process queries

B) Search engines only return hyperlinks, requiring users to manually explore documents to find answers

C) Search engines cannot handle natural language queries

D) Search engines don't support multiple languages

**Answer:** B) Search engines only return hyperlinks, requiring users to manually explore documents to find answers

**Topic:** RAG Introduction and Problem Statement

**Timestamp:** [00:01:41] - [00:03:21]

**Explanation:** The instructor explains that traditional search engines return paginated hyperlinks (typically 15 per page), and users get tired of exploring documents manually. There's even a joke mentioned that "if you have a national security secret, the best place to hide it is on page two because nobody visits page two of search results."

---

### Question 2
In a RAG pipeline, what are the two main components that work together to generate natural language answers?

A) Parser and Chunker

B) Retriever (search engine) and LLM (Large Language Model)

C) Embedder and Vector Database

D) Query Processor and Response Formatter

**Answer:** B) Retriever (search engine) and LLM (Large Language Model)

**Topic:** RAG Architecture Components

**Timestamp:** [00:03:21] - [00:05:02]

**Explanation:** The instructor describes RAG as bringing together a retriever (search engine) that finds relevant search results, and an LLM that observes the user question and search results to synthesize a natural language answer based on the facts provided.

---

### Question 3
Why does the instructor recommend using smaller LLMs in RAG systems instead of very large ones?

A) Smaller LLMs are more accurate

B) Smaller LLMs consume less memory

C) In RAG, the LLM has a simple task (reformatting retrieved information), and smaller models allow for more instances to run on GPU clusters

D) Smaller LLMs are easier to fine-tune

**Answer:** C) In RAG, the LLM has a simple task (reformatting retrieved information), and smaller models allow for more instances to run on GPU clusters

**Topic:** LLM Sizing Strategy in RAG

**Timestamp:** [00:16:07] - [00:17:43]

**Explanation:** The instructor explains that in RAG, the LLM doesn't use its "big brain" - it has a simple task of reformatting and interpreting retrieved answers. Smaller LLMs (2B, 7B, 30B parameters) can handle this task effectively, and being smaller allows running more instances across GPU clusters for better load balancing.

---

### Question 4
What is the main security advantage of RAG over fine-tuning LLMs with proprietary data?

A) RAG systems are encrypted by default

B) RAG systems don't store data permanently

C) In RAG, security filters can be applied to the retrieval system, and the LLM doesn't remember proprietary data after inference

D) RAG systems require authentication for every query

**Answer:** C) In RAG, security filters can be applied to the retrieval system, and the LLM doesn't remember proprietary data after inference

**Topic:** Security Architecture in Enterprise RAG

**Timestamp:** [00:09:54] - [00:13:00]

**Explanation:** The instructor explains that RAG allows applying security filters to ensure only authorized results reach the LLM, and crucially, "at inference time the LLM doesn't remember that data," providing better security than fine-tuning where "all bets are off with security."

---

### Question 5
What are the three main stages in the data injection pipeline for RAG?

A) Download, Process, Store

B) Parsing, Chunking, Embedding/Indexing

C) Extract, Transform, Load

D) Collect, Validate, Deploy

**Answer:** B) Parsing, Chunking, Embedding/Indexing

**Topic:** RAG Data Injection Pipeline

**Timestamp:** [00:30:17] - [00:33:43]

**Explanation:** The instructor details the data injection journey: First, parsing (converting documents like PDFs to textual form), then chunking (isolating thoughts into separate chunks), and finally embedding (using text embedders to create embedding vectors) followed by indexing into vector databases.

---

### Question 6
What computational challenge does the instructor highlight about using very large LLMs (like 450 billion parameters)?

A) They require too much storage space

B) They are too slow to load into memory

C) Due to autoregressive nature, generating a 100-token answer requires 100 forward passes, each computing 450 billion parameters

D) They cannot handle concurrent requests

**Answer:** C) Due to autoregressive nature, generating a 100-token answer requires 100 forward passes, each computing 450 billion parameters

**Topic:** Computational Complexity of Large LLMs

**Timestamp:** [00:20:52] - [00:22:25]

**Explanation:** The instructor explains the "utter absurdity" of using very large LLMs: due to their autoregressive nature, each token requires a forward pass, so a 100-token answer needs 100 passes through the entire 450 billion parameter model, making it computationally inefficient.

---

### Question 7
According to the instructor, what is the primary factor that provides the biggest improvement in RAG system performance?

A) Using larger, more powerful LLMs

B) Implementing better retrieval algorithms

C) Improving data quality through derivative data creation (summaries, knowledge graphs, better chunking)

D) Increasing the size of the vector database

**Answer:** C) Improving data quality through derivative data creation (summaries, knowledge graphs, better chunking)

**Topic:** RAG Performance Optimization Priorities

**Timestamp:** [00:19:14] - [00:20:52]

**Explanation:** The instructor emphasizes that "most of the bang that you get primarily is from having better data." This includes creating derivative data like question-answers, summarizations, knowledge graphs, reinterpretations, and better chunking - all focused on improving the data quality itself rather than just using larger models.

---

## Part 2: RAG Implementation and Production Issues

### Question 8
What is the primary problem with running the basic "Hello World" RAG example code in production?

A) The embedding model is too slow

B) The vector database doesn't support enough documents

C) The code performs expensive parsing, chunking, and indexing operations on every user request

D) The LLM responses are not accurate enough

**Answer:** C) The code performs expensive parsing, chunking, and indexing operations on every user request

**Topic:** RAG Architecture & Performance Optimization

**Timestamp:** [01:05:58]

**Explanation:** The instructor emphasizes that the "Hello World" example performs line 20-21 operations (parsing, chunking, indexing, embedding) on every request, which is extremely expensive. These operations should be done once and the index should be persisted for later use, not repeated for every user query.

---

### Question 9
In the demonstration, how many chunks were created from a single chapter about ancient Indian and Chinese civilization?

A) 20 chunks

B) 30 chunks

C) 40 chunks

D) 50 chunks

**Answer:** C) 40 chunks

**Topic:** Document Processing & Chunking

**Timestamp:** [01:02:43]

**Explanation:** The instructor specifically mentions that one PDF chapter was converted into 40 chunks during the chunking process, demonstrating how documents are broken down into smaller, manageable pieces for indexing.

---

### Question 10
When the instructor deliberately changed the query from "ancient Indian civilization" to "ancient Greek civilization," what happened and why is this problematic?

A) The system returned an error message

B) The LLM used its parametric memory to answer about Greek civilization despite it not being in the documents

C) The vector database crashed due to the mismatch

D) The embedding model failed to process the query

**Answer:** B) The LLM used its parametric memory to answer about Greek civilization despite it not being in the documents

**Topic:** LLM Parametric Memory vs Grounded Responses

**Timestamp:** [01:09:14]

**Explanation:** The instructor demonstrates that the LLM answered about Greek civilization using its pre-trained knowledge (parametric memory) even though the document only contained information about Indian and Chinese civilizations. This is problematic because you cannot determine if the answer came from the search results or the LLM's internal knowledge.

---

### Question 11
According to the instructor, what is the data exfiltration risk when using external LLM APIs like OpenAI?

A) The API costs are too expensive

B) Confidential data from your documents gets sent to external servers

C) The responses are not accurate enough

D) The processing speed is too slow

**Answer:** B) Confidential data from your documents gets sent to external servers

**Topic:** Security & Data Privacy in RAG Systems

**Timestamp:** [01:18:36]

**Explanation:** The instructor warns that when you send queries containing confidential information (like airplane wingspan designs) to external APIs, that sensitive data leaves your premises and goes to third-party servers, creating a data exfiltration risk.

---

### Question 12
What percentage of queries are typically semantic repeats according to the instructor, and what hardware savings can semantic caching provide?

A) 80% repeats, 5x hardware savings

B) 90% repeats, 10x hardware savings

C) 95% repeats, 15x hardware savings

D) 85% repeats, 8x hardware savings

**Answer:** B) 90% repeats, 10x hardware savings

**Topic:** Semantic Caching & Performance Optimization

**Timestamp:** [02:06:02]

**Explanation:** The instructor states that over 90% of queries are semantic repeats, meaning you can use one-tenth the hardware (10x savings) by implementing semantic caching, as most questions are semantically similar even if worded differently.

---

### Question 13
Why does the instructor implement a consistency check between the embedder and vector database?

A) To verify the authentication credentials

B) To ensure the embedding vector size matches the vector database collection schema

C) To check if the database has enough storage space

D) To validate the query syntax

**Answer:** B) To ensure the embedding vector size matches the vector database collection schema

**Topic:** Vector Database Architecture & Error Prevention

**Timestamp:** [01:31:10]

**Explanation:** The instructor explains that when creating a vector database collection, you must specify the vector size. If your embedder produces vectors of size 200 but the database expects size 100, there's a compatibility problem. The consistency check prevents this mismatch before data insertion.

---

### Question 14
According to the instructor's best practices, what four components should a complete RAG response include?

A) Answer, metadata, timestamp, user ID

B) Key insights, recommended quotes, thoughtful answer, follow-up questions

C) Query, response, confidence score, processing time

D) Source documents, embeddings, tokens used, cost calculation

**Answer:** B) Key insights, recommended quotes, thoughtful answer, follow-up questions

**Topic:** RAG Response Architecture & User Experience

**Timestamp:** [01:39:08]

**Explanation:** The instructor emphasizes that a complete RAG response should provide: key insights from the search results, recommended quotes (relevant source citations), a thoughtful answer to the user's question, and suggested follow-up questions to continue the conversation.

---

### Question 15
What technique does the instructor suggest to prevent LLM hallucination and ensure responses are grounded in search results?

A) Use smaller language models only

B) Increase the temperature parameter to 0

C) Ask the LLM to cite specific search results for every statement in its response

D) Limit responses to exactly 50 tokens

**Answer:** C) Ask the LLM to cite specific search results for every statement in its response

**Topic:** Response Grounding & Hallucination Prevention

**Timestamp:** [01:17:02]

**Explanation:** The instructor recommends asking the LLM to point to specific search results that substantiate every statement in its response. This prevents hallucination and ensures the LLM cannot use its parametric memory, as it must back up everything with source documents from the search results.
