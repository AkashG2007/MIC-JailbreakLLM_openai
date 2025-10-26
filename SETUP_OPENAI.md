# OpenAI Integration Setup Guide

This guide explains how to switch from Ollama to OpenAI in the MIC-JailbreakLLM project.

## Prerequisites

1. Python 3.8 or higher
2. A valid OpenAI API key (get one from https://platform.openai.com/api-keys)

## Installation

1. Install the required dependencies:
```bash
pip install -r requirements.txt
```

## Configuration

The `.env` file has been created in the project root. You need to:

1. **Get your OpenAI API key:**
   - Go to https://platform.openai.com/api-keys
   - Create a new API key (free tier is available)
   - Copy the key

2. **Update the `.env` file:**
   - Open the `.env` file in the project root
   - Replace `your_openai_api_key_here` with your actual OpenAI API key
   - Optionally change the model (default is `gpt-3.5-turbo`)
   
3. **Switch between Ollama and OpenAI:**
   - To use OpenAI: Set `BACKEND_MODEL=openai` in `.env`
   - To use Ollama: Set `BACKEND_MODEL=ollama` in `.env` (or leave it as default)

## Environment Variables

The `.env` file contains the following important variables:

### OpenAI Configuration
- `OPENAI_API_KEY` - Your OpenAI API key
- `OPENAI_MODEL` - The model to use (default: gpt-3.5-turbo)
- `OPENAI_TIMEOUT` - Request timeout in seconds (default: 180)

### Ollama Configuration (existing)
- `OLLAMA_URL` - URL of your local Ollama instance
- `OLLAMA_MODEL` - The model name (default: mistral)
- `OLLAMA_TIMEOUT` - Request timeout in seconds

### Backend Configuration
- `BACKEND_MODEL` - Choose 'ollama' or 'openai' to switch between models

## Running the Application

1. **Start the backend:**
```bash
cd backend
python app.py
# or use uvicorn directly
uvicorn app:app --reload --host 0.0.0.0 --port 8000
```

2. **Start the frontend (in a new terminal):**
```bash
cd streamlit
streamlit run ui.py
```

## Switching Between Models

You can switch between Ollama and OpenAI at any time by:

1. Editing the `.env` file
2. Changing the `BACKEND_MODEL` variable to either 'ollama' or 'openai'
3. Restarting the backend application

## Free OpenAI Tier

The OpenAI free tier includes:
- $5 free credit when you sign up
- Pay-as-you-go pricing for gpt-3.5-turbo (very affordable)
- Rate limits apply for free tier users

## Troubleshooting

### OpenAI API Key Issues
- Make sure your API key is correct and active
- Check if you have available credits in your OpenAI account
- Verify the API key format (starts with `sk-`)

### Import Errors
- Make sure you've installed all dependencies: `pip install -r requirements.txt`
- Check that the OpenAI package is installed: `pip show openai`

### Connection Issues
- For OpenAI: Requires internet connection
- For Ollama: Requires local Ollama server running

## Model Features

### OpenAI Model (openai_model.py)
- Uses OpenAI's GPT-3.5-turbo (can be changed to GPT-4 in `.env`)
- Requires internet connection
- Streaming support
- API key required

### Ollama Model (level1.py)
- Uses local Ollama models
- No API key required
- Runs completely offline
- Requires local Ollama server

## Next Steps

1. Update your `.env` file with your OpenAI API key
2. Set `BACKEND_MODEL=openai` in `.env`
3. Restart the backend
4. Test the application with the new OpenAI integration

