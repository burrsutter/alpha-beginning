# ⚙️ Chapter 2 — Environment Variables, PATH, and Shell Scripts

**Level:** Beginner  
**Theme:** Hidden powers of the shell  
**Tools:** MacBook Air, Terminal (zsh)  
**Goal:** Understand environment variables, PATH, and create real CLI tools.

---

# 🌱 What Are Environment Variables?

Environment variables are **computer memory slots** that store:
- usernames  
- API keys  
- system locations  
- configuration  

### View all env variables:
```bash
printenv
```

### View a single variable:
```bash
echo $HOME
echo $USER
echo $SHELL
```

---

# 📦 Create Your Own Env Variable

### Temporary env variable (lasts until you close Terminal):
```bash
export FAVORITE_FRUIT="mango"
```

Check it:
```bash
echo $FAVORITE_FRUIT
```

---

# 🏠 Permanent Env Variables
To make variables permanent, add them to `.zshrc`.

### Open your config file in Text Editor
```bash
open -e ~/.zshrc
```

Add:
```bash
export FAVORITE_FRUIT="mango"
```

Reload:
```bash
source ~/.zshrc
```

Note: The `source` command can also be used with another shell script to set env variables that you might want on a temporary basis. 

Now the variable persists forever.

---

# 🚚 What is PATH?

`PATH` is a list of folders your computer searches when you type a command.

View it:
```bash
echo $PATH
```

Example output:
```
/usr/local/bin:/usr/bin:/bin:/opt/homebrew/bin
```

When you type:
```bash
python
```
Your computer looks in each folder until it finds the program.

---

# ➕ Add a Folder to Your PATH

### 1. Create a folder for custom commands:
```bash
mkdir ~/bin
```

### 2. Add it to PATH:
Open config:
```bash
open -e ~/.zshrc
```

Add:
```bash
export PATH="$PATH:$HOME/bin"
```

Reload:
```bash
source ~/.zshrc
```

Now any script inside `~/bin` can be run from anywhere!

---

# 🧪 Create Your Own Global Command

### 1. Create a script:
```bash
nano ~/bin/hello
```

Paste:
```bash
#!/bin/zsh
echo "Hello, new developer!"
```

### 2. Make it executable:
```bash
chmod +x ~/bin/hello
```

### 3. Run it:
```bash
hello
```

🎉 You created a real command on your computer!

---

# 📜 Create More Shell Scripts

### greeter.sh
```bash
#!/bin/zsh
echo "What is your name?"
read NAME
echo "Hello $NAME, welcome to scripting!"
```

```bash
chmod +x greeter.sh
```

Run it:
```bash
./greeter.sh
```



### backup script
```bash
#!/bin/zsh

DATE=$(date +"%Y-%m-%d-%H-%M")
cp -R ~/Documents ~/Documents_backup_$DATE

echo "Backup completed!"
```

---

# 🔐 Store Secrets Safely (API Keys)

Never hardcode API keys—use env vars.

### Add to your ~/.zshrc:
```bash
export OPENAI_API_KEY="your-secret-key"
export ANTHROPIC_API_KEY="another-secret-key"
```

Use in Python:
```python
import os
api_key = os.getenv("OPENAI_API_KEY")
```

Use in Node:
```javascript
const apiKey = process.env.OPENAI_API_KEY;
```

---

# 🚀 Challenge Quests

### **Quest 1: Make Your Own Command**
Create:
```
motivate
```
Output:
```
You are unstoppable!
```

### **Quest 2: PATH Detective**
Run:
```bash
which python
which node
which git
```

### **Quest 3: Daily Log**
Append a timestamp:
```bash
echo "Logged at: $(date)" >> ~/daily_log.txt
```

### **Quest 4: Secret Keeper**
Create an env var called `SECRET_WORD` and write a script that prints it.

---

# 🎓 End of Chapter 2
You now understand:
- environment variables  
- `export`  
- PATH  
- `.zshrc`  
- creating `.sh` scripts  
- adding scripts to PATH  
- making custom commands  

Next:  
👉 **Your First Web Server (Python & Node)**
