# ÇED Raporu Mevzuat Uyum Motoru

> **Sector:** Çevre / ÇED (Çevresel Etki Değerlendirmesi)
> **Difficulty:** High
> **Market Size (TR):** Her yıl 500+ ÇED başvurusu
> **Monetization:** B2B SaaS (çevre danışmanlık firmaları)

## Problem

LLM ÇED raporu taslağı oluşturabilir. Ancak bu raporun **Çevre, Şehircilik ve İklim Değişikliği Bakanlığı'nın ÇED Yönetmeliği, EK-I ve EK-II listelerindeki eşik değerlere ve zorunlu rapor içerik gerekliliklerine** uygun olup olmadığını doğrulayamaz.

## The Validation Layer

- Proje türü ve kapasitesi ÇED gerektiriyor mu? (EK-I / EK-II kontrolü)
- Zorunlu bölümler (Flora, Fauna, Su Kalitesi, Gürültü, Sosyoekonomik) mevcut mu?
- Alternatif yer analizi yapılmış mı?
- Halkın katılımı toplantısı planlanmış mı?
- Emisyon tahminleri yönetmelik sınır değerleriyle karşılaştırılmış mı?
- İzleme ve takip planı oluşturulmuş mu?

## Tech Stack

- **LLM**: GPT-4o (rapor taslağı)
- **Kural Motoru**: Python + ÇED Yönetmeliği JSON kural seti
- **GIS**: OpenLayers / QGIS (alan analizi)
- **Backend**: FastAPI

## Business Model

- **Target**: Çevre danışmanlık firmaları, büyük inşaat/sanayi projeleri
- **Pricing**: Rapor başına veya aylık SaaS
- **Argüman**: Bakanlık ret riskini ve revizyon döngülerini azaltır

## Turkey Context

- ÇED Yönetmeliği 2014/EK-I ve EK-II listeleri düzenli güncelleniyor
- Bakanlık online ÇED başvuru sistemi mevcut
- TÜBİTAK 1507 Çevre Teknolojileri kategorisi

## Getting Started

1. ÇED Yönetmeliği EK-I listesini JSON eşik değer tablosuna aktar
2. Proje parametreleri gir → ÇED gerekip gerekmediğini hesapla
3. Zorunlu rapor bölümlerini kontrol listesine dönüştür
4. LLM eksik bölümler için taslak üretir

## Resources

- [ÇED Yönetmeliği](https://www.mevzuat.gov.tr)
- [Bakanlık ÇED Sistemi](https://ced.csb.gov.tr)
