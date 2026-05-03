# Poliçe Uygunluk Kontrolü

> **Sector:** Sigorta
> **Difficulty:** Medium
> **Market Size (TR):** Tüm sigorta satış kanalları
> **Monetization:** B2B SaaS, white-label

## Problem

LLM müşteri profiline göre sigorta poliçesi önerisi yapabilir. Ancak önerilen poliçenin **SEDDK düzenlemelerine, zorunlu sigorta gerekliliklerine, sektöre özel lisans şartlarına ve müşteri risk profiline** uygun olup olmadığı doğrulanamaz.

## The Validation Layer

- Müşteri bu poliçeyi satın almaya yasal olarak uygun mu?
- Zorunlu sigorta gereklilikleri karşılanıyor mu? (trafik, DASK)
- Poliçe SEDDK onaylı ürün listesinde mi?
- Prim hesabı aktüeryal kurallara uygun mu?
- Sözleşme dili SEDDK standart kloz gerekliliklerini karşılıyor mu?

## Tech Stack

- **LLM**: GPT-4o (müşteri profili analizi)
- **Kural Motoru**: Python + SEDDK ürün onay listesi
- **DB**: Aktüeryal tablo veritabanı
- **Backend**: FastAPI

## Business Model

- **Target**: Sigorta acenteleri, online sigorta platformları
- **Pricing**: Aylık SaaS
- **Argüman**: Satış hatası riskini ve müşteri şikayetlerini azaltır

## Turkey Context

- DASK (Doğal Afet Sigortaları Kurumu) zorunlu deprem sigortası
- SEDDK poliçe standart klozları yayımlıyor

## Getting Started

1. SEDDK onaylı ürün listesini JSON'a aktar
2. Zorunlu sigorta türlerini ve şartlarını tanımla
3. LLM önerisini bu liste ve kurallara karşı kontrol et

## Resources

- [SEDDK](https://www.seddk.gov.tr)
- [DASK](https://www.dask.org.tr)
