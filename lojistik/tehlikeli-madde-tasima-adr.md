# Tehlikeli Madde Taşıma Uyum Motoru (ADR)

> **Sector:** Lojistik / Karayolu Taşımacılığı  
> **Difficulty:** High  
> **Market Size (TR):** 500.000+ TIR ve kamyon, yüzlerce lojistik firması  
> **Monetization:** B2B SaaS, lojistik yazılımı entegrasyonu

## Problem

LLM tehlikeli madde sevkiyat belgesi oluşturabilir. Ancak belgenin **ADR 2023 (Avrupa Karayolu Tehlikeli Madde Taşımacılığı Anlaşması) gerekliliklerine, UN numarası etiketleme kuralına ve araç donanım zorunluluklarına** uygunluğunu doğrulayamaz. Uyumsuz belge = idari para cezası + malın el konulması.

## The Validation Layer

- Maddenin UN numarası doğru mu?
- Tehlike sınıfı ve ambalaj grubu doğru belirlenmiş mi?
- Zorunlu taşımacılık belgesi (CMR + tehlikeli madde belgesi) eksiksiz mi?
- Etiketleme ve işaretleme ADR gereklilikleriyle uyumlu mu?
- Sürücü ADR SRC belgesi mevcut mu ve geçerli mi?
- Taşınan miktar muafiyet limitini aşıyor mu?

## Tech Stack

- **Kural Motoru:** Python + ADR 2023 madde listesi ve kurallar JSON
- **LLM:** GPT-4o (belge oluşturma ve açıklama)
- **Veri:** UN Tehlikeli Madde Listesi, ADR 2023 tam metin
- **Backend:** FastAPI

## Business Model

- **Target:** Kimya şirketleri, lojistik operatörleri, akış düzenleme depoları
- **Pricing:** Sevkiyat başına veya aylık SaaS
- **Argüman:** ADR ihlali can kaybı riski + çok yüksek idari para cezası

## Turkey Context

- Türkiye ADR'ye taraf; Ulaştırma Bakanlığı denetimleri sıklaştı
- TMGD (Tehlikeli Madde Güvenlik Danışmanı) zorunluluğu 2022'de genişletildi
- Lojistik sektöründe dijitalleşme hızlanıyor

## Getting Started

1. ADR 2023 Tablo A (madde listesi) JSON'a aktar
2. UN no. girdisi al, sınıf + ambalaj grubu dönüdür
3. Belge checklist kontrolü yaz
4. LLM: eksik belge için hazırlama kılavuzu üretir

## Resources

- [ADR 2023 UNECE](https://unece.org/transport/dangerous-goods/adr-2023)
- [T.C. Ulaştırma TMGD Mevzuat](https://www.uab.gov.tr)
