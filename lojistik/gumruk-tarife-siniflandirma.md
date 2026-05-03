# Gümrük Tarife Sınıflandırma Doğrulama

> **Sector:** Lojistik / Dış Ticaret  
> **Difficulty:** High  
> **Market Size (TR):** 200B USD+ ithalat/ihracat hacmi  
> **Monetization:** B2B SaaS, gümrük müşavirliği aracı

## Problem

LLM bir ürün tanımından GTIİP (Gümrük Tarife İstatistik Pozisyonu) kodu tahmin edebilir. Ancak bu kodun **HS nomenklâtürün teknik açıklama kurallarına, Türkiye gümrük tarifesindeki istisnalara ve BAĞş itibarile uygulanan ek tarife/kotalara** uygunluğunu doğrulayamaz. Yanlış GTIİP = vergi cezası + gümrük gözetimi.

## The Validation Layer

- GTIİP kodu HS 2022 güncel versiyonuyla uyumlu mu?
- Ürünün teknik özellikleri sınıflandırma kriterlerini sağlıyor mu?
- Bu GTIİP kodu için ek tarife / anti-damping vergi uygulanmış mı?
- Ürün mensei ile tercihli tarife uygulaması müçbir mı?
- İthalat/ihracat kısıtlaması var mı?

## Tech Stack

- **Kural Motoru:** Python + HS tarife tablosu JSON
- **LLM:** GPT-4o (ürün tanımı → GTIİP tahmini)
- **Veri:** Ticaret Bakanlığı Tarife veritabanı, WCO HS nomenclature
- **Backend:** FastAPI

## Business Model

- **Target:** Gümrük müşavirleri, ithalatçı/ihracatçı firmalar, lojistik şirketleri
- **Pricing:** Sorgu başına veya aylık SaaS
- **Argüman:** Hatalı GTIİP sınıflandırma vergi cezası + beyan düzeltme maliyeti

## Turkey Context

- TÜFE'nin yüksekliği ithalat gümrük gelirlerini artırdı, denetim sıklaştı
- AB-Türkiye Gümrük Birliği güncellemesi müzekeresi tarife uyumluluk ihtiyacını artırıyor

## Getting Started

1. WCO HS 2022 nomenclature JSON olarak al (açık veri)
2. GPT-4o: ürün açıklamasından 6-8 haneli GTIİP kodu tahmin et
3. Tahmin edilen kodu HS kuralı ile dogrula (GRI kuralları)
4. Ek tarife/kota kontrolü için Ticaret Bakanlığı veritabanı entegrasyonu

## Resources

- [WCO HS Nomenclature](https://www.wcoomd.org)
- [T.C. Gümrük Tarife Cetveli](https://www.ticaret.gov.tr)
