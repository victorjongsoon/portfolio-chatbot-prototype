# Portfolio Chatbot Prototype

This project is a prototype chatbot that allows you to **ask questions about my resume** using a combination of:

- Pinecone vector database  
- HuggingFace LLM (Zephyr-7b-beta)  
- LangChain PDF parsing & text splitting  
- Gradio UI for easy interaction  

---

## Architecture

The chatbot is implemented in **two phases**, using a simple RAG (Retrieval-Augmented Generation) pipeline:

![Portfolio Chatbot Prototype Architecture](Victor%20Portfolio%20Chatbot%20Prototype%20Architecture.png)

### Phase 1: Data Preparation & Indexing

- The resume PDF (`Resume.pdf`) is loaded using `LangChain`'s PDF loader.
- The text is split into **chunks** (overlapping text blocks).
- Each chunk is embedded into a vector using `LlamaTextEmbedV2`.
- The embeddings are stored in **Pinecone** (Vector Database), along with metadata.

### Phase 2: RAG Pipeline

- A user query is received via the **Gradio UI**.
- The query is embedded and used to retrieve **top relevant chunks** from Pinecone.
- A prompt is built by combining retrieved chunks + user query.
- The prompt is sent to **HuggingFace Zephyr-7b-beta LLM**.
- The LLM generates an answer, which is displayed in the Gradio UI.

---

This architecture allows the chatbot to **ground its answers based on real data** from my resume, making it more accurate and controllable.

---

### Requirements

- Python 3.11+
- pip packages:
    - `pinecone-client`
    - `langchain`
    - `langchain_community`
    - `gradio`
    - `requests`

## Demo

Watch the demo video on YouTube: [Portfolio Chatbot Prototype Demo](https://www.youtube.com/watch?v=AgzKZMj_n70)

## Author

**Victor Jong**  
[GitHub](https://github.com/victorjongsoon)
