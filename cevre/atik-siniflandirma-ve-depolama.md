# Atık Sınıflandırma ve Depolama Kontrol Motoru

> **Sector:** Çevre / Atık Yönetimi
> **Difficulty:** Medium
> **Market Size (TR):** Atık üreten tüm sanayi tesisleri
> **Monetization:** B2B SaaS

## Problem

LLM atık yönetim planı oluşturabilir. Ancak atığın **Atık Yönetimi Yönetmeliği'ndeki tehlikeli/tehlikesiz sınıflandırmasına, depolama eşik değerlerine ve lisanslı bertaraf yöntemlerine** uygun olup olmadığı doğrulanamaz.

## The Validation Layer

- Atık, EWC (Avrupa Atık Kataloğu) kodu doğru sınıflandırılmış mı?
- Tehlikeli atık mı? Özel lisanslı taşıyıcı gerekli mi?
- Geçici depolama süresi (tehlikeli: 90 gün) aşılmış mı?
- Atık beyan sistemi (TABS) bildirimi yapılmış mı?
- Geri kazanım tesisi lisans kapsamı bu atıkla uyuşuyor mu?

## Tech Stack

- **LLM**: Claude (atık tanımlama ve plan yazımı)
- **Kural Motoru**: Python + EWC kodu eşleştirme
- **Entegrasyon**: TABS (Atık Beyan Sistemi) API
- **Backend**: FastAPI

## Business Model

- **Target**: Organize sanayi bölgeleri, fabrikalar, hastaneler
- **Pricing**: Tesis başına aylık SaaS
- **Argüman**: Çevre cezaları, lisans iptali riski

## Turkey Context

- TABS (Atık Beyan Sistemi) zorunlu beyan platformu
- Tehlikeli atık bertarafı için Çevre Lisansı zorunlu

## Getting Started

1. EWC kodu listesini ve tehlikelilik sınıflarını JSON'a aktar
2. Atık kodu gir → tehlikelilik ve depolama kurallarını döndür
3. LLM atık kaynağından kodu tahmin eder, motor doğrular

## Resources

- [Atık Yönetimi Yönetmeliği](https://www.mevzuat.gov.tr)
- [TABS](https://tabs.csb.gov.tr)
