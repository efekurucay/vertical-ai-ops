# Karbon Ayak İzi Hesap Doğrulama

> **Sector:** Çevre / Kurumsal Sürdürülebilirlik  
> **Difficulty:** Medium  
> **Market Size (TR/Global):** ESG raporlaması zorunlu hale gelen tüm şirketler  
> **Monetization:** B2B SaaS, ESG danışmanlık aracı

## Problem

LLM ESG raporu veya karbon ayak izi hesabı yapabilir. Ancak hesaplama metodolojisinin **GHG Protocol standartlarına, ISO 14064'e veya AB CSRD yönetmeliğine** uygunluğunu doğrulayamaz. Yanlış karbon muhasebesi = greenwashing riski + düzenleyici ceza.

## The Validation Layer

- Kapsam 1/2/3 sınıflandırması doğru yapılmış mı?
- Emisyon faktörleri GHG Protocol'un güncel veritabanından mı?
- Ölçüm belirsizliği (uncertainty) raporlanmış mı?
- Temel yıl doğru seçilmiş ve belgelenmiş mi?
- 3. taraf doğrulama gerektiriyor mu? (AB CSRD kapsamı)

## Tech Stack

- **Kural Motoru:** Python + GHG Protocol emisyon faktör DB
- **LLM:** GPT-4o (rapor yazımı + açıklama)
- **Standartlar:** GHG Protocol, ISO 14064, CSRD
- **Backend:** FastAPI

## Business Model

- **Target:** AB'ye ihracat yapan şirketler (CBAM kapsamı), borsada işlem gören şirketler
- **Pricing:** Yıllık raporlama SaaS
- **Argüman:** AB Sınırda Karbon Düzenleme Mekanizması (CBAM) 2026'da tam uygulamaya giriyor

## Turkey Context

- Türkiye'nin AB ile gümrük birliği CBAM'dan etkilenecek sektörleri (demir-çelik, çimento, gübre) kapsıyor
- Borsa İstanbul sürdürülebilirlik endeksi şirketleri için ESG raporlama baskısı artıyor
- SPK zorunlu ESG açıklama gereklilikleri 2024'te genişletildi

## Getting Started

1. GHG Protocol Kapsam 1/2/3 sınıflandırma kurallarını JSON'a aktar
2. Sektör bazlı emisyon faktörleri tablosu oluştur (IEA veri kullan)
3. Hesap kontrolü: kullanılan faktör vs. standart faktör örtüşüyor mu?
4. LLM eksik bölümleri tamamlar ve açıklar

## Resources

- [GHG Protocol](https://ghgprotocol.org)
- [AB CSRD Yönetmeliği](https://finance.ec.europa.eu/capital-markets-union-and-financial-markets/company-reporting-and-auditing/company-reporting/corporate-sustainability-reporting_en)
- [CBAM Bilgi](https://taxation-customs.ec.europa.eu/carbon-border-adjustment-mechanism_en)
