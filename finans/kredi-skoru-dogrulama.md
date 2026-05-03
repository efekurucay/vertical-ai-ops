# Kredi Skoru Doğrulama Motoru

> **Sector:** Finans / Bankacılık  
> **Difficulty:** Medium  
> **Market Size (TR):** Tüm BDDK lisanslı bankalar + kredi kuruluşları  
> **Monetization:** B2B SaaS, white-label API

---

## Problem

LLM'ler müşteri finansal verisini analiz edip kredi uygunluk kararı önerebilir. Ancak bu önerilerin **BDDK'nın kredi sınıflandırma yönetmeliğine, bankanın iç politikasına veya tüketici koruma mevzuatına** uygun olup olmadığı doğrulanamaz.

Daha da önemlisi: LLM "bu müşteri kredi alabilir" dediğinde **hangi DTI (Debt-to-Income) oranı hesabına, hangi teminat değerlemesine, hangi kara liste kontrolüne** dayandığını açıklayamaz — bu da hem yasal hem etik sorun yaratır.

---

## The Validation Layer

- DTI (Borç/Gelir) oranı BDDK limitlerini aşıyor mu?
- Müşteri Kredibil veya KKB'de aktif icra/takip kaydı var mı?
- Teklif edilen faiz oranı TCMB azami faiz sınırını aşıyor mu?
- Bireysel kredi limitinin yasal üst sınırını (aylık gelirin 4 katı) aşıyor mu?
- KVKK kapsamında rıza belgesi mevcut mu?

---

## Technical Architecture

```
[Müşteri Başvurusu]
      │
      ▼
[LLM — Başvuru özetleme + ilk değerlendirme]
      │
      ▼
[Kural Motoru]
  ├── KKB/Findeks API entegrasyonu
  ├── DTI Hesaplama Modülü
  ├── TCMB Faiz Limiti Kontrolü
  ├── Yasal Limit Kontrolü
  └── KVKK Rıza Doğrulama
      │
      ▼
[Karar: ONAYLA / KOŞULLU / REDDET + Gerekçe Kodu]
```

---

## Tech Stack

- **LLM**: Claude Haiku (hız gerektiren ilk sınıflandırma için)
- **Kural Motoru**: Python rules engine (rule-engine kütüphanesi)
- **Veri**: KKB/Findeks entegrasyonu, TCMB API
- **Backend**: Node.js / FastAPI
- **Audit**: Immutable log (PostgreSQL + event sourcing)

---

## Business Model

- **Target customer**: Fintech kredi platformları, dijital bankalar, tüketici finansmanı şirketleri
- **Pricing model**: Sorgu başına ücretlendirme veya aylık API aboneliği
- **Neden ödeyecekler**: Manuel kredi analist maliyeti vs. otomatik karar maliyeti; ayrıca BDDK denetimine hazırlık

---

## Turkey Context

- **BDDK Kredi Sınıflandırma Yönetmeliği** ve **Bireysel Kredilerde Borç/Gelir Oranı** sınırlamaları (2019 sonrası güncellemeler) direkt kaynak
- KKB (Kredi Kayıt Bürosu) API'si resmi entegrasyon ortaklığı gerektiriyor — MVP için mock data ile başla
- TÜBİTAK 1507 "Finansal Teknolojiler" kategorisine uygun

---

## Getting Started (MVP in a Weekend)

1. BDDK DTI kurallarını ve TCMB faiz limitlerini JSON config dosyasına yaz
2. Basit kural motoru: gelir/borç girdisi alır, limitleri kontrol eder
3. LLM katmanı: ret gerekçesini insan-okunabilir dile çevirir
4. API endpoint olarak sun

---

## Resources

- [BDDK Yönetmelikleri](https://www.bddk.org.tr/Mevzuat)
- [KKB Entegrasyon Dokümantasyonu](https://www.kkb.com.tr)
- [TCMB Faiz Kararları](https://www.tcmb.gov.tr)
