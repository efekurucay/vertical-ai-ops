# Kredi Skoru Doğrulama Katmanı

> **Sector:** Finans / Kredi  
> **Difficulty:** Medium  
> **Monetization:** API + kredi karar destek ürünü

## Problem

LLM kredi başvurularını özetleyebilir ve müşteri profili hakkında görüş sunabilir. Ama kredi tahsis sürecinde karar, yalnızca metinsel izlenime göre verilemez. Gelir, borçluluk, davranışsal veriler ve regülasyon temelli eşikler ayrı ayrı doğrulanmalıdır.

## Validation Layer

- Gelir / gider oranı minimum şartları sağlıyor mu?
- Mevcut borçluluk eşiği aşılıyor mu?
- Başvuru verisi ile resmi belge verisi uyumlu mu?
- Skor kartı çıktısı manuel override gerektiriyor mu?
- Red veya onay kararı açıklanabilir mi?

## Tech Stack

- Python scoring pipeline
- Belge OCR + alan eşleştirme
- LLM: dosya özeti ve insan okunur karar açıklaması
- Rule engine + FastAPI

## Business Model

- Banka, leasing, faktoring ve BNPL sağlayıcıları
- API başına fiyat veya yıllık lisans

## Turkey Context

Türkiye’de kredi verme süreçlerinde belge yoğunluğu ve manuel değerlendirme hâlâ yüksek. Bu yüzden LLM destekli fakat kural tabanlı son kontrol katmanı ciddi zaman kazandırabilir.

## Getting Started

1. Kredi başvuru alanları için şema oluştur
2. Gelir ve borçluluk oranı validator’ları yaz
3. OCR çıktısı ile beyan edilen veriyi karşılaştır
4. LLM ile karar açıklamasını üret
