# Mobil Programlama Ödev 7 

## Derin Bağlantı (Deep Link) Yapısı
Bu e-ticaret uygulamasında, özel bir protokol şemasına dayalı derin bağlantı yapısı kullanılmıştır:

Genel Format: Uygulama, myapp://product/:id formatını dinler.

Şema (Scheme): myapp olarak belirlenmiştir. İşletim sistemi, bu özel şemayı tanıdığında uygulamayı başlatır.

Host: product anahtar kelimesi, bu linkin uygulamanın içindeki bir ürün detay sayfasına yönlendirme yaptığını belirtir.

Parametre: :id kısmı, dinamik olarak değişen ürün kimliğini taşır. Flutter uygulaması bu ID'yi ayrıştırarak kullanıcıyı ilgili ProductDetailPage'e yönlendirir.

Örnek Kullanım: Dışarıdan bir kaynağın (tarayıcıdaki HTML dosyası gibi) myapp://product/5 linkine tıklanması, uygulamayı açar ve kullanıcıyı doğrudan ID'si 5 olan ürünün detay sayfasına götürür.

## Uygulama Test Adımları
Derin bağlantıların (Deep Link) tüm senaryolarda doğru çalıştığından emin olmak için bu adımları takip edin:

Flutter Uygulamasını Başlatın: Geliştirdiğiniz Flutter uygulamasını bir fiziksel telefonda veya emülatörde çalıştırın.

HTML Test Sayfasını Açın: Sağladığınız test_html.html dosyasını cihazınızın varsayılan web tarayıcısında (Android Chrome veya iOS Safari gibi) açın.

Kapalı Uygulama Testi: Uygulamayı tamamen kapatın (arka plandan da kaldırın). Tarayıcıdaki bir ürün linkine (Örn: Ürün 42'yi Aç) tıklayın.

Kontrol: Uygulamanın otomatik olarak açılması ve "Seçilen Ürün ID: 3" yazan detay sayfasını göstermesi gerekir.

Açık Uygulama Testi (Akış Dinleme): Uygulama açıkken (örneğin ana sayfadayken) tarayıcıya geri dönün ve farklı bir ürün linkine (Örn: Ürün 10'u Aç) tıklayın.

Kontrol: Uygulama, yeni bir sayfa açmadan mevcut görünümde direkt olarak "Seçilen Ürün ID: 10" detay sayfasına yönlenmelidir.

Bu adımlar, hem uygulamanın başlatılma anında (getInitialUri) hem de çalışma esnasında (uriLinkStream) linkleri başarılı bir şekilde yakaladığını doğrular.
