<div align="center">

# UI-md 📱✨

> **iOS & iPadOS için Apple HIG Tasarım Sistemi ve Yapay Zeka (AI) Kodlama Mimarisi**

<br />

<!-- DİL SEÇİMİ / LANGUAGE SWITCHER BAR -->
[![English](https://img.shields.io/badge/Language-English-238636?style=for-the-badge&logo=github&logoColor=white)](README.md)
[![Türkçe](https://img.shields.io/badge/Dil-Türkçe%20(Aktif)-E30A17?style=for-the-badge&logo=apple&logoColor=white)](README.tr.md)

<br />
<br />

[![Swift](https://img.shields.io/badge/Swift-5.9%2B-orange.svg?style=flat&logo=swift)](https://swift.org)
[![iOS](https://img.shields.io/badge/iOS-17.0%2B-blue.svg?style=flat&logo=apple)](https://developer.apple.com/ios/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Uygulama Kataloğu](https://img.shields.io/badge/Tersine%20Mühendislik%20Uygulamalar-200-brightgreen.svg)](references/UI_REFERENCES_INDEX.md)
[![Apple HIG](https://img.shields.io/badge/Apple%20HIG-%25100%20Uyumlu-purple.svg)](rules/ios_core_hig.md)
[![App Store Review](https://img.shields.io/badge/App%20Store%20Onayı-Section%2010%20Hazır-success.svg)](rules/app_store_review_rules.md)

</div>

---

**UI-md**, mobil yazılım geliştiricileri, ürün tasarımcıları ve yapay zeka kodlama ajanları (Cursor, Windsurf, Claude Code, Antigravity, Copilot) için hazırlanmış açık kaynaklı, üretime hazır bir tasarım çerçevesi ve kural setidir.

Dünyaca ünlü **200 lider iOS uygulamasının** (Airbnb, Spotify, Duolingo, Tinder, Notion, Cash App, Apple Wallet vb.) tersine mühendislikle çıkarılmış tasarım token'larını; tavizsiz **Apple Human Interface Guidelines (HIG)** kuralları, App Store ret kontrol listeleri ve yerel Swift CLI araçlarıyla bir araya getirir.

---

## 🧭 İçindekiler

- [Neden UI-md?](#-neden-ui-md)
- [Depo Mimarisi](#-depo-mimarisi)
- [4 Temel Sütun](#-4-temel-sütun)
  - [1. 200 Uygulamanın Tersine Mühendislik Kataloğu](#1-200-uygulamanın-tersine-mühendislik-kataloğu)
  - [2. Apple HIG & App Store Onay Bariyerleri](#2-apple-hig--app-store-onay-bariyerleri)
  - [3. Taşınabilir AI Agent Entegrasyonu (Cursor, Claude, Windsurf)](#3-taşınabilir-ai-agent-entegrasyonu)
  - [4. Yerel Swift CLI Aracı (`designmd-swift`)](#4-yerel-swift-cli-aracı)
- [Hızlı Başlangıç Rehberi](#-hızlı-başlangıç-rehberi)
- [Referans Uygulama: ChronoQuest](#-referans-uygulama)
- [DESIGN.md Format Spesifikasyonu](#-designmd-spesifikasyonu)
- [Katkıda Bulunma](#-katkıda-bulunma)
- [Lisans](#-lisans)

---

## 💡 Neden UI-md?

Mevcut yapay zeka modelleri ve promptları genellikle mobil ortam için web hissiyatı uyandıran, 44pt'den küçük dokunma alanlarına sahip, doğrusal (linear) animasyonlar kullanan ve Dynamic Type veya Karanlık Mod desteği eksik olan arayüzler üretir.

**UI-md bu sorunu kökten çözer:**
* **Sıfır Tahminli Token'lar:** Makine tarafından okunabilir YAML front matter ve insan tarafından okunabilir Markdown açıklamaları.
* **Varsayılan Olarak Apple HIG:** 44×44 pt minimum dokunma alanları, Taptic Engine dokunsal geri bildirimi, Spring yay fiziği (`.spring(response: 0.35, dampingFraction: 0.75)`) ve Safe Area / Dynamic Island koruması.
* **App Store Section 10 Garantisi:** Sahte butonlar, kırık webview sarmalayıcılar ve yanlış ikon kullanımlarına karşı yerleşik kontrol bariyerleri.

---

## 🏛️ Depo Mimarisi

```
UI-md/
├── README.md                      # İngilizce ana vitrin belgesi
├── README.tr.md                   # Türkçe ana vitrin belgesi
├── PORTABLE_IOS_DESIGN_RULES.md   # Herhangi bir iOS projesine taşınabilen hepsi-bir-arada kural seti
├── AGENTS.md                      # AI Ajan çalışma ilkeleri ve entegrasyon rehberi
├── LICENSE                        # MIT Açık Kaynak Lisansı
├── CONTRIBUTING.md                # Topluluk katkı kuralları
├── rules/                         # Çekirdek Apple ve tasarım sistemi kuralları
│   ├── ios_core_hig.md           # Apple HIG çekirdek etkileşim kuralları (44pt, Haptic, Spring)
│   ├── app_store_review_rules.md  # Section 10 App Store onay/ret kriterleri
│   ├── adaptive_m3_ios.md         # Material Design 3 for iOS adaptasyon kuralları
│   └── design_md_spec.md          # YAML Frontmatter + Markdown DESIGN.md spesifikasyonu
├── references/
│   └── UI_REFERENCES_INDEX.md     # 200 lider uygulamanın indeks kataloğu
├── ui-references/                 # 200 uygulamanın tersine mühendislik tasarım sistemleri
│   ├── dating/                   # 12 uygulama (Tinder, Bumble, Hinge, vb.)
│   ├── finance/                  # 22 uygulama (Apple Wallet, Cash App, Robinhood, vb.)
│   ├── fitness/                  # 19 uygulama (Calm, AllTrails, Apple Fitness, vb.)
│   ├── food/                     # 16 uygulama (DoorDash, Deliveroo, Starbucks, vb.)
│   ├── messaging/                # 16 uygulama (Discord, iMessage, Telegram, vb.)
│   ├── misc/                     # 20 uygulama (Duolingo, ChatGPT, Character AI, vb.)
│   ├── music/                    # 14 uygulama (Apple Music, Spotify, Audible, vb.)
│   ├── productivity/             # 22 uygulama (Notion, Asana, Bear, Google Calendar, vb.)
│   ├── social/                   # 23 uygulama (Instagram, BeReal, Bluesky, vb.)
│   ├── travel/                   # 20 uygulama (Airbnb, Apple Maps, Uber, vb.)
│   └── video/                    # 16 uygulama (Netflix, Disney+, YouTube, Twitch, vb.)
├── agents/
│   └── ios-ui-architect.md        # Özelleştirilmiş iOS UI/UX Lead Architect ajan promptu
└── designmd-swift/                # Yerel Swift CLI aracı (Linter & Theme.swift üreticisi)
```

---

## ⚡ 4 Temel Sütun

### 1. 200 Uygulamanın Tersine Mühendislik Kataloğu

11 farklı sektörde önde gelen mobil uygulamaların renk paletlerini, tipografi ölçeklerini, köşe yarıçaplarını ve SwiftUI bileşen yapılarını keşfedin:

| Kategori | Uygulama Sayısı | Öne Çıkan Örnekler | Dizin Yolu |
| :--- | :---: | :--- | :--- |
| **Dating** | 12 | Bumble, Tinder, Hinge, Raya, Feeld | [`ui-references/dating/`](ui-references/dating/) |
| **Finance** | 22 | Apple Wallet, Cash App, Binance, Robinhood, Revolut | [`ui-references/finance/`](ui-references/finance/) |
| **Fitness** | 19 | Apple Fitness, Calm, Fitbit, Strava, Nike | [`ui-references/fitness/`](ui-references/fitness/) |
| **Food & Drink** | 16 | DoorDash, Deliveroo, Starbucks, Domino's | [`ui-references/food/`](ui-references/food/) |
| **Messaging** | 16 | Discord, iMessage, Telegram, KakaoTalk, GroupMe | [`ui-references/messaging/`](ui-references/messaging/) |
| **Misc & AI** | 20 | Duolingo, ChatGPT, Character AI, Amazon | [`ui-references/misc/`](ui-references/misc/) |
| **Music** | 14 | Apple Music, Spotify, Audible, Bandcamp | [`ui-references/music/`](ui-references/music/) |
| **Productivity** | 22 | Notion, Asana, Bear, Apple Notes, Google Calendar | [`ui-references/productivity/`](ui-references/productivity/) |
| **Social** | 23 | Instagram, BeReal, Bluesky, TikTok, Twitter/X | [`ui-references/social/`](ui-references/social/) |
| **Travel** | 20 | Airbnb, Apple Maps, Uber, Booking.com, Waze | [`ui-references/travel/`](ui-references/travel/) |
| **Video & Streaming** | 16 | Netflix, Apple TV, Disney+, YouTube, Twitch | [`ui-references/video/`](ui-references/video/) |

👉 **[200 Uygulamanın Tam İnteraktif Tablosunu Görüntüle](references/UI_REFERENCES_INDEX.md)**

---

### 2. Apple HIG & App Store Onay Bariyerleri

[`rules/`](rules/) klasöründeki kurallar tavizsiz uygulanır:
1. **44 × 44 pt Dokunma Hedefi:** Tüm etkileşimli nesneler en az 44pt dokunma alanına (`.contentShape(Rectangle())`) sahiptir.
2. **Spring Fizik Animasyonları:** Doğrusal (linear) animasyonlar yasaktır. Her zaman `.spring(response: 0.35, dampingFraction: 0.75)` yay fiziği kullanılır.
3. **Taptic Engine Haptic Bildirimi:** Kademeli geçişlerde, seçimlerde ve başarı/hata anlarında dokunsal geri bildirim verilir.
4. **Dynamic Type & Semantik Renkler:** Sistem yazı tipi boyutuna göre otomatik ölçeklenen metinler ve Karanlık Mod uyumlu semantik renkler.
5. **Thumb Zone Ergonomisi:** Birincil butonlar alt 1/3'lük başparmak erişim bölgesinde minimum 54pt yükseklikle konumlandırılır.

---

### 3. Taşınabilir AI Agent Entegrasyonu

UI-md sistemini kendi iOS projenize **10 saniyede** entegre edebilirsiniz:

#### Cursor İçin (`.cursorrules`):
Projenizin kök dizinine [`PORTABLE_IOS_DESIGN_RULES.md`](PORTABLE_IOS_DESIGN_RULES.md) dosyasını kopyalayın ve `.cursorrules` dosyanıza şu satırları ekleyin:
```markdown
Tüm UI/UX tasarımı için PORTABLE_IOS_DESIGN_RULES.md kurallarını referans al:
- Tüm buton ve tutamaçlarda en az 44x44pt dokunma alanı sağla.
- Asla linear animasyon kullanma; Apple yay fiziği (.spring(response: 0.35, dampingFraction: 0.75)) uygula.
- Semantik sistem renkleri ve WCAG 4.5:1 kontrast standardı kullan.
- Dynamic Type desteği ve App Store Section 10 onay kriterlerine sadık kal.
```

#### Claude Code, Windsurf veya Antigravity İçin:
[`PORTABLE_IOS_DESIGN_RULES.md`](PORTABLE_IOS_DESIGN_RULES.md) ve [`AGENTS.md`](AGENTS.md) dosyalarını projenizin kök dizinine kopyalamanız yeterlidir.

---

### 4. Yerel Swift CLI Aracı (`designmd-swift`)

`DESIGN.md` dosyalarını denetlemek ve doğrudan SwiftUI `Theme.swift` kodu üretmek için:

```bash
cd designmd-swift
swift build -c release

# DESIGN.md dosyasını denetle (lint)
.build/release/designmd lint /yol/DESIGN.md

# SwiftUI Theme.swift çıktısı üret
.build/release/designmd generate /yol/DESIGN.md --output Sources/Theme.swift
```

---

## 🎮 Referans Uygulama

UI-md standartlarıyla sıfırdan geliştirilen **ChronoQuest** projesini inceleyin. Zaman ve takvim aritmetiğini öğreten bu oyun; polar koordinatlı saat kadranı, dinamik gün/gece teması, 44pt tutamaçlar ve haptic geri bildirimlerle geliştirilmiş canlı bir örnektir.

---

## 📄 DESIGN.md Format Spesifikasyonu

UI-md içindeki her `DESIGN.md` iki katmanlı bir mimariye sahiptir:
* **Makine Katmanı (YAML Front Matter):** Kesin token değerleri (`colors`, `typography`, `spacing`, `motion`).
* **İnsan Katmanı (Markdown):** Tasarım mantığı, UX kalıpları ve etkileşim detayları.

```yaml
---
name: UygulamaAdi
platform:
  os: [iOS, iPadOS]
  minimumDeployment: "17.0"
colors:
  primary:
    light: "#1C1C1E"
    dark: "#F2F2F7"
  accent: "#007AFF"
touchTargets:
  minimum: 44pt
  buttonHeight: 54pt
motion:
  springDefault:
    response: 0.35
    dampingFraction: 0.75
---
```

---

## 🤝 Katkıda Bulunma

Topluluk katkılarını memnuniyetle karşılıyoruz! Yeni bir uygulamanın tasarım sistemini eklemek veya kural setlerini genişletmek için lütfen [Katkı Rehberi](CONTRIBUTING.md)'ni inceleyin.

---

## 📜 Lisans

Bu proje **MIT Lisansı** ile lisanslanmıştır. Detaylar için [LICENSE](LICENSE) dosyasına göz atabilirsiniz.

---

<p align="center">
  Apple & AI Geliştirici Topluluğu için <b>Ali Beysülen</b> tarafından ❤️ ile geliştirilmiştir.
</p>
