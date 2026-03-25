In this project, I preferred to work with real-world GitHub documentation instead of artificial datasets.

I selected README files from popular repositories in AI, Machine Learning, Deep Learning, and LLM domains such as PyTorch, OpenAI Cookbook, LangChain, FastAPI, and Hands-on ML.

The main reason behind this choice was to work with:

Structured markdown content
Real technical documentation
Texts that reflect actual production-level use cases

This allowed me to simulate a real scenario where large-scale documentation needs to be processed and prepared for LLM-based systems like semantic search or RAG pipelines.

Initially, I experimented with the BigQuery GitHub dataset, but due to limitations in accessing consistent README content, I switched to raw markdown sources to ensure better data quality and reliability.

# Step 1  :  Dataset Selection

In this project, I preferred to work with real-world GitHub documentation instead of artificial datasets.

I selected README files from popular repositories in AI, Machine Learning, Deep Learning, and LLM domains such as PyTorch, OpenAI Cookbook, LangChain, FastAPI, and Hands-on ML.

The main reason behind this choice was to work with:

Structured markdown content
Real technical documentation
Texts that reflect actual production-level use cases

This allowed me to simulate a real scenario where large-scale documentation needs to be processed and prepared for LLM-based systems like semantic search or RAG pipelines.

Initially, I experimented with the BigQuery GitHub dataset, but due to limitations in accessing consistent README content, I switched to raw markdown sources to ensure better data quality and reliability.
  
# Step 2 — Simple Chunking

In this step, I implemented a basic chunking strategy using a sliding window approach.

My aim was to split long markdown documents into smaller pieces that can be processed by LLMs more efficiently.

I used overlapping chunks to preserve context between segments. This is important because splitting text without overlap may lead to loss of meaning, especially when sentences are cut in the middle.

The implementation was straightforward and effective as a baseline. However, I observed that this method does not always respect the semantic structure of the text, which led me to explore more advanced approaches in the following steps.

Step 3 — Paragraph Chunking

In this step, I tried a more natural way of splitting the documents by using paragraph boundaries instead of fixed character limits.

My intention was to preserve the meaning and flow of the text, since paragraphs usually represent complete ideas.

Compared to the previous method, this approach produced more readable and structured chunks. However, I noticed that in technical documentation, paragraphs can sometimes be too short or fragmented, which may lead to loss of context.

This made me realize that while paragraph-based chunking improves readability, it may still not be enough on its own for building effective LLM-based systems.

Step 4 — Section Chunking

In this step, I leveraged the natural structure of markdown documents and applied section-based chunking.

Instead of splitting text arbitrarily, I used markdown headers to divide the content into meaningful sections. This allowed me to keep related information together and preserve the overall context.

Compared to the previous approaches, this method felt much more aligned with how technical documentation is actually written and consumed.

Each chunk became more self-contained and easier to understand, which makes this approach especially suitable for LLM-based applications such as semantic search or RAG systems.

Step 5 — Comparison

In this step, I compared the three chunking strategies I implemented.

Simple chunking was the easiest to apply and worked well as a baseline, but it sometimes broke sentences and disrupted meaning.

Paragraph-based chunking improved readability, but in technical documents, paragraphs can be too short and fragmented, which may lead to loss of context.

Section-based chunking clearly performed the best. Since markdown documents are already structured with headers, this approach preserved the meaning and kept related information together.

Step 6 — Final Conclusion

In this project, I experimented with different chunking strategies to better understand how to prepare real-world documentation for LLM-based systems.

I started with a simple approach, then gradually moved towards more structured methods. This helped me clearly see how different strategies affect readability, context, and overall data quality.

Among all approaches, section-based chunking stood out as the most effective, since it aligns naturally with the structure of markdown documents and keeps related information together.

This project gave me a strong understanding of how important data preprocessing is when working with LLMs, especially in real-world scenarios.


