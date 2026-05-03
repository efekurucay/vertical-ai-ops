# Pestisit Kalıntı Limit Kontrol Motoru

> **Sector:** Tarım / Gıda Güvenliği
> **Difficulty:** Medium
> **Market Size (TR):** 500.000+ tarımsal işletme, gıda ihracatı
> **Monetization:** B2B SaaS (ihracatçı, gıda üreticisi)

## Problem

LLM tarım ilaçlaması planı veya gıda güvenliği raporu oluşturabilir. Ancak kullanılan pestisitlerin **Türk Gıda Kodeksi'ndeki MRL (Maksimum Kalıntı Limiti) değerlerine, AB'nin EC No 396/2005 tüzüğüne ve hedef pazarın özel gerekliliklerine** uygun olup olmadığını doğrulayamaz.

## The Validation Layer

- Kullanılan pestisit bu ürün/ürün grubu için kayıtlı mı?
- Uygulama miktarı MRL limitini aşmayacak şekilde mi planlandı?
- Son uygulama-hasat aralığı (PHI) yeterli mi?
- Hedef pazar (AB, Japonya, ABD) için özel MRL farklılıkları var mı?
- Bekleme süresi tüm kombine uygulanan ilaçlar için karşılanıyor mu?

## Tech Stack

- **LLM**: Claude (ilaçlama planı taslağı)
- **MRL Veritabanı**: EU Pesticide Database API + Gıda Kodeksi
- **Kural Motoru**: Python + ürün/ilaç/pazar matrisi
- **Backend**: FastAPI

## Business Model

- **Target**: Tarım ihracatçıları, gıda üreticileri, tarım danışmanları
- **Pricing**: Kullanıcı başına aylık SaaS
- **Argüman**: İhracatta ürün reddi ve gümrük karantinası maliyetleri

## Turkey Context

- Türkiye'nin meyve-sebze ihracatında AB MRL uyumsuzluğu sık karşılaşılan sorun
- Gıda Tarım ve Hayvancılık Bakanlığı pestisit kayıt sistemi
- TÜBİTAK TEYDEB AgriTech kategorisi

## Getting Started

1. EU Pesticide Database API ile top 50 ihraç ürünü için MRL listesi çek
2. Ürün + pestisit + miktar girdisiyle MRL karşılaştırması yap
3. LLM uyumlu ilaçlama programı önerir, motor doğrular

## Resources

- [EU Pesticide Database](https://food.ec.europa.eu/plants/pesticides/eu-pesticides-database_en)
- [Türk Gıda Kodeksi](https://www.tarimorman.gov.tr)
