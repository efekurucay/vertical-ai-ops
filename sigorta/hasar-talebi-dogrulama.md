# Hasar Talebi Doğrulama Motoru

> **Sector:** Sigorta / InsurTech  
> **Difficulty:** Medium  
> **Market Size (TR):** 60+ sigorta şirketi, milyonlarca yıllık hasar talebi  
> **Monetization:** B2B SaaS, işlem başına API

## Problem

LLM'ler hasar formlarını okuyup ön değerlendirme yapabilir. Ancak talebin **poliçe kapsamına, muafiyet maddelerine, beyan yükümlülüğü ihlallerine ve SEDDK düzenlemelerine** uygun olup olmadığını deterministik olarak kontrol edemez. Sigorta şirketleri hâlâ her talebi manuel inceliyor.

## The Validation Layer

- Hasar tarihi poliçe aktif dönemi içinde mi?
- Hasar türü poliçenin kapsam listesinde mi?
- Muafiyet tutarı doğru hesaplanmış mı?
- Sigortalı beyanları poliçe başlangıcındaki beyanlarla tutarlı mı?
- Talep tutarı azami tazminat limitini aşıyor mu?
- SEDDK zorunlu bildirim süreleri ihlal edilmiş mi?

## Tech Stack

- **Kural Motoru:** Python + JSON policy rules
- **LLM:** Claude 3.5 (hasar belgesi OCR + analiz)
- **OCR:** Azure Document Intelligence veya Tesseract
- **Backend:** FastAPI + PostgreSQL

## Business Model

- **Target:** Sigorta şirketleri hasar departmanları, acenteler
- **Pricing:** Talep başına 0.5-2 USD veya aylık SaaS
- **Argüman:** Ortalama hasar işleme süresini 5 günden 2 saate indirir

## Turkey Context

- SEDDK (Sigortacılık ve Özel Emeklilik Düzenleme ve Denetleme Kurumu) düzenlemeleri ana çerçeve
- Zorunlu trafik sigortasında hasar sıklığı çok yüksek — otomasyon ihtiyacı net
- TÜBİTAK 1507 "InsurTech" kategorisi

## Getting Started

1. Örnek poliçe JSON şeması oluştur (kapsam, muafiyet, limit)
2. Hasar formu verisiyle kural kontrolü yaz
3. LLM ile OCR çıktısını yapılandırılmış veriye dönüştür
4. Kural motoruyla çapraz kontrol et

## Resources

- [SEDDK Mevzuat](https://www.seddk.gov.tr)
- [Azure Document Intelligence](https://azure.microsoft.com/en-us/products/ai-services/ai-document-intelligence)
