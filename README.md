<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portfolio - Data Analytics Developer</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --bg-primary: #0a0118;
            --bg-secondary: #150428;
            --bg-card: #1a0a2e;
            --accent-purple: #a855f7;
            --accent-pink: #ec4899;
            --accent-violet: #8b5cf6;
            --text-primary: #ffffff;
            --text-secondary: #c4b5fd;
            --border-color: rgba(168, 85, 247, 0.2);
        }

        body {
            font-family: 'Inter', sans-serif;
            background: linear-gradient(135deg, var(--bg-primary) 0%, var(--bg-secondary) 100%);
            color: var(--text-primary);
            min-height: 100vh;
            padding: 2rem;
            position: relative;
            overflow-x: hidden;
        }

        body::before {
            content: '';
            position: fixed;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(168, 85, 247, 0.1) 1px, transparent 1px);
            background-size: 50px 50px;
            animation: moveGrid 20s linear infinite;
            z-index: 0;
            pointer-events: none;
        }

        @keyframes moveGrid {
            0% { transform: translate(0, 0); }
            100% { transform: translate(50px, 50px); }
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            position: relative;
            z-index: 1;
        }

        /* Header */
        .header {
            background: linear-gradient(135deg, rgba(139, 92, 246, 0.1) 0%, rgba(168, 85, 247, 0.05) 100%);
            border: 1px solid var(--border-color);
            border-radius: 24px;
            padding: 3rem;
            margin-bottom: 2rem;
            backdrop-filter: blur(10px);
            box-shadow: 0 8px 32px rgba(168, 85, 247, 0.2);
            position: relative;
            overflow: hidden;
        }

        .header::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 2px;
            background: linear-gradient(90deg, transparent, var(--accent-purple), transparent);
            animation: shimmer 3s linear infinite;
        }

        @keyframes shimmer {
            0% { transform: translateX(-100%); }
            100% { transform: translateX(100%); }
        }

        .profile-section {
            display: flex;
            align-items: center;
            gap: 2rem;
            margin-bottom: 2rem;
        }

        .avatar {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            border: 4px solid var(--accent-purple);
            background: linear-gradient(135deg, var(--accent-purple), var(--accent-pink));
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            box-shadow: 0 0 30px rgba(168, 85, 247, 0.5);
            animation: pulse 2s ease-in-out infinite;
        }

        @keyframes pulse {
            0%, 100% { box-shadow: 0 0 30px rgba(168, 85, 247, 0.5); }
            50% { box-shadow: 0 0 50px rgba(168, 85, 247, 0.8); }
        }

        .profile-info h1 {
            font-size: 2.5rem;
            font-weight: 800;
            background: linear-gradient(135deg, var(--accent-purple), var(--accent-pink));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 0.5rem;
        }

        .profile-info .subtitle {
            font-size: 1.2rem;
            color: var(--text-secondary);
            margin-bottom: 0.5rem;
        }

        .profile-info .education {
            font-size: 0.95rem;
            color: var(--text-secondary);
            opacity: 0.8;
        }

        .typing-text {
            font-size: 1.1rem;
            color: var(--accent-purple);
            font-weight: 600;
            min-height: 30px;
        }

        .typing-cursor {
            animation: blink 1s step-end infinite;
        }

        @keyframes blink {
            50% { opacity: 0; }
        }

        /* Grid Layout */
        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 1.5rem;
            margin-bottom: 1.5rem;
        }

        .card {
            background: linear-gradient(135deg, rgba(26, 10, 46, 0.8) 0%, rgba(21, 4, 40, 0.6) 100%);
            border: 1px solid var(--border-color);
            border-radius: 20px;
            padding: 2rem;
            backdrop-filter: blur(10px);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, rgba(168, 85, 247, 0.1) 0%, transparent 100%);
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        .card:hover::before {
            opacity: 1;
        }

        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 12px 40px rgba(168, 85, 247, 0.3);
            border-color: var(--accent-purple);
        }

        .card-title {
            font-size: 1.4rem;
            font-weight: 700;
            margin-bottom: 1.5rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .card-icon {
            width: 32px;
            height: 32px;
            background: linear-gradient(135deg, var(--accent-purple), var(--accent-pink));
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.2rem;
        }

        /* Skills */
        .skills-grid {
            display: grid;
            gap: 1rem;
        }

        .skill-category {
            margin-bottom: 1.5rem;
        }

        .skill-category h3 {
            font-size: 1rem;
            color: var(--accent-purple);
            margin-bottom: 0.8rem;
            font-weight: 600;
        }

        .skill-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
        }

        .skill-tag {
            background: rgba(168, 85, 247, 0.15);
            border: 1px solid rgba(168, 85, 247, 0.3);
            padding: 0.5rem 1rem;
            border-radius: 12px;
            font-size: 0.85rem;
            color: var(--text-secondary);
            transition: all 0.3s ease;
            cursor: default;
        }

        .skill-tag:hover {
            background: rgba(168, 85, 247, 0.3);
            border-color: var(--accent-purple);
            transform: translateY(-2px);
            color: var(--text-primary);
        }

        /* Chart */
        .chart-container {
            height: 200px;
            display: flex;
            align-items: flex-end;
            gap: 1rem;
            margin-bottom: 1rem;
        }

        .bar {
            flex: 1;
            background: linear-gradient(to top, var(--accent-purple), var(--accent-pink));
            border-radius: 8px 8px 0 0;
            position: relative;
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .bar:hover {
            filter: brightness(1.2);
            transform: scaleY(1.05);
        }

        .bar::after {
            content: attr(data-label);
            position: absolute;
            bottom: -25px;
            left: 50%;
            transform: translateX(-50%);
            font-size: 0.75rem;
            color: var(--text-secondary);
            white-space: nowrap;
        }

        /* Progress Circles */
        .progress-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 1.5rem;
        }

        .progress-item {
            text-align: center;
        }

        .progress-circle {
            width: 100px;
            height: 100px;
            margin: 0 auto 1rem;
            position: relative;
        }

        .progress-circle svg {
            transform: rotate(-90deg);
        }

        .progress-circle circle {
            fill: none;
            stroke-width: 8;
        }

        .progress-bg {
            stroke: rgba(168, 85, 247, 0.1);
        }

        .progress-bar {
            stroke: url(#gradient);
            stroke-linecap: round;
            transition: stroke-dashoffset 1s ease;
        }

        .progress-text {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 1.2rem;
            font-weight: 700;
            color: var(--accent-purple);
        }

        .progress-label {
            font-size: 0.9rem;
            color: var(--text-secondary);
        }

        /* Projects */
        .project-item {
            background: rgba(168, 85, 247, 0.05);
            border: 1px solid rgba(168, 85, 247, 0.2);
            border-radius: 12px;
            padding: 1rem;
            margin-bottom: 1rem;
            transition: all 0.3s ease;
        }

        .project-item:hover {
            background: rgba(168, 85, 247, 0.1);
            border-color: var(--accent-purple);
            transform: translateX(5px);
        }

        .project-title {
            font-weight: 600;
            margin-bottom: 0.5rem;
            color: var(--text-primary);
        }

        .project-description {
            font-size: 0.85rem;
            color: var(--text-secondary);
            line-height: 1.5;
        }

        /* Stats */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 1rem;
            margin-bottom: 1rem;
        }

        .stat-item {
            text-align: center;
            padding: 1rem;
            background: rgba(168, 85, 247, 0.05);
            border-radius: 12px;
            border: 1px solid rgba(168, 85, 247, 0.2);
            transition: all 0.3s ease;
        }

        .stat-item:hover {
            background: rgba(168, 85, 247, 0.15);
            transform: scale(1.05);
        }

        .stat-number {
            font-size: 2rem;
            font-weight: 800;
            background: linear-gradient(135deg, var(--accent-purple), var(--accent-pink));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .stat-label {
            font-size: 0.85rem;
            color: var(--text-secondary);
            margin-top: 0.5rem;
        }

        /* Contact */
        .contact-grid {
            display: grid;
            gap: 1rem;
        }

        .contact-item {
            display: flex;
            align-items: center;
            gap: 1rem;
            padding: 1rem;
            background: rgba(168, 85, 247, 0.05);
            border-radius: 12px;
            border: 1px solid rgba(168, 85, 247, 0.2);
            transition: all 0.3s ease;
            text-decoration: none;
            color: var(--text-primary);
        }

        .contact-item:hover {
            background: rgba(168, 85, 247, 0.15);
            border-color: var(--accent-purple);
            transform: translateX(5px);
        }

        .contact-icon {
            width: 40px;
            height: 40px;
            background: linear-gradient(135deg, var(--accent-purple), var(--accent-pink));
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.2rem;
        }

        /* Footer */
        .footer {
            text-align: center;
            padding: 2rem;
            color: var(--text-secondary);
            font-size: 0.9rem;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .profile-section {
                flex-direction: column;
                text-align: center;
            }

            .profile-info h1 {
                font-size: 2rem;
            }

            .grid {
                grid-template-columns: 1fr;
            }

            .stats-grid {
                grid-template-columns: 1fr;
            }

            .progress-grid {
                grid-template-columns: 1fr;
            }
        }

        /* Animation for page load */
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

        .card {
            animation: fadeInUp 0.6s ease forwards;
            opacity: 0;
        }

        .card:nth-child(1) { animation-delay: 0.1s; }
        .card:nth-child(2) { animation-delay: 0.2s; }
        .card:nth-child(3) { animation-delay: 0.3s; }
        .card:nth-child(4) { animation-delay: 0.4s; }
        .card:nth-child(5) { animation-delay: 0.5s; }
        .card:nth-child(6) { animation-delay: 0.6s; }
    </style>
</head>
<body>
    <div class="container">
        <!-- Header -->
        <div class="header">
            <div class="profile-section">
                <div class="avatar">👩‍💻</div>
                <div class="profile-info">
                    <h1>Tu Nombre</h1>
                    <div class="subtitle">Data Analytics Developer</div>
                    <div class="education">🎓 Estudiante de Administración de Sistemas Informáticos | 9º Semestre</div>
                </div>
            </div>
            <div class="typing-text" id="typingText"></div>
        </div>

        <!-- Stats Grid -->
        <div class="stats-grid">
            <div class="stat-item">
                <div class="stat-number">5+</div>
                <div class="stat-label">Lenguajes</div>
            </div>
            <div class="stat-item">
                <div class="stat-number">10+</div>
                <div class="stat-label">Proyectos</div>
            </div>
            <div class="stat-item">
                <div class="stat-number">9º</div>
                <div class="stat-label">Semestre</div>
            </div>
        </div>

        <!-- Main Grid -->
        <div class="grid">
            <!-- Skills Card -->
            <div class="card">
                <div class="card-title">
                    <div class="card-icon">💻</div>
                    Stack Tecnológico
                </div>
                <div class="skills-grid">
                    <div class="skill-category">
                        <h3>📊 Análisis de Datos</h3>
                        <div class="skill-tags">
                            <span class="skill-tag">Python</span>
                            <span class="skill-tag">Pandas</span>
                            <span class="skill-tag">NumPy</span>
                            <span class="skill-tag">Matplotlib</span>
                            <span class="skill-tag">Seaborn</span>
                        </div>
                    </div>
                    <div class="skill-category">
                        <h3>📈 Visualización</h3>
                        <div class="skill-tags">
                            <span class="skill-tag">Power BI</span>
                            <span class="skill-tag">Plotly</span>
                            <span class="skill-tag">Tableau</span>
                        </div>
                    </div>
                    <div class="skill-category">
                        <h3>💾 Lenguajes</h3>
                        <div class="skill-tags">
                            <span class="skill-tag">C++</span>
                            <span class="skill-tag">Java</span>
                            <span class="skill-tag">JavaScript</span>
                            <span class="skill-tag">PHP</span>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Experience Chart -->
            <div class="card">
                <div class="card-title">
                    <div class="card-icon">📊</div>
                    Nivel de Experiencia
                </div>
                <div class="chart-container">
                    <div class="bar" style="height: 85%;" data-label="Python"></div>
                    <div class="bar" style="height: 70%;" data-label="Power BI"></div>
                    <div class="bar" style="height: 80%;" data-label="Web Dev"></div>
                    <div class="bar" style="height: 75%;" data-label="SQL"></div>
                    <div class="bar" style="height: 65%;" data-label="Pipelines"></div>
                </div>
            </div>

            <!-- Projects -->
            <div class="card">
                <div class="card-title">
                    <div class="card-icon">🚀</div>
                    Proyectos Destacados
                </div>
                <div class="project-item">
                    <div class="project-title">📊 Dashboards Interactivos</div>
                    <div class="project-description">Desarrollo de dashboards en Power BI para análisis empresarial y toma de decisiones basada en datos</div>
                </div>
                <div class="project-item">
                    <div class="project-title">🔄 Pipeline de Datos ETL</div>
                    <div class="project-description">Automatización de procesos de extracción, transformación y carga de datos con Python</div>
                </div>
                <div class="project-item">
                    <div class="project-title">🌐 Aplicaciones Web</div>
                    <div class="project-description">Desarrollo de sitios web modernos con análisis integrado y visualización en tiempo real</div>
                </div>
            </div>

            <!-- Progress Circles -->
            <div class="card">
                <div class="card-title">
                    <div class="card-icon">🎯</div>
                    Competencias Principales
                </div>
                <div class="progress-grid">
                    <div class="progress-item">
                        <div class="progress-circle">
                            <svg width="100" height="100">
                                <defs>
                                    <linearGradient id="gradient1" x1="0%" y1="0%" x2="100%" y2="100%">
                                        <stop offset="0%" style="stop-color:#a855f7" />
                                        <stop offset="100%" style="stop-color:#ec4899" />
                                    </linearGradient>
                                </defs>
                                <circle class="progress-bg" cx="50" cy="50" r="40" />
                                <circle class="progress-bar" cx="50" cy="50" r="40" 
                                        stroke-dasharray="251.2" stroke-dashoffset="50.24"
                                        stroke="url(#gradient1)" />
                            </svg>
                            <div class="progress-text">85%</div>
                        </div>
                        <div class="progress-label">Análisis de Datos</div>
                    </div>
                    <div class="progress-item">
                        <div class="progress-circle">
                            <svg width="100" height="100">
                                <circle class="progress-bg" cx="50" cy="50" r="40" />
                                <circle class="progress-bar" cx="50" cy="50" r="40" 
                                        stroke-dasharray="251.2" stroke-dashoffset="62.8"
                                        stroke="url(#gradient1)" />
                            </svg>
                            <div class="progress-text">75%</div>
                        </div>
                        <div class="progress-label">Desarrollo Web</div>
                    </div>
                    <div class="progress-item">
                        <div class="progress-circle">
                            <svg width="100" height="100">
                                <circle class="progress-bg" cx="50" cy="50" r="40" />
                                <circle class="progress-bar" cx="50" cy="50" r="40" 
                                        stroke-dasharray="251.2" stroke-dashoffset="37.68"
                                        stroke="url(#gradient1)" />
                            </svg>
                            <div class="progress-text">90%</div>
                        </div>
                        <div class="progress-label">Visualización</div>
                    </div>
                    <div class="progress-item">
                        <div class="progress-circle">
                            <svg width="100" height="100">
                                <circle class="progress-bg" cx="50" cy="50" r="40" />
                                <circle class="progress-bar" cx="50" cy="50" r="40" 
                                        stroke-dasharray="251.2" stroke-dashoffset="75.36"
                                        stroke="url(#gradient1)" />
                            </svg>
                            <div class="progress-text">70%</div>
                        </div>
                        <div class="progress-label">Pipelines ETL</div>
                    </div>
                </div>
            </div>

            <!-- About -->
            <div class="card">
                <div class="card-title">
                    <div class="card-icon">✨</div>
                    Sobre Mí
                </div>
                <p style="color: var(--text-secondary); line-height: 1.8; margin-bottom: 1rem;">
                    Soy una desarrolladora apasionada por transformar datos en insights accionables. 
                    Mi enfoque principal es el análisis de datos y la visualización, creando soluciones 
                    que ayudan a las organizaciones a tomar decisiones informadas.
                </p>
                <p style="color: var(--text-secondary); line-height: 1.8;">
                    Actualmente curso el 9º semestre de Administración de Sistemas Informáticos, 
                    combinando conocimientos de desarrollo web, análisis de datos y administración 
                    de sistemas para crear soluciones completas e innovadoras.
                </p>
            </div>

            <!-- Contact -->
            <div class="card">
                <div class="card-title">
                    <div class="card-icon">📧</div>
                    Contacto
                </div>
                <div class="contact-grid">
                    <a href="mailto:tu@email.com" class="contact-item">
                        <div class="contact-icon">📧</div>
                        <div>
                            <div style="font-weight: 600;">Email</div>
                            <div style="font-size: 0.85rem; color: var(--text-secondary);">tu@email.com</div>
                        </div>
                    </a>
                    <a href="https://linkedin.com/in/tu-perfil" class="contact-item" target="_blank">
                        <div class="contact-icon">💼</div>
                        <div>
                            <div style="font-weight: 600;">LinkedIn</div>
                            <div style="font-size: 0.85rem; color: var(--text-secondary);">/in/tu-perfil</div>
                        </div>
                    </a>
                    <a href="https://github.com/tu-usuario" class="contact-item" target="_blank">
                        <div class="contact-icon">💻</div>
                        <div>
                            <div style="font-weight: 600;">GitHub</div>
                            <div style="font-size: 0.85rem; color: var(--text-secondary);">@tu-usuario</div>
                        </div>
                    </a>
                </div>
            </div>
        </div>

        <!-- Footer -->
        <div class="footer">
            <p>💜 Creado con pasión por el análisis de datos y el desarrollo</p>
            <p style="margin-top: 0.5rem; opacity: 0.7;">© 2026 - Transformando datos en decisiones inteligentes</p>
        </div>
    </div>

    <script>
        // Typing animation
        const phrases = [
            "📊 Especialista en Análisis de Datos",
            "💻 Desarrolladora Full Stack",
            "📈 Creadora de Visualizaciones",
            "🔄 Arquitecta de Pipelines ETL",
            "🎓 Estudiante de Sistemas Informáticos"
        ];
        
        let phraseIndex = 0;
        let charIndex = 0;
        let isDeleting = false;
        const typingSpeed = 100;
        const deletingSpeed = 50;
        const pauseDuration = 2000;

        function typeText() {
            const currentPhrase = phrases[phraseIndex];
            const typingElement = document.getElementById('typingText');
            
            if (isDeleting) {
                typingElement.textContent = currentPhrase.substring(0, charIndex - 1);
                charIndex--;
            } else {
                typingElement.textContent = currentPhrase.substring(0, charIndex + 1);
                charIndex++;
            }
            
            typingElement.innerHTML += '<span class="typing-cursor">|</span>';
            
            let timeout = isDeleting ? deletingSpeed : typingSpeed;
            
            if (!isDeleting && charIndex === currentPhrase.length) {
                timeout = pauseDuration;
                isDeleting = true;
            } else if (isDeleting && charIndex === 0) {
                isDeleting = false;
                phraseIndex = (phraseIndex + 1) % phrases.length;
            }
            
            setTimeout(typeText, timeout);
        }

        // Start typing animation
        typeText();

        // Animate bars on scroll
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        });

        document.querySelectorAll('.card').forEach(card => {
            observer.observe(card);
        });
    </script>
</body>
</html>
