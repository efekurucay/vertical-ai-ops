# KVKK/GDPR Veri İşleme Uyum Motoru

> **Sector:** Yazılım / IT / Legal-Tech  
> **Difficulty:** Medium  
> **Market Size (TR):** Tüm kişisel veri işleyen şirketler (KVKK kapsamı: her ölçekten işletme)  
> **Monetization:** B2B SaaS, developer API

---

## Problem

Bir LLM'e "bu özellik için KVKK uyumlu bir veri işleme politikası yaz" dediğinizde makul görünen bir metin üretir. Ancak bu metnin **KVKK Madde 5, 6, 10 ve ilgili KVKK Kurul kararlarına** gerçekten uygun olup olmadığını bilemez.

En yaygın hatalar: hukuki dayanak (meşru menfaat vs. açık rıza) yanlış seçilmesi, aydınlatma yükümlülüğünün eksik yerine getirilmesi, veri saklama süresinin belirtilmemesi, yurt dışı aktarım kontrolünün atlanması.

---

## The Validation Layer

- Veri işleme faaliyeti için uygun hukuki dayanak seçilmiş mi? (rıza, sözleşme, meşru menfaat)
- Aydınlatma metni KVKK Madde 10 gerekliliklerini karşılıyor mu? (8 zorunlu unsur)
- Veri saklama süresi belirtilmiş mi ve orantılı mı?
- Yurt dışı aktarım varsa KVKK Madde 9 uygulanmış mı?
- VERBİS kaydı gerekiyor mu? (yıllık 50+ çalışan veya özel nitelikli veri)
- Açık rıza alınıyorsa özgür iradeye dayalı, ayrıştırılmış ve geri alınabilir mi?

---

## Technical Architecture

```
[Veri İşleme Aktivitesi Tanımı]
      │
      ▼
[LLM — Politika/aydınlatma metni üretir]
      │
      ▼
[KVKK Kural Motoru]
  ├── Hukuki Dayanak Uygunluk Kontrolü
  ├── Aydınlatma Metni 8-Unsur Checklist
  ├── Saklama Süresi Orantılılık Kontrolü
  ├── Yurt Dışı Aktarım Tespiti
  ├── VERBİS Yükümlülüğü Değerlendirme
  └── GDPR Ek Kontrolleri (AB hedef kitle varsa)
      │
      ▼
[Uyumluluk Skoru + Madde Referanslı Eksik Listesi]
```

---

## Tech Stack

- **LLM**: GPT-4o veya Claude 3.5 (metin üretimi + analiz)
- **Kural Motoru**: Python + JSON rule definitions
- **Hukuki Kaynak**: KVKK mevzuat parse edilmiş, KVKK Kurul kararları vektör DB
- **Backend**: FastAPI
- **Frontend**: Next.js (uyumluluk dashboard)

---

## Business Model

- **Target customer**: Veri sorumlusu olan her şirket (özellikle yazılım/SaaS şirketleri, e-ticaret, fintech)
- **Freemium**: Tek politika analizi ücretsiz
- **Pro**: Sınırsız analiz + VERBİS hazırlık + otomatik güncelleme bildirimi
- **Enterprise**: API entegrasyonu + custom kural setleri

---

## Turkey Context

- KVKK Kurulu aktif olarak ceza veriyor (2024'te 10M+ TL cezalar kesildi)
- KOBİ'lerin büyük çoğunluğu VERBİS yükümlülüklerinden habersiz
- Hem KVKK hem GDPR uyumu gereken şirket sayısı artıyor (Türk yazılım ihracatı)
- TÜBİTAK 1507 "Siber Güvenlik ve Veri Gizliliği" kategorisi

---

## Getting Started (MVP in a Weekend)

1. KVKK Madde 10'un 8 zorunlu unsurunu JSON kural olarak tanımla
2. LLM ürettiği aydınlatma metnini bu 8 unsur için kontrol et
3. Eksik unsur varsa LLM'e "şu unsur eksik, ekle" komutu ver
4. Basit web arayüzü: metin gir, uyumluluk raporu al

---

## Resources

- [KVKK Mevzuat](https://www.kvkk.gov.tr/Icerik/4150/Mevzuat)
- [KVKK Kurul Kararları](https://www.kvkk.gov.tr/Icerik/5309/Karar-Arama)
- [GDPR Full Text](https://gdpr-info.eu)
- [VERBİS Kılavuzu](https://verbis.kvkk.gov.tr)
