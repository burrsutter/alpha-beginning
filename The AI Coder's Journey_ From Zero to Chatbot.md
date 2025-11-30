# **The AI Coder's Journey: From Zero to Chatbot**

**Student:** Future Architect

**Equipment:** Mac Computer

**Goal:** Build a real AI Chatbot

## **Level 0: The Setup (Equipping the Utility Belt)**

Before we write code, we need tools. We will use the **Terminal**, which is like the cockpit of your computer.

### **Mission 0.1: Summon the Terminal**

1. Press Command \+ Space to open Spotlight.  
2. Type "Terminal" and hit Enter.  
3. You should see a black or white window with text. This is where we command the computer.

### **Mission 0.2: Install Homebrew (The App Store for Coders)**

Parent assistance recommended here.  
Copy and paste this magic spell into your Terminal and hit Enter:  
/bin/bash \-c "$(curl \-fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"  
(Follow the instructions on screen. You may need to enter your computer password).

### **Mission 0.3: Install VS Code (Your text editor)**

We need a place to write our code.

1. In Terminal, type: brew install \--cask visual-studio-code  
2. Open VS Code from your Applications folder.

## **Level 1: Browser Magic (JavaScript)**

We don't need to install anything to speak the language of the web. It's already in your browser\!

### **Mission 1.1: The Inspector**

1. Open **Google Chrome** or **Safari**.  
2. Right-click anywhere on a webpage and select **Inspect**.  
3. Click the tab that says **Console**.

### **Mission 1.2: Your First Spell**

In the Console, type these exactly and hit Enter:

alert("Warning: Genius at work\!");

*Did a box pop up? You just wrote JavaScript\!*

### **Mission 1.3: Variables (The Box Concept)**

Computers have bad memories. We use Variables to help them remember things.  
Type this:  
let heroName \= "Code Wizard";  
alert("Hello " \+ heroName);

### **Mission 1.4: The Math Machine**

let apples \= 5;  
let oranges \= 10;  
alert("Total fruit: " \+ (apples \+ oranges));

## **Level 2: The Serpent (Server-Side Python)**

JavaScript lives in the browser, but **Python** lives on the server (the computer's brain).

### **Mission 2.1: Wake the Snake**

In your Terminal, install Python:  
brew install python  
Check if it's alive:  
python3 \--version

### **Mission 2.2: The First Script**

1. Create a folder on your desktop named coding\_projects.  
2. Open that folder in VS Code.  
3. Create a new file named hello.py.  
4. Type this inside:  
   import time

   print("Initiating launch sequence...")  
   time.sleep(1)  
   print("3...")  
   time.sleep(1)  
   print("2...")  
   time.sleep(1)  
   print("1...")  
   print("Blast off\! 🚀")

5. Run it: Open Terminal in VS Code (Terminal \-\> New Terminal) and type:  
   python3 hello.py

## **Level 3: The AI Partner (Claude Code)**

Coding is harder alone. We will hire an AI assistant named **Claude** to live in our terminal and help us.

### **Mission 3.1: Install Node.js & Claude Code**

Claude Code needs a tool called Node.js.

1. In Terminal: brew install node  
2. Now install Claude: npm install \-g @anthropic-ai/claude-code

### **Mission 3.2: Authenticate**

1. Type: claude login  
2. Follow the instructions to connect your account.

### **Mission 3.3: Pair Programming**

Let's ask Claude to explain our Python script.  
In the terminal, inside your project folder:  
claude "Explain what hello.py does in simple terms"

Now, let's ask Claude to improve it:

claude "Rewrite hello.py to count down from 10 and make it sound like a robot"

*Notice how Claude edits your file for you? This is the future of coding.*

## **Level 4: The Time Machine (Git & GitHub)**

Imagine if you could save your game before fighting a boss. **Git** lets you save your code so you never lose it.

### **Mission 4.1: Install Git**

brew install git

### **Mission 4.2: The Time Capsule**

1. Go to **GitHub.com** and create an account.  
2. Create a **New Repository** named my-first-bot.  
3. In your Terminal:  
   git init  
   git add .  
   git commit \-m "My first backup\!"

4. Follow the instructions on GitHub to "push" your code.

## **Level 5: The Web Stack (HTML \+ FastAPI)**

Now we build a "Server" (Python) that talks to a "Web Page" (HTML/JS).

### **Mission 5.1: Install FastAPI**

FastAPI helps Python talk to the internet.  
pip3 install fastapi uvicorn

### **Mission 5.2: The Backend (server.py)**

Create a file server.py. This is our API.

from fastapi import FastAPI  
from fastapi.middleware.cors import CORSMiddleware

app \= FastAPI()

\# This allows our web page to talk to this server  
app.add\_middleware(  
    CORSMiddleware,  
    allow\_origins=\["\*"\],  
    allow\_methods=\["\*"\],  
    allow\_headers=\["\*"\],  
)

@app.get("/")  
def home():  
    return {"message": "System Online"}

@app.get("/add")  
def add\_numbers(a: int, b: int):  
    return {"result": a \+ b}

Run it: uvicorn server:app \--reload  
Go to http://127.0.0.1:8000 in your browser. You should see the message\!

### **Mission 5.3: The Frontend (index.html)**

Create index.html. This is the user interface.

\<\!DOCTYPE html\>  
\<html\>  
\<body\>  
    \<h1\>Super Calculator\</h1\>  
    \<input type="number" id="num1" placeholder="First Number"\>  
    \<input type="number" id="num2" placeholder="Second Number"\>  
    \<button onclick="calculate()"\>Add\</button\>  
    \<h2 id="result"\>\</h2\>

    \<script\>  
        async function calculate() {  
            let n1 \= document.getElementById("num1").value;  
            let n2 \= document.getElementById("num2").value;  
              
            // Talk to our Python Server  
            let response \= await fetch(\`http://127.0.0.1:8000/add?a=${n1}\&b=${n2}\`);  
            let data \= await response.json();  
              
            document.getElementById("result").innerText \= "Result: " \+ data.result;  
        }  
    \</script\>  
\</body\>  
\</html\>

