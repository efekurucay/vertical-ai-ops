# Poliçe Uygunluk Kontrol Motoru

> **Sector:** Sigorta  
> **Difficulty:** Medium  
> **Market Size (TR):** Tüm sigorta acenteleri ve brokerler  
> **Monetization:** B2B SaaS, white-label

## Problem

LLM müşteri profiline göre sigorta ürünü önerisi yapabilir. Ancak önerilen ürünün **SEDDK tescil durumuna, müşterinin risk profiline uygunluğuna, yasal zorunluluk gerekliliklerine ve acentenin yetki belgesine** uygun olup olmadığını doğrulayamaz.

## The Validation Layer

- Önerilen poliçe ürünü SEDDK'da tescilli mi?
- Müşteri yaşı/mesleği poliçe kabul kriterlerine uyuyor mu?
- Zorunlu sigorta türü (trafik, DASK) mevcut mu ve güncel mi?
- Acente bu ürünü satmaya yetkili mi?
- Prim hesabı aktüeryal kurallara uygun mu?

## Tech Stack

- **Kural Motoru:** Python + SEDDK ürün tescil veritabanı
- **LLM:** GPT-4o (ürün açıklaması ve öneri)
- **Backend:** Node.js / FastAPI

## Business Model

- **Target:** Sigorta acenteleri, bancassurance kanalları
- **Pricing:** Kullanıcı başına aylık SaaS
- **Argüman:** Uygunsuz ürün satışı SEDDK cezası + itibar riski

## Turkey Context

- SEDDK ürün tescil listesi düzenli güncelleniyor
- DASK zorunluluğu penetrasyon sorunu yaratıyor — kontrol motoru fırsatı
- Acentelerin büyük çoğunluğu hâlâ kağıt tabanlı süreçler kullanıyor

## Getting Started

1. SEDDK tescil listesini parse et
2. Müşteri profili → uygun ürün eşleştirme kuralları yaz
3. LLM ile önerileri müşteriye açıkla
4. Uygunsuz ürün önerisi yapılırsa bloke et
