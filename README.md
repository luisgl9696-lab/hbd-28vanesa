<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>¡Feliz Cumpleaños Vanesa!</title>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@500;700&family=Pacifico&family=Poppins:wght@300;600&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --color-fondo: #121212; /* Fondo oscuro para resaltar fuegos artificiales */
            --color-cake-base: #f7d794;
            --color-frosting: #ff6b6b;
            --color-candle: #fff;
            --color-flame: #ffdd59;
            --color-envelope: #ff5252;
            --color-paper: #fff;
        }

        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            background-color: var(--color-fondo);
            font-family: 'Poppins', sans-serif;
            overflow-x: hidden;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: flex-start;
        }

        /* --- Header y Título --- */
        header {
            text-align: center;
            margin-top: 40px;
            z-index: 10;
        }

        h1 {
            font-family: 'Pacifico', cursive;
            color: #fff;
            font-size: 3rem;
            text-shadow: 0 0 10px rgba(255,255,255,0.7);
            margin-bottom: 10px;
        }

        /* --- El Pastel --- */
        #cake-container {
            position: relative;
            width: 300px;
            height: 350px;
            margin-bottom: 40px;
            z-index: 5;
        }

        .cake-base {
            position: absolute;
            bottom: 0;
            width: 100%;
            height: 150px;
            background: var(--color-cake-base);
            border-radius: 20px 20px 5px 5px;
        }

        .cake-frosting {
            position: absolute;
            bottom: 140px;
            width: 100%;
            height: 50px;
            background: var(--color-frosting);
            border-radius: 15px 15px 0 0;
            box-shadow: 0 10px 0 #f04d4d;
        }

        /* Velas */
        .candles-container {
            position: absolute;
            bottom: 190px;
            width: 100%;
            height: 80px;
            display: grid;
            grid-template-columns: repeat(14, 1fr); /* 2 filas de 14 */
            gap: 2px;
            justify-items: center;
        }

        .candle {
            width: 6px;
            height: 40px;
            background: var(--color-candle);
            border-radius: 3px;
            position: relative;
        }

        .flame {
            position: absolute;
            top: -15px;
            left: 50%;
            transform: translateX(-50%);
            width: 10px;
            height: 15px;
            background: var(--color-flame);
            border-radius: 50% 50% 20% 20%;
            box-shadow: 0 0 10px rgba(255,221,89,0.8);
            animation: flicker 1s ease-in-out infinite alternate;
        }

        @keyframes flicker {
            0% { transform: translateX(-50%) scale(1); opacity: 0.9; }
            50% { transform: translateX(-50%) scale(1.1); opacity: 1; }
            100% { transform: translateX(-50%) scale(1) translateY(-2px); opacity: 0.9; }
        }

        /* --- Sobre y Carta --- */
        .envelope-wrapper {
            position: relative;
            cursor: pointer;
            width: 350px;
            height: 250px;
            margin-bottom: 50px;
            z-index: 20;
            transition: transform 0.3s;
        }

        .envelope-wrapper:hover { transform: scale(1.05); }

        .envelope {
            position: relative;
            width: 100%;
            height: 100%;
            background-color: var(--color-envelope);
            border-radius: 10px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.5);
        }

        .envelope::before {
            content: "";
            position: absolute;
            top: 0;
            z-index: 2;
            border-top: 150px solid var(--color-envelope);
            border-left: 175px solid transparent;
            border-right: 175px solid transparent;
            transform-origin: top;
            transition: all 0.5s ease-in-out 0.2s;
        }

        .envelope::after {
            content: "";
            position: absolute;
            bottom: 0;
            width: 0;
            height: 0;
            border-top: 125px solid transparent;
            border-right: 175px solid #f04d4d;
            border-bottom: 125px solid #f04d4d;
            border-left: 175px solid #f04d4d;
            border-radius: 0 0 10px 10px;
            z-index: 3;
        }

        .label-to {
            position: absolute;
            top: 100px;
            width: 100%;
            text-align: center;
            color: #fff;
            font-size: 1.5rem;
            font-family: 'Poppins', sans-serif;
            z-index: 4;
            letter-spacing: 2px;
        }

        .label-open {
            position: absolute;
            bottom: 10px;
            width: 100%;
            text-align: center;
            color: rgba(255,255,255,0.7);
            font-size: 0.8rem;
            text-transform: uppercase;
            z-index: 4;
        }

        /* La Carta (Hoja) */
        .paper-sheet {
            position: absolute;
            bottom: 10px;
            left: 5%;
            width: 90%;
            height: 90%;
            background-color: var(--color-paper);
            border-radius: 5px;
            z-index: 1;
            transition: all 0.7s ease-in-out;
            padding: 30px;
            box-sizing: border-box;
            overflow-y: auto;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            opacity: 0; /* Oculta inicialmente */
        }

        /* El Mensaje Final */
        .heartfelt-message {
            font-family: 'Dancing Script', cursive; /* Letra a mano */
            font-size: 1.3rem;
            color: #333;
            line-height: 1.7;
            text-align: left;
            margin: 0;
            white-space: pre-wrap; /* Mantiene saltos de línea */
        }

        /* --- Estado Abierto --- */
        .envelope-wrapper.open .envelope::before {
            transform: rotateX(180deg);
            z-index: 0;
        }

        .envelope-wrapper.open .paper-sheet {
            transform: translateY(-300px); /* Saca la carta hacia arriba */
            height: auto;
            min-height: 400px;
            width: 350px; /* Se ajusta fuera del sobre */
            left: 0;
            z-index: 100;
            opacity: 1;
            box-shadow: 0 15px 50px rgba(0,0,0,0.6);
        }

        /* --- Confeti / Fuegos Artificiales Canvas --- */
        #fx-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }

        /* Ajustes para Móvil */
        @media (max-width: 400px) {
            h1 { font-size: 2.2rem; }
            .envelope-wrapper, #cake-container { width: 300px; }
            .envelope::before { border-left-width: 150px; border-right-width: 150px; }
            .envelope::after { border-right-width: 150px; border-left-width: 150px; }
            .candles-container { grid-template-columns: repeat(14, 1fr); gap: 1px;}
            .candle { width: 4px; }
            .envelope-wrapper.open .paper-sheet { width: 300px; transform: translateY(-350px); }
        }
    </style>
</head>
<body>

    <canvas id="fx-canvas"></canvas>

    <header>
        <h1>¡Feliz Cumpleaños, Hermana!</h1>
    </header>

    <div id="cake-container">
        <div class="cake-base"></div>
        <div class="cake-frosting"></div>
        <div class="candles-container" id="candles">
            </div>
    </div>

    <div class="envelope-wrapper" id="envelope">
        <div class="envelope">
            <p class="label-to">Para: Vanesa</p>
            <p class="label-open">clic para abrir</p>
            <div class="paper-sheet">
                <p class="heartfelt-message">Querida hermana, en este día tan especial en el que celebramos tu vida, quiero aprovechar para decirte lo mucho que te admiro y lo inmensamente afortunado que me siento de caminar a tu lado.

No eres solo mi hermana, sino ese pilar fundamental, esa persona llena de luz que siempre encuentra la palabra precisa o el abrazo necesario cuando el mundo se pone difícil.

Tu capacidad para entregarte con tanto amor y tu esencia tan única hacen que cada momento compartido sea un tesoro que guardo con todo mi cariño.

Deseo de todo corazón que este nuevo año de vida te devuelva multiplicado todo lo bueno que das, que tus sueños se sientan cada vez más cerca y que nunca te falten motivos para sonreír con esa alegría que te caracteriza.

Gracias por ser mi confidente, mi apoyo incondicional y, sobre todo, por ser una mujer tan extraordinaria a la que amo con toda mi alma.

¡Feliz cumpleaños!</p>
            </div>
        </div>
    </div>

    <script>
        // --- Configuración e Inicialización ---
        const envelope = document.getElementById('envelope');
        const candlesContainer = document.getElementById('candles');
        const canvas = document.getElementById('fx-canvas');
        const ctx = canvas.getContext('2d');

        let particles = [];

        // --- Generar 28 Velas ---
        for (let i = 0; i < 28; i++) {
            const candle = document.createElement('div');
            candle.classList.add('candle');
            const flame = document.createElement('div');
            flame.classList.add('flame');
            flame.style.animationDelay = `${Math.random() * 0.5}s`; // Parpadeo aleatorio
            candle.appendChild(flame);
            candlesContainer.appendChild(candle);
        }

        // --- Manejo del Canvas para FX (Fuegos/Confeti) ---
        function resizeCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }
        window.addEventListener('resize', resizeCanvas);
        resizeCanvas();

        // --- Clase Partícula (para Fuegos y Confeti) ---
        class Particle {
            constructor(x, y, color, type) {
                this.x = x;
                this.y = y;
                this.color = color;
                this.type = type; // 'firework' o 'confetti'
                this.radius = type === 'firework' ? Math.random() * 3 + 1 : Math.random() * 4 + 2;
                this.angle = Math.random() * Math.PI * 2;
                this.speed = type === 'firework' ? Math.random() * 6 + 2 : Math.random() * 3 + 1;
                this.friction = type === 'firework' ? 0.95 : 0.99;
                this.gravity = type === 'firework' ? 0.15 : 0.05;
                this.opacity = 1;
                this.decay = type === 'firework' ? 0.015 : 0.01;
                this.vx = Math.cos(this.angle) * this.speed;
                this.vy = (Math.sin(this.angle) * this.speed) - (type === 'firework' ? 3 : 0); // Empuje inicial hacia arriba para fuegos
            }

            draw() {
                ctx.save();
                ctx.globalAlpha = this.opacity;
                ctx.beginPath();
                if (this.type === 'confetti') {
                    ctx.rect(this.x, this.y, this.radius, this.radius * 1.5); // Rectángulos para confeti
                } else {
                    ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2); // Círculos para fuegos
                }
                ctx.fillStyle = this.color;
                ctx.fill();
                ctx.restore();
            }

            update() {
                this.vx *= this.friction;
                this.vy *= this.friction;
                this.vy += this.gravity;
                this.x += this.vx;
                this.y += this.vy;
                this.opacity -= this.decay;
            }
        }

        function createFirework(x, y) {
            const colors = ['#ff5252', '#ffdd59', '#3ae374', '#fff'];
            const color = colors[Math.floor(Math.random() * colors.length)];
            for (let i = 0; i < 60; i++) {
                particles.push(new Particle(x, y, color, 'firework'));
            }
        }

        function createConfettiShower() {
            for (let i = 0; i < 100; i++) {
                const x = Math.random() * canvas.width;
                const y = Math.random() * canvas.height * 0.3; // Comienza arriba
                const color = `hsl(${Math.random() * 360}, 100%, 50%)`;
                particles.push(new Particle(x, y, color, 'confetti'));
            }
        }

        // --- Bucle de Animación ---
        function animate() {
            requestAnimationFrame(animate);
            ctx.clearRect(0, 0, canvas.width, canvas.height); // Fondo transparente
            
            particles.forEach((particle, index) => {
                if (particle.opacity > 0) {
                    particle.update();
                    particle.draw();
                } else {
                    particles.splice(index, 1);
                }
            });
        }
        animate();

        // --- Efectos de Carga de Página ---
        window.addEventListener('load', () => {
            // Unos fuegos artificiales al inicio
            setTimeout(() => createFirework(canvas.width * 0.3, canvas.height * 0.4), 500);
            setTimeout(() => createFirework(canvas.width * 0.7, canvas.height * 0.3), 1000);
            setTimeout(() => createFirework(canvas.width * 0.5, canvas.height * 0.5), 1500);
        });

        // --- Interacción del Sobre ---
        envelope.addEventListener('click', () => {
            if (!envelope.classList.contains('open')) {
                envelope.classList.add('open');
                // Al abrir, disparar lluvia de confeti
                createConfettiShower();
            } else {
                envelope.classList.remove('open');
            }
        });

    </script>
</body>
</html>
