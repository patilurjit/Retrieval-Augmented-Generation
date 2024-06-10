# Retrieval-Augmented-Generation

Retrieval-Augmented Generation (RAG) is a technique in natural language processing (NLP) that combines the strengths of retrieval-based and generation-based models to produce more accurate and contextually relevant responses. Here is a breakdown of RAG:
* **Retrieval** - Seeking relevant information from a source given a query. For example, getting relevant passages of Wikipedia text from a database given a question.
* **Augmentation** - Using the relevant retrieved information to modify an input to a generative model (e.g. an LLM).
* **Generation** - Generating an output given an input. For example, in the case of an LLM, generating a passage of text given an input prompt.

![RAG work flow](https://github.com/patilurjit/Retrieval-Augmented-Generation/blob/main/images/RAG%20Flow.jpg)

# Why are RAGs used?
1. **Prevention of hallucinations**: Large language models (LLMs) are impressive, but they can sometimes produce incorrect yet seemingly accurate information. RAG pipelines mitigate this issue by supplying LLMs with factual data from retrieved sources, leading to more accurate outputs. Even if a RAG-generated answer appears incorrect, the retrieval process provides access to the original sources for verification.
2. **Utilizing custom data**: While many base LLMs are trained on vast amounts of internet text, giving them strong language modeling capabilities, they often lack specific, detailed knowledge. RAG systems address this by incorporating domain-specific data, such as medical records or company documentation, enabling LLMs to generate customized and contextually relevant responses for specialized applications.

# Implementation
1. **Import and format PDF document** - The PDF document is downloaded with a get request and then preprocessed to be used further.
2. **Splitting pages into sentences** - The text on each page is split into individual sentences which are further split into smaller lists of sentences to fit within the context window of the embedding generation model using a `spaCy` pipeline.
3. **Embedding generation** - The embeddings are generated by passing the smaller chunks of text to the `all-mpnet-base-v2` model which generates an embedding vector of size 768.
4. **Vector database for storing embeddings** - The embeddings are stored in MongoDB Atlas, which is a vector database for faster retrieval of relevant text.
5. **Retrieve relevant passages** - Relevant passages are retrieved using the `vectorSearch` operator.
6. **Setting up the LLM model for response generation** - The LLM chosen for response generation is Google's `gemma-2b-it`, which is the instruct version of the Gemma model with 2 billion parameters.
7. **Augmenting the prompt with context items** - The prompt is combined with the context items retrieved from the database.
8. **Combine the retrieval augmentation and response generation** - The prompt is augmented with the retrieved items and used to generate a response. 
