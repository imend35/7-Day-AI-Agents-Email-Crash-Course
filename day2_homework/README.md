In this project, I preferred to work with real-world GitHub documentation instead of artificial datasets.

I selected README files from popular repositories in AI, Machine Learning, Deep Learning, and LLM domains such as PyTorch, OpenAI Cookbook, LangChain, FastAPI, and Hands-on ML.

The main reason behind this choice was to work with:

Structured markdown content
Real technical documentation
Texts that reflect actual production-level use cases

This allowed me to simulate a real scenario where large-scale documentation needs to be processed and prepared for LLM-based systems like semantic search or RAG pipelines.

Initially, I experimented with the BigQuery GitHub dataset, but due to limitations in accessing consistent README content, I switched to raw markdown sources to ensure better data quality and reliability.

# Step 1  :  Dataset Selection

For this project, I intentionally chose to use real-world GitHub markdown documentation instead of synthetic or small-scale datasets.

I selected README files from well-known repositories in the AI, Machine Learning, Deep Learning, and LLM ecosystem, including:

Hands-on Machine Learning (Scikit-Learn)
PyTorch
OpenAI Cookbook
LangChain
FastAPI

These repositories were chosen because they provide:

Well-structured markdown content with clear headings (#, ##, ###)
Rich technical explanations relevant to AI systems
Real-world documentation patterns used in production environments

Using these sources allowed me to simulate a realistic scenario where large documentation needs to be processed and prepared for LLM-based applications such as semantic search or Retrieval-Augmented Generation (RAG).

Additionally, I avoided using the BigQuery GitHub dataset due to content alignment and extraction limitations, and instead opted for raw markdown files to ensure data quality and consistency.

This approach enabled me to better evaluate different chunking strategies on meaningful, structured, and domain-specific text data.

  # Step 2 — Simple Chunking (Sliding Window Approach)

In this step, I applied a simple chunking strategy using a sliding window approach to split large documents into smaller, manageable pieces.

The main goal of this step was to prepare long markdown documents for LLM processing by dividing them into fixed-size chunks while preserving contextual continuity.

Instead of splitting the text into completely separate blocks, I used an overlapping window technique. This means each chunk shares some common content with the previous one, helping to maintain context across boundaries.

###  Why this approach?
Large documents cannot be directly processed by LLMs due to token limitations
Splitting text improves retrieval performance
Overlapping prevents loss of meaning when sentences are cut in the middle

  ###  Implementation logic
Chunk size: 2000 characters
Step size: 1000 characters (overlap)
Each new chunk starts before the previous one ends

  This creates a structure like:

Chunk 1 → [0 - 2000]
Chunk 2 → [1000 - 3000]
Chunk 3 → [2000 - 4000]

  def sliding_window(text, size=2000, step=1000):
    chunks = []
    for i in range(0, len(text), step):
        chunk = text[i:i+size]
        chunks.append(chunk)
        if i + size >= len(text):
            break
    return chunks


### Outcome

This method produced uniform chunk sizes and was easy to implement. However, since it is purely character-based, it sometimes splits sentences or breaks semantic structure.

This limitation motivated the exploration of more advanced chunking strategies in the next steps.

  
