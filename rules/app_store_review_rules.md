# App Store Review Guidelines - UI & UX Kabul Kriterleri

Bu kural seti, geliştirilen uygulamanın Apple App Store inceleme sürecinde (App Review) arayüz ve kullanıcı deneyimi gerekçeleriyle **reddedilmesini (rejection)** önlemek için hazırlanmıştır.

---

## 1. Kritik UI Reddedilme Sebepleri (Section 10 - User Interface)

* **10.1 HIG Uyumluluğu:**
  - Uygulama, Apple iOS Human Interface Guidelines standartlarına tam uyumlu olmak zorundadır. Standart dışı, tutarsız ve kullanıcıyı yanıltıcı arayüzler reddedilir.
* **10.2 Sistem Uygulamalarını Taklit Etmeme:**
  - App Store, iTunes Store, Ayarlar veya Apple'ın varsayılan dahili uygulamalarına birebir benzeyen, kullanıcıda sistem uygulamasıymış hissi uyandıran tasarımlar kesinlikle reddedilir.
* **10.3 Sistem İkon ve Butonlarının Doğru Kullanımı:**
  - Apple'ın sistem ikonları (örneğin paylaşım ikonu, arama büyüteci, çöp kutusu, geri butonu vb.) kendi standart anlamları dışında başka bir eylem için kullanılamaz.
* **10.4 Alternatif Masaüstü / Ana Ekran Simülasyonu:**
  - iOS ana ekranını, kilit ekranını veya alternatif bir masaüstü widget ortamını simüle eden uygulamalar reddedilir.
* **10.5 Standart Donanım Anahtarlarını Değiştirmeme:**
  - Ses açma/kapatma (Volume Up/Down) veya Sessiz (Mute) anahtarının temel işlevini değiştiren veya arayüzde zorunlu eyleme bağlayan yapılar onaylanmaz.
* **10.6 Arayüz Kalite Eşiği (Quality Bar):**
  - Apple "amatör" görünen, birkaç günde alelacele toplanmış veya aşırı karmaşık/kullanışsız UI'ları doğrudan reddetme hakkını saklı tutar.

---

## 2. Fonksiyonel ve Deneyimsel Kurallar (Functionality & Content)

* **Boş / Çalışmayan Ekranlar:**
  - "Yapım aşamasında", "Çok yakında" veya tıklandığında hiçbir şey yapmayan sahte butonlar bulunan uygulamalar reddedilir.
* **Webview Sarmalayıcılar:**
  - Sadece bir web sitesini tam ekran gösteren, hiçbir native iOS deneyimi ve dokunma optimizasyonu sunmayan uygulamalar onaylanmaz.
* **Çökme ve Donma (Crashes & ANR):**
  - Uygulama inceleme sırasında tek bir kez bile çökerse doğrudan reddedilir.
* **Kullanıcı Girişi ve İzinler:**
  - Giriş yapmadan (Login Wall) deneyimlenebilecek içerikler için zorunlu kayıt istenmemelidir.
  - Kamera, Konum, Bildirim gibi izinler kullanıcı eylemi öncesinde bağlamsal olarak ve açıklayıcı metinle (`NSLocationWhenInUseUsageDescription` vb.) istenmelidir.

