# Portable iOS UI/UX Design System & Rule Set

> **Taşınabilirlik Notu:** Bu dosyayı herhangi bir iOS (SwiftUI / UIKit) projenizin kök dizinine kopyalayarak (`AGENTS.md`, `CLAUDE.md`, `.cursorrules` veya `.agents/rules/` olarak) doğrudan yapay zeka ajanlarınıza ve geliştirici ekibinize standart bir kural seti olarak sunabilirsiniz.

---

## 1. Apple Core Human Interface Guidelines (HIG)

### 1.1 Üç Temel Felsefe
1. **Clarity (Netlik):** Metinler her boyutta okunmalı, ikonlar tek bakışta anlaşılmalı (SF Symbols), arayüz süslemeleri asla içeriğin ve kullanıcının ana eyleminin önüne geçmemelidir.
2. **Deference (İçerik Odaklılık):** Arayüz arka planda kalmalı, kullanıcının odaklandığı veri veya etkileşim nesnesi öne çıkmalıdır. Arka plan bulanıklıkları (`.ultraThinMaterial`) ve katmanlar içeriği vurgulamak için kullanılmalıdır.
3. **Depth (Derinlik ve Hissiyat):** Ekrandaki katmanlar ve hareketler fiziksel kütle hissi taşımalı; sert/mekanik geçişler yerine yay (`.spring`) animasyonları ve yumuşak gölgelerle derinlik sağlanmalıdır.

### 1.2 Dokunma Hedefleri ve Etkileşim (Touch Targets & Haptics)
* **44 × 44 pt Kuralı (Zorunlu):**
  - Parmakla dokunulan tüm butonlar, ikonlar ve hücreler minimum **44 x 44 pt** dokunma alanına sahip olmalıdır.
  - SwiftUI: `.frame(minWidth: 44, minHeight: 44).contentShape(Rectangle())`
* **Doğrudan Manipülasyon (Direct Manipulation):**
  - Nesneler (ör. saat kolları, kartlar, listeler) dolaylı kaydırıcılar yerine parmakla tutulup sürüklenebilmelidir (`DragGesture`).
* **Haptic Feedback (Taptic Engine):**
  - Buton tıklamaları, başarı, hata ve sınır aşımı durumlarında uygun haptic verilmelidir (`UIImpactFeedbackGenerator(style: .medium)` veya SwiftUI `.sensoryFeedback()`).
* **Anlık Dokunma Tepkisi (Touch States):**
  - Tıklanan öğe parmak kaldırılmadan önce hafifçe küçülmeli (`scaleEffect: 0.96`) veya opaklığı azalmalıdır (`opacity: 0.7`).

### 1.3 Tipografi & Dynamic Type
* **Sistem Fontu:** Birincil tercih **SF Pro**; kod veya tabular veriler için **SF Mono** veya **SF Rounded**.
* **Dynamic Type:** Sabit font boyutu yerine Apple metin stilleri kullanılmalıdır (`.font(.headline)`, `.font(.body)`, `.font(.caption)`).
* Kullanıcı sistem ayarlarında yazı boyutunu büyüttüğünde metinler taşmamalı, arayüz esnek (`minimumScaleFactor` / çok satır) olmalıdır.

### 1.4 Renk & Karanlık Mod (Dark Mode)
* Hardcoded HEX değerleri yerine semantik sistem renkleri kullanılmalıdır (`Color(uiColor: .systemBackground)`, `Color(uiColor: .secondarySystemBackground)`, `Color.primary`).
* WCAG Standartları: Metin ve zemin arasında en az 4.5:1 kontrast sağlanmalıdır.

### 1.5 Hareket & Fizik (Motion)
* Doğrusal (linear) animasyonlar yasaktır. Her zaman Spring (yay) fiziği kullanılmalıdır:
  ```swift
  .animation(.spring(response: 0.35, dampingFraction: 0.75), value: isExpanded)
  ```

---

## 2. Adaptif Material 3 (M3) for iOS Kuralları

Google Material Design 3 tasarım dili iOS'e entegre edilirken şu adaptasyonlar zorunludur:

1. **Platform Alışkanlıkları Korunmalıdır:**
   - Edge-swipe ile geri dönme jesti engellenmemelidir.
   - iOS'in native alert/modal sunum biçimleri kullanılmalıdır.
2. **Safe Area & Dynamic Island / Notch Koruması:**
   - Top App Bar yüksekliği iOS `UINavigationBar` standartları ile uyumlu olmalıdır. İçerik çentik veya Dynamic Island altına taşmamalıdır.
3. **Floating Action Button (FAB) & Home Indicator:**
   - FAB asla alt kısımdaki Home Indicator çizgisinin üzerine binmemelidir.
   - Home Indicator Safe Area mesafesine ek olarak en az +16pt alt padding verilmelidir.
4. **Tonal Elevation vs Ağır Gölgeler:**
   - M3'ün Surface Tint ve katmanlı tonlama mantığı (`surfaceContainerLowest` - `surfaceContainerHighest`) tercih edilmeli; yapay siyah gölgeler yerine yüzey tonu ve ince sınır hatları (`stroke`) kullanılmalıdır.
5. **Dokunma Tepkisi:**
   - Android dairesel dalga (ripple) efekti yerine iOS'in native buton opaklık/yaylanma tepkisi ve Haptic Feedback kullanılmalıdır.

---

## 3. App Store Review Guidelines (UI Reddedilme Önlemleri)

App Store inceleme sürecinde Section 10 UI kuralları uyarınca reddedilmemek için:

1. **10.1 HIG Uyumu:** Arayüz tutarsız, karmaşık veya alışılmadık olmamalıdır.
2. **10.2 Sistem Uygulamalarını Taklit Etmeme:** App Store, Ayarlar veya Kamera gibi dahili iOS uygulamalarını taklit eden, kullanıcıyı yanıltan tasarımlar yapılmamalıdır.
3. **10.3 Sistem İkonlarının İstismarı:** Apple sistem ikonları (SF Symbols) kendi semantik anlamları dışında keyfi eylemler için kullanılmamalıdır.
4. **10.4 Masaüstü Simülasyonu:** iOS ana ekranını veya widget ortamını taklit eden yapay ortamlar oluşturulmamalıdır.
5. **10.5 Donanım Düğmeleri:** Ses ve sessize alma donanım tuşlarının işlevleri değiştirilmemelidir.
6. **10.6 Kalite Çıtası:** Bitmemiş, yapım aşamasında ekranlar veya işlevsiz boş butonlar bulunmamalıdır.

---

## 4. DESIGN.md Standart Spesifikasyonu (Token Yapısı)

Her ekran veya uygulama için tasarım sistemi aşağıdaki formatta tanımlanır:

```yaml
---
name: AppDesignSystem
platform: [iOS, iPadOS]
colors:
  primary: { light: "#1A1C1E", dark: "#F2F2F7" }
  accent: "#007AFF"
  surface: { light: "#F2F2F7", dark: "#1C1C1E" }
typography:
  largeTitle: { fontFamily: SF Pro, textStyle: largeTitle, fontSize: 34pt, fontWeight: 700 }
  headline: { fontFamily: SF Pro, textStyle: headline, fontSize: 17pt, fontWeight: 600 }
  body: { fontFamily: SF Pro, textStyle: body, fontSize: 17pt, fontWeight: 400 }
  caption: { fontFamily: SF Pro, textStyle: caption1, fontSize: 12pt, fontWeight: 400 }
rounded:
  sm: 8pt
  md: 14pt
  lg: 20pt
  curve: continuous
spacing:
  xs: 4pt
  sm: 8pt
  md: 16pt
  lg: 24pt
motion:
  defaultSpring: "response: 0.35, dampingFraction: 0.75"
haptics:
  tap: "impact(weight: .medium)"
---
```

---

## 5. SwiftUI Kod Üretim Şablonu

```swift
import SwiftUI

struct StandardCardView: View {
    let title: String
    let subtitle: String
    let action: () -> Void

    var body: some View {
        Button(action: {
            UIImpactFeedbackGenerator(style: .medium).impactOccurred()
            action()
        }) {
            VStack(alignment: .leading, spacing: 8) {
                Text(title)
                    .font(.headline)
                    .foregroundColor(.primary)
                Text(subtitle)
                    .font(.subheadline)
                    .foregroundColor(.secondary)
            }
            .padding(16)
            .frame(maxWidth: .infinity, alignment: .leading)
            .frame(minHeight: 44) // 44pt Touch Target kuralı
            .background(Color(uiColor: .secondarySystemBackground))
            .clipShape(RoundedRectangle(cornerRadius: 14, style: .continuous))
        }
        .buttonStyle(ScaleButtonStyle())
    }
}

struct ScaleButtonStyle: ButtonStyle {
    func makeBody(configuration: Configuration) -> some View {
        configuration.label
            .scaleEffect(configuration.isPressed ? 0.97 : 1.0)
            .opacity(configuration.isPressed ? 0.8 : 1.0)
            .animation(.spring(response: 0.25, dampingFraction: 0.7), value: configuration.isPressed)
    }
}
```

