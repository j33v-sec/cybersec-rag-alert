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
             ┌──────────────▼────┐   ┌───────▼────────-┐
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

