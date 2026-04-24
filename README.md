# PM_Copilot
PM Copilot: A multi-agent AI assistant that generates PRDs, market sizing (TAM/SAM/SOM), user stories, and risk registers from a single product description in under 90 seconds. Built with GPT-4o, Gemini 2.0 Flash, Groq/Llama-3.3, LangChain, and Streamlit.

# 🚀 PM Copilot — Multi-Agent AI Assistant for Product Managers

> Go from a product idea to a full PRD, market analysis, user stories, and risk register — in under 90 seconds.

[[Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)]
(https://genai-copilot-kllgp4b2wyconulezh6fiw.streamlit.app/)
[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://python.org)
[![LangChain](https://img.shields.io/badge/LangChain-Orchestration-green.svg)](https://langchain.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## 🔗 Live Demo

**Try it now →** 
[https://genai-copilot-kllgp4b2wyconulezh6fiw.streamlit.app/](https://genai-copilot-kllgp4b2wyconulezh6fiw.streamlit.app/)

No login or setup required. Type a product idea and get four PM deliverables instantly.

---

## 📌 Overview

PM Copilot is a fully deployed, multi-agent AI assistant that automates the four most time-consuming Product Management deliverables:

| Deliverable | Model Used | What You Get |
|---|---|---|
| **PRD** | GPT-4o (OpenAI) | Problem statement, user personas, functional & non-functional requirements, success metrics |
| **Market Sizing** | Gemini 2.0 Flash (Google) | TAM / SAM / SOM estimates, competitive landscape, go-to-market recommendations |
| **User Stories** | Groq / Llama-3.3 | Role-based stories in standard format with acceptance criteria |
| **Risk Register** | Groq / Llama-3.3 | Technical, market, and execution risks ranked by severity with mitigations |

All four outputs are generated simultaneously from a **single natural-language product description** and can be refined through ongoing conversation.

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────┐
│                   Streamlit Chat UI                  │
│           (Input, Tabs, Session State, Export)        │
└──────────────────────┬──────────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────────┐
│              LangChain Orchestrator                  │
│     (Prompt Templates, Routing, Conversation Memory) │
└───────┬──────────────┬──────────────┬───────────────┘
        │              │              │
        ▼              ▼              ▼
   ┌─────────┐   ┌──────────┐   ┌──────────────┐
   │ GPT-4o  │   │  Gemini  │   │ Groq/Llama   │
   │  (PRD)  │   │ 2.0 Flash│   │    3.3       │
   │         │   │ (Market) │   │(Stories/Risk)│
   └─────────┘   └──────────┘   └──────────────┘
```

### Why Three Different Models?

- **GPT-4o** — Best-in-class for long-context structured document generation (PRDs).
- **Gemini 2.0 Flash** — Fast, free-tier friendly, and strong at research-style outputs (market sizing).
- **Groq / Llama-3.3** — Completely free, ultra-fast inference, and reliable at following structured templates (user stories & risk tables).

Two of the three models cost nothing, keeping the system nearly free to operate.

---

## ✨ Key Features

- **One-Shot Generation** — Describe your product idea in plain English, get four complete deliverables.
- **Multi-Agent Orchestration** — LangChain routes each task to the best-suited LLM in parallel.
- **Conversational Refinement** — Keep chatting to refine any output. No need to start over.
- **Markdown Export** — Download any deliverable as a `.md` file ready for Confluence, Notion, or GitHub.
- **Live Deployment** — Publicly accessible on Streamlit Community Cloud with zero setup.

---

## 🛠️ Tech Stack

| Layer | Technology | Role |
|---|---|---|
| Frontend | Streamlit | Chat UI, session state, tab navigation, download buttons |
| Orchestration | LangChain | Task routing, prompt templating, conversation memory |
| LLM — PRD | GPT-4o (OpenAI) | Structured PRD generation, multi-turn dialogue |
| LLM — Market | Gemini 2.0 Flash (Google) | TAM/SAM/SOM, competitive analysis, GTM strategy |
| LLM — Stories/Risk | Groq / Llama-3.3 | User stories, risk register, structured tables |
| Infrastructure | Streamlit Cloud + GitHub | Public deployment, version control, secret management |

---

## ⚡ Quick Start

### Prerequisites

- Python 3.10+
- API keys for OpenAI, Google Gemini, and Groq

### Environment Variables

Create a `.env` file in the project root with the following:

```
OPENAI_API_KEY=your_openai_key_here
GOOGLE_API_KEY=your_gemini_key_here
GROQ_API_KEY=your_groq_key_here
```

> ⚠️ **Never commit your `.env` file.** The `.gitignore` is already configured to exclude it.

---

## 📊 Sample Output

For the prompt: *"A productivity app for college students with AI study schedules"*

| Deliverable | Highlights |
|---|---|
| PRD | 4 user personas, 12 functional requirements, 5 success metrics |
| Market Analysis | TAM: $8.4B · SAM: $1.2B · SOM: $84M · 4 competitors identified |
| User Stories | 10 role-based stories across student, professor, and admin roles |
| Risk Register | 7 risks ranked High/Medium/Low with mitigation strategies |

All generated in **under 90 seconds**.

---

## 🧩 Challenges & Learnings

- **Gemini quota limits** — Free tier ran out mid-demo; added graceful fallback messaging.
- **Invisible characters in API keys** — Hidden newline characters caused silent auth failures; solved with `.strip()` on all key loads.
- **GitHub secret scanning** — Hardcoded keys in notebooks triggered push blocks; migrated all secrets to Streamlit's secrets manager.
- **LangChain import paths** — Always import from `langchain_core.messages`, not the deprecated `langchain.schema`.

---

## 🔮 Future Roadmap

- Real-time web search integration for live market data
- User authentication and saved project history
- Direct export to Jira, Notion, and Confluence
- Fine-tuned models trained on PRD-specific corpora
- Competitive battle cards and OKR generation modules

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

<p align="center">
  <b>⭐ If you found this useful, consider giving the repo a star!</b>
</p>
