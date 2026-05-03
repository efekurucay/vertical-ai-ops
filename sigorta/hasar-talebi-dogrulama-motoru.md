# Hasar Talebi Doğrulama Motoru

> **Sector:** Sigorta / Claims  
> **Difficulty:** High  
> **Monetization:** Claim başına ücret + SaaS

## Problem

LLM hasar dosyasını okuyup olay özetini çıkarabilir. Ancak tazminat kararı, poliçe kapsamı, eksper raporu, tarih uyumu ve fraud sinyalleri gibi doğrulanabilir unsurlara bağlıdır.

## Validation Layer

- Hasar tarihi poliçe yürürlük dönemine giriyor mu?
- Talep edilen zarar poliçe kapsamına dahil mi?
- Eksper raporu ile müşteri beyanı tutarlı mı?
- Fraud ihtimali oluşturan anomali var mı?
- Eksik belge nedeniyle karar askıda mı?

## Tech Stack

- OCR + belge parser
- Kural motoru
- Anomali tespiti
- LLM: dosya özeti ve çağrı merkezi yardımcısı

## Business Model

- Sigorta şirketleri, TPAs, broker’lar
- İşlem hacmine göre fiyatlama

## Turkey Context

Hasar süreçlerinde manuel inceleme maliyeti yüksek. Özellikle araç, sağlık ve konut branşlarında fraud kontrolü ile birlikte çalışan doğrulama sistemleri önemli tasarruf sağlar.

## Getting Started

1. Poliçe kapsam matrisini modele dök
2. Hasar belgelerini parse et
3. Tarih, kapsam ve fraud kuralları yaz
4. İnsan incelemesine gidecek dosyaları işaretle
