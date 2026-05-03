# Portföy Risk Limiti Kontrolü

> **Sector:** Finans / Varlık Yönetimi  
> **Difficulty:** High  
> **Monetization:** Kurumsal SaaS

## Problem

LLM yatırımcı profiline göre portföy önerileri verebilir. Ancak regülasyon, fon iç tüzüğü ve risk limitleri, önerinin ötesinde doğrulanabilir kurallar gerektirir. Bir portföyün belirli varlık sınıflarında aşırı yoğunlaşması, kurum açısından ciddi uyum ve risk problemi yaratır.

## Validation Layer

- Varlık dağılımı fon iç tüzüğüne uygun mu?
- Tek ihraççı limiti aşılıyor mu?
- Sektörel yoğunlaşma kuralları ihlal ediliyor mu?
- Volatilite ve VaR limitleri kurum politikasına uygun mu?
- Yatırımcı risk profiliyle ürün sınıfı eşleşiyor mu?

## Tech Stack

- Python risk hesaplama kütüphaneleri
- Portföy analitik motoru
- LLM: yatırım komitesi özeti üretimi
- FastAPI + dashboard

## Business Model

- Varlık yönetim şirketleri ve family office’ler
- Kullanıcı başına lisans veya portföy hacmine göre fiyatlama

## Turkey Context

Türkiye’de serbest fonlar, portföy yönetim şirketleri ve bireysel yatırım araçları genişledikçe risk ve uygunluk kontrolü daha önemli hale geliyor. SPK denetim perspektifi nedeniyle kural tabanlı açıklanabilir sistemler öne çıkıyor.

## Getting Started

1. Portföy bileşenlerini normalize et
2. İç tüzük kurallarını makine okunur hale getir
3. Limit ihlallerini açıklayan validator katmanı kur
4. LLM ile komite özeti üret
