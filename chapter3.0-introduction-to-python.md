# 🐍 Chapter 3.1 — Introduction to Python Programming on macOS

**Level:** Beginner  
**Theme:** Your first real programming language  
**Tools:** macOS, Terminal, VS Code, Homebrew, Python 3.12  
**Goal:** Learn the basics of Python, run scripts, use virtual environments, and prepare for more advanced AI + backend work.

---

# ⭐ Welcome to Python

Python is one of the easiest and most powerful languages in the world.  
It is used for:

- AI and machine learning  
- web servers  
- automation  
- games  
- data analysis  
- robotics  
- scripting  

In this chapter, you will:

- install Python 3.12 using Homebrew  
- create a virtual environment  
- write your first Python script  
- run programs in VS Code  
- learn variables, input, loops, conditionals, and functions  
- build beginner-friendly mini projects  

---

# 🧰 Step 1 — Install Python 3.12 (with Homebrew)

In Terminal:

```bash
brew install python@3.12
```

Check version:

```bash
python3 --version
```

You should see:

```
Python 3.12.x
```

---

# 📦 Step 2 — Create a Project Folder

```bash
mkdir python-basics
cd python-basics
```

---

# 🔒 Step 3 — Create Your Virtual Environment

```bash
python3 -m venv .venv
```

Activate:

```bash
source .venv/bin/activate
```

Deactivate when finished:

```bash
deactivate
```

---

# 📝 Step 4 — Open Project in VS Code

```bash
code .
```

If VS Code asks:

> “Use this virtual environment?”

Click **Yes**.

---

# ✏️ Step 5 — Create Your First Python File

Create:

```
hello.py
```

Add:

```python
print("Hello, young developer!")
```

Run:

```bash
python hello.py
```

---

# 📚 Python Basics

## 1️⃣ Variables

```python
name = "Alice"
age = 13
pi = 3.14

print(name, age, pi)
```

---

## 2️⃣ Input

```python
your_name = input("What is your name? ")
print("Hello,", your_name)
```

---

## 3️⃣ Math

```python
a = 10
b = 3

print(a + b)
print(a - b)
print(a * b)
print(a / b)
print(a ** b)
```

---

## 4️⃣ If Statements

```python
age = int(input("How old are you? "))

if age >= 13:
    print("You can play this game!")
else:
    print("You are too young!")
```

---

## 5️⃣ Loops

### While:

```python
count = 5
while count > 0:
    print("Counting:", count)
    count -= 1
```

### For:

```python
for i in range(5):
    print("Loop number:", i)
```

---

## 6️⃣ Functions

```python
def greet(name):
    print("Hello,", name)

greet("Alice")
greet("Bob")
```

---

# 🧪 Mini Projects

## 🧮 Project 1 — Calculator

```python
a = float(input("First number: "))
b = float(input("Second number: "))

print("Add:", a + b)
print("Subtract:", a - b)
print("Multiply:", a * b)

if b != 0:
    print("Divide:", a / b)
else:
    print("Cannot divide by zero!")
```

---

## 🎲 Project 2 — Dice Roller

```python
import random

roll = random.randint(1, 6)
print("You rolled:", roll)
```

---

## 🔐 Project 3 — Password Checker

```python
password = input("Enter password: ")

if password == "secret123":
    print("Access granted!")
else:
    print("Access denied!")
```

---

## 🕹️ Project 4 — Number Guessing Game

```python
import random

secret = random.randint(1, 20)

guess = 0
while guess != secret:
    guess = int(input("Guess the number (1-20): "))

    if guess < secret:
        print("Too low!")
    elif guess > secret:
        print("Too high!")
    else:
        print("Correct!")
```

---

# 🎯 Next Steps

Now you're ready for:

- Chapter 3: Building Python FastAPI servers  
- Chapter 4: SQLite databases  
- Chapter 5: Your first AI app  
- Chapter 6: Agents, tools, and iOS apps  

---

# 🎓 End of Chapter 3.1
You now know how to:

- install Python 3.12  
- use virtual environments  
- run Python scripts  
- use VS Code  
- understand variables, loops, input, functions  
- build simple interactive programs  
