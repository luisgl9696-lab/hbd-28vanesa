<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>¡Feliz Cumpleaños Vanesa!</title>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@500;700&family=Pacifico&family=Poppins:wght@300;600&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --color-fondo: #1a1a1a; /* Fondo oscuro elegante */
            --color-titulo: #ff6b6b; /* Color cálido para el título */
            --color-cake-base: #f7d794;
            --color-frosting: #ff6b6b;
            --color-candle: #fff;
            --color-flame: #ffdd59;
            --color-envelope: #ff5252;
            --color-paper: #ffffff;
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

        /* --- Título Principal Mejorado --- */
        header {
            text-align: center;
            margin-top: 50px;
            z-index: 10;
        }

        h1 {
            font-family: 'Pacifico', cursive;
            color: var(--color-titulo);
            font-size: 3.5rem;
            text-shadow: 0 0 15px rgba(255, 107, 107, 0.6);
            margin: 0;
        }

        /* --- El Pastel con 28 Velas --- */
        #cake-container {
            position: relative;
            width: 300px;
            height: 350px;
            margin-top: 30px;
            margin-bottom: 50px;
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

        /* --- Sobre y Carta Interactiva --- */
        .envelope-wrapper {
            position: relative;
            cursor: pointer;
            width: 380px;
            height: 270px;
            margin-bottom: 60px;
            z-index: 20;
            transition: transform 0.3s;
        }

        .envelope-wrapper:hover { transform: scale(1.03); }

        .envelope {
            position: relative;
            width: 100%;
            height: 100%;
            background-color: var(--color-envelope);
            border-radius: 12px;
            box-shadow: 0 25px 50px rgba(0,0,0,0.5);
            overflow: visible; /* Importante para que la carta salga */
        }

        /* Tapa del Sobre */
        .envelope::before {
            content: "";
            position: absolute;
            top: 0;
            z-index: 2;
            border-top: 160px solid var(--color-envelope);
            border-left: 190px solid transparent;
            border-right: 190px solid transparent;
            transform-origin: top;
            transition: all 0.5s ease-in-out 0.2s;
        }

        /* Cuerpo del Sobre */
        .envelope::after {
            content: "";
            position: absolute;
            bottom: 0;
            width: 0;
            height: 0;
            border-top: 135px solid transparent;
            border-right: 190px solid #f04d4d;
            border-bottom: 135px solid #f04d4d;
            border-left: 190px solid #f04d4d;
            border-radius: 0 0 12px 12px;
            z-index: 3;
        }

        .label-to {
            position: absolute;
            top: 100px;
            width: 100%;
            text-align: center;
            color: #fff;
            font-size: 1.6rem;
            font-family: 'Poppins', sans-serif;
            z-index: 4;
            letter-spacing: 2px;
            font-weight: 600;
        }

        .label-open {
            position: absolute;
            bottom: 15px;
            width: 100%;
            text-align: center;
            color: rgba(255,255,255,0.8);
            font-size: 0.9rem;
            text-transform: uppercase;
            z-index: 4;
            letter-spacing: 1px;
        }

        /* --- La Carta (Hoja) SOLUCIÓN DE SCROLL --- */
        .paper-sheet {
            position: absolute;
            bottom: 15px;
            left: 15px;
            width: calc(100% - 30px); /* Ajuste de ancho */
            height: calc(100% - 30px); /* Ajuste de alto inicial */
            background-color: var(--color-paper);
            border-radius: 8px;
            z-index: 1;
            transition: all 0.7s ease-in-out;
            opacity: 0; /* Oculta inicialmente */
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            overflow: hidden; /* Evita que el texto se salga antes de abrir */
        }

        /* --- El Mensaje Final Mejorado --- */
        .heartfelt-message {
            font-family: 'Dancing Script', cursive; /* Letra a mano */
            font-size: 1.4rem;
            color: #2c3e50;
            line-height: 1.8;
            text-align: left;
            margin: 0;
            padding: 40px; /* Padding interno de la hoja */
            white-space: pre-wrap; /* Mantiene saltos de línea */
            box-sizing: border-box;
            height: 100%; /* Ocupa todo el alto disponible */
            overflow-y: auto; /* IMPORTANTE: Activa el scroll vertical */
            scrollbar-width: thin; /* Scrollbar más discreto en Firefox */
            scrollbar-color: #ff6b6b #f0f0f0;
        }

        /* Estilo para el scrollbar en Webkit (Chrome, Safari, Edge) */
        .heartfelt-message::-webkit-scrollbar {
            width: 8px;
        }
        .heartfelt-message::-webkit-scrollbar-track {
            background: #f0f0f0;
            border-radius: 4px;
        }
        .heartfelt-message::-webkit-scrollbar-thumb {
            background-color: #ff6b6b;
            border-radius: 4px;
        }

        /* --- Estado Abierto (Animación Final) --- */
        .envelope-wrapper.open .envelope::before {
            transform: rotateX(180deg);
            z-index: 0;
        }

        .envelope-wrapper.open .paper-sheet {
            transform: translateY(-350px); /* Saca la carta hacia arriba */
            height: 480px; /* Agrandamos la hoja para que el scroll sea útil */
            width: 360px; /* Se ajusta fuera del sobre */
            left: 10px;
            z-index: 100;
            opacity: 1;
            box-shadow: 0 20px 60px rgba(0,0,0,0.7);
            overflow: visible; /* Permite que el contenido interno haga scroll */
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

        /* Ajustes para Móvil (Responsive) */
        @media (max-width: 420px) {
            h1 { font-size: 2.6rem; margin-top: 30px;}
            .envelope-wrapper, #cake-container { width: 320px; }
            .envelope-wrapper { height: 230px; }
            .envelope::before { border-top-width: 135px; border-left-width: 160px; border-right-width: 160px; }
            .envelope::after { border-top-width: 115px; border-right-width: 160px; border-bottom-width: 115px; border-left-width: 160px; }
            .label-to { top: 85px; font-size: 1.4rem; }
            
            .envelope-wrapper.open .paper-sheet { 
                width: 310px; 
                height: 450px;
                transform: translateY(-380px); 
                left: 5px;
            }
            .heartfelt-message { font-size: 1.2rem; padding: 30px; }
        }
    </style>
</head>
<body>

    <canvas id="fx-canvas"></canvas>

    <header>
        <h1>¡Feliz Cumpleaños, Vanesa!</h1>
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
                <div class="heartfelt-message">
Querida hermana, en este día tan especial en el que celebramos tu vida, quiero aprovechar para decirte lo mucho que te admiro y lo inmensamente afortunado que me siento de caminar a tu lado.

No eres solo mi hermana, sino ese pilar fundamental, esa persona llena de luz que siempre encuentra la palabra precisa o el abrazo necesario cuando el mundo se pone difícil.

Tu capacidad para entregarte con tanto amor y tu esencia tan única hacen que cada momento compartido sea un tesoro que guardo con todo mi cariño.

Deseo de todo corazón que este nuevo año de vida te devuelva multiplicado todo lo bueno que das, que tus sueños se sientan cada vez más cerca y que nunca te falten motivos para sonreír con esa alegría que te caracteriza.

Gracias por ser mi confidente, mi apoyo incondicional y, sobre todo, por ser una mujer tan extraordinaria a la que amo con toda mi alma.

¡Feliz cumpleaños!
                </div>
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
                this.vy = (Math.sin(this.angle) * this.speed) - (type === 'firework' ? 3 : 0);
            }

            draw() {
                ctx.save();
                ctx.globalAlpha = this.opacity;
                ctx.beginPath();
                if (this.type === 'confetti') {
                    ctx.rect(this.x, this.y, this.radius, this.radius * 1.5);
                } else {
                    ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2);
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
            for (let i = 0; i < 120; i++) {
                const x = Math.random() * canvas.width;
                const y = Math.random() * canvas.height * 0.3;
                const color = `hsl(${Math.random() * 360}, 100%, 50%)`;
                particles.push(new Particle(x, y, color, 'confetti'));
            }
        }

        // --- Bucle de Animación ---
        function animate() {
            requestAnimationFrame(animate);
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            
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
            setTimeout(() => createFirework(canvas.width * 0.3, canvas.height * 0.4), 500);
            setTimeout(() => createFirework(canvas.width * 0.7, canvas.height * 0.3), 1000);
            setTimeout(() => createFirework(canvas.width * 0.5, canvas.height * 0.5), 1500);
        });

        // --- Interacción del Sobre ---
        envelope.addEventListener('click', () => {
            if (!envelope.classList.contains('open')) {
                envelope.classList.add('open');
                createConfettiShower();
            } else {
                // Al hacer clic de nuevo, se cierra
                envelope.classList.remove('open');
            }
        });

    </script>
</body>
</html>
