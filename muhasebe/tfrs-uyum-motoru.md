# TFRS/MSUGT Uyum Motoru

> **Sector:** Muhasebe / Finansal Raporlama  
> **Difficulty:** High  
> **Market Size (TR):** 1M+ aktif işletme, 100K+ muhasebeci  
> **Monetization:** B2B SaaS, muhasebe yazılımı entegrasyonu

## Problem

LLM'e "bu işlemi muhasebeleştir" dediğinizde mantıklı görünen bir kayıt üretebilir. Ancak bu kaydın **TFRS (Türkiye Finansal Raporlama Standartları) veya MSUGT'a (Muhasebe Sistemi Uygulama Genel Tebliği) uygun hesap kodunu, doğru dönemsellik ilkesini, doğru KDV uygulamasını** kullandığını doğrulayamaz.

## The Validation Layer

- Kullanılan hesap kodu işlem türüyle uyumlu mu? (Tekdüzen hesap planı)
- Borç/alacak dengesi sağlanmış mı?
- KDV oranı işlem türüne göre doğru mu? (0, 1, 10, 20)
- Amortisman süresi VUK'a uygun mu?
- Dönemsellik: gelir/gider doğru döneme kaydedilmiş mi?
- e-Fatura/e-Arşiv formatı GİB şemasına uygun mu?

```
İşlem Verisi → LLM (muhasebe kaydı taslağı) → TFRS/MSUGT Kural Motoru → Onaylı Kayıt
```

## Tech Stack

- **Kural Motoru:** Python + tekdüzen hesap planı JSON
- **LLM:** GPT-4o (işlem tanımından hesap tahmini)
- **Entegrasyon:** GİB e-fatura API, Logo/Luca/Mikro ERP bağlantıları
- **Backend:** FastAPI

## Business Model

- **Target:** KOBİ'ler, mali müşavirler, muhasebe büroları
- **Pricing:** Kullanıcı başına aylık SaaS veya işlem başına
- **Argüman:** Vergi incelemesinde hatalı kayıt = ceza + faiz; otomasyon bu riski sıfırlar

## Turkey Context

- GİB e-fatura ve e-defter zorunluluğu kapsamı her yıl genişliyor
- VUK ve TFRS arasındaki farklar (özellikle amortisman) muhasebecilere ek yük yaratıyor
- TÜBİTAK 1507 "Dijital Dönüşüm" kategorisi

## Getting Started

1. Tekdüzen hesap planını JSON'a aktar
2. İşlem türü → hesap kodu eşleştirme kuralları yaz
3. LLM işlem açıklamasından işlem türü tahmin eder
4. Kural motoru hesap kodunu doğrular, yanlışsa düzeltir

## Resources

- [GİB e-Fatura](https://www.gib.gov.tr/e-fatura)
- [KGK TFRS Standartları](https://www.kgk.gov.tr)
- [VUK Mevzuat](https://www.mevzuat.gov.tr)
