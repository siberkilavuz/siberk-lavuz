<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Siber Kılavuz</title>
    <style>
        /* Genel Stil */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            background-color: #ffffff;
            color: #ffbb00;
            overflow-x: hidden;
        }

        /* Arka Plan Video */
        .background-video {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            object-fit: cover;
            z-index: -1;
            filter: brightness(60%);
        }

        header {
            background-color: rgba(136, 45, 45, 0.7);
            color: #ffffff;
            padding: 2rem 0;
            text-align: center;
            transition: opacity 1s;
        }

        /* Geçiş Animasyonları */
        .fade-in {
            opacity: 0;
            animation: fadeIn 2s forwards;
        }

        @keyframes fadeIn {
            to { opacity: 1; }
        }

        nav {
            display: flex;
            justify-content: center;
            gap: 1rem;
            background-color: rgba(0, 0, 0, 0.8);
            padding: 1rem 0;
        }

        nav a {
            color: #e10b0b;
            text-decoration: none;
            padding: 0.5rem 1rem;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        nav a:hover {
            background-color: #ffffff;
            border-radius: 5px;
        }

        .container {
            padding: 3rem 2rem;
            max-width: 1200px;
            margin: auto;
            text-align: center;
        }

        /* Bölümler */
        .section {
            display: none;
            transition: transform 0.5s ease-in-out, opacity 0.5s;
        }
        
        .active-section {
            display: block;
            opacity: 1;
            transform: translateY(0);
        }

        .services div {
            display: inline-block;
            width: 30%;
            padding: 1rem;
            box-sizing: border-box;
            vertical-align: top;
            background-color: rgba(255, 0, 0, 0.9);
            border-radius: 5px;
            margin: 1%;
            box-shadow: 0 0 10px rgba(255, 255, 255, 0.1);
        }

        footer {
            background-color: rgba(0, 0, 0, 0.7);
            color: #ffffff;
            text-align: center;
            padding: 1rem 0;
            position: relative;
            z-index: 1;
        }
        
        .product-card {
            padding: 1rem;
            margin: 1rem;
            border: 1px solid #ddd;
            border-radius: 10px;
            background-color: #fff;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
            text-align: center;
        }

        .product-card button {
            background-color: #28a745;
            color: #fff;
            padding: 0.5rem;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        /* Slider */
        .slider {
            max-width: 100%;
            overflow: hidden;
            margin-bottom: 2rem;
        }
        .slide {
            display: none;
            font-size: 1.5rem;
            padding: 2rem;
            background: rgba(0, 0, 0, 0.7);
            color: white;
            text-align: center;
        }
        .active-slide {
            display: block;
        }

        

        /* Müşteri Yorumları */
        #reviews {
            background-color: #f9f9f9;
            padding: 2rem;
            text-align: center;
        }

        .review {
            margin: 1rem 0;
            font-style: italic;
        }
        .review span {
            display: block;
            margin-top: 0.5rem;
            font-weight: bold;
        }

        /* İletişim */
        .contact-form {
            max-width: 600px;
            margin: auto;
            background-color: #f9f9f9;
            padding: 2rem;
            border-radius: 5px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
        }

        .contact-form input, .contact-form textarea {
            width: 100%;
            padding: 0.8rem;
            margin-bottom: 1rem;
            border: 1px solid #ddd;
            border-radius: 5px;
        }

        .contact-form button {
            background-color: #ffbb00;
            color: white;
            padding: 1rem 2rem;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            width: 100%;
        }

        .contact-info {
            margin: 2rem 0;
        }

        .contact-info p {
            font-size: 1.1rem;
        }
    </style>

    <script>
        function showSection(sectionId) {
            // Tüm bölümleri gizle
            const sections = document.querySelectorAll('.section');
            sections.forEach(section => {
                section.classList.remove('active-section');
            });

            // Seçilen bölümü göster
            const activeSection = document.getElementById(sectionId);
            activeSection.classList.add('active-section');
        }

        // Varsayılan olarak "home" bölümü gösterilir
        window.onload = function() {
            showSection('home');
            setInterval(showSlide, 3000); // Her 3 saniyede kaydır
        };

        // Slider
        let currentSlide = 0;
        const slides = document.querySelectorAll('.slide');

        function showSlide() {
            slides.forEach((slide, index) => {
                slide.classList.toggle('active-slide', index === currentSlide);
            });
            currentSlide = (currentSlide + 1) % slides.length;
        }

      
        

        // Ürün filtreleme
        function filterProducts(category) {
            const products = document.querySelectorAll('.product-card');
            products.forEach(product => {
                product.style.display = product.classList.contains(category) || category === 'all' ? 'block' : 'none';
            });
        }

        // Sepete ürün ekleme
        function addToCart(product) {
            const cartItems = document.getElementById('cart-items');
            cartItems.innerHTML += `<p>${product}</p>`;
        }
    </script>
</head>
<body>

    <!-- Arka Plan Video -->
    <video autoplay muted loop class="background-video">
        <source src="galeri/videolar/Matrix Rain Codes (4K FULL HD).mp4 " type="video/mp4">
    </video>

    <header class="fade-in">
        <h1>Siber Kılavuz</h1>
        <p>Dijital Dünyada Güvenle Yol Alın</p>
    </header>

    <nav>
        <a onclick="showSection('home')"><b>Ana Sayfa</b></a>
        <a onclick="showSection('about')"><b>Hakkımızda</b></a>
        <a onclick="showSection('services')"><b>Hizmetler</b></a>
        <a onclick="showSection('products')"><b>Ürünler</b></a>
        <a onclick="showSection('cart')"><b>Sepet</b></a>
        <a onclick="showSection('contact')"><b>İletişim</b></a>
    </nav>

    <div class="container">
        <!-- Slider -->
        <div class="slider">
            <div class="slide active-slide"><b>Hoşgeldiniz Siber Kılavuz’a</b></div>
            <div class="slide">Dijital Güvenliğiniz İçin Buradayız</div>
            <div class="slide">Eğitim ve Danışmanlık Hizmetlerimizi İnceleyin</div>
        </div>

        <!-- Ana Sayfa Bölümü -->
        <section id="home" class="section active-section">
            <h2><b>Hoşgeldiniz</b></h2>
            <p><b>Siber Kılavuz, dijital güvenlik konusunda size rehberlik eden bir platformdur. Güvenli bir dijital dünyaya adım atın!</b></p>
        
        </section>
        <!-- Hakkımızda Bölümü -->
        <section id="about" class="section">
            <h2>Hakkımızda</h2>
            <p><b>Siber kılavuz olarak 2024 yılında YouTube'dan başladığımız şirket olma yolunda bizi yalnız bırakmayan ve bize destek olan her takipçimize ayrı ayrı teşekkür ediyoruz.</b></p>
            <p><b>Siber kılavuz olarak diğer şirket ve platformlardan farkımız takipçilerimizi bir araç olarak değil ailemiz olarak görmemizdir.</b></p>
            <p><b>siz takipçilerimizi şirket olma yolunda nasıl ailemiz olarak görüyorsak şirket olduktan sonra da bu süreç böyle ilerliyecektir.</b> </p>
            <p><b>bu durum her daim vizyonumuz da ve misyonumuzda bulunacaktır.</b></p>
        </section>

        <!-- Hizmetler Bölümü -->
        <section id="services" class="section">
            <h2>Hizmetler</h2>
            <div class="services">
                <div>
                    <h3><u>Siber Güvenlik Eğitimleri</u></h3>
                    <p><b>Dijital güvenlik konusunda uzmanlaşmak isteyenler için YouTube'da ücretsiz eğitimlerimiz mevcuttur.</b></p>
                </div>
                <div>
                    <h3><u>Siber Güvenlik Danışmanlık:</u></h3>
                    <p><b>Dünyada genel olarak Bilgisayar mühendisliği seçecek olan kişiler siber güvenlik mesleği ve yazlım mühendisliği mesleği arasında kalırlar bu teknoloji dünyasında ve deryasındaki yüzlerce meslekten birini seçmeye karar vermek için danışmanlık alabilirsiniz.</b></p>
                </div>   
            </div>
            
        </section>

        <!-- Ürünler Bölümü -->
        <section id="products" class="section">
            <h2>Ürünler</h2><br>
            <h2>geliştirme kartları</h2>
            <button onclick="filterProducts('all')">Tüm Ürünler</button>
            <button onclick="filterProducts('yazilim')">Yazılım</button>
            <button onclick="filterProducts('hizmet')">Hizmetler</button>

            <div class="product-card yazilim">
                <h3>ESP 8266 WİFİ CH340</h3>
                <p>NodeMCU V3 ESP8266 ESP-12F Geliştirme Kartı - CH340, internet bağlantılı projelerinizi hızlı ve kolay bir şekilde gerçekleştirmek için tasarlanmıştır.</p>
                <img src="galeri/fotoğraflar/ch340.jpg"  height="250px" alt="">
                <img src="galeri/fotoğraflar/ch3402.jpg" height="250px"  alt="">
                <button onclick="addToCart('ESP 8266 WİFİ CH340 ürününü satın almak için lütfen satıcı ile iletişime geçin.')">Sepete Ekle</button>
            </div>
            <div class="product-card hizmet">
                <h3>DİGİSPARK</h3>
                <p>Bir Kickstarter projesi olarak başlayan digispark Arduino IDE üzerinden aynı Arduino gibi programlanabilir bir geliştirme kartıdır. Boyutlarının küçük olması ve USB portlarına direkt bağlanmasıyla dikkat çekmektedir. Küçük ve az yer kaplaması istenen projelerde rahatlıkla kullanılabilir.</p>
                <img src="galeri/fotoğraflar/digispark.webp" height="250px" alt="">
               <img src="galeri/fotoğraflar/digispark2.webp"  height="250px"   alt="">
                <button onclick="addToCart('DİGİSPARK ürününü satın almak için lütfen satıcı ile iletişime geçin.')">Sepete Ekle</button>
             </div>
           
                <div class="product-card yazilim">
                    <h3>ESP 8266 WİFİ CH340</h3>
                    <p>NodeMCU V3 ESP8266 ESP-12F Geliştirme Kartı - CH340, internet bağlantılı projelerinizi hızlı ve kolay bir şekilde gerçekleştirmek için tasarlanmıştır.</p>
                    <img src="galeri/fotoğraflar/ch340.jpg"  height="250px" alt="">
                    <img src="galeri/fotoğraflar/ch3402.jpg" height="250px"  alt="">
                    <button onclick="addToCart('ESP 8266 WİFİ CH340 ürününü satın almak için lütfen satıcı ile iletişime geçin.')">Sepete Ekle</button>
                </div>
           
           
           
           
            </div>
        </section>

        <!-- Sepet Bölümü -->
        <section id="cart" class="section">
            <h2>Sepetiniz</h2>
            <div id="cart-items"></div>
        </section>

        <!-- Müşteri Yorumları -->
        <section id="reviews" class="section">
            <h2>Müşteri Yorumları</h2>
            <div class="review">
                <p>“Siber Kılavuz sayesinde çok daha güvendeyim!”</p>
                <span>- Ali Y.</span>
            </div>
            <div class="review">
                <p>“Profesyonel destekleri sayesinde şirketimizin güvenliği sağlandı.”</p>
                <span>- Ayşe T.</span>
            </div>
        </section>

        <!-- İletişim Bölümü -->
        <section id="contact" class="section">
            <h2>İletişim</h2>
            <div class="contact-info">
                <p><strong>Adres:</strong> Adana, Türkiye</p>
                <p><strong>Telefon:</strong> +90 555 123 45 67</p>
                <p><strong>E-posta:</strong> info@siberkilavuz.com</p>
            </div>

            <div class="contact-form">
                <h3>Bizimle İletişime Geçin</h3>
                <form>
                    <input type="text" placeholder="Adınız" required><br>
                    <input type="email" placeholder="E-posta" required><br>
                    <textarea placeholder="Mesajınız" rows="4" required></textarea><br>
                    <button type="submit">Gönder</button>
                </form>
            </div>
        
        
        
        </section>

       

    </div>

    <footer>
        <p>&copy;  <em><u><b>2024 Siber Kılavuz</b></u></em></p>
    </footer>

</body>
</html>
