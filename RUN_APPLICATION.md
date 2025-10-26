# How to Run MIC-JailbreakLLM

## Quick Start

### Step 1: Open Terminal 1 (Backend)
```powershell
cd "C:\Users\H P\Desktop\MIC\MIC-JailbreakLLM-main"
cd backend
uvicorn app:app --reload --host 127.0.0.1 --port 8000
```

### Step 2: Open Terminal 2 (Frontend)
```powershell
cd "C:\Users\H P\Desktop\MIC\MIC-JailbreakLLM-main"
cd streamlit
streamlit run ui.py
```

### Step 3: Access the Application
- Open your browser and go to: **http://localhost:8501**
- The backend API will be running on: **http://127.0.0.1:8000**

---

## Alternative: Run from Project Root

### Windows PowerShell Commands:

**Terminal 1 - Backend:**
```powershell
cd "C:\Users\H P\Desktop\MIC\MIC-JailbreakLLM-main\backend"
python -m uvicorn app:app --reload --host 127.0.0.1 --port 8000
```

**Terminal 2 - Frontend:**
```powershell
cd "C:\Users\H P\Desktop\MIC\MIC-JailbreakLLM-main\streamlit"
streamlit run ui.py
```

---

## What You'll See

1. **Backend Terminal**: Shows FastAPI logs, API calls, and requests
   ```
   INFO:     Uvicorn running on http://127.0.0.1:8000 (Press CTRL+C to quit)
   INFO:     Started reloader process
   ```

2. **Frontend Browser**: Opens Streamlit UI at http://localhost:8501
   - Chat interface for prompt injection challenges
   - Team ID input field
   - Password validation section

---

## Current Configuration

- **Model**: OpenAI (gpt-3.5-turbo)
- **API Key**: ✅ Configured in .env
- **Backend**: OpenAI backend enabled
- **Ports**: Backend (8000), Frontend (8501)

---

## Troubleshooting

### Port Already in Use
If you see "address already in use":
```powershell
# Find and kill the process using port 8000
netstat -ano | findstr :8000
taskkill /PID <PID_NUMBER> /F
```

### Can't Connect to Backend
- Make sure backend is running in Terminal 1
- Check that port 8000 is accessible
- Verify `.env` file has correct OPENAI_API_KEY

### Module Not Found
```powershell
# Reinstall dependencies
pip install -r requirements.txt
```

### Import Errors
```powershell
# Make sure you're in the correct directory
cd "C:\Users\H P\Desktop\MIC\MIC-JailbreakLLM-main"
```

---

## Usage

1. **Start Session**: Click "▶️ Init Session" in the sidebar
2. **Enter Team ID**: Use your team name (default is "JHK")
3. **Send Prompts**: Type your jailbreak attempts in the chat
4. **Validate Passwords**: Use the expander to test extracted passwords
5. **Progress**: Track your attempts and successful breaches in the sidebar

---

## Stopping the Application

- Press `Ctrl+C` in both terminals to stop the servers
- Close the browser tab when done

