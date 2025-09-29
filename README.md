<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>بازار میوه‌های تازه - میوه‌های ارگانیک درجه یک</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Vazirmatn:wght@300;400;500;700&display=swap');
        
        body {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Vazirmatn', 'Tahoma', sans-serif;
            line-height: 1.6;
            color: #333;
            background: #f8fff8;
            direction: rtl;
        }

        * {
            box-sizing: border-box;
        }

        /* Header & Navigation */
        .header {
            background: linear-gradient(135deg, #2d5a2d 0%, #4a7c4a 100%);
            color: white;
            padding: 1rem 0;
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 2rem;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 1.8rem;
            font-weight: bold;
        }

        .nav-menu {
            display: flex;
            list-style: none;
            gap: 2rem;
            margin: 0;
            padding: 0;
        }

        .nav-menu a {
            color: white;
            text-decoration: none;
            transition: color 0.3s ease;
            font-weight: 500;
        }

        .nav-menu a:hover {
            color: #90EE90;
        }

        /* Main Container */
        .main-container {
            min-height: 100vh;
            padding-top: 80px;
        }

        /* Page Sections */
        .page-section {
            display: none;
            opacity: 0;
            transform: translateY(20px);
            transition: all 0.5s ease;
        }

        .page-section.active {
            display: block;
            opacity: 1;
            transform: translateY(0);
        }

        /* Hero Section */
        .hero {
            background: linear-gradient(135deg, rgba(45, 90, 45, 0.8), rgba(74, 124, 74, 0.8)), 
                        linear-gradient(45deg, #f0f8f0, #e8f5e8);
            padding: 80px 0;
            text-align: center;
            color: white;
            position: relative;
            overflow: hidden;
        }

        .hero-content {
            max-width: 800px;
            margin: 0 auto;
            padding: 0 2rem;
            position: relative;
            z-index: 2;
        }

        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 1rem;
            animation: fadeInUp 1s ease-out;
        }

        .hero p {
            font-size: 1.3rem;
            margin-bottom: 2rem;
            animation: fadeInUp 1s ease-out 0.3s both;
        }

        .cta-button {
            background: linear-gradient(45deg, #ff6b6b, #ff8e53);
            color: white;
            padding: 15px 30px;
            border: none;
            border-radius: 50px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
            display: inline-block;
            animation: fadeInUp 1s ease-out 0.6s both;
        }

        .cta-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(255, 107, 107, 0.3);
        }

        /* Floating Fruits Animation */
        .floating-fruit {
            position: absolute;
            opacity: 0.1;
            animation: float 6s ease-in-out infinite;
        }

        .floating-fruit:nth-child(1) { top: 20%; right: 10%; animation-delay: 0s; }
        .floating-fruit:nth-child(2) { top: 60%; left: 15%; animation-delay: 2s; }
        .floating-fruit:nth-child(3) { bottom: 30%; right: 20%; animation-delay: 4s; }

        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(180deg); }
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Main Content */
        .main-content {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
        }

        .section {
            padding: 4rem 0;
        }

        .section h2 {
            text-align: center;
            font-size: 2.5rem;
            color: #2d5a2d;
            margin-bottom: 3rem;
            position: relative;
        }

        .section h2::after {
            content: '';
            position: absolute;
            bottom: -10px;
            right: 50%;
            transform: translateX(50%);
            width: 80px;
            height: 3px;
            background: linear-gradient(45deg, #ff6b6b, #ff8e53);
            border-radius: 2px;
        }

        /* Features Section */
        .features {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .feature-card {
            background: white;
            padding: 2rem;
            border-radius: 15px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
            text-align: center;
            transition: transform 0.3s ease;
        }

        .feature-card:hover {
            transform: translateY(-5px);
        }

        .feature-icon {
            margin-bottom: 1rem;
        }

        /* Products Section */
        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .product-card {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
            position: relative;
            cursor: pointer;
        }

        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 35px rgba(0,0,0,0.15);
        }

        .product-image {
            height: 200px;
            background: linear-gradient(135deg, #f0f8f0, #e8f5e8);
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
        }

        .product-info {
            padding: 1.5rem;
        }

        .product-name {
            font-size: 1.3rem;
            font-weight: bold;
            color: #2d5a2d;
            margin-bottom: 0.5rem;
        }

        .product-description {
            color: #666;
            margin-bottom: 1rem;
            font-size: 0.9rem;
        }

        .product-price {
            font-size: 1.5rem;
            font-weight: bold;
            color: #ff6b6b;
            margin-bottom: 1rem;
        }

        .price-input {
            width: 100%;
            padding: 8px 12px;
            border: 2px solid #e8f5e8;
            border-radius: 8px;
            font-size: 1rem;
            transition: border-color 0.3s ease;
            text-align: center;
            font-family: 'Vazirmatn', sans-serif;
        }

        .price-input:focus {
            outline: none;
            border-color: #4a7c4a;
        }

        .view-product-btn {
            background: linear-gradient(45deg, #4a7c4a, #2d5a2d);
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            transition: all 0.3s ease;
            width: 100%;
            margin-top: 10px;
            font-family: 'Vazirmatn', sans-serif;
        }

        .view-product-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(74, 124, 74, 0.3);
        }

        /* Individual Product Page */
        .product-page {
            padding: 2rem 0;
        }

        .product-detail {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 3rem;
            align-items: center;
            margin-bottom: 3rem;
        }

        .product-detail-image {
            text-align: center;
            background: linear-gradient(135deg, #f0f8f0, #e8f5e8);
            padding: 3rem;
            border-radius: 20px;
        }

        .product-detail-info h1 {
            font-size: 2.5rem;
            color: #2d5a2d;
            margin-bottom: 1rem;
        }

        .product-detail-info p {
            font-size: 1.1rem;
            line-height: 1.8;
            margin-bottom: 1.5rem;
        }

        .price-section {
            background: white;
            padding: 2rem;
            border-radius: 15px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
            margin-bottom: 2rem;
        }

        .price-section h3 {
            color: #2d5a2d;
            margin-bottom: 1rem;
        }

        .price-display {
            font-size: 2rem;
            font-weight: bold;
            color: #ff6b6b;
            margin: 1rem 0;
        }

        .back-btn {
            background: linear-gradient(45deg, #666, #888);
            color: white;
            padding: 12px 25px;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-family: 'Vazirmatn', sans-serif;
            margin-bottom: 2rem;
        }

        .back-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(102, 102, 102, 0.3);
        }

        /* About Section */
        .about-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 3rem;
            align-items: center;
            margin-top: 3rem;
        }

        .about-text {
            font-size: 1.1rem;
            line-height: 1.8;
        }

        .about-image {
            text-align: center;
        }

        /* Contact Section */
        .contact-info {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .contact-card {
            background: white;
            padding: 2rem;
            border-radius: 15px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
            text-align: center;
        }

        .contact-icon {
            margin-bottom: 1rem;
        }

        /* Footer */
        .footer {
            background: #2d5a2d;
            color: white;
            text-align: center;
            padding: 3rem 0;
            margin-top: 4rem;
        }

        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 1rem;
            margin: 2rem 0;
        }

        .social-link {
            width: 40px;
            height: 40px;
            background: rgba(255,255,255,0.1);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: background 0.3s ease;
        }

        .social-link:hover {
            background: rgba(255,255,255,0.2);
        }

        /* Mobile Responsive */
        @media (max-width: 768px) {
            .nav-menu {
                display: none;
            }
            
            .hero h1 {
                font-size: 2.5rem;
            }
            
            .hero p {
                font-size: 1.1rem;
            }
            
            .about-content, .product-detail {
                grid-template-columns: 1fr;
            }
            
            .nav-container {
                padding: 0 1rem;
            }
            
            .main-content {
                padding: 0 1rem;
            }
        }

        /* Smooth scrolling */
        html {
            scroll-behavior: smooth;
        }

        /* Animation classes */
        .fade-in {
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.6s ease;
        }

        .fade-in.visible {
            opacity: 1;
            transform: translateY(0);
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header class="header">
        <div class="nav-container">
            <div class="logo">
                <svg width="40" height="40" viewBox="0 0 40 40">
                    <circle cx="20" cy="22" r="15" fill="#ff6b6b"/>
                    <path d="M20 8 Q23 10 20 18 Q17 10 20 8" fill="#90EE90"/>
                </svg>
                بازار میوه‌های تازه
            </div>
            <nav>
                <ul class="nav-menu">
                    <li><a href="#" onclick="showSection('home')">صفحه اصلی</a></li>
                    <li><a href="#" onclick="showSection('products')">محصولات</a></li>
                    <li><a href="#" onclick="showSection('about')">درباره ما</a></li>
                    <li><a href="#" onclick="showSection('contact')">تماس با ما</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <div class="main-container">
        <!-- Home Section -->
        <section id="home" class="page-section active">
            <div class="hero">
                <div class="floating-fruit">
                    <svg width="60" height="60" viewBox="0 0 60 60">
                        <circle cx="30" cy="30" r="25" fill="#ff6b6b"/>
                        <path d="M30 10 Q35 15 30 25 Q25 15 30 10" fill="#4a7c4a"/>
                    </svg>
                </div>
                <div class="floating-fruit">
                    <svg width="60" height="60" viewBox="0 0 60 60">
                        <ellipse cx="30" cy="35" rx="20" ry="25" fill="#ffd93d"/>
                        <path d="M30 15 Q35 20 30 30 Q25 20 30 15" fill="#4a7c4a"/>
                    </svg>
                </div>
                <div class="floating-fruit">
                    <svg width="60" height="60" viewBox="0 0 60 60">
                        <circle cx="30" cy="30" r="22" fill="#ff8c42"/>
                        <circle cx="25" cy="25" r="3" fill="#ffb366" opacity="0.8"/>
                    </svg>
                </div>
                
                <div class="hero-content">
                    <h1>بازار میوه‌های تازه</h1>
                    <p>میوه‌های ارگانیک درجه یک، تازه از باغ تا سفره شما. بهترین کیفیت و طعم طبیعی را تجربه کنید.</p>
                    <a href="#" onclick="showSection('products')" class="cta-button">خرید میوه‌های تازه</a>
                </div>
            </div>

            <div class="main-content">
                <!-- Features Section -->
                <div class="section fade-in">
                    <h2>چرا بازار میوه‌های تازه؟</h2>
                    <div class="features">
                        <div class="feature-card">
                            <div class="feature-icon">
                                <svg width="60" height="60" viewBox="0 0 60 60">
                                    <circle cx="30" cy="30" r="25" fill="#4a7c4a" opacity="0.1"/>
                                    <path d="M30 10 L35 20 L45 20 L37 28 L40 38 L30 33 L20 38 L23 28 L15 20 L25 20 Z" fill="#ffd93d"/>
                                </svg>
                            </div>
                            <h3>کیفیت درجه یک</h3>
                            <p>میوه‌های دست‌چین از باغ‌های ارگانیک معتبر، تضمین بالاترین کیفیت و تازگی برای مشتریان عزیز.</p>
                        </div>
                        <div class="feature-card">
                            <div class="feature-icon">
                                <svg width="60" height="60" viewBox="0 0 60 60">
                                    <circle cx="30" cy="30" r="25" fill="#4a7c4a" opacity="0.1"/>
                                    <path d="M15 25 L30 15 L45 25 L45 45 L15 45 Z" fill="#ff6b6b"/>
                                    <rect x="25" y="35" width="10" height="10" fill="#ffffff"/>
                                </svg>
                            </div>
                            <h3>تازه از باغ</h3>
                            <p>مستقیم از باغ‌های محلی به درب منزل شما. میوه‌های ما در اوج رسیدگی برداشت می‌شوند.</p>
                        </div>
                        <div class="feature-card">
                            <div class="feature-icon">
                                <svg width="60" height="60" viewBox="0 0 60 60">
                                    <circle cx="30" cy="30" r="25" fill="#4a7c4a" opacity="0.1"/>
                                    <circle cx="30" cy="30" r="20" fill="none" stroke="#4a7c4a" stroke-width="3"/>
                                    <path d="M20 30 L27 37 L40 24" stroke="#4a7c4a" stroke-width="3" fill="none"/>
                                </svg>
                            </div>
                            <h3>۱۰۰٪ ارگانیک</h3>
                            <p>محصولات ارگانیک تأیید شده، بدون استفاده از سموم مضر. خالص، طبیعی و سالم برای شما و خانواده.</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Products Section -->
        <section id="products" class="page-section">
            <div class="main-content">
                <div class="section">
                    <h2>محصولات تازه ما</h2>
                    <div class="products-grid">
                        <div class="product-card" onclick="showProduct('apple')">
                            <div class="product-image">
                                <svg width="80" height="80" viewBox="0 0 80 80">
                                    <circle cx="40" cy="45" r="30" fill="#ff6b6b"/>
                                    <path d="M40 15 Q47 20 40 35 Q33 20 40 15" fill="#4a7c4a"/>
                                    <ellipse cx="35" cy="40" rx="4" ry="6" fill="#ff9999" opacity="0.6"/>
                                    <ellipse cx="45" cy="35" rx="3" ry="4" fill="#ff9999" opacity="0.4"/>
                                </svg>
                            </div>
                            <div class="product-info">
                                <div class="product-name">سیب تازه</div>
                                <div class="product-description">سیب‌های ارگانیک ترد و شیرین، عالی برای میان‌وعده یا پخت</div>
                                <div class="product-price">
                                    <input type="number" class="price-input" id="apple-price" placeholder="0" step="1000"> تومان/کیلو
                                </div>
                                <button class="view-product-btn">مشاهده جزئیات</button>
                            </div>
                        </div>

                        <div class="product-card" onclick="showProduct('banana')">
                            <div class="product-image">
                                <svg width="80" height="80" viewBox="0 0 80 80">
                                    <path d="M20 55 Q30 25 50 35 Q45 50 35 60 Q20 65 20 55" fill="#ffd93d"/>
                                    <path d="M25 50 Q35 35 45 40" stroke="#f4c430" stroke-width="2" fill="none"/>
                                    <ellipse cx="30" cy="45" rx="2" ry="4" fill="#f4c430" opacity="0.6"/>
                                </svg>
                            </div>
                            <div class="product-info">
                                <div class="product-name">موز ارگانیک</div>
                                <div class="product-description">موزهای شیرین و رسیده، سرشار از پتاسیم و انرژی طبیعی</div>
                                <div class="product-price">
                                    <input type="number" class="price-input" id="banana-price" placeholder="0" step="1000"> تومان/دست
                                </div>
                                <button class="view-product-btn">مشاهده جزئیات</button>
                            </div>
                        </div>

                        <div class="product-card" onclick="showProduct('orange')">
                            <div class="product-image">
                                <svg width="80" height="80" viewBox="0 0 80 80">
                                    <circle cx="40" cy="40" r="28" fill="#ff8c42"/>
                                    <circle cx="32" cy="32" r="4" fill="#ffb366" opacity="0.8"/>
                                    <circle cx="48" cy="28" r="3" fill="#ffb366" opacity="0.6"/>
                                    <circle cx="28" cy="48" r="3" fill="#ffb366" opacity="0.7"/>
                                    <circle cx="52" cy="45" r="2" fill="#ffb366" opacity="0.5"/>
                                </svg>
                            </div>
                            <div class="product-info">
                                <div class="product-name">پرتقال آبدار</div>
                                <div class="product-description">پرتقال‌های غنی از ویتامین C، عالی برای آب‌میوه تازه</div>
                                <div class="product-price">
                                    <input type="number" class="price-input" id="orange-price" placeholder="0" step="1000"> تومان/کیلو
                                </div>
                                <button class="view-product-btn">مشاهده جزئیات</button>
                            </div>
                        </div>

                        <div class="product-card" onclick="showProduct('grape')">
                            <div class="product-image">
                                <svg width="80" height="80" viewBox="0 0 80 80">
                                    <circle cx="40" cy="20" r="6" fill="#8e44ad"/>
                                    <circle cx="32" cy="28" r="6" fill="#8e44ad"/>
                                    <circle cx="48" cy="28" r="6" fill="#8e44ad"/>
                                    <circle cx="40" cy="36" r="6" fill="#8e44ad"/>
                                    <circle cx="32" cy="44" r="6" fill="#8e44ad"/>
                                    <circle cx="48" cy="44" r="6" fill="#8e44ad"/>
                                    <circle cx="40" cy="52" r="6" fill="#8e44ad"/>
                                    <path d="M40 10 Q42 8 40 12" stroke="#4a7c4a" stroke-width="2" fill="none"/>
                                </svg>
                            </div>
                            <div class="product-info">
                                <div class="product-name">انگور بنفش</div>
                                <div class="product-description">انگورهای شیرین بدون هسته، سرشار از آنتی‌اکسیدان</div>
                                <div class="product-price">
                                    <input type="number" class="price-input" id="grape-price" placeholder="0" step="1000"> تومان/کیلو
                                </div>
                                <button class="view-product-btn">مشاهده جزئیات</button>
                            </div>
                        </div>

                        <div class="product-card" onclick="showProduct('strawberry')">
                            <div class="product-image">
                                <svg width="80" height="80" viewBox="0 0 80 80">
                                    <circle cx="40" cy="45" r="25" fill="#ff69b4"/>
                                    <circle cx="35" cy="40" r="2" fill="#ff1493" opacity="0.8"/>
                                    <circle cx="45" cy="38" r="1.5" fill="#ff1493" opacity="0.6"/>
                                    <circle cx="32" cy="50" r="1.5" fill="#ff1493" opacity="0.7"/>
                                    <circle cx="48" cy="48" r="1" fill="#ff1493" opacity="0.5"/>
                                    <path d="M40 20 Q45 25 40 35 Q35 25 40 20" fill="#4a7c4a"/>
                                </svg>
                            </div>
                            <div class="product-info">
                                <div class="product-name">توت‌فرنگی تازه</div>
                                <div class="product-description">توت‌فرنگی‌های شیرین و آبدار، عالی برای دسر یا میان‌وعده</div>
                                <div class="product-price">
                                    <input type="number" class="price-input" id="strawberry-price" placeholder="0" step="1000"> تومان/بسته
                                </div>
                                <button class="view-product-btn">مشاهده جزئیات</button>
                            </div>
                        </div>

                        <div class="product-card" onclick="showProduct('avocado')">
                            <div class="product-image">
                                <svg width="80" height="80" viewBox="0 0 80 80">
                                    <ellipse cx="40" cy="45" rx="22" ry="28" fill="#32cd32"/>
                                    <path d="M40 18 Q45 23 40 33 Q35 23 40 18" fill="#228b22"/>
                                    <ellipse cx="35" cy="40" rx="3" ry="5" fill="#90ee90" opacity="0.6"/>
                                    <ellipse cx="45" cy="50" rx="2" ry="4" fill="#90ee90" opacity="0.4"/>
                                </svg>
                            </div>
                            <div class="product-info">
                                <div class="product-name">آووکادو رسیده</div>
                                <div class="product-description">آووکادوهای کرمی و مغذی، عالی برای سالاد و نان</div>
                                <div class="product-price">
                                    <input type="number" class="price-input" id="avocado-price" placeholder="0" step="1000"> تومان/عدد
                                </div>
                                <button class="view-product-btn">مشاهده جزئیات</button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Individual Product Pages -->
        <section id="product-apple" class="page-section">
            <div class="main-content">
                <div class="product-page">
                    <button class="back-btn" onclick="showSection('products')">← بازگشت به محصولات</button>
                    <div class="product-detail">
                        <div class="product-detail-image">
                            <svg width="200" height="200" viewBox="0 0 200 200">
                                <circle cx="100" cy="110" r="75" fill="#ff6b6b"/>
                                <path d="M100 35 Q115 45 100 85 Q85 45 100 35" fill="#4a7c4a"/>
                                <ellipse cx="85" cy="95" rx="8" ry="12" fill="#ff9999" opacity="0.6"/>
                                <ellipse cx="115" cy="85" rx="6" ry="8" fill="#ff9999" opacity="0.4"/>
                            </svg>
                        </div>
                        <div class="product-detail-info">
                            <h1>سیب تازه</h1>
                            <p>سیب‌های ارگانیک ما از بهترین باغ‌های منطقه تهیه می‌شوند. این سیب‌ها دارای طعمی ترد و شیرین هستند و سرشار از ویتامین‌ها و فیبر طبیعی می‌باشند.</p>
                            <p><strong>ویژگی‌ها:</strong></p>
                            <ul>
                                <li>۱۰۰٪ ارگانیک و طبیعی</li>
                                <li>غنی از ویتامین C و فیبر</li>
                                <li>بافت ترد و طعم شیرین</li>
                                <li>مناسب برای تمام سنین</li>
                                <li>قابل نگهداری تا ۲ هفته در یخچال</li>
                            </ul>
                        </div>
                    </div>
                    <div class="price-section">
                        <h3>تنظیم قیمت</h3>
                        <input type="number" class="price-input" id="apple-detail-price" placeholder="قیمت را وارد کنید" step="1000" onchange="updatePrice('apple', this.value)">
                        <div class="price-display" id="apple-display">قیمت: <span id="apple-price-text">تعیین نشده</span> تومان/کیلو</div>
                    </div>
                </div>
            </div>
        </section>

        <section id="product-banana" class="page-section">
            <div class="main-content">
                <div class="product-page">
                    <button class="back-btn" onclick="showSection('products')">← بازگشت به محصولات</button>
                    <div class="product-detail">
                        <div class="product-detail-image">
                            <svg width="200" height="200" viewBox="0 0 200 200">
                                <path d="M50 135 Q75 65 125 85 Q115 125 85 150 Q50 160 50 135" fill="#ffd93d"/>
                                <path d="M60 125 Q85 85 115 100" stroke="#f4c430" stroke-width="4" fill="none"/>
                                <ellipse cx="75" cy="115" rx="4" ry="8" fill="#f4c430" opacity="0.6"/>
                            </svg>
                        </div>
                        <div class="product-detail-info">
                            <h1>موز ارگانیک</h1>
                            <p>موزهای ارگانیک ما از مناطق گرمسیری تهیه شده و دارای بالاترین کیفیت هستند. این موزها سرشار از پتاسیم، ویتامین B6 و انرژی طبیعی می‌باشند.</p>
                            <p><strong>ویژگی‌ها:</strong></p>
                            <ul>
                                <li>سرشار از پتاسیم و ویتامین B6</li>
                                <li>منبع عالی انرژی طبیعی</li>
                                <li>مناسب برای ورزشکاران</li>
                                <li>کمک به تقویت سیستم ایمنی</li>
                                <li>طعم شیرین و بافت نرم</li>
                            </ul>
                        </div>
                    </div>
                    <div class="price-section">
                        <h3>تنظیم قیمت</h3>
                        <input type="number" class="price-input" id="banana-detail-price" placeholder="قیمت را وارد کنید" step="1000" onchange="updatePrice('banana', this.value)">
                        <div class="price-display" id="banana-display">قیمت: <span id="banana-price-text">تعیین نشده</span> تومان/دست</div>
                    </div>
                </div>
            </div>
        </section>

        <section id="product-orange" class="page-section">
            <div class="main-content">
                <div class="product-page">
                    <button class="back-btn" onclick="showSection('products')">← بازگشت به محصولات</button>
                    <div class="product-detail">
                        <div class="product-detail-image">
                            <svg width="200" height="200" viewBox="0 0 200 200">
                                <circle cx="100" cy="100" r="70" fill="#ff8c42"/>
                                <circle cx="80" cy="80" r="8" fill="#ffb366" opacity="0.8"/>
                                <circle cx="120" cy="70" r="6" fill="#ffb366" opacity="0.6"/>
                                <circle cx="70" cy="120" r="6" fill="#ffb366" opacity="0.7"/>
                                <circle cx="130" cy="115" r="4" fill="#ffb366" opacity="0.5"/>
                            </svg>
                        </div>
                        <div class="product-detail-info">
                            <h1>پرتقال آبدار</h1>
                            <p>پرتقال‌های تازه و آبدار ما سرشار از ویتامین C و طعمی فوق‌العاده شیرین و ترش دارند. این پرتقال‌ها برای تهیه آب‌میوه طبیعی یا مصرف مستقیم عالی هستند.</p>
                            <p><strong>ویژگی‌ها:</strong></p>
                            <ul>
                                <li>غنی از ویتامین C و آنتی‌اکسیدان</li>
                                <li>تقویت کننده سیستم ایمنی</li>
                                <li>آبدار و طعم عالی</li>
                                <li>مناسب برای آب‌گیری</li>
                                <li>تازه و بدون مواد نگهدارنده</li>
                            </ul>
                        </div>
                    </div>
                    <div class="price-section">
                        <h3>تنظیم قیمت</h3>
                        <input type="number" class="price-input" id="orange-detail-price" placeholder="قیمت را وارد کنید" step="1000" onchange="updatePrice('orange', this.value)">
                        <div class="price-display" id="orange-display">قیمت: <span id="orange-price-text">تعیین نشده</span> تومان/کیلو</div>
                    </div>
                </div>
            </div>
        </section>

        <section id="product-grape" class="page-section">
            <div class="main-content">
                <div class="product-page">
                    <button class="back-btn" onclick="showSection('products')">← بازگشت به محصولات</button>
                    <div class="product-detail">
                        <div class="product-detail-image">
                            <svg width="200" height="200" viewBox="0 0 200 200">
                                <circle cx="100" cy="50" r="15" fill="#8e44ad"/>
                                <circle cx="80" cy="70" r="15" fill="#8e44ad"/>
                                <circle cx="120" cy="70" r="15" fill="#8e44ad"/>
                                <circle cx="100" cy="90" r="15" fill="#8e44ad"/>
                                <circle cx="80" cy="110" r="15" fill="#8e44ad"/>
                                <circle cx="120" cy="110" r="15" fill="#8e44ad"/>
                                <circle cx="100" cy="130" r="15" fill="#8e44ad"/>
                                <path d="M100 25 Q105 20 100 30" stroke="#4a7c4a" stroke-width="4" fill="none"/>
                            </svg>
                        </div>
                        <div class="product-detail-info">
                            <h1>انگور بنفش</h1>
                            <p>انگورهای بنفش ما بدون هسته و دارای طعمی فوق‌العاده شیرین هستند. این انگورها سرشار از آنتی‌اکسیدان‌های مفید برای سلامتی قلب و عروق می‌باشند.</p>
                            <p><strong>ویژگی‌ها:</strong></p>
                            <ul>
                                <li>بدون هسته و طعم شیرین</li>
                                <li>سرشار از آنتی‌اکسیدان</li>
                                <li>مفید برای سلامت قلب</li>
                                <li>حاوی ویتامین K و C</li>
                                <li>مناسب برای تمام اعضای خانواده</li>
                            </ul>
                        </div>
                    </div>
                    <div class="price-section">
                        <h3>تنظیم قیمت</h3>
                        <input type="number" class="price-input" id="grape-detail-price" placeholder="قیمت را وارد کنید" step="1000" onchange="updatePrice('grape', this.value)">
                        <div class="price-display" id="grape-display">قیمت: <span id="grape-price-text">تعیین نشده</span> تومان/کیلو</div>
                    </div>
                </div>
            </div>
        </section>

        <section id="product-strawberry" class="page-section">
            <div class="main-content">
                <div class="product-page">
                    <button class="back-btn" onclick="showSection('products')">← بازگشت به محصولات</button>
                    <div class="product-detail">
                        <div class="product-detail-image">
                            <svg width="200" height="200" viewBox="0 0 200 200">
                                <circle cx="100" cy="115" r="60" fill="#ff69b4"/>
                                <circle cx="85" cy="100" r="4" fill="#ff1493" opacity="0.8"/>
                                <circle cx="115" cy="95" r="3" fill="#ff1493" opacity="0.6"/>
                                <circle cx="80" cy="125" r="3" fill="#ff1493" opacity="0.7"/>
                                <circle cx="120" cy="120" r="2" fill="#ff1493" opacity="0.5"/>
                                <path d="M100 50 Q115 60 100 85 Q85 60 100 50" fill="#4a7c4a"/>
                            </svg>
                        </div>
                        <div class="product-detail-info">
                            <h1>توت‌فرنگی تازه</h1>
                            <p>توت‌فرنگی‌های تازه و آبدار ما از بهترین مزارع منطقه تهیه می‌شوند. این میوه‌های قرمز زیبا سرشار از ویتامین C و طعمی شیرین و خوشمزه دارند.</p>
                            <p><strong>ویژگی‌ها:</strong></p>
                            <ul>
                                <li>سرشار از ویتامین C و فولات</li>
                                <li>آنتی‌اکسیدان‌های قوی</li>
                                <li>کم کالری و مغذی</li>
                                <li>مناسب برای دسر و اسموتی</li>
                                <li>تازه و بدون مواد شیمیایی</li>
                            </ul>
                        </div>
                    </div>
                    <div class="price-section">
                        <h3>تنظیم قیمت</h3>
                        <input type="number" class="price-input" id="strawberry-detail-price" placeholder="قیمت را وارد کنید" step="1000" onchange="updatePrice('strawberry', this.value)">
                        <div class="price-display" id="strawberry-display">قیمت: <span id="strawberry-price-text">تعیین نشده</span> تومان/بسته</div>
                    </div>
                </div>
            </div>
        </section>

        <section id="product-avocado" class="page-section">
            <div class="main-content">
                <div class="product-page">
                    <button class="back-btn" onclick="showSection('products')">← بازگشت به محصولات</button>
                    <div class="product-detail">
                        <div class="product-detail-image">
                            <svg width="200" height="200" viewBox="0 0 200 200">
                                <ellipse cx="100" cy="115" rx="55" ry="70" fill="#32cd32"/>
                                <path d="M100 45 Q115 55 100 80 Q85 55 100 45" fill="#228b22"/>
                                <ellipse cx="85" cy="100" rx="6" ry="10" fill="#90ee90" opacity="0.6"/>
                                <ellipse cx="115" cy="125" rx="4" ry="8" fill="#90ee90" opacity="0.4"/>
                            </svg>
                        </div>
                        <div class="product-detail-info">
                            <h1>آووکادو رسیده</h1>
                            <p>آووکادوهای رسیده و کرمی ما سرشار از چربی‌های مفید و ویتامین‌های ضروری هستند. این میوه‌های مغذی برای سلامت قلب و مغز بسیار مفید می‌باشند.</p>
                            <p><strong>ویژگی‌ها:</strong></p>
                            <ul>
                                <li>سرشار از چربی‌های مفید امگا ۳</li>
                                <li>غنی از ویتامین K، E و فولات</li>
                                <li>مفید برای سلامت قلب</li>
                                <li>بافت کرمی و طعم ملایم</li>
                                <li>مناسب برای رژیم‌های سالم</li>
                            </ul>
                        </div>
                    </div>
                    <div class="price-section">
                        <h3>تنظیم قیمت</h3>
                        <input type="number" class="price-input" id="avocado-detail-price" placeholder="قیمت را وارد کنید" step="1000" onchange="updatePrice('avocado', this.value)">
                        <div class="price-display" id="avocado-display">قیمت: <span id="avocado-price-text">تعیین نشده</span> تومان/عدد</div>
                    </div>
                </div>
            </div>
        </section>

        <!-- About Section -->
        <section id="about" class="page-section">
            <div class="main-content">
                <div class="section">
                    <h2>درباره بازار میوه‌های تازه</h2>
                    <div class="about-content">
                        <div class="about-text">
                            <p>بیش از ۲۰ سال است که بازار میوه‌های تازه منبع مورد اعتماد شما برای میوه‌های ارگانیک درجه یک محسوب می‌شود. ما مستقیماً با کشاورزان محلی همکاری می‌کنیم که متعهد به کشاورزی پایدار و کیفیت استثنایی هستند.</p>
                            
                            <p>ماموریت ما ساده است: ارائه تازه‌ترین و خوشمزه‌ترین میوه‌ها به شما، در عین حمایت از جوامع محلی و پایداری زیست‌محیطی. هر قطعه میوه با دقت انتخاب می‌شود تا فقط بهترین محصولات طبیعت را دریافت کنید.</p>
                            
                            <p>از خانواده ما به خانواده شما، ما متعهد به ارائه گزینه‌های سالم و مغذی هستیم که طعمی فوق‌العاده دارند و از سلامتی شما حمایت می‌کنند. امروز از ما دیدن کنید و تفاوت کیفیت را بچشید!</p>
                        </div>
                        <div class="about-image">
                            <svg width="300" height="200" viewBox="0 0 300 200">
                                <!-- Farm scene -->
                                <rect x="0" y="150" width="300" height="50" fill="#90EE90"/>
                                <rect x="50" y="100" width="200" height="50" fill="#8B4513"/>
                                <rect x="60" y="80" width="20" height="70" fill="#654321"/>
                                <rect x="220" y="80" width="20" height="70" fill="#654321"/>
                                <polygon points="50,100 150,50 250,100" fill="#DC143C"/>
                                <rect x="140" y="120" width="20" height="30" fill="#8B4513"/>
                                <circle cx="120" cy="130" r="8" fill="#FFD700"/>
                                <circle cx="180" cy="125" r="8" fill="#FF6347"/>
                                <!-- Sun -->
                                <circle cx="250" cy="50" r="20" fill="#FFD700"/>
                                <!-- Trees -->
                                <circle cx="30" cy="120" r="25" fill="#228B22"/>
                                <rect x="27" y="140" width="6" height="20" fill="#8B4513"/>
                                <circle cx="270" cy="130" r="20" fill="#228B22"/>
                                <rect x="267" y="145" width="6" height="15" fill="#8B4513"/>
                            </svg>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Contact Section -->
        <section id="contact" class="page-section">
            <div class="main-content">
                <div class="section">
                    <h2>از فروشگاه ما دیدن کنید</h2>
                    <div class="contact-info">
                        <div class="contact-card">
                            <div class="contact-icon">
                                <svg width="50" height="50" viewBox="0 0 50 50">
                                    <circle cx="25" cy="25" r="20" fill="#4a7c4a" opacity="0.1"/>
                                    <path d="M25 10C19.5 10 15 14.5 15 20c0 7.5 10 20 10 20s10-12.5 10-20c0-5.5-4.5-10-10-10zm0 13c-1.7 0-3-1.3-3-3s1.3-3 3-3 3 1.3 3 3-1.3 3-3 3z" fill="#4a7c4a"/>
                                </svg>
                            </div>
                            <h3>آدرس</h3>
                            <p>خیابان باغ شماره ۱۲۳<br>دره تازه، تهران</p>
                        </div>
                        
                        <div class="contact-card">
                            <div class="contact-icon">
                                <svg width="50" height="50" viewBox="0 0 50 50">
                                    <circle cx="25" cy="25" r="20" fill="#4a7c4a" opacity="0.1"/>
                                    <path d="M15 18c0-1.1.9-2 2-2h14c1.1 0 2 .9 2 2v14c0 1.1-.9 2-2 2H17c-1.1 0-2-.9-2-2V18zm2 0v14h14V18H17zm7 7l-7-5v2l7 5 7-5v-2l-7 5z" fill="#4a7c4a"/>
                                </svg>
                            </div>
                            <h3>تماس</h3>
                            <p>تلفن: ۰۲۱-۱۲۳-میوه<br>ایمیل: hello@freshgarden.ir</p>
                        </div>
                        
                        <div class="contact-card">
                            <div class="contact-icon">
                                <svg width="50" height="50" viewBox="0 0 50 50">
                                    <circle cx="25" cy="25" r="20" fill="#4a7c4a" opacity="0.1"/>
                                    <circle cx="25" cy="25" r="15" fill="none" stroke="#4a7c4a" stroke-width="2"/>
                                    <path d="M25 15v10l7 4" stroke="#4a7c4a" stroke-width="2" fill="none"/>
                                </svg>
                            </div>
                            <h3>ساعات کاری</h3>
                            <p>شنبه تا پنج‌شنبه: ۸ تا ۲۰<br>جمعه: ۹ تا ۱۸</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>
    </div>

    <!-- Footer -->
    <footer class="footer">
        <div class="footer-content">
            <h3>بازار میوه‌های تازه</h3>
            <p>منبع مورد اعتماد شما برای میوه‌های ارگانیک درجه یک از سال ۱۳۸۲</p>
            
            <div class="social-links">
                <a href="#" class="social-link">
                    <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                        <path d="M24 4.557c-.883.392-1.832.656-2.828.775 1.017-.609 1.798-1.574 2.165-2.724-.951.564-2.005.974-3.127 1.195-.897-.957-2.178-1.555-3.594-1.555-3.179 0-5.515 2.966-4.797 6.045-4.091-.205-7.719-2.165-10.148-5.144-1.29 2.213-.669 5.108 1.523 6.574-.806-.026-1.566-.247-2.229-.616-.054 2.281 1.581 4.415 3.949 4.89-.693.188-1.452.232-2.224.084.626 1.956 2.444 3.379 4.6 3.419-2.07 1.623-4.678 2.348-7.29 2.04 2.179 1.397 4.768 2.212 7.548 2.212 9.142 0 14.307-7.721 13.995-14.646.962-.695 1.797-1.562 2.457-2.549z"/>
                    </svg>
                </a>
                <a href="#" class="social-link">
                    <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                        <path d="M22.46 6c-.77.35-1.6.58-2.46.69.88-.53 1.56-1.37 1.88-2.38-.83.5-1.75.85-2.72 1.05C18.37 4.5 17.26 4 16 4c-2.35 0-4.27 1.92-4.27 4.29 0 .34.04.67.11.98C8.28 9.09 5.11 7.38 3 4.79c-.37.63-.58 1.37-.58 2.15 0 1.49.75 2.81 1.91 3.56-.71 0-1.37-.2-1.95-.5v.03c0 2.08 1.48 3.82 3.44 4.21a4.22 4.22 0 0 1-1.93.07 4.28 4.28 0 0 0 4 2.98 8.521 8.521 0 0 1-5.33 1.84c-.34 0-.68-.02-1.02-.06C3.44 20.29 5.7 21 8.12 21 16 21 20.33 14.46 20.33 8.79c0-.19 0-.37-.01-.56.84-.6 1.56-1.36 2.14-2.23z"/>
                    </svg>
                </a>
                <a href="#" class="social-link">
                    <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                        <path d="M12.017 0C5.396 0 .029 5.367.029 11.987c0 5.079 3.158 9.417 7.618 11.174-.105-.949-.199-2.403.041-3.439.219-.937 1.406-5.957 1.406-5.957s-.359-.72-.359-1.781c0-1.663.967-2.911 2.168-2.911 1.024 0 1.518.769 1.518 1.688 0 1.029-.653 2.567-.992 3.992-.285 1.193.6 2.165 1.775 2.165 2.128 0 3.768-2.245 3.768-5.487 0-2.861-2.063-4.869-5.008-4.869-3.41 0-5.409 2.562-5.409 5.199 0 1.033.394 2.143.889 2.741.099.12.112.225.085.345-.09.375-.293 1.199-.334 1.363-.053.225-.172.271-.402.165-1.495-.69-2.433-2.878-2.433-4.646 0-3.776 2.748-7.252 7.92-7.252 4.158 0 7.392 2.967 7.392 6.923 0 4.135-2.607 7.462-6.233 7.462-1.214 0-2.357-.629-2.75-1.378l-.748 2.853c-.271 1.043-1.002 2.35-1.492 3.146C9.57 23.812 10.763 24.009 12.017 24.009c6.624 0 11.99-5.367 11.99-11.988C24.007 5.367 18.641.001 12.017.001z"/>
                    </svg>
                </a>
            </div>
            
            <p>&copy; ۱۴۰۳ بازار میوه‌های تازه. تمامی حقوق محفوظ است. | بهترین‌های طبیعت از سال ۱۳۸۲</p>
        </div>
    </footer>

    <script>
        // Store prices in localStorage
        const prices = JSON.parse(localStorage.getItem('fruitPrices')) || {};

        // Show specific section
        function showSection(sectionId) {
            // Hide all sections
            document.querySelectorAll('.page-section').forEach(section => {
                section.classList.remove('active');
            });
            
            // Show target section
            const targetSection = document.getElementById(sectionId);
            if (targetSection) {
                targetSection.classList.add('active');
                
                // Scroll to top
                window.scrollTo({ top: 0, behavior: 'smooth' });
                
                // Load prices if on products section
                if (sectionId === 'products') {
                    loadPrices();
                }
            }
        }

        // Show individual product page
        function showProduct(productId) {
            showSection(`product-${productId}`);
            
            // Load price for this specific product
            const savedPrice = prices[productId];
            if (savedPrice) {
                document.getElementById(`${productId}-detail-price`).value = savedPrice;
                document.getElementById(`${productId}-price-text`).textContent = parseInt(savedPrice).toLocaleString('fa-IR');
            }
        }

        // Update price
        function updatePrice(productId, price) {
            if (price && price > 0) {
                prices[productId] = price;
                localStorage.setItem('fruitPrices', JSON.stringify(prices));
                
                // Update display
                const priceText = parseInt(price).toLocaleString('fa-IR');
                document.getElementById(`${productId}-price-text`).textContent = priceText;
                
                // Update main products page price
                const mainPriceInput = document.getElementById(`${productId}-price`);
                if (mainPriceInput) {
                    mainPriceInput.value = price;
                }
            }
        }

        // Load saved prices
        function loadPrices() {
            Object.keys(prices).forEach(productId => {
                const price = prices[productId];
                const input = document.getElementById(`${productId}-price`);
                if (input && price) {
                    input.value = price;
                }
            });
        }

        // Sync prices between main page and detail pages
        document.querySelectorAll('.price-input').forEach(input => {
            input.addEventListener('change', function() {
                const productId = this.id.replace('-price', '').replace('-detail', '');
                const price = this.value;
                
                if (price && price > 0) {
                    updatePrice(productId, price);
                }
            });
        });

        // Initialize page
        document.addEventListener('DOMContentLoaded', function() {
            // Load saved prices
            loadPrices();
            
            // Add fade-in animation to elements
            const observerOptions = {
                threshold: 0.1,
                rootMargin: '0px 0px -50px 0px'
            };

            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.classList.add('visible');
                    }
                });
            }, observerOptions);

            document.querySelectorAll('.fade-in').forEach(element => {
                observer.observe(element);
            });

            // Add hover effects to product cards
            document.querySelectorAll('.product-card').forEach(card => {
                card.addEventListener('mouseenter', function() {
                    this.style.transform = 'translateY(-8px) scale(1.02)';
                });
                
                card.addEventListener('mouseleave', function() {
                    this.style.transform = 'translateY(0) scale(1)';
                });
            });

            // Header background change on scroll
            window.addEventListener('scroll', function() {
                const header = document.querySelector('.header');
                if (window.scrollY > 100) {
                    header.style.background = 'rgba(45, 90, 45, 0.95)';
                    header.style.backdropFilter = 'blur(10px)';
                } else {
                    header.style.background = 'linear-gradient(135deg, #2d5a2d 0%, #4a7c4a 100%)';
                    header.style.backdropFilter = 'none';
                }
            });

            // Initialize visible elements
            setTimeout(() => {
                document.querySelectorAll('.fade-in').forEach(element => {
                    const rect = element.getBoundingClientRect();
                    if (rect.top < window.innerHeight && rect.bottom > 0) {
                        element.classList.add('visible');
                    }
                });
            }, 100);
        });

        // Format numbers in Persian
        function formatPersianNumber(num) {
            return parseInt(num).toLocaleString('fa-IR');
        }

        // Add Persian number formatting to inputs
        document.querySelectorAll('.price-input').forEach(input => {
            input.addEventListener('blur', function() {
                if (this.value) {
                    const formatted = formatPersianNumber(this.value);
                    // Keep the actual value but show formatted in display
                }
            });
        });
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'986a18f4d60cd3a9',t:'MTc1OTEzNDQwNi4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
