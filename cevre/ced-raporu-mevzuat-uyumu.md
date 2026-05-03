# Ç ED Raporu Mevzuat Uyum Motoru

> **Sector:** Çevre / Kamu  
> **Difficulty:** High  
> **Market Size (TR):** Yılda 2.000+ ÇED başvurusu  
> **Monetization:** B2B (proje başına), danışmanlık SaaS

## Problem

LLM Çevre Etki Değerlendirmesi raporu taslağı yazabilir. Ancak taslağın **ÇED Yönetmeliği (2014/29 sayılı), Ek-1/Ek-2 listesi kıstasları, görüş alınması gereken kurumların listesi ve başvuru form formatlarına** uygunluğunu doğrulayamaz. Eksik veya hatalı ÇED raporu milyonlarca TL yatırımı durduruyor.

## The Validation Layer

- Proje türü Ek-1 mi yoksa Ek-2 kapsamında mı?
- Çevişkenlik kıstasları (kapasite, alan) doğru değerlendirilmiş mi?
- Zorunlu bölümler tamam mı? (proje tanımı, alternatiflerin incelenmesi, izleme planı)
- Görüş alınması gereken Tüm kurumlar listelendi mi?
- Halk katılım toplantısı şartı var mı ve belgeler eklenmiş mi?

## Tech Stack

- **Kural Motoru:** Python + ÇED Yönetmeliği JSON rule set
- **LLM:** GPT-4o (rapor bölüm üretimi)
- **Veri:** ÇŞB ÇED portalinden proje türü listesi
- **Backend:** FastAPI

## Business Model

- **Target:** Çevre danışmanlık firmaları, büyük sanayi yatırımcıları
- **Pricing:** Proje başına tek seferlik ücret (5.000–50.000 TL)
- **Argüman:** ÇEB red kararı = projenin 6-18 ay gecikmesi

## Turkey Context

- ÇŞB ÇED portali üzerinden başvurular dijitale taşındı ancak içerik kalitesi hala manuel değerlendiriliyor
- Her yıl Ek-1 ve Ek-2 listelerinde güncelleme yapılıyor — dinamik kural güncellemesi kritik

## Getting Started

1. ÇED Yönetmeliği Ek-1/Ek-2 listesini JSON'a aktar
2. Zorunlu bölüm checklist kontrolü yaz
3. Proje türü → ilgili kurum listesi eşleştirmesi yap
4. LLM eksik bölümleri tamamlamak için öneri üretir

## Resources

- [ÇEB ÇED Portal](https://ced.csb.gov.tr)
- [ÇED Yönetmeliği](https://www.mevzuat.gov.tr)
