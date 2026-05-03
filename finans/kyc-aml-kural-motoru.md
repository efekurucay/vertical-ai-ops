# KYC / AML Kural Motoru

> **Sector:** Finans / Bankacılık  
> **Difficulty:** High  
> **Monetization:** SaaS + API + kurum içi kurulum

## Problem

LLM müşteri onboarding metinlerini okuyup riskli alanları işaretleyebilir. Ancak KYC ve AML süreçlerinde asıl değer, kararın açıklanabilir ve mevzuata bağlı olmasıdır. Banka, fintech ya da ödeme kuruluşu, müşteriyi neden reddettiğini veya neden incelemeye aldığını kuralla temellendirmek zorundadır.

## Validation Layer

- Kimlik doğrulama zorunlu alanları eksiksiz mi?
- Adres, vergi numarası, şirket sicil kaydı gibi alanlar çapraz kontrol edildi mi?
- Yaptırım listesi, PEP listesi ve adverse media taraması yapıldı mı?
- Risk skoru kurum eşiklerine göre doğru hesaplandı mı?
- Şüpheli işlem senaryoları AML kurallarıyla eşleşiyor mu?

## Tech Stack

- Python / FastAPI
- Rule engine (json rules veya DSL)
- OFAC, UN, AB yaptırım listeleri
- LLM: açıklama üretimi ve belge özetleme

## Business Model

- Banka ve fintech’lere yıllık lisans
- API bazlı kullanım fiyatlaması
- On-prem kurulum seçeneği

## Turkey Context

Türkiye’de MASAK yükümlülükleri ve elektronik kimlik doğrulama süreçleri nedeniyle açıklanabilir kontrol katmanı kritik hale geliyor. Fintech sayısındaki artış, bu alanda dikey AI ürünleri için iyi bir giriş noktası oluşturuyor.

## Getting Started

1. Müşteri onboarding formunu JSON şemaya dök
2. Temel KYC zorunlu alanlarını kural seti haline getir
3. Yaptırım listesi eşleştirme modülü ekle
4. LLM'i sadece açıklama ve özetleme katmanında kullan
