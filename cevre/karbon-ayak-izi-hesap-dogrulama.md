# Karbon Ayak İzi Hesap Doğrulama Motoru

> **Sector:** Çevre / İklim
> **Difficulty:** Medium
> **Market Size (Global):** ESG raporlaması zorunlu tüm şirketler
> **Monetization:** B2B SaaS, ESG danışmanlık entegrasyonu

## Problem

LLM karbon ayak izi raporu taslağı veya emisyon hesabı oluşturabilir. Ancak bu hesabın **GHG Protocol (Sera Gazı Protokolü) Scope 1-2-3 metodolojisine, ISO 14064 standardına ve AB CSRD direktifine** uygun olup olmadığını doğrulayamaz.

## The Validation Layer

- Scope 1, 2, 3 emisyonlar doğru kategorize edilmiş mi?
- Kullanılan emisyon faktörleri güncel ve onaylı kaynaklardan mı?
- Baz yıl ve sınır tanımı (operational control / equity share) tutarlı mı?
- Önemli emisyon kaynakları dışlanmış mı?
- Üçüncü taraf doğrulama gereksinimi değerlendirilmiş mi?

## Tech Stack

- **LLM**: GPT-4o (rapor yazımı)
- **Kural Motoru**: Python + GHG Protocol kural JSON
- **Emisyon Faktörleri**: IPCC, IEA, DEFRA güncel veri setleri
- **Backend**: FastAPI

## Business Model

- **Target**: ESG raporlaması yapan şirketler, sürdürülebilirlik danışmanları
- **Pricing**: Şirket büyüklüğüne göre aylık SaaS
- **Argüman**: AB CSRD direktifi (2025 itibari ile zorunlu), BRSA ESG beklentileri

## Turkey Context

- Borsa İstanbul sürdürülebilirlik endeksi şirketleri için ESG raporlaması beklentisi
- AB'ye ihracat yapan şirketler CBAM (Sınırda Karbon Düzenleme Mekanizması) kapsamında

## Getting Started

1. GHG Protocol Scope 1-2-3 sınıflandırmasını JSON'a aktar
2. Emisyon faktörü veritabanı oluştur (IEA/DEFRA)
3. LLM rapor taslağındaki iddiaları bu faktörlerle çapraz kontrol et

## Resources

- [GHG Protocol](https://ghgprotocol.org)
- [ISO 14064](https://www.iso.org/standard/66453.html)
- [AB CSRD](https://finance.ec.europa.eu/capital-markets-union-and-financial-markets/company-reporting-and-auditing/company-reporting/corporate-sustainability-reporting_en)
