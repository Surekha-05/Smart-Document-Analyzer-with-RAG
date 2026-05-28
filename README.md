# 🚀 AI-Powered Multi-Modal RAG System


This repository contains an AI-powered, multi-modal Retrieval-Augmented Generation (RAG) platform. It allows users to interact intelligently with various data sources, including documents, YouTube videos, and audio files. The system integrates an AI chat assistant and a presentation generator, all accessible through a unified Streamlit interface.

## Features

-   **💬 AI Chat Assistant**: A conversational AI powered by NVIDIA models for general queries.
-   **📄 PDF Q&A**: Upload documents (PDF, DOCX, TXT, PPTX) and ask questions based on their content. The system uses RAG with NVIDIA AI for context-aware answers.
-   **🎥 YouTube Q&A**: Paste a YouTube video URL to fetch its transcript and ask questions about the video's content.
-   **🎤 Audio Intelligence**: Upload audio files (MP3, WAV, M4A) for automatic transcription via Whisper, AI-powered summarization, and conversational Q&A using a local LLM.
-   **📊 AI Presentation Generator**: Automatically create a PowerPoint presentation from a PDF document based on a specified topic. The process involves RAG, content summarization, and image sourcing.

## Technology Stack

-   **Frontend**: Streamlit
-   **AI & LLMs**:
    -   NVIDIA AI Endpoints (`meta/llama-3.1-8b-instruct`, `openai/gpt-oss-120b`)
    -   Ollama (`phi3`) for local audio processing
-   **Embeddings**:
    -   NVIDIA Embeddings (`nvidia/llama-nemotron-embed-1b-v2`)
    -   Sentence Transformers (`all-MiniLM-L6-v2`)
-   **Vector Storage & Search**: FAISS (Facebook AI Similarity Search)
-   **Core Frameworks**: LangChain
-   **Data Processing**:
    -   PyMuPDF (for PDF extraction)
    -   `youtube-transcript_api`
    -   `openai-whisper` (for audio transcription)
    -   `python-pptx` (for presentation generation)
    -   `sumy` (for extractive summarization)
    -   `unstructured` (for diverse document loading)

## Modules Overview

The `backend/` directory is organized into several modular components:

-   `/chatbot`: Implements the general-purpose AI chat functionality using `langchain-nvidia-ai-endpoints`.
-   `/pdf_rag`: Manages document uploading, parsing (PDF, DOCX, TXT, PPTX), vectorization using NVIDIA embeddings, and RAG-based Q&A.
-   `/yt_rag`: Handles YouTube transcript extraction, vectorization, and Q&A.
-   `/audio_to_chat`: Provides audio intelligence features, including local transcription with Whisper, summarization, and Q&A powered by local embeddings and Ollama.
-   `/pdf_to_ppt`: A complete pipeline to generate a PowerPoint presentation from a PDF. It extracts text and images, uses RAG to find relevant content for a topic, summarizes it into slides, and fetches images.

## Setup and Installation

Follow these steps to set up and run the project locally.

**1. Clone the Repository**
```bash
git clone https://github.com/surekha-05/Smart-Document-Analyzer-with-RAG.git
cd Smart-Document-Analyzer-with-RAG
```

**2. Create a Virtual Environment (Recommended)**
```bash
python -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
```

**3. Install Dependencies**
```bash
pip install -r requirements.txt
```

**4. Set Up Environment Variables**

You need an API key from a service like NVIDIA NIM to use the hosted models.

-   Navigate to the `backend/` directory.
-   Create a file named `.env` by copying the structure from `backend/.env`:

    ```env
    NVIDIA_API_KEY = "YOUR_NVIDIA_API_KEY_HERE"
    NVIDIA_API_KEY_2 = "YOUR_NVIDIA_API_KEY_HERE"
    NVIDIA_API_KEY_3 = "YOUR_NVIDIA_API_KEY_HERE"
    ```
-   Replace `"YOUR_NVIDIA_API_KEY_HERE"` with your actual NVIDIA API key. All three variables can hold the same key.

**5. Install and Run Ollama (for Audio Q&A)**

The Audio Intelligence module requires a local LLM running via Ollama.

-   [Download and install Ollama](https://ollama.com/).
-   Pull the required model from your terminal:
    ```bash
    ollama pull phi3
    ```
-   Ensure the Ollama server is running in the background.

**6. Run the Application**

From the root directory of the project, run:
```bash
streamlit run main.py
```

The application will open in your web browser.

## Usage

Once the application is running, you can navigate through the different functionalities using the tabs at the top of the page:

-   **AI Chat**: Have a direct conversation with the AI assistant.
-   **PDF Q&A**: Upload a document, click "Process Document," and then ask questions related to its content.
-   **YouTube Q&A**: Paste a YouTube video URL, click "Load Transcript," and then ask questions.
-   **Audio Q&A**: Upload an audio file, click "Process Audio," to get a summary and transcript. you can then ask questions about the audio.
-   **PPT Generator**: Upload a PDF, specify a topic from the document, configure the settings (e.g., number of slides), and click "Generate Presentation" to create and download a `.pptx` file.

## Images

<img width="1764" height="802" alt="image" src="https://github.com/user-attachments/assets/ad94976e-cf8c-4df3-a738-92a05feb4ad6" />
<img width="1553" height="826" alt="image" src="https://github.com/user-attachments/assets/9828e0de-ce65-442e-a1c4-268f2cf121ae" />
<img width="1817" height="868" alt="image" src="https://github.com/user-attachments/assets/94e1f84d-542e-430f-b44a-b98e2cc707de" />
<img width="1525" height="867" alt="image" src="https://github.com/user-attachments/assets/301c1e3b-0be4-4c1b-8021-b5a44b089743" />
<img width="1800" height="387" alt="image" src="https://github.com/user-attachments/assets/ce4a4af4-a531-46b6-bb5a-d1b7479a97e7" />
<img width="1216" height="790" alt="image" src="https://github.com/user-attachments/assets/218d15e2-c049-4acf-ac45-d4036a838de9" />
