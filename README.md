# Supplementary Repository: RAG vs Non-RAG Concept Extraction for ENDOH Ontology Expansion

This repository serves as a supplementary resource for our study comparing Retrieval-Augmented Generation (RAG) and Non-RAG LLM-based methods for automatic concept extraction to support expansion of the Environmental Determinants of Health Ontology (ENDOH). It includes all scripts, notebooks, data processing steps, and evaluation procedures used to generate, clean, and analyze concept sets across 15 environmental health categories.

---

## Overview of the Project

The objective of this repository is to systematically compare two LLM-based concept extraction strategies:

1. RAG (Retrieval-Augmented Generation)  
2. Non-RAG (LLM-only Generation)

Both pipelines generate candidate concepts for ontology expansion, and both are evaluated using semantic similarity and other quantitative metrics. The repository includes all processes from literature ingestion to final similarity scoring.

---

# Methodology Summary

## 1. RAG Pipeline

The RAG method grounds the LLM in relevant literature before generating concepts. This reduces hallucinations and increases alignment with real-world terminology.

### Steps in the RAG Pipeline

1. **Source Document Loading**  
   Load domain-relevant PDF files (open-access journals, conference papers).

2. **Text Cleaning**
   Remove boilerplate content such as headers, footers, page numbers, and references.

3. **Text Chunking**
   Segment the cleaned text into smaller chunks (e.g., 350–400 tokens) with preserved context.

4. **Vector Embedding**
   Convert chunks to embeddings using a SentenceTransformer model (all-MiniLM-L6-v2).

5. **FAISS Index Construction**
   Store embeddings in a FAISS index for fast similarity search.

6. **Adaptive-k Retrieval**
   Retrieve top-k most relevant chunks for each category using:
   - Minimum k threshold  
   - Maximum k threshold  
   - Score drop-based automatic adjustment  
   This guarantees at least ten relevant documents per category.

7. **RAG Concept Extraction**
   Provide the LLM with:
   - The category definition  
   - The retrieved literature chunks  
   - Target output format (one concept per line)  

8. **Post-processing**
   Deduplicate concepts, normalize formatting, and save to CSV.

---

## 2. Non-RAG Pipeline

The Non-RAG method uses the same category prompts but does not include literature. Instead, it includes a placeholder text block and its reference.

### Steps in the Non-RAG Pipeline

1. Use the same category prompt used in RAG, except literature is removed.
2. Insert the prompt
3. Generate concepts across one or multiple temperatures (0.1 to 1.0).
4. Clean and standardize the generated concepts.
5. Save the results to the output CSV.

---

## 3. Semantic Evaluation Pipeline

Both RAG and Non-RAG outputs are evaluated using the same semantic similarity framework.

### Leave-One-Out Semantic Similarity for ENDOH Concepts

For each existing ENDOH concept:

1. Remove the concept temporarily.  
2. Compute its cosine similarity against all remaining ENDOH concepts.  
3. Record the highest similarity value.  
4. Insert the concept back.  
5. Repeat for all concepts.  
6. Compute the final average similarity score.

This provides a baseline for comparison. For example:

RAG average similarity = 0.5490  
Non-RAG average similarity = 0.4976

---

# Repository Structure