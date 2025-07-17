<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Manish Mir - Software Developer</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js" onerror="console.log('Three.js failed to load')"></script>
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
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        .header {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 40px;
            margin-bottom: 30px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .header::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: linear-gradient(90deg, #667eea, #764ba2, #667eea);
            background-size: 200% 100%;
            animation: shimmer 3s ease-in-out infinite;
        }

        @keyframes shimmer {
            0%, 100% { background-position: 200% 0; }
            50% { background-position: -200% 0; }
        }

        .profile-section {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 40px;
            flex-wrap: wrap;
            position: relative;
        }

        .profile-image {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            background: linear-gradient(135deg, #667eea, #764ba2);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 60px;
            font-weight: bold;
            color: white;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            transition: transform 0.3s ease;
        }

        .profile-image:hover {
            transform: scale(1.05);
        }

        .hero-3d-container {
            position: absolute;
            top: -50px;
            right: -50px;
            width: 300px;
            height: 200px;
            z-index: 1;
        }

        #hero-3d-canvas {
            width: 100%;
            height: 100%;
            opacity: 0.8;
        }

        .profile-info h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
            background: linear-gradient(135deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .profile-info .title {
            font-size: 1.3rem;
            color: #666;
            margin-bottom: 20px;
        }

        .contact-info {
            display: flex;
            gap: 30px;
            justify-content: center;
            flex-wrap: wrap;
            margin-top: 20px;
        }

        .contact-item {
            display: flex;
            align-items: center;
            gap: 8px;
            padding: 8px 16px;
            background: rgba(102, 126, 234, 0.1);
            border-radius: 25px;
            text-decoration: none;
            color: #667eea;
            transition: all 0.3s ease;
            font-size: 0.9rem;
        }

        .contact-item:hover {
            background: rgba(102, 126, 234, 0.2);
            transform: translateY(-2px);
        }

        .dashboard {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 30px;
            margin-bottom: 30px;
        }

        .card {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 30px 60px rgba(0, 0, 0, 0.15);
        }

        .card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 3px;
            background: linear-gradient(90deg, #667eea, #764ba2);
        }

        .skills-3d-container {
            position: absolute;
            top: 10px;
            right: 10px;
            width: 120px;
            height: 120px;
            z-index: 1;
            pointer-events: none;
        }

        .skills-3d-canvas {
            width: 100%;
            height: 100%;
            opacity: 0.3;
        }

        .projects-3d-container {
            position: absolute;
            bottom: 10px;
            right: 10px;
            width: 100px;
            height: 100px;
            z-index: 1;
            pointer-events: none;
        }

        .projects-3d-canvas {
            width: 100%;
            height: 100%;
            opacity: 0.4;
        }

        .card-header {
            display: flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 20px;
        }

        .card-icon {
            width: 50px;
            height: 50px;
            border-radius: 12px;
            background: linear-gradient(135deg, #667eea, #764ba2);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 20px;
            font-weight: bold;
        }

        .card-title {
            font-size: 1.4rem;
            font-weight: 600;
            color: #333;
        }

        .about-text {
            color: #666;
            line-height: 1.8;
            font-size: 1rem;
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
        }

        .skill-category {
            background: rgba(102, 126, 234, 0.05);
            padding: 20px;
            border-radius: 15px;
            border-left: 4px solid #667eea;
        }

        .skill-category h4 {
            color: #667eea;
            margin-bottom: 10px;
            font-size: 1.1rem;
        }

        .skill-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
        }

        .skill-tag {
            background: rgba(102, 126, 234, 0.1);
            color: #667eea;
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 500;
        }

        .timeline {
            position: relative;
            padding-left: 30px;
        }

        .timeline::before {
            content: '';
            position: absolute;
            left: 15px;
            top: 0;
            bottom: 0;
            width: 2px;
            background: linear-gradient(to bottom, #667eea, #764ba2);
        }

        .timeline-item {
            position: relative;
            margin-bottom: 30px;
            padding-left: 30px;
        }

        .timeline-item::before {
            content: '';
            position: absolute;
            left: -37px;
            top: 5px;
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: #667eea;
            border: 3px solid white;
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.2);
        }

        .timeline-title {
            font-weight: 600;
            color: #333;
            margin-bottom: 5px;
        }

        .timeline-company {
            color: #667eea;
            font-weight: 500;
            margin-bottom: 5px;
        }

        .timeline-date {
            color: #999;
            font-size: 0.9rem;
            margin-bottom: 10px;
        }

        .timeline-desc {
            color: #666;
            line-height: 1.6;
        }

        .timeline-desc ul {
            margin-left: 20px;
        }

        .timeline-desc li {
            margin-bottom: 5px;
        }

        .project-grid {
            display: grid;
            gap: 20px;
        }

        .project-item {
            background: rgba(102, 126, 234, 0.05);
            padding: 20px;
            border-radius: 15px;
            border-left: 4px solid #667eea;
            transition: all 0.3s ease;
        }

        .project-item:hover {
            background: rgba(102, 126, 234, 0.1);
            transform: translateX(5px);
        }

        .project-title {
            font-weight: 600;
            color: #333;
            margin-bottom: 10px;
            font-size: 1.1rem;
        }

        .project-desc {
            color: #666;
            line-height: 1.6;
        }

        .cert-item {
            background: rgba(102, 126, 234, 0.05);
            padding: 15px 20px;
            border-radius: 10px;
            margin-bottom: 15px;
            border-left: 4px solid #667eea;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .cert-title {
            font-weight: 600;
            color: #333;
        }

        .cert-year {
            color: #667eea;
            font-weight: 500;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .stat-item {
            text-align: center;
            padding: 20px;
            background: rgba(102, 126, 234, 0.05);
            border-radius: 15px;
        }

        .stat-number {
            font-size: 2rem;
            font-weight: bold;
            color: #667eea;
            margin-bottom: 5px;
        }

        .stat-label {
            color: #666;
            font-size: 0.9rem;
        }

        .footer {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 30px;
            text-align: center;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
        }

        .footer-links {
            display: flex;
            justify-content: center;
            gap: 30px;
            margin-bottom: 20px;
            flex-wrap: wrap;
        }

        .footer-link {
            color: #667eea;
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s ease;
        }

        .footer-link:hover {
            color: #764ba2;
        }

        @media (max-width: 768px) {
            .profile-section {
                flex-direction: column;
                text-align: center;
            }

            .hero-3d-container {
                display: none;
            }

            .skills-3d-container,
            .projects-3d-container {
                display: none;
            }

            .contact-info {
                flex-direction: column;
                align-items: center;
                gap: 15px;
            }

            .dashboard {
                grid-template-columns: 1fr;
            }

            .skills-grid {
                grid-template-columns: 1fr;
            }

            .stats-grid {
                grid-template-columns: repeat(2, 1fr);
            }

            .footer-links {
                flex-direction: column;
                gap: 15px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Header Section -->
        <div class="header">
            <div class="profile-section">
                <div class="hero-3d-container">
                    <canvas id="hero-3d-canvas"></canvas>
                </div>
                <div class="profile-image">
                    MM
                </div>
                <div class="profile-info">
                    <h1>Manish Mir</h1>
                    <div class="title">Software Developer & AI Enthusiast</div>
                    <div class="contact-info">
                        <a href="mailto:manishmir01@gmail.com" class="contact-item">
                            📧 manishmir01@gmail.com
                        </a>
                        <a href="tel:+91-6353760688" class="contact-item">
                            📱 +91-6353760688
                        </a>
                        <a href="https://www.linkedin.com/in/manish-mir/" class="contact-item">
                            💼 LinkedIn
                        </a>
                        <a href="https://github.com/ManishMir" class="contact-item">
                            💻 GitHub
                        </a>
                        <a href="https://leetcode.com/u/Manishmir/" class="contact-item">
                            🏆 LeetCode
                        </a>
                    </div>
                </div>
            </div>
        </div>

        <!-- Dashboard -->
        <div class="dashboard">
            <!-- About Me Card -->
            <div class="card">
                <div class="card-header">
                    <div class="card-icon">👨‍💻</div>
                    <h3 class="card-title">About Me</h3>
                </div>
                <div class="about-text">
                    A dedicated and hardworking individual with a strong desire to grow in the tech field. I thrive on problem-solving, adaptability, and continuous learning. Passionate about software development, AI, and innovation. Seeking opportunities to contribute, learn, and evolve into a proficient software professional.
                </div>
                <div class="stats-grid">
                    <div class="stat-item">
                        <div class="stat-number">2+</div>
                        <div class="stat-label">Years Experience</div>
                    </div>
                    <div class="stat-item">
                        <div class="stat-number">5+</div>
                        <div class="stat-label">Programming Languages</div>
                    </div>
                    <div class="stat-item">
                        <div class="stat-number">3+</div>
                        <div class="stat-label">Major Projects</div>
                    </div>
                </div>
            </div>

            <!-- Technical Skills Card -->
            <div class="card">
                <div class="skills-3d-container">
                    <canvas class="skills-3d-canvas" id="skills-3d-canvas"></canvas>
                </div>
                <div class="card-header">
                    <div class="card-icon">🛠️</div>
                    <h3 class="card-title">Technical Skills</h3>
                </div>
                <div class="skills-grid">
                    <div class="skill-category">
                        <h4>Programming Languages</h4>
                        <div class="skill-tags">
                            <span class="skill-tag">Java</span>
                            <span class="skill-tag">C#</span>
                            <span class="skill-tag">Python</span>
                            <span class="skill-tag">JavaScript</span>
                            <span class="skill-tag">SQL</span>
                        </div>
                    </div>
                    <div class="skill-category">
                        <h4>Frameworks & Tools</h4>
                        <div class="skill-tags">
                            <span class="skill-tag">ASP.NET</span>
                            <span class="skill-tag">React Native</span>
                            <span class="skill-tag">Git</span>
                            <span class="skill-tag">VS Code</span>
                            <span class="skill-tag">N8N</span>
                        </div>
                    </div>
                    <div class="skill-category">
                        <h4>Core Competencies</h4>
                        <div class="skill-tags">
                            <span class="skill-tag">Debugging</span>
                            <span class="skill-tag">Unit Testing</span>
                            <span class="skill-tag">Problem Solving</span>
                            <span class="skill-tag">Teamwork</span>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Education Card -->
            <div class="card">
                <div class="card-header">
                    <div class="card-icon">🎓</div>
                    <h3 class="card-title">Education</h3>
                </div>
                <div class="skills-3d-container">
                    <canvas class="skills-3d-canvas" id="skills-3d-canvas"></canvas>
                </div>
                <div class="timeline">
                    <div class="timeline-item">
                        <div class="timeline-title">Master of Computer Application (AI)</div>
                        <div class="timeline-company">Parul University, Vadodara, Gujarat</div>
                        <div class="timeline-date">2023 – 2025</div>
                        <div class="timeline-desc">
                            Specialized in Artificial Intelligence with focus on machine learning, data structures, and advanced programming concepts.
                        </div>
                    </div>
                    <div class="timeline-item">
                        <div class="timeline-title">Bachelor of Computer Application</div>
                        <div class="timeline-company">Sardar Patel University, Anand, Gujarat</div>
                        <div class="timeline-date">2020 – 2023</div>
                        <div class="timeline-desc">
                            Foundation in computer science principles, programming languages, and software development methodologies.
                        </div>
                    </div>
                </div>
            </div>

            <!-- Experience Card -->
            <div class="card">
                <div class="card-header">
                    <div class="card-icon">💼</div>
                    <h3 class="card-title">Professional Experience</h3>
                </div>
                <div class="timeline">
                    <div class="timeline-item">
                        <div class="timeline-title">DSA Trainee</div>
                        <div class="timeline-company">AccioJob | Remote</div>
                        <div class="timeline-date">Sep 2024 – Apr 2025</div>
                        <div class="timeline-desc">
                            <ul>
                                <li>Intensive training in Data Structures, Algorithms, and problem-solving</li>
                                <li>Regular participation in coding contests and problem-solving assessments</li>
                            </ul>
                        </div>
                    </div>
                    <div class="timeline-item">
                        <div class="timeline-title">Dotnet Developer Intern</div>
                        <div class="timeline-company">Memo TechnoLabs | Vadodara, Gujarat</div>
                        <div class="timeline-date">Dec 2024 – May 2025</div>
                        <div class="timeline-desc">
                            <ul>
                                <li>Built cross-platform website using C# and ASP.NET</li>
                                <li>Focused on UI/UX design, performance optimization, and third-party integrations</li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Projects Card -->
            <div class="card">
                <div class="projects-3d-container">
                    <canvas class="projects-3d-canvas" id="projects-3d-canvas"></canvas>
                </div>
                <div class="card-header">
                    <div class="card-icon">🚀</div>
                    <h3 class="card-title">Featured Projects</h3>
                </div>
                <div class="project-grid">
                    <div class="project-item">
                        <div class="project-title">E-Voting System (2023)</div>
                        <div class="project-desc">
                            A secure, web-based online voting system that enables users to cast votes electronically, reducing the need for physical polling stations and manual counting.
                        </div>
                        <div class="skill-tags">
                            <span class="skill-tag">Asp.net</span>
                            <span class="skill-tag">SQL</span>
                            <span class="skill-tag">BootStraip</span>
                            <span class="skill-tag">Html</span>
                            <span class="skill-tag">Agile</span>
                        </div>
                    </div>
                    <div class="project-item">
                        <div class="project-title">Emotion Detection System</div>
                        <div class="project-desc">
                            Advanced system that detects emotions and hand gestures, with the ability to open specific applications like Instagram, perform searches, and provide interactive entertainment features.
                        </div>
                        <div class="skill-tags">
                            <span class="skill-tag">Python</span>
                            <span class="skill-tag">openCV</span>
                            <span class="skill-tag"></span>
                            <span class="skill-tag">Html</span>
                            <span class="skill-tag">Css</span>
                        </div>
                    </div>
                    <div class="project-item">
                        <div class="project-title">AI Social Media Agent</div>
                        <div class="project-desc">
                            Built an AI-powered social media agent using n8n to auto-generate videos with Google Veo3, save to Drive, and upload to YouTube with captions. Integrated ChatGPT, Google APIs, and automation logic.
                        </div>
                        <div class="skill-tags">
                            <span class="skill-tag">N8N</span>
                            <span class="skill-tag">Google Veo3</span>
                            <span class="skill-tag">Google Drive</span>
                            <span class="skill-tag">ChatGPT</span>
                            <span class="skill-tag">YouTube</span>
                        </div>
                    </div>
                        <div class="project-item">
                        <div class="project-title">AI HR Agent</div>
                        <div class="project-desc">
                           Built an AI-powered HR agent using n8n, OpenAI GPT-4o, and WhatsApp API to automate leave requests, attendance, FAQs, and candidate shortlisting.
                            Integrated with Google Sheets, Gmail, and Calendar for seamless end-to-end HR operations.
                            Impact:
                            This system dramatically reduces HR workload by automating repetitive tasks and enabling intelligent decision-making, all in a scalable, modular architecture.
                        </div>
                        <div class="skill-tags">
                            <span class="skill-tag">N8N</span>
                            <span class="skill-tag">WhatsApp API</span>
                            <span class="skill-tag">OpenAI GPT-4o</span>
                            <span class="skill-tag">Supabase Vector Store</span>
                            <span class="skill-tag">Google Sheets</span>
                            <span class="skill-tag">Calendar</span>
                            <span class="skill-tag">Gmail APIs</span>
                            <span class="skill-tag">LangChain for parsing & decision making</span>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Certifications Card -->
            <div class="card">
                <div class="card-header">
                    <div class="card-icon">🏅</div>
                    <h3 class="card-title">Certifications</h3>
                </div>
                <div class="cert-item">
                    <div class="cert-title">Introduction to AI</div>
                    <div class="cert-year">2023</div>
                </div>
                <div class="cert-item">
                    <div class="cert-title">Java Training</div>
                    <div class="cert-year">2022</div>
                </div>
            </div>
        </div>

        <!-- Footer -->
        <div class="footer">
            <div class="footer-links">
                <a href="mailto:manishmir01@gmail.com" class="footer-link">Email</a>
                <a href="https://www.linkedin.com/in/manish-mir/" class="footer-link">LinkedIn</a>
                <a href="https://github.com/ManishMir" class="footer-link">GitHub</a>
                <a href="https://leetcode.com/u/Manishmir/" class="footer-link">LeetCode</a>
            </div>
            <p style="color: #666; margin-top: 20px;">
                © 2025 Manish Mir. Passionate about technology and continuous learning.
            </p>
        </div>
    </div>

    <script>
        // 3D Scene Setup
        function create3DScene(canvasId, sceneType) {
            try {
                const canvas = document.getElementById(canvasId);
                if (!canvas) return;

                const scene = new THREE.Scene();
                const camera = new THREE.PerspectiveCamera(75, canvas.offsetWidth / canvas.offsetHeight, 0.1, 1000);
                const renderer = new THREE.WebGLRenderer({ canvas: canvas, alpha: true, antialias: true });
                renderer.setSize(canvas.offsetWidth, canvas.offsetHeight);
                renderer.setClearColor(0x000000, 0);

                // Lighting
                const ambientLight = new THREE.AmbientLight(0x404040, 0.4);
                scene.add(ambientLight);
                const directionalLight = new THREE.DirectionalLight(0xffffff, 0.8);
                directionalLight.position.set(1, 1, 1);
                scene.add(directionalLight);

                let objects = [];

                if (sceneType === 'hero') {
                    // Create laptop-like object
                    const laptopGroup = new THREE.Group();
                    
                    // Laptop base
                    const baseGeometry = new THREE.BoxGeometry(2, 0.1, 1.5);
                    const baseMaterial = new THREE.MeshPhongMaterial({ color: 0x333333 });
                    const base = new THREE.Mesh(baseGeometry, baseMaterial);
                    laptopGroup.add(base);

                    // Laptop screen
                    const screenGeometry = new THREE.BoxGeometry(1.8, 1.2, 0.05);
                    const screenMaterial = new THREE.MeshPhongMaterial({ color: 0x1a1a1a });
                    const screen = new THREE.Mesh(screenGeometry, screenMaterial);
                    screen.position.set(0, 0.6, -0.7);
                    screen.rotation.x = -Math.PI / 8;
                    laptopGroup.add(screen);

                    // Screen glow effect
                    const screenGlowGeometry = new THREE.BoxGeometry(1.6, 1.0, 0.01);
                    const screenGlowMaterial = new THREE.MeshPhongMaterial({ 
                        color: 0x667eea, 
                        emissive: 0x334455,
                        transparent: true,
                        opacity: 0.8
                    });
                    const screenGlow = new THREE.Mesh(screenGlowGeometry, screenGlowMaterial);
                    screenGlow.position.set(0, 0.6, -0.69);
                    screenGlow.rotation.x = -Math.PI / 8;
                    laptopGroup.add(screenGlow);

                    // Floating particles
                    const particleGeometry = new THREE.SphereGeometry(0.02, 8, 8);
                    const particleMaterial = new THREE.MeshPhongMaterial({ 
                        color: 0x667eea,
                        emissive: 0x334455,
                        transparent: true,
                        opacity: 0.8
                    });

                    for (let i = 0; i < 20; i++) {
                        const particle = new THREE.Mesh(particleGeometry, particleMaterial);
                        particle.position.set(
                            (Math.random() - 0.5) * 6,
                            (Math.random() - 0.5) * 4,
                            (Math.random() - 0.5) * 4
                        );
                        particle.userData = {
                            velocity: new THREE.Vector3(
                                (Math.random() - 0.5) * 0.02,
                                (Math.random() - 0.5) * 0.02,
                                (Math.random() - 0.5) * 0.02
                            ),
                            originalPosition: particle.position.clone()
                        };
                        objects.push(particle);
                        scene.add(particle);
                    }

                    laptopGroup.position.set(0, 0, 0);
                    scene.add(laptopGroup);
                    objects.push(laptopGroup);

                    camera.position.set(0, 2, 4);
                    camera.lookAt(0, 0, 0);

                } else if (sceneType === 'skills') {
                    // Create rotating geometric shapes representing skills
                    const geometries = [
                        new THREE.OctahedronGeometry(0.3),
                        new THREE.TetrahedronGeometry(0.3),
                        new THREE.IcosahedronGeometry(0.3)
                    ];

                    const materials = [
                        new THREE.MeshPhongMaterial({ color: 0x667eea, transparent: true, opacity: 0.8 }),
                        new THREE.MeshPhongMaterial({ color: 0x764ba2, transparent: true, opacity: 0.8 }),
                        new THREE.MeshPhongMaterial({ color: 0x48c6ef, transparent: true, opacity: 0.8 })
                    ];

                    for (let i = 0; i < 3; i++) {
                        const mesh = new THREE.Mesh(geometries[i], materials[i]);
                        mesh.position.set(
                            Math.cos(i * Math.PI * 2 / 3) * 0.5,
                            Math.sin(i * Math.PI * 2 / 3) * 0.5,
                            0
                        );
                        objects.push(mesh);
                        scene.add(mesh);
                    }

                    camera.position.set(0, 0, 2);
                    camera.lookAt(0, 0, 0);

                } else if (sceneType === 'projects') {
                    // Create floating cubes representing projects
                    const projectGeometry = new THREE.BoxGeometry(0.2, 0.2, 0.2);
                    const projectMaterials = [
                        new THREE.MeshPhongMaterial({ color: 0x667eea, transparent: true, opacity: 0.9 }),
                        new THREE.MeshPhongMaterial({ color: 0x764ba2, transparent: true, opacity: 0.9 }),
                        new THREE.MeshPhongMaterial({ color: 0x48c6ef, transparent: true, opacity: 0.9 })
                    ];

                    for (let i = 0; i < 6; i++) {
                        const cube = new THREE.Mesh(projectGeometry, projectMaterials[i % 3]);
                        cube.position.set(
                            (Math.random() - 0.5) * 2,
                            (Math.random() - 0.5) * 2,
                            (Math.random() - 0.5) * 2
                        );
                        cube.userData = {
                            rotationSpeed: new THREE.Vector3(
                                (Math.random() - 0.5) * 0.02,
                                (Math.random() - 0.5) * 0.02,
                                (Math.random() - 0.5) * 0.02
                            )
                        };
                        objects.push(cube);
                        scene.add(cube);
                    }

                    camera.position.set(0, 0, 3);
                    camera.lookAt(0, 0, 0);
                }

                // Animation loop
                function animate() {
                    requestAnimationFrame(animate);

                    if (sceneType === 'hero') {
                        // Rotate laptop
                        if (objects[0]) {
                            objects[0].rotation.y += 0.005;
                        }
                        
                        // Animate particles
                        for (let i = 1; i < objects.length; i++) {
                            const particle = objects[i];
                            if (particle.userData) {
                                particle.position.add(particle.userData.velocity);
                                
                                // Bounce particles
                                if (Math.abs(particle.position.x) > 3) particle.userData.velocity.x *= -1;
                                if (Math.abs(particle.position.y) > 2) particle.userData.velocity.y *= -1;
                                if (Math.abs(particle.position.z) > 2) particle.userData.velocity.z *= -1;
                            }
                        }

                    } else if (sceneType === 'skills') {
                        // Rotate skill shapes
                        objects.forEach((obj, index) => {
                            obj.rotation.x += 0.01;
                            obj.rotation.y += 0.01;
                            obj.position.y = Math.sin(Date.now() * 0.001 + index) * 0.2;
                        });

                    } else if (sceneType === 'projects') {
                        // Rotate project cubes
                        objects.forEach((cube) => {
                            if (cube.userData.rotationSpeed) {
                                cube.rotation.x += cube.userData.rotationSpeed.x;
                                cube.rotation.y += cube.userData.rotationSpeed.y;
                                cube.rotation.z += cube.userData.rotationSpeed.z;
                            }
                        });
                    }

                    renderer.render(scene, camera);
                }

                animate();

                // Handle resize
                window.addEventListener('resize', () => {
                    if (canvas.offsetWidth && canvas.offsetHeight) {
                        camera.aspect = canvas.offsetWidth / canvas.offsetHeight;
                        camera.updateProjectionMatrix();
                        renderer.setSize(canvas.offsetWidth, canvas.offsetHeight);
                    }
                });

            } catch (error) {
                console.log('3D scene creation failed:', error);
            }
        }

        // Initialize 3D scenes when page loads
        window.addEventListener('load', () => {
            setTimeout(() => {
                create3DScene('hero-3d-canvas', 'hero');
                create3DScene('skills-3d-canvas', 'skills');
                create3DScene('projects-3d-canvas', 'projects');
            }, 1000);
        });
    </script>
</body>
</html>
