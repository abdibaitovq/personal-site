# personal-site
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
    <title>Уларбек Абдибаитов</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500&display=swap" rel="stylesheet">
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        html {
            scroll-behavior: smooth;
        }
        body {
            font-family: 'Orbitron', sans-serif;
            color: #00ffe7;
            overflow-x: hidden;
        }
        canvas#stars {
            position: fixed;
            top: 0;
            left: 0;
            z-index: -1;
            width: 100%;
            height: 100%;
            background: black;
        }
        header {
            text-align: center;
            padding: 2rem;
            font-size: 2rem;
            background: rgba(0,0,0,0.6);
            box-shadow: 0 0 20px #00ffe7;
        }
        nav {
            margin-top: 1rem;
        }
        nav a {
            margin: 0 10px;
            text-decoration: none;
            color: #ffffff;
            font-weight: bold;
            font-size: 1.2rem;
            transition: color 0.3s;
        }
        nav a:hover {
            color: #ff00cc;
        }
        section {
            padding: 4rem 2rem;
            max-width: 900px;
            margin: auto;
            border-bottom: 1px solid #00ffe7;
            background: rgba(0,0,0,0.4);
        }
        h2 {
            font-size: 1.8rem;
            color: #ff00cc;
            margin-bottom: 1rem;
            text-shadow: 0 0 10px #ff00cc;
        }
        p {
            font-size: 1.2rem;
            line-height: 1.6;
        }
        .theme-toggle {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 10px 20px;
            background: none;
            border: 2px solid #00ffe7;
            color: #00ffe7;
            cursor: pointer;
            z-index: 999;
        }
        .photo {
            text-align: center;
            margin-top: 2rem;
        }
        .photo img {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            box-shadow: 0 0 15px #00ffe7;
        }
        footer {
            text-align: center;
            padding: 2rem;
            font-size: 1rem;
            background: rgba(0,0,0,0.5);
            color: #888;
            margin-top: 3rem;
        }
    </style>
</head>
<body>
    <canvas id="stars"></canvas>

    <header>
        Уларбек Абдибаитов — Персональный сайт
        <nav>
            <a href="#bio">Биография</a>
            <a href="#goals">Цели</a>
            <a href="#contacts">Контакты</a>
        </nav>
    </header>

    <div class="photo">
        <img src="https://img.freepik.com/premium-vector/letter-u-logo-design-template-u-letter-logotype-business-company-identity_754537-1728.jpg" alt="Фото">
    </div>

    <section id="bio">
        <h2>Биография</h2>
        <p>Я Уларбек Абдибаитов, родился 16 февраля 2009 года в городе Ош. Учусь в Инновационном колледже STEM, по направлению прикладной информатики, группа ПИЕС 9-5-25.</p>
    </section>

    <section id="goals">
        <h2>Цели</h2>
        <p>Моя цель — работать в банке и применять информационные технологии для развития финансовой сферы.</p>
    </section>

    <section id="contacts">
        <h2>Контакты</h2>
        <p>Телефон: +996222221808</p>
        <p>Instagram: @abdibaitovq</p>
        <p>Telegram: @abdibaitovq</p>
        <p>WhatsApp: +996222221808</p>
        <p>Email: frefire7705@gmail.com</p>
    </section>

    <footer>
        Сайт выполнен Абдибаитовым Уларбеком
    </footer>

    <script>
        // Звёздный фон
        const canvas = document.getElementById('stars');
        const ctx = canvas.getContext('2d');
        let stars = [];

        function resizeCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }

        window.addEventListener('resize', resizeCanvas);
        resizeCanvas();

        for (let i = 0; i < 150; i++) {
            stars.push({
                x: Math.random() * canvas.width,
                y: Math.random() * canvas.height,
                radius: Math.random() * 1.5,
                velocity: Math.random() * 0.5 + 0.2
            });
        }

        function drawStars() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            ctx.fillStyle = '#ffffff';
            for (let star of stars) {
                ctx.beginPath();
                ctx.arc(star.x, star.y, star.radius, 0, 2 * Math.PI);
                ctx.fill();
                star.y += star.velocity;
                if (star.y > canvas.height) {
                    star.y = 0;
                    star.x = Math.random() * canvas.width;
                }
            }
            requestAnimationFrame(drawStars);
        }

        drawStars();

        // Переключение темы
        function toggleTheme() {
            const sections = document.querySelectorAll('section');
            sections.forEach(sec => {
                sec.style.background = sec.style.background.includes('0.4') ? 'rgba(0,0,0,0.8)' : 'rgba(0,0,0,0.4)';
            });
        }
    </script>
</body>
</html>
