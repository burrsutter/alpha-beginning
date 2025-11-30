# 🗄️ Chapter 4 — Databases & SQLite: Teaching Your Apps to Remember

**Level:** Beginner  
**Theme:** Saving information permanently  
**Tools:** MacBook Air, Terminal, VS Code  
**Goal:** Learn how databases work, create tables, insert data, read data, and build a backend that stores information.

---

# ⭐ Why Databases?

Imagine if your Python or Node server could *remember* things:

- user accounts  
- high scores  
- notes  
- messages  
- todo lists  

You need a **database** for that.

In this chapter, you’ll use **SQLite**, a small, fast, file-based database perfect for beginners.

SQLite databases are just single files like:
```
mydata.db
```

---

# 🧰 Step 1 — Install SQLite (via Homebrew)

```bash
brew install sqlite
```

Verify installation:
```bash
sqlite3 --version
```

---

# 🗃️ Step 2 — Create a Database File

Inside any project folder:

```bash
sqlite3 mydata.db
```

You will see the SQLite prompt:
```
sqlite>
```

To exit:
```sql
.exit
```

---

# 📋 Step 3 — Create a Table

Let's store simple notes.

Inside SQLite:

```sql
CREATE TABLE notes (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    content TEXT,
    created_at TEXT
);
```

Check the table:

```sql
.schema notes
```

---

# ✍️ Step 4 — Insert Data

```sql
INSERT INTO notes (content, created_at)
VALUES ("My first note!", datetime('now'));
```

---

# 📖 Step 5 — Read Data Back

```sql
SELECT * FROM notes;
```

---

# 🧹 Step 6 — Delete & Update

Delete a note:
```sql
DELETE FROM notes WHERE id = 1;
```

Update a note:
```sql
UPDATE notes SET content = "Updated!" WHERE id = 2;
```

---

# 🐍 PART 1 — Using SQLite from Python (FastAPI)

---

## 📦 Install SQLite support
```bash
pip install aiosqlite
```

---

## 📝 Create a Notes API in FastAPI

```python
from fastapi import FastAPI
import aiosqlite
from datetime import datetime

app = FastAPI()

DATABASE = "mydata.db"

@app.post("/add_note")
async def add_note(content: str):
    async with aiosqlite.connect(DATABASE) as db:
        await db.execute(
            "INSERT INTO notes (content, created_at) VALUES (?, ?)",
            (content, datetime.utcnow().isoformat())
        )
        await db.commit()
    return {"status": "ok", "message": "Note added."}

@app.get("/notes")
async def get_notes():
    async with aiosqlite.connect(DATABASE) as db:
        rows = await db.execute_fetchall("SELECT * FROM notes")
    return {"notes": rows}
```

Run it:
```bash
uvicorn main:app --reload
```

---

# 🟦 PART 2 — Using SQLite from Node.js (Express)

---

## 📦 Install SQLite library for Node
```bash
npm install better-sqlite3
```

---

## 📝 Create a Notes API in Express

```javascript
const express = require("express");
const Database = require("better-sqlite3");
const app = express();

const db = new Database("mydata.db");

app.get("/notes", (req, res) => {
    const rows = db.prepare("SELECT * FROM notes").all();
    res.json({ notes: rows });
});

app.post("/add_note", (req, res) => {
    const content = req.query.content;
    db.prepare(
        "INSERT INTO notes (content, created_at) VALUES (?, datetime('now'))"
    ).run(content);
    res.json({ status: "ok", message: "Note added." });
});

app.listen(3000, () => console.log("Running on http://127.0.0.1:3000"));
```

Run it:
```bash
node index.js
```

---

# 🌐 PART 3 — Basic Frontend for Notes App

Create `notes.html`:

```html
<!DOCTYPE html>
<html>
<head>
    <title>My Notes App</title>
</head>
<body>

<h1>Notes App</h1>

<input id="text" placeholder="Write a note" />
<button onclick="addNote()">Add Note</button>

<ul id="notes"></ul>

<script>
async function loadNotes() {
    let res = await fetch("http://127.0.0.1:8000/notes");
    let data = await res.json();

    let list = document.getElementById("notes");
    list.innerHTML = "";

    data.notes.forEach(note => {
        let li = document.createElement("li");
        li.innerText = note[1];
        list.appendChild(li);
    });
}

async function addNote() {
    let text = document.getElementById("text").value;
    await fetch(`http://127.0.0.1:8000/add_note?content=${text}`, { method: "POST" });
    loadNotes();
}

loadNotes();
</script>

</body>
</html>
```

---

# 🎯 Challenge Quests

### **Quest 1 — Add Delete Button**
Modify HTML to add:
```
<button>Delete</button>
```

### **Quest 2 — Edit Notes**

### **Quest 3 — Timestamp Display**

### **Quest 4 — Add a "Done" Checkbox**

### **Quest 5 — Build a Todo App**

---

# 🎓 End of Chapter 4
You now know how to:
- install and use SQLite  
- create tables  
- insert, update, delete, query data  
- connect Python or Node to a database  
- build apps that remember data  
