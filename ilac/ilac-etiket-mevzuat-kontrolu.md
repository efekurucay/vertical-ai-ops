# İlaç Etiket Mevzuat Kontrolü

> **Sector:** İlaç / Regülatif
> **Difficulty:** Medium
> **Market Size (TR):** 300+ ilaç üreticisi/ithalatçısı
> **Monetization:** B2B SaaS

## Problem

LLM ilaç kutusu etiketi ve kullanma kılavuzu taslağı oluşturabilir. Ancak bu içeriğin **TİTCK beşeri ilaç yönetmeliği, AB direktifleri ve zorunlu etiket unsurları listesiyle** tam uyumlu olup olmadığını doğrulayamaz.

## The Validation Layer

- Ruhsat numarası ve sahibi bilgisi mevcut mu?
- ATC kodu ve etken madde miktarı belirtilmiş mi?
- Kontrendikasyonlar ve uyarılar tam mı?
- Son kullanma tarihi ve seri numarası formatı doğru mu?
- Braille yazısı zorunlu mu ve var mı? (AB ihracat durumunda)
- Saklama koşulları belirtilmiş mi?
- QR kod/2D barkod gereklilik kontrol edildi mi?

## Tech Stack

- **LLM**: GPT-4o (etiket taslağı)
- **Kural Motoru**: Python + TİTCK etiket gereklilik JSON
- **Görüntü İşleme**: Tesseract OCR (mevcut etiket analizi)
- **Backend**: FastAPI

## Business Model

- **Target**: İlaç üreticileri, ithalatçıları, regülatif işler departmanları
- **Pricing**: Ürün başına veya aylık SaaS
- **Argüman**: Ruhsat başvurusu ret riskini azaltır

## Turkey Context

- TİTCK beşeri tıbbi ürünler yönetmeliği etiket gerekliliklerini belirliyor
- AB GMP sertifikası için etiket uyumu kritik

## Getting Started

1. TİTCK etiket zorunlu unsurlar listesini JSON'a aktar
2. LLM ürettiği etiketi bu listeden geçir
3. Eksik/hatalı unsurları raporla

## Resources

- [TİTCK Beşeri İlaçlar](https://www.titck.gov.tr)
