# DESIGN.md - Apple / SwiftUI & UIKit Format Spesifikasyonu

Bu doküman, yapay zeka ajanlarının ve geliştiricilerin native Apple platformlarında (iOS/iPadOS/macOS) tutarlı, sıfır tahminle (zero-guessing) UI üretebilmesi için kullanılan **DESIGN.md** standartlarını belirler.

---

## 1. Temel İlke

> **"Makine tarafından okunabilir token'lar (YAML front matter) kesin değerleri taşır; insan tarafından okunabilir metin (Markdown) tasarımın arkasındaki nedeni açıklar."**

CSS / Web birimleri (`px`, `rem`, `@media`) yerine native Apple kavramları kullanılır:
* `pt` (points)
* Dynamic Type textStyle (`largeTitle`, `body`, `caption`)
* SF Pro font ailesi ve SF Symbols
* Semantic system colors (`systemBackground`, `label`, `accent`)
* Continuous corner radius (`.continuous`)

---

## 2. Standart DESIGN.md Yapısı

Her `DESIGN.md` dosyası iki ana bölümden oluşur:

### 2.1 YAML Front Matter (Tokens)
```yaml
---
name: AppName
platform:
  os: [iOS, iPadOS]
  minimumDeployment: "17.0"
  appearance: [light, dark]
colors:
  primary:
    light: "#1A1C1E"
    dark: "#F2F2F7"
  secondary: "#6C7278"
  accent: "#007AFF"
  background:
    light: "#FFFFFF"
    dark: "#000000"
  surface:
    light: "#F2F2F7"
    dark: "#1C1C1E"
typography:
  largeTitle:
    fontFamily: SF Pro
    textStyle: largeTitle
    fontSize: 34pt
    fontWeight: 700
  headline:
    fontFamily: SF Pro
    textStyle: headline
    fontSize: 17pt
    fontWeight: 600
  body:
    fontFamily: SF Pro
    textStyle: body
    fontSize: 17pt
    fontWeight: 400
  caption:
    fontFamily: SF Pro
    textStyle: caption1
    fontSize: 12pt
    fontWeight: 400
rounded:
  sm: 8pt
  md: 14pt
  lg: 20pt
  pill: 9999pt
  curve: continuous
spacing:
  xs: 4pt
  sm: 8pt
  md: 16pt
  lg: 24pt
  xl: 32pt
motion:
  defaultSpring: "response: 0.35, dampingFraction: 0.75"
  quickResponse: "response: 0.2, dampingFraction: 0.8"
haptics:
  primaryAction: "impact(weight: .medium)"
  selection: "selectionChanged"
  error: "notification(type: .error)"
---
```

### 2.2 Markdown Rationale (Tasarım Gerekçeleri)
YAML'ın ardından gelen kısımdır:
* **Overview:** Uygulamanın hissettirmesi gereken atmosfer (ör. sakin, profesyonel, enerjik).
* **Component Rationale:** Kartların, butonların, navigasyon yapısının nasıl davranacağı.
* **Layout Patterns:** Listelerin aralıkları, grid yapısı, Safe Area yönetimi.

---

## 3. SwiftUI Kod Eşleşmesi Örneği

Token'ların doğrudan SwiftUI koduna aktarımı:

```swift
struct PrimaryButton: View {
    let title: String
    let action: () -> Void

    var body: some View {
        Button(action: {
            UIImpactFeedbackGenerator(style: .medium).impactOccurred()
            action()
        }) {
            Text(title)
                .font(.headline) // Dynamic Type uyumlu
                .foregroundColor(.white)
                .frame(maxWidth: .infinity)
                .frame(minHeight: 44) // 44pt Touch Target kuralı
                .background(Color.accentColor)
                .clipShape(RoundedRectangle(cornerRadius: 14, style: .continuous))
        }
        .buttonStyle(ScaleButtonStyle())
    }
}
```
