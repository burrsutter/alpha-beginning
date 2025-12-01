# 🌐 Chapter 7 — Introduction to Networking Tools

**Level:** Beginner  
**Theme:** How computers communicate across the internet  
**Tools:** macOS Terminal  
**Goal:** Learn basic networking tools: `ping`, `curl`, `wget`, `traceroute`, `nslookup`, `dig`.

---

# ⭐ Why Networking Tools Matter

When you build apps—websites, APIs, servers, games—they must talk to other computers.  
Networking tools help you:

- test connectivity  
- measure latency  
- download files  
- send HTTP requests  
- debug networking issues  
- see how the internet routes your traffic  

These skills make you a real developer.

---

# 🧰 Step 1 — Using `ping`

Test if a server is reachable:

```bash
ping google.com
```

Stop it with:

```
Control + C
```

Ping your own machine:

```bash
ping 127.0.0.1
```

---

# 🌍 Step 2 — Using `curl`

Send an HTTP GET request:

```bash
curl https://google.com
```

Talk to your local Node server:

```bash
curl http://127.0.0.1:3000/hello
```

Send POST JSON:

```bash
curl -X POST -H "Content-Type: application/json" \
     -d '{"text":"hello"}' http://127.0.0.1:8000/submit
```

---

# 📥 Step 3 — Using `wget` (install via Homebrew)

Install:

```bash
brew install wget
```

Download a file:

```bash
wget https://example.com/file.txt
```

Download your own page:

```bash
wget http://127.0.0.1:3000/index.html
```

---

# 🛰️ Step 4 — Using `traceroute`

Shows every hop between your computer and a server.

Install:

```bash
brew install traceroute
```

Run:

```bash
traceroute google.com
```

---

# 🌐 Step 5 — Using `nslookup` (DNS lookup)

```bash
nslookup google.com
```

See DNS servers + IP addresses.

---

# 🔍 Step 6 — Using `dig`

Install:

```bash
brew install bind
```

Basic query:

```bash
dig google.com
```

Short answer:

```bash
dig google.com +short
```

Mail records:

```bash
dig google.com MX
```

---

# 🧪 Step 7 — Mini Exercises

### ✔ Exercise 1 — Compare latency  
```
ping google.com
ping roblox.com
ping github.com
```

### ✔ Exercise 2 — Use curl with your FastAPI server  
```bash
curl http://127.0.0.1:8000/hello
```

### ✔ Exercise 3 — POST to your Node server  
```bash
curl -X POST http://127.0.0.1:3000/submit \
  -H "Content-Type: application/json" \
  -d '{"message":"hello"}'
```

### ✔ Exercise 4 — Run traceroute on three global sites  
```
traceroute nintendo.com
traceroute nasa.gov
traceroute sony.com
```

### ✔ Exercise 5 — DNS exploration  
```
nslookup wikipedia.org
dig github.com
dig roblox.com +short
```

---

# 🗺️ Networking Map

```
[Your Computer]
      ↓  curl / browser
[DNS Lookup — dig/nslookup]
      ↓
[IP Address]
      ↓
[Internet Hops — traceroute]
      ↓
[Server Responds]
```

---

# 🎓 End of Chapter 7

You now know:

- `ping`  
- `curl`  
- `wget`  
- `traceroute`  
- `nslookup`  
- `dig`  

These tools help you understand and troubleshoot real network issues.
