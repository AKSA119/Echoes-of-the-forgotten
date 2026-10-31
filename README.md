# Echoes of the Forgotten

A cloud-API-powered digital time capsule for letters, old documents, and forgotten software. It creates a factual summary, source-supported details, uncertainties, a timeline, and a clearly labeled fictional atmospheric story.

## Why this fits the open-source AI theme

The application uses a hosted API to access an open-weight model. The model is central to artifact analysis, timeline generation, creative reconstruction, and question answering. It does **not** run a model locally. This project is open-source code, while inference is provided by a third-party cloud service.

> Open weights and open-source software are not identical. Check the selected model's license and the provider's current terms before submitting.

## Features

- Upload TXT, Markdown, or text-based PDF files, or paste text
- Artifact categories for memories, found documents, and forgotten software
- Factual summary, supported evidence, uncertainties, and timeline
- Clearly labeled fictional “echo”
- Ask questions about the archive
- Download the result as JSON
- Includes a fictional sample so you can demo without personal documents

## Run without a local model

The app runs as a Python web interface, but all model inference is performed by the Groq cloud API. No Ollama, model download, or GPU is required.

### 1. Create an API key

Create a Groq account and an API key at https://console.groq.com/ . Check the current free-tier availability, rate limits, and supported models in your account.

### 2. Install dependencies

Python 3.10+ is recommended.

```bash
python -m venv .venv
```

Windows:
```bat
.venv\Scripts\activate
```

macOS/Linux:
```bash
source .venv/bin/activate
```

Then:
```bash
pip install -r requirements.txt
```

### 3. Configure the API key

Copy `.env.example` to `.env`, then replace the placeholder:

```env
GROQ_API_KEY=your_real_key_here
GROQ_MODEL=openai/gpt-oss-20b
```

If the model is unavailable to your account, choose a supported model from https://console.groq.com/docs/models and update `GROQ_MODEL`.

### 4. Launch

```bash
python app.py
```

Open the local URL printed in the terminal. This is just the app UI; inference is still cloud-based.

## Deploy publicly on Hugging Face Spaces (Gradio)

1. Create a new **Gradio** Space at https://huggingface.co/spaces.
2. Upload `app.py`, `requirements.txt`, and this README.
3. Open **Settings → Secrets** and add `GROQ_API_KEY` with your API key as the value.
4. Optionally add `GROQ_MODEL` as a Space variable.
5. Wait for the Space to build and open the public app URL.

Never put the API key in source code, README, screenshots, or public repository files. Do not commit `.env`.

Free hosting and API quotas can change; verify the current provider limits. Publicly deployed apps may consume your API quota, so consider access controls or usage limits before sharing widely.

## Demo script (about 60 seconds)

1. Open the sample letter.
2. Click **Uncover the echo**.
3. Show the factual summary and evidence separately from the fictional story.
4. Ask: “Which details are actually supported by the source?”
5. Download the JSON archive.

## Privacy and limitations

- Uploaded text is sent to the configured AI API for processing. Do not upload private family records or sensitive information unless you are comfortable with the provider's data terms.
- The model may make mistakes. Review outputs before treating them as historical facts.
- The creative echo is fiction, not evidence and not communication with a deceased person.
- The first version supports TXT, Markdown, and text-based PDFs. Scanned PDFs and audio transcription are not included.
- Archives are downloadable JSON files. This app does not provide a permanent cloud database or user accounts.

## Suggested repository description

**Echoes of the Forgotten — an open-source AI time capsule that turns old artifacts into evidence-aware timelines and fictional stories.**

## License

This project code is offered under the MIT License. Review the model's own license separately; the app's license does not change model terms.
