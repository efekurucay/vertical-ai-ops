# Pestisit Kalıntı Limit Kontrol Motoru

> **Sector:** Tarım / Gıda Güvenliği  
> **Difficulty:** Medium  
> **Market Size (TR/Global):** Tarımsal ihracatçılar, gıda işleyiciler  
> **Monetization:** B2B SaaS, laboratuvar entegrasyonu

## Problem

LLM pestisit kalıntı analiz raporunu okuyup değerlendirme yapabilir. Ancak tespit edilen değerlerin **Türkiye Gıda Kodeksi, AB MRL (Maksimum Kalıntı Limitleri) direktifi veya hedef pazara göre ABD EPA limitleri** açısından uyumlu olup olmadığını deterministik olarak doğrulayamaz. Uyumsuz ürün = ihracatın iade edilmesi veya imhası.

## The Validation Layer

- Her pestisit bileşeni için ölçülen değer hedef pazar MRL'sını aşıyor mu?
- Ürn çeşidi + pestisit kombinasyonu için geçerli MRL doğru seçilmiş mi?
- Birden fazla pestisit varsa kumulatif etki değerlendirmesi gerekiyor mu?
- Ürün organik sertifikalıysa izinli pestisitler listesiyle uyumlu mu?

## Tech Stack

- **Kural Motoru:** Python + AB Pesticides MRL DB (resmi API mevcut)
- **LLM:** Claude 3.5 (lab raporu parse + açıklama)
- **Veri:** EU MRL Database, EPA Database, Tarım Bakanlığı GİP
- **Backend:** FastAPI

## Business Model

- **Target:** Sebze-meyve ihracatçıları, gıda işleyiciler, organik sertifika kuruluşları
- **Pricing:** Analiz başına veya yıllık abonelik
- **Argüman:** AB 2023'te Türkiye'den ihracatında pestisit ihlali gerekçesiyle onlarca sevkiyat iade etti

## Turkey Context

- Türkiye dünyanın en büyük sebze-meyve ihracatçılarından biri
- AB, Rusya, Körfez ülkeleri farklı MRL standartları uyguluyor — çok hedef pazar desteği kritik
- Tarım Bakanlığı'nın izinli pestisit listesi (GİP) düzenli güncelleniyor

## Getting Started

1. AB MRL veri tabanını API ile çek (resmi AB endpoint mevcut)
2. CSV formatındaki lab raporu parse et: bileşen + mg/kg değeri
3. Her bileşen için MRL kontrolü yap, aşan değerleri işaretle
4. LLM: uyumsuz ürün için alternatif pazar veya düzeltici eylem öner

## Resources

- [EU MRL Database](https://ec.europa.eu/food/plant/pesticides/eu-pesticides-database)
- [Tarım Bakanlığı GİP Listesi](https://www.tarimorman.gov.tr)
- [Codex Alimentarius MRLs](https://www.fao.org/fao-who-codexalimentarius)
