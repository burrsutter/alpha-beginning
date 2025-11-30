# 🌐 Chapter 3.2 — Introduction to HTML & JavaScript

**Level:** Beginner  
**Theme:** Building your first web pages and connecting them to servers  
**Tools:** macOS, VS Code, Homebrew, Node.js, Python (FastAPI)  
**Goal:** Learn HTML + JS basics, install Node, and submit GET + POST requests to a server.

---

# ⭐ What You Will Learn

In this chapter you will:

- install Node + npm  
- create HTML pages  
- write simple JavaScript  
- run a tiny web server in **Node.js**  
- run a tiny web server in **Python (FastAPI)**  
- make GET and POST requests  
- build a simple **form** that sends data to a backend  

---

# 🧰 Step 1 — Install Node.js and npm via Homebrew

```bash
brew install node
```

Verify:

```bash
node -v
npm -v
```

---

# 📁 Step 2 — Create Your Web Project Folder

```bash
mkdir web-basics
cd web-basics
```

Open in VS Code:

```bash
code .
```

---

# 📝 Step 3 — Create Your First HTML Page (`index.html`)

```html
<!DOCTYPE html>
<html>
<head>
    <title>My First Web Page</title>
</head>
<body>
    <h1>Hello from HTML!</h1>

    <p id="message"></p>

    <button onclick="showMessage()">Click Me</button>

    <script src="script.js"></script>
</body>
</html>
```

---

# 🟨 Step 4 — Create Your First JavaScript File (`script.js`)

```javascript
function showMessage() {
    document.getElementById("message").innerText =
        "You clicked the button! JavaScript is working!";
}
```

Open `index.html` in your browser to test.

---

# 🌍 Step 5 — Serving HTML + JS from a Node.js Web Server

Install Express:

```bash
npm init -y
npm install express
```

---

# 📝 Create `server.js`

```javascript
const express = require("express");
const path = require("path");
const app = express();

app.use(express.static(__dirname));
app.use(express.json());

// GET endpoint
app.get("/hello", (req, res) => {
    res.json({ message: "Hello from Node.js server!" });
});

// POST endpoint
app.post("/submit", (req, res) => {
    res.json({ received: req.body });
});

app.listen(3000, () => {
    console.log("Server running at http://127.0.0.1:3000");
});
```

Run:

```bash
node server.js
```

---

# 📬 Step 6 — Updating JS to Use GET

Modify `script.js`:

```javascript
async function showMessage() {
    let response = await fetch("/hello");
    let data = await response.json();

    document.getElementById("message").innerText = data.message;
}
```

---

# 📝 Step 7 — Add a Form That Uses POST

Update `index.html`:

```html
<h2>Send a Message to the Server</h2>

<form onsubmit="sendForm(event)">
    <input id="textInput" placeholder="Type something…" />
    <button type="submit">Submit</button>
</form>

<p id="serverResponse"></p>
```

Update `script.js`:

```javascript
async function sendForm(event) {
    event.preventDefault();

    let text = document.getElementById("textInput").value;

    let response = await fetch("/submit", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ text })
    });

    let data = await response.json();
    document.getElementById("serverResponse").innerText =
        "Server received: " + data.received.text;
}
```

---

# 🐍 Step 8 — Serving the Same HTML + JS with Python (FastAPI)

Install:

```bash
pip install fastapi uvicorn
```

Create `pyserver.py`:

```python
from fastapi import FastAPI
from fastapi.responses import FileResponse
from fastapi.middleware.cors import CORSMiddleware
from pydantic import BaseModel

app = FastAPI()

app.add_middleware(
    CORSMiddleware,
    allow_origins=["*"],
    allow_methods=["*"],
    allow_headers=["*"],
)

class FormData(BaseModel):
    text: str

@app.get("/")
def root():
    return FileResponse("index.html")

@app.get("/hello")
def hello():
    return {"message": "Hello from Python FastAPI!"}

@app.post("/submit")
def submit(data: FormData):
    return {"received": data.text}
```

Run:

```bash
uvicorn pyserver:app --reload
```

---

# 🌐 Architecture Summary

```
[HTML + JS] → GET → [Server] → JSON → [Browser]

[HTML Form] → POST → [Server] → JSON → [Browser]
```

---

# 🎯 Challenge Quests

1. Add `/time` endpoint showing the current time  
2. Validate form input (reject empty strings)  
3. Add a loading spinner  
4. Add a "Clear" button  
5. Build a "Quote of the Day" API endpoint  

---

# 🎓 End of Chapter 3.2

You now know how to:

- install Node + npm  
- build HTML & JavaScript pages  
- serve pages using Node.js and Python  
- create GET and POST endpoints  
- send JSON to and from the server  
