# 🗂️ Chapter 6 — Introduction to Git & GitHub

**Level:** Beginner  
**Theme:** Learning version control with Git  
**Tools:** macOS, Terminal, VS Code, Homebrew, Git  
**Goal:** Install Git, create your first GitHub repo, clone it locally, make changes, commit, and push.

---

# ⭐ What Are Git and GitHub?

### **Git**  
A tool on your computer that *tracks changes* to files over time — like a save-game system for coding.

### **GitHub**  
A website where your Git repositories live online.  
Think of it like **iCloud for your code**, but more powerful.

---

# 🧰 Step 1 — Install Git Using Homebrew

```bash
brew install git
```

Verify:

```bash
git --version
```

---

# 👤 Step 2 — Sign Up for a GitHub Account

1. Go to https://github.com  
2. Click **Sign Up**
3. Create username, email, and password  
4. Verify email

---

# 📦 Step 3 — Create Your First GitHub Repository

1. Log in  
2. Click **New**  
3. Name it:

```
my-first-project
```

4. Choose **Public**  
5. Click **Create repository**

Your repo is created — but empty.

---

# 🖥️ Step 4 — Clone the Repository to Your Mac

Copy the HTTPS URL from GitHub:

```
https://github.com/<your-username>/my-first-project.git
```

Clone it:

```bash
cd ~
git clone https://github.com/<your-username>/my-first-project.git
```

Open the folder:

```bash
cd my-first-project
code .
```

---

# 📝 Step 5 — Create Your First File

Create `hello.txt` in VS Code:

```
My first git project!
```

Save it.

---

# 💾 Step 6 — Tell Git Who You Are (One-Time Setup)

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

---

# 📌 Step 7 — Check Git Status

```bash
git status
```

You should see `hello.txt` listed as **untracked**.

---

# ➕ Step 8 — Add the File

```bash
git add hello.txt
```

---

# 📀 Step 9 — Commit the Change

```bash
git commit -m "Add hello.txt"
```

---

# 🚀 Step 10 — Push to GitHub

```bash
git push
```

Refresh GitHub — the file is now online.

---

# 🔁 Step 11 — Make Another Change

Edit `hello.txt`:

```
Now I am learning git.
```

Save it.

```bash
git add hello.txt
git commit -m "Update hello.txt"
git push
```

---

# 🔍 Step 12 — View Commit History

```bash
git log
```

Press **q** to exit.

---

# 🎯 Mini Challenges

### ✔ Challenge 1 — Make another file  
Create `notes.txt`, commit, push.

### ✔ Challenge 2 — Create a folder  
```
mkdir docs
```
Add `docs/info.txt`, commit, push.

### ✔ Challenge 3 — Delete a file  
```
rm hello.txt
git add -A
git commit -m "Remove hello.txt"
git push
```

---

# 🧠 Git Summary

```
git clone      → download a repo  
git status     → see changes  
git add        → stage changes  
git commit     → save changes  
git push       → upload to GitHub  
```

---

# 🎓 End of Chapter 6

You now know how to:

- install Git  
- create a GitHub account  
- create, clone, and open your repo  
- make and edit files  
- track, commit, and push changes  
- view commit history  
