<p align="center">
  <img src="https://mcp.com.ai/img/mcp-products/orca/orca-logo-trans.png" alt="OrcA — Orchestrator for APIs and Agents" width="360">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/MCP-Model%20Context%20Protocol-1193b0?style=for-the-badge" />
  <img src="https://img.shields.io/badge/OpenAPI-OrcA%20for%20MCP-da7756?style=for-the-badge" />
</p>

<h1 align="center">OrcA — OpenAPI & Arazzo to MCP Server, inside VS Code</h1>

<p align="center">
  <b>Be HAPI. Build Once. Deploy Everywhere. Discover Globally.</b><br/>
  Self-host, deploy, and register MCP servers with confidence using HAPI CLI, Docker, or Cloudflare Workers.
</p>

<p align="center">
  <a href="https://mcp.com.ai"><b>Website</b></a>
  ·
  <a href="https://docs.mcp.com.ai"><b>Docs</b></a>
  ·
  <a href="https://orca.mcp.com.ai"><b>OrcA for MCP</b></a>  
  ·
  <a href="https://run.mcp.com.ai"><b>Run MCP</b></a>
  ·
  <a href="https://hapi.mcp.com.ai"><b>HAPI CLI</b></a>
</p>

---

## Orchestrator for APIs and Agents for MCP

It bridges the gap between your API contracts and MCP servers, all within VS Code.

**Turn any OpenAPI (Swagger) or Arazzo contract into a running MCP server, without leaving your editor.** OrcA finds your API contracts, lets you explore them, previews the exact MCP tools an AI agent will get, runs them locally, and deploys them. It is powered by [HAPI](https://docs.mcp.com.ai), the headless API engine of the HAPI MCP Stack.

> **API contract in, MCP tools out.** No glue code, no SDK, no context switching between editor, terminal, browser and docs.

---

## 🆕 New in 0.3: see everything your agent does with your MCP servers

**Stop guessing why your agent called the wrong tool.** OrcA 0.3 turns VS Code into an MCP traffic analyzer and a chat playground for your own servers: every LLM round, every tool call, every byte, on one screen.

<p align="center">
  <img src="https://mcp.com.ai/animations/orca/orca-0.3-traffic-analysis.gif" alt="OrcA 0.3: chat with your MCP servers and watch every LLM round and tool call in the OrcA Traffic graph" width="900">
</p>

- 📡 **MCP Traffic, as a Git graph.** Every JSON-RPC message and LLM round in one live timeline. See which model round triggered which tool calls, on which server, how long each took, and what it cost. Filter, search payloads, diff two calls, **Copy as cURL**, and **Replay** in one click.
- 💬 **Chat with your MCP servers.** Connect any running server and ask questions in the new **OrcA** sidebar. Use **GitHub Copilot's models with no API key**, or OpenAI, Anthropic, Groq, OpenRouter, Ollama, LM Studio. Risky tools ask before they run.
- ⇄ **Watch Copilot, Claude & co.** Put any server behind OrcA's local capture proxy and see exactly what *other* AI clients send it. No code changes, no extra tools.
- 🎯 **From a tool call to the line in your spec.** Jump from any frame or tool straight to the OpenAPI operation or Arazzo workflow behind it.
- 🔒 **Private by design.** No telemetry, no vendor SDKs. Secrets are redacted, keys live in VS Code's secret storage, and nothing is written to disk unless you save a session.

> **Try it in 30 seconds:** open an OpenAPI file → **Run with HAPI** → right-click the server in **MCP Servers** → **Connect** → open **OrcA › Chat** and ask a question → **OrcA: Show Traffic**.

---

## Why OrcA?

Your API contracts live in your IDE. Your MCP servers live somewhere else. Every change means switching between the editor, a terminal, a browser console and the docs, and hoping they still agree.

OrcA puts the whole loop in one place:

| Without OrcA | With OrcA |
| --- | --- |
| Hand-write MCP tool wrappers for every endpoint | Every OpenAPI operation becomes an MCP tool automatically |
| Guess what tools an agent will see | **Dry Run** shows the exact MCP `tools/list` before you ship |
| Terminal scripts to start a server | **Run with HAPI**: one click, from the editor title bar |
| Separate dashboards to deploy and monitor | **Deploy** and manage MCP servers from the sidebar |
| Multi-step API calls left to the LLM to improvise | **Arazzo workflows** run as one deterministic MCP tool |
| Debug agents with `console.log` and guesswork | **OrcA Traffic** shows every LLM round and tool call, with timing, tokens and cost |
| A separate inspector app to try your MCP tools | **Chat** with your servers right in VS Code, with the model you already use |
| No idea what Copilot sends to your server | The **capture proxy** records every request from any MCP client |

---

![OrcA MCP explainer](https://mcp.com.ai/img/mcp-products/orca/orca-explainer.gif)

## Features

### 🔎 Contracts: every OpenAPI and Arazzo file, found for you
OrcA recognizes contracts by their **content** (`openapi: 3.x`, `arazzo: 1.1`), not only by their file names. It groups them by where they live:
- **Workspace**: the folders you have open.
- **HAPI Home**: your personal spec library (`~/.hapi/specs`).

Start a new contract from a clean **OpenAPI 3.1** or **Arazzo 1.1** template with **New Contract…**. **Filter Contracts…** finds one by file name, title or description as you type.

### 🧭 Outline that follows your file
Open any contract and the **Outline** mirrors it:
- **OpenAPI / Swagger:** paths → operations (colored by HTTP method), schemas and properties, security schemes, servers, tags, and `x-hapi` metadata.
- **Arazzo:** source descriptions, workflows → steps, success criteria, outputs and components.

Click any node to jump to its **exact line**, even in large specs. You can add or remove Arazzo sources, workflows and steps from the tree, and undo the change.

### 🧪 Dry Run: see the MCP tools before you serve them
Preview what an AI agent will get, in the format you need:
- **JSON:** a ChatGPT App submission dump, ready to complete.
- **Markdown:** an AI-agent **system prompt** template built from your tools.
- **YAML** or a readable **table**.

The result opens beside your contract. Nothing is started, and nothing is deployed.

### ▶️ Run with HAPI: a local MCP server in one click
Run `hapi serve` for any OpenAPI or Arazzo contract in an integrated terminal. **Run with Options…** adds headless (MCP-only) mode, development mode (hot reload), or a custom port. Paths with spaces are handled on Linux, macOS and Windows.

### ☁️ Deploy and manage MCP servers
- **Deploy MCP Server** from any OpenAPI contract: just name the server. Your HAPI profile decides where it runs and on which plan.
- **MCP Servers** view: running and stopped servers, with start, stop, restart, logs, open in browser, and delete.
- **Add to VS Code**: register a running server in `.vscode/mcp.json` with one click, so Copilot, Claude and other MCP clients in VS Code can use it right away.

### 💬 Chat with your MCP servers
The **OrcA** view in the Secondary Sidebar has a **Chat** tab. Connect servers in **MCP Servers**, pick a model (VS Code language models need no key; OpenAI, Anthropic, Groq, OpenRouter, Ollama, LM Studio and any OpenAI-compatible endpoint work too), and ask. Every tool call shows up as a card with arguments, latency and size; tools that can change data ask first (**Allow Once**, **Allow for This Session**, **Deny**). Each answer ends with a summary of tools, tokens, time and cost.

### 📡 Traffic analysis
**OrcA Traffic** (bottom Panel, or an editor tab) records every JSON-RPC message and every LLM round, drawn as a Git-style graph: a chat round forks to the tool calls it caused and merges back into the next round. Filter and search, compare two calls in the native diff editor, **Copy as cURL**, **Replay** (with a guard for mutating tools), jump to the **operation in your contract**, and save a session to `.orca-traffic.json`.

### 🌐 Any MCP server, not only HAPI ones
Already running an MCP server you wrote by hand? **Add External MCP Server…** (a name, a URL, optional headers) or **Import MCP Servers…** from `.vscode/mcp.json`, and it gets the same chat, traffic analysis, proxy and catalog as HAPI servers. OrcA connects to **Streamable HTTP** servers.

**Generate Contract** then infers an **OpenAPI 3.1 contract from the server's live catalog**, deterministically: every tool becomes an operation, so **Open Operation in Contract**, the Outline, search and **Dry Run** work for hand-written servers too. **Regenerate Contract** shows exactly what changed on the server since, in a diff.

### ⇄ Capture any MCP client
**Expose via Proxy** puts a server behind `http://127.0.0.1:7331/mcp/<server>`, and **Add to VS Code › Through OrcA** registers that address, so you can watch what Copilot, Claude or any other client sends. Streams pass through untouched; OAuth servers are not proxied yet.

### 🏠 HAPI Home
Browse the folders the `hapi` CLI uses (`specs`, `config`, `plugins`, `logs`, `certs`) and run, dry-run or deploy the specs stored there. Private keys are never previewed without your confirmation.

### ✅ Arazzo workflow authoring
Arazzo 1.1 schema validation in the **Problems** panel, **Validate All** across your workspace, export to JSON or YAML, and custom deployment hooks.

### 🔔 Activity, status and guidance
- **Activity** tab of the OrcA view (Secondary Sidebar): server events and failed calls, linked to their traffic frames.
- **Status bar:** your HAPI session and mode (`local` or `remote`).
- **OrcA Guide:** an animated tour plus built-in docs, available offline.
- **Get started with OrcA:** a walkthrough on the VS Code Welcome page.

---

## How to

**Turn an OpenAPI spec into MCP tools in 60 seconds**
1. Open your `openapi.yaml` (or create one with **OrcA: New Contract…**).
2. Click **Dry Run** in the editor title bar and choose **Table** to see the MCP tools.
3. Click **Run with HAPI**. Your MCP server is now running on `http://localhost:3000/mcp`.
4. In **MCP Servers**, use **Add to VS Code** to connect it to your AI assistant.

**Generate an AI-agent system prompt from an API**
Run **Dry Run → Markdown**. You get a prompt template with every tool already listed; complete the role and policies with your favorite coding agent.

**Prepare a ChatGPT App submission**
Run **Dry Run → JSON**. The tool names, descriptions and read-only/destructive hints are filled in from your contract.

**See exactly what your agent sends to your MCP server**
Right-click the running server › **Expose via Proxy**, then **Add to VS Code › Through OrcA**. Use Copilot as usual and watch **OrcA Traffic**: each call, its latency, size and payload.

**Chat with your API before wiring an agent**
**Connect** the server, open **OrcA › Chat**, choose a model, and ask. Tool calls, tokens and cost are shown per turn.

**Document a hand-written MCP server in one click**
**Add External MCP Server…** → **Connect** → right-click → **Generate Contract**. You get an OpenAPI 3.1 file with every tool, its input and output schemas, and annotations; regenerate later to spot catalog drift.

**Orchestrate multiple API calls deterministically**
Create an **Arazzo workflow** (**New Contract… → Arazzo Workflow**), describe the steps, and run it with HAPI. The whole workflow is exposed as a single MCP tool.

---

## Requirements

- **VS Code 1.138** or newer (Windows, macOS, Linux, WSL, SSH and Dev Containers).
- The [**HAPI CLI**](https://hapi.mcp.com.ai) for Run and Dry Run. Don't have it? OrcA offers to install it in one click (**OrcA: Install HAPI CLI**).

## Privacy

OrcA has **no telemetry**. In the default **local** mode, OrcA makes no calls to the HAPI API; your contracts and servers stay on your machine. It connects to MCP servers only when you ask, and to an LLM only when you chat, using only the provider you chose. Traffic stays in memory, with secrets redacted, and is written to disk only when you save a session. **Remote** mode talks only to the HAPI API you configure. Sign-in tokens, API keys and server headers are kept in VS Code's secret storage.

## Frequently asked questions

**Does OrcA support Swagger 2.0?**
OrcA works with **OpenAPI 3.x**. Convert Swagger 2.0 documents to OpenAPI 3 first; OrcA tells you when a file is Swagger 2.0.

**Can OrcA connect to MCP servers that HAPI did not create?**
Yes. Add them as **external** servers (or import them from `.vscode/mcp.json`). OrcA supports Streamable HTTP servers; stdio and legacy SSE servers are listed as not supported.

**What is Arazzo?**
[Arazzo](https://spec.openapis.org/arazzo/latest.html) is the OpenAPI Initiative's specification for describing sequences of API calls (workflows). OrcA writes and validates **Arazzo 1.1**.

**Does OrcA send my data anywhere?**
No. There is no analytics or telemetry code. The chat talks only to the provider you selected (or to VS Code's own models), and traffic never leaves your machine unless you save and share a session file.

**Which MCP clients can use the servers?**
Any client that speaks the Model Context Protocol over HTTP, including VS Code (GitHub Copilot), Claude, ChatGPT Apps, and your own agents.

---

## Learn more

- 📘 [HAPI MCP documentation](https://docs.mcp.com.ai)
- 🌐 [MCP.com.ai](https://mcp.com.ai)
- 🎥 [La Rebelion Labs on YouTube](https://www.youtube.com/@larebelionlabs)
- 📰 [Newsletter](https://rebelion.la/newsletter)

**OrcA** is part of the **HAPI MCP Stack** by [La Rebelion Labs](https://rebelion.la). *Be HAPI, and enjoy building!*
