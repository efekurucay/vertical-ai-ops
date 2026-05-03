# Uuş Planı Hava Sahası Uyum Motoru

> **Sector:** Havacılık  
> **Difficulty:** Very High  
> **Market Size (TR/Global):** DHMİ + 500+ hava yolu şirketi  
> **Monetization:** B2B, API lisansı (havayolları ve operasyonel destek şirketleri)

## Problem

LLM uçuş planı taslağı oluşturabilir. Ancak planın **ICAO DOC 4444 prosedürlerine, NOTAM uyarılarına, hava sahası sınırlamalarına ve DHMİ AIP (Aeronautical Information Publication) Güncel sürümüne** uygunluğunu doğrulayamaz. Hatalı uçuş planı uçuş güvenliğini tehdit eder.

## The Validation Layer

- Rotada aktif NOTAM kısıtlaması var mı?
- Uuçuş seviyesi (FL) rotadaki hava sahası sınıflandırmasıyla uyumlu mu?
- Yakıt hesabı ICAO rezerv gereksinimleri sağlıyor mu?
- Alternati havaalanı tanımlanmış ve uygun mu?
- ETOPS gereksinimi var mı? (uzun mesafe iki motorlu uçuşlar)

## Tech Stack

- **Kural Motoru:** Python + ICAO kural seti
- **Veri:** DHMİ AIP API, FAA NOTAM API
- **LLM:** GPT-4o (uçuş planı oluşturma ve briefing)
- **Backend:** FastAPI

## Business Model

- **Target:** Genel havacılık operatörleri, charter şirketleri, uçuş operasyon merkezleri
- **Pricing:** Uçuş başına veya aylık lisans
- **Argüman:** Uçuş planlama insan hatasını azaltmak en büyük değer

## Turkey Context

- DHMİ AIP güncel ve erişilebilir
- Türkiye artan transit uçuş trafiğiyle önemli bir hava sahası yönetim merkezi

## Getting Started

1. ICAO uçuş planı formatını parse et (ICAO FPL formatı)
2. NOTAM API ile rota kontrolü yap
3. Yakıt hesabı doğrulama kuralı ekle
4. LLM: plan hatası varsa pilot-okunabilir özet üretir

## Resources

- [ICAO DOC 4444](https://www.icao.int)
- [DHMİ AIP](https://www.dhmi.gov.tr)
