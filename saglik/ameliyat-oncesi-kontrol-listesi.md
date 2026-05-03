# Ameliyat Öncesi Kontrol Listesi Motoru

> **Sector:** Sağlık / Cerrahi
> **Difficulty:** Medium
> **Market Size (TR):** 1.500+ hastane, yılda 5M+ ameliyat
> **Monetization:** B2B SaaS (HBS entegrasyonu)

## Problem

LLM ameliyat öncesi hazırlık talimatları oluşturabilir. Ancak **WHO Güvenli Cerrahi Kontrol Listesi, Sağlık Bakanlığı protokolleri ve hastane akreditasyon standartlarının** tüm maddelerinin eksiksiz tamamlandığını doğrulayan bir mekanizma yoktur. Atlanan tek bir adım (örneğin kan grubu doğrulaması) hayati sonuçlara yol açabilir.

## The Validation Layer

- Aydınlatılmış onam belgesi imzalanmış mı?
- Alerji durumu son 24 saatte sorgulanmış mı?
- Kan grubu ve cross-match tamamlandı mı?
- Oruç süresi yeterli mi? (katı gıda 6 saat, sıvı 2 saat)
- Implant/protez/pacemaker bilgisi ameliyat ekibine iletildi mi?
- Antibiyotik profilaksisi planlandı mı ve zamanlaması doğru mu?
- Cerrahi alan işaretlemesi yapıldı mı?

## Tech Stack

- **LLM**: GPT-4o (hasta özeti ve talimat üretimi)
- **Kural Motoru**: WHO checklist + Sağlık Bakanlığı protokolü JSON
- **Entegrasyon**: HL7 FHIR, HBS API
- **Frontend**: Tablet uyumlu Next.js UI

## Business Model

- **Target**: Hastaneler, cerrahi klinikler, JCI/ISO 15189 akreditasyonu hedefleyenler
- **Pricing**: Ameliyathane başına aylık SaaS
- **Argüman**: JCI akreditasyon şartı, malpraktis risk azaltımı

## Turkey Context

- Sağlık Bakanlığı SKS (Sağlıkta Kalite Standartları) ameliyat güvenliği bölümü
- JCI akreditasyonu hedefleyen hastane sayısı artıyor

## Getting Started

1. WHO Güvenli Cerrahi Kontrol Listesi'ni JSON formatına dönüştür
2. Her madde için tamamlanma durumu takibi yap
3. Eksik maddeler için LLM açıklama ve hatırlatma üretir

## Resources

- [WHO Surgical Safety Checklist](https://www.who.int/teams/integrated-health-services/patient-safety/research/safe-surgery)
- [SKS Hastane](https://kalite.saglik.gov.tr)
