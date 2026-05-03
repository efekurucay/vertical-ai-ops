# Elektrik Piyasası Dengeleme Kural Motoru

> **Sector:** Enerji / Elektrik Piyasası
> **Difficulty:** High
> **Market Size (TR):** 300+ piyasa katılımcısı (üretici, tedarikçi)
> **Monetization:** B2B SaaS

## Problem

LLM enerji alım-satım stratejisi önerebilir. Ancak bu stratejinin **EPDK'nın Elektrik Piyasası Yan Hizmetler Yönetmeliği, ENTSO-E grid kuralları ve TEİAŞ dengeleme mekanizması prosedürlerine** uygun olup olmadığını bilemez.

## The Validation Layer

- Gün öncesi piyasasında teklif saatleri ve formatı doğru mu?
- Yan hizmet sunumu için teknik yeterlilik koşulları sağlandı mı?
- Dengeleme sapma limitleri içinde mi?
- Fatura döngüsü ve uzlaştırma formatı TEİAŞ şartnamesine uygun mu?
- Lisans kapsamı bu işlem türüne izin veriyor mu?

## Tech Stack

- **LLM**: GPT-4o (strateji ve rapor)
- **Kural Motoru**: Python + EPDK yönetmelik JSON
- **Piyasa Verisi**: EPİAŞ API
- **Backend**: FastAPI

## Business Model

- **Target**: Enerji üreticileri, tedarikçiler, enerji yönetim şirketleri
- **Pricing**: Tesis başına aylık SaaS
- **Argüman**: EPDK cezaları ve dengeleme sapma maliyetleri

## Turkey Context

- EPİAŞ (Enerji Piyasaları İşletme A.Ş.) gün öncesi ve dengeleme piyasası API'si
- EPDK lisans gereklilikleri sıkı

## Getting Started

1. EPİAŞ API ile gün öncesi piyasa formatını öğren
2. Teklif format kurallarını JSON'a aktar
3. LLM teklifini bu kurallara göre kontrol et

## Resources

- [EPİAŞ](https://www.epias.com.tr)
- [EPDK](https://www.epdk.gov.tr)
