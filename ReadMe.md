<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Atharva Wagh - Frontend Developer</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700;800&display=swap');

        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #0f172a 0%, #1e293b 50%, #334155 100%);
            color: #f8fafc;
            overflow-x: hidden;
            line-height: 1.6;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
        }

        /* Animated Background */
        .bg-animation {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            opacity: 0.1;
        }

        .bg-animation::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><circle cx="50" cy="50" r="2" fill="white" opacity="0.3"><animate attributeName="r" values="2;10;2" dur="3s" repeatCount="indefinite"/></circle></svg>');
            animation: float 20s infinite linear;
        }

        @keyframes float {
            0% { transform: translateY(100vh) rotate(0deg); }
            100% { transform: translateY(-100vh) rotate(360deg); }
        }

        /* Header Section */
        .header {
            text-align: center;
            margin-bottom: 4rem;
            position: relative;
        }

        .profile-banner {
            width: 100%;
            height: 200px;
            background: linear-gradient(45deg, #0ea5e9, #06b6d4, #10b981, #3b82f6);
            background-size: 400% 400%;
            animation: gradientShift 8s ease infinite;
            border-radius: 20px;
            margin-bottom: 2rem;
            position: relative;
            overflow: hidden;
        }

        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .profile-banner::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><polygon points="0,100 100,0 100,100" fill="rgba(255,255,255,0.1)"/></svg>');
        }

        .main-title {
            font-size: 3.5rem;
            font-weight: 800;
            margin-bottom: 1rem;
            background: linear-gradient(45deg, #0ea5e9, #06b6d4);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: titleGlow 2s ease-in-out infinite alternate;
        }

        @keyframes titleGlow {
            from { filter: drop-shadow(0 0 10px rgba(14, 165, 233, 0.5)); }
            to { filter: drop-shadow(0 0 20px rgba(6, 182, 212, 0.5)); }
        }

        .subtitle {
            font-size: 1.3rem;
            color: #94a3b8;
            margin-bottom: 2rem;
            font-weight: 400;
        }

        .coding-gif {
            position: absolute;
            right: -50px;
            top: 50%;
            transform: translateY(-50%);
            width: 300px;
            height: 200px;
            background: rgba(15, 23, 42, 0.8);
            border-radius: 15px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(6, 182, 212, 0.3);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.2rem;
            opacity: 0.9;
            color: #06b6d4;
            font-weight: 500;
        }

        /* Stats Cards */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin: 3rem 0;
        }

        .stat-card {
            background: rgba(15, 23, 42, 0.6);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 2rem;
            border: 1px solid rgba(6, 182, 212, 0.2);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .stat-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(6, 182, 212, 0.1), transparent);
            transition: left 0.5s ease;
        }

        .stat-card:hover::before {
            left: 100%;
        }

        .stat-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(6, 182, 212, 0.2);
            border-color: rgba(6, 182, 212, 0.4);
        }

        .stat-title {
            font-size: 1.1rem;
            font-weight: 600;
            margin-bottom: 1rem;
            color: #06b6d4;
        }

        .stat-content {
            font-size: 0.95rem;
            line-height: 1.6;
        }

        /* About Section */
        .about-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin: 4rem 0;
        }

        .about-card {
            background: rgba(15, 23, 42, 0.4);
            backdrop-filter: blur(15px);
            border-radius: 25px;
            padding: 2.5rem;
            border: 1px solid rgba(59, 130, 246, 0.2);
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .about-card:hover {
            background: rgba(15, 23, 42, 0.7);
            transform: scale(1.02);
            border-color: rgba(59, 130, 246, 0.4);
            box-shadow: 0 25px 50px rgba(59, 130, 246, 0.1);
        }

        .about-icon {
            font-size: 2.5rem;
            margin-bottom: 1.5rem;
            display: block;
        }

        .about-title {
            font-size: 1.4rem;
            font-weight: 700;
            margin-bottom: 1rem;
            color: #3b82f6;
        }

        /* Social Links */
        .social-section {
            text-align: center;
            margin: 4rem 0;
        }

        .section-title {
            font-size: 2rem;
            font-weight: 700;
            margin-bottom: 2rem;
            color: #0ea5e9;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 1.5rem;
            flex-wrap: wrap;
        }

        .social-link {
            width: 60px;
            height: 60px;
            background: rgba(15, 23, 42, 0.6);
            backdrop-filter: blur(10px);
            border-radius: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s ease;
            border: 1px solid rgba(16, 185, 129, 0.3);
            text-decoration: none;
            color: #10b981;
            font-size: 1.5rem;
        }

        .social-link:hover {
            transform: translateY(-5px) scale(1.1);
            background: rgba(16, 185, 129, 0.2);
            box-shadow: 0 10px 25px rgba(16, 185, 129, 0.3);
            border-color: rgba(16, 185, 129, 0.6);
        }

        /* Tech Stack */
        .tech-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
            gap: 1.5rem;
            margin: 3rem 0;
        }

        .tech-item {
            background: rgba(15, 23, 42, 0.5);
            backdrop-filter: blur(10px);
            border-radius: 15px;
            padding: 1.5rem;
            text-align: center;
            transition: all 0.3s ease;
            border: 1px solid rgba(14, 165, 233, 0.2);
        }

        .tech-item:hover {
            transform: translateY(-8px) rotate(5deg);
            background: rgba(14, 165, 233, 0.2);
            border-color: rgba(14, 165, 233, 0.4);
            box-shadow: 0 15px 30px rgba(14, 165, 233, 0.2);
        }

        .tech-icon {
            font-size: 2.5rem;
            margin-bottom: 0.5rem;
            display: block;
        }

        .tech-name {
            font-size: 0.9rem;
            font-weight: 600;
        }

        /* GitHub Stats */
        .github-stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin: 3rem 0;
        }

        .stat-image {
            background: rgba(15, 23, 42, 0.6);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 1.5rem;
            border: 1px solid rgba(59, 130, 246, 0.2);
            text-align: center;
            transition: all 0.3s ease;
        }

        .stat-image:hover {
            transform: scale(1.02);
            background: rgba(15, 23, 42, 0.9);
            border-color: rgba(59, 130, 246, 0.4);
        }

        .stat-placeholder {
            width: 100%;
            height: 200px;
            background: linear-gradient(45deg, #1e40af, #3b82f6, #0ea5e9, #06b6d4);
            border-radius: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: 600;
            margin-bottom: 1rem;
            font-size: 1.1rem;
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .main-title {
                font-size: 2.5rem;
            }
            
            .coding-gif {
                position: static;
                transform: none;
                width: 100%;
                margin: 2rem 0;
            }
            
            .container {
                padding: 1rem;
            }
            
            .stats-grid {
                grid-template-columns: 1fr;
            }
        }

        /* Animation for page load */
        .fade-in {
            animation: fadeInUp 0.8s ease forwards;
            opacity: 0;
            transform: translateY(30px);
        }

        .fade-in:nth-child(1) { animation-delay: 0.1s; }
        .fade-in:nth-child(2) { animation-delay: 0.2s; }
        .fade-in:nth-child(3) { animation-delay: 0.3s; }
        .fade-in:nth-child(4) { animation-delay: 0.4s; }

        @keyframes fadeInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
    </style>
</head>
<body>
    <div class="bg-animation"></div>
    
    <div class="container">
        <!-- Header Section -->
        <div class="header fade-in">
            <div class="profile-banner"></div>
            <h1 class="main-title">Hi 👋, I'm Atharva Wagh</h1>
            <p class="subtitle">A passionate frontend developer from India</p>
            <div class="coding-gif">
                🚀 Coding in Progress...
            </div>
        </div>

        <!-- About Cards -->
        <div class="about-grid fade-in">
            <div class="about-card">
                <span class="about-icon">🌱</span>
                <h3 class="about-title">Currently Learning</h3>
                <p>Diving deep into Graphic Designing to enhance my creative skills and bring visual concepts to life.</p>
            </div>
            
            <div class="about-card">
                <span class="about-icon">👨‍💻</span>
                <h3 class="about-title">Portfolio</h3>
                <p>Check out all my projects and work at <a href="https://portfolio-ai34.onrender.com/" style="color: #0ea5e9; text-decoration: none; font-weight: 500;">my portfolio</a></p>
            </div>
            
            <div class="about-card">
                <span class="about-icon">💬</span>
                <h3 class="about-title">Ask Me About</h3>
                <p>React development, frontend technologies, and creating amazing user experiences.</p>
            </div>
            
            <div class="about-card">
                <span class="about-icon">📫</span>
                <h3 class="about-title">Contact Me</h3>
                <p>Reach out at <a href="mailto:watharva383@gmail.com" style="color: #0ea5e9; text-decoration: none; font-weight: 500;">watharva383@gmail.com</a></p>
            </div>
        </div>

        <!-- Social Links -->
        <div class="social-section fade-in">
            <h3 class="section-title">Connect with me</h3>
            <div class="social-links">
                <a href="https://x.com/watharva383?t=smepiyiin8ckpioi0je4jw&s=08" class="social-link" title="Twitter">🐦</a>
                <a href="https://linkedin.com/in/atharva-wagh-686824322" class="social-link" title="LinkedIn">💼</a>
                <a href="https://stackoverflow.com/users/user:29531307" class="social-link" title="Stack Overflow">📚</a>
                <a href="https://fb.com/atharva.wagh.313" class="social-link" title="Facebook">📘</a>
                <a href="https://instagram.com/atharva.wagh.313" class="social-link" title="Instagram">📷</a>
            </div>
        </div>

        <!-- Tech Stack -->
        <div class="fade-in">
            <h3 class="section-title">Languages and Tools</h3>
            <div class="tech-grid">
                <div class="tech-item">
                    <span class="tech-icon">⚡</span>
                    <div class="tech-name">C</div>
                </div>
                <div class="tech-item">
                    <span class="tech-icon">🔥</span>
                    <div class="tech-name">C++</div>
                </div>
                <div class="tech-item">
                    <span class="tech-icon">🎨</span>
                    <div class="tech-name">CSS3</div>
                </div>
                <div class="tech-item">
                    <span class="tech-icon">🚀</span>
                    <div class="tech-name">Express.js</div>
                </div>
                <div class="tech-item">
                    <span class="tech-icon">⚛️</span>
                    <div class="tech-name">React</div>
                </div>
                <div class="tech-item">
                    <span class="tech-icon">🌊</span>
                    <div class="tech-name">Tailwind</div>
                </div>
            </div>
        </div>

        <!-- GitHub Stats -->
        <div class="fade-in">
            <h3 class="section-title">GitHub Statistics</h3>
            <div class="github-stats">
                <div class="stat-image">
                    <div class="stat-placeholder">📊 Top Languages</div>
                    <p>Most used programming languages</p>
                </div>
                <div class="stat-image">
                    <div class="stat-placeholder">📈 GitHub Stats</div>
                    <p>Overall GitHub statistics</p>
                </div>
                <div class="stat-image">
                    <div class="stat-placeholder">🔥 Streak Stats</div>
                    <p>Contribution streak information</p>
                </div>
            </div>
        </div>

        <!-- Profile Views -->
        <div class="stats-grid fade-in">
            <div class="stat-card">
                <div class="stat-title">👀 Profile Views</div>
                <div class="stat-content">Thanks for visiting my profile! Every view motivates me to keep building amazing projects.</div>
            </div>
            <div class="stat-card">
                <div class="stat-title">🏆 Achievements</div>
                <div class="stat-content">Constantly working on new projects and learning cutting-edge technologies.</div>
            </div>
        </div>
    </div>

    <script>
        // Add some interactive elements
        document.addEventListener('DOMContentLoaded', function() {
            // Animate social links on hover
            const socialLinks = document.querySelectorAll('.social-link');
            socialLinks.forEach(link => {
                link.addEventListener('mouseenter', function() {
                    this.style.transform = 'translateY(-5px) scale(1.1) rotate(10deg)';
                });
                link.addEventListener('mouseleave', function() {
                    this.style.transform = 'translateY(0) scale(1) rotate(0deg)';
                });
            });

            // Add floating animation to tech items
            const techItems = document.querySelectorAll('.tech-item');
            techItems.forEach((item, index) => {
                item.style.animationDelay = `${index * 0.1}s`;
                item.style.animation = 'float 6s ease-in-out infinite';
            });

            // Create floating particles
            function createParticle() {
                const particle = document.createElement('div');
                particle.style.position = 'fixed';
                particle.style.width = '3px';
                particle.style.height = '3px';
                particle.style.background = 'rgba(6, 182, 212, 0.7)';
                particle.style.borderRadius = '50%';
                particle.style.pointerEvents = 'none';
                particle.style.left = Math.random() * window.innerWidth + 'px';
                particle.style.top = window.innerHeight + 'px';
                particle.style.zIndex = '-1';
                particle.style.boxShadow = '0 0 6px rgba(6, 182, 212, 0.5)';
                
                document.body.appendChild(particle);
                
                const animation = particle.animate([
                    { transform: 'translateY(0px)', opacity: 1 },
                    { transform: 'translateY(-100vh)', opacity: 0 }
                ], {
                    duration: Math.random() * 3000 + 2000,
                    easing: 'linear'
                });
                
                animation.onfinish = () => particle.remove();
            }

            // Create particles periodically
            setInterval(createParticle, 300);
        });
    </script>
</body>
</html>
