# What is RAG
Taken from Ben Clavié at Mastering LLMs Conference.

No more than **stitching together Retrieval and Generation to ground the latter**.
- The Retrieval part comes from Information Retrieval.
- The Generation part comes from an LLM.

A **good RAG** is made of good components:
- good retrieval pipeline
- good generative model
- good way of linking them up

### The most simple RAG pipeline
A bi-encoder: we need to encode documents (we can do this offline) and the query (encoded in real-time).
- We create single-vector representations from text/documents

  
![image](https://github.com/user-attachments/assets/960ad9e0-970c-48de-a339-b24de2b41916)

*Figure: Compact RAG MVP*

### Where´s the vector DB?

The key of a VectorDB is to allow **Approximate Search** when search is huuge.

### What is re-ranking
Documents are unaware to the query. The query is unaware fo my documents. Sometimes it is good to know where the query is aiming at. How do we fix this?
The most common approach is using **Cross-Encoders**.

![image](https://github.com/user-attachments/assets/690b5a91-55c4-4fd1-8ad1-d3c73b02f940)

*Figure: Cross-encoder to make docuemnts and query aware between each other*

Vert powerful, the model knows exactly what you are looking for and retrieves the best information to get an answer. 
However, this is not very realistic to execute!

The idea behind **re-ranking**, is to:
- Retrieve a subset of your documents, with an efficient model
- Over that subset, score your documents with a very powerful but computationally expensive model

![image](https://github.com/user-attachments/assets/eb5412be-1b48-4aed-ad38-956e4cc1f10a)

*Figure: Compact RAG MVP + Re-ranking*

### Keyword search: old-times live on

- Semantic search via embeddings is bound to **lose information because of compression**!
- Embeddings learn to **represent information that is useful to their training queries**.
- This training will never be fully representative, especially when you use the model on your own data, in which it hasnt been trained.
- About **keyword-search**:
  - To capture all this signal, **you should ensure your pipeline uses Keyword Search**
  - **BM25**, which is powered by TF-IDF, supports **full-text-search** and is a strong baseline
  - BM25 is very powerful on longer documents and documents containing a lot fo domain-specific jargon.
  - It´s nearly a frere-lunch addition to the pipeline.
  
![image](https://github.com/user-attachments/assets/fb70c733-3e31-43ff-8e9d-1f31f7005915)

*Figure: Compact RAG MVP + Re-ranking + Full-Text Search*

### Metadata Filtering

Outside of academic benchmarks, documents do not exist in a vacuum. There´s a lot fo metadata around them, some of which can be very informative.
Example:
- "Can you get me the cruise division financial report for Q4 2022"

What goes on here is:
- The model must accurately represent all of "financial report", "cruise division", "Q4" and "2022" into a **single vector**. If not, it will contain only some of these contents.
- If the number of documents you search for is too high, you are passing too many irrelevant documents for the LLM to handle correctly.
- It can happen, but it is unlikely to happen every time

A solution:
- Use **entity detection models** who can easily extract zero-shot entity types from text.
- It will detect, for example:
  - "cruise division" -> department
  - "financial report" -> document type
  - "Q4 2022" -> time period

All you need to do is ensure **business/query-relevant information is stored alongside their associated documents**. Then, we can **use this metadata to pre-filter** to only query things that make sense.
So, you need to process **documents** thorugh the metadata filtering layer.

![image](https://github.com/user-attachments/assets/00dd3ec6-481c-44bb-903f-f4b9ffe5597f)

*Figure: Compact RAG MVP + Re-ranking + Full-Text Search + Metadata filtering*

# So what
- This is your **ideal quick MVP**
- Most other imporvements are also valuable, but with decreasing cost-effort ratio
- It´s worth learnign about sparse and multi-vector methods (SPLADE and COLBERT)


  


