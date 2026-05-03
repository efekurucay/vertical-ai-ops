# YEK Lisans Başvuru Uyum Motoru

> **Sector:** Enerji / Yenilenebilir  
> **Difficulty:** High  
> **Market Size (TR):** Her yıl yeni RES/GES/HES başvuruları  
> **Monetization:** Proje başına, danışmanlık SaaS

## Problem

LLM YEK lisans başvuru dosyası taslağı yazabilir. Ancak dosyanın **EPDK lisanslama yönetmeliği, Enerji ve Tabii Kaynaklar Bakanlığı ön izin şartları ve teknik minimum gereklilikler** açısından tam olup olmadığını doğrulayamaz. Eksik evrak = başvuru iptali.

## The Validation Layer

- Başvuru türüne göre zorunlu belgeler tamam mı? (RES, GES, HES farklı liste)
- Kapasite sınırı lisans gerektiriyor mu? (1 MW altı muafiyet)
- Arazi belgeleri (tapu, kiralama sözleşmesi) eşleşiyor mu?
- ÇED zorunluluğu var mı? (kapasite eşiğine göre)
- Bağlantı kapasitesi talep formu doldurul mu?

## Tech Stack

- **Kural Motoru:** Python + EPDK lisanslama checklist JSON
- **LLM:** GPT-4o (başvuru belgesi hazırlama)
- **Veri:** EPDK mevzuat veritabanı
- **Backend:** FastAPI

## Business Model

- **Target:** YEK yatırımcıları, enerji mühendislik büroları, EPK danışmanları
- **Pricing:** Başvuru başına veya yıllık abonelik
- **Argüman:** Başvuru hataları projeyi 1-2 yıl geciktirebilir

## Turkey Context

- Türkiye 2035 hedefi: kurulu gücün %65'i yenilenebilir enerji
- EPDK lisanslama süreci karmaşık ve dökümantasyon ağır
- YEKA ihale süreçleri ek format gerektiriyor

## Getting Started

1. EPDK yönetmeliğinden başvuru türü bazlı belge listelerini JSON'a aktar
2. Checklist kontrolü: yüklenen belgeler vs. zorunlu liste
3. LLM eksik belgeleri ve nasıl tamamlanacağını açıklar
4. Kapasite hesabı ile lisans zorunluluk tespiti ekle

## Resources

- [EPDK Mevzuat](https://www.epdk.gov.tr/Detay/Icerik/3-0-24/elektrik-piyasasi-mevzuat)
- [ETKB Yenilenebilir Enerji](https://www.enerji.gov.tr)
