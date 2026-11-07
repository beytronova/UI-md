# Apple Core Human Interface Guidelines (HIG) & iOS UI Kural Seti

Bu belge, Apple ekosisteminde (iOS / iPadOS) birinci sınıf, yerel ve kullanıcı dostu bir kullanıcı arayüzü (UI) ve kullanıcı deneyimi (UX) geliştirmek için zorunlu kural setidir.

---

## 1. Temel Tasarım Felsefesi (Core Design Principles)

Apple arayüzlerinin temeli üç ana sütun üzerine oturur:

### 1.1 Clarity (Netlik)
* **Okunabilirlik Önceliği:** Metinler her ekran boyutunda ve dinamik yazı tipi ayarında rahatça okunmalıdır.
* **Anlaşılır İkonografi:** İkonlar evrensel ve bağlama uygun olmalı (tercihen SF Symbols kullanılmalıdır).
* **Görsel Sadeleştirme:** Arayüzdeki süslemeler ve dekoratif öğeler asla içeriğin ve ana eylemin önüne geçmemelidir. Kullanıcı ekrana baktığı ilk anda ne yapacağını kavramalıdır.

### 1.2 Deference (Saygı ve İçerik Odaklılık)
* **İçerik Başrolde:** Arayüz arka planda kalmalı, kullanıcının odaklandığı veri, medya veya etkileşim nesnesi öne çıkarılmalıdır.
* **Modern Katmanlar:** Şeffaflık efektleri (`Material` / `.ultraThinMaterial`, `blur` ve `translucency`) içeriğe derinlik kazandırmak ve bağlamı kaybetmemek için kullanılmalıdır.

### 1.3 Depth (Derinlik ve Hissiyat)
* **Katman Hiyerarşisi:** Z ekseninde mantıklı katmanlar kullanılmalıdır (Arka Plan -> Kart/Yüzey -> İçerik -> Eylemler/Modaller).
* **Fiziksel Algı:** Arayüz elemanları gerçek dünyadaki kütle ve elastikiyet kurallarını hissettirmeli, akıcı spring animasyonları ve yumuşak gölgelerle desteklenmelidir.

---

## 2. Etkileşim ve Dokunma Hedefleri (Interactivity & Touch Targets)

* **44 × 44 pt Kuralı (Kesin Kural):**
  - Kullanıcının parmakla dokunduğu tüm interaktif alanlar (butonlar, ikonlar, sürüklenebilir kontrol noktaları, hücreler) minimum **44 x 44 pt** dokunma alanına (hit target) sahip olmalıdır.
  - Görsel öğe 20x20 pt olsa dahi, `.contentShape(Rectangle())` veya `frame(minWidth: 44, minHeight: 44)` kullanılarak dokunma hedefi genişletilmelidir.
* **Doğrudan Manipülasyon (Direct Manipulation):**
  - Kullanıcı arayüzdeki nesneleri (örneğin saat kadranı kolları, kartlar, listeler) dolaylı kaydırıcılar yerine doğrudan parmağıyla tutup sürükleyebilmelidir (`DragGesture`).
* **Haptic Feedback (Dokunsal Geri Bildirim):**
  - Dokunma, başarı, hata veya kritik sınır aşımı durumlarında sistem motoru tetiklenmelidir (`UIImpactFeedbackGenerator`, `UINotificationFeedbackGenerator` veya SwiftUI `.sensoryFeedback()`).
  - Haptikler gereksiz yere sık kullanılmamalı, sadece eylemin sonucunu doğrulamak için hissettirilmelidir.
* **Anında Görsel Tepki (Touch States):**
  - Bir butona dokunulduğunda kullanıcı parmağını kaldırmadan önce opaklık azalması (`opacity: 0.7`) veya hafif ölçeklenme (`scaleEffect: 0.96`) gibi anlık tepki almalıdır.

---

## 3. Navigasyon ve Bilgi Mimarisi (Navigation & Layout)

* **Hiyerarşik Netlik:** Kullanıcı her zaman nerede olduğunu ve önceki ekrana nasıl döneceğini bilmelidir (Native Navigation Bar ve Back butonu).
* **Safe Area Uyumluluğu:**
  - Dynamic Island, Notch ve alttaki Home Indicator alanları asla ana içerik veya butonlarla çakışmamalıdır.
  - Arka planlar Safe Area'yı kaplamalı (`.ignoresSafeArea()`), ancak butonlar ve interaktif metinler Safe Area içinde kalmalıdır.
* **Minimum Dokunuş Prensibi:** Kullanıcı ana hedefine veya oyun mekaniğine en az menü geçişiyle ulaşmalıdır.
* **Modaller ve Tam Ekran:**
  - Geçici işlemler için Sheet veya Popover kullanılmalıdır.
  - Yoğun odaklanma gerektiren deneyimlerde navigation bar minimal tutulmalı veya gizlenmelidir.

---

## 4. Renk, Tema ve Erişilebilirlik (Color & Dark Mode)

* **Semantik Sistem Renkleri:**
  - Sabit hardcoded HEX kodları yerine dinamik semantik renkler tercih edilmelidir (`Color(uiColor: .systemBackground)`, `Color(uiColor: .secondarySystemBackground)`, `Color.primary`, `Color.accentColor`).
* **Otomatik Karanlık Mod (Dark Mode):**
  - Tüm renkler ve yüzeyler sistemin Aydınlık/Karanlık mod değişimine anında adapte olmalıdır.
* **WCAG Kontrast Standartları:**
  - Metin ve arka plan arasında minimum 4.5:1 (büyük metinlerde 3:1) kontrast oranı sağlanmalıdır.

---

## 5. Tipografi ve Dynamic Type (Typography)

* **Apple Sistem Fontu:** Birinci tercih San Francisco (`SF Pro`) ve kod/sayı odaklı alanlarda `SF Mono` / `SF Rounded` olmalıdır.
* **Dynamic Type (Dinamik Yazı Tipi Uyumu):**
  - Hardcoded font boyutları (`font(.system(size: 24))`) yerine Apple'ın metin stilleri kullanılmalıdır:
    - `.largeTitle`, `.title`, `.title2`, `.title3`, `.headline`, `.body`, `.callout`, `.subheadline`, `.footnote`, `.caption`.
  - Kullanıcı sistem genelinde yazı boyutunu büyüttüğünde arayüz bozulmamalı, metinler `minimumScaleFactor` veya otomatik çok satırlı düzen ile korunmalıdır.

---

## 6. Hareket ve Animasyon Fiziği (Motion & Physics)

* **Spring (Yay) Eğrileri:**
  - Doğrusal (linear) animasyonlardan kaçınılmalıdır. Apple arayüzlerinde hareket her zaman yay fiziği taşır (`.spring(response: 0.35, dampingFraction: 0.75)`).
* **Geri Çekilme ve Eylemsizlik:**
  - Kapatılan modallar, kaydırılan kartlar ve bırakılan nesneler el hareketinin hızına (velocity) duyarlı şekilde yerine oturmalıdır.

