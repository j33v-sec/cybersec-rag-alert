# CyberSec RAG Alert: AI-Powered Cybersecurity Advisory Watcher
A smart, local-first cybersecurity advisory monitoring system that scrapes, analyzes, ranks, and alerts you of critical threats — powered by open-source LLMs, FAISS vector search, and automated scheduling.

# Project Overview
CyberSec RAG Alert is a Python-based automation tool designed to help security engineers and analysts:
- Automatically track cybersecurity advisories from Cybersecurity websites
- Analyze and summarize advisories using a local LLM (like Phi-2 or Mistral)
- Use RAG (Retrieval-Augmented Generation) and FAISS vector search to prioritize and contextualize alerts
- Alert users on a daily/weekly basis via email or terminal

                    ┌────────────────────────────┐
                    │CyberSecurity.my Advisories │
                    └────────────┬───────────────┘
                                 │
                        [1] Web Scraper
                                 ↓
                    ┌────────────────────────────┐
                    │   Advisory JSON Storage    │
                    └────────────┬───────────────┘
                                 │
                ┌─────────────────────────────────────┐
                │ [2] Embed Advisories into Vectors   │
                │     using Sentence Transformers     │
                └────────────┬───────────────┬────────┘
                             │               │
             ┌──────────────-▼───┐   ┌───────▼────────-┐
             │  FAISS Vector DB  │   │   User Query    │
             └──────────────┬────┘   └───────┬─────────┘
                            │                │
             ┌──────────────▼────────────────▼─────────┐
             │   RAG Prompt Builder (Prompt + Docs)    │
             └──────────────┬──────────────────────────┘
                            ↓
                  [3] Local Language Model
                            ↓
                 Smart Alert or Summary Output
                            ↓
                    🔔 Email / CLI / Log

# Technical Components

| Area                         | Tool/Library                          | Purpose                               |
| ---------------------------- | ------------------------------------- | ------------------------------------- |
| Web Scraping                 | `requests`, `BeautifulSoup`           | Extract advisory content              |
| Embedding Model              | `sentence-transformers`               | Convert advisories into vector form   |
| Vector Search                | `FAISS`                               | Perform semantic similarity search    |
| Local LLM                    | `transformers` + `Phi-2` or `Mistral` | Generate smart summaries and rankings |
| RAG Architecture             | Custom Python                         | Retrieve + augment + generate         |
| Alerting                     | `smtplib` / `terminal` / `Slack API`  | Notify users                          |
| Scheduling                   | `cron` or `APScheduler`               | Automate daily/weekly runs            |
| Model Fine-tuning (Optional) | `PEFT`, `LoRA`, `datasets`            | Learn from user feedback (planned)    |

# Features

- Scrapes the latest security advisories
- Uses vector similarity search to retrieve relevant threats
- Ranks and filters "important" advisories using custom rules + AI
- Summarizes using a local, offline AI model (no cloud dependency)
- Sends alerts or displays summaries via CLI/email
- Easily extensible to other advisory sources (e.g., NIST, NVD, CISA)

# Why This Project Matters

- Security Use Case: Helps you monitor threat intelligence more intelligently.
- AI Skills: Shows practical LLM integration using RAG and vector DBs.
- Infra Awareness: Demonstrates end-to-end design from data ingestion to delivery.
- Open Source First: Respects privacy and works offline.

# Future Enhancements

- Auto-feedback learning loop (user-labeled important advisories)
- Fine-tuning with LoRA
- Web dashboard (Streamlit)
- Slack or Teams alert integration
- Multi-source ingestion (CISA, NIST, etc.)
