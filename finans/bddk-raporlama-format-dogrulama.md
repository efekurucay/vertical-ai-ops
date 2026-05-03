# BDDK Raporlama Format Doğrulama

> **Sector:** Finans / Bankacılık
> **Difficulty:** Medium
> **Market Size (TR):** 50+ banka, 400+ finansal kuruluş
> **Monetization:** B2B SaaS, API lisansı

## Problem

Bankalar BDDK'ya periyodik raporlar göndermek zorunda. LLM bu raporları hazırlayabilir ancak **BDDK'nın belirlediği XBRL formatı, sütun sıralaması, kod yapısı ve validasyon kurallarına** uygun olup olmadığını doğrulayamaz. Hatalı format nedeniyle raporun reddedilmesi para cezası ve itibar riski doğurur.

## The Validation Layer

- XBRL şemasına uygunluk
- Zorunlu alanların doldurulmuş olması
- Sayısal değerlerin izin verilen aralıklarda olması
- Dönemler arası tutarlılık (önceki rapordaki değerlerle çelişki yok mu?)
- Onay/imza adımlarının tamamlanmış olması

```
Rapor Verisi → LLM (draft) → BDDK Format Motoru → Onaylı XBRL Çıktı
```

## Technical Architecture

```
[Ham Finansal Veri]
      ↓
[LLM — Rapor taslağı]
      ↓
[BDDK Kural Motoru]
  ├── XBRL Validator
  ├── Zorunlu Alan Kontrolü
  ├── Dönemler Arası Tutarlılık
  └── İzin Verilen Değer Aralıkları
      ↓
[Geçerli Rapor / Hata Listesi + Madde Referansı]
```

## Tech Stack

- **LLM**: GPT-4o (rapor taslağı)
- **XBRL**: python-xbrl kütüphanesi
- **Kural Motoru**: Python + BDDK taxonomy JSON
- **Backend**: FastAPI

## Business Model

- **Target**: Bankalar, finans şirketleri, muhasebe/denetim firmaları
- **Pricing**: Aylık SaaS veya rapor başına ücret
- **Argüman**: BDDK cezaları ve itibar riski

## Turkey Context

- BDDK XBRL taxonomy güncel olarak yayımlıyor
- Raporlama hataları için idari para cezası uygulanıyor
- TÜBİTAK 1507 Fintech kategorisi

## Getting Started

1. BDDK sitesinden XBRL taxonomy indir
2. Python ile temel alan validasyonu yaz
3. LLM rapor taslağını bu validatörden geçir
4. Hata raporunu insan-okunabilir hale getir

## Resources

- [BDDK Raporlama](https://www.bddk.org.tr)
- [python-xbrl](https://github.com/greenkeytech/python-xbrl)
