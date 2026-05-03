# Deprem Yönetmeliği Uyum Motoru (TBDY 2018)

> **Sector:** İnşaat / Mühendislik  
> **Difficulty:** High  
> **Market Size (TR):** 300B USD+ inşaat sektörü, 200.000+ lisanslı inşaat mühendisi  
> **Monetization:** B2B SaaS, proje başı lisans

---

## Problem

LLM'ler statik hesap sonuçları, zemin raporu verileri veya mimari proje tanımlaması üzerinden TBDY 2018 uyumluluğu hakkında yorum yapabilir. Ancak bu yorumun **gerçekten TBDY 2018 Bölüm 3, Madde 4.3.4 veya ilgili TS standartlarına** uygun olup olmadığını deterministik olarak ispatlayamaz.

Deprem ülkesi olan Türkiye'de bu doğrulama eksikliği can ve mülk güvenliği açısından kritiktir. 2023 Kahramanmaraş depremi bu sorunun ne kadar hayati olduğunu bir kez daha gösterdi.

---

## The Validation Layer

- Bina deprem yükleri TBDY 2018 Tablo 4.1'e göre doğru hesaplanmış mı?
- Zemin sınıfı (ZA-ZE) deprem tehlike haritasından doğru alınmış mı?
- Perde duvar/kolon oranları minimum gereklilikleri karşılıyor mu?
- Kolon boyutları TBDY minimum şartlarını sağlıyor mu?
- Kat adedine göre bina yükseklik sınıfı doğru belirlenmiş mi?

```
Bina Verileri + Zemin Raporu → LLM (hesap taslağı) → TBDY 2018 Kural Motoru → Kontrol Raporu
```

---

## Technical Architecture

```
[Proje Parametreleri]
(kat adedi, alan, zemin, konum)
      │
      ▼
[LLM — Hesap taslağı + öneri üretir]
      │
      ▼
[TBDY 2018 Kural Motoru]
  ├── Deprem Tehlike Haritası API (AFAD)
  ├── Zemin Sınıfı Doğrulama
  ├── Yük Kombinasyonu Kontrolleri
  ├── Minimum Kesit Gereklilikleri
  └── Bölgesel Katsayı Tabloları
      │
      ▼
[Kontrol Raporu: Madde bazında PASS/FAIL + Bölüm Referansı]
      │
      ▼
[Mühendis İmzası İçin Hazır Çıktı]
```

---

## Tech Stack

- **LLM**: GPT-4o veya Claude (hesap anlatımı)
- **Kural Motoru**: Python (numpy tabanlı hesap doğrulama)
- **Veri**: AFAD Deprem Tehlike Haritası API, TBDY 2018 PDF → JSON parse
- **Hesap**: Sonlu elemanlar kontrol için açık kaynak: OpenSees
- **Backend**: FastAPI
- **Frontend**: Next.js + 3D görselleştirme (Three.js)

---

## Business Model

- **Target customer**: İnşaat mühendisliği büroları, müteahhitler, belediye teknik birimleri
- **Pricing model**: Proje başı ücret (küçük bina: 500 TL, büyük proje: 5.000 TL)
- **Güçlü argüman**: Yapı denetim firmaları bu kontrolü manuel yapıyor; otomasyon denetim maliyetini %60 düşürür

---

## Turkey Context

- AFAD'ın güncel deprem tehlike haritası API olarak erişilebilir
- Çevre, Şehircilik ve İklim Değişikliği Bakanlığı e-yapı ruhsatı sistemine entegrasyon orta vadede mümkün
- Kahramanmaraş depremi sonrası yasa değişiklikleri yapı denetimini daha sıkı hale getirdi — pazar ihtiyacı arttı
- TÜBİTAK 1507 "Afet Risk Azaltma" kategorisi

---

## Getting Started (MVP in a Weekend)

1. TBDY 2018'den kolon minimum boyutları ve kat yüksekliği tablolarını JSON'a aktar
2. Basit Python fonksiyon: kolon boyutu + kat adedi girdisi alır, TBDY kuralını kontrol eder
3. AFAD API'den spektrum değeri çek (koordinat girdisiyle)
4. LLM: başarısız kontroller için düzeltme önerisi üretir

---

## Resources

- [TBDY 2018 — Türkiye Bina Deprem Yönetmeliği](https://www.afad.gov.tr/deprem-yonetmeligi)
- [AFAD Deprem Tehlike Haritası](https://tdth.afad.gov.tr)
- [OpenSees Açık Kaynak FEM](https://opensees.berkeley.edu)
