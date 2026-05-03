# Poliçe Uygunluk Kontrolü

> **Sector:** Sigorta  
> **Difficulty:** Medium  
> **Monetization:** Sigorta şirketi SaaS entegrasyonu

## Problem

LLM müşteri beyanına göre uygun poliçe türleri önerebilir. Ancak poliçe üretiminde teminat, istisna, yaş, meslek, sağlık beyanı ve bölgesel risk gibi birçok alan resmi kurallarla doğrulanmalıdır.

## Validation Layer

- Başvuru sahibi poliçe yaş sınırına uygun mu?
- Beyan edilen risk profili teminat kapsamına giriyor mu?
- İstisnalar ve muafiyetler doğru uygulandı mı?
- Eksik beyan nedeniyle poliçe iptal riski var mı?
- Fiyatlandırma kural setine uyum var mı?

## Tech Stack

- Rule engine
- Sigorta ürün ağacı ve teminat tabloları
- LLM: müşteri açıklaması ve acente yardımcısı
- API first backend

## Business Model

- Sigorta şirketleri ve broker’lar
- Poliçe başına ücret veya yıllık lisans

## Turkey Context

Türkiye’de sigorta penetrasyonu artarken ürün çeşitliliği de büyüyor. Bu da acente ve operasyon ekiplerinin hata yapma riskini artırıyor; doğrulama katmanı burada güçlü değer üretir.

## Getting Started

1. Teminat ve istisna kurallarını yapılandırılmış veri haline getir
2. Başvuru formunu validator pipeline’a bağla
3. Hata / istisna açıklamaları için LLM katmanı ekle
