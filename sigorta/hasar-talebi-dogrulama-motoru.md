# Hasar Talebi Doğrulama Motoru

> **Sector:** Sigorta
> **Difficulty:** Medium
> **Market Size (TR):** 60+ sigorta şirketi, milyonlarca yıllık hasar talebi
> **Monetization:** B2B SaaS, API entegrasyonu

## Problem

LLM hasar taleplerini analiz edip ödeme kararı önerebilir. Ancak bu önerinin **poliçe kapsamı, muafiyet tutarları, bekleme süreleri, hariç tutulan durumlar ve TRAMER kurallarıyla** uyumlu olup olmadığını doğrulayamaz. Hatalı ödeme hem şirkete zarar verir hem de sigortalıya haksızlık olur.

## The Validation Layer

- Hasar, poliçe kapsamında mı?
- Muafiyet tutarı düşüldü mü?
- Bekleme süresi dolmuş mu?
- Hasar tarihi poliçe geçerlilik süresi içinde mi?
- TRAMER'de daha önce aynı hasar bildirilmiş mi?
- Hasar miktarı sigortalı değeri aşıyor mu?

```
Hasar Bildirimi → LLM (analiz ve taslak karar) → Sigorta Kural Motoru → Ödeme / Red / İnceleme
```

## Technical Architecture

```
[Hasar Formu + Belgeler]
      ↓
[LLM — Hasar özeti ve ön değerlendirme]
      ↓
[Sigorta Kural Motoru]
  ├── Poliçe Kapsam Kontrolü
  ├── Muafiyet Hesaplama
  ├── Bekleme Süresi Kontrolü
  ├── TRAMER Sorgulama
  └── Sigortalı Değer Kontrolü
      ↓
[Karar: ÖDE / REDDET / UZMAN İNCELEMESİ]
```

## Tech Stack

- **LLM**: Claude 3.5 Sonnet (belge analizi)
- **DB**: PostgreSQL (poliçe veritabanı)
- **API**: TRAMER entegrasyonu
- **Backend**: FastAPI

## Business Model

- **Target**: Sigorta şirketleri, acente yönetim sistemleri
- **Pricing**: İşlem başına API ücreti
- **Argüman**: Hasar inceleme maliyetini %40-60 düşürür

## Turkey Context

- TRAMER (Trafik Sigortaları Bilgi Merkezi) entegrasyonu zorunlu araç sigortaları için
- SEDDK (Sigortacılık ve Özel Emeklilik Düzenleme Denetleme Kurumu) denetimi
- TÜBİTAK 1507 InsurTech kategorisi

## Getting Started

1. Basit poliçe JSON şeması oluştur
2. Muafiyet ve kapsam kontrol kurallarını yaz
3. LLM hasar bildirimi özetini bu kurallara göre test et
4. TRAMER mock API ile test

## Resources

- [SEDDK](https://www.seddk.gov.tr)
- [TRAMER](https://www.tramer.com.tr)
