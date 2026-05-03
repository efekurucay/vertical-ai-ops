# Portföy Risk Limiti Kontrolü

> **Sector:** Finans / Portföy Yönetimi
> **Difficulty:** High
> **Market Size (TR):** 70+ portföy yönetim şirketi, yatırım fonları
> **Monetization:** B2B SaaS, API

## Problem

LLM portföy optimizasyon önerileri yapabilir. Ancak önerilen ağırlıkların **SPK'nın yatırım fonu tebliğlerinde belirlenen konsantrasyon limitlerine, tek varlık üst sınırlarına, kaldıraç limitine ve likidite gerekliliklerine** uygun olup olmadığını bilemez.

## The Validation Layer

- Tek varlıktaki ağırlık SPK limitini aşıyor mu? (%10 kuralı)
- Yabancı varlık oranı fon türüne göre belirlenen limiti aşıyor mu?
- Kaldıraç oranı yasal sınırda mı?
- Portföy VaR (Value at Risk) limiti dahilinde mi?
- Likidite: T+2 çözümlenebilir varlık oranı yeterli mi?

## Tech Stack

- **LLM**: GPT-4o (portföy analizi ve önerisi)
- **Kural Motoru**: Python + SPK tebliğ JSON kuralları
- **Risk Hesaplama**: numpy/scipy (VaR, korelasyon)
- **Veri**: MKK API, Borsa İstanbul API

## Business Model

- **Target**: Portföy yönetim şirketleri, yatırım fonları, varlık yöneticileri
- **Pricing**: AUM bazlı yıllık lisans
- **Argüman**: SPK denetim cezaları ve lisans iptali riski

## Turkey Context

- SPK III-52.1 Tebliği yatırım fonu portföy sınırlamalarını düzenliyor
- MKK (Merkezi Kayıt Kuruluşu) API portföy verisi sağlıyor

## Getting Started

1. SPK III-52.1 Tebliği'nden limit tablosunu JSON'a aktar
2. Python ile portföy ağırlık kontrolü yaz
3. LLM önerisini bu limitlerle test et

## Resources

- [SPK Tebliğler](https://www.spk.gov.tr)
- [MKK](https://www.mkk.com.tr)
