# Enerji Verimliliği Sertifika Doğrulama Motoru

> **Sector:** Enerji / Bina
> **Difficulty:** Medium
> **Market Size (TR):** 500.000+ yapı ruhsatı/yıl
> **Monetization:** B2B SaaS (mimari yazılım entegrasyonu)

## Problem

LLM bina enerji performans raporu taslağı oluşturabilir. Ancak bu raporun **BEP-TR (Binalarda Enerji Performansı - Türkiye) yönetmeliği, enerji kimlik belgesi sınıflandırması ve zorunlu hesaplama metodolojisine** uygun olup olmadığını doğrulayamaz.

## The Validation Layer

- Isıtma/soğutma yükleri BEP-TR metoduna göre hesaplanmış mı?
- Hava sızdırmazlık ve ısı köprüsü değerleri iklim bölgesine uygun mu?
- Yenilenebilir enerji katkısı doğru hesaplandı mı?
- A-G enerji sınıfı doğru tahsis edildi mi?
- Yetkili enerji verimliliği danışmanı imzaladı mı?

## Tech Stack

- **LLM**: GPT-4o (rapor taslağı)
- **Hesaplama Motoru**: Python + BEP-TR algoritması
- **İklim Veritabanı**: Türkiye iklim bölgeleri JSON
- **Backend**: FastAPI

## Business Model

- **Target**: Mimar ve mühendislik büroları, yapı denetim firmaları
- **Pricing**: Proje başına veya aylık SaaS
- **Argüman**: BEP belgesi zorunluluğu (ruhsat şartı)

## Turkey Context

- BEP-TR yönetmeliği yeni yapılarda zorunlu
- A-G enerji sınıfı belgesi alım-satım belgesi olarak gerekli

## Getting Started

1. BEP-TR ısı geçirgenlik U-değer tablolarını JSON'a aktar
2. İklim bölgesine göre minimum U-değer kontrolü yaz
3. LLM mimari açıklamadan bina özelliklerini çıkarır, motor kontrol eder

## Resources

- [BEP-TR Yönetmeliği](https://www.mevzuat.gov.tr)
- [Enver Portalı](https://enver.csb.gov.tr)
