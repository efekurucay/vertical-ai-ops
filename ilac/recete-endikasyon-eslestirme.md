# Reçete-Endikasyon Eşleştirme Motoru

> **Sector:** İlaç / Klinik
> **Difficulty:** Medium
> **Market Size (TR):** 75.000+ hekim, 30.000+ eczane
> **Monetization:** API (EHR, eczane yazılımı entegrasyonu)

## Problem

LLM tanı koduna göre ilaç önerisi yapabilir. Ancak önerilen ilacın **TİTCK onaylı endikasyonları, SGK geri ödeme koşulları ve off-label kullanım kurallarıyla** uyumlu olup olmadığını deterministik olarak kontrol edemez.

## The Validation Layer

- İlaç bu tanı kodu için TİTCK onaylı mı?
- SGK bu kombinasyonu (ilaç + tanı) geri ödüyor mu?
- Off-label kullanım söz konusuysa özel onay alındı mı?
- Reçete türü (kırmızı, yeşil, normal) doğru mu?
- Uzman hekime özel ilaçsa pratisyen hekim reçete yazıyor mu?

## Tech Stack

- **LLM**: GPT-4o (klinik karar destek)
- **DB**: TİTCK endikasyon veritabanı + SGK SUT
- **Kural Motoru**: Python + ICD-10 / ATC eşleştirme
- **Entegrasyon**: Medula (SGK e-reçete sistemi)

## Business Model

- **Target**: EHR yazılım şirketleri, eczane zinciri yazılımları
- **Pricing**: Kullanıcı başına API lisansı
- **Argüman**: SGK ceza ve geri ödeme reddi riskini azaltır

## Turkey Context

- SGK Medula sistemi e-reçete zorunluluğu
- SUT (Sağlık Uygulama Tebliği) geri ödeme kriterleri

## Getting Started

1. SGK SUT ilaç listesini ve koşullarını JSON'a aktar
2. ICD-10 tanı kodu + ATC kodu eşleştirme matrisi oluştur
3. Reçete girişinde otomatik kontrol çalıştır

## Resources

- [SGK SUT](https://www.sgk.gov.tr)
- [TİTCK](https://www.titck.gov.tr)
