<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GitHub Profile Preview</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #0f172a 0%, #1e293b 100%);
            color: #e2e8f0;
            padding: 40px 20px;
            min-height: 100vh;
        }

        .container {
            max-width: 900px;
            margin: 0 auto;
            background: rgba(30, 41, 59, 0.6);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 60px 40px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
            border: 1px solid rgba(148, 163, 184, 0.1);
        }

        h1 {
            text-align: center;
            font-size: 3em;
            background: linear-gradient(135deg, #38bdf8 0%, #9333ea 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 10px;
            animation: fadeInDown 1s ease-out;
        }

        .wave {
            display: inline-block;
            animation: wave 2s infinite;
            transform-origin: 70% 70%;
        }

        @keyframes wave {
            0%, 100% { transform: rotate(0deg); }
            10%, 30% { transform: rotate(14deg); }
            20% { transform: rotate(-8deg); }
            40% { transform: rotate(-4deg); }
            50% { transform: rotate(10deg); }
        }

        h3 {
            text-align: center;
            color: #94a3b8;
            font-weight: 400;
            font-size: 1.3em;
            margin-bottom: 30px;
            animation: fadeInDown 1s ease-out 0.2s both;
        }

        .typing-container {
            text-align: center;
            margin: 30px 0;
            min-height: 60px;
            animation: fadeIn 1s ease-out 0.4s both;
        }

        .typing-text {
            font-family: 'Courier New', monospace;
            font-size: 1.2em;
            color: #38bdf8;
            font-weight: 600;
        }

        .section {
            margin: 50px 0;
            animation: fadeInUp 1s ease-out;
        }

        .section-title {
            font-size: 1.8em;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 3px solid #38bdf8;
            display: inline-block;
            background: linear-gradient(90deg, #38bdf8, #9333ea);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: slideInLeft 0.8s ease-out;
        }

        .about-list {
            list-style: none;
            margin: 20px 0;
        }

        .about-list li {
            padding: 12px 0;
            font-size: 1.1em;
            color: #cbd5e1;
            position: relative;
            padding-left: 30px;
            animation: fadeInLeft 0.8s ease-out;
        }

        .about-list li::before {
            content: "▹";
            position: absolute;
            left: 0;
            color: #38bdf8;
            font-size: 1.5em;
            animation: pulse 2s infinite;
        }

        .tech-stack {
            margin: 30px 0;
        }

        .tech-category {
            margin: 30px 0;
        }

        .tech-category h4 {
            color: #38bdf8;
            margin-bottom: 15px;
            font-size: 1.3em;
            text-align: center;
        }

        .badge-container {
            display: flex;
            flex-wrap: wrap;
            gap: 12px;
            justify-content: center;
            align-items: center;
        }

        .badge {
            transition: all 0.3s ease;
            animation: fadeIn 0.8s ease-out;
            filter: drop-shadow(0 4px 8px rgba(56, 189, 248, 0.3));
        }

        .badge:hover {
            transform: translateY(-5px) scale(1.05);
            filter: drop-shadow(0 8px 16px rgba(56, 189, 248, 0.5));
        }

        .goals-list {
            list-style: none;
            margin: 20px 0;
        }

        .goals-list li {
            padding: 15px;
            margin: 10px 0;
            background: rgba(56, 189, 248, 0.1);
            border-left: 4px solid #38bdf8;
            border-radius: 8px;
            font-size: 1.1em;
            transition: all 0.3s ease;
            animation: fadeInRight 0.8s ease-out;
        }

        .goals-list li:hover {
            background: rgba(56, 189, 248, 0.2);
            transform: translateX(10px);
        }

        .social-links {
            display: flex;
            gap: 20px;
            justify-content: center;
            margin: 30px 0;
        }

        .social-links a {
            transition: all 0.3s ease;
            display: inline-block;
            animation: bounceIn 1s ease-out;
        }

        .social-links a:hover {
            transform: translateY(-8px) rotate(5deg);
        }

        .footer {
            text-align: center;
            margin-top: 60px;
            padding-top: 30px;
            border-top: 2px solid rgba(148, 163, 184, 0.2);
            font-size: 1.1em;
            color: #94a3b8;
            font-style: italic;
            animation: fadeIn 1s ease-out 1s both;
        }

        .particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }

        .particle {
            position: absolute;
            width: 4px;
            height: 4px;
            background: #38bdf8;
            border-radius: 50%;
            opacity: 0;
            animation: float 8s infinite;
        }

        @keyframes float {
            0% {
                transform: translateY(100vh) translateX(0);
                opacity: 0;
            }
            10% {
                opacity: 1;
            }
            90% {
                opacity: 1;
            }
            100% {
                transform: translateY(-100px) translateX(100px);
                opacity: 0;
            }
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
            }
            to {
                opacity: 1;
            }
        }

        @keyframes fadeInDown {
            from {
                opacity: 0;
                transform: translateY(-30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
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

        @keyframes fadeInLeft {
            from {
                opacity: 0;
                transform: translateX(-30px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        @keyframes fadeInRight {
            from {
                opacity: 0;
                transform: translateX(30px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        @keyframes slideInLeft {
            from {
                opacity: 0;
                transform: translateX(-50px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        @keyframes bounceIn {
            0% {
                opacity: 0;
                transform: scale(0.3);
            }
            50% {
                opacity: 1;
                transform: scale(1.05);
            }
            70% {
                transform: scale(0.9);
            }
            100% {
                transform: scale(1);
            }
        }

        @keyframes pulse {
            0%, 100% {
                opacity: 1;
            }
            50% {
                opacity: 0.5;
            }
        }

        hr {
            border: none;
            height: 1px;
            background: linear-gradient(90deg, transparent, #38bdf8, transparent);
            margin: 40px 0;
        }
    </style>
</head>
<body>
    <div class="particles" id="particles"></div>
    
    <div class="container">
        <h1>Hey <span class="wave">👋</span> I am Abhinandan Verma</h1>
        <h3>MCA Student | Aspiring Software Developer 🚀</h3>

        <div class="typing-container">
            <div class="typing-text" id="typingText"></div>
        </div>

        <hr>

        <div class="section">
            <h2 class="section-title">👨‍💻 About Me</h2>
            <ul class="about-list">
                <li>🎓 MCA Student from India</li>
                <li>💻 Passionate about <strong>Software & Web Development</strong></li>
                <li>🧠 Focused on <strong>clean logic, fundamentals & consistency</strong></li>
                <li>🔥 Believe in <em>learning by building projects</em></li>
            </ul>
        </div>

        <hr>

        <div class="section tech-stack">
            <h2 class="section-title">🛠️ Tech Stack</h2>
            
            <div class="tech-category">
                <h4>💻 Programming</h4>
                <div class="badge-container">
                    <img class="badge" src="https://img.shields.io/badge/C-00599C?style=for-the-badge&logo=c&logoColor=white"/>
                    <img class="badge" src="https://img.shields.io/badge/C++-004482?style=for-the-badge&logo=cplusplus&logoColor=white"/>
                    <img class="badge" src="https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white"/>
                    <img class="badge" src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
                </div>
            </div>

            <div class="tech-category">
                <h4>🌐 Web Development</h4>
                <div class="badge-container">
                    <img class="badge" src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white"/>
                    <img class="badge" src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white"/>
                    <img class="badge" src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black"/>
                    <img class="badge" src="https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB"/>
                </div>
            </div>

            <div class="tech-category">
                <h4>🗄️ Database & Tools</h4>
                <div class="badge-container">
                    <img class="badge" src="https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white"/>
                    <img class="badge" src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white"/>
                    <img class="badge" src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white"/>
                    <img class="badge" src="https://img.shields.io/badge/VS%20Code-007ACC?style=for-the-badge&logo=visualstudiocode&logoColor=white"/>
                </div>
            </div>
        </div>

        <hr>

        <div class="section">
            <h2 class="section-title">🎯 Goals</h2>
            <ul class="goals-list">
                <li>✔️ Become a Full-Stack Developer</li>
                <li>✔️ Build real-world projects</li>
                <li>✔️ Strengthen DSA & logic</li>
                <li>✔️ Crack software developer roles</li>
            </ul>
        </div>

        <hr>

        <div class="section">
            <h2 class="section-title">🤝 Connect With Me</h2>
            <div class="social-links">
                <a href="https://www.linkedin.com/in/abhinandan-verma-21a2792bb/" target="_blank">
                    <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"/>
                </a>
                <a href="https://www.instagram.com/abhinandanmaurya10/" target="_blank">
                    <img src="https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white"/>
                </a>
            </div>
        </div>
        <div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:38BDF8,100:9333EA&height=160&text=Thanks+for+visiting!&fontColor=ffffff&fontSize=30" />
</div>

        <div class="footer">
            📌 <em>Learning. Building. Improving. One commit at a time.</em>
        </div>
    </div>

    <script>
        // Typing animation
        const phrases = [
            "Welcome to my GitHub Profile",
            "Learning - Building - Improving",
            "Code Every Day",
            "Let's Build Something Amazing!"
        ];
        let phraseIndex = 0;
        let charIndex = 0;
        let isDeleting = false;
        const typingSpeed = 100;
        const deletingSpeed = 50;
        const pauseTime = 2000;

        function type() {
            const current = phrases[phraseIndex];
            const typingText = document.getElementById('typingText');

            if (isDeleting) {
                typingText.textContent = current.substring(0, charIndex - 1);
                charIndex--;
            } else {
                typingText.textContent = current.substring(0, charIndex + 1);
                charIndex++;
            }

            if (!isDeleting && charIndex === current.length) {
                setTimeout(() => isDeleting = true, pauseTime);
            } else if (isDeleting && charIndex === 0) {
                isDeleting = false;
                phraseIndex = (phraseIndex + 1) % phrases.length;
            }

            const speed = isDeleting ? deletingSpeed : typingSpeed;
            setTimeout(type, speed);
        }

        // Start typing animation
        setTimeout(type, 1000);

        // Create floating particles
        function createParticles() {
            const particlesContainer = document.getElementById('particles');
            const particleCount = 30;

            for (let i = 0; i < particleCount; i++) {
                const particle = document.createElement('div');
                particle.className = 'particle';
                particle.style.left = Math.random() * 100 + '%';
                particle.style.animationDelay = Math.random() * 8 + 's';
                particle.style.animationDuration = (Math.random() * 5 + 5) + 's';
                particlesContainer.appendChild(particle);
            }
        }

        createParticles();

        // Add staggered animation delays to list items
        document.querySelectorAll('.about-list li').forEach((li, index) => {
            li.style.animationDelay = (index * 0.1) + 's';
        });

        document.querySelectorAll('.goals-list li').forEach((li, index) => {
            li.style.animationDelay = (index * 0.1) + 's';
        });

        document.querySelectorAll('.badge').forEach((badge, index) => {
            badge.style.animationDelay = (index * 0.05) + 's';
        });
    </script>
</body>
</html>
