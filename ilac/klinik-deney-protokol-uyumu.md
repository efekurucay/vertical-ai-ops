# Klinik Araştırma Protokol Uyum Motoru

> **Sector:** İlaç / Klinik Araştırma
> **Difficulty:** High
> **Market Size (TR):** 300+ klinik araştırma merkezi
> **Monetization:** B2B SaaS, CRO ortaklıkları

## Problem

LLM klinik araştırma protokolü taslağı oluşturabilir veya mevcut protokolü özetleyebilir. Ancak bu protokolün **TİTCK Klinik Araştırmalar Yönetmeliği, ICH-GCP kılavuzu, Helsinki Bildirgesi ve etik kurul gerekliliklerine** tam uyumunu deterministik olarak kontrol edemez.

## The Validation Layer

- Dahil/dışlama kriterleri açıkça belirtilmiş mi?
- Birincil ve ikincil sonlanım noktaları tanımlanmış mı?
- Örnek büyüklüğü hesabı ve istatistiksel güç analizi mevcut mu?
- Yan etki raporlama prosedürleri (SAE, SUSAR) tanımlanmış mı?
- Gönüllü bilgilendirme ve onam formu ICH-GCP E6'ya uygun mu?
- Veri güvenliği ve gizliliği planı (KVKK) mevcut mu?

## Tech Stack

- **LLM**: GPT-4o (protokol taslağı)
- **Kural Motoru**: Python + ICH-GCP kural seti JSON
- **Veri**: TİTCK klinik araştırma yönetmeliği parse edilmiş
- **Backend**: FastAPI

## Business Model

- **Target**: CRO'lar (Sözleşmeli Araştırma Kuruluşları), ilaç şirketleri, üniversite araştırma merkezleri
- **Pricing**: Protokol başına ücret veya aylık SaaS
- **Argüman**: Etik kurul onay sürecini hızlandırır

## Turkey Context

- TİTCK Klinik Araştırmalar Yönetmeliği (2021) aktif
- Türkiye AB GCP uyum sürecinde
- TÜBİTAK ARDEB klinik araştırma hibesi

## Getting Started

1. ICH-GCP E6(R2)'nin zorunlu bölümlerini checklist olarak JSON'a aktar
2. Protokol metnini bu bölümlere göre kontrol et
3. Eksik bölümler için LLM taslak içerik üretir

## Resources

- [TİTCK Klinik Araştırmalar](https://www.titck.gov.tr)
- [ICH-GCP E6(R2)](https://www.ich.org/page/efficacy-guidelines)
