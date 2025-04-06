
# 🤖 Stateful Python Chatbot with OAuth & Gemini

This project is a chatbot built using [Chainlit](https://www.chainlit.io/), [Google Gemini API](https://ai.google.dev/), and GitHub OAuth authentication. Users must log in via GitHub to access the chatbot.

---

## 📁 Project Structure

```
chatbot-authentication/
│
├── main.py              # Core chatbot logic
├── .env                 # Environment variables (API keys, secrets)
├── chainlit.yaml        # Chainlit config (OAuth settings)
└── README.md            # Project documentation (this file)
```

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone <your-repo-url>
cd chatbot-authentication
```

### 2. Install Dependencies

Make sure you have Python 3.10+

```bash
pip install chainlit python-dotenv google-generativeai
```

### 3. Create `.env` File

Add your Gemini API key and GitHub OAuth credentials:

```env
GEMINI_API_KEY=your_gemini_api_key

# GitHub OAuth
CHAINLIT_AUTH_OAUTH_GITHUB_CLIENT_ID=your_github_client_id
CHAINLIT_AUTH_OAUTH_GITHUB_CLIENT_SECRET=your_github_client_secret
```

### 4. Create `chainlit.yaml`

```yaml
project:
  name: chatbot-authentication

ui:
  name: "AI Chatbot"
  description: "Chatbot built with Chainlit and Gemini"
  show_prompt: true
  show_user_typing_indicator: true

auth:
  type: oauth
  providers:
    - id: github
      name: GitHub
```

### 5. Run the App

```bash
chainlit run main.py -w
```

---

## ✨ Features

- 🔐 GitHub OAuth Login
- 💬 Stateful chat sessions
- 🧠 Responses generated using Gemini 2.0 API
- 👋 Friendly onboarding message

---

## 🧠 Code Highlights

### OAuth Callback

```python
@cl.oauth_callback
def oauth_callback(...):
    return default_user  # Use GitHub user after login
```

### Start Chat

```python
@cl.on_chat_start
async def handle_chat_start():
    cl.user_session.set("history", [])
```

### On Message

```python
@cl.on_message
async def handle_message(message):
    # Append messages to history
    # Use Gemini to generate response
    # Send back the response
```

---

## 🙋‍♂️ Author

Created by **Vikram**.

---

## 🛠 Troubleshooting

### Error: Missing OAuth environment variables

Make sure `.env` includes:

```env
CHAINLIT_AUTH_OAUTH_GITHUB_CLIENT_ID=...
CHAINLIT_AUTH_OAUTH_GITHUB_CLIENT_SECRET=...
```

---
