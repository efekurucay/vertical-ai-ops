# Hasta Taburculuk Uygunluğu Değerlendirmesi

> **Sector:** Sağlık / Hastane Yönetimi
> **Difficulty:** Medium
> **Market Size (TR):** 1.500+ hastane
> **Monetization:** B2B SaaS (hastane bilgi sistemleri)

## Problem

LLM hasta verilerini analiz edip taburculuk önerisi yapabilir. Ancak bu önerinin **klinik taburculuk kriterlerine, SGK yatış süresi limitlerinin aşılıp aşılmadığına ve hasta güvenliği protokollerine** uygun olup olmadığını doğrulayamaz.

## The Validation Layer

- Vital bulgular taburculuk eşiklerini karşılıyor mu? (ateş < 38°C, SpO2 > 94%)
- SGK DRG koduna göre ortalama yatış süresi aşıldı mı?
- Taburculuk sonrası bakım planı oluşturulmuş mu?
- Kontrol randevusu verilmiş mi?
- İlaç eğitimi tamamlandı mı?
- Yüksek düşme riski olan hasta için güvenlik önlemleri alındı mı?

## Tech Stack

- **LLM**: GPT-4o (klinik özet)
- **Kural Motoru**: Python + klinik protokol JSON
- **Veri**: HBS (Hastane Bilgi Sistemi) entegrasyonu
- **SGK**: DRG ve SUT veritabanı

## Business Model

- **Target**: Özel hastaneler, hastane zincirleri
- **Pricing**: Yatak başına aylık SaaS
- **Argüman**: Gereksiz yatışı azaltır, SGK fatura uyumsuzluğunu önler

## Turkey Context

- SGK DRG (Tanı İlişkili Gruplar) yatış süresi ve ödeme kriterleri
- Sağlık Bakanlığı Kalite Standartları (SKS) taburculuk protokolü gereklilikleri

## Getting Started

1. 20 yaygın tanı için taburculuk kriter setleri oluştur
2. LLM hasta özetini bu kriterlere karşı değerlendir
3. Eksik kriterleri raporla, tamamlandığında onay ver

## Resources

- [SGK SUT](https://www.sgk.gov.tr)
- [SKS Hastane](https://kalite.saglik.gov.tr)
