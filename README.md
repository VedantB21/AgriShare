<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AgriShare - Modern Farming, Shared Together</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            overflow-x: hidden;
        }

        /* Header & Navigation */
        .navbar {
            position: fixed;
            top: 0;
            width: 100%;
            background: linear-gradient(135deg, #2e7d32, #4caf50);
            backdrop-filter: blur(10px);
            padding: 1rem 2rem;
            z-index: 1000;
            transition: all 0.3s ease;
        }

        .nav-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 1200px;
            margin: 0 auto;
        }

        .logo {
            font-size: 2rem;
            font-weight: bold;
            color: white;
            text-decoration: none;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .logo::before {
            content: "🌾";
            font-size: 2rem;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .nav-links a {
            color: white;
            text-decoration: none;
            transition: color 0.3s ease;
            font-weight: 500;
        }

        .nav-links a:hover {
            color: #c8e6c9;
        }

        .mobile-menu {
            display: none;
            background: none;
            border: none;
            color: white;
            font-size: 1.5rem;
            cursor: pointer;
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            background: linear-gradient(135deg, #1b5e20, #2e7d32, #4caf50);
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><circle cx="50" cy="50" r="2" fill="rgba(255,255,255,0.1)"/></svg>') repeat;
            animation: float 20s infinite linear;
        }

        @keyframes float {
            0% { transform: translateY(100vh) rotate(0deg); }
            100% { transform: translateY(-100vh) rotate(360deg); }
        }

        .hero-content {
            z-index: 2;
            max-width: 800px;
            padding: 2rem;
            animation: fadeInUp 1s ease;
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

        .hero h1 {
            font-size: 3.5rem;
            color: white;
            margin-bottom: 1rem;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .hero p {
            font-size: 1.3rem;
            color: #c8e6c9;
            margin-bottom: 2rem;
        }

        .cta-buttons {
            display: flex;
            gap: 1rem;
            justify-content: center;
            flex-wrap: wrap;
        }

        .btn {
            padding: 1rem 2rem;
            border: none;
            border-radius: 50px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
            display: inline-block;
        }

        .btn-primary {
            background: linear-gradient(45deg, #ff9800, #f57c00);
            color: white;
            box-shadow: 0 4px 15px rgba(255, 152, 0, 0.3);
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(255, 152, 0, 0.4);
        }

        .btn-secondary {
            background: transparent;
            color: white;
            border: 2px solid white;
        }

        .btn-secondary:hover {
            background: white;
            color: #2e7d32;
            transform: translateY(-2px);
        }

        /* Tractor Animation */
        .tractor-animation {
            position: absolute;
            bottom: 10%;
            left: -10%;
            font-size: 3rem;
            animation: moveTractor 15s infinite linear;
        }

        @keyframes moveTractor {
            0% { left: -10%; }
            100% { left: 110%; }
        }

        /* Section Styles */
        .section {
            padding: 5rem 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .section-title {
            text-align: center;
            font-size: 2.5rem;
            margin-bottom: 3rem;
            color: #2e7d32;
            position: relative;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 60px;
            height: 4px;
            background: linear-gradient(45deg, #4caf50, #8bc34a);
            border-radius: 2px;
        }

        /* How It Works */
        .process-steps {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .step {
            background: white;
            padding: 2rem;
            border-radius: 15px;
            text-align: center;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .step::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: linear-gradient(45deg, #4caf50, #8bc34a);
        }

        .step:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0,0,0,0.15);
        }

        .step-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
            display: block;
        }

        .step h3 {
            color: #2e7d32;
            margin-bottom: 1rem;
            font-size: 1.3rem;
        }

        /* Equipment Catalog */
        .equipment-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .equipment-card {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
        }

        .equipment-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0,0,0,0.15);
        }

        .equipment-header {
            background: linear-gradient(135deg, #4caf50, #8bc34a);
            padding: 1.5rem;
            text-align: center;
        }

        .equipment-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
        }

        .equipment-header h3 {
            color: white;
            font-size: 1.5rem;
        }

        .equipment-body {
            padding: 2rem;
        }

        .price-info {
            background: #f5f5f5;
            padding: 1rem;
            border-radius: 10px;
            margin: 1rem 0;
        }

        .savings-badge {
            background: linear-gradient(45deg, #ff9800, #f57c00);
            color: white;
            padding: 0.5rem 1rem;
            border-radius: 20px;
            font-size: 0.9rem;
            font-weight: bold;
            display: inline-block;
            margin-top: 1rem;
        }

        /* Testimonials */
        .testimonials {
            background: linear-gradient(135deg, #f1f8e9, #c8e6c9);
            margin: 3rem -2rem;
            padding: 5rem 2rem;
        }

        .testimonial-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .testimonial {
            background: white;
            padding: 2rem;
            border-radius: 15px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
            position: relative;
        }

        .testimonial::before {
            content: '"';
            font-size: 4rem;
            color: #4caf50;
            position: absolute;
            top: -10px;
            left: 20px;
            font-family: serif;
        }

        .farmer-info {
            display: flex;
            align-items: center;
            gap: 1rem;
            margin-top: 1rem;
        }

        .farmer-avatar {
            width: 60px;
            height: 60px;
            background: linear-gradient(45deg, #4caf50, #8bc34a);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            color: white;
        }

        /* Partners Section */
        .partners-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .partner-card {
            background: white;
            padding: 2rem;
            border-radius: 15px;
            text-align: center;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
        }

        .partner-card:hover {
            transform: translateY(-5px);
        }

        .partner-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
            color: #4caf50;
        }

        /* Dashboard Preview */
        .dashboard-preview {
            background: white;
            border-radius: 15px;
            padding: 2rem;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
            margin-top: 3rem;
        }

        .dashboard-nav {
            display: flex;
            gap: 1rem;
            margin-bottom: 2rem;
            flex-wrap: wrap;
        }

        .dashboard-tab {
            padding: 0.5rem 1rem;
            background: #f5f5f5;
            border: none;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .dashboard-tab.active {
            background: linear-gradient(45deg, #4caf50, #8bc34a);
            color: white;
        }

        .dashboard-content {
            min-height: 300px;
            background: #f9f9f9;
            border-radius: 10px;
            padding: 2rem;
            text-align: center;
        }

        /* Contact Form */
        .contact-form {
            max-width: 600px;
            margin: 0 auto;
            background: white;
            padding: 3rem;
            border-radius: 15px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
        }

        .form-group {
            margin-bottom: 2rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            color: #2e7d32;
            font-weight: bold;
        }

        .form-group input,
        .form-group textarea,
        .form-group select {
            width: 100%;
            padding: 1rem;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            font-size: 1rem;
            transition: border-color 0.3s ease;
        }

        .form-group input:focus,
        .form-group textarea:focus,
        .form-group select:focus {
            outline: none;
            border-color: #4caf50;
        }

        /* Footer */
        .footer {
            background: linear-gradient(135deg, #1b5e20, #2e7d32);
            color: white;
            padding: 3rem 2rem 1rem;
            text-align: center;
        }

        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin-bottom: 2rem;
        }

        .footer-section h3 {
            margin-bottom: 1rem;
            color: #c8e6c9;
        }

        .footer-section a {
            color: white;
            text-decoration: none;
            display: block;
            margin-bottom: 0.5rem;
            transition: color 0.3s ease;
        }

        .footer-section a:hover {
            color: #c8e6c9;
        }

        .language-selector {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: linear-gradient(45deg, #4caf50, #8bc34a);
            color: white;
            border: none;
            padding: 1rem;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(76, 175, 80, 0.3);
            transition: all 0.3s ease;
            z-index: 1000;
        }

        .language-selector:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(76, 175, 80, 0.4);
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }
            
            .mobile-menu {
                display: block;
            }

            .hero h1 {
                font-size: 2.5rem;
            }

            .cta-buttons {
                flex-direction: column;
                align-items: center;
            }

            .section {
                padding: 3rem 1rem;
            }
            
            .testimonials {
                margin: 3rem -1rem;
                padding: 3rem 1rem;
            }
        }

        /* Smooth Scrolling Animation */
        .scroll-animation {
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.6s ease;
        }

        .scroll-animation.visible {
            opacity: 1;
            transform: translateY(0);
        }

        /* Loading Animation */
        .loading {
            display: inline-block;
            width: 20px;
            height: 20px;
            border: 2px solid #f3f3f3;
            border-top: 2px solid #4caf50;
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav class="navbar">
        <div class="nav-container">
            <a href="#home" class="logo">AgriShare</a>
            <ul class="nav-links">
                <li><a href="#home">Home</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#how-it-works">How It Works</a></li>
                <li><a href="#equipment">Equipment</a></li>
                <li><a href="#testimonials">Stories</a></li>
                <li><a href="#partners">Partners</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
            <button class="mobile-menu">☰</button>
        </div>
    </nav>

    <!-- Hero Section -->
    <section id="home" class="hero">
        <div class="hero-content">
            <h1>Modern Farming, Shared Together</h1>
            <p>Empowering farmers through collective ownership of agricultural equipment. Share costs, maximize profits, grow together.</p>
            <div class="cta-buttons">
                <a href="#contact" class="btn btn-primary">Join as a Farmer</a>
                <a href="#partners" class="btn btn-secondary">Partner with Us</a>
            </div>
        </div>
        <div class="tractor-animation">🚜</div>
    </section>

    <!-- About Section -->
    <section id="about" class="section scroll-animation">
        <h2 class="section-title">About AgriShare</h2>
        <div style="text-align: center; max-width: 800px; margin: 0 auto;">
            <p style="font-size: 1.2rem; margin-bottom: 2rem; color: #555;">
                AgriShare was born from a simple observation: small farmers struggle with the high cost of modern agricultural equipment, while these same machines often sit idle for most of the year.
            </p>
            <p style="font-size: 1.1rem; margin-bottom: 3rem; color: #666;">
                Our mission is to democratize access to modern farming technology through innovative co-ownership models, enabling farmers to share resources, reduce costs, and increase productivity together.
            </p>
            
            <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 2rem; margin-top: 3rem;">
                <div style="text-align: center;">
                    <div style="font-size: 3rem; margin-bottom: 1rem;">🎯</div>
                    <h3 style="color: #2e7d32; margin-bottom: 1rem;">Mission</h3>
                    <p>Empower small farmers with affordable access to modern equipment</p>
                </div>
                <div style="text-align: center;">
                    <div style="font-size: 3rem; margin-bottom: 1rem;">👁️</div>
                    <h3 style="color: #2e7d32; margin-bottom: 1rem;">Vision</h3>
                    <p>Create a sustainable ecosystem where farmers thrive together</p>
                </div>
                <div style="text-align: center;">
                    <div style="font-size: 3rem; margin-bottom: 1rem;">❤️</div>
                    <h3 style="color: #2e7d32; margin-bottom: 1rem;">Impact</h3>
                    <p>Transform rural livelihoods through collective ownership</p>
                </div>
            </div>
        </div>
    </section>

    <!-- How It Works -->
    <section id="how-it-works" class="section scroll-animation">
        <h2 class="section-title">How It Works</h2>
        <div class="process-steps">
            <div class="step">
                <span class="step-icon">👥</span>
                <h3>Join a Group</h3>
                <p>Register individually or as part of your FPO. Connect with farmers in your area who need similar equipment.</p>
            </div>
            <div class="step">
                <span class="step-icon">🚜</span>
                <h3>Select Equipment</h3>
                <p>Choose from tractors, harvesters, irrigation systems, and more. Browse our catalog of modern agricultural machinery.</p>
            </div>
            <div class="step">
                <span class="step-icon">💰</span>
                <h3>Share Ownership</h3>
                <p>Split the cost among group members. Access government subsidies and financing options for affordable ownership.</p>
            </div>
            <div class="step">
                <span class="step-icon">📅</span>
                <h3>Schedule Usage</h3>
                <p>Use our digital calendar to book equipment when you need it. Fair scheduling ensures everyone gets their turn.</p>
            </div>
            <div class="step">
                <span class="step-icon">🔧</span>
                <h3>Share Maintenance</h3>
                <p>Automated cost-splitting for maintenance and repairs. Get timely service reminders and insurance updates.</p>
            </div>
        </div>
    </section>

    <!-- Equipment Catalog -->
    <section id="equipment" class="section scroll-animation">
        <h2 class="section-title">Equipment Catalog</h2>
        <div class="equipment-grid">
            <div class="equipment-card">
                <div class="equipment-header">
                    <div class="equipment-icon">🚜</div>
                    <h3>Tractor (45 HP)</h3>
                </div>
                <div class="equipment-body">
                    <div class="price-info">
                        <p><strong>Total Price:</strong> ₹8,50,000</p>
                        <p><strong>Per Farmer:</strong> ₹1,70,000 (5 farmers)</p>
                        <p><strong>Monthly Rental Alternative:</strong> ₹15,000</p>
                    </div>
                    <p>Perfect for plowing, tilling, and transport. Suitable for 10-15 acre operations.</p>
                    <span class="savings-badge">Save ₹1,80,000/year vs rental</span>
                </div>
            </div>

            <div class="equipment-card">
                <div class="equipment-header">
                    <div class="equipment-icon">🌾</div>
                    <h3>Combine Harvester</h3>
                </div>
                <div class="equipment-body">
                    <div class="price-info">
                        <p><strong>Total Price:</strong> ₹25,00,000</p>
                        <p><strong>Per Farmer:</strong> ₹2,50,000 (10 farmers)</p>
                        <p><strong>Custom Hiring:</strong> ₹2,500/acre</p>
                    </div>
                    <p>Efficient harvesting for wheat, rice, and other grains. Reduces labor costs significantly.</p>
                    <span class="savings-badge">Save ₹2,00,000/season vs hiring</span>
                </div>
            </div>

            <div class="equipment-card">
                <div class="equipment-header">
                    <div class="equipment-icon">💧</div>
                    <h3>Drip Irrigation System</h3>
                </div>
                <div class="equipment-body">
                    <div class="price-info">
                        <p><strong>Total Price:</strong> ₹3,00,000</p>
                        <p><strong>Per Farmer:</strong> ₹60,000 (5 farmers)</p>
                        <p><strong>Water Savings:</strong> 40-60%</p>
                    </div>
                    <p>Modern irrigation for efficient water usage. Covers 25 acres with smart controllers.</p>
                    <span class="savings-badge">90% Government Subsidy Available</span>
                </div>
            </div>
        </div>
    </section>

    <!-- Dashboard Preview -->
    <section class="section scroll-animation">
        <h2 class="section-title">Farmer Dashboard Preview</h2>
        <div class="dashboard-preview">
            <div class="dashboard-nav">
                <button class="dashboard-tab active" onclick="showDashboard('profile')">My Profile</button>
                <button class="dashboard-tab" onclick="showDashboard('equipment')">Equipment Pool</button>
                <button class="dashboard-tab" onclick="showDashboard('booking')">Book & Schedule</button>
                <button class="dashboard-tab" onclick="showDashboard('payments')">Payments & Wallet</button>
                <button class="dashboard-tab" onclick="showDashboard('maintenance')">Maintenance Alerts</button>
            </div>
            <div class="dashboard-content" id="dashboard-content">
                <div style="text-align: center; padding: 2rem;">
                    <h3 style="color: #2e7d32; margin-bottom: 1rem;">👨‍🌾 Farmer Profile</h3>
                    <p><strong>Name:</strong> Rajesh Kumar</p>
                    <p><strong>Village:</strong> Khandala, Maharashtra</p>
                    <p><strong>Land Size:</strong> 12 acres</p>
                    <p><strong>Crops:</strong> Cotton, Soybean, Wheat</p>
                    <p><strong>Group:</strong> Khandala Farmers Collective (8 members)</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Testimonials -->
    <section id="testimonials" class="testimonials scroll-animation">
        <div style="max-width: 1200px; margin: 0 auto;">
            <h2 class="section-title" style="color: #2e7d32;">Farmer Success Stories</h2>
            <div class="testimonial-grid">
                <div class="testimonial">
                    <p style="margin-bottom: 1rem; font-style: italic;">
                        "AgriShare changed my farming completely. Now I use modern tractor without paying full price. My yield increased by 40% and costs reduced by half."
                    </p>
                    <div class="farmer-info">
                        <div class="farmer-avatar">🧑‍🌾</div>
                        <div>
                            <strong>Suresh Patil</strong><br>
                            <small>Cotton Farmer, Akola</small>
                        </div>
                    </div>
                </div>

                <div class="testimonial">
                    <p style="margin-bottom: 1rem; font-style: italic;">
                        "The scheduling system is so simple. I book equipment from my phone, and it arrives on time. No more waiting weeks for custom hiring."
                    </p>
                    <div class="farmer-info">
                        <div class="farmer-avatar">👨‍🌾</div>
                        <div>
                            <strong>Ramesh Deshmukh</strong><br>
                            <small>Wheat Farmer, Nagpur</small>
                        </div>
                    </div>
                </div>

                <div class="testimonial">
                    <p style="margin-bottom: 1rem; font-style: italic;">
                        "Our FPO joined AgriShare last year. Together we bought harvester and drip irrigation. Best decision for our community!"
                    </p>
                    <div class="farmer-info">
                        <div class="farmer-avatar">👩‍🌾</div>
                        <div>
                            <strong>Sunita Joshi</strong><br>
                            <small>FPO President, Amravati</small>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Partners Section -->
    <section id="partners" class="section scroll-animation">
        <h2 class="section-title">Partners & Support</h2>
        <div class="partners-grid">
            <div class="partner-card">
                <div class="partner-icon">🏦</div>
                <h3>Banks & NBFCs</h3>
                <p>Easy financing options with competitive interest rates for equipment purchase.</p>
            </div>
            <div class="partner-card">
                <div class="partner-icon">🛡️</div>
                <h3>Insurance Partners</h3>
                <p>Comprehensive equipment insurance to protect your investment from damages.</p>
            </div>
            <div class="partner-card">
                <div class="partner-icon">🏛️</div>
                <h3>Government Schemes</h3>
                <p>Direct linkage to PM-Kisan, SMAM, and state subsidies for maximum benefits.</p>
            </div>
            <div class="partner-card">
                <div class="partner-icon">🤝</div>
                <h3>FPO Network</h3>
                <p>Collaboration with 500+ Farmer Producer Organizations across India.</p>
            </div>
            <div class="partner-card">
                <div class="partner-icon">🔧</div>
                <h3>Service Centers</h3>
                <p>24/7 maintenance support with authorized service centers in every district.</p>
            </div>
            <div class="partner-card">
                <div class="partner-icon">📱</div>
                <h3>Tech Partners</h3>
                <p>Digital payment integration with UPI, banking, and mobile wallet solutions.</p>
            </div>
        </div>
    </section>

    <!-- Revenue Model for Investors -->
    <section class="section scroll-animation" style="background: linear-gradient(135deg, #f8f9fa, #e9ecef); margin: 3rem -2rem; padding: 5rem 2rem; border-radius: 20px;">
        <div style="max-width: 1000px; margin: 0 auto;">
            <h2 class="section-title">For Investors & Partners</h2>
            <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 2rem; margin-top: 3rem;">
                <div style="background: white; padding: 2rem; border-radius: 15px; box-shadow: 0 5px 20px rgba(0,0,0,0.1);">
                    <h3 style="color: #2e7d32; margin-bottom: 1rem;">📊 Revenue Streams</h3>
                    <ul style="list-style: none; padding: 0;">
                        <li style="margin-bottom: 0.8rem;">💳 <strong>Platform Commission:</strong> 3-5% on equipment purchases</li>
                        <li style="margin-bottom: 0.8rem;">🔄 <strong>Subscription Model:</strong> ₹500/month per farmer for premium features</li>
                        <li style="margin-bottom: 0.8rem;">🔧 <strong>Maintenance Services:</strong> 10-15% markup on service costs</li>
                        <li style="margin-bottom: 0.8rem;">📱 <strong>Digital Services:</strong> Payment processing, insurance commissions</li>
                        <li style="margin-bottom: 0.8rem;">🎓 <strong>Training Programs:</strong> Equipment training and certification courses</li>
                    </ul>
                </div>
                
                <div style="background: white; padding: 2rem; border-radius: 15px; box-shadow: 0 5px 20px rgba(0,0,0,0.1);">
                    <h3 style="color: #2e7d32; margin-bottom: 1rem;">📈 Market Potential</h3>
                    <ul style="list-style: none; padding: 0;">
                        <li style="margin-bottom: 0.8rem;">👥 <strong>Target Market:</strong> 146 million farmers in India</li>
                        <li style="margin-bottom: 0.8rem;">💰 <strong>Equipment Market:</strong> ₹75,000 crore annually</li>
                        <li style="margin-bottom: 0.8rem;">📱 <strong>Digital Adoption:</strong> 60% smartphone penetration in rural areas</li>
                        <li style="margin-bottom: 0.8rem;">🏛️ <strong>Government Support:</strong> ₹5,000 crore subsidy allocation</li>
                        <li style="margin-bottom: 0.8rem;">🚀 <strong>Growth Rate:</strong> 12-15% CAGR in agri-tech sector</li>
                    </ul>
                </div>
            </div>
            
            <div style="text-align: center; margin-top: 3rem;">
                <a href="#contact" class="btn btn-primary">Invest in AgriShare</a>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="section scroll-animation">
        <h2 class="section-title">Get Started Today</h2>
        <div class="contact-form">
            <form id="contactForm">
                <div class="form-group">
                    <label for="userType">I am a:</label>
                    <select id="userType" name="userType" required>
                        <option value="">Select your role</option>
                        <option value="farmer">Farmer</option>
                        <option value="fpo">FPO Representative</option>
                        <option value="investor">Investor/Partner</option>
                        <option value="service">Service Provider</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label for="name">Full Name:</label>
                    <input type="text" id="name" name="name" required>
                </div>
                
                <div class="form-group">
                    <label for="phone">Phone Number:</label>
                    <input type="tel" id="phone" name="phone" required>
                </div>
                
                <div class="form-group">
                    <label for="location">Village/City:</label>
                    <input type="text" id="location" name="location" required>
                </div>
                
                <div class="form-group" id="farmerFields" style="display: none;">
                    <label for="landSize">Land Size (in acres):</label>
                    <input type="number" id="landSize" name="landSize" min="0" step="0.5">
                </div>
                
                <div class="form-group">
                    <label for="interest">Equipment/Service Interest:</label>
                    <textarea id="interest" name="interest" rows="3" placeholder="Tell us what equipment you need or how you want to partner with us"></textarea>
                </div>
                
                <button type="submit" class="btn btn-primary" style="width: 100%;">
                    Submit Application <span id="loadingSpinner" class="loading" style="display: none;"></span>
                </button>
            </form>
        </div>
        
        <!-- Contact Info -->
        <div style="text-align: center; margin-top: 3rem; padding-top: 2rem; border-top: 2px solid #e0e0e0;">
            <h3 style="color: #2e7d32; margin-bottom: 1rem;">Need Help?</h3>
            <p style="font-size: 1.1rem; margin-bottom: 1rem;">
                📞 Helpline: <strong>1800-123-AGRI (2474)</strong> (Toll-Free)
            </p>
            <p style="font-size: 1.1rem; margin-bottom: 1rem;">
                💬 WhatsApp Support: <strong>+91 98765-43210</strong>
            </p>
            <p style="font-size: 1.1rem;">
                📧 Email: <strong>support@agrishare.in</strong>
            </p>
            
            <div style="margin-top: 2rem;">
                <h4 style="color: #2e7d32; margin-bottom: 1rem;">Local Coordinators</h4>
                <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 1rem; max-width: 600px; margin: 0 auto;">
                    <div>
                        <strong>Amravati Region</strong><br>
                        Prakash Sharma<br>
                        📱 +91 99999-11111
                    </div>
                    <div>
                        <strong>Nagpur Region</strong><br>
                        Sunita Desai<br>
                        📱 +91 99999-22222
                    </div>
                    <div>
                        <strong>Akola Region</strong><br>
                        Rajesh Patil<br>
                        📱 +91 99999-33333
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
        <div class="footer-content">
            <div class="footer-section">
                <h3>AgriShare</h3>
                <p>Empowering farmers through collective ownership of agricultural equipment.</p>
                <div style="margin-top: 1rem;">
                    <span style="font-size: 1.5rem; margin-right: 1rem;">📱</span>
                    <span style="font-size: 1.5rem; margin-right: 1rem;">💻</span>
                    <span style="font-size: 1.5rem;">📧</span>
                </div>
            </div>
            
            <div class="footer-section">
                <h3>Quick Links</h3>
                <a href="#about">About Us</a>
                <a href="#how-it-works">How It Works</a>
                <a href="#equipment">Equipment</a>
                <a href="#testimonials">Success Stories</a>
                <a href="#partners">Partners</a>
            </div>
            
            <div class="footer-section">
                <h3>For Farmers</h3>
                <a href="#contact">Join as Farmer</a>
                <a href="#equipment">Equipment Catalog</a>
                <a href="javascript:void(0)" onclick="showDashboard('booking')">Book Equipment</a>
                <a href="javascript:void(0)">Government Schemes</a>
                <a href="javascript:void(0)">Training Programs</a>
            </div>
            
            <div class="footer-section">
                <h3>Support</h3>
                <a href="javascript:void(0)">Help Center</a>
                <a href="javascript:void(0)">Contact Support</a>
                <a href="javascript:void(0)">Terms of Service</a>
                <a href="javascript:void(0)">Privacy Policy</a>
                <a href="javascript:void(0)">FAQs</a>
            </div>
        </div>
        
        <div style="border-top: 1px solid rgba(255,255,255,0.2); padding-top: 2rem; text-align: center;">
            <p>&copy; 2025 AgriShare. All rights reserved. | Made with ❤️ for Indian Farmers</p>
            <p style="margin-top: 0.5rem; font-size: 0.9rem; opacity: 0.8;">
                🌾 Connecting Farmers • Sharing Resources • Growing Together 🌾
            </p>
        </div>
    </footer>

    <!-- Language Selector -->
    <button class="language-selector" onclick="toggleLanguage()">
        🌐 हिंदी
    </button>

    <!-- AI Chatbot Placeholder -->
    <div id="chatbot" style="position: fixed; bottom: 80px; right: 20px; width: 60px; height: 60px; background: linear-gradient(45deg, #4caf50, #8bc34a); border-radius: 50%; display: flex; align-items: center; justify-content: center; cursor: pointer; box-shadow: 0 4px 15px rgba(76, 175, 80, 0.3); transition: all 0.3s ease; z-index: 1000;" onclick="openChatbot()">
        <span style="font-size: 1.5rem; color: white;">🤖</span>
    </div>

    <script>
        // Smooth scrolling for navigation links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        // Scroll animation observer
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -100px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, observerOptions);

        document.querySelectorAll('.scroll-animation').forEach(el => {
            observer.observe(el);
        });

        // Dashboard functionality
        const dashboardContent = {
            profile: `
                <div style="text-align: center; padding: 2rem;">
                    <h3 style="color: #2e7d32; margin-bottom: 1rem;">👨‍🌾 Farmer Profile</h3>
                    <p><strong>Name:</strong> Rajesh Kumar</p>
                    <p><strong>Village:</strong> Khandala, Maharashtra</p>
                    <p><strong>Land Size:</strong> 12 acres</p>
                    <p><strong>Crops:</strong> Cotton, Soybean, Wheat</p>
                    <p><strong>Group:</strong> Khandala Farmers Collective (8 members)</p>
                    <div style="margin-top: 2rem;">
                        <div class="btn btn-primary" style="display: inline-block; margin: 0.5rem;">Update Profile</div>
                    </div>
                </div>
            `,
            equipment: `
                <div style="text-align: center; padding: 2rem;">
                    <h3 style="color: #2e7d32; margin-bottom: 2rem;">🚜 My Equipment Pool</h3>
                    <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 1rem;">
                        <div style="background: #f0f9f0; padding: 1rem; border-radius: 10px; border-left: 4px solid #4caf50;">
                            <strong>Tractor (45 HP)</strong><br>
                            <small>Shared with 4 others</small><br>
                            <span style="color: #4caf50;">✓ Available</span>
                        </div>
                        <div style="background: #fff3e0; padding: 1rem; border-radius: 10px; border-left: 4px solid #ff9800;">
                            <strong>Harvester</strong><br>
                            <small>Shared with 9 others</small><br>
                            <span style="color: #ff9800;">⏰ In Use by Suresh</span>
                        </div>
                        <div style="background: #e3f2fd; padding: 1rem; border-radius: 10px; border-left: 4px solid #2196f3;">
                            <strong>Drip System</strong><br>
                            <small>Shared with 4 others</small><br>
                            <span style="color: #2196f3;">🔧 Under Maintenance</span>
                        </div>
                    </div>
                </div>
            `,
            booking: `
                <div style="padding: 2rem;">
                    <h3 style="color: #2e7d32; margin-bottom: 2rem; text-align: center;">📅 Book & Schedule</h3>
                    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 2rem;">
                        <div>
                            <h4 style="margin-bottom: 1rem;">Quick Booking</h4>
                            <div style="margin-bottom: 1rem;">
                                <label style="display: block; margin-bottom: 0.5rem;">Equipment:</label>
                                <select style="width: 100%; padding: 0.5rem; border: 1px solid #ddd; border-radius: 5px;">
                                    <option>Tractor (45 HP)</option>
                                    <option>Harvester</option>
                                    <option>Sprayer</option>
                                </select>
                            </div>
                            <div style="margin-bottom: 1rem;">
                                <label style="display: block; margin-bottom: 0.5rem;">Date:</label>
                                <input type="date" style="width: 100%; padding: 0.5rem; border: 1px solid #ddd; border-radius: 5px;">
                            </div>
                            <div style="margin-bottom: 1rem;">
                                <label style="display: block; margin-bottom: 0.5rem;">Duration:</label>
                                <select style="width: 100%; padding: 0.5rem; border: 1px solid #ddd; border-radius: 5px;">
                                    <option>Half Day (4 hours)</option>
                                    <option>Full Day (8 hours)</option>
                                    <option>2 Days</option>
                                </select>
                            </div>
                            <button class="btn btn-primary" style="width: 100%;">Book Now</button>
                        </div>
                        <div>
                            <h4 style="margin-bottom: 1rem;">My Upcoming Bookings</h4>
                            <div style="background: #f0f9f0; padding: 1rem; border-radius: 8px; margin-bottom: 1rem;">
                                <strong>Tomorrow - Tractor</strong><br>
                                <small>9:00 AM - 5:00 PM</small><br>
                                <span style="color: #4caf50;">✓ Confirmed</span>
                            </div>
                            <div style="background: #fff3e0; padding: 1rem; border-radius: 8px;">
                                <strong>Next Week - Harvester</strong><br>
                                <small>Monday, 6:00 AM</small><br>
                                <span style="color: #ff9800;">⏳ Pending</span>
                            </div>
                        </div>
                    </div>
                </div>
            `,
            payments: `
                <div style="padding: 2rem; text-align: center;">
                    <h3 style="color: #2e7d32; margin-bottom: 2rem;">💰 Payments & Wallet</h3>
                    <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 1rem; margin-bottom: 2rem;">
                        <div style="background: linear-gradient(45deg, #4caf50, #8bc34a); color: white; padding: 1.5rem; border-radius: 10px;">
                            <h4>Wallet Balance</h4>
                            <h2>₹15,450</h2>
                        </div>
                        <div style="background: linear-gradient(45deg, #2196f3, #03a9f4); color: white; padding: 1.5rem; border-radius: 10px;">
                            <h4>This Month</h4>
                            <h2>₹3,200</h2>
                            <small>Equipment usage</small>
                        </div>
                        <div style="background: linear-gradient(45deg, #ff9800, #ffc107); color: white; padding: 1.5rem; border-radius: 10px;">
                            <h4>Pending Dues</h4>
                            <h2>₹1,800</h2>
                            <small>Maintenance share</small>
                        </div>
                    </div>
                    <div style="text-align: left;">
                        <h4 style="margin-bottom: 1rem;">Recent Transactions</h4>
                        <div style="background: white; border: 1px solid #ddd; border-radius: 8px;">
                            <div style="padding: 1rem; border-bottom: 1px solid #eee;">
                                <strong>Tractor Usage Fee</strong> <span style="float: right; color: #f44336;">-₹800</span><br>
                                <small>Yesterday, 2:30 PM</small>
                            </div>
                            <div style="padding: 1rem; border-bottom: 1px solid #eee;">
                                <strong>Wallet Recharge</strong> <span style="float: right; color: #4caf50;">+₹5,000</span><br>
                                <small>3 days ago, 10:15 AM</small>
                            </div>
                            <div style="padding: 1rem;">
                                <strong>Maintenance Share</strong> <span style="float: right; color: #f44336;">-₹450</span><br>
                                <small>1 week ago, 4:45 PM</small>
                            </div>
                        </div>
                    </div>
                </div>
            `,
            maintenance: `
                <div style="padding: 2rem; text-align: center;">
                    <h3 style="color: #2e7d32; margin-bottom: 2rem;">🔧 Maintenance Alerts</h3>
                    <div style="display: grid; gap: 1rem; text-align: left;">
                        <div style="background: #ffebee; border-left: 4px solid #f44336; padding: 1rem; border-radius: 8px;">
                            <div style="display: flex; justify-content: space-between; align-items: center;">
                                <div>
                                    <strong>🚨 Urgent: Tractor Service Due</strong><br>
                                    <small>Last service: 3 months ago</small>
                                </div>
                                <button class="btn btn-primary" style="font-size: 0.9rem; padding: 0.5rem 1rem;">Schedule Service</button>
                            </div>
                        </div>
                        <div style="background: #fff3e0; border-left: 4px solid #ff9800; padding: 1rem; border-radius: 8px;">
                            <div style="display: flex; justify-content: space-between; align-items: center;">
                                <div>
                                    <strong>⚠️ Harvester Insurance Renewal</strong><br>
                                    <small>Expires in 15 days</small>
                                </div>
                                <button class="btn btn-secondary" style="font-size: 0.9rem; padding: 0.5rem 1rem; background: #ff9800; color: white; border: none;">Renew</button>
                            </div>
                        </div>
                        <div style="background: #e8f5e8; border-left: 4px solid #4caf50; padding: 1rem; border-radius: 8px;">
                            <div style="display: flex; justify-content: space-between; align-items: center;">
                                <div>
                                    <strong>✅ Drip System Maintenance Complete</strong><br>
                                    <small>Service completed yesterday</small>
                                </div>
                                <span style="color: #4caf50; font-weight: bold;">✓ Done</span>
                            </div>
                        </div>
                    </div>
                    <div style="margin-top: 2rem; text-align: center;">
                        <p style="color: #666; margin-bottom: 1rem;">🔔 Get instant notifications on your phone</p>
                        <button class="btn btn-primary">Enable Push Notifications</button>
                    </div>
                </div>
            `
        };

        function showDashboard(tab) {
            // Update active tab
            document.querySelectorAll('.dashboard-tab').forEach(t => t.classList.remove('active'));
            event.target.classList.add('active');
            
            // Update content
            document.getElementById('dashboard-content').innerHTML = dashboardContent[tab];
        }

        // Contact form functionality
        document.getElementById('userType').addEventListener('change', function() {
            const farmerFields = document.getElementById('farmerFields');
            if (this.value === 'farmer' || this.value === 'fpo') {
                farmerFields.style.display = 'block';
            } else {
                farmerFields.style.display = 'none';
            }
        });

        document.getElementById('contactForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const spinner = document.getElementById('loadingSpinner');
            const submitBtn = e.target.querySelector('button[type="submit"]');
            
            // Show loading
            spinner.style.display = 'inline-block';
            submitBtn.disabled = true;
            
            // Simulate form submission
            setTimeout(() => {
                alert('Thank you! Your application has been submitted successfully. Our team will contact you within 24 hours.');
                
                // Hide loading
                spinner.style.display = 'none';
                submitBtn.disabled = false;
                
                // Reset form
                this.reset();
                document.getElementById('farmerFields').style.display = 'none';
            }, 2000);
        });

        // Language toggle
        function toggleLanguage() {
            const btn = document.querySelector('.language-selector');
            if (btn.textContent.includes('हिंदी')) {
                btn.innerHTML = '🌐 English';
                // Here you would implement actual language switching
                alert('Hindi language support coming soon! / हिंदी भाषा समर्थन जल्द आ रहा है!');
            } else {
                btn.innerHTML = '🌐 हिंदी';
            }
        }

        // Chatbot functionality
        function openChatbot() {
            alert('🤖 AI Assistant: Hello! I can help you with:\n\n• How to join AgriShare\n• Equipment information\n• Booking process\n• Government schemes\n• Technical support\n\nFull chatbot coming soon!');
        }

        // Mobile menu functionality
        document.querySelector('.mobile-menu').addEventListener('click', function() {
            const navLinks = document.querySelector('.nav-links');
            navLinks.style.display = navLinks.style.display === 'flex' ? 'none' : 'flex';
            
            if (navLinks.style.display === 'flex') {
                navLinks.style.position = 'fixed';
                navLinks.style.top = '80px';
                navLinks.style.left = '0';
                navLinks.style.right = '0';
                navLinks.style.background = 'linear-gradient(135deg, #2e7d32, #4caf50)';
                navLinks.style.flexDirection = 'column';
                navLinks.style.padding = '2rem';
                navLinks.style.zIndex = '999';
                navLinks.style.borderRadius = '0 0 15px 15px';
                navLinks.style.boxShadow = '0 5px 20px rgba(0,0,0,0.2)';
            }
        });

        // Navbar scroll effect
        window.addEventListener('scroll', function() {
            const navbar = document.querySelector('.navbar');
            if (window.scrollY > 100) {
                navbar.style.background = 'linear-gradient(135deg, rgba(46, 125, 50, 0.95), rgba(76, 175, 80, 0.95))';
                navbar.style.backdropFilter = 'blur(10px)';
            } else {
                navbar.style.background = 'linear-gradient(135deg, #2e7d32, #4caf50)';
                navbar.style.backdropFilter = 'none';
            }
        });

        // Add some interactive hover effects
        document.querySelectorAll('.equipment-card, .step, .testimonial, .partner-card').forEach(card => {
            card.addEventListener('mouseenter', function() {
                this.style.transform = 'translateY(-8px) scale(1.02)';
            });
            
            card.addEventListener('mouseleave', function() {
                this.style.transform = 'translateY(0) scale(1)';
            });
        });

        // Auto-advance testimonials (simple version)
        let currentTestimonial = 0;
        const testimonials = document.querySelectorAll('.testimonial');
        
        setInterval(() => {
            testimonials[currentTestimonial].style.opacity = '0.7';
            currentTestimonial = (currentTestimonial + 1) % testimonials.length;
            
            setTimeout(() => {
                testimonials.forEach(t => t.style.opacity = '1');
                testimonials[currentTestimonial].style.transform = 'scale(1.05)';
                
                setTimeout(() => {
                    testimonials[currentTestimonial].style.transform = 'scale(1)';
                }, 500);
            }, 250);
        }, 5000);

        // Initialize page
        document.addEventListener('DOMContentLoaded', function() {
            // Add initial animations
            setTimeout(() => {
                document.querySelectorAll('.scroll-animation').forEach((el, index) => {
                    setTimeout(() => {
                        if (el.getBoundingClientRect().top < window.innerHeight) {
                            el.classList.add('visible');
                        }
                    }, index * 100);
                });
            }, 500);
        });
    </script>
</body>
</html>
