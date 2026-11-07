# Antigravity & AI Agent Çalışma Rehberi (UI-md)

Bu çalışma alanı, iOS / iPadOS mobil uygulamaları için endüstri standardında UI/UX tasarımı, SwiftUI bileşenleri ve tasarım sistemleri üretmek üzere tasarlanmıştır.

## Dizin Yapısı ve Entegrasyon

* `rules/`:
  - `ios_core_hig.md`: Apple Human Interface Guidelines ve çekirdek etkileşim kuralları (44pt, Haptic, SF Pro, Dynamic Type, Spring).
  - `adaptive_m3_ios.md`: Material Design 3 for iOS adaptasyon kuralları (Safe Area, FAB, Tonal Elevation).
  - `app_store_review_rules.md`: App Store Section 10 UI onay/ret kriterleri.
  - `design_md_spec.md`: YAML Frontmatter + Markdown DESIGN.md spesifikasyonu.
* `references/`:
  - `UI_REFERENCES_INDEX.md`: 11 kategoride 200 adet lider uygulamanın (Spotify, Airbnb, Instagram, Notion, Tinder vb.) tersine mühendislik DESIGN.md kütüphanesinin indeks tablosu.
* `ui-references/`:
  - 200 uygulamanın ham `DESIGN-swiftui.md` ve `DESIGN.md` dosyaları.
* `PORTABLE_IOS_DESIGN_RULES.md`:
  - Herhangi bir başka projeye doğrudan kopyalanıp kullanılabilen hepsi-bir-arada kural paketi.
* `designmd-swift/`:
  - DESIGN.md dosyalarını linter'dan geçiren ve `Theme.swift` çıktısı üreten yerel Swift aracı.

---

## Agent Çalışma İlkeleri

Kullanıcı bir ekran, bileşen veya akış talep ettiğinde:
1. **İlgili Sektör Referansını İncele:** `references/UI_REFERENCES_INDEX.md` üzerinden sektördeki en iyi uygulamaların renk, tipografi ve spacing token'larına bak.
2. **Apple HIG & 44pt Kuralını Uygula:** Dokunma hedeflerini asla 44pt altına düşürme, Haptic geri bildirim ve Spring animasyonu ekle.
3. **App Store Onayını Garantiye Al:** `app_store_review_rules.md` kontrol listesine sadık kal.
4. **SwiftUI Çıktısı Ver:** Temiz, modüler, Dynamic Type ve Dark Mode destekli kod üret.

