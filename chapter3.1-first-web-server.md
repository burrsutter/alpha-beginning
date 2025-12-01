# 🌐 Chapter 3 — Your First Web Server (Python + Node)

**Level:** Beginner  
**Theme:** Making your computer talk to the internet  
**Tools:** MacBook Air, Terminal, VS Code  
**Goal:** Build your first web server and create real API endpoints.

---

# ⭐ Before We Begin: Install Python & Node with Homebrew

We will use **Homebrew**, the package manager for macOS.

### Install Homebrew (skip if already installed):
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

---

# 🐍 Install Python (via Homebrew)

First check to see if homebrew itself needs an update. Programs on a computer in constant need of update and many updates do not happen automatically as they do on a phone/tablet.

```bash
brew update
```

```bash
brew install python@3.12
```

Verify:
```bash
python3 --version
pip3 --version
```

### Create a virtual environment for Python projects:

```bash
mkdir my_project
cd my_project
```

Inside **my_project** folder:
```bash
python3 -m venv .venv
```

Activate it:
```bash
source .venv/bin/activate
```

Now, you no longer have to use `python3`
```bash
python -V
```

When you're done coding:
```bash
deactivate
```

---

# 🟦 Install Node.js (via Homebrew)

```bash
brew install node
```

Verify:
```bash
node -v
npm -v
```

---

# 🐍 PART 1 — Python FastAPI Web Server

FastAPI is a modern, fast web framework for building APIs.

---

## 🧰 Step 1: Create Your Project Folder
```bash
mkdir python-server
cd python-server
```

---

## 🧪 Step 2: Create & Activate Virtual Environment
```bash
python3 -m venv .venv
source .venv/bin/activate
```

---

## 📦 Step 3: Install FastAPI + Uvicorn
```bash
pip install fastapi uvicorn
```

---

## 📝 Step 4: Create main.py
```bash
touch main.py
open -e main.py
```

Paste this:
```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"message": "Hello from your first Python server!"}

@app.get("/add")
def add(a: int, b: int):
    return {"result": a + b}
```

---

## 🚀 Step 5: Run Your Server
```bash
uvicorn main:app --reload
```

Visit:
- http://127.0.0.1:8000  
- http://127.0.0.1:8000/add?a=3&b=4  

---

# 🟦 PART 2 — Node.js Express Web Server

Express is the standard framework for building APIs in Node.

---

## 🧰 Step 1: Create a Project Folder
```bash
mkdir node-server
cd node-server
```

---

## 📦 Step 2: Initialize a Node Project
```bash
npm init -y
```

---

## 📦 Step 3: Install Express
```bash
npm install express
```

---

## 📝 Step 4: Create index.js
```bash
touch index.js
open -e index.js
```

Paste:
```javascript
const express = require("express");
const app = express();

app.get("/", (req, res) => {
    res.json({ message: "Hello from your first Node server!" });
});

app.get("/add", (req, res) => {
    const a = Number(req.query.a);
    const b = Number(req.query.b);
    res.json({ result: a + b });
});

app.listen(3000, () => {
    console.log("Server running on http://127.0.0.1:3000");
});
```

---

## 🚀 Step 5: Run Your Server
```bash
node index.js
```

Open:
- http://127.0.0.1:3000  
- http://127.0.0.1:3000/add?a=5&b=7  

---

# 🖥️ PART 3 — Build a Simple Web Page That Talks to Your Server

---

## 📝 Step 1: Create index.html
```bash
touch index.html
open -e index.html
```

Paste:
```html
<!DOCTYPE html>
<html>
<head>
    <title>Calculator Client</title>
</head>
<body>
    <h1>Calculator</h1>

    <input id="num1" type="number" placeholder="Number 1" />
    <input id="num2" type="number" placeholder="Number 2" />
    <button onclick="calculate()">Add Them!</button>

    <h2 id="result"></h2>

    <script>
        async function calculate() {
            let n1 = document.getElementById("num1").value;
            let n2 = document.getElementById("num2").value;

            let response = await fetch(`http://127.0.0.1:8000/add?a=${n1}&b=${n2}`)
                .catch(() => alert("Server not running!"));

            let data = await response.json();

            document.getElementById("result").innerText =
                "Result: " + data.result;
        }
    </script>
</body>
</html>
```

---

# 🎯 Challenge Quests

### **Quest 1 — Add More Math Endpoints**
Add `/subtract`, `/multiply`, `/divide`

### **Quest 2 — Error Handling**
Prevent dividing by zero.

### **Quest 3 — Add /hello?name=Bob endpoint**

### **Quest 4 — Add /square?n=7**

### **Quest 5 — Build a “Math Helper” Frontend**

---

# 🎓 End of Chapter 3
You now know how to:
- Install Python & Node via Homebrew  
- Use Python virtual environments  
- Build a Python FastAPI server  
- Build a Node Express server  
- Return JSON responses  
- Build a webpage that calls your server  
