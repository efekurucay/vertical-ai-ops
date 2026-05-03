# YEK Lisans Başvuru Uyum Motoru

> **Sector:** Enerji / Yenilenebilir Enerji
> **Difficulty:** Medium
> **Market Size (TR):** Her yıl yüzlerce YEK/YEKDEM başvurusu
> **Monetization:** B2B SaaS, danışmanlık entegrasyonu

## Problem

LLM YEK (Yenilenebilir Enerji Kaynakları) lisans başvurusu için gerekli belgeleri listeleyebilir veya taslak yazabilir. Ancak başvurunun **EPDK lisanslama yönetmeliği, YEKDEM mekanizması koşulları ve bölgeye özel kısıtlamalara** tam uyumlu olup olmadığını doğrulayamaz.

## The Validation Layer

- Proje kapasitesi lisans muafiyeti eşiğini aşıyor mu? (1 MW üzeri)
- Bağlantı noktası şebeke kapasitesi mevcut mu? (TEİAŞ/EDAŞ görüşü)
- ÇED durumu projenin büyüklüğüyle uyumlu mu?
- YEKDEM başvuru süresi ve döngüsü uygun mu?
- Arazi kullanım izni türü (irtifak, kiralama) doğru mu?

## Tech Stack

- **LLM**: Claude (başvuru taslağı)
- **Kural Motoru**: Python + EPDK yönetmelik JSON
- **GIS**: Şebeke kapasite haritası entegrasyonu
- **Backend**: FastAPI

## Business Model

- **Target**: YEK yatırımcıları, EPC firmaları, enerji danışmanlık şirketleri
- **Pricing**: Proje başına veya aylık SaaS
- **Argüman**: Başvuru ret riskini ve revizyon maliyetini azaltır

## Turkey Context

- EPDK lisanslama süreci karmaşık ve uzun
- YEKDEM (Yenilenebilir Enerji Kaynaklarını Destekleme Mekanizması) periyodik başvuru
- TÜBİTAK 1507 Enerji kategorisi

## Getting Started

1. EPDK lisanslama yönetmeliğindeki belge listesini JSON'a aktar
2. Proje parametreleri gir → gerekli belge ve koşulları listele
3. Yüklenen belgelerle kontrol listesini karşılaştır

## Resources

- [EPDK](https://www.epdk.gov.tr)
- [TEİAŞ Bağlantı](https://www.teias.gov.tr)
