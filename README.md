# Retrieval-Augmented-Generation

Retrieval-Augmented Generation (RAG) is a technique in natural language processing (NLP) that combines the strengths of retrieval-based and generation-based models to produce more accurate and contextually relevant responses. Here is a breakdown of RAG:
* **Retrieval** - Seeking relevant information from a source given a query. For example, getting relevant passages of Wikipedia text from a database given a question.
* **Augmentation** - Using the relevant retrieved information to modify an input to a generative model (e.g. an LLM).
* **Generation** - Generating an output given an input. For example, in the case of an LLM, generating a passage of text given an input prompt.

![RAG work flow](https://github.com/patilurjit/Retrieval-Augmented-Generation/blob/main/images/RAG%20Flow.jpg)

# Why are RAGs used?
1. **Prevention of hallucinations**: Large language models (LLMs) are impressive, but they can sometimes produce incorrect yet seemingly accurate information. RAG pipelines mitigate this issue by supplying LLMs with factual data from retrieved sources, leading to more accurate outputs. Even if a RAG-generated answer appears incorrect, the retrieval process provides access to the original sources for verification.
2. **Utilizing custom data**: While many base LLMs are trained on vast amounts of internet text, giving them strong language modeling capabilities, they often lack specific, detailed knowledge. RAG systems address this by incorporating domain-specific data, such as medical records or company documentation, enabling LLMs to generate customized and contextually relevant responses for specialized applications.
