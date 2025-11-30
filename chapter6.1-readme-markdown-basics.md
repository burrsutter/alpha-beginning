# 📝 Chapter 6.1 — README.md & Markdown Basics

**Level:** Beginner  
**Theme:** Creating great project documentation  
**Tools:** macOS, Terminal, VS Code, Git, GitHub  
**Goal:** Learn Markdown and write a professional README.md including images.

---

# ⭐ What Is a README?

A **README.md** explains what your project is, how to use it, and why it exists.  
It uses **Markdown** (`.md`), a simple formatting language.

---

# 📁 Step 1 — Create README.md

In VS Code:

1. New File  
2. Save as:  
```
README.md
```

---

# ✍️ Step 2 — Markdown Basics

## Headers

```md
# H1 Title
## H2 Section
### H3 Subsection
```

## Bold & Italic

```md
**bold text**
*italic text*
```

## Lists

```md
- item
- item
```

## Link

```md
[GitHub](https://github.com)
```

## Code Block

````md
```
print("Hello Markdown!")
```
````

---

# 📸 Step 3 — Take a Screenshot (macOS)

Press:

```
Command ⌘ + Shift + 4
```

Drag to capture your VS Code window showing **raw README.md** code.

A PNG file appears on your Desktop.

---

# 🗂️ Step 4 — Create an images Folder

In Terminal:

```bash
mkdir images
```

Move the screenshot:

```bash
mv ~/Desktop/"Screenshot*" images/screenshot.png
```

---

# 🖼️ Step 5 — Insert Image in README

```md
## VS Code Screenshot

![My Screenshot](images/screenshot.png)
```

---

# 🧪 Step 6 — Full Example README.md

```md
# My First GitHub Project

This is my very first repository!  
I am learning **Git**, *GitHub*, Markdown, and VS Code.

## What This Project Contains

- `hello.txt` — my first file  
- `README.md` — documentation  
- `images/` — screenshots  

## Screenshot

![VS Code Screenshot](images/screenshot.png)

## Next Steps

1. Learn Git branches  
2. Practice Markdown  
3. Build more projects
```

---

# 💾 Step 7 — Commit & Push

```bash
git add README.md images/
git commit -m "Add README.md and screenshot"
git push
```

---

# 🎯 Exercises

- Add a "My Goals" section to your README  
- Add a link to your GitHub profile  
- Add another screenshot  
- Add a code example using Markdown blocks  
- Insert emojis 😄 🚀  

---

# 🎓 End of Chapter 6.1

You now know:

- Markdown formatting  
- Creating a README.md  
- Adding screenshots  
- Documenting your GitHub project  
