<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Perfil GitHub - Desenvolvedor Full-Stack</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #2d3436;
            --secondary: #0984e3;
            --accent: #00b894;
            --light: #f5f6fa;
            --dark: #2d3436;
            --gray: #636e72;
            --shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: #f9f9f9;
            color: var(--dark);
            line-height: 1.6;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        header {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            padding: 80px 0;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        header::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 320"><path fill="%23000000" fill-opacity="0.1" d="M0,224L48,213.3C96,203,192,181,288,181.3C384,181,480,203,576,202.7C672,203,768,181,864,170.7C960,160,1056,160,1152,170.7C1248,181,1344,203,1392,213.3L1440,224L1440,320L1392,320C1344,320,1248,320,1152,320C1056,320,960,320,864,320C768,320,672,320,576,320C480,320,384,320,288,320C192,320,96,320,48,320L0,320Z"></path></svg>');
            background-size: cover;
            background-position: center;
        }

        .profile-img {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            border: 5px solid white;
            margin: 0 auto 20px;
            background-color: #ddd;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            z-index: 1;
        }

        .profile-img i {
            font-size: 60px;
            color: var(--gray);
        }

        h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
            position: relative;
            z-index: 1;
        }

        .tagline {
            font-size: 1.2rem;
            margin-bottom: 20px;
            position: relative;
            z-index: 1;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 20px;
            position: relative;
            z-index: 1;
        }

        .social-links a {
            color: white;
            font-size: 1.5rem;
            transition: transform 0.3s;
        }

        .social-links a:hover {
            transform: translateY(-5px);
        }

        section {
            padding: 60px 0;
        }

        .section-title {
            text-align: center;
            margin-bottom: 40px;
            font-size: 2rem;
            color: var(--primary);
            position: relative;
        }

        .section-title::after {
            content: "";
            display: block;
            width: 80px;
            height: 4px;
            background: var(--accent);
            margin: 10px auto;
        }

        .about-content {
            display: flex;
            flex-wrap: wrap;
            gap: 40px;
            align-items: center;
        }

        .about-text {
            flex: 1;
            min-width: 300px;
        }

        .skills {
            flex: 1;
            min-width: 300px;
        }

        .skill-item {
            margin-bottom: 20px;
        }

        .skill-name {
            display: flex;
            justify-content: space-between;
            margin-bottom: 5px;
        }

        .skill-bar {
            height: 10px;
            background-color: #e0e0e0;
            border-radius: 5px;
            overflow: hidden;
        }

        .skill-level {
            height: 100%;
            background-color: var(--secondary);
            border-radius: 5px;
        }

        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 30px;
        }

        .project-card {
            background: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: transform 0.3s;
        }

        .project-card:hover {
            transform: translateY(-10px);
        }

        .project-img {
            height: 180px;
            background-color: #ddd;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .project-img i {
            font-size: 50px;
            color: var(--gray);
        }

        .project-info {
            padding: 20px;
        }

        .project-title {
            font-size: 1.2rem;
            margin-bottom: 10px;
            color: var(--primary);
        }

        .project-tech {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin: 15px 0;
        }

        .tech-tag {
            background-color: var(--light);
            color: var(--secondary);
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 500;
        }

        .btn {
            display: inline-block;
            padding: 10px 20px;
            background-color: var(--secondary);
            color: white;
            text-decoration: none;
            border-radius: 5px;
            font-weight: 500;
            transition: background-color 0.3s;
        }

        .btn:hover {
            background-color: var(--primary);
        }

        .education {
            background-color: var(--light);
        }

        .education-item {
            background: white;
            padding: 30px;
            border-radius: 10px;
            box-shadow: var(--shadow);
            margin-bottom: 20px;
        }

        .education-icon {
            font-size: 2rem;
            color: var(--secondary);
            margin-bottom: 15px;
        }

        .education-title {
            font-size: 1.3rem;
            margin-bottom: 10px;
            color: var(--primary);
        }

        footer {
            background-color: var(--primary);
            color: white;
            padding: 40px 0;
            text-align: center;
        }

        .contact-info {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 30px;
            margin-bottom: 30px;
        }

        .contact-item {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .contact-item i {
            color: var(--accent);
        }

        .copyright {
            margin-top: 20px;
            font-size: 0.9rem;
            color: #b2bec3;
        }

        @media (max-width: 768px) {
            h1 {
                font-size: 2rem;
            }
            
            .about-content {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="container">
            <div class="profile-img">
                <i class="fas fa-user"></i>
            </div>
            <h1>Seu Nome</h1>
            <p class="tagline">Desenvolvedor Full-Stack com Foco em Front-end</p>
            <div class="social-links">
                <a href="#"><i class="fab fa-github"></i></a>
                <a href="#"><i class="fab fa-linkedin"></i></a>
                <a href="#"><i class="fab fa-twitter"></i></a>
                <a href="#"><i class="fas fa-envelope"></i></a>
            </div>
        </div>
    </header>

    <section class="about">
        <div class="container">
            <h2 class="section-title">Sobre Mim</h2>
            <div class="about-content">
                <div class="about-text">
                    <p>Sou um desenvolvedor full-stack com foco especializado em front-end, atualmente cursando Análise e Desenvolvimento de Sistemas no SENAI. Tenho paixão por criar interfaces modernas, responsivas e com excelente experiência do usuário.</p>
                    <p>Minha jornada na programação começou há 2 anos, e desde então venho me especializando em tecnologias como React, Vue.js, TypeScript e Node.js. Acredito que um bom front-end é a ponte entre a tecnologia e as pessoas.</p>
                    <p>Estou sempre em busca de novos desafios e oportunidades para aprender e crescer profissionalmente.</p>
                </div>
                <div class="skills">
                    <div class="skill-item">
                        <div class="skill-name">
                            <span>HTML/CSS</span>
                            <span>95%</span>
                        </div>
                        <div class="skill-bar">
                            <div class="skill-level" style="width: 95%"></div>
                        </div>
                    </div>
                    <div class="skill-item">
                        <div class="skill-name">
                            <span>JavaScript</span>
                            <span>90%</span>
                        </div>
                        <div class="skill-bar">
                            <div class="skill-level" style="width: 90%"></div>
                        </div>
                    </div>
                    <div class="skill-item">
                        <div class="skill-name">
                            <span>React</span>
                            <span>85%</span>
                        </div>
                        <div class="skill-bar">
                            <div class="skill-level" style="width: 85%"></div>
                        </div>
                    </div>
                    <div class="skill-item">
                        <div class="skill-name">
                            <span>Vue.js</span>
                            <span>80%</span>
                        </div>
                        <div class="skill-bar">
                            <div class="skill-level" style="width: 80%"></div>
                        </div>
                    </div>
                    <div class="skill-item">
                        <div class="skill-name">
                            <span>Node.js</span>
                            <span>75%</span>
                        </div>
                        <div class="skill-bar">
                            <div class="skill-level" style="width: 75%"></div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section class="projects">
        <div class="container">
            <h2 class="section-title">Projetos em Destaque</h2>
            <div class="projects-grid">
                <div class="project-card">
                    <div class="project-img">
                        <i class="fas fa-shopping-cart"></i>
                    </div>
                    <div class="project-info">
                        <h3 class="project-title">E-commerce React</h3>
                        <p>Plataforma de e-commerce desenvolvida com React, Redux e Styled Components.</p>
                        <div class="project-tech">
                            <span class="tech-tag">React</span>
                            <span class="tech-tag">Redux</span>
                            <span class="tech-tag">Styled Components</span>
                        </div>
                        <a href="#" class="btn">Ver Projeto</a>
                    </div>
                </div>
                <div class="project-card">
                    <div class="project-img">
                        <i class="fas fa-tasks"></i>
                    </div>
                    <div class="project-info">
                        <h3 class="project-title">Sistema de Gestão</h3>
                        <p>Aplicação web para gestão de tarefas e projetos com Vue.js e Firebase.</p>
                        <div class="project-tech">
                            <span class="tech-tag">Vue.js</span>
                            <span class="tech-tag">Firebase</span>
                            <span class="tech-tag">Vuex</span>
                        </div>
                        <a href="#" class="btn">Ver Projeto</a>
                    </div>
                </div>
                <div class="project-card">
                    <div class="project-img">
                        <i class="fas fa-mobile-alt"></i>
                    </div>
                    <div class="project-info">
                        <h3 class="project-title">App de Finanças</h3>
                        <p>Aplicativo mobile para controle financeiro pessoal desenvolvido com React Native.</p>
                        <div class="project-tech">
                            <span class="tech-tag">React Native</span>
                            <span class="tech-tag">Node.js</span>
                            <span class="tech-tag">MongoDB</span>
                        </div>
                        <a href="#" class="btn">Ver Projeto</a>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section class="education">
        <div class="container">
            <h2 class="section-title">Formação</h2>
            <div class="education-item">
                <div class="education-icon">
                    <i class="fas fa-graduation-cap"></i>
                </div>
                <h3 class="education-title">Tecnólogo em Análise e Desenvolvimento de Sistemas</h3>
                <p><strong>SENAI</strong> | 2022 - 2024 (Previsão)</p>
                <p>Formação focada em desenvolvimento de software, engenharia de requisitos, banco de dados e gestão de projetos.</p>
            </div>
            <div class="education-item">
                <div class="education-icon">
                    <i class="fas fa-certificate"></i>
                </div>
                <h3 class="education-title">Curso de React Avançado</h3>
                <p><strong>Alura</strong> | 2023</p>
                <p>Curso focado em conceitos avançados de React como Hooks, Context API, performance e testes.</p>
            </div>
        </div>
    </section>

    <footer>
        <div class="container">
            <h2 class="section-title" style="color: white;">Contato</h2>
            <div class="contact-info">
                <div class="contact-item">
                    <i class="fas fa-envelope"></i>
                    <span>seu.email@exemplo.com</span>
                </div>
                <div class="contact-item">
                    <i class="fas fa-phone"></i>
                    <span>(11) 99999-9999</span>
                </div>
                <div class="contact-item">
                    <i class="fas fa-map-marker-alt"></i>
                    <span>São Paulo, Brasil</span>
                </div>
            </div>
            <div class="social-links">
                <a href="#"><i class="fab fa-github"></i></a>
                <a href="#"><i class="fab fa-linkedin"></i></a>
                <a href="#"><i class="fab fa-twitter"></i></a>
                <a href="#"><i class="fab fa-instagram"></i></a>
            </div>
            <p class="copyright">&copy; 2023 Seu Nome. Todos os direitos reservados.</p>
        </div>
    </footer>
</body>
</html>
