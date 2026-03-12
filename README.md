<div align="center">

<br/>

<img src="https://img.shields.io/badge/v1.0.0-0080ff?style=for-the-badge" alt="v1.0.0" />
&nbsp;
<img src="https://img.shields.io/badge/OpenAI_Compatible-412991?style=for-the-badge&logo=openai&logoColor=white" alt="OpenAI Compatible" />
&nbsp;
<img src="https://img.shields.io/badge/Windows_%7C_macOS_%7C_Linux-22c55e?style=for-the-badge" alt="Cross Platform" />

<br/><br/>

# UPtrim Context Proxy

### Your AI forgets you. We fix that.

<br/>

Every time you close a chat, your AI starts over — your name, your preferences, your projects, gone.<br/>
UPtrim gives any local LLM a permanent memory. Drop it in, change nothing, and your AI finally knows who you are.<br/>
**Works with what you already use. No code changes. No cloud.**

<br/>

[Get Started](#-getting-started) &nbsp;&nbsp;|&nbsp;&nbsp; [What We Fix](#-six-problems-we-fix) &nbsp;&nbsp;|&nbsp;&nbsp; [Settings Guide](#-every-setting-explained) &nbsp;&nbsp;|&nbsp;&nbsp; [Licensing](#-licensing--tiers)

<br/>

---

<br/>

**Works with everything you already use**

<br/>

<img src="https://img.shields.io/badge/Ollama-000000?style=for-the-badge&logo=ollama" alt="Ollama" />&nbsp;
<img src="https://img.shields.io/badge/llama.cpp-333333?style=for-the-badge" alt="llama.cpp" />&nbsp;
<img src="https://img.shields.io/badge/vLLM-5046e5?style=for-the-badge" alt="vLLM" />&nbsp;
<img src="https://img.shields.io/badge/LM_Studio-1a1a2e?style=for-the-badge" alt="LM Studio" />&nbsp;
<img src="https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai&logoColor=white" alt="OpenAI" />

<br/><br/>

<img src="https://img.shields.io/badge/Open_WebUI-16a34a?style=for-the-badge" alt="Open WebUI" />&nbsp;
<img src="https://img.shields.io/badge/SillyTavern-c084fc?style=for-the-badge" alt="SillyTavern" />&nbsp;
<img src="https://img.shields.io/badge/n8n-ea4b71?style=for-the-badge&logo=n8n&logoColor=white" alt="n8n" />&nbsp;
<img src="https://img.shields.io/badge/Claude_Desktop-d97706?style=for-the-badge" alt="Claude Desktop" />

<br/><br/>

</div>

---

<br/>

## 🎯 Six Problems We Fix

<table>
<tr>
<td width="50%" valign="top">

### 🧠 &nbsp; Your AI Forgets You Every Time
Every new chat starts from zero — your name, preferences, and projects all gone. UPtrim automatically learns facts from your conversations and brings up the right ones at the right time. Your AI finally knows who you are.

</td>
<td width="50%" valign="top">

### 📁 &nbsp; Your AI Can't Read Your Documents
The answer is sitting in a PDF or a spreadsheet, but your AI can't touch it. Upload files (33+ types) and ask questions — UPtrim finds the right file, pulls the right section, and hands it to the model.

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🔀 &nbsp; One Model Can't Do Everything
Quick questions waste your best model's time. Hard problems overwhelm your fast model. Connect up to 10 backends and let UPtrim auto-route — simple questions go to the fast model, complex tasks go to the powerful one.

</td>
<td width="50%" valign="top">

### 🔐 &nbsp; Shared AI Means Shared Memories
When multiple people use the same AI, everyone's data bleeds together. UPtrim gives every user their own isolated memory space — your team shares one AI, but nobody sees anyone else's data.

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🤖 &nbsp; You Shouldn't Have to Do the Legwork
When your AI doesn't know something, you end up switching tabs, searching, and pasting results back in. Agent mode lets the AI search the web, fetch URLs, edit files, and run code on its own.

</td>
<td width="50%" valign="top">

### 🧬 &nbsp; Long Chats Go Off the Rails
After enough back-and-forth, your AI forgets what you said 20 messages ago and starts repeating itself. UPtrim keeps important details visible and summarizes the rest — chat for hours without it falling apart.

</td>
</tr>
</table>

<br/>

---

<br/>

## 📑 Guide

<br/>

| | Section | |
|:---:|---------|---|
| **01** | [Getting Started](#-getting-started) | First launch, connecting your apps |
| **02** | [How It Works](#-how-it-works) | What happens to every request |
| **03** | [Connecting Your Frontend](#-connecting-your-frontend) | Open WebUI, SillyTavern, custom apps, direct API |
| **04** | [The Dashboard](#-the-dashboard) | Admin panel, user memory page, chat UI |
| **05** | [Memory](#-memory) | How memories work, what gets stored, how to tune it |
| **06** | [File Uploads & RAG](#-file-uploads--rag) | Uploading files, talking about them, semantic search |
| **07** | [Multi-Backend & Model Routing](#-multi-backend--model-routing) | Multiple LLMs, auto-routing, model aliases |
| **08** | [Identity & Users](#-identity--users) | Who's who, security modes, user accounts |
| **09** | [The Agent System](#-the-agent-system) | Multi-step tool use, sub-agents, safety limits |
| **10** | [Advanced Intelligence](#-advanced-intelligence) | Ghost agents, knowledge graph, persona, predictions |
| **11** | [MCP Integration](#-mcp-integration) | n8n, Claude Desktop, external memory access |
| **12** | [CLI Chat Client](#-cli-chat-client) | Terminal chat with themes, streaming, slash commands |
| **13** | [Desktop App](#-desktop-app) | Native chat application |
| **14** | [Remote Access](#-remote-access) | Cloudflare Tunnel & Tailscale setup |
| **15** | [Every Setting Explained](#-every-setting-explained) | Every config key — what it does, when to change it |
| **16** | [Licensing & Tiers](#-licensing--tiers) | Free trial, paid tiers, feature comparison |
| **17** | [Troubleshooting](#-troubleshooting) | Common issues and how to fix them |

<br/>

---

<br/>

## 🚀 Getting Started

<br/>

> **You need:** An LLM backend running somewhere (Ollama, llama.cpp, vLLM, LM Studio, OpenAI — anything OpenAI-compatible) and UPtrim. That's it.

<br/>

### First Launch

Run UPtrim. On first launch:

| | What Happens |
|:---:|---|
| ✅ | Database created automatically |
| ✅ | Security token generated — **save this from your console**, you need it for the dashboard |
| ✅ | Dashboard opens in your browser at `http://localhost:9099/dashboard` |
| ✅ | Proxy starts listening for chat requests on port `9099` |

<br/>

> [!IMPORTANT]
> If your LLM backend isn't at `localhost:8080`, set your upstream URL in the dashboard after startup — no restart needed. Or configure the `upstream` setting before launching.

<br/>

<div align="right">
<a href="#-guide">Back to top ↑</a>
</div>

---

<br/>

## 🔄 How It Works

<br/>

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
```

<br/>

UPtrim is **invisible to both sides**. Your frontend thinks it's talking directly to the LLM. Your backend thinks it's getting normal requests. In between:

<br/>

| Step | | What Happens |
|:----:|---|---|
| `1` | 🔍 | **Identifies the user** — from headers, tokens, or other signals |
| `2` | 🧠 | **Retrieves relevant memories** — preferences, facts, history |
| `3` | 📁 | **Adds file context** — if the user is asking about their uploads |
| `4` | 📤 | **Sends enriched request** to your backend |
| `5` | 📥 | **Streams response** back to the user |
| `6` | 💾 | **Extracts new facts** and stores them for next time |

<br/>

> The user never sees any of this. They just notice the AI *remembers* them.

<br/>

<div align="right">
<a href="#-guide">Back to top ↑</a>
</div>

---

<br/>

## 🔌 Connecting Your Frontend

<br/>

<table>
<tr>
<td width="33%" valign="top">

#### Open WebUI

Set the OpenAI API base URL to:
```
http://<proxy-ip>:9099/v1
```
User identity is picked up automatically from OWUI headers — each user gets their own memory.

</td>
<td width="33%" valign="top">

#### SillyTavern

Add a **Chat Completion API** source:
- **URL:** `http://<proxy-ip>:9099`
- **Type:** OpenAI-compatible

Enable SillyTavern integration in the dashboard for per-character memory.

</td>
<td width="33%" valign="top">

#### Any Other App

Change the base URL to:
```
http://<proxy-ip>:9099/v1
```
If your app sends an API key, UPtrim uses it for user identification.

</td>
</tr>
</table>

<br/>

<details>
<summary><b>Direct API Example</b> (Python)</summary>

<br/>

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

<br/>

<div align="right">
<a href="#-guide">Back to top ↑</a>
</div>

---

<br/>

## 📊 The Dashboard

<br/>

The dashboard lives at **`http://localhost:9099/dashboard`**. Log in with the security token from first startup (or set your own via [`dash_token_custom`](#security--authentication)).

<br/>

<table>
<tr>
<td width="50%" valign="top">

| Section | What You Can Do |
|---------|----------------|
| **Status** | Health, backends, NLP, active users |
| **Config** | Every setting with live preview |
| **Users** | Accounts, linking, passwords |
| **Memories** | Search, edit, pin, import/export |
| **Files** | Uploads, storage per user |
| **Prompts** | Custom system prompts |

</td>
<td width="50%" valign="top">

| Section | What You Can Do |
|---------|----------------|
| **Models** | Aliases, auto-routing config |
| **Tokens** | API token management |
| **Invites** | Registration invite codes |
| **Tunnels** | Cloudflare & Tailscale setup |
| **Logs** | Errors, audit trail, security |
| **Backup** | One-click backup & restore |

</td>
</tr>
</table>

<br/>

> [!TIP]
> **For end users:** `/my-memory` — personal memory viewer, no admin access needed.
>
> **Quick chat:** `/chat` — standalone chat UI through the proxy.

<br/>

<div align="right">
<a href="#-guide">Back to top ↑</a>
</div>

---

<br/>

## 🧠 Memory

<br/>

Your AI forgets your name the moment you close the chat. UPtrim fixes that — every conversation is automatically analyzed for facts worth remembering:

<br/>

```
 "My name is Alex"                         →  🏷️  identity
 "I'm a Python developer at Acme Corp"     →  💼  work
 "I prefer concise responses"              →  💬  communication
 "My daughter Emma starts school in Sep"   →  👨‍👩‍👧  family
 "I'm allergic to shellfish"               →  🏥  health
 "I use neovim and arch btw"              →  🔧  technical
```

<br/>

Next time that user chats, relevant facts are quietly injected into the context. The model responds like it knows them — because now it does.

<br/>

### Memory Categories

<br/>

| Category | What It Stores | Priority | Always On? |
|:---------|:--------------|:--------:|:----------:|
| 🏷️ Identity | Name, age, location | **9** | ✅ |
| 💬 Communication | Response style preferences | **8** | ✅ |
| 🏥 Health | Allergies, conditions, medications | **7** | |
| 🍽️ Dietary | Food preferences & restrictions | **6** | |
| 💼 Work | Job, company, projects | **6** | |
| 👨‍👩‍👧 Family | Family members & relationships | **6** | |
| 🔧 Technical | Languages, tools, frameworks | **5** | |
| ⭐ Preferences | Likes, dislikes | **5** | |
| 👥 People | Other people mentioned | **5** | |
| 📝 General | Everything else | **3** | |

<br/>

> Higher priority = more likely included. Priority **7+** is always injected. Everything else competes based on relevance to the current conversation.

<br/>

<table>
<tr>
<td width="50%" valign="top">

#### What Users Can Do

| | |
|---|---|
| 👁️ | View memories at `/my-memory` |
| ✏️ | Edit if extraction got something wrong |
| 🗑️ | Delete memories they don't want |
| 📌 | Pin important ones — always included |
| 🚩 | Report problematic memories |

</td>
<td width="50%" valign="top">

#### What Admins Can Do

| | |
|---|---|
| 🔍 | Browse **all** user memories |
| 🧹 | Quality sweeps & deduplication |
| 📤 | Import/export as JSON |
| ⚙️ | Per-category priorities & TTLs |
| 📊 | Per-user memory caps |

</td>
</tr>
</table>

<br/>

<div align="right">
<a href="#-guide">Back to top ↑</a>
</div>

---

<br/>

## 📁 File Uploads & RAG

<br/>

The answer is sitting in a PDF on your desktop, but your AI can't touch it. Upload files and just ask — UPtrim figures out which file(s) you mean and injects the relevant content.

<br/>

### Supported Formats

<br/>

| | Types |
|---|---|
| 📄 **Documents** | `PDF` `DOCX` `DOC` `PPTX` `XLSX` `XLS` `RTF` `ODT` `EPUB` |
| 📊 **Data** | `CSV` `JSON` `XML` `YAML` `TOML` |
| 💻 **Code** | `Python` `JavaScript` `TypeScript` `Go` `Rust` `Java` `C/C++` `Ruby` `PHP` `Lua` `R` `Shell` `SQL` + more |
| 📝 **Text** | `TXT` `Markdown` `LOG` `INI` `CFG` `CONF` |
| 🌐 **Web** | `HTML` `CSS` |

<br/>

### How It Works

<br/>

**On upload** — text extracted, keywords generated, smart summary created, optional vector embeddings built.

**On question** — UPtrim matches the query to the right file(s), pulls relevant sections, injects into context.

<br/>

> [!NOTE]
> Works with 20+ files. Say *"the budget spreadsheet"* — it finds your `.csv` or `.xlsx` budget file. Say *"compare the two contracts"* — it pulls both. Fuzzy matching, synonyms, and file type awareness handle the rest.

<br/>

<details>
<summary><b>Semantic Search</b> — optional but powerful</summary>

<br/>

Enable embeddings for meaning-based matching:

```json
"file_embedding_enabled": true
```

Now *"employee compensation"* finds content about *"salary breakdown"* even without keyword overlap. Works on top of the existing keyword matching.

</details>

<br/>

<div align="right">
<a href="#-guide">Back to top ↑</a>
</div>

---

<br/>

## 🔀 Multi-Backend & Model Routing

<br/>

<table>
<tr>
<td width="60%" valign="top">

### Adding Backends

In the dashboard, add extra backends:

```json
"extra_backends": [
    {"url": "http://ollama:11434", "name": "ollama-local"},
    {"url": "http://vllm-server:8000", "name": "vllm-gpu"},
    {"url": "https://api.openai.com", "name": "openai", "api_key": "sk-..."}
]
```

Max backends by tier: **1** (trial) → **5** (earlybird/standard) → **10** (premium)

</td>
<td width="40%" valign="top">

### Model Aliases

Give friendly names to ugly model IDs:

| Alias | Points To |
|-------|-----------|
| `writer` | `Nous-Hermes-2-Mixtral-8x7B...` |
| `coder` | `deepseek-coder-33b-instruct` |
| `fast` | `llama3-8b-instruct` |

Users request the alias, UPtrim translates.

</td>
</tr>
</table>

<br/>

### Auto-Model Routing

When enabled, UPtrim picks the best model per request:

```
auto_tier_fast:      "llama3-8b"       ←  quick questions, simple chat
auto_tier_balanced:  "llama3-70b"      ←  most conversations
auto_tier_smart:     "gpt-4"           ←  complex reasoning, coding
```

> *"What's the weather?"* → fast model. &nbsp; *"Refactor this and explain the design tradeoffs"* → smart model.

<br/>

<div align="right">
<a href="#-guide">Back to top ↑</a>
</div>

---

<br/>

## 🔐 Identity & Users

<br/>

When multiple people share one AI, everyone's context bleeds together. UPtrim keeps every user **completely isolated** — User A never sees User B's data.

<br/>

### How Users Are Identified

| Priority | Source | When It's Used |
|:--------:|--------|---------------|
| **1** | Open WebUI headers | Behind OWUI |
| **2** | Custom headers | Your own frontend |
| **3** | API tokens | Each token → a user |
| **4** | SillyTavern headers | ST integration enabled |
| **5** | IP fallback | Last resort |

<br/>

### User Accounts

<table>
<tr>
<td width="50%" valign="top">

| Feature | How |
|---------|-----|
| Self-registration | Enable in settings, optional invite codes |
| Admin creation | Dashboard → Users → Create |
| Self-service | Users log in at `/my-memory` |
| Account linking | Link identities across sources |

</td>
<td width="50%" valign="top">

#### Security Modes

| Mode | Best For |
|------|----------|
| `auto` | **Recommended** — auto-adjusts |
| `local_only` | Your own machine only |
| `open` | Behind your own auth |

#### Identity Modes

| Mode | Behavior |
|------|----------|
| `strict` | Must identify, spoofing checked |
| `required` | Must identify or blocked |
| `quarantine` | Unknowns get sandboxed |
| `legacy` | Lenient, backward compat |

</td>
</tr>
</table>

<br/>

<div align="right">
<a href="#-guide">Back to top ↑</a>
</div>

---

<br/>

## 🤖 The Agent System

<br/>

Tired of switching tabs to look things up for your AI? Agent mode lets the model plan, act, and iterate on its own — web search, file editing, code execution — until the task is done.

<br/>

```json
"agent_enabled": true,
"agent_auto_detect": true
```

> When auto-detect is on, coding tasks, file operations, and research queries enter agent mode automatically. Regular conversation stays normal.

<br/>

<table>
<tr>
<td width="50%" valign="top">

### Capabilities

| | |
|---|---|
| 📖 | Read, write, and edit files |
| ⚡ | Run shell commands & Python |
| 🌐 | Web search & URL fetching |
| 🧮 | Calculator |
| 🧠 | Store & recall memories |
| 🔄 | Spawn sub-agents in parallel |
| 🔍 | Scout large files efficiently |

</td>
<td width="50%" valign="top">

### Safety Limits

| Setting | Default | Purpose |
|---------|:-------:|---------|
| Max iterations | **10** | Prevents runaway loops |
| Timeout | **120s** | Hard cutoff |
| Tool restrictions | Per-tool | Disable anything risky |
| Tier gating | By license | Advanced → paid tier |

</td>
</tr>
</table>

<br/>

<div align="right">
<a href="#-guide">Back to top ↑</a>
</div>

---

<br/>

## 🧬 Problems That Solve Themselves

<br/>

These run invisibly in the background. No configuration needed — they activate when enabled for your tier.

<br/>

<table>
<tr>
<td width="50%" valign="top">

<details>
<summary><b>👻 Your AI Waits for You to Do the Legwork</b></summary>

<br/>

Ghost Agent fixes this — invisible background workers fetch URLs, search the web, and scan your memories *before* your request even hits the model. You get better answers without asking for them.

</details>

<details>
<summary><b>🕸️ Flat Memory Misses the Connections</b></summary>

<br/>

Storing facts as a flat list means your AI knows isolated details but can't see how they relate. Knowledge Graph builds a web of relationships — people, projects, concepts — across all conversations, so your AI understands context the way you do.

</details>

<details>
<summary><b>🎭 Everyone Gets the Same Generic Voice</b></summary>

<br/>

One person wants concise technical answers, another wants friendly explanations — but the AI talks to everyone the same way. Persona Engine learns each user's preferred style and adapts automatically.

</details>

</td>
<td width="50%" valign="top">

<details>
<summary><b>🔮 Your AI Never Follows Up on Anything</b></summary>

<br/>

You say "I need to finish the report by Friday" and the AI says "Good luck!" then never mentions it again. Predictive Context tracks conversation patterns and pre-loads what you'll need before you ask.

</details>

<details>
<summary><b>😴 Old Memories Pile Up and Conflict</b></summary>

<br/>

The more your AI remembers, the messier it gets — duplicates, outdated info, contradictions. Memory Gardener runs during idle time: merges duplicates, resolves conflicts, and keeps everything lean without you lifting a finger.

</details>

<details>
<summary><b>🧬 Your AI Treats Every Message the Same</b></summary>

<br/>

A quick question, a debugging session, and a brainstorming request all need different context — but your AI doesn't know that. Intent Classification analyzes each message and adjusts which memories get prioritized for that type.

</details>

</td>
</tr>
</table>

<br/>

<div align="right">
<a href="#-guide">Back to top ↑</a>
</div>

---

<br/>

## 🔗 MCP Integration

<br/>

Memory operations exposed via **Model Context Protocol** for external tools.

The MCP server runs automatically at `/mcp/` when available.

<br/>

| Operation | Description |
|-----------|-------------|
| **Search** | Find relevant memories for a query |
| **Store** | Save new facts as memories |
| **Recall** | Get most relevant memories for a context |
| **Forget** | Delete specific memories |

<br/>

<details>
<summary><b>Using with n8n</b></summary>

<br/>

Add an **MCP Client Tool** node:

| Field | Value |
|-------|-------|
| URL | `http://your-proxy:9099/mcp/` |
| Auth | Bearer token (your API key) |

</details>

<details>
<summary><b>Using with Claude Desktop</b></summary>

<br/>

Add to `claude_desktop_config.json`:

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

</details>

<br/>

<div align="right">
<a href="#-guide">Back to top ↑</a>
</div>

---

<br/>

## 💻 CLI Chat Client

<br/>

Full terminal chat client. Streaming, conversations, model switching — all from your terminal.

<br/>

<table>
<tr>
<td width="50%" valign="top">

### Features

| | |
|---|---|
| 🔄 | Streaming with live tokens/sec |
| 💾 | Save, load, manage conversations |
| 🎨 | 6+ themes — dark, light, monokai, nord, dracula |
| 📋 | Multi-line paste support |
| 📤 | Export as markdown, JSON, text |
| 🧠 | View & search memories |
| 🎛️ | Temperature, system prompt, sampling |

</td>
<td width="50%" valign="top">

### Slash Commands

| Command | |
|---------|---|
| `/help` | Show all commands |
| `/model` | List or switch models |
| `/temperature 0.7` | Set temperature |
| `/system` | Edit system prompt |
| `/memory` | View/search memories |
| `/save` | Save conversation |
| `/load` | Load conversation |
| `/export md` | Export (md/json/txt) |
| `/clear` | Start fresh |
| `/quit` | Exit |

</td>
</tr>
</table>

<br/>

<div align="right">
<a href="#-guide">Back to top ↑</a>
</div>

---

<br/>

## 🖥️ Desktop App

<br/>

Native desktop chat application with conversation management, themes, settings, and full proxy integration.

<br/>

<div align="right">
<a href="#-guide">Back to top ↑</a>
</div>

---

<br/>

## 🌐 Remote Access

<br/>

Access your proxy from anywhere — no port forwarding needed.

<br/>

<table>
<tr>
<td width="50%" valign="top">

### Cloudflare Tunnel

1. Create a tunnel at [Cloudflare Zero Trust](https://one.dash.cloudflare.com/)
2. Copy the tunnel token
3. Dashboard → **Tunnels → Cloudflare → Paste → Start**

> Accessible at `*.trycloudflare.com` or your custom domain.

</td>
<td width="50%" valign="top">

### Tailscale

1. Get an auth key from [Tailscale admin](https://login.tailscale.com/admin/settings/keys)
2. Dashboard → **Tunnels → Tailscale → Paste → Start**

> Joins your Tailscale mesh — accessible from any device on it.

</td>
</tr>
</table>

<br/>

> Both tunnels auto-reconnect if the connection drops.

<br/>

<div align="right">
<a href="#-guide">Back to top ↑</a>
</div>

---

<br/>

## ⚙️ Every Setting Explained

<br/>

All settings live in `config.json`. Change them from the **dashboard** (recommended) or edit the file directly. Environment variables override config values at startup.

> [!TIP]
> Most settings apply immediately — no restart needed. The dashboard shows a live preview before you apply changes.

<br/>

---

### Server Basics

<br/>

| Setting | Default | What It Does |
|---------|---------|-------------|
| **`upstream`** | `"http://127.0.0.1:8080"` | URL of your LLM backend. Ollama = `:11434`, llama.cpp = `:8080`, LM Studio = `:1234`, vLLM = `:8000` |
| **`host`** | `"0.0.0.0"` | Listen address. `0.0.0.0` = any device on your network. `127.0.0.1` = local only |
| **`port`** | `9099` | Listen port. Change if 9099 conflicts |
| **`debug`** | `false` | Verbose logging. Useful for troubleshooting, noisy for daily use |

<br/>

**`extra_backends`** — `[]`

Additional LLM backends. Each entry needs `url`, optional `name` and `api_key`:

```json
[
  {"url": "http://ollama:11434", "name": "local"},
  {"url": "https://api.openai.com", "name": "openai", "api_key": "sk-..."}
]
```

> Max backends: **1** (trial) → **5** (earlybird/standard) → **10** (premium)

<br/>

---

### Context & Token Management

<br/>

> These control how the model's context window is divided between memory, files, and conversation.

<br/>

| Setting | Default | What It Does | When To Change |
|---------|:-------:|-------------|----------------|
| **`context_tokens`** | `8000` | Your model's total context window. **Match this to your model.** 8K model → 8000. 32K → 32000. 128K → 128000. | Always set this first — wrong value = weird behavior |
| **`reserve_tokens`** | `5000` | Tokens saved for the model's response | Increase if responses get cut off |
| **`soft_limit`** | `1500` | Preferred character limit for memory injection | Lower if memories crowd out conversation |
| **`hard_limit`** | `3000` | Absolute max memory injection characters | Safety cap — rarely needs changing |
| **`max_sys_chars`** | `1500` | Max system message length after processing | Increase for long custom system prompts |
| **`max_msg_chars`** | `600` | Max per-message summary when condensing history | Lower to save context space |
| **`recent_keep`** | `6` | Recent turns kept in full (older get summarized) | **4–8 is the sweet spot** |
| **`chars_per_token`** | `3.0` | Estimated chars per token for budget math | Most models: 2.5–4.0 |
| **`ai_short`** | `80` | AI responses shorter than this adjust extraction | Rarely needs changing |
| **`user_short_words`** | `3` | Messages under this skip extraction | Keeps "hi" and "ok" out of memories |
| **`summary_chars`** | `500` | Target length for conversation summaries | Increase for more detailed history |

<br/>

---

### Memory Settings

<br/>

| Setting | Default | What It Does | When To Change |
|---------|:-------:|-------------|----------------|
| **`mem_max_inject`** | `1800` | Total character budget for all injected memories | Increase for models with big context |
| **`mem_always_pri`** | `7` | Priority threshold for "always inject" | Lower = more memories always shown |
| **`mem_relevance_boost`** | `2` | How much relevance matters vs. raw priority | At 3+, relevant beats high-priority |
| **`mem_max_per_user`** | `500` | Max memories per user (0 = unlimited) | **200–500 for active daily users** |

<br/>

<details>
<summary><b>Per-Category Priority & Always-Inject</b> — tune what gets remembered and when</summary>

<br/>

Each category has a **priority** (1–10) and an **always-inject** flag.

| Setting | Default | What It Controls |
|---------|:-------:|-----------------|
| `mem_pri_identity` / `mem_always_identity` | **9** / ✅ | Name, age, location — forgetting a name feels broken |
| `mem_pri_communication` / `mem_always_communication` | **8** / ✅ | Response style — keeps tone consistent |
| `mem_pri_health` / `mem_always_health` | **7** / ❌ | Allergies, conditions — only when relevant |
| `mem_pri_dietary` / `mem_always_dietary` | **6** / ❌ | Food preferences — only when food is discussed |
| `mem_pri_work` / `mem_always_work` | **6** / ❌ | Job, company — only for work conversations |
| `mem_pri_family` / `mem_always_family` | **6** / ❌ | Family members — only when family comes up |
| `mem_pri_technical` / `mem_always_technical` | **5** / ❌ | Languages, tools — only for tech talk |
| `mem_pri_preference` / `mem_always_preference` | **5** / ❌ | Likes and dislikes — only when relevant |
| `mem_pri_people` / `mem_always_people` | **5** / ❌ | Other people mentioned — only when they come up |
| `mem_pri_general` / `mem_always_general` | **3** / ❌ | Everything else — only when relevant |

> [!TIP]
> **AI "forgets" something?** Find its category, raise priority or set `always` to `true`.
>
> **Drowning in irrelevant memories?** Lower priorities or set more categories to `always: false`.

</details>

<details>
<summary><b>Memory Expiration (TTL)</b></summary>

<br/>

| Setting | Default | Meaning |
|---------|:-------:|---------|
| `mem_ttl_people` | **30** | Memories about others expire after 30 days |
| `mem_ttl_general` | **0** | General memories never expire (0 = forever) |
| `mem_ttl_uploaded` | **90** | File-sourced memories expire after 90 days |
| `mem_ttl_temporary` | **7** | Situational memories expire after 7 days |

Set to `0` to disable expiration. Lower if memory gets cluttered.

</details>

<br/>

---

### File Upload & RAG

<br/>

| Setting | Default | What It Does | When To Change |
|---------|:-------:|-------------|----------------|
| **`upload_max_mb`** | `100` | Max single file size (MB) | Raise for large files |
| **`upload_max_files_per_user`** | `50` | Max files per user | Prevents disk filling |
| **`upload_max_bytes_per_user`** | `500` | Total storage per user (MB) | Adjust per your disk space |
| **`upload_chunk_size`** | `400` | Text chunk size (KB) for retrieval | **300–500 is the sweet spot** |
| **`upload_max_chunks`** | `50` | Max chunks per file | Content past this is truncated |
| **`file_inject_budget`** | `4000` | Max chars of file content per request | Increase for large context models |
| **`file_inject_max`** | `3` | Max files injected per request | Increase if model handles more context |
| **`file_budget_dynamic`** | `true` | Auto-adapt budget to available space | **Leave on** |
| **`file_budget_pct`** | `0.40` | % of remaining context for files | Higher = more file content |
| **`file_budget_safety_margin`** | `500` | Buffer to prevent context overflow | Rarely needs changing |
| **`allow_query_param_token`** | `false` | Allow `?token=xxx` in URLs | Less secure — leave off unless needed |

<br/>

<details>
<summary><b>Semantic File Search</b> (optional)</summary>

<br/>

| Setting | Default | What It Does |
|---------|---------|-------------|
| **`file_embedding_enabled`** | `false` | FAISS semantic search — meaning-based matching on top of keywords |
| **`file_embedding_model`** | `"BAAI/bge-base-en-v1.5"` | Embedding model — default is a solid balance |
| **`file_embedding_chunk_size`** | `512` | Chunk size for embeddings specifically |
| **`file_embedding_topk`** | `5` | Top-k matches to consider |
| **`file_embedding_threshold`** | `0.35` | Min similarity score. **0.3–0.5 typical** |
| **`embedding_gpu`** | `"auto"` | `auto` / `always` / `never` |

</details>

<br/>

---

### Security & Authentication

<br/>

| Setting | Default | What It Does |
|---------|---------|-------------|
| **`security_mode`** | `"auto"` | `auto` (recommended) / `local_only` / `open` (behind your own auth) |
| **`trusted_proxies`** | `"127.0.0.1,::1"` | IPs of trusted reverse proxies. Add nginx/Cloudflare IPs here |
| **`dash_token_custom`** | `""` | Your own dashboard token. Empty = auto-generated |
| **`dashboard_password`** | `""` | Optional password gate (in addition to token) |
| **`protect_read_endpoints`** | `true` | Require auth for read-only endpoints |
| **`log_security_events`** | `true` | Log failed auth, suspicious requests. **Leave on** |
| **`maintenance_mode`** | `false` | Reject all writes. Use during backups |
| **`identity_mode`** | `"strict"` | `strict` / `required` / `quarantine` / `legacy` |
| **`security_profile`** | `"cloudflare_strict"` | Security preset. Most secure by default |
| **`trust_owui_headers`** | `"auto"` | Trust OWUI identity headers. `auto` / `always` / `never` |
| **`owui_hmac_secret`** | `""` | HMAC secret for cryptographic header verification |
| **`strict_memory_isolation`** | `true` | Block anon/quarantined from memory ops. **Leave on** |
| **`identity_source_priority`** | `"owui_header,custom_header,api_token,api_payload,ip_fallback"` | Identity check order |

<br/>

<details>
<summary><b>Rate Limiting</b></summary>

<br/>

| Setting | Default | What It Does |
|---------|:-------:|-------------|
| `rate_limit_rpm` | **60** | Max requests/minute per user |
| `rate_limit_burst` | **10** | Burst allowance above limit |
| `max_queue_depth` | **20** | Max queued requests |
| `stale_request_timeout` | **30** | Seconds before queued request is dropped |

</details>

<br/>

---

### Registration & Invites

<br/>

| Setting | Default | What It Does |
|---------|:-------:|-------------|
| **`registration_enabled`** | `false` | Allow self-registration |
| **`registration_require_invite`** | `true` | Require invite code |
| **`registration_default_role`** | `"user"` | Role for new users. `user` or `viewer` |

<br/>

---

### SillyTavern Integration

<br/>

| Setting | Default | What It Does |
|---------|---------|-------------|
| **`st_enabled`** | `true` | Detect SillyTavern headers |
| **`st_auto_create_users`** | `true` | Auto-create accounts for ST users |
| **`st_header_name`** | `"x-st-user"` | Header with ST username |
| **`st_user_prefix`** | `"st:"` | Prefix to avoid ID collisions |
| **`st_default_role`** | `"user"` | Default role for ST users |

<br/>

---

### NLP & Extraction

<br/>

| Setting | Default | What It Does |
|---------|---------|-------------|
| **`use_spacy`** | `true` | Use spaCy for extraction. Falls back to regex if unavailable |
| **`nlp_mode`** | `"auto"` | See modes below |
| **`use_gpu`** | `"auto"` | GPU for spaCy: `auto` / `always` / `never` |

<br/>

| NLP Mode | Quality | Speed | Needs |
|----------|:-------:|:-----:|-------|
| `auto` | Best available | Auto | Whatever's installed |
| `spacy_trf` | ⭐⭐⭐ | Slow (fast w/ GPU) | Transformer model |
| `full_spacy` | ⭐⭐ | Fast | Standard model |
| `spacy_lite` | ⭐ | Very fast | Small model |
| `regex_only` | Basic | Instant | Nothing extra |

<br/>

---

### Auto-Model Routing

<br/>

| Setting | Default | What It Does |
|---------|---------|-------------|
| **`auto_model_enabled`** | `true` | Auto-select model by complexity |
| **`auto_tier_fast`** | `""` | Model for quick requests. Empty = disabled |
| **`auto_tier_balanced`** | `""` | Model for typical conversations |
| **`auto_tier_smart`** | `""` | Model for complex reasoning |

<br/>

---

### Agent Settings

<br/>

| Setting | Default | What It Does | When To Change |
|---------|:-------:|-------------|----------------|
| **`agent_enabled`** | `false` | Enable agent framework | Turn on for tool-using tasks |
| **`agent_auto_detect`** | `true` | Auto-trigger on coding/research tasks | Off = must be explicit |
| **`agent_max_iterations`** | `10` | Max loop iterations | Complex coding: 15–25 |
| **`agent_timeout_seconds`** | `120` | Hard timeout (seconds) | Increase for big tasks |
| **`agent_tools`** | *(all)* | Comma-separated enabled tools | Restrict for safety |
| **`agent_model_override`** | `""` | Force specific model for agents | Use your best model here |
| **`agent_sub_agents_enabled`** | `true` | Allow sub-agent spawning | Powerful but uses more compute |
| **`agent_max_sub_agents`** | `3` | Max parallel sub-agents | Higher = more parallelism |

<br/>

---

### Open WebUI Integration

<br/>

| Setting | Default | What It Does |
|---------|---------|-------------|
| **`auto_create_owui_users`** | `true` | Auto-create accounts for new OWUI users |
| **`owui_base_url`** | `""` | OWUI URL for connectivity testing |

<br/>

---

### UI & Behavior

<br/>

| Setting | Default | What It Does |
|---------|:-------:|-------------|
| **`enable_tui`** | `true` | Show terminal UI. `false` for cleaner headless output |
| **`greet_new_users`** | `true` | Store welcome greeting for new users |

<br/>

---

### Development & Experimental

<br/>

| Setting | Default | What It Does |
|---------|:-------:|-------------|
| **`dev_mode_enabled`** | `false` | Debug endpoints. **Don't enable in production** |
| **`experimental_file_tools`** | `false` | Experimental features. May be unstable |

<br/>

---

### Remote Access Settings

<br/>

| Setting | Default | What It Does |
|---------|---------|-------------|
| **`cf_tunnel_token`** | `""` | Cloudflare Tunnel token (set via dashboard) |
| **`ts_authkey`** | `""` | Tailscale auth key (set via dashboard) |
| **`ts_hostname`** | `""` | Custom Tailscale hostname |

<br/>

---

### Performance Tuning

<br/>

> These are **environment variables**, not config.json settings.

<br/>

| Variable | Default | What To Know |
|----------|---------|-------------|
| `THREAD_POOL_SIZE` | `min(8, cpu+2)` | Main thread pool. Increase on powerful servers |
| `EXTRACT_POOL_SIZE` | `pool_size // 2` | Memory extraction threads |
| `GC_EVERY_REQUESTS` | `200` | Garbage collection frequency. Lower = less RAM, more CPU |
| `POOL_RECYCLE_REQUESTS` | `500` | DB connection recycling interval |
| `WORKERS` | `1` | Uvicorn workers. >1 needs care with SQLite |

<br/>

<div align="right">
<a href="#-guide">Back to top ↑</a>
</div>

---

<br/>

## 💳 Licensing & Tiers

<br/>

UPtrim works immediately with a **free developer key** — no sign-up, no credit card. Hit a limit? Paid tiers remove caps and unlock advanced features.

<br/>

### Feature Comparison

<br/>

| | <img src="https://img.shields.io/badge/Trial-Free-gray?style=flat-square" /> | <img src="https://img.shields.io/badge/Earlybird-$40%2Fyr-0080ff?style=flat-square" /> | <img src="https://img.shields.io/badge/Standard-$100%2Fyr-8b5cf6?style=flat-square" /> | <img src="https://img.shields.io/badge/Premium-$200%2Fyr-f59e0b?style=flat-square" /> |
|:--|:--:|:--:|:--:|:--:|
| **Memories / user** | 30 | ∞ | ∞ | ∞ |
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

<br/>

### How to Activate

<br/>

<table>
<tr>
<td width="33%" valign="top" align="center">

**At Startup**

Enter your key when prompted:
```
XXXXX-XXXXX-XXXXX-XXXXX
```

</td>
<td width="33%" valign="top" align="center">

**From Dashboard**

Settings → License → Enter Key → Activate

</td>
<td width="33%" valign="top" align="center">

**Via API**

```bash
POST /api/license/activate
Authorization: Bearer TOKEN
{"key": "XXXXX-XXXXX-..."}
```

</td>
</tr>
</table>

<br/>

> [!NOTE]
> Licenses work **offline for up to 14 days** using cached validation.

<br/>

<div align="right">
<a href="#-guide">Back to top ↑</a>
</div>

---

<br/>

## 🔧 Troubleshooting

<br/>

<details>
<summary><b>"Cannot connect to upstream"</b></summary>

<br/>

Your LLM backend isn't reachable.

- **Is it running?** Try accessing its URL directly
- **Check `upstream` setting** — does it match where your backend actually is?
- **Different machine?** Check firewalls aren't blocking the port
- **Docker?** Use the container name or host IP, not `localhost`

</details>

<details>
<summary><b>Memories aren't being created</b></summary>

<br/>

- **Short messages** (under 3 words) skip extraction — nothing useful to extract
- **Check NLP status** in dashboard — `regex_only` means spaCy isn't loaded
- **Memory cap hit** — check `mem_max_per_user`
- **Tier limit** — trial caps at 30 memories per user

</details>

<details>
<summary><b>File uploads fail</b></summary>

<br/>

- Check file size against `upload_max_mb` (default: 100 MB)
- Check total storage against `upload_max_bytes_per_user` (default: 500 MB)
- Make sure the file extension is [supported](#supported-formats)
- Check dashboard logs for the specific error

</details>

<details>
<summary><b>Lost my dashboard token</b></summary>

<br/>

1. **Check console output** from first startup
2. **Set your own** — `"dash_token_custom": "mytoken"` in config.json
3. **Regenerate** via `/api/regenerate-api-key`

</details>

<details>
<summary><b>High memory / RAM usage</b></summary>

<br/>

- Disable file embeddings: `file_embedding_enabled: false`
- Lower `mem_max_per_user`
- Reduce `THREAD_POOL_SIZE` and `EXTRACT_POOL_SIZE`
- Lower `POOL_RECYCLE_REQUESTS`

</details>

<details>
<summary><b>Wrong user getting wrong memories</b></summary>

<br/>

- Check **Dashboard → Identity Info**
- Behind a reverse proxy? Add its IP to `trusted_proxies`
- Check `trust_owui_headers` setting
- Use **Dashboard → Debug Headers** to inspect incoming headers

</details>

<details>
<summary><b>Model gives weird responses / context overflow</b></summary>

<br/>

- **#1 cause:** `context_tokens` doesn't match your actual model — fix this first
- Lower `mem_max_inject` or `hard_limit` if memories overwhelm context
- Reduce `recent_keep` for more room
- Check `reserve_tokens` leaves enough input space

</details>

<details>
<summary><b>Slow responses</b></summary>

<br/>

- Check if NLP is bottlenecking on CPU — switch from `spacy_trf` to `full_spacy`
- Reduce `file_embedding_topk` if semantic search is slow
- Check backend health — the LLM itself might be the bottleneck

</details>

<br/>

<div align="right">
<a href="#-guide">Back to top ↑</a>
</div>

---

<br/>

<div align="center">

<br/>

<img src="https://img.shields.io/badge/UPtrim_Context_Proxy-v1.0.0-0080ff?style=for-the-badge" alt="UPtrim v1.0.0" />

<br/><br/>

**Your AI forgets you. We fix that.**

<br/>

<sub>Ships as a single package. Download it, run it, and your AI never forgets again.</sub>

<br/><br/>

</div>
