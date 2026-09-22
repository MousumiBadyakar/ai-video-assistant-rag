# 🎬 AI Video Assistant

An AI-powered meeting assistant that converts video/audio content into **transcripts, summaries, action items, key decisions, open questions, and RAG-based answers**.

The project combines *OpenAI Whisper, Sarvam AI, OpenRouter, LangChain, HuggingFace embeddings, and ChromaDB* to build an end-to-end meeting intelligence pipeline.

## 🚀 Live Demo

🔗 **[Try the AI Video Assistant](https://ai-video-assistant-rag-bzdqcspuvayber2p3saiw6.streamlit.app/)**

## ✨ Features

* 🎙️ **Speech-to-Text** — English transcription using OpenAI Whisper.
* 🌐 **Hinglish Transcription** — Hinglish-to-English transcription using Sarvam AI.
* 📝 **Meeting Summarization** — Generates concise meeting summaries.
* 🏷️ **Title Generation** — Automatically generates a meeting title.
* ✅ **Action Items** — Extracts tasks and follow-ups.
* 🔑 **Key Decisions** — Identifies important decisions.
* ❓ **Open Questions** — Extracts unresolved questions.
* 🧠 **RAG Q&A** — Ask questions grounded in the meeting transcript.
* 💬 **Interactive Chat** — Continue conversations about the processed meeting.
* 🖥️ **Streamlit + CLI** — Available through both a web interface and command line.

## 🧠 RAG Architecture

```text
Video / Audio
     │
     ▼
Audio Processing
     │
     ▼
Whisper / Sarvam AI
     │
     ▼
Meeting Transcript
     │
     ├──────────────► Summary
     │
     ├──────────────► Action Items
     │
     ├──────────────► Key Decisions
     │
     └──────────────► RAG Pipeline
                           │
                           ▼
                    Text Chunking
                           │
                           ▼
                 HuggingFace Embeddings
                           │
                           ▼
                       ChromaDB
                           │
                           ▼
                      Retriever
                           │
                           ▼
                     Mistral LLM
                           │
                           ▼
                    Grounded Answer
```

### RAG Workflow

1. The transcript is split into smaller chunks.
2. Chunks are converted into vector embeddings using `all-MiniLM-L6-v2`.
3. Embeddings are stored in ChromaDB.
4. Relevant chunks are retrieved for each user question.
5. Retrieved context is passed to Mistral AI.
6. The model generates an answer based on the meeting transcript.

## 🛠️ Tech Stack

**Language:** Python

**GenAI / LLM:** OpenRouter, LangChain

**Speech-to-Text:** OpenAI Whisper, Sarvam AI

**RAG:** ChromaDB, HuggingFace Sentence Transformers

**Audio/Video:** yt-dlp, Pydub, FFmpeg

**UI:** Streamlit

**Environment:** python-dotenv

## 📁 Project Structure

```text
ai-video-assistant-rag/
│
├── core/
│   ├── extractor.py
│   ├── rag_engine.py
│   ├── summarizer.py
│   ├── transcriber.py
│   └── vector_store.py
│
├── utils/
│   └── audio_processor.py
│
├── app.py
├── main.py
├── requirements.txt
├── .env.example
├── .gitignore
└── README.md
```

## 🚀 Setup

### 1. Clone the repository

```bash
git clone https://github.com/MousumiBadyakar/ai-video-assistant-rag.git
cd ai-video-assistant-rag
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

Windows:

```powershell
.venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure API keys

Create a `.env` file:

```env
OPENROUTER_API_KEY=your_openrouter_api_key
SARVAM_API_KEY=your_sarvam_api_key
```

Optional:

```env
WHISPER_MODEL=small
SARVAM_STT_MODEL=saaras:v4
```

### 5. Install FFmpeg

FFmpeg is required for audio/video processing.

Verify:

```bash
ffmpeg -version
```

## ▶️ Run

### Streamlit

```bash
streamlit run app.py
```

### CLI

```bash
python main.py
```




## 👩‍💻 Author

**Mousumi Badyakar**

