# IMO Emisyon Uyum Motoru (CII/EEXI)

> **Sector:** Denizcilik  
> **Difficulty:** High  
> **Market Size (Global):** 50.000+ ticari gemi  
> **Monetization:** B2B SaaS, gemi yönetim şirketi API

## Problem

LLM gemi emisyon raporu oluşturabilir. Ancak raporun **IMO MARPOL Ek VI, CII (Carbon Intensity Indicator) ve EEXI (Energy Efficiency Existing Ship Index) gerekliliklerine** uygun olup olmadığını doğrulayamaz. IMO 2023 sıkılaşmalarıyla uyumsuzluk liman giriş yasağına yol açabiliyor.

## The Validation Layer

- CII derecelendirmesi (A-E) doğru hesaplanmış mı?
- EEXI referans değeri gemi tipi ve tonajına göre doğru mu?
- Yıllık yakıt tüketim raporu (DCS) eksiksiz mi?
- İyileştirme planı (SEEMP Part III) CII hedeflerine uyumlu mu?
- Flag state sertifikası güncel mi?

## Tech Stack

- **Kural Motoru:** Python + IMO DCS formulas
- **LLM:** GPT-4o (rapor yazımı ve açıklama)
- **Veri:** IMO GISIS veritabanı, gemi karakteristik verileri
- **Backend:** FastAPI

## Business Model

- **Target:** Gemi işletmecileri, tekne sigortacıları, liman otoriteleri
- **Pricing:** Gemi başına yıllık SaaS
- **Argüman:** AB ETS (Emissions Trading System) 2024'te deniz taşımacılığını kapsama aldı

## Turkey Context

- Türkiye büyük bir gemi sökümü ve inşa merkezi; IMO uyumu stratejik önem taşıyor
- Türkiye Denizcilik İşletmeleri ve özel armatörler bu çözüme açık
- Gemi finansında yeşil kredi koşulları CII uyumunu zorunlu kılıyor

## Getting Started

1. IMO CII hesaplama formülünü Python'a implement et
2. Gemi tipi + DWT + yıllık taşınan mil → CII skoru hesapla
3. A-E derecelendirme sınırlarını IMO tablosundan yükle
4. LLM: C/D/E alan gemiler için iyileştirme önerileri üretir

## Resources

- [IMO MARPOL Annex VI](https://www.imo.org)
- [CII Gösterge Hesaplama Rehberi](https://www.imo.org/en/OurWork/Environment/Pages/IMO-and-shipping.aspx)
