# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview
This is a LangChain RAG (Retrieval-Augmented Generation) study project focused on exploring various RAG implementations using the LangChain framework. The project includes examples in both Korean and English, with support for multiple LLM providers.

## Project Structure
- `conda_rag/`: Main project directory containing all notebooks and data
  - `001_SimpleRAG.ipynb`: Basic RAG implementation
  - `002_SimpleRAG_LCEL.ipynb`: RAG using LangChain Expression Language (LCEL)
  - `test.ipynb`: Testing notebook
  - `data/`: Contains text files, CSVs, JSON Lines, and PDFs for RAG experiments
  - `requirements.txt`: Python dependencies

## Development Commands

### Environment Setup
```bash
# Create conda environment (recommended)
conda create -n langchain_rag python=3.10
conda activate langchain_rag

# Install dependencies
cd conda_rag
pip install -r requirements.txt
```

### Running Notebooks
```bash
# Start Jupyter
jupyter notebook

# Or use JupyterLab
jupyter lab
```

### Environment Variables
Create a `.env` file in the root directory with your API keys:
```
OPENAI_API_KEY=your_key_here
ANTHROPIC_API_KEY=your_key_here
GOOGLE_API_KEY=your_key_here
GROQ_API_KEY=your_key_here
DEEPL_AUTH_KEY=your_key_here
```

## Key Architecture Components

### LLM Integrations
The project supports multiple LLM providers through LangChain:
- OpenAI (GPT models)
- Anthropic (Claude)
- Google (Gemini)
- Groq
- Ollama (local models)

### Vector Databases
- **Chroma**: Primary vector store for embeddings
- **FAISS**: Alternative vector store option

### Embeddings
- OpenAI embeddings
- HuggingFace embeddings
- Sentence Transformers

### RAG Pipeline
1. Document loading (PDF, TXT, CSV, XLSX)
2. Text splitting and chunking
3. Embedding generation
4. Vector storage (Chroma/FAISS)
5. Retrieval with similarity search
6. LLM generation with retrieved context
7. Optional: Gradio UI for interactive chat

### Key Libraries
- `langchain`: Core framework
- `langchain-community`: Community integrations
- `langchain-experimental`: Experimental features
- `gradio`: Web UI framework
- `transformers`: HuggingFace transformers
- `krag`: Korean RAG utilities

## Development Notes

### Working with Notebooks
- Notebooks contain both Korean and English documentation
- Clear cell outputs before committing to avoid large diffs
- Test data files are in `conda_rag/data/`

### Adding New LLM Providers
1. Add the provider's langchain package to `requirements.txt`
2. Import and configure in the notebook
3. Update `.env` with necessary API keys

### Vector Database Management
- Chroma databases are stored locally (not tracked in git)
- Clear old vector stores when switching between experiments
- Use unique collection names for different experiments

### Testing RAG Performance
- Test data available in `qa_test.xlsx` and `qa_test_revised.xlsx`
- Evaluate retrieval quality and generation accuracy
- Consider both Korean and English test cases