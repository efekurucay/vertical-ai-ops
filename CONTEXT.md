# vertical-ai-ops — Proje Bağlamı

> Bu dosya, reponun tüm bağlamını, fikir kaynağını, dosya yapısını, şablonu ve kalan işleri içerir.
> Yeni bir agent veya geliştirici projeye başlarken **yalnızca bu dosyayı** okuyarak tüm context'i alabilir.

---

## Proje Fikri

LLM'ler metin üretmekte çok iyidir. Ama **yüksek hata maliyeti olan, yazılı kurallara bağlı, denetlenebilir kararlar** gerektiren sektörlerde tek başına LLM yeterli değildir.

Bu repo, tam da bu boşluğu dolduran **100 dikey AI fırsatını** belgeler:
- Kural motoru + LLM hibrit mimarisi
- Sektörel mevzuat, standart veya protokol uyum doğrulaması
- B2B SaaS veya API olarak konumlandırılabilir ürünler
- Türkiye pazarına özel bağlam

### Kazanma Kriterleri
Bir fırsatın bu repoya girmesi için üç kriter:
1. **Yüksek hata maliyeti** — yanlış karar = para cezası, hukuki risk, sağlık tehlikesi
2. **Yazılı kurallar mevcut** — kanun, yönetmelik, standart, protokol
3. **Düşük dijitalleşme** — sektör hâlâ kağıt/Excel kullanıyor

---

## Dosya Yapısı

```
vertical-ai-ops/
├── CONTEXT.md          ← Bu dosya: tüm bağlam ve backlog
├── README.md           ← Kısa manifesto (todo)
├── CONTRIBUTING.md     ← Katkı rehberi (todo)
├── template.md         ← Yeni sektör şablonu (todo)
├── backlog.csv         ← 100 fırsatın tam listesi
│
├── lojistik/
├── havayolu/
├── denizcilik/
├── finans/
├── sigorta/
├── saglik/
├── ilac/
├── medikal-cihaz/
├── kozmetik/
├── cevre/
├── enerji/
├── tarim/
├── insaat/
├── madencilik/
├── it/
├── siber-guvenlik/
├── hr/
├── medya/
├── eticaret/
├── perakende/
├── bankacilik/
├── hukuk/
├── kamu/
├── akademi/
├── gayrimenkul/
├── turizm/
├── otomotiv/
├── tekstil/
├── sosyal-hizmetler/
├── spor/
├── savunma/
└── ulasim/
```

---

## Her Dosyanın Şablonu

Her `.md` dosyası aşağıdaki bölümleri içermelidir:

```markdown
# [Fırsat Başlığı]

> **Sector:** [Dikey]  
> **Difficulty:** Low / Medium / High / Very High  
> **Market Size (TR):** [Tahmini büyüklük]  
> **Monetization:** [Gelir modeli]

## Problem
[LLM tek başına neden yetersiz kalıyor?]

## Validation Layer
[Hangi sorular kural motoruyla doğrulanmalı?]
- Soru 1
- Soru 2

## Tech Stack
- Kural motoru (Python / DSL / JSON rules)
- LLM kullanımı (sadece açıklama/özet katmanı)
- Veri kaynakları
- Backend (FastAPI tercih)

## Business Model
- Target kitle
- Pricing modeli
- Argüman (neden ödeme yaparlar?)

## Turkey Context
[Türkiye'ye özel yasal çerçeve, pazar durumu, fırsatlar]

## Getting Started
[İlk prototipi nasıl kurarsın? Adım adım]

## Resources
[Faydalı linkler]
```

**Örnek tamamlanmış dosya:** `lojistik/gumruk-tarife-siniflandirma.md`

---

## İlerleme Durumu

| Durum | Sayı |
|-------|------|
| ✅ done | 10 |
| ⏳ todo | 90 |
| **Toplam** | **100** |

Güncel listeye `backlog.csv` dosyasından bakabilirsin.

### Tamamlanan Dosyalar (10)

| # | Dosya |
|---|-------|
| 1 | `lojistik/gumruk-tarife-siniflandirma.md` |
| 2 | `lojistik/tehlikeli-madde-tasima-adr.md` |
| 3 | `lojistik/soguk-zincir-protokol.md` |
| 4 | `havayolu/ucus-plani-hava-sahasi.md` |
| 5 | `denizcilik/imo-emisyon-uyumu.md` |
| 6 | `finans/kyc-aml-kural-motoru.md` |
| 7 | `finans/portfoy-risk-limiti-kontrolu.md` |
| 8 | `finans/kredi-skoru-dogrulama-katmani.md` |
| 9 | `sigorta/police-uygunluk-kontrolu.md` |
| 10 | `sigorta/hasar-talebi-dogrulama-motoru.md` |

---

## Agent Talimatları

Bu repoyu devam ettirmek için bir agent'a şu talimatı verebilirsin:

```
Repo: https://github.com/efekurucay/vertical-ai-ops

Görev:
1. backlog.csv dosyasını oku
2. durum = 'todo' olan satırları bul
3. Her satır için ilgili klasörde bir .md dosyası oluştur
4. Her dosya CONTEXT.md'deki şablonu takip etmeli
5. Tamamlanan her dosya için backlog.csv'deki durumu 'done' olarak güncelle

Şablon: CONTEXT.md > 'Her Dosyanın Şablonu' bölümüne bak
Örnek tamamlanmış dosya: lojistik/gumruk-tarife-siniflandirma.md
Dil: Türkçe
```

---

## Teknoloji Tercihleri

- **Backend:** Python / FastAPI
- **Rule Engine:** JSON tabanlı kural seti veya DSL
- **LLM:** GPT-4o veya Claude 3.5 (açıklama/özet katmanı için)
- **Veri:** Resmi mevzuat, standart ve yönetmelik belgeleri
- **Deployment:** Docker + Coolify veya Hetzner VPS

---

*Son güncelleme: 2026-05-04*
