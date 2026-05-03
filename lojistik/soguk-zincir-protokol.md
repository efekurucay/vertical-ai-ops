# Soğuk Zincir Protokol Kontrol Motoru

> **Sector:** Lojistik / Gıda-Sağlık  
> **Difficulty:** Medium  
> **Market Size (TR):** Soğukl zincir lojistik sektörü (ilaç, gıda, aşı)  
> **Monetization:** B2B SaaS, IoT entegrasyonu

## Problem

LLM soğuk zincir lojistik planı oluşturabilir. Ancak taşınan ürünün **WHO sıcaklık kontrol kılavuzlarına, ilaç GMP gerekliliklerine veya gıda güvenliği sıcaklık aralıklarına** uygun depolandığını ve taşındığını doğrulayamaz. Zincir kırılması = ürün imhası veya insan sağlığı riski.

## The Validation Layer

- Depo sıcaklık log’ları ürün gereksinimiyle uyumlu mu?
- Taşıma süresince sıcaklık sapması izin verilen aralığı aştı mı?
- Soğuk zincir belgeleri (yalıtım raporu, kalıbrasyon) tamam mı?
- Aşı taşımasında WHO EVM (Effective Vaccine Management) standartları uygulanmış mı?
- Alarm ve müdahale prosedürleri belgelenmiş mi?

## Tech Stack

- **Kural Motoru:** Python + ürün bazlı sıcaklık aralıkları JSON
- **IoT:** MQTT/InfluxDB sıcaklık log entegrasyonu
- **LLM:** Claude 3.5 (sapma analizi + öneri)
- **Backend:** FastAPI + Time-series DB

## Business Model

- **Target:** İlaç lojistik şirketleri, gıda dağıtıcılar, aşı tedarik zinciri
- **Pricing:** Sevkiyat başına veya IoT cihaz başına aylık
- **Argüman:** Zincir kırılması uyarısı ürün imhası maliyetini en aza indirir

## Turkey Context

- COVID-19 aşı tedarik süreci soğuk zincir altyapısı önemini ortaya koydu
- Sağlık Bakanlığı ilaç lojistiğinde GMP uyumu şart koşuyor
- TÜBİTAK 1507 "Sağlık Teknolojileri" + "IoT" kategorisi
