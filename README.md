<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NextGen STEM - Learning Portal</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;700;900&family=Exo+2:wght@300;400;600&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary-color: #00f5ff;
            --secondary-color: #ff00ff;
            --accent-color: #ffff00;
            --dark-bg: #050510;
            --card-bg: rgba(5, 5, 20, 0.9);
            --input-bg: rgba(10, 10, 30, 0.8);
            --text-light: #e0e0ff;
            --success: #00ff88;
            --error: #ff3366;
            --border-color: rgba(0, 245, 255, 0.5);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Exo 2', sans-serif;
            background-color: var(--dark-bg);
            color: var(--text-light);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
            position: relative;
        }

        /* Animated Background */
        .bg-animation {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            background: linear-gradient(135deg, #050510 0%, #0a0a1a 50%, #050515 100%);
            overflow: hidden;
        }

        .particles {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
        }

        .particle {
            position: absolute;
            background-color: var(--primary-color);
            border-radius: 50%;
            opacity: 0.3;
            animation: float 15s infinite linear;
        }

        @keyframes float {
            0% {
                transform: translateY(0) translateX(0);
                opacity: 0;
            }
            10% {
                opacity: 0.3;
            }
            90% {
                opacity: 0.3;
            }
            100% {
                transform: translateY(-100vh) translateX(100px);
                opacity: 0;
            }
        }

        .circuit-lines {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: 
                linear-gradient(90deg, rgba(0, 245, 255, 0.05) 1px, transparent 1px),
                linear-gradient(rgba(0, 245, 255, 0.05) 1px, transparent 1px);
            background-size: 50px 50px;
            animation: circuit-move 20s linear infinite;
        }

        @keyframes circuit-move {
            0% {
                background-position: 0 0;
            }
            100% {
                background-position: 50px 50px;
            }
        }

        /* Main Container */
        .login-container {
            width: 90%;
            max-width: 450px;
            position: relative;
            z-index: 10;
        }

        .login-card {
            background: var(--card-bg);
            border-radius: 20px;
            padding: 40px 30px;
            backdrop-filter: blur(10px);
            box-shadow: 
                0 0 30px rgba(0, 245, 255, 0.2),
                0 0 60px rgba(255, 0, 255, 0.1),
                inset 0 0 20px rgba(0, 245, 255, 0.05);
            border: 2px solid var(--border-color);
            position: relative;
            overflow: hidden;
            animation: card-glow 3s infinite alternate;
        }

        @keyframes card-glow {
            0% {
                box-shadow: 
                    0 0 30px rgba(0, 245, 255, 0.2),
                    0 0 60px rgba(255, 0, 255, 0.1),
                    inset 0 0 20px rgba(0, 245, 255, 0.05);
            }
            100% {
                box-shadow: 
                    0 0 40px rgba(0, 245, 255, 0.3),
                    0 0 80px rgba(255, 0, 255, 0.2),
                    inset 0 0 30px rgba(0, 245, 255, 0.1);
            }
        }

        .login-card::before {
            content: '';
            position: absolute;
            top: -2px;
            left: -2px;
            right: -2px;
            bottom: -2px;
            background: linear-gradient(45deg, var(--primary-color), var(--secondary-color), var(--accent-color), var(--primary-color));
            border-radius: 20px;
            z-index: -1;
            background-size: 400% 400%;
            animation: gradient-border 8s ease infinite;
            opacity: 0.6;
        }

        @keyframes gradient-border {
            0% {
                background-position: 0% 50%;
            }
            50% {
                background-position: 100% 50%;
            }
            100% {
                background-position: 0% 50%;
            }
        }

        /* Logo and Title */
        .logo-section {
            text-align: center;
            margin-bottom: 30px;
        }

        .logo {
            width: 80px;
            height: 80px;
            margin: 0 auto 15px;
            position: relative;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0% {
                transform: scale(1);
            }
            50% {
                transform: scale(1.05);
            }
            100% {
                transform: scale(1);
            }
        }

        .logo-icon {
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 40px;
            color: var(--dark-bg);
            box-shadow: 0 0 20px rgba(0, 245, 255, 0.5);
        }

        .platform-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 36px;
            font-weight: 900;
            background: linear-gradient(90deg, var(--primary-color), var(--accent-color));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            margin-bottom: 5px;
            letter-spacing: 2px;
            text-transform: uppercase;
            line-height: 1.1;
        }

        .platform-subtitle {
            font-size: 14px;
            color: rgba(224, 224, 255, 0.7);
            font-weight: 300;
        }

        /* Login Form */
        .login-form {
            margin-top: 30px;
        }

        .form-group {
            margin-bottom: 25px;
            position: relative;
        }

        .form-input {
            width: 100%;
            padding: 15px 20px;
            background: var(--input-bg);
            border: 2px solid var(--border-color);
            border-radius: 10px;
            color: var(--text-light);
            font-size: 16px;
            transition: all 0.3s ease;
            outline: none;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
        }

        .form-input:focus {
            border-color: var(--primary-color);
            box-shadow: 
                0 0 15px rgba(0, 245, 255, 0.4),
                0 4px 10px rgba(0, 0, 0, 0.3);
            background: rgba(15, 15, 35, 0.9);
        }

        .form-label {
            position: absolute;
            top: 15px;
            left: 20px;
            color: rgba(224, 224, 255, 0.5);
            font-size: 16px;
            transition: all 0.3s ease;
            pointer-events: none;
            background: var(--input-bg);
            padding: 0 5px;
        }

        .form-input:focus + .form-label,
        .form-input:not(:placeholder-shown) + .form-label {
            top: -10px;
            left: 15px;
            font-size: 12px;
            color: var(--primary-color);
            background: var(--input-bg);
        }

        .form-icon {
            position: absolute;
            right: 15px;
            top: 50%;
            transform: translateY(-50%);
            color: rgba(224, 224, 255, 0.5);
            font-size: 18px;
        }

        /* Options Row */
        .options-row {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 25px;
            font-size: 14px;
        }

        .remember-me {
            display: flex;
            align-items: center;
        }

        .remember-me input {
            margin-right: 8px;
            accent-color: var(--primary-color);
        }

        .forgot-password {
            color: var(--primary-color);
            text-decoration: none;
            transition: all 0.3s ease;
        }

        .forgot-password:hover {
            color: var(--accent-color);
            text-shadow: 0 0 5px rgba(255, 255, 0, 0.5);
        }

        /* Login Button */
        .login-btn {
            width: 100%;
            padding: 15px;
            background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
            border: none;
            border-radius: 10px;
            color: var(--dark-bg);
            font-family: 'Orbitron', sans-serif;
            font-size: 16px;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 1px;
            cursor: pointer;
            position: relative;
            overflow: hidden;
            transition: all 0.3s ease;
            margin-bottom: 20px;
            box-shadow: 0 4px 15px rgba(0, 245, 255, 0.3);
        }

        .login-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(0, 245, 255, 0.4);
        }

        .login-btn:active {
            transform: translateY(1px);
        }

        .login-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.4), transparent);
            transition: left 0.5s;
        }

        .login-btn:hover::before {
            left: 100%;
        }

        /* Divider */
        .divider {
            display: flex;
            align-items: center;
            margin: 20px 0;
            color: rgba(224, 224, 255, 0.5);
            font-size: 14px;
        }

        .divider::before,
        .divider::after {
            content: '';
            flex: 1;
            height: 1px;
            background: rgba(0, 245, 255, 0.3);
        }

        .divider span {
            padding: 0 15px;
        }

        /* Social Login */
        .social-login {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-bottom: 25px;
        }

        .social-btn {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            background: var(--input-bg);
            border: 2px solid var(--border-color);
            color: var(--text-light);
            font-size: 20px;
            transition: all 0.3s ease;
            cursor: pointer;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
        }

        .social-btn:hover {
            background: rgba(0, 245, 255, 0.2);
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0, 245, 255, 0.3);
        }

        /* Signup Link */
        .signup-link {
            text-align: center;
            font-size: 14px;
            color: rgba(224, 224, 255, 0.7);
        }

        .signup-link a {
            color: var(--primary-color);
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s ease;
        }

        .signup-link a:hover {
            color: var(--accent-color);
            text-shadow: 0 0 5px rgba(255, 255, 0, 0.5);
        }

        /* Language Selector */
        .language-selector {
            position: absolute;
            top: 20px;
            right: 20px;
            z-index: 20;
        }

        .language-btn {
            background: var(--input-bg);
            border: 2px solid var(--border-color);
            border-radius: 5px;
            color: var(--text-light);
            padding: 8px 15px;
            font-size: 14px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 8px;
            transition: all 0.3s ease;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
        }

        .language-btn:hover {
            background: rgba(0, 245, 255, 0.2);
        }

        .language-dropdown {
            position: absolute;
            top: 100%;
            right: 0;
            margin-top: 5px;
            background: var(--card-bg);
            border: 2px solid var(--border-color);
            border-radius: 5px;
            width: 150px;
            display: none;
            z-index: 30;
            backdrop-filter: blur(10px);
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
        }

        .language-dropdown.active {
            display: block;
        }

        .language-option {
            padding: 10px 15px;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .language-option:hover {
            background: rgba(0, 245, 255, 0.2);
        }

        /* Notification */
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 15px 20px;
            border-radius: 10px;
            color: white;
            font-weight: 500;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            transform: translateX(120%);
            transition: transform 0.3s ease;
            z-index: 100;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .notification.show {
            transform: translateX(0);
        }

        .notification.success {
            background: linear-gradient(90deg, var(--success), #00cc6a);
        }

        .notification.error {
            background: linear-gradient(90deg, var(--error), #cc0052);
        }

        /* Loading Animation */
        .loading {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(5, 5, 20, 0.95);
            z-index: 1000;
            justify-content: center;
            align-items: center;
            flex-direction: column;
        }

        .loading.active {
            display: flex;
        }

        .loading-spinner {
            width: 60px;
            height: 60px;
            border: 5px solid rgba(0, 245, 255, 0.3);
            border-top-color: var(--primary-color);
            border-radius: 50%;
            animation: spin 1s linear infinite;
            margin-bottom: 20px;
        }

        @keyframes spin {
            to {
                transform: rotate(360deg);
            }
        }

        .loading-text {
            font-family: 'Orbitron', sans-serif;
            font-size: 18px;
            color: var(--primary-color);
        }

        /* Responsive Design */
        @media (max-width: 480px) {
            .login-card {
                padding: 30px 20px;
            }
            
            .platform-title {
                font-size: 30px;
            }
            
            .language-selector {
                top: 10px;
                right: 10px;
            }
        }
    </style>
</head>
<body>
    <!-- Animated Background -->
    <div class="bg-animation">
        <div class="circuit-lines"></div>
        <div class="particles" id="particles"></div>
    </div>

    <!-- Language Selector -->
    <div class="language-selector">
        <button class="language-btn" id="languageBtn">
            <i class="fas fa-globe"></i>
            <span id="currentLang">EN</span>
            <i class="fas fa-chevron-down"></i>
        </button>
        <div class="language-dropdown" id="languageDropdown">
            <div class="language-option" data-lang="en">
                <i class="fas fa-flag-usa"></i> English
            </div>
            <div class="language-option" data-lang="es">
                <i class="fas fa-flag"></i> Español
            </div>
            <div class="language-option" data-lang="fr">
                <i class="fas fa-flag"></i> Français
            </div>
            <div class="language-option" data-lang="hi">
                <i class="fas fa-flag"></i> हिन्दी
            </div>
            <div class="language-option" data-lang="zh">
                <i class="fas fa-flag"></i> 中文
            </div>
        </div>
    </div>

    <!-- Login Container -->
    <div class="login-container">
        <div class="login-card">
            <div class="logo-section">
                <div class="logo">
                    <div class="logo-icon">
                        <i class="fas fa-rocket"></i>
                    </div>
                </div>
                <h1 class="platform-title">NextGen STEM</h1>
                <p class="platform-subtitle">The Future of Learning</p>
            </div>

            <form class="login-form" id="loginForm">
                <div class="form-group">
                    <input type="text" class="form-input" id="username" placeholder=" " required>
                    <label class="form-label" for="username">Username or Email</label>
                    <i class="fas fa-user form-icon"></i>
                </div>

                <div class="form-group">
                    <input type="password" class="form-input" id="password" placeholder=" " required>
                    <label class="form-label" for="password">Password</label>
                    <i class="fas fa-lock form-icon"></i>
                </div>

                <div class="options-row">
                    <div class="remember-me">
                        <input type="checkbox" id="remember">
                        <label for="remember">Remember me</label>
                    </div>
                    <a href="#" class="forgot-password">Forgot Password?</a>
                </div>

                <button type="submit" class="login-btn">Login to Dashboard</button>
            </form>

            <div class="divider">
                <span>OR</span>
            </div>

            <div class="social-login">
                <div class="social-btn">
                    <i class="fab fa-google"></i>
                </div>
                <div class="social-btn">
                    <i class="fab fa-microsoft"></i>
                </div>
                <div class="social-btn">
                    <i class="fab fa-apple"></i>
                </div>
            </div>

            <div class="signup-link">
                Don't have an account? <a href="#">Sign Up</a>
            </div>
        </div>
    </div>

    <!-- Notification -->
    <div class="notification" id="notification">
        <i class="fas fa-check-circle"></i>
        <span id="notificationText">Login successful!</span>
    </div>

    <!-- Loading Screen -->
    <div class="loading" id="loading">
        <div class="loading-spinner"></div>
        <div class="loading-text">Initializing your journey...</div>
    </div>

    <script>
        // Create particles
        const particlesContainer = document.getElementById('particles');
        const particleCount = 50;

        for (let i = 0; i < particleCount; i++) {
            const particle = document.createElement('div');
            particle.classList.add('particle');
            
            // Random size between 2px and 6px
            const size = Math.random() * 4 + 2;
            particle.style.width = `${size}px`;
            particle.style.height = `${size}px`;
            
            // Random position
            particle.style.left = `${Math.random() * 100}%`;
            particle.style.top = `${Math.random() * 100}%`;
            
            // Random animation duration between 10s and 20s
            const duration = Math.random() * 10 + 10;
            particle.style.animationDuration = `${duration}s`;
            
            // Random animation delay
            particle.style.animationDelay = `${Math.random() * 5}s`;
            
            particlesContainer.appendChild(particle);
        }

        // Language selector functionality
        const languageBtn = document.getElementById('languageBtn');
        const languageDropdown = document.getElementById('languageDropdown');
        const currentLang = document.getElementById('currentLang');
        const languageOptions = document.querySelectorAll('.language-option');

        languageBtn.addEventListener('click', () => {
            languageDropdown.classList.toggle('active');
        });

        languageOptions.forEach(option => {
            option.addEventListener('click', () => {
                const lang = option.getAttribute('data-lang');
                currentLang.textContent = lang.toUpperCase();
                languageDropdown.classList.remove('active');
                
                // Show notification
                showNotification(`Language changed to ${option.textContent.trim()}`, 'success');
            });
        });

        // Close language dropdown when clicking outside
        document.addEventListener('click', (e) => {
            if (!languageBtn.contains(e.target) && !languageDropdown.contains(e.target)) {
                languageDropdown.classList.remove('active');
            }
        });

        // Login form functionality
        const loginForm = document.getElementById('loginForm');
        const loading = document.getElementById('loading');

        loginForm.addEventListener('submit', (e) => {
            e.preventDefault();
            
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            
            // Basic validation
            if (!username || !password) {
                showNotification('Please fill in all fields', 'error');
                return;
            }
            
            // Show loading screen
            loading.classList.add('active');
            
            // Simulate API call
            setTimeout(() => {
                loading.classList.remove('active');
                
                // For demo purposes, accept any non-empty credentials
                showNotification('Login successful! Redirecting to dashboard...', 'success');
                
                // In a real app, you would redirect to the dashboard
                setTimeout(() => {
                    // window.location.href = '/dashboard';
                    console.log('Redirecting to dashboard...');
                }, 2000);
            }, 2000);
        });

        // Notification functionality
        function showNotification(message, type) {
            const notification = document.getElementById('notification');
            const notificationText = document.getElementById('notificationText');
            const icon = notification.querySelector('i');
            
            // Set message
            notificationText.textContent = message;
            
            // Set type and icon
            notification.className = 'notification';
            if (type === 'success') {
                notification.classList.add('success');
                icon.className = 'fas fa-check-circle';
            } else if (type === 'error') {
                notification.classList.add('error');
                icon.className = 'fas fa-exclamation-circle';
            }
            
            // Show notification
            notification.classList.add('show');
            
            // Hide after 3 seconds
            setTimeout(() => {
                notification.classList.remove('show');
            }, 3000);
        }

        // Social login buttons
        const socialBtns = document.querySelectorAll('.social-btn');
        socialBtns.forEach(btn => {
            btn.addEventListener('click', () => {
                const platform = btn.querySelector('i').className.includes('google') ? 'Google' : 
                                btn.querySelector('i').className.includes('microsoft') ? 'Microsoft' : 'Apple';
                
                showNotification(`Connecting with ${platform}...`, 'success');
                
                // Simulate social login
                setTimeout(() => {
                    showNotification(`${platform} login successful!`, 'success');
                }, 1500);
            });
        });

        // Forgot password link
        document.querySelector('.forgot-password').addEventListener('click', (e) => {
            e.preventDefault();
            showNotification('Password reset link sent to your email', 'success');
        });

        // Signup link
        document.querySelector('.signup-link a').addEventListener('click', (e) => {
            e.preventDefault();
            showNotification('Redirecting to signup page...', 'success');
        });
    </script>
</body>
</html>
