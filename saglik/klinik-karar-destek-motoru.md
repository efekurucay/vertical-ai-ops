# Klinik Karar Destek Motoru

> **Sector:** Sağlık  
> **Difficulty:** High  
> **Market Size (TR):** 1.500+ hastane, 25.000+ aile hekimi
> **Monetization:** B2B SaaS (hastane), API (EHR entegrasyonu)

---

## Problem

LLM'ler semptom listesinden olası tanılar üretebilir, tedavi protokolü önerebilir. Ancak üretilen önerinin **Türkiye İlaç ve Tıbbi Cihaz Kurumu (TİTCK) onaylı endikasyonlarla, hastanın alerjileriyle, mevcut ilaçlarıyla ve SGK geri ödeme kriterleriyle** uyumlu olup olmadığını bilmez.

Tıpta "plausible but wrong" ölümcül olabilir. Bir LLM'in "mantıklı görünen" bir ilaç kombinasyonu önerisini klinisyen fark etmeden uygularsa ciddi ilaç etkileşimi yaşanabilir.

---

## The Validation Layer

- Önerilen ilaç, hastanın bildirilen alerjileriyle çakışıyor mu?
- İki veya daha fazla ilaç arasında bilinen ciddi etkileşim var mı? (CYP450 metabolizması)
- Önerilen doz yaş/kilo/böbrek fonksiyonu için uygun mu?
- SGK bu ilacı bu tanıyla geri ödüyor mu?
- TİTCK bu ilacı bu endikasyon için onaylamış mı?

```
Anamnez + Semptomlar → LLM (olası tanı + tedavi taslağı) → Klinik Kural Motoru → Güvenli Öneri
```

---

## Technical Architecture

```
[Hasta Verisi (EHR)]
      │
      ▼
[LLM — Tanı taslağı + protokol önerisi]
      │
      ▼
[Kural Motoru]
  ├── TİTCK İlaç Veritabanı
  ├── İlaç Etkileşim DB (DrugBank / custom TR)
  ├── SGK Geri Ödeme Kriterleri
  ├── Doz Hesaplama Modülü (yaş/kilo/GFR)
  └── Alerji Çakışma Kontrolü
      │
      ▼
[Klinisyen Ekranı: Onaylandı / Uyarı / Bloke + Gerekçe]
```

---

## Tech Stack

- **LLM**: GPT-4o veya Meditron (tıp fine-tune modeli)
- **İlaç DB**: TİTCK resmi veri + DrugBank API
- **Kural Motoru**: Python + medical-specific DSL
- **EHR Entegrasyon**: HL7 FHIR standardı
- **Backend**: FastAPI + PostgreSQL

---

## Business Model

- **Target customer**: Özel hastaneler, poliklinik zincirleri, aile hekimliği yazılım sağlayıcıları
- **Pricing model**: Hasta başına aylık SaaS veya EHR modülü lisansı
- **Güçlü satış argümanı**: Tıbbi hata sigortası maliyetini düşürür; JCI akreditasyon gerekliliklerini destekler

---

## Turkey Context

- TİTCK'nin ilaç veritabanı resmi olarak mevcut ancak API sunulmuyor — PDF/Excel parse etmek ilk teknik engel
- SGK geri ödeme listesi (SUT) düzenli güncelleniyor, makine-okunabilir versiyon kısmen erişilebilir
- Sağlık Bakanlığı'nın HBYS sistemleriyle entegrasyon uzun vadeli hedef
- TÜBİTAK 1507 "Dijital Sağlık" kategorisi + Sağlık Bakanlığı dijital dönüşüm hibeleri mevcut

---

## Getting Started (MVP in a Weekend)

1. TİTCK sitesinden 1.000 ilaçlık bir subset indir, JSON'a dönüştür
2. Basit etkileşim kontrolü: 50 kritik ilaç çifti manuel olarak tanımla
3. FastAPI endpoint: ilaç listesi gönder, etkileşim raporu al
4. LLM: etkileşim uyarısını klinisyene anlaşılır dille açıklar

---

## Resources

- [TİTCK Beşeri İlaçlar Veritabanı](https://www.titck.gov.tr)
- [DrugBank API](https://www.drugbank.com)
- [HL7 FHIR Standartları](https://www.hl7.org/fhir)
- [SGK SUT Listeleri](https://www.sgk.gov.tr)
