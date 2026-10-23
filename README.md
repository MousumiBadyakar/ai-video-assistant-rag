# 🎬 AI Video Assistant — RAG-Powered Meeting Intelligence

An AI-powered application that transforms video and audio content into structured, searchable meeting intelligence. Generate transcripts, concise summaries, action items, key decisions, and open questions — then ask questions about the content using **Retrieval-Augmented Generation (RAG)**.

Built with Python, Streamlit, OpenAI Whisper, Sarvam AI, LangChain, Hugging Face embeddings, ChromaDB, and LLM APIs through OpenRouter.

## 🚀 Live Demo

**[Try AI Video Assistant](https://ai-video-assistant-rag-bzdqcspuvayber2p3saiw6.streamlit.app/)**

> Note: Processing time and available features may depend on the input length, configured API providers, and deployment resources.

## ✨ Key Features

- 🎙️ **Speech-to-Text:** Transcribe English audio using OpenAI Whisper.
- 🌐 **Hinglish Transcription:** Convert Hinglish speech into English text using Sarvam AI.
- 📝 **Meeting Summarization:** Generate concise summaries from transcripts.
- 🏷️ **Automatic Title Generation:** Create descriptive meeting titles.
- ✅ **Action Item Extraction:** Identify tasks and follow-up activities.
- 🔑 **Key Decision Detection:** Highlight important decisions discussed in the content.
- ❓ **Open Question Extraction:** Surface unresolved questions.
- 🧠 **RAG-Powered Q&A:** Ask questions and retrieve relevant context from the processed transcript.
- 💬 **Interactive Chat:** Continue asking questions about the processed content.
- 🖥️ **Web UI and CLI:** Use the Streamlit interface or command-line entry point.

## 🧠 System Architecture

```text
          Video / Audio Input
                  |
                  v
          Audio Extraction
                  |
                  v
       Speech-to-Text Processing
        /                    \
       v                      v
 OpenAI Whisper            Sarvam AI
       \                      /
        v                    v
          Meeting Transcript
                  |
        +---------+----------+
        |         |          |
        v         v          v
     Summary   Action      Decisions
               Items       & Questions
                  |
                  v
             RAG Pipeline
                  |
                  v
          Text Chunking
                  |
                  v
       Hugging Face Embeddings
          all-MiniLM-L6-v2
                  |
                  v
              ChromaDB
           Vector Storage
                  |
                  v
          Relevant Retrieval
                  |
                  v
             LLM via
             OpenRouter
                  |
                  v
        Context-Grounded Answers
```

*The architecture illustrates the application's main processing stages. Exact execution paths depend on the configured transcription and language-model providers.*

## 🔍 How the RAG Pipeline Works

The Retrieval-Augmented Generation pipeline allows users to ask questions about the processed transcript.

1. **Transcript preparation:** The generated transcript is split into smaller text chunks.
2. **Embedding generation:** Each chunk is converted into a vector representation using the `all-MiniLM-L6-v2` embedding model.
3. **Vector storage:** The embeddings and associated text are stored in ChromaDB.
4. **Retrieval:** When a user asks a question, relevant transcript chunks are retrieved.
5. **Context construction:** The retrieved content is supplied to the language model as context.
6. **Answer generation:** The model generates a response grounded in the retrieved transcript content.

This approach helps users explore lengthy recordings without having to search through the entire transcript manually.

## 🛠️ Tech Stack

| Category | Technologies |
|---|---|
| Language | Python |
| Frontend | Streamlit |
| Speech-to-Text | OpenAI Whisper, Sarvam AI |
| LLM Integration | LangChain, OpenRouter |
| Embeddings | Hugging Face, `all-MiniLM-L6-v2` |
| Vector Database | ChromaDB |
| Audio/Video Processing | yt-dlp, Pydub, FFmpeg |
| Configuration | python-dotenv |

## 📁 Project Structure

```text
ai-video-assistant-rag/
├── core/
│   ├── extractor.py
│   ├── rag_engine.py
│   ├── summarizer.py
│   ├── transcriber.py
│   └── vector_store.py
├── utils/
│   └── audio_processor.py
├── app.py
├── main.py
├── requirements.txt
├── .env.example
├── .gitignore
└── README.md
```

## ⚙️ Installation and Setup

### Prerequisites

- Python installed on your system
- FFmpeg installed and available on your system's PATH
- API keys for the external services you intend to use

### 1. Clone the repository

```bash
git clone https://github.com/MousumiBadyakar/ai-video-assistant-rag.git
cd ai-video-assistant-rag
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

Activate it on Windows:

```powershell
.venv\Scripts\activate
```

On macOS or Linux:

```bash
source .venv/bin/activate
```

### 3. Install dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Configure environment variables

Create a `.env` file in the project root. Add the API keys required by your configuration:

```env
OPENROUTER_API_KEY=your_openrouter_api_key
SARVAM_API_KEY=your_sarvam_api_key
```

Optional configuration:

```env
WHISPER_MODEL=small
SARVAM_STT_MODEL=saaras:v4
```

Use the variable names supported by your current implementation. Keep your actual API keys private, and never commit your `.env` file to GitHub.

### 5. Install FFmpeg

FFmpeg is required for audio/video processing.

Verify the installation:

```bash
ffmpeg -version
```

If the command is not recognized, install FFmpeg and add its executable directory to your system's PATH.

## ▶️ Running the Application

### Launch the Streamlit interface

```bash
streamlit run app.py
```

Open the local URL displayed in your terminal, typically `http://localhost:8501`.

### Run the command-line interface

```bash
python main.py
```

Follow the prompts displayed by the CLI, if applicable.

## 🔐 Security and Configuration

- Store API keys in environment variables or a local `.env` file.
- Keep `.env` out of version control.
- Avoid exposing credentials in logs, screenshots, or public repositories.
- Use only the API providers and configuration options supported by your current implementation.

## 🔮 Future Improvements

- Support additional languages and transcription providers.
- Improve retrieval quality through configurable chunk sizes and retrieval parameters.
- Add transcript timestamps and source-context references to answers.
- Support exporting summaries and action items into downloadable reports.
- Add persistent meeting history and searchable session management.
- Expand automated testing and deployment monitoring.

## 👩‍💻 Author

**Mousumi Badyakar**

---

⭐ If you find this project interesting, consider giving the repository a star!
