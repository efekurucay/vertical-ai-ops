# KYC/AML Kural Motoru

> **Sector:** Finans / Bankacılık  
> **Difficulty:** High  
> **Market Size (TR):** ~50+ banka, 400+ finansal kurum  
> **Monetization:** B2B SaaS, API lisansı

---

## Problem

Bir LLM'e "bu müşteri profili KYC uyumlu mu?" diye sorduğunuzda makul görünen ama **MASAK yönetmeliğine, FATF tavsiyelerine veya müşteri kurumun iç risk kriterlerine** aykırı bir değerlendirme üretebilir. Finansal kurum çalışanı bu çıktıyı referans alırsa hem yasal sorumluluk hem düzenleyici ceza riski doğar.

LLM'in temel sorunu: "risk yüksek görünüyor" diyebilir ama **hangi MASAK maddesine göre, hangi işlem eşiğini aşarak** risk oluştuğunu deterministik olarak ispatlayamaz.

---

## The Validation Layer

Doğrulama katmanı şunları kontrol eder:

- İşlem tutarı yasal bildirим eşiklerini aşıyor mu? (Türkiye'de 225.000 TL ve üzeri)
- Müşteri, MASAK'ın yayımladığı terör finansmanı listelerinde var mı?
- PEP (Politically Exposed Person) statüsü var mı?
- İşlem örüntüsü yapısal parçalama (structuring) belirtisi taşıyor mu?
- Coğrafi risk: işlem FATF'ın yüksek riskli ülke listesindeki bir ülkeyi kapsıyor mu?

Her kontrol için **kural gerekçesi** (hangi madde, hangi liste, hangi tarihli güncellemesiyle) kaydedilir ve audit trail oluşturulur.

```
Müşteri Verisi → LLM (narratif risk özeti) → MASAK Kural Motoru → Onay / Red + Gerekçe
```

---

## Technical Architecture

```
[Müşteri Verisi]
      │
      ▼
[LLM — Narratif risk özeti üretir]
      │
      ▼
[Kural Motoru]
  ├── MASAK Liste API (günlük güncelleme)
  ├── FATF Ülke Risk Listesi
  ├── İşlem Eşik Kontrolleri
  ├── PEP Database
  └── Structuring Pattern Detector
      │
      ▼
[Sonuç: PASS / FLAG / BLOCK + Madde Referansı]
      │
      ▼
[Audit Log + Uyumluluk Raporu]
```

---

## Tech Stack

- **LLM**: GPT-4o veya Claude 3.5 Sonnet (narratif özet için)
- **Kural Motoru**: Python + Pydantic validation + custom rule DSL
- **Listeler**: MASAK resmi API, OFAC SDN list, UN Sanctions
- **DB**: PostgreSQL (audit log), Redis (gerçek zamanlı liste cache)
- **Backend**: FastAPI
- **Frontend**: Next.js (compliance officer dashboard)

---

## Business Model

- **Target customer**: Orta ölçekli bankalar, ödeme kuruluşları, kripto borsaları
- **Pricing model**: İşlem başına API ücreti (0.01–0.05 USD/sorgu) veya aylık SaaS
- **Neden ödeyecekler**: MASAK cezaları 6 haneli TL'yi aşıyor; mevcut çözümler pahalı ve entegrasyonu zor
- **Sales motion**: Compliance officer → CTO → procurement

---

## Turkey Context

- **MASAK** (Mali Suçları Araştırma Kurulu) düzenli liste güncellemeleri yayımlıyor ancak bunlar makine-okunabilir formatta değil — ilk MVP bu listeyi parse edip API'ye dönüştürmekle başlayabilir
- **5549 sayılı Kanun** ve **Suç Gelirlerinin Aklanmasının Önlenmesi Hakkında Yönetmelik** ana yasal çerçeve
- TÜBİTAK 1507 programı bu tür regtech çözümleri için uygun — "yapay zeka destekli uyum otomasyonu" başlığı altında başvurulabilir

---

## Getting Started (MVP in a Weekend)

1. MASAK'ın güncel terör listesini PDF'ten parse et, JSON'a dönüştür
2. FastAPI endpoint: müşteri adı + TCKN alır, liste kontrolü yapar, sonuç döner
3. LLM katmanı ekle: pozitif match'lerde narratif açıklama üretir
4. Basit Next.js dashboard: arama + sonuç gösterimi

---

## Resources

- [MASAK Resmi Sitesi](https://www.masak.gov.tr)
- [FATF High-Risk Countries List](https://www.fatf-gafi.org/en/topics/high-risk-and-other-monitored-jurisdictions.html)
- [5549 Sayılı Kanun](https://www.mevzuat.gov.tr/mevzuatmetin/1.5.5549.pdf)
