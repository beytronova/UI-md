# Adaptif Material Design 3 (M3) for iOS Kural Seti

Bu belge, Google'ın Material Design 3 (M3 / Material You) tasarım dilini iOS platformuna taşırken dikkat edilmesi gereken hibrit ve adaptif kuralları içerir. Amaç: Google ekosisteminin imza kimliğini korurken, iOS kullanıcı deneyimine yabancılaşmamaktır.

---

## 1. Tasarım Yaklaşımı (Adaptif M3 Felsefesi)

* **Birebir Taklitten Kaçınma:** iOS'in kendi sistem uygulamalarını tamamen kopyalamak Google kimliğini yok eder.
* **Kaba Porttan Kaçınma:** Android için yazılmış bir UI'ı doğrudan iOS'e aktarmak kullanıcıda yabancılık ve kalitesizlik hissi yaratır.
* **Altın Denge:**
  - *Korunan M3 Kimliği:* Tonal renk paletleri, ikonografi, tipografi hiyerarşisi (Display -> Headline -> Body -> Label).
  - *Saygı Duyulan iOS Dinamikleri:* Edge-swipe ile geri dönme jesti, native modal/alert sunumları, iOS haptic ve yaylanma fizikleri.

---

## 2. Navigasyon ve Çubuklar (Navigation & Bars)

### 2.1 Bottom Navigation vs iOS Tab Bar
* M3 Bottom Navigation Bar kullanılacaksa, iOS'in geleneksel Tab Bar alışkanlıkları ve HIG boşluk kuralları gözetilmelidir.
* İkon ve etiket hizalamaları iOS ekran alt boşluklarına ve Safe Area sınırlarına tam uyum sağlamalıdır.

### 2.2 Top App Bar & Safe Area
* Üst App Bar yüksekliği iOS `UINavigationBar` standartları ile uyumlu olmalıdır.
* Dynamic Island veya Çentik (Notch) altına taşma olmamalı, içerik Safe Area'nın altına otomatik kaydırılmalıdır (`Large Title` daralma mantığı).

---

## 3. Floating Action Button (FAB) Yerleşimi

* **Home Indicator Çakışması:** iOS cihazların altındaki Home Indicator çizgisinin üzerine FAB gelmemelidir.
* **Alt Boşluk (Padding):** FAB için standart Android alt boşluğu yerine, iOS ekran altı Safe Area + ek padding (minimum 16pt Safe Area üstü) bırakılmalıdır.
* **Genişletilmiş FAB (Extended FAB):** Sayfa kaydırıldığında küçülmeli (`shrink to icon`), durduğunda genişlemelidir.

---

## 4. Yüzeyler, Kartlar ve Gölgelendirme (Surfaces & Elevation)

* **Tonal Elevation:**
  - iOS'te sık kullanılan ağır drop-shadow efektleri yerine, M3'ün **Surface Tint** ve yüzey tonlama katmanları (0-5 kademe) kullanılmalıdır.
  - Kart arka planları `surfaceContainerLowest` ile `surfaceContainerHighest` arasında değişen tonlarla ayrıştırılmalıdır.
* **Karanlık Mod Derinliği:**
  - Karanlık modda derinlik gölgeyle değil, yüzey renginin ton açıklığı ve hafif opaklık farklarıyla sağlanmalıdır.

---

## 5. Tipografi ve Hibrit Ölçekleme

* **M3 Tipografi Hiyerarşisi:**
  - `Display (Large, Medium, Small)`
  - `Headline (Large, Medium, Small)`
  - `Title (Large, Medium, Small)`
  - `Body (Large, Medium, Small)`
  - `Label (Large, Medium, Small)`
* **iOS Font Entegrasyonu:**
  - Native performansı ve okunabilirliği korumak için sistem fontu olan **SF Pro** ile M3 hiyerarşisi hibritlenebilir veya Roboto sistem metin stilleriyle eşleştirilmelidir.
  - Dynamic Type desteği M3 metin stillerine entegre edilmelidir.

---

## 6. Renk Sistemi ve Material You Entegrasyonu

* **Tonal Paletler (Tone 0 - 100):**
  - Primary, Secondary, Tertiary ve Neutral tonları tanımlanmalıdır.
* **Semantik Eşleşme:**
  - `primary` & `onPrimary`
  - `surface` & `onSurface`
  - `surfaceContainer` & `outline`
* **SwiftUI / UIKit Tanımlamaları:**
  - Renkler `Color` extension veya `UIColor` assetleri olarak sistem `colorScheme` (`.light` / `.dark`) ile otomatik değişecek şekilde yapılandırılmalıdır.

---

## 7. Hareket ve Dokunma Tepkileri (Motion & Physics)

* Android'deki dairesel dalgalanma (ripple) efekti yerine, iOS'te basıldığında hafif opaklık/ölçek değişimi ve iOS Taptic Engine geri bildirimi tercih edilmelidir.
* Animasyon ivmelenmelerinde iOS'in kendi yay fiziği (`UIView.animate(withDuration:... usingSpringWithDamping:...)` veya SwiftUI `.spring()`) uygulanmalıdır.
