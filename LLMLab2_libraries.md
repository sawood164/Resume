#  Top 15 Questions from Lecture LLM

---

### **Question 1: Vector Indices Fundamentals**  
What is the primary purpose of vector indices in machine learning systems?  
**A)** To store structured data in relational databases  
**B)** To enable exact matching of employee records  
**C)** To store, organize, and retrieve high-dimensional vector representations efficiently  
**D)** To compress images and audio files  
✅ **Correct Answer:** C  
🧠 Topic: Vector Indices Introduction  
⏱️ Timestamp: [00:01:33] - [00:03:08]  
📌 **Explanation:** Vector indices are specialized data structures designed to retrieve high-dimensional vectors efficiently for similarity search across text, image, audio, etc.

---

### **Question 2: Distance Metrics in High-Dimensional Spaces**  
Why is L2 (Euclidean) distance not preferred over cosine similarity in high-dimensional vector spaces?  
**A)** L2 distance is computationally more expensive  
**B)** In high-dimensional spaces, most points become equidistant from each other, making L2 less effective for similarity measurement  
**C)** Cosine similarity is faster to compute  
**D)** L2 distance only works with normalized vectors  
✅ **Correct Answer:** B  
🧠 Topic: Distance Metrics and Similarity Measures  
⏱️ Timestamp: [00:12:29] - [00:16:09]  
📌 **Explanation:** In high dimensions, L2 becomes less meaningful. Cosine similarity remains useful because it measures angle between vectors.

---

### **Question 3: Distance Metrics Relationship**  
According to the explanation provided, when are cosine distance and dot product practically equivalent?  
**A)** When vectors have different magnitudes  
**B)** When vectors are normalized to unit length (norm = 1)  
**C)** When using high-dimensional vectors only  
**D)** When vectors contain negative values  
✅ **Correct Answer:** B  
🧠 Topic: Distance Metrics in Vector Search  
⏱️ Timestamp: [01:32:18]  
📌 **Explanation:** For unit vectors, the dot product equals cosine similarity because the denominator becomes 1.

---

### **Question 4: Approximate Nearest Neighbor Search Evaluation**  
In approximate nearest neighbor search, what does "recall at K" measure?  
**A)** The number of queries processed per second  
**B)** The fraction of true top-K results that were found in the returned results  
**C)** The total memory usage of the index  
**D)** The time taken to build the vector index  
✅ **Correct Answer:** B  
🧠 Topic: Evaluation Metrics for Vector Search  
⏱️ Timestamp: [00:18:08] - [00:19:43]  
📌 **Explanation:** Recall at K evaluates the fraction of actual top-K neighbors found in the results returned.

---

### **Question 5: Locality Sensitive Hashing (LSH)**  
What is the core principle behind Locality Sensitive Hashing for vector search?  
**A)** Vectors are sorted by their magnitude  
**B)** Similar vectors are mapped to the same hash bucket using random planes  
**C)** Vectors are compressed using principal component analysis  
**D)** Exact matches are found using B-tree indexing  
✅ **Correct Answer:** B  
🧠 Topic: Locality Sensitive Hashing Algorithm  
⏱️ Timestamp: [00:24:18] - [00:30:30]  
📌 **Explanation:** LSH reduces search space by hashing similar vectors into the same buckets using random hyperplanes.

---

### **Question 6: Hierarchical Navigable Small World (HNSW) Construction**  
How does the HNSW algorithm determine which layer a vector belongs to during index construction?  
**A)** Vectors are assigned based on their magnitude  
**B)** K-means clustering is used to assign layers  
**C)** A probabilistic method using random number generation determines layer assignment  
**D)** Vectors are assigned sequentially to different layers  
✅ **Correct Answer:** C  
🧠 Topic: HNSW Construction Algorithm  
⏱️ Timestamp: [00:38:36] - [00:44:46]  
📌 **Explanation:** HNSW assigns vectors to layers probabilistically using random number thresholds, ensuring sparsity at higher layers.

---

### **Question 7: HNSW Algorithm Performance**  
According to the demonstration, what makes HNSW (Hierarchical Navigable Small World) algorithm particularly effective for approximate nearest neighbor search?  
**A)** It uses the least memory compared to other algorithms  
**B)** It provides exact results identical to flat L2 search while being much faster  
**C)** It requires fewer hyperparameter configurations  
**D)** It works best with small datasets only  
✅ **Correct Answer:** B  
🧠 Topic: HNSW Algorithm Performance  
⏱️ Timestamp: [01:16:44]  
📌 **Explanation:** HNSW finds the same neighbors as brute-force L2 but does so significantly faster, making it the preferred choice in production.

---

### **Question 8: Inverted File Index (IVF) Fundamentals**  
What is the fundamental approach used by Inverted File Index for efficient vector search?  
**A)** Creating a hierarchical graph structure  
**B)** Using random projections for dimensionality reduction  
**C)** Clustering vectors and maintaining cluster-to-vector mappings  
**D)** Compressing vectors using quantization techniques  
✅ **Correct Answer:** C  
🧠 Topic: Inverted File Index Algorithm  
⏱️ Timestamp: [00:49:34] - [00:51:13]  
📌 **Explanation:** IVF clusters vectors and limits the search to nearby clusters only—greatly reducing computation.

---

### **Question 9: FAISS IVF Index Training Requirements**  
What is the primary reason why IVF (Inverted File) index requires training before adding vectors, unlike the flat index?  
**A)** To optimize memory usage and reduce storage requirements  
**B)** To create clusters and determine which cluster each vector belongs to  
**C)** To improve search speed by preprocessing all vectors  
**D)** To validate the dimensional consistency of input vectors  
✅ **Correct Answer:** B  
🧠 Topic: FAISS IVF Index Implementation  
⏱️ Timestamp: [01:06:56]  
📌 **Explanation:** Training is needed to generate clusters, so future vectors can be assigned to the correct buckets.

---

### **Question 10: Product Quantization Benefits**  
What is the main benefit of Product Quantization in vector indexing?  
**A)** It improves search accuracy by using more precise distance calculations  
**B)** It significantly reduces memory usage by replacing high-dimensional sub-vectors with cluster IDs  
**C)** It eliminates the need for distance calculations  
**D)** It automatically determines the optimal number of clusters  
✅ **Correct Answer:** B  
🧠 Topic: Product Quantization Method  
⏱️ Timestamp: [00:51:13] - [00:52:46]  
📌 **Explanation:** PQ drastically reduces memory by converting sub-vectors to compact cluster codes.

---

### **Question 11: Product Quantization Trade-offs**  
In the Product Quantization (PQ) example shown, what was the primary trade-off observed when searching through the index?  
**A)** Increased search time but better accuracy  
**B)** Reduced memory usage but significantly degraded search accuracy  
**C)** Higher memory consumption but exact results  
**D)** Faster training time but slower search performance  
✅ **Correct Answer:** B  
🧠 Topic: Product Quantization Implementation  
⏱️ Timestamp: [01:21:22]  
📌 **Explanation:** Memory is saved at the cost of accuracy; some nearest neighbors may be incorrect due to compression.

---

### **Question 12: Composite Index Structures**  
What happens when you combine IVF with PQ (Product Quantization) in FAISS?  
**A)** Only the original vectors are clustered into groups  
**B)** Only sub-vectors are quantized without any clustering  
**C)** Both original vectors are clustered AND sub-vectors are quantized separately  
**D)** The algorithms cannot be combined in FAISS  
✅ **Correct Answer:** C  
🧠 Topic: Composite Index Architecture  
⏱️ Timestamp: [01:22:56]  
📌 **Explanation:** IVF+PQ enables scalable search by combining clustering (IVF) with compression (PQ).

---

### **Question 13: FAISS Library Implementation**  
In the FAISS library example shown, what does the `index.search(query_vectors, k)` function return?  
**A)** Only the indices of the nearest neighbor vectors  
**B)** Only the distances to the nearest neighbor vectors  
**C)** Both distances and indices of the k nearest neighbors for each query vector  
**D)** The actual vector values of the nearest neighbors  
✅ **Correct Answer:** C  
🧠 Topic: FAISS Library Usage and Implementation  
⏱️ Timestamp: [01:00:45] - [01:02:18]  
📌 **Explanation:** FAISS returns both distance metrics and the indices of k nearest neighbors.

---

### **Question 14: Vector Database Advantages Over FAISS**  
What are the key limitations of FAISS that vector databases like Qdrant address?  
**A)** FAISS cannot handle high-dimensional vectors effectively  
**B)** FAISS lacks persistence, metadata support, and efficient incremental updates  
**C)** FAISS only works with specific distance metrics  
**D)** FAISS cannot perform approximate nearest neighbor search  
✅ **Correct Answer:** B  
🧠 Topic: Vector Database vs FAISS Comparison  
⏱️ Timestamp: [01:26:06]  
📌 **Explanation:** Qdrant supports persistent storage, metadata filters, and live updates—things FAISS lacks.

---

### **Question 15: Qdrant Search with Filtering**  
In the Qdrant demonstration, what was the result when searching for vector1 but filtering only for category "sports"?  
**A)** Both vector1 and vector2 were returned  
**B)** Only vector1 was returned with highest score  
**C)** Only vector2 was returned despite vector1 being the nearest match  
**D)** No results were returned due to filtering conflict  
✅ **Correct Answer:** C  
🧠 Topic: Qdrant Filtered Search Capabilities  
⏱️ Timestamp: [01:50:41]  
📌 **Explanation:** Filtering lets you exclude results that are closer if they don’t match metadata—great for hybrid search use cases.

---
