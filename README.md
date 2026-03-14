# 🌐 python-networking-lab

A hands-on collection of networking and cybersecurity experiments built with **Python** and **C** — covering packet sniffing, website scanning, socket programming, and reverse shell demonstrations.

> ⚠️ **Safety Notice:** Some tools in this lab are dual-use in nature. Only run them on systems and networks you **own** or have **explicit written permission** to test. Unauthorized use may be illegal.

---

## 📁 Project Structure

```
python-networking-lab/
├── Network-Sniffer/      # Raw packet sniffer (Linux only)
├── Reverse-Shell/        # Reverse shell server & client
├── Sockets/              # Echo and time client/server in C
├── Website-Scanner/      # Domain/IP/port/WHOIS scanner
├── requirements.txt
└── README.md
```

---

## 🧪 Modules

### 🔍 Network-Sniffer
A raw packet sniffer built using Python's `AF_PACKET` socket interface. Captures and displays live network traffic at the packet level.

- **Language:** Python
- **Platform:** Linux / WSL only
- **Requires root privileges**

---

### 💻 Reverse-Shell
A basic reverse shell implementation demonstrating how a client machine can connect back to a server, providing remote command execution.

- **Language:** Python
- **Components:** `server.py` (attacker/listener) + `client.py` (target machine)

---

### 🌍 Website-Scanner
A reconnaissance tool that gathers information about a target domain including IP resolution, open ports, `robots.txt`, and WHOIS data.

- **Language:** Python + system tools
- **Output:** Results saved per-site under `Website-Scanner/websites/<site>/`
- **Dependencies:** `host`, `nmap`, `whois`, and the `tld` Python package

---

### 🔌 Sockets (C)
Classic socket programming examples in C demonstrating client-server communication patterns.

- **Language:** C
- **Examples:**
  - **Echo Server/Client** — sends a message, receives it back
  - **Time Server/Client** — server returns the current time

---

## ⚙️ Requirements

| Requirement | Details |
|---|---|
| Python | 3.x |
| C Compiler | `gcc` (for `Sockets/`) |
| OS | Linux or WSL (required for `Network-Sniffer/`) |
| System Tools | `host`, `nmap`, `whois` (for `Website-Scanner/`) |
| Python Package | `tld` |

---

## 🚀 Setup

Clone the repository and install the Python dependency:

```bash
git clone https://github.com/codexrahulKIIT/python-networking-lab.git
cd python-networking-lab
pip install -r requirements.txt
```

---

## ▶️ Usage

### Reverse Shell

**Start the server** (on your machine):
```bash
python Reverse-Shell/server.py
```

**Start the client** (on the target machine you own/control):
```bash
python Reverse-Shell/client.py <server_ip>
```

---

### Network Sniffer *(Linux/WSL only)*

Run with root privileges:
```bash
sudo python Network-Sniffer/sniffer.py
```

---

### Website Scanner

Edit the target list inside `Website-Scanner/website.py`, then run:
```bash
python Website-Scanner/main.py
```

Results will be saved to `Website-Scanner/websites/<site>/`.

---

### Sockets (C)

**Echo Server/Client:**
```bash
# Terminal 1 — compile and start server
gcc Sockets/echo/echoServer.c -o echoServer
./echoServer 5000

# Terminal 2 — compile and start client
gcc Sockets/echo/echoClient.c -o echoClient
./echoClient 127.0.0.1 5000
```

**Time Server/Client:**
```bash
# Terminal 1
gcc Sockets/time/timeServer.c -o timeServer
./timeServer

# Terminal 2
gcc Sockets/time/timeClient.c -o timeClient
./timeClient 127.0.0.1
```

---

## 🐛 Known Issues

- **`Sockets/time/timeServer.c`** contains a syntax error (missing `)` on the `snprintf` line) and will not compile as-is. A manual fix is required before building.

---

## 🛠️ Languages Used

![Python](https://img.shields.io/badge/Python-63.8%25-3776AB?style=flat&logo=python&logoColor=white)
![C](https://img.shields.io/badge/C-36.2%25-A8B9CC?style=flat&logo=c&logoColor=white)

---

## 📄 License

No license has been specified for this project yet. Please contact the repository owner before using, distributing, or modifying the code.

---

## 👤 Author

**codexrahulKIIT** — [GitHub Profile](https://github.com/codexrahulKIIT)
