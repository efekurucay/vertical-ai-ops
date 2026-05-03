# Organik Sertifika Uyum Motoru

> **Sector:** Tarım / Organik
> **Difficulty:** Medium
> **Market Size (TR):** 80.000+ organik tarım işletmesi
> **Monetization:** B2B SaaS (organik sertifika kuruluşları)

## Problem

LLM organik tarım planı veya sertifika başvurusu taslağı yazabilir. Ancak bu planın **Organik Tarımın Esasları ve Uygulanmasına İlişkin Yönetmelik, EC 834/2007 (AB organik tüzüğü) ve sertifika kuruluşunun özel gerekliliklerine** uygun olup olmadığını doğrulayamaz.

## The Validation Layer

- Dönüşüm süresi tamamlandı mı? (tarla: 2 yıl, çok yıllık: 3 yıl)
- Kullanılan girdiler izin verilen maddeler listesinde mi?
- Tampon bölge gereklilikleri karşılandı mı?
- Kayıt ve izleme belgeleri eksiksiz mi?
- Paralel üretim durumu var mı? (aynı arazide hem organik hem konvansiyonel)

## Tech Stack

- **LLM**: Claude (plan taslağı)
- **Kural Motoru**: Python + organik girdi izin listesi JSON
- **DB**: Tarım Bakanlığı organik sertifika verisi
- **Backend**: FastAPI

## Business Model

- **Target**: Organik sertifika kuruluşları, organik tarım kooperatifleri
- **Pricing**: İşletme başına yıllık SaaS
- **Argüman**: Sertifika denetim sürecini hızlandırır

## Turkey Context

- BÜGEM (Bitkisel Üretim Genel Müdürlüğü) organik tarım denetimi
- AB'ye organik ürün ihracatı için EC tüzüğü uyumu zorunlu

## Getting Started

1. İzin verilen organik girdiler listesini (EC 889/2008 EK II) JSON'a aktar
2. Kullanılan girdi listesini kontrol et
3. Dönüşüm takvimini hesapla ve doğrula

## Resources

- [Tarım Bakanlığı Organik Tarım](https://www.tarimorman.gov.tr)
- [EC 834/2007](https://eur-lex.europa.eu)
