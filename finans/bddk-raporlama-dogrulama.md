# BDDK Raporlama Format Doğrulama

> **Sector:** Finans / Bankacılık  
> **Difficulty:** Medium  
> **Market Size (TR):** 50+ banka, 400+ finansal kurum  
> **Monetization:** B2B SaaS, API lisansı

## Problem

LLM'ler BDDK'ya sunulacak finansal raporların taslağını oluşturabilir. Ancak bu raporların **BDDK'nın belirlediği XBRL formatına, hesap kodlarına ve dönemsel raporlama şablonlarına** uygunluğunu doğrulayamaz. Hatalı format doğrudan red ve idari yaptırım anlamına gelir.

## The Validation Layer

- Rapor XBRL şemasıyla uyumlu mu?
- Hesap kodları BDDK tekdüzen hesap planına göre doğru mu?
- Zorunlu alanların tamamı doldurulmuş mu?
- Dönemsel tutarlılık: önceki dönemle kıyaslandığında anormal sapmalar var mı?
- Raporlama tarihi ve frekansı yasal gerekliliklere uyuyor mu?

```
Finansal Veri → LLM (rapor taslağı) → BDDK Format Motoru → XBRL Çıktı
```

## Tech Stack

- **Kural Motoru:** Python + lxml (XBRL parse)
- **Şema:** BDDK XBRL taxonomy
- **LLM:** GPT-4o (narratif bölümler için)
- **Backend:** FastAPI

## Business Model

- **Target:** Orta ölçekli bankalar, katılım bankaları, finansal kiralama şirketleri
- **Pricing:** Aylık SaaS veya raporlama dönemi başına
- **Argüman:** Manuel kontrol saatlerini %80 azaltır, BDDK red riskini ortadan kaldırır

## Turkey Context

- BDDK XBRL taxonomy resmi olarak yayımlanmış durumda
- 2024 itibarıyla dijital raporlama zorunluluğu genişletildi
- TÜBİTAK 1507 "Finansal Teknolojiler" kategorisi uygun

## Getting Started

1. BDDK XBRL taxonomy dosyasını indir
2. Python lxml ile validasyon motoru yaz
3. LLM ile hata mesajlarını anlaşılır dile çevir
4. Test bankası verisiyle doğrula

## Resources

- [BDDK XBRL Taxonomy](https://www.bddk.org.tr)
- [XBRL International](https://www.xbrl.org)
