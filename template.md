# [Opportunity Title]

> **Sector:** [e.g., Finance / Healthcare / Law]  
> **Difficulty:** [Low / Medium / High]  
> **Market Size (TR):** [estimate]  
> **Monetization:** [B2B SaaS / API / Consulting / Other]

---

## Problem

*Why does the LLM fall short here? What specifically goes wrong when you let the model generate output without validation?*

---

## The Validation Layer

*What does the rule engine check? Where do the rules come from (which regulation/standard/protocol)? How does it communicate errors back to the LLM or user?*

```
Input → LLM (draft generation) → Rule Engine (validation) → Output or Error
```

---

## Technical Architecture

*Stack, data sources, integration points.*

```
[LLM] ──► [Parser] ──► [Rule Engine] ──► [Result]
               ▲              │
          [Regulation DB] ◄───┘
```

---

## Tech Stack

- **LLM**: e.g., GPT-4o, Claude 3.5, local Llama via Ollama
- **Rule Engine**: e.g., custom Python, Drools, OPA
- **Data Sources**: e.g., official regulation PDFs, government APIs
- **Frontend**: e.g., Next.js
- **Backend**: e.g., FastAPI / Node.js

---

## Business Model

*Who pays? How much? Why now?*

- **Target customer**: 
- **Pricing model**: 
- **Why they'll pay**: 
- **Sales motion**: 

---

## Turkey Context

*Local regulation, market conditions, existing players, funding opportunities (TÜBİTAK 1507/BIGG etc.)*

---

## Getting Started (MVP in a Weekend)

1. Step one
2. Step two
3. Step three

---

## Resources

- [Relevant regulation or standard link]()
- [Related library or tool]()
