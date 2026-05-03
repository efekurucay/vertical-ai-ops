# Organik Sertifika Uyum Motoru

> **Sector:** Tarım / Organik  
> **Difficulty:** Medium  
> **Market Size (TR):** 80.000+ organik tarım işletmesi  
> **Monetization:** SaaS, sertifikasyon kuruluşu entegrasyonu

## Problem

LLM organik tarım planı veya tarım kaydı belgesi oluşturabilir. Ancak bu belgeler ile pratiklerin **Organik Tarımın Esasları ve Uygulanmasına İlişkin Yönetmelik ve AB Organik Yönetmeliği (2018/848) gerekliliklerine** uygunluğunu doğrulayamaz.

## The Validation Layer

- Dönüşüm süresi dolmuş mu? (çoğunlukla 2-3 yıl)
- Kullanılan girdiler izinli listede mi?
- Tampon bölge ve komsu tarım alanı kontaminasyon riski değerlendirilmiş mi?
- Kayıt tutma zorunlulukları karşılanıyor mu?
- Sertifikasyon kuruluşu yetkili mi? (T.C. akreditasyonu)

## Tech Stack

- **Kural Motoru:** Python + organik gıda mevzuat JSON
- **LLM:** GPT-4o (tarım planı üretimi)
- **Backend:** FastAPI + SQLite (küçük işletmeler için)

## Business Model

- **Target:** Organik tarım işletmeleri, sertifikasyon kuruluşları
- **Pricing:** İşletme başına yıllık abonelik
- **Argüman:** Sertifika kaybı = premium fiyat kaybı + pazar erişimi kaybı

## Turkey Context

- Tarım Bakanlığı organik tarımı destekliyor ancak denetim kapasitesi sınırlı
- Türkiye'den AB'ye organik ürün ihracatı büycdüyor — AB uyumu kritik
- Yönetmelik 2023'te güncellendi, pek çok işletme yeni gereklilikleri bilmiyor

## Getting Started

1. İzin verilen girdi listesini JSON'a aktar
2. Dönüşüm takvimi kontrolü: başlangıç tarihi + süre
3. Kayıt tutma checklist üret
4. LLM uyumsuz uygulamalar için alternatif önerir
