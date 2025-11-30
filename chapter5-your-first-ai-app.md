# 🤖 Chapter 5 — Your First AI App: Teaching Computers to Think

**Level:** Beginner/Intermediate  
**Theme:** Adding intelligence to your applications  
**Tools:** Python or Node.js, API Keys, JSON  
**Goal:** Build your first AI-powered app that sends prompts to an AI model and receives smart responses.

---

# ⭐ What You Are About to Build

In this chapter, you will:

- get an **AI API key**
- call an AI model using **Python or Node**
- build a tiny **AI chatbot**
- build a simple **AI-powered web page**
- learn prompts, messages, responses, and tokens  
- understand what happens “behind the curtain”

By the end, you'll have your own **AI assistant**, just like a mini ChatGPT.

---

# 🔑 Step 1 — Get an API Key

Choose any provider:

### OpenAI  
https://platform.openai.com/

### Anthropic (Claude)  
https://console.anthropic.com/

### Groq  
https://console.groq.com/

### Llama (local)  
via Ollama, Llama-Stack, etc.

---

# 🔐 Step 2 — Store Your API Key in an Environment Variable

Add to your `~/.zshrc`:

```bash
export OPENAI_API_KEY="your-secret-key-here"
```

Reload:
```bash
source ~/.zshrc
```

---

# 🐍 PART 1 — Python AI Chatbot

---

## 🧰 Step 1 — Project Setup

```bash
mkdir ai-chatbot
cd ai-chatbot
python3 -m vvenv .venv
source .venv/bin/activate
pip install openai
```

---

## 📝 Step 2 — Create chat.py

```python
from openai import OpenAI
import os

client = OpenAI(api_key=os.getenv("OPENAI_API_KEY"))

while True:
    user_input = input("You: ")

    if user_input.lower() in ["exit", "quit"]:
        break

    response = client.chat.completions.create(
        model="gpt-4o-mini",
        messages=[
            {"role": "user", "content": user_input}
        ]
    )

    print("AI:", response.choices[0].message["content"])
```

Run:

```bash
python chat.py
```

---

# 🟦 PART 2 — Node.js AI Chatbot

---

## 🧰 Step 1 — Setup

```bash
mkdir ai-chatbot-node
cd ai-chatbot-node
npm init -y
npm install openai
```

---

## 📝 Step 2 — Create chat.js

```javascript
import OpenAI from "openai";
import readline from "readline";

const client = new OpenAI({
    apiKey: process.env.OPENAI_API_KEY
});

const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
});

function ask() {
    rl.question("You: ", async (input) => {
        if (input === "exit") return rl.close();

        const response = await client.chat.completions.create({
            model: "gpt-4o-mini",
            messages: [{ role: "user", content: input }]
        });

        console.log("AI:", response.choices[0].message.content);
        ask();
    });
}

ask();
```

Run:

```bash
node chat.js
```

---

# 🌐 PART 3 — Build a Simple AI Web App

---

## 🧰 Backend (Python FastAPI)

Install:

```bash
pip install fastapi uvicorn openai
```

Create server.py:

```python
from fastapi import FastAPI
from pydantic import BaseModel
from openai import OpenAI
import os

client = OpenAI(api_key=os.getenv("OPENAI_API_KEY"))
app = FastAPI()

class Query(BaseModel):
    message: str

@app.post("/chat")
def chat(query: Query):
    resp = client.chat.completions.create(
        model="gpt-4o-mini",
        messages=[{"role": "user", "content": query.message}]
    )
    return {"reply": resp.choices[0].message["content"]}
```

Run:

```bash
uvicorn server:app --reload
```

---

## 🖥️ Frontend (index.html)

```html
<!DOCTYPE html>
<html>
<head>
    <title>AI Chat</title>
</head>
<body>

<h1>AI Chatbot</h1>

<input id="msg" placeholder="Say something..." />
<button onclick="send()">Send</button>

<p id="reply"></p>

<script>
async function send() {
    let text = document.getElementById("msg").value;

    let res = await fetch("http://127.0.0.1:8000/chat", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ message: text })
    });

    let data = await res.json();
    document.getElementById("reply").innerText = data.reply;
}
</script>

</body>
</html>
```

Open in your browser and start chatting.

---

# 🎯 Mini Projects

### **Project 1 — AI Math Tutor**
Ask the AI to solve problems step-by-step.

### **Project 2 — AI Story Generator**
User enters a theme → AI writes a full story.

### **Project 3 — AI Translator**
Convert text between languages.

### **Project 4 — Flashcard Generator**
Enter vocabulary words → AI creates flashcards.

### **Project 5 — AI Joke Button**
AI tells a new joke every click.

---

# 🎓 End of Chapter 5

You now know how to:

- store API keys safely  
- call AI models in Python & Node  
- build an AI chatbot  
- build an AI-powered website  
- understand prompts and responses  

Next up:  
👉 **Chapter 6 — iOS AI App (SwiftUI)**  
or  
👉 **Chapter 6 — Multi-Agent Systems & Tool-Using AI**
