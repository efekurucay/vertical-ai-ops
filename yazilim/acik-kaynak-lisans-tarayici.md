# Açık Kaynak Lisans Uyumluluk Tarayıcısı

> **Sector:** Yazılım / IT  
> **Difficulty:** Low-Medium  
> **Market Size (Global):** Her yazılım şirketi (özellikle IP-sensitive ürünler)  
> **Monetization:** Developer tool SaaS, CI/CD entegrasyon aboneliği

---

## Problem

LLM'e "bu bağımlılık listesi için lisans riski nedir?" diye sorduğunuzda genel bilgi verebilir ama **GPL-3.0'ın copyleft etkisinin projenin özel kaynak kodunu nasıl etkilediğini, hangi kullanım senaryosunda LGPL'nin sorun çıkarıp çıkarmadığını veya Apache 2.0 ile MIT'nin patent maddelerinin nasıl farklılaştığını** deterministik olarak analiz edemez.

Sonuç: Yazılım şirketleri ticari ürünlerine farkında olmadan GPL bağımlılığı ekliyor, bu da kaynak kodu açma zorunluluğu doğuruyor.

---

## The Validation Layer

- Kullanılan her bağımlılık hangi lisansa sahip? (direkt + transitif)
- Herhangi bir lisans projenin kullanım senaryosuyla uyumsuz mu? (copyleft + proprietary)
- GPL/AGPL bağımlılık varsa: statik/dinamik link ayrımına göre risk nedir?
- Çift lisanslı bağımlılıklar var mı? Hangi lisans seçilmiş?
- SPDX standardında lisans bildirimleri mevcut mu?

```
package.json / requirements.txt → Lisans Tarayıcı → Uyumluluk Matrisi → Risk Raporu
```

---

## Technical Architecture

```
[Bağımlılık Dosyası]
(package.json, requirements.txt, go.mod, Gemfile)
      │
      ▼
[Bağımlılık Çözücü — Transitif ağacı genişletir]
      │
      ▼
[Lisans Tespiti]
  ├── npm registry / PyPI / GitHub API
  ├── SPDX License DB
  └── ClearlyDefined.io
      │
      ▼
[Uyumluluk Kural Motoru]
  ├── Lisans Uyumluluk Matrisi
  ├── Kullanım Senaryosu Profili (SaaS / Gömülü / Dağıtım)
  └── Copyleft Bulaşma Analizi
      │
      ▼
[Risk Raporu: Yeşil / Sarı / Kırmızı + Alternatif Öneri]
      │
      ▼
[LLM — Riski proje bağlamında açıklar, alternatif kütüphane önerir]
```

---

## Tech Stack

- **Kural Motoru**: Python + SPDX lisans uyumluluk matrisi (JSON)
- **Lisans Veri**: ClearlyDefined.io API, npm/PyPI metadata
- **LLM**: Claude Haiku (hızlı açıklama + alternatif öneri)
- **CI/CD**: GitHub Actions, GitLab CI entegrasyon
- **Backend**: FastAPI
- **Frontend**: Next.js (proje dashboard)

---

## Business Model

- **Target customer**: Kurumsal yazılım şirketleri, M&A due diligence süreçleri, açık kaynak kullanan SaaS'lar
- **Freemium**: Küçük projeler ücretsiz
- **Pro**: Sınırsız proje + CI/CD entegrasyon + haftalık tarama
- **Enterprise**: Özel kural setleri + SBOM (Software Bill of Materials) üretimi
- **Güçlü zaman**: Log4Shell ve diğer supply chain güvenlik olayları sonrası bu alan çok sıcak

---

## Turkey Context

- Yerli yazılım ihracatının artmasıyla IP uyumluluğu kritik hale geliyor
- ABD/AB'ye yazılım satan Türk şirketleri lisans uyumluluğunu ihale şartı olarak görmeye başladı
- FOSS.TR topluluğu ve TBD (Türkiye Bilişim Derneği) bu konuda farkındalık oluşturmaya çalışıyor

---

## Getting Started (MVP in a Weekend)

1. SPDX lisans uyumluluk matrisini JSON olarak al (açık kaynak mevcut: `spdx/license-list-data`)
2. `package.json` parser: bağımlılıkları çıkar, npm API'den lisansları al
3. Uyumluluk matrisiyle çapraz kontrol: GPL + proprietary = kırmızı işaretle
4. LLM: kırmızı işaretli bağımlılık için alternatif MIT/Apache lisanslı kütüphane öner

---

## Resources

- [SPDX License List](https://spdx.org/licenses)
- [ClearlyDefined.io](https://clearlydefined.io)
- [FOSSA (competitor, inspiration)](https://fossa.com)
- [OSS Review Toolkit](https://github.com/oss-review-toolkit/ort)
