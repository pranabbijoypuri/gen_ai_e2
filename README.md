# gen_ai_e2

## Overview

This repository contains a Medical Diagnosis RAG assistant built with LangChain, Chroma, and Gradio. It uses a knowledge base and patient history retriever to answer clinical questions with citation-aware responses.

## Setup Instructions

### 1. Create and activate the virtual environment

```powershell
cd <<your solution folder>>
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

If you use Command Prompt instead of PowerShell:

```cmd
cd <<your solution folder>>
python -m venv .venv
.\.venv\Scripts\activate.bat
```

### 2. Install dependencies with Poetry

```powershell
pip install poetry
poetry install
```

If Poetry is already installed and available as `python -m poetry`, use:

```powershell
python -m poetry install
```

> Note: This project is configured for dependency management only and does not install the package itself.

### 3. Install any missing packages manually

If you need to add or update packages, use:

```powershell
poetry add <package-name>
```

## Environment Variables

Create a `.env` file in the project root (`<<your solution folder>>\.env`) with the following values:

```env
OPENAI_API_KEY=your_openai_api_key_here
HF_TOKEN=your_hugging_face_token
```

This project loads environment variables using `python-dotenv`, so the notebook will read `.env` automatically.

## Model Setup

This project currently uses the following models configured in the notebook:

- Embedding model: `sentence-transformers/all-MiniLM-L6-v2`
- Chat model: `gpt-5-nano`

If you need to change the models, update the values in the notebook cell under `EMBEDDING_MODEL_NAME` and `CHAT_MODEL_NAME`.

### Recommended model configuration

```python
EMBEDDING_MODEL_NAME = "sentence-transformers/all-MiniLM-L6-v2"
CHAT_MODEL_NAME = "gpt-5-nano"
```

## Running the Notebook

Open `Medical_Diagnosis_RAG_Assistant.ipynb` in Jupyter or VS Code and run the cells in order from top to bottom.

### Optional: Launch the Gradio chat UI

The notebook includes a Gradio-based chat interface. After the main setup cells execute successfully, run the final interface cell to start Gradio.

## Troubleshooting

- If imports fail, confirm the `.venv` is active and `poetry install` completed successfully.
- If Gradio cannot render markdown properly, verify the notebook is using the `gr.Blocks` chat UI code and that you have a compatible Gradio version installed.
- Ensure `OPENAI_API_KEY` and `HF_TOKEN` is set in `.env` before running the notebook.

## Notes

- This project is not intended to provide medical diagnosis. It is a decision-support assistant and should be used only for demonstration purposes.
- The notebook uses local sample data in `sample_data/` and persists the Chroma database under `chroma_db/`.
