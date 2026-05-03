# Sözleşme Uyum Motoru

> **Sector:** Hukuk / LegalTech  
> **Difficulty:** Medium  
> **Market Size (TR):** 80.000+ avukat, 3M+ KOBİ  
> **Monetization:** B2B SaaS, freemium API

---

## Problem

LLM'ler sözleşme taslağı oluşturmada iyi. Sorun: üretilen sözleşmenin **Türk Borçlar Kanunu, Türk Ticaret Kanunu, KVKK veya özel sektör düzenlemelerine** aykırı maddeler içerip içermediğini bilmez.

Örneğin: LLM tüketici sözleşmesine "tek taraflı değişiklik hakkı" maddesi yazabilir — ancak bu Tüketicinin Korunması Hakkında Kanun'a (6502) göre geçersiz ve haksız şart sayılır. Bir avukat veya hukuk departmanı olmayan KOBİ bu hatayı fark etmeyebilir.

---

## The Validation Layer

- Sözleşme türüne göre zorunlu madde var mı? (iş sözleşmesinde kıdem bilgisi, kira sözleşmesinde depozito limiti)
- Haksız şart listesindeki ifadeler var mı? (6502 sayılı Kanun eki)
- KVKK gerektiren rıza ve aydınlatma metni eklenmiş mi?
- Tüketici sözleşmesiyse cayma hakkı bilgisi mevcut mu?
- Ticari sözleşmede faiz oranı yasal limiti aşıyor mu?

```
Sözleşme Taslağı → LLM (üretim/düzenleme) → Hukuki Kural Motoru → Onay veya Uyarı Listesi
```

---

## Technical Architecture

```
[Kullanıcı isteği veya mevcut sözleşme]
      │
      ▼
[LLM — Sözleşme taslağı üretir veya revize eder]
      │
      ▼
[NLP Parser — Maddeleri ayrıştırır, tiplerini sınıflar]
      │
      ▼
[Kural Motoru]
  ├── Zorunlu Madde Kontrolleri (sözleşme tipine göre)
  ├── Haksız Şart Listesi Eşleştirme
  ├── KVKK Checklist
  ├── Faiz/Ceza Limiti Kontrolü
  └── Sektörel Özel Kurallar
      │
      ▼
[Sonuç: Temiz / Uyarılar + Madde Referansı / Bloke]
```

---

## Tech Stack

- **LLM**: GPT-4o (sözleşme üretimi), Claude 3.5 (analiz)
- **NLP**: spaCy (Türkçe model) + custom entity recognition
- **Kural Motoru**: Python + JSON rule definitions
- **Hukuki DB**: Mevzuat.gov.tr parse edilmiş içerik
- **Backend**: FastAPI
- **Frontend**: Next.js (avukat/KOBİ dashboard)

---

## Business Model

- **Target customer**: Hukuk departmanı olmayan KOBİ'ler, serbest avukatlar, HR departmanları (iş sözleşmeleri)
- **Freemium**: Ayda 3 sözleşme ücretsiz, sonrası abonelik
- **Enterprise**: Sınırsız + API + özel kurallar
- **Güçlü argüman**: Hukuki danışmanlık saatinin maliyeti vs. aylık abonelik

---

## Turkey Context

- **Mevzuat.gov.tr** tüm kanunları barındırıyor, ancak makine-okunabilir formatta değil
- Yargıtay içtihatları da doğrulama için kritik — Adalet Bakanlığı'nın UYAP sistemi kısmen erişilebilir
- LegalTech Türkiye'de henüz çok erken aşamada; ciddi bir rakip yok
- TÜBİTAK BIGG programı bu tür B2B SaaS girişimleri için aktif destek veriyor

---

## Getting Started (MVP in a Weekend)

1. 6502 sayılı Kanun'daki haksız şart listesini JSON'a aktar (yaklaşık 30 madde)
2. Regex + basit NLP: sözleşme metninde bu ifadeleri ara
3. LLM: bulunan her sorunlu madde için "neden sorun, nasıl düzelt" açıklaması üret
4. Basit web UI: metin yapıştır, rapor al

---

## Resources

- [Türk Borçlar Kanunu](https://www.mevzuat.gov.tr/mevzuatmetin/1.5.6098.pdf)
- [6502 Sayılı Tüketicinin Korunması Hakkında Kanun](https://www.mevzuat.gov.tr/mevzuatmetin/1.5.6502.pdf)
- [KVKK Mevzuat](https://www.kvkk.gov.tr/Icerik/4150/Mevzuat)
