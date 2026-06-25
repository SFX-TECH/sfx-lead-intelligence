# SFX Lead Intelligence Command Center

> A local-LLM command center: a semantic hub over 16 of my projects (30,000+ chunks) with a knowledge graph and an MCP server, plus a lead-intelligence dashboard with 9 AI routes. Runs entirely on my own GPU. No cloud.

![AI](https://img.shields.io/badge/AI-local%20LLM%20(Ollama)%20%C2%B7%20RAG%20%C2%B7%20MCP-7a5cff)
![Quality](https://img.shields.io/badge/chat%20quality-61%25%20%E2%86%92%2099%25-2ea44f)
![Stack](https://img.shields.io/badge/stack-Next.js%2015%20%C2%B7%20Ollama%20%C2%B7%20n8n-000000)
![Privacy](https://img.shields.io/badge/privacy-100%25%20local-2ea44f)
![License](https://img.shields.io/badge/license-proprietary-8a8a8a)

**Source is private by design** — public showcase only.

<!-- drop a screenshot of the knowledge graph or dashboard here: assets/hero.png -->

---

## What it is
Two halves of one local-LLM workbench I built to run my own company on:

**1. Context Hub** — a semantic index over **16 of my projects (30,000+ chunks)** with a force-directed **knowledge graph** and an **MCP server**, so any AI agent (or I) can search, ask questions across, and reason over my entire body of work. Fully local embeddings; nothing leaves the machine.

**2. Lead Intelligence Dashboard** — a command-center UI over scanned Southwest-Florida business leads (fed by an upstream n8n pipeline), with **9 local-LLM AI routes** spanning research, outreach drafting, and sales preparation.

## The part I'm proudest of: a ground-truth eval harness
Anyone can make an LLM answer. The hard problem is knowing whether the answer is *right*, at scale, without reading every one by hand. I built a **ground-truth evaluation harness** that grades the system's answers across 20+ query types, which **lifted chat quality from 61% to 99%** and catches regressions before they ship.

## How it's built
```mermaid
flowchart LR
    P["16 projects · 30k+ chunks"] --> EMB["Local embeddings + index"]
    LEADS["Scanned SWFL leads<br/>(n8n pipeline → Sheet)"] --> DASH
    EMB --> HUB["Context Hub:<br/>semantic search · Q&A · knowledge graph · MCP"]
    EMB --> DASH["Lead dashboard:<br/>9 local-LLM AI routes"]
    HUB --> EVAL["Ground-truth eval harness<br/>(61% → 99%, gates releases)"]
    DASH --> EVAL
```

## Tech
| Layer | Stack |
|---|---|
| App | Next.js 15 (App Router, TypeScript) |
| Local LLM | Ollama (qwen3) + nomic-embed — on-GPU, offline |
| Retrieval | Semantic index (RAG) + force-directed knowledge graph |
| Interop | Model Context Protocol (MCP) server |
| Upstream | n8n lead-generation pipeline → Google Sheets |
| Quality | Custom ground-truth evaluation harness (20+ query types) |

## Status
In production (internal) — it's the system I use daily to search my projects and run SFX Tech's lead intelligence.

---

Built by **Jesse Jolly** · [SFX Tech Innovation](https://sfxtechinnovation.com) · [LinkedIn](https://linkedin.com/in/jessegjolly)

*Source code is private and proprietary. This repository showcases the product and its architecture only.*
