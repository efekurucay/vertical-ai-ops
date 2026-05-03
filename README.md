# vertical-ai-ops

> **Where LLMs fall short — and deterministic rule engines fill the gap.**

Large Language Models are excellent at generating plausible-sounding text. But in regulated, high-stakes industries, "plausible" isn't good enough. A contract that *looks* valid but violates a specific clause is worse than no contract at all. A drug prescription that *seems* correct but contains a contraindicated combination is dangerous.

This repository maps **100+ vertical-specific opportunities** where the real value isn't in the LLM itself — it's in the **validation layer** built around it.

---

## The Core Pattern

```
LLM (generation) + Deterministic Rule Engine (validation) = Trustworthy Output
```

This is exactly how coding agents became powerful: LLMs generate code, but the *compiler*, *linter*, and *test runner* validate it. The same pattern hasn't been replicated in most other industries — yet.

This repo is a playbook for building those validation layers.

---

## Why This Matters

In 2025, Microsoft CEO Mustafa Suleyman claimed that "almost all white-collar jobs" would be automated within 12–18 months. Most other AI leaders — including Dario Amodei (Anthropic) and Jensen Huang (Nvidia) — disagreed strongly. Huang specifically said the narrative that AI destroys jobs is "wrong and harmful."

The nuanced truth: **LLMs won't replace knowledge workers wholesale — but they will replace workflows that lack validation infrastructure.** The opportunity is to build that infrastructure sector by sector.

---

## Repository Structure

```
vertical-ai-ops/
├── README.md
├── CONTRIBUTING.md
├── template.md              ← Use this to add a new vertical
│
├── finans/
│   ├── kyc-aml-kural-motoru.md
│   ├── kredi-skoru-dogrulama.md
│   └── bddk-raporlama-dogrulama.md
│
├── saglik/
│   ├── klinik-karar-destek-motoru.md
│   └── ilac-etkilesim-kontrolu.md
│
├── hukuk/
│   ├── sozlesme-uyum-motoru.md
│   └── mahkeme-dilekce-usul-uyumu.md
│
├── insaat/
│   └── deprem-yonetmeligi-uyumu.md
│
├── yazilim/
│   ├── kvkk-gdpr-veri-isleme.md
│   └── acik-kaynak-lisans-tarayici.md
│
└── ... (more sectors coming)
```

---

## Sectors Covered (so far)

| # | Sector | Opportunity |
|---|--------|-------------|
| 1 | Finance | KYC/AML rule engine |
| 2 | Finance | Credit score validation |
| 3 | Finance | BDDK reporting format verification |
| 4 | Healthcare | Clinical decision support |
| 5 | Healthcare | Drug interaction checker |
| 6 | Law | Contract compliance engine |
| 7 | Law | Court petition procedural validation |
| 8 | Construction | Earthquake regulation (TBDY 2018) |
| 9 | Software/IT | KVKK/GDPR data processing compliance |
| 10 | Software/IT | Open-source license compatibility scanner |

> Full list of 100 opportunities: see [`opportunities.csv`](./opportunities.csv)

---

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md). Each vertical lives in its own markdown file. Use [template.md](./template.md) to add a new one.

---

## Author

**Yahya Efe Kuruçay** · AI Product Engineer · [efekurucay.com](https://www.efekurucay.com) · [@efekurucay24](https://twitter.com/efekurucay24)

> Inspired by Cal Newport's analysis of why LLM coding agents succeeded where general office automation failed — and what that means for every other industry.
