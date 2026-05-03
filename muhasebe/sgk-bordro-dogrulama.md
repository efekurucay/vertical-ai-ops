# SGK Bordro Doğrulama Motoru

> **Sector:** Muhasebe / İK  
> **Difficulty:** Medium  
> **Market Size (TR):** Her işveren (1.5M+ aktif işyeri)  
> **Monetization:** B2B SaaS, bordro yazılımı entegrasyonu

## Problem

LLM bordro hesaplama yapabilir. Ancak hesaplanan tutarların **SGK prim tavanı/tabanı, asgari ücret güncellemeleri, AGİ hesabı, kısa çalışma ödeneği kuralları ve sigorta kolları kesinti oranlarına** göre doğru olup olmadığını garanti edemez. Hatalı bordro = SGK cezası + işçi hakkı kaybı.

## The Validation Layer

- Brüt maaş SGK prime esas kazanç tavanını aşıyor mu?
- SGK prim oranları güncel mi? (işveren + işçi payları)
- Asgari ücretin altında ödeme var mı?
- AGİ hesabı medeni durum ve çocuk sayısına göre doğru mu?
- Kıdem tazminatı tavanı aşılmış mı?
- Engelli çalışan için indirimler uygulanmış mı?

## Tech Stack

- **Kural Motoru:** Python + yıllık güncellenen SGK parametreleri (JSON config)
- **LLM:** Claude Haiku (hata açıklaması)
- **Entegrasyon:** Logo Tiger, İşnet, SAP HR modülleri
- **Backend:** FastAPI

## Business Model

- **Target:** KOBİ HR departmanları, muhasebe büroları, ERP satıcıları
- **Pricing:** Çalışan başına aylık veya bordro dönemi başına
- **Argüman:** SGK denetiminde hatalı bordro ağır ceza; otomatik kontrol bu riski ortadan kaldırır

## Turkey Context

- SGK parametreleri yılda en az bir kez değişiyor (asgari ücret, tavan)
- E-bildirge sistemi üzerinden otomatik kontrol yapılabilir
- İşverenlerin %60'ı 10 kişinin altında; bu segment için uygun fiyatlı SaaS pazarı büyük

## Getting Started

1. Güncel SGK prim oranları ve tavanı JSON config olarak tanımla
2. Basit bordro doğrulama fonksiyonu: brüt → net hesap kontrolü
3. Hatalı hesaplarda LLM açıklama üretir
4. Aylık parametre güncelleme mekanizması ekle

## Resources

- [SGK Mevzuat](https://www.sgk.gov.tr/wps/portal/sgk/tr/calisan/mevzuat)
- [Asgari Ücret Kararları](https://www.ailevecalisma.gov.tr)
