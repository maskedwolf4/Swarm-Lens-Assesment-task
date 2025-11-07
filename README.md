# Swarm Lens RAG System

A **Retrieval-Augmented Generation (RAG)** system built with LangGraph and Streamlit for document-based Q&A with multimodal document support.[1]

## Features

- **Multimodal Document Support**: PDF, DOCX, PPTX, TXT
- **LangGraph Workflow**: Orchestrated RAG pipeline with state management
- **Smart Retrieval**: ChromaDB vector store with fallback to online search (Tavily)
- **Quality Evaluation**: Document relevance scoring and answer grounding assessment
- **Interactive UI**: Streamlit-based interface with real-time processing

## Workflow

```
Document Upload → Chunking → Embedding → Vector Store
                                             ↓
User Question → Retrieval → Relevance Check → Answer Generation
                                ↓                    ↓
                         Fallback to Online    Evaluation
```

## Setup

### Prerequisites
- Python 3.12+
- Google Gemini API key
- Tavily API key (optional)
- LangChain API key (optional, for tracing)

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/maskedwolf4/Swarm-Lens-Assesment-task.git
cd Swarm-Lens-Assesment-task
```

2. **Install dependencies**
```bash
pip install -e .
```

3. **Configure environment variables**
```bash
cp .env.example .env
```

Edit `.env` with your API keys:
```
GEMINI_API_KEY=your_gemini_api_key
TAVILY_API_KEY=your_tavily_api_key
LANGCHAIN_API_KEY=your_langchain_api_key  # Optional
```

## Usage

### Run the Application
```bash
streamlit run app.py
```

### Using the Interface
1. Upload a document (PDF, DOCX, PPTX, TXT)
2. Wait for processing
3. Ask questions about the document
4. View answers with relevance scores and system metrics

## Project Structure

- `app.py` - Main Streamlit application
- `rag_workflow.py` - LangGraph workflow implementation
- `document_loader.py` - Multimodal document loading
- `document_processor.py` - Text chunking and vector store creation
- `chains/` - LangChain chains for evaluation
- `config.py` - Configuration settings
- `state.py` - Workflow state definitions

## Key Components

### Document Processing
- Loads and extracts text from multiple formats
- Chunks text with overlap for better retrieval
- Creates embeddings using Google Generative AI

### RAG Workflow (LangGraph)
- **Retrieve**: Fetch relevant documents from vector store
- **Grade**: Evaluate document relevance
- **Generate**: Create answers using Gemini
- **Fallback**: Online search if documents insufficient

### Evaluation
- Document relevance scoring
- Question-answer match assessment
- Answer grounding verification

## API Keys Required

| Service | Purpose | Required |
|---------|---------|----------|
| Google Gemini | LLM for generation & embeddings | ✅ Yes |
| Tavily | Online search fallback | ❌ Optional |
| LangChain | Workflow tracing | ❌ Optional |

---

**Built for Swarm Lens AI Intern Assessment**

