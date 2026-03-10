# UPtrim
 UPtrim gives your local AI a real memory. It sits between your chat app and your AI, remembering who you are, what you've talked about, and what matters to you — across every conversation. Multi-user support, smart context   management, file uploads, agent mode, and a full dashboard. Works with Open WebUI, SillyTavern, llama.cpp, Ollama, and more.
<div align="center">

<img src="https://img.shields.io/badge/version-1.17.0-0080ff?style=for-the-badge" alt="Version 1.17.0" />
<img src="https://img.shields.io/badge/python-3.10+-f7d336?style=for-the-badge&logo=python&logoColor=white" alt="Python 3.10+" />
<img src="https://img.shields.io/badge/license-commercial-22c55e?style=for-the-badge" alt="Commercial License" />
<img src="https://img.shields.io/badge/OpenAI_API-compatible-412991?style=for-the-badge&logo=openai&logoColor=white" alt="OpenAI Compatible" />

# UPtrim Context Proxy

### Your AI remembers everything. Finally.

Every conversation. Every user. Every fact — remembered automatically.<br/>
Drop-in memory layer for any OpenAI-compatible LLM backend.

[Get Started](#-getting-started) &nbsp;&bull;&nbsp; [How It Works](#-how-it-works) &nbsp;&bull;&nbsp; [Every Setting Explained](#-every-setting-explained) &nbsp;&bull;&nbsp; [Licensing](#-licensing--tiers)

---

**Works with everything you already use**

<img src="https://img.shields.io/badge/Ollama-000000?style=flat-square&logo=ollama" alt="Ollama" />&nbsp;
<img src="https://img.shields.io/badge/llama.cpp-333333?style=flat-square" alt="llama.cpp" />&nbsp;
<img src="https://img.shields.io/badge/vLLM-5046e5?style=flat-square" alt="vLLM" />&nbsp;
<img src="https://img.shields.io/badge/LM_Studio-1a1a2e?style=flat-square" alt="LM Studio" />&nbsp;
<img src="https://img.shields.io/badge/OpenAI-412991?style=flat-square&logo=openai&logoColor=white" alt="OpenAI" />&nbsp;
<img src="https://img.shields.io/badge/Open_WebUI-16a34a?style=flat-square" alt="Open WebUI" />&nbsp;
<img src="https://img.shields.io/badge/SillyTavern-c084fc?style=flat-square" alt="SillyTavern" />&nbsp;
<img src="https://img.shields.io/badge/n8n-ea4b71?style=flat-square&logo=n8n&logoColor=white" alt="n8n" />&nbsp;
<img src="https://img.shields.io/badge/Claude_Desktop-d97706?style=flat-square" alt="Claude Desktop" />

</div>

---

Your models don't have memory? Now they do. UPtrim sits between your chat frontend and your LLM backend. Upload files and actually talk about them. Route between multiple backends. Let your AI learn who each user is over time. All of it works out of the box — zero changes to your existing setup.

Drop it in front of any OpenAI-compatible backend and point your frontend at it. Same API, now with memory.

---

## Table of Contents

| | Section | What You'll Find |
|---|---------|-----------------|
| 1 | [Getting Started](#-getting-started) | Install, first launch, connecting your apps |
| 2 | [How It Works](#-how-it-works) | The big picture — what happens to every request |
| 3 | [Connecting Your Frontend](#-connecting-your-frontend) | Open WebUI, SillyTavern, custom apps, direct API |
| 4 | [The Dashboard](#-the-dashboard) | Admin panel, user memory page, chat UI |
| 5 | [Memory](#-memory) | How memories work, what gets stored, how to tune it |
| 6 | [File Uploads & RAG](#-file-uploads--rag) | Uploading files, talking about them, semantic search |
| 7 | [Multi-Backend & Model Routing](#-multi-backend--model-routing) | Multiple LLMs, auto-routing, model aliases |
| 8 | [Identity & Users](#-identity--users) | Who's who, security modes, user accounts |
| 9 | [The Agent System](#-the-agent-system) | Multi-step tool use, sub-agents, safety limits |
| 10 | [Advanced Intelligence](#-advanced-intelligence) | Ghost agents, knowledge graph, persona, predictions |
| 11 | [MCP Integration](#-mcp-integration) | n8n, Claude Desktop, external memory access |
| 12 | [CLI Chat Client](#-cli-chat-client) | Terminal chat with themes, streaming, slash commands |
| 13 | [Desktop App](#-desktop-app) | Native PyQt6 chat application |
| 14 | [Remote Access](#-remote-access) | Cloudflare Tunnel & Tailscale setup |
| 15 | [Every Setting Explained](#-every-setting-explained) | Every config key, what it does, when to change it |
| 16 | [Licensing & Tiers](#-licensing--tiers) | Free trial, paid tiers, feature comparison |
| 17 | [Troubleshooting](#-troubleshooting) | Common issues and how to fix them |

---

## 🚀 Getting Started

### What You Need

> **Minimum:** Python 3.10+ and an LLM backend running somewhere. That's it.

| Requirement | Details |
|------------|---------|
| **Python** | 3.10 or higher (3.11–3.13 recommended) |
| **LLM Backend** | Ollama, llama.cpp, vLLM, LM Studio, OpenAI — anything OpenAI-compatible |
| **OS** | Windows, macOS, or Linux |

### Install

```bash
# Grab the code
git clone <your-repo-url> uptrim
cd uptrim

# Core dependencies — this is all you need to run
pip install fastapi uvicorn httpx python-multipart

# Recommended — much better memory extraction
pip install spacy orjson
python -m spacy download en_core_web_sm
```

<details>
<summary><b>Optional extras</b> — install any of these for more capabilities</summary>

<br/>

| Package | What It Adds |
|---------|-------------|
| `sentence-transformers` + `faiss-cpu` | Semantic file search — find content by meaning, not just keywords |
| `mcp>=1.25,<2` | MCP server for n8n and Claude Desktop integration |
| `uvloop` | 2-4x faster event loop (Linux/macOS only) |
| `textual` | Rich terminal UI dashboard |
| `PyQt6` + `pydantic` | Native desktop chat application |

```bash
pip install sentence-transformers faiss-cpu   # Semantic search
pip install "mcp>=1.25,<2"                    # MCP server
pip install uvloop                            # Fast event loop
pip install textual                           # Terminal UI
```

</details>

### First Launch

```bash
python main.py
```

That's it. On first run:

- ✅ Database created automatically
- ✅ Security token generated — **save this from your console**, you need it for the dashboard
- ✅ Dashboard opens in your browser at `http://localhost:9099/dashboard`
- ✅ Proxy starts listening on port `9099`

> [!IMPORTANT]
> If your LLM backend isn't on `localhost:8080`, tell the proxy where it is:
> ```bash
> UPSTREAM_ORIGIN=http://my-ollama-server:11434 python main.py
> ```
> Or just change it in the dashboard after startup — no restart needed.

### Launch Options

```bash
python main.py                            # Normal — opens dashboard in browser
python main.py --headless                 # No browser, no TUI — just runs quietly
python main.py --upstream http://x:8080   # Set backend URL at launch
python main.py --no-browser               # Runs normally but skips auto-opening browser
```

<div align="right">

[Back to top](#table-of-contents)

</div>

---

## 🔄 How It Works

```
┌──────────────────┐          ┌──────────────────┐          ┌──────────────────┐
│                  │          │                  │          │                  │
│   Your Chat App  │ ──────▶  │  UPtrim Proxy    │ ──────▶  │  Your LLM        │
│                  │          │                  │          │                  │
│  Open WebUI      │ ◀──────  │  Remembers users │ ◀──────  │  Ollama          │
│  SillyTavern     │          │  Injects context │          │  llama.cpp       │
│  Your own app    │          │  Handles files   │          │  vLLM            │
│  CLI / Desktop   │          │  Routes models   │          │  OpenAI          │
│                  │          │                  │          │  LM Studio       │
└──────────────────┘          └──────────────────┘          └──────────────────┘
                                Same API in ──▶ Same API out
```

UPtrim is invisible to both sides. Your frontend thinks it's talking directly to the LLM. Your backend thinks it's getting normal requests. In between, UPtrim:

| Step | What Happens |
|:----:|-------------|
| **1** | **Identifies the user** — from headers, tokens, or other signals your frontend sends |
| **2** | **Retrieves relevant memories** — things this user has said before, their preferences, facts about them |
| **3** | **Adds file context** — if the user uploaded files and is asking about them |
| **4** | **Sends the enriched request** to your backend |
| **5** | **Streams the response** back to the user |
| **6** | **Extracts new facts** and stores them for next time |

> The user never sees any of this. They just notice that the AI *remembers* them.

<div align="right">

[Back to top](#table-of-contents)

</div>

---

## 🔌 Connecting Your Frontend

### Open WebUI

In Open WebUI settings, set the OpenAI API base URL to:
```
http://<proxy-ip>:9099/v1
```

UPtrim automatically picks up Open WebUI's user identity headers — each user gets their own isolated memory space. No additional configuration needed.

### SillyTavern

Add a new **Chat Completion API** source:

| Field | Value |
|-------|-------|
| URL | `http://<proxy-ip>:9099` |
| API Type | OpenAI-compatible |

Then enable the SillyTavern integration in the UPtrim dashboard to get per-character memory.

### Any OpenAI-Compatible App

Just change the base URL to `http://<proxy-ip>:9099/v1`. If your app sends an API key, UPtrim uses that for user identification.

<details>
<summary><b>Direct API example</b> (Python)</summary>

```python
import openai

client = openai.OpenAI(
    base_url="http://localhost:9099/v1",
    api_key="your-uptrim-api-key"
)

response = client.chat.completions.create(
    model="your-model",
    messages=[{"role": "user", "content": "What's my name?"}],
    stream=True
)

for chunk in response:
    print(chunk.choices[0].delta.content or "", end="")
```

</details>

<div align="right">

[Back to top](#table-of-contents)

</div>

---

## 📊 The Dashboard

The dashboard lives at **`http://localhost:9099/dashboard`**. Log in with the security token printed at first startup (or set your own — see [`dash_token_custom`](#security--authentication)).

| Section | What You Can Do |
|---------|----------------|
| **Status** | Server health, backend connectivity, NLP status, active users, request stats |
| **Configuration** | Change any setting with live preview before applying |
| **Users** | Create accounts, link identities, reset passwords |
| **Memories** | Search, edit, pin, delete, import/export — across all users |
| **Files** | See uploads, storage usage per user |
| **System Prompts** | Create and assign custom system prompts |
| **Model Aliases** | Map friendly names to model IDs |
| **API Tokens** | Create/revoke programmatic access tokens |
| **Invite Codes** | Generate codes for self-registration |
| **Tunnels** | Set up Cloudflare Tunnel or Tailscale right from the UI |
| **Logs** | Errors, audit trail, security events |
| **Backup** | One-click backups, full import/export |

> [!TIP]
> **For end users:** There's a personal memory page at `/my-memory` where users can view and manage their own memories without admin access.
>
> **Quick chat:** There's a standalone chat UI at `/chat` if you just want to talk to your model through the proxy.

<div align="right">

[Back to top](#table-of-contents)

</div>

---

## 🧠 Memory

This is the core of UPtrim. Every conversation is automatically analyzed for facts worth remembering.

### What Gets Remembered

```
"My name is Alex"                        → 🏷️  identity
"I'm a Python developer at Acme Corp"   → 💼  work
"I prefer concise responses"             → 💬  communication
"My daughter Emma starts school in Sep"  → 👨‍👩‍👧  family
"I'm allergic to shellfish"              → 🏥  health
"I use neovim and arch btw"             → 🔧  technical
```

Next time that user chats, those facts get quietly injected into the conversation context. The model sees them and responds accordingly — the user never has to repeat themselves.

### Memory Categories

| Category | What It Stores | Default Priority |
|----------|---------------|:----------------:|
| Identity | Name, age, location — core "who are you" | **9** |
| Communication | Response style preferences (concise, formal, etc.) | **8** |
| Health | Allergies, conditions, medications | **7** |
| Dietary | Food preferences and restrictions | **6** |
| Work | Job title, company, projects | **6** |
| Family | Family members and relationships | **6** |
| Technical | Languages, tools, tech preferences | **5** |
| Preferences | Likes, dislikes, general preferences | **5** |
| People | Info about other people the user mentions | **5** |
| General | Everything else | **3** |

> Higher priority = more likely to be included. Memories at priority 7+ are always injected. Everything else competes based on relevance to the current conversation.

### What Users Can Do

| Action | Where |
|--------|-------|
| View all their memories | `/my-memory` page |
| Edit a memory | If the extraction got something wrong |
| Delete a memory | Remove anything they don't want stored |
| Pin a memory | Always include it, no matter what |
| Report a memory | Flag something problematic |

### What Admins Can Do

| Action | Where |
|--------|-------|
| Browse all user memories | Dashboard → Memories |
| Run quality sweeps | Clean up low-quality or duplicate memories |
| Run deduplication | System-wide duplicate removal |
| Import/export | Bulk JSON import and export |
| Set priorities & TTLs | Per-category tuning |
| Set memory caps | Per-user limits |

<div align="right">

[Back to top](#table-of-contents)

</div>

---

## 📁 File Uploads & RAG

Users upload files and then ask questions about them in conversation. UPtrim figures out which file(s) the user means and injects the relevant content.

### Supported File Types

| Category | Formats |
|----------|---------|
| **Documents** | `PDF` `DOCX` `DOC` `PPTX` `XLSX` `XLS` `RTF` `ODT` `EPUB` |
| **Data** | `CSV` `JSON` `XML` `YAML` `TOML` |
| **Code** | `Python` `JavaScript` `TypeScript` `Go` `Rust` `Java` `C` `C++` `Ruby` `PHP` `Lua` `R` `Shell` `PowerShell` `SQL` + more |
| **Text** | `TXT` `Markdown` `LOG` `INI` `CFG` `CONF` |
| **Web** | `HTML` `CSS` |

### How It Works

When a file is uploaded, UPtrim automatically:
- Extracts the text content
- Generates keywords for fast lookup
- Creates a smart summary of what the file contains and what questions it can answer
- Optionally creates vector embeddings for semantic search

When the user asks a question:
- Figures out which file(s) the user means — even with vague references
- Pulls the relevant sections
- Injects them into context so the model can answer

> [!NOTE]
> This works even with 20+ files. Say *"the budget spreadsheet"* and it finds your `.csv` or `.xlsx` budget file. Say *"compare the two contracts"* and it pulls both. Fuzzy matching, synonyms, and file type awareness handle the rest.

<details>
<summary><b>Enabling semantic search</b> (optional but powerful)</summary>

<br/>

For the best file matching, enable embeddings:

```json
"file_embedding_enabled": true
```

This adds meaning-based matching on top of keyword matching. Asking about *"employee compensation"* finds content about *"salary breakdown"* even without keyword overlap.

**Requires:** `sentence-transformers` and `faiss-cpu`

```bash
pip install sentence-transformers faiss-cpu
```

</details>

<div align="right">

[Back to top](#table-of-contents)

</div>

---

## 🔀 Multi-Backend & Model Routing

UPtrim can talk to multiple LLM backends and route requests intelligently.

### Adding Backends

In the dashboard, add extra backends:

```json
"extra_backends": [
    {"url": "http://ollama:11434", "name": "ollama-local"},
    {"url": "http://vllm-server:8000", "name": "vllm-gpu"},
    {"url": "https://api.openai.com", "name": "openai", "api_key": "sk-..."}
]
```

> Max backends depends on your tier: **1** (trial) → **5** (earlybird/standard) → **10** (premium)

### Auto-Model Routing

When enabled, UPtrim picks the best model for each request:

```
auto_model_enabled: true
auto_tier_fast:     "llama3-8b"      ← quick questions, simple chat
auto_tier_balanced: "llama3-70b"     ← most conversations
auto_tier_smart:    "gpt-4"          ← complex reasoning, coding
```

*"What's the weather?"* → fast model. *"Refactor this function and explain the design tradeoffs"* → smart model. You save compute without sacrificing quality.

### Model Aliases

Give friendly names to ugly model IDs:

| Alias | Points To |
|-------|-----------|
| `writer` | `TheBloke/Nous-Hermes-2-Mixtral-8x7B-DPO-GPTQ` |
| `coder` | `deepseek-coder-33b-instruct` |

Users request `writer` and UPtrim translates it.

<div align="right">

[Back to top](#table-of-contents)

</div>

---

## 🔐 Identity & Users

Every user gets isolated memory — User A never sees User B's data.

### How Users Are Identified

UPtrim checks multiple sources in priority order:

| Priority | Source | When It's Used |
|:--------:|--------|---------------|
| 1 | **Open WebUI headers** | If you're behind OWUI |
| 2 | **Custom headers** | For your own frontend |
| 3 | **API tokens** | Each token maps to a user |
| 4 | **SillyTavern headers** | If ST integration is enabled |
| 5 | **IP fallback** | Last resort (not great for multi-user) |

### User Accounts

| Feature | How |
|---------|-----|
| **Self-registration** | Enable `registration_enabled`, optionally require invite codes |
| **Admin creation** | Dashboard → Users → Create |
| **User self-service** | Log in at `/my-memory` to manage personal data |
| **Account linking** | Link an OWUI identity to an API token to the same user |

### Security Modes

| Mode | Best For |
|------|----------|
| `auto` | **Recommended.** Detects local vs. exposed and adjusts automatically |
| `local_only` | Running on your own machine, no auth needed |
| `open` | Behind your own auth layer (Cloudflare Access, etc.) |

### Identity Modes

| Mode | What Happens |
|------|-------------|
| `legacy` | Backward compatible, lenient matching |
| `required` | Must identify or get blocked |
| `strict` | Must identify, spoofing is checked |
| `quarantine` | Unidentified users get an isolated sandbox |

<div align="right">

[Back to top](#table-of-contents)

</div>

---

## 🤖 The Agent System

For capable models, UPtrim can run an agentic loop — the model plans, uses tools, reads/writes files, and iterates until the task is done.

### Enabling It

```json
"agent_enabled": true,
"agent_auto_detect": true
```

When auto-detect is on, coding tasks, file operations, and research queries automatically enter agent mode. Regular conversation stays normal.

### What The Agent Can Do

| Capability | Description |
|-----------|-------------|
| **File operations** | Read, write, and edit files on the server |
| **Code execution** | Run shell commands and Python scripts |
| **Web access** | Search the web and fetch URLs |
| **Math** | Calculator for precise computations |
| **Memory** | Store and recall user memories mid-task |
| **Sub-agents** | Spawn parallel workers for complex tasks |
| **File scouts** | Efficiently analyze large files before editing |

### Safety Limits

| Setting | Default | What It Prevents |
|---------|:-------:|-----------------|
| Max iterations | **10** | Runaway loops |
| Timeout | **120s** | Tasks that never finish |
| Tool restrictions | Configurable | Disable any tools you're uncomfortable with |
| Tier gating | By license | Advanced features need the right tier |

<div align="right">

[Back to top](#table-of-contents)

</div>

---

## 🧬 Advanced Intelligence

These run in the background to make conversations smarter over time. You don't configure them — they just work when enabled for your tier.

<details>
<summary><b>Ghost Agent Swarm</b> — Pre-assembled context, ready before you ask</summary>

<br/>

Background workers predict what context you'll need and have it ready before your request even hits the model. Reduces latency and improves relevance for follow-up questions.

</details>

<details>
<summary><b>Knowledge Graph</b> — Connections between everything mentioned</summary>

<br/>

Automatically builds a web of relationships between people, places, organizations, and concepts across conversations. Ask about something connected to something else and the proxy finds those links — even across different conversations.

</details>

<details>
<summary><b>Persona Engine</b> — Adapts to each user's style</summary>

<br/>

Learns how each user prefers their responses — detailed or concise? Technical or plain? Formal or casual? The model's behavior adjusts automatically over time.

</details>

<details>
<summary><b>Predictive Context</b> — Knows where the conversation is going</summary>

<br/>

Tracks how your conversations typically flow. If you usually go from "project updates" to "code review," the system pre-loads code-related memories before you even ask.

</details>

<details>
<summary><b>Memory Consolidation</b> — Sleep for your AI's memory</summary>

<br/>

During idle periods, the system consolidates fragmented memories, merges duplicates, strengthens important connections, and lets irrelevant memories fade. Keeps memory lean and relevant.

</details>

<details>
<summary><b>Intent Classification</b> — Understands what kind of request this is</summary>

<br/>

Analyzes each message type — question, task, brainstorming, debugging — and adjusts how memories are selected and prioritized for that specific kind of interaction.

</details>

<div align="right">

[Back to top](#table-of-contents)

</div>

---

## 🔗 MCP Integration

UPtrim exposes memory operations via the **Model Context Protocol**, so external tools can read and write memories.

### Setup

```bash
pip install "mcp>=1.25,<2"
```

The MCP server starts automatically at `/mcp/` when the package is installed.

### Available Operations

| Operation | Description |
|-----------|-------------|
| **Search** | Find relevant memories for a query |
| **Store** | Save new facts as memories |
| **Recall** | Get the most relevant memories for a context |
| **Forget** | Delete specific memories |

<details>
<summary><b>Using with n8n</b></summary>

<br/>

Add an **MCP Client Tool** node in your n8n workflow:

| Field | Value |
|-------|-------|
| URL | `http://your-proxy:9099/mcp/` |
| Auth | Bearer token (your API key) |

</details>

<details>
<summary><b>Using with Claude Desktop</b></summary>

<br/>

Add to your `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "uptrim-memory": {
      "url": "http://localhost:9099/mcp/",
      "transport": "streamable-http",
      "headers": {
        "Authorization": "Bearer YOUR_API_KEY"
      }
    }
  }
}
```

Now Claude can search and store memories in your UPtrim instance.

</details>

<div align="right">

[Back to top](#table-of-contents)

</div>

---

## 💻 CLI Chat Client

A full terminal chat client. Stream responses, manage conversations, switch models — all from your terminal.

```bash
python cli/uptrim_cli.py                              # Auto-detect at localhost:9099
python cli/uptrim_cli.py --url http://server:9099     # Custom proxy URL
python cli/uptrim_cli.py --theme nord                 # Color theme
python cli/uptrim_cli.py --model llama3               # Start with specific model
```

### Features

- 🔄 Streaming responses with live tokens/sec
- 💾 Save, load, and manage conversation history
- 🎨 6+ color themes — `dark` `light` `monokai` `nord` `dracula` and more
- 📋 Multi-line paste support
- 📤 Export as markdown, JSON, or plain text
- 🧠 View and search your memories from the terminal
- 🎛️ Customize temperature, system prompt, and sampling on the fly

### Slash Commands

| Command | What It Does |
|---------|-------------|
| `/help` | Show all commands |
| `/model` | List or switch models |
| `/temperature 0.7` | Set temperature |
| `/system` | Edit system prompt |
| `/memory` | View or search your memories |
| `/save` | Save this conversation |
| `/load` | Load a previous conversation |
| `/export md` | Export as markdown (also: `json`, `txt`) |
| `/clear` | Start fresh |
| `/quit` | Exit |

<div align="right">

[Back to top](#table-of-contents)

</div>

---

## 🖥️ Desktop App

A native desktop chat application built with PyQt6.

```bash
cd chat-app
pip install PyQt6 pydantic
python run_chat.py
```

Full GUI with conversation management, themes, settings, and proxy integration.

<div align="right">

[Back to top](#table-of-contents)

</div>

---

## 🌐 Remote Access

Access your proxy from anywhere without opening ports on your router.

### Cloudflare Tunnel

1. Go to the [Cloudflare Zero Trust dashboard](https://one.dash.cloudflare.com/) and create a tunnel
2. Copy the tunnel token
3. In UPtrim dashboard: **Tunnels → Cloudflare → Paste token → Start**

> Your proxy is now accessible at a `*.trycloudflare.com` URL or your custom domain.

### Tailscale

1. Get an auth key from the [Tailscale admin console](https://login.tailscale.com/admin/settings/keys)
2. In UPtrim dashboard: **Tunnels → Tailscale → Paste auth key → Start**

> Your proxy joins your Tailscale mesh network — accessible from any device on it.

Both tunnels auto-reconnect if the connection drops.

<div align="right">

[Back to top](#table-of-contents)

</div>

---

## ⚙️ Every Setting Explained

All settings live in `config.json` in the data directory. Change them from the **dashboard** (recommended) or edit the file directly. Environment variables override config values at startup.

> [!TIP]
> Most settings can be changed without restarting. The dashboard shows a live preview before you apply.

---

### Server Basics

<table>
<tr><td><b><code>upstream</code></b></td><td><code>"http://127.0.0.1:8080"</code></td></tr>
<tr><td colspan="2">

The URL of your LLM backend — where UPtrim sends chat requests. Set this to match your setup:

| Backend | Typical URL |
|---------|------------|
| Ollama | `http://localhost:11434` |
| llama.cpp | `http://localhost:8080` |
| LM Studio | `http://localhost:1234` |
| vLLM | `http://localhost:8000` |
| OpenAI | `https://api.openai.com` |

</td></tr>
</table>

<table>
<tr><td><b><code>host</code></b></td><td><code>"0.0.0.0"</code></td></tr>
<tr><td colspan="2">
What address UPtrim listens on. <code>0.0.0.0</code> accepts connections from any device on your network. Change to <code>127.0.0.1</code> if you only want local access.
</td></tr>
</table>

<table>
<tr><td><b><code>port</code></b></td><td><code>9099</code></td></tr>
<tr><td colspan="2">
The port UPtrim listens on. Change if 9099 conflicts with something else on your system.
</td></tr>
</table>

<table>
<tr><td><b><code>debug</code></b></td><td><code>false</code></td></tr>
<tr><td colspan="2">
Verbose logging. Useful for troubleshooting, noisy for production. Leave off unless you're chasing a bug.
</td></tr>
</table>

<table>
<tr><td><b><code>extra_backends</code></b></td><td><code>[]</code></td></tr>
<tr><td colspan="2">

Additional LLM backends beyond your primary. Each entry needs a `url` and optional `name` and `api_key`:

```json
[
  {"url": "http://ollama:11434", "name": "local"},
  {"url": "https://api.openai.com", "name": "openai", "api_key": "sk-..."}
]
```

Max backends depends on tier: 1 (trial) → 5 (earlybird/standard) → 10 (premium).

</td></tr>
</table>

---

### Context & Token Management

> These control how much of the model's context window goes to memory, files, and conversation history.

<table>
<tr><td><b><code>context_tokens</code></b></td><td><code>8000</code></td></tr>
<tr><td colspan="2">
Your model's total context window in tokens. <b>Match this to your model.</b> Running an 8K model? Set to ~8000. 32K model? 32000. 128K? You get the idea. Getting this wrong is the #1 cause of weird behavior.
</td></tr>
</table>

<table>
<tr><td><b><code>reserve_tokens</code></b></td><td><code>5000</code></td></tr>
<tr><td colspan="2">
Tokens reserved for the model's response. Context of 8000 minus reserve of 5000 = 3000 tokens for input (system prompt + memories + messages). Increase if your model gives long responses.
</td></tr>
</table>

<table>
<tr><td><b><code>soft_limit</code></b></td><td><code>1500</code></td></tr>
<tr><td colspan="2">
Preferred character limit for memory injection. UPtrim stays under this for most requests — only exceeds it when high-priority memories demand it.
</td></tr>
</table>

<table>
<tr><td><b><code>hard_limit</code></b></td><td><code>3000</code></td></tr>
<tr><td colspan="2">
Absolute maximum characters of memory to inject. Even with tons of relevant memories, injection stops here.
</td></tr>
</table>

<table>
<tr><td><b><code>max_sys_chars</code></b></td><td><code>1500</code></td></tr>
<tr><td colspan="2">
Maximum character length for the system message. Longer system prompts get trimmed.
</td></tr>
</table>

<table>
<tr><td><b><code>max_msg_chars</code></b></td><td><code>600</code></td></tr>
<tr><td colspan="2">
Max summary length per older user message when condensing conversation history.
</td></tr>
</table>

<table>
<tr><td><b><code>recent_keep</code></b></td><td><code>6</code></td></tr>
<tr><td colspan="2">
How many recent conversation turns to keep in full (older ones get summarized). Higher = more conversation context, less room for memories. <b>Sweet spot: 4–8.</b>
</td></tr>
</table>

<table>
<tr><td><b><code>chars_per_token</code></b></td><td><code>3.0</code></td></tr>
<tr><td colspan="2">
Estimated characters per token for budget math. English text averages 3–4. Most models work fine at 3.0.
</td></tr>
</table>

<table>
<tr><td><b><code>ai_short</code></b></td><td><code>80</code></td></tr>
<tr><td colspan="2">
AI responses shorter than this (characters) are treated as "short responses" — extraction behavior may adjust.
</td></tr>
</table>

<table>
<tr><td><b><code>user_short_words</code></b></td><td><code>3</code></td></tr>
<tr><td colspan="2">
Messages under this word count skip memory extraction. Keeps "hi", "ok", and "thanks" out of memories.
</td></tr>
</table>

<table>
<tr><td><b><code>summary_chars</code></b></td><td><code>500</code></td></tr>
<tr><td colspan="2">
Target length for auto-generated conversation summaries.
</td></tr>
</table>

---

### Memory Settings

> These control how memories are stored, prioritized, and injected into conversations.

<table>
<tr><td><b><code>mem_max_inject</code></b></td><td><code>1800</code></td></tr>
<tr><td colspan="2">
Total character budget for memory injection per request. All memories combined must fit in this.
</td></tr>
</table>

<table>
<tr><td><b><code>mem_always_pri</code></b></td><td><code>7</code></td></tr>
<tr><td colspan="2">
Priority threshold for "always inject." Memories at or above this priority are always included, no matter the topic. Lower it to include more by default; raise it to be picky.
</td></tr>
</table>

<table>
<tr><td><b><code>mem_relevance_boost</code></b></td><td><code>2</code></td></tr>
<tr><td colspan="2">
How much relevance matters vs. raw priority. At <code>1</code>, priority dominates. At <code>3+</code>, a highly relevant low-priority memory can beat an irrelevant high-priority one.
</td></tr>
</table>

<table>
<tr><td><b><code>mem_max_per_user</code></b></td><td><code>500</code></td></tr>
<tr><td colspan="2">
Max memories stored per user. <code>0</code> = unlimited. When hit, lowest-quality memories get pruned. <b>Good range for active users: 200–500.</b>
</td></tr>
</table>

<details>
<summary><b>Per-Category Priority & Always-Inject</b></summary>

<br/>

Each category has a **priority** (1–10) and an **always-inject** flag. Higher priority = included first. Always-inject = included regardless of relevance.

| Setting | Default | What It Controls |
|---------|:-------:|-----------------|
| `mem_pri_identity` | `9` | Name, age, location — the core "who are you" |
| `mem_always_identity` | `true` | Always include? **Yes** — forgetting a name feels broken |
| `mem_pri_communication` | `8` | Response style (concise, detailed, formal) |
| `mem_always_communication` | `true` | Always include? **Yes** — keeps tone consistent |
| `mem_pri_health` | `7` | Allergies, conditions, medications |
| `mem_always_health` | `false` | Only when health topics come up |
| `mem_pri_dietary` | `6` | Food preferences and restrictions |
| `mem_always_dietary` | `false` | Only when food is discussed |
| `mem_pri_work` | `6` | Job, company, projects, role |
| `mem_always_work` | `false` | Only for work conversations |
| `mem_pri_family` | `6` | Family members and relationships |
| `mem_always_family` | `false` | Only when family comes up |
| `mem_pri_technical` | `5` | Languages, tools, frameworks |
| `mem_always_technical` | `false` | Only for tech conversations |
| `mem_pri_preference` | `5` | Likes, dislikes, preferences |
| `mem_always_preference` | `false` | Only when relevant |
| `mem_pri_people` | `5` | Other people the user mentions |
| `mem_always_people` | `false` | Only when those people come up |
| `mem_pri_general` | `3` | Everything else |
| `mem_always_general` | `false` | Only when relevant |

> [!TIP]
> **Users complain the AI "forgets" something?** Find its category and raise the priority or set `always` to `true`.
>
> **Model drowning in irrelevant memories?** Lower priorities or set more categories to `always: false`.

</details>

<details>
<summary><b>Memory Expiration (TTL)</b></summary>

<br/>

| Setting | Default | Meaning |
|---------|:-------:|---------|
| `mem_ttl_people` | `30` | Memories about other people expire after 30 days |
| `mem_ttl_general` | `0` | General memories never expire (`0` = forever) |
| `mem_ttl_uploaded` | `90` | File-sourced memories expire after 90 days |
| `mem_ttl_temporary` | `7` | Temporary/situation memories expire after 7 days |

Set to `0` to disable expiration. Lower the number if memory gets cluttered.

</details>

---

### File Upload & RAG Settings

<table>
<tr><td><b><code>upload_max_mb</code></b></td><td><code>100</code></td></tr>
<tr><td colspan="2">
Max single file size in MB. Need to upload huge files? Raise it. Most users are fine at 100.
</td></tr>
</table>

<table>
<tr><td><b><code>upload_max_files_per_user</code></b></td><td><code>50</code></td></tr>
<tr><td colspan="2">
How many files a user can have at once. Prevents one user from filling your disk.
</td></tr>
</table>

<table>
<tr><td><b><code>upload_max_bytes_per_user</code></b></td><td><code>500</code></td></tr>
<tr><td colspan="2">
Total storage per user in MB. 500 = lots of small files or a few large ones.
</td></tr>
</table>

<table>
<tr><td><b><code>upload_chunk_size</code></b></td><td><code>400</code></td></tr>
<tr><td colspan="2">
Text chunk size in KB for file retrieval. Smaller = more precise but more overhead. Bigger = more context per hit but less precise. <b>Sweet spot: 300–500.</b>
</td></tr>
</table>

<table>
<tr><td><b><code>upload_max_chunks</code></b></td><td><code>50</code></td></tr>
<tr><td colspan="2">
Max chunks per file. Content beyond this gets truncated.
</td></tr>
</table>

<table>
<tr><td><b><code>file_inject_budget</code></b></td><td><code>4000</code></td></tr>
<tr><td colspan="2">
Max characters of file content injected per request. Increase for models with large context windows.
</td></tr>
</table>

<table>
<tr><td><b><code>file_inject_max</code></b></td><td><code>3</code></td></tr>
<tr><td colspan="2">
Max files injected per request. User has 20 files and asks a vague question? UPtrim picks the top 3 most relevant.
</td></tr>
</table>

<table>
<tr><td><b><code>file_budget_dynamic</code></b></td><td><code>true</code></td></tr>
<tr><td colspan="2">
File budget adapts based on available context. Memories using less room → files get more room. <b>Leave on.</b>
</td></tr>
</table>

<table>
<tr><td><b><code>file_budget_pct</code></b></td><td><code>0.40</code></td></tr>
<tr><td colspan="2">
With dynamic budgeting, files can use up to this percentage of remaining context after system prompt and messages.
</td></tr>
</table>

<table>
<tr><td><b><code>file_budget_safety_margin</code></b></td><td><code>500</code></td></tr>
<tr><td colspan="2">
Safety buffer (chars) so file injection doesn't overflow the context.
</td></tr>
</table>

<table>
<tr><td><b><code>allow_query_param_token</code></b></td><td><code>false</code></td></tr>
<tr><td colspan="2">
Allow <code>?token=xxx</code> in URLs. Convenient for some integrations but less secure (tokens show in logs). <b>Leave off unless needed.</b>
</td></tr>
</table>

<details>
<summary><b>Semantic File Search (Optional)</b></summary>

<br/>

<table>
<tr><td><b><code>file_embedding_enabled</code></b></td><td><code>false</code></td></tr>
<tr><td colspan="2">
FAISS-powered semantic search. Without it, keyword + fuzzy matching works well. With it, you also get meaning-based matching — <i>"employee compensation"</i> finds <i>"salary breakdown"</i> even without keyword overlap. Requires <code>sentence-transformers</code> + <code>faiss-cpu</code>.
</td></tr>
</table>

<table>
<tr><td><b><code>file_embedding_model</code></b></td><td><code>"BAAI/bge-base-en-v1.5"</code></td></tr>
<tr><td colspan="2">
Embedding model. Default is a good quality/speed balance. Change only if you know what you're doing.
</td></tr>
</table>

<table>
<tr><td><b><code>file_embedding_chunk_size</code></b></td><td><code>512</code></td></tr>
<tr><td colspan="2">
Chunk size for embeddings specifically. Larger = more context per embedding, less precise.
</td></tr>
</table>

<table>
<tr><td><b><code>file_embedding_topk</code></b></td><td><code>5</code></td></tr>
<tr><td colspan="2">
Top-k embedding matches to consider. Higher = more candidates, more processing.
</td></tr>
</table>

<table>
<tr><td><b><code>file_embedding_threshold</code></b></td><td><code>0.35</code></td></tr>
<tr><td colspan="2">
Minimum similarity for a match. Lower = more results (noisier). Higher = only strong matches. <b>Typical: 0.3–0.5.</b>
</td></tr>
</table>

<table>
<tr><td><b><code>embedding_gpu</code></b></td><td><code>"auto"</code></td></tr>
<tr><td colspan="2">
<code>auto</code> detects CUDA. <code>always</code> forces GPU (fails without one). <code>never</code> forces CPU.
</td></tr>
</table>

</details>

---

### Security & Authentication

<table>
<tr><td><b><code>security_mode</code></b></td><td><code>"auto"</code></td></tr>
<tr><td colspan="2">

| Value | Behavior |
|-------|----------|
| `auto` | **Recommended.** Detects local vs. exposed, adjusts automatically |
| `local_only` | Relaxed auth — assumes only you can access it |
| `open` | Assumes you have your own auth in front (Cloudflare Access, nginx, etc.) |

</td></tr>
</table>

<table>
<tr><td><b><code>trusted_proxies</code></b></td><td><code>"127.0.0.1,::1"</code></td></tr>
<tr><td colspan="2">
Comma-separated IPs of trusted reverse proxies. Behind nginx or Cloudflare? Add their IPs here so identity resolution works correctly.
</td></tr>
</table>

<table>
<tr><td><b><code>dash_token_custom</code></b></td><td><code>""</code></td></tr>
<tr><td colspan="2">
Set your own dashboard token instead of the auto-generated one. Empty = use auto-generated.
</td></tr>
</table>

<table>
<tr><td><b><code>dashboard_password</code></b></td><td><code>""</code></td></tr>
<tr><td colspan="2">
Optional password gate for the dashboard. If set, users enter this password <i>in addition to</i> the token.
</td></tr>
</table>

<table>
<tr><td><b><code>protect_read_endpoints</code></b></td><td><code>true</code></td></tr>
<tr><td colspan="2">
Require auth even for read-only API endpoints. Set <code>false</code> if you want unauthenticated apps to read data.
</td></tr>
</table>

<table>
<tr><td><b><code>log_security_events</code></b></td><td><code>true</code></td></tr>
<tr><td colspan="2">
Log failed auth, suspicious requests, etc. <b>Leave on.</b>
</td></tr>
</table>

<table>
<tr><td><b><code>maintenance_mode</code></b></td><td><code>false</code></td></tr>
<tr><td colspan="2">
Rejects all writes. Useful during backups or migrations.
</td></tr>
</table>

<table>
<tr><td><b><code>identity_mode</code></b></td><td><code>"strict"</code></td></tr>
<tr><td colspan="2">
How strictly identity is enforced. See <a href="#identity-modes">Identity Modes</a>.
</td></tr>
</table>

<table>
<tr><td><b><code>security_profile</code></b></td><td><code>"cloudflare_strict"</code></td></tr>
<tr><td colspan="2">
Preset security config. <code>cloudflare_strict</code> is the most secure. <code>default</code> is more permissive. <code>cloudflare_quarantine</code> sandboxes unknowns.
</td></tr>
</table>

<table>
<tr><td><b><code>trust_owui_headers</code></b></td><td><code>"auto"</code></td></tr>
<tr><td colspan="2">
Trust Open WebUI's identity headers. <code>auto</code> trusts when behind a trusted proxy. <code>always</code> trusts unconditionally. <code>never</code> ignores them.
</td></tr>
</table>

<table>
<tr><td><b><code>owui_hmac_secret</code></b></td><td><code>""</code></td></tr>
<tr><td colspan="2">
HMAC secret for cryptographic header verification. Prevents spoofing. Set this to a shared secret between OWUI and UPtrim.
</td></tr>
</table>

<table>
<tr><td><b><code>strict_memory_isolation</code></b></td><td><code>true</code></td></tr>
<tr><td colspan="2">
Blocks anonymous/quarantined users from all memory operations. <b>Strong default — leave on.</b>
</td></tr>
</table>

<table>
<tr><td><b><code>identity_source_priority</code></b></td><td><code>"owui_header,custom_header,api_token,api_payload,ip_fallback"</code></td></tr>
<tr><td colspan="2">
Order identity sources are checked. Rearrange if your setup needs different priority.
</td></tr>
</table>

<details>
<summary><b>Rate Limiting</b></summary>

<br/>

<table>
<tr><td><b><code>rate_limit_rpm</code></b></td><td><code>60</code></td></tr>
<tr><td colspan="2">
Max requests per minute per user. Higher for power users, lower for public instances.
</td></tr>
</table>

<table>
<tr><td><b><code>rate_limit_burst</code></b></td><td><code>10</code></td></tr>
<tr><td colspan="2">
Burst allowance above the rate limit before throttling kicks in.
</td></tr>
</table>

<table>
<tr><td><b><code>max_queue_depth</code></b></td><td><code>20</code></td></tr>
<tr><td colspan="2">
Max queued requests. Full queue = new requests rejected immediately.
</td></tr>
</table>

<table>
<tr><td><b><code>stale_request_timeout</code></b></td><td><code>30</code></td></tr>
<tr><td colspan="2">
Seconds before a queued request is dropped as stale.
</td></tr>
</table>

</details>

---

### Registration & Invites

<table>
<tr><td><b><code>registration_enabled</code></b></td><td><code>false</code></td></tr>
<tr><td colspan="2">
Allow self-registration. Off by default.
</td></tr>
</table>

<table>
<tr><td><b><code>registration_require_invite</code></b></td><td><code>true</code></td></tr>
<tr><td colspan="2">
Require an invite code to register. Create codes from the dashboard.
</td></tr>
</table>

<table>
<tr><td><b><code>registration_default_role</code></b></td><td><code>"user"</code></td></tr>
<tr><td colspan="2">
Role for new self-registered users. Usually <code>user</code>. Options: <code>user</code>, <code>viewer</code>.
</td></tr>
</table>

---

### SillyTavern Integration

<table>
<tr><td><b><code>st_enabled</code></b></td><td><code>true</code></td></tr>
<tr><td colspan="2">
Detect SillyTavern user headers automatically.
</td></tr>
</table>

<table>
<tr><td><b><code>st_auto_create_users</code></b></td><td><code>true</code></td></tr>
<tr><td colspan="2">
Auto-create accounts for new SillyTavern users.
</td></tr>
</table>

<table>
<tr><td><b><code>st_header_name</code></b></td><td><code>"x-st-user"</code></td></tr>
<tr><td colspan="2">
The header SillyTavern sends the username in.
</td></tr>
</table>

<table>
<tr><td><b><code>st_user_prefix</code></b></td><td><code>"st:"</code></td></tr>
<tr><td colspan="2">
Prefix for SillyTavern user IDs to avoid collisions.
</td></tr>
</table>

<table>
<tr><td><b><code>st_default_role</code></b></td><td><code>"user"</code></td></tr>
<tr><td colspan="2">
Default role for auto-created ST users.
</td></tr>
</table>

---

### NLP & Extraction

<table>
<tr><td><b><code>use_spacy</code></b></td><td><code>true</code></td></tr>
<tr><td colspan="2">
Use spaCy for memory extraction. Falls back to regex automatically if not installed. spaCy is significantly better.
</td></tr>
</table>

<table>
<tr><td><b><code>nlp_mode</code></b></td><td><code>"auto"</code></td></tr>
<tr><td colspan="2">

| Value | Quality | Speed | Requirements |
|-------|:-------:|:-----:|-------------|
| `auto` | Best available | Auto | Whatever's installed |
| `spacy_trf` | Best | Slow (fast with GPU) | `en_core_web_trf` model |
| `full_spacy` | Good | Fast | `en_core_web_sm` model |
| `spacy_lite` | Decent | Very fast | `en_core_web_sm` model |
| `regex_only` | Basic | Instant | Nothing extra |

</td></tr>
</table>

<table>
<tr><td><b><code>use_gpu</code></b></td><td><code>"auto"</code></td></tr>
<tr><td colspan="2">
GPU for spaCy. <code>auto</code> detects CUDA. <code>always</code> forces GPU. <code>never</code> forces CPU.
</td></tr>
</table>

---

### Auto-Model Routing

<table>
<tr><td><b><code>auto_model_enabled</code></b></td><td><code>true</code></td></tr>
<tr><td colspan="2">
Auto-select models based on request complexity. Needs multiple backends or models.
</td></tr>
</table>

<table>
<tr><td><b><code>auto_tier_fast</code></b></td><td><code>""</code></td></tr>
<tr><td colspan="2">
Model for quick, simple requests. Empty = disabled.
</td></tr>
</table>

<table>
<tr><td><b><code>auto_tier_balanced</code></b></td><td><code>""</code></td></tr>
<tr><td colspan="2">
Model for typical conversations. Your "default."
</td></tr>
</table>

<table>
<tr><td><b><code>auto_tier_smart</code></b></td><td><code>""</code></td></tr>
<tr><td colspan="2">
Model for complex reasoning, coding, and analysis.
</td></tr>
</table>

---

### Agent Settings

<table>
<tr><td><b><code>agent_enabled</code></b></td><td><code>false</code></td></tr>
<tr><td colspan="2">
Enable the agent framework. Certain requests trigger a multi-step tool-using loop instead of a single LLM call.
</td></tr>
</table>

<table>
<tr><td><b><code>agent_auto_detect</code></b></td><td><code>true</code></td></tr>
<tr><td colspan="2">
Let UPtrim decide when to use agent mode. Off = must be explicitly triggered.
</td></tr>
</table>

<table>
<tr><td><b><code>agent_max_iterations</code></b></td><td><code>10</code></td></tr>
<tr><td colspan="2">
Safety limit on agent loop iterations. 10 handles most tasks. Complex coding might need 15–25.
</td></tr>
</table>

<table>
<tr><td><b><code>agent_timeout_seconds</code></b></td><td><code>120</code></td></tr>
<tr><td colspan="2">
Hard timeout for the entire agent session. Returns whatever progress it has.
</td></tr>
</table>

<table>
<tr><td><b><code>agent_tools</code></b></td><td><i>(comma-separated list)</i></td></tr>
<tr><td colspan="2">
Which tools the agent can use. Restrict to only allow tools you're comfortable with.
</td></tr>
</table>

<table>
<tr><td><b><code>agent_model_override</code></b></td><td><code>""</code></td></tr>
<tr><td colspan="2">
Force a specific model for agent tasks. Useful to always use your most capable model.
</td></tr>
</table>

<table>
<tr><td><b><code>agent_sub_agents_enabled</code></b></td><td><code>true</code></td></tr>
<tr><td colspan="2">
Allow sub-agent spawning for parallel work. Powerful but uses more compute.
</td></tr>
</table>

<table>
<tr><td><b><code>agent_max_sub_agents</code></b></td><td><code>3</code></td></tr>
<tr><td colspan="2">
Max concurrent sub-agents. Higher = more parallelism, more backend load.
</td></tr>
</table>

---

### Open WebUI Integration

<table>
<tr><td><b><code>auto_create_owui_users</code></b></td><td><code>true</code></td></tr>
<tr><td colspan="2">
Auto-create accounts when new Open WebUI users are detected.
</td></tr>
</table>

<table>
<tr><td><b><code>owui_base_url</code></b></td><td><code>""</code></td></tr>
<tr><td colspan="2">
Your Open WebUI URL. Used for connectivity testing in the dashboard.
</td></tr>
</table>

---

### UI & Behavior

<table>
<tr><td><b><code>enable_tui</code></b></td><td><code>true</code></td></tr>
<tr><td colspan="2">
Show terminal UI when running. <code>false</code> for cleaner headless output.
</td></tr>
</table>

<table>
<tr><td><b><code>greet_new_users</code></b></td><td><code>true</code></td></tr>
<tr><td colspan="2">
Store a welcome greeting for new users. The model greets them warmly on first conversation.
</td></tr>
</table>

---

### Development & Experimental

<table>
<tr><td><b><code>dev_mode_enabled</code></b></td><td><code>false</code></td></tr>
<tr><td colspan="2">
Developer-only debug endpoints. <b>Don't enable in production.</b>
</td></tr>
</table>

<table>
<tr><td><b><code>experimental_file_tools</code></b></td><td><code>false</code></td></tr>
<tr><td colspan="2">
Experimental file manipulation tools. May be unstable.
</td></tr>
</table>

---

### Remote Access Settings

<table>
<tr><td><b><code>cf_tunnel_token</code></b></td><td><code>""</code></td></tr>
<tr><td colspan="2">
Cloudflare Tunnel token. Easiest to set via dashboard Tunnels panel.
</td></tr>
</table>

<table>
<tr><td><b><code>ts_authkey</code></b></td><td><code>""</code></td></tr>
<tr><td colspan="2">
Tailscale auth key. Set via dashboard Tunnels panel.
</td></tr>
</table>

<table>
<tr><td><b><code>ts_hostname</code></b></td><td><code>""</code></td></tr>
<tr><td colspan="2">
Custom hostname for your Tailscale node (e.g., <code>uptrim-proxy</code>).
</td></tr>
</table>

---

### Performance Tuning (Environment Variables)

> These are set as **environment variables**, not in config.json.

| Variable | Default | What To Know |
|----------|---------|-------------|
| `THREAD_POOL_SIZE` | `min(8, cpu+2)` | Main thread pool. Increase on beefy servers. |
| `EXTRACT_POOL_SIZE` | `pool_size // 2` | Memory extraction threads. Increase if extraction feels slow. |
| `GC_EVERY_REQUESTS` | `200` | Garbage collection frequency. Lower = less RAM, more CPU. |
| `POOL_RECYCLE_REQUESTS` | `500` | DB connection recycling. Prevents stale connections. |
| `WORKERS` | `1` | Uvicorn workers. >1 only if you understand SQLite implications. |

<div align="right">

[Back to top](#table-of-contents)

</div>

---

## 💳 Licensing & Tiers

UPtrim works immediately with a **free trial**. Paid tiers unlock more features.

### Feature Comparison

| | <sub>Trial (Free)</sub> | <sub>Earlybird ($40/yr)</sub> | <sub>Standard ($100/yr)</sub> | <sub>Premium ($200/yr)</sub> |
|:--|:--:|:--:|:--:|:--:|
| **Memories per user** | 30 | Unlimited | Unlimited | Unlimited |
| **LLM Backends** | 1 | 5 | 5 | 10 |
| **Upload Storage** | 15 MB | 25 MB | 25 MB | 1 GB |
| Custom Prompts | | ✅ | ✅ | ✅ |
| Model Aliases | | ✅ | ✅ | ✅ |
| Remote Access | | ✅ | ✅ | ✅ |
| MCP Tools | | ✅ | ✅ | ✅ |
| File Tools | | ✅ | ✅ | ✅ |
| Auto-Model Routing | | ✅ | ✅ | ✅ |
| Ghost Agent | | ✅ | ✅ | ✅ |
| Advanced Agent | | ✅ | ✅ | ✅ |
| Persona Engine | | | | ✅ |
| Predictive Context | | | | ✅ |
| Knowledge Graph | | | | ✅ |
| Memory Consolidation | | | | ✅ |
| Dev Settings | | | | ✅ |
| CLI Access | | | | ✅ |

### How to Activate

<details>
<summary><b>At startup</b></summary>

```
Enter license key: XXXXX-XXXXX-XXXXX-XXXXX
```

</details>

<details>
<summary><b>From the dashboard</b></summary>

Navigate to **Settings → License → Enter Key → Activate**

</details>

<details>
<summary><b>Via API</b></summary>

```bash
curl -X POST http://localhost:9099/api/license/activate \
  -H "Authorization: Bearer YOUR_DASH_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"key": "XXXXX-XXXXX-XXXXX-XXXXX"}'
```

</details>

> [!NOTE]
> Licenses work offline for up to **14 days** using cached validation.

<div align="right">

[Back to top](#table-of-contents)

</div>

---

## 🔧 Troubleshooting

<details>
<summary><b>"Cannot connect to upstream"</b></summary>

<br/>

Your LLM backend isn't reachable.

1. **Is it running?** Try: `curl http://your-backend-url/v1/models`
2. **Check the `upstream` setting** — does it match where your backend actually is?
3. **Different machine?** Make sure firewalls aren't blocking the port
4. **Docker?** Use the container name or host IP, not `localhost`

</details>

<details>
<summary><b>"spaCy model not found"</b></summary>

<br/>

```bash
python -m spacy download en_core_web_sm
```

UPtrim works without spaCy (falls back to regex), but extraction is noticeably better with it.

For best quality with GPU:
```bash
pip install spacy[cuda12x]
python -m spacy download en_core_web_trf
```

</details>

<details>
<summary><b>Memories aren't being created</b></summary>

<br/>

- **Short messages** (under 3 words) skip extraction by design — nothing useful to extract
- **Check NLP status** in the dashboard. If it says `regex_only` and you expected spaCy, reinstall it
- **Memory cap hit** — check `mem_max_per_user`
- **Tier limit** — trial is capped at 30 memories per user

</details>

<details>
<summary><b>File uploads fail</b></summary>

<br/>

- Check file size against `upload_max_mb` (default: 100 MB)
- Check total storage against `upload_max_bytes_per_user` (default: 500 MB)
- Make sure the file extension is [supported](#supported-file-types)
- Check the dashboard logs for the specific error message

</details>

<details>
<summary><b>Lost my dashboard token</b></summary>

<br/>

Three options:

1. **Check terminal history** — it was printed at first startup
2. **Set your own** — add `"dash_token_custom": "mytoken"` to `config.json` and restart
3. **Regenerate** — use the API key (also printed at startup): `POST /api/regenerate-api-key`

</details>

<details>
<summary><b>High memory / RAM usage</b></summary>

<br/>

- Disable file embeddings if you don't need semantic search: `file_embedding_enabled: false`
- Lower `mem_max_per_user` to cap stored memories
- Reduce `THREAD_POOL_SIZE` and `EXTRACT_POOL_SIZE` env vars
- Lower `POOL_RECYCLE_REQUESTS` to recycle DB connections more often

</details>

<details>
<summary><b>Wrong user getting wrong memories</b></summary>

<br/>

- Check **Dashboard → Identity Info** to see how resolution is configured
- Behind a reverse proxy? Make sure its IP is in `trusted_proxies`
- For Open WebUI, check `trust_owui_headers` setting
- Use **Dashboard → Debug Headers** to see exactly what headers arrive

</details>

<details>
<summary><b>Model gives weird responses / context overflow</b></summary>

<br/>

- **`context_tokens` mismatch** — this is the #1 cause. Set it to match your actual model's context size.
- **Memories overwhelming context** — lower `mem_max_inject` or `hard_limit`
- **Long conversations** — reduce `recent_keep` to free room
- **Reserve too low** — check that `reserve_tokens` leaves enough room for input

</details>

<details>
<summary><b>Slow response times</b></summary>

<br/>

- Install `orjson` for 3–10x faster JSON: `pip install orjson`
- Install `uvloop` (Linux/macOS) for faster networking: `pip install uvloop`
- Check if spaCy transformer mode is bottlenecking on CPU — switch to `full_spacy` or add a GPU
- Reduce `file_embedding_topk` if semantic search is slow

</details>

---

<div align="center">

<br/>

<img src="https://img.shields.io/badge/UPtrim_Context_Proxy-v1.17.0-0080ff?style=for-the-badge" alt="UPtrim v1.17.0" />

**Your AI remembers everything. Finally.**

<sub>Built with FastAPI, SQLite, FAISS, and spaCy</sub>

</div>
