# Valentine-
"A special surprise for the most amazing girl in the world."
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>A Special Message for You ❤️</title>
    <style>
        :root {
            --primary-pink: #ff4d6d;
            --secondary-pink: #ff758f;
            --bg-gradient: linear-gradient(135deg, #ffafbd 0%, #ffc1cc 100%);
            --celebration-gradient: linear-gradient(45deg, #ff0a54, #ff7096, #ff4d6d);
        }

        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            font-family: 'Poppins', sans-serif;
            background: var(--bg-gradient);
            display: flex;
            align-items: center;
            justify-content: center;
            transition: background 2s ease-in-out;
        }

        /* Glassmorphism Card */
        #container {
            position: relative;
            padding: 50px;
            background: rgba(255, 255, 255, 0.25);
            backdrop-filter: blur(15px);
            -webkit-backdrop-filter: blur(15px);
            border: 1px solid rgba(255, 255, 255, 0.4);
            border-radius: 30px;
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.1);
            text-align: center;
            z-index: 100;
            max-width: 90%;
            transform: scale(1);
            transition: all 0.8s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        h1 {
            color: #d63384;
            font-size: clamp(2rem, 8vw, 3.5rem);
            margin-bottom: 40px;
            text-shadow: 2px 2px 10px rgba(255, 255, 255, 0.5);
        }

        .btn-wrapper {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 40px;
            min-height: 80px;
        }

        button {
            padding: 18px 45px;
            font-size: 1.5rem;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            font-weight: 700;
            transition: all 0.3s ease;
            box-shadow: 0 10px 20px rgba(214, 51, 132, 0.3);
        }

        #yesBtn {
            background: var(--primary-pink);
            color: white;
            z-index: 101;
        }

        #yesBtn:hover {
            transform: scale(1.15) translateY(-5px);
            background: var(--secondary-pink);
            box-shadow: 0 15px 30px rgba(214, 51, 132, 0.5);
        }

        #noBtn {
            background: white;
            color: var(--primary-pink);
            position: fixed; /* Dynamic movement */
            transition: all 0.15s ease-out;
            z-index: 102;
        }

        /* Particles */
        .particle {
            position: absolute;
            pointer-events: none;
            z-index: 1;
            filter: drop-shadow(0 0 5px rgba(255,255,255,0.5));
        }

        @keyframes floatUp {
            0% { transform: translateY(110vh) translateX(0) rotate(0deg); opacity: 1; }
            100% { transform: translateY(-10vh) translateX(50px) rotate(360deg); opacity: 0; }
        }

        /* Success State Details */
        .success h1 {
            color: white;
            font-size: 4rem;
            animation: heartBeat 1.5s infinite;
        }

        @keyframes heartBeat {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }

        .hidden {
            display: none !important;
        }
    </style>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@700&display=swap" rel="stylesheet">
</head>
<body id="body">

    <div id="container">
        <h1 id="question">Will you be my Valentine? ❤️</h1>
        <div class="btn-wrapper">
            <button id="yesBtn">YES</button>
            <button id="noBtn">No</button>
        </div>
    </div>

    <script>
        const noBtn = document.getElementById('noBtn');
        const yesBtn = document.getElementById('yesBtn');
        const body = document.getElementById('body');
        const container = document.getElementById('container');
        const question = document.getElementById('question');

        // Advanced "Run Away" Logic
        const moveButton = () => {
            // Ensure button stays within visible screen bounds
            const padding = 50;
            const maxX = window.innerWidth - noBtn.offsetWidth - padding;
            const maxY = window.innerHeight - noBtn.offsetHeight - padding;
            
            const randomX = Math.floor(Math.random() * maxX) + padding/2;
            const randomY = Math.floor(Math.random() * maxY) + padding/2;
            
            noBtn.style.left = `${randomX}px`;
            noBtn.style.top = `${randomY}px`;
        };

        // Move on hover (desktop) and touch (mobile)
        noBtn.addEventListener('mouseenter', moveButton);
        noBtn.addEventListener('touchstart', (e) => {
            e.preventDefault(); // Prevents accidental clicking on mobile
            moveButton();
        });

        // Floating Hearts & Roses Generator
        function spawnParticle(type) {
            const particle = document.createElement('div');
            particle.classList.add('particle');
            particle.innerHTML = type;
            particle.style.left = Math.random() * 100 + 'vw';
            particle.style.fontSize = (Math.random() * 20 + 20) + 'px';
            particle.style.animation = `floatUp ${Math.random() * 3 + 3}s linear forwards`;
            document.body.appendChild(particle);
            
            setTimeout(() => particle.remove(), 6000);
        }

        // Background ambiance
        setInterval(() => spawnParticle('❤️'), 600);
        setInterval(() => spawnParticle('✨'), 1000);

        // Success Transition
        yesBtn.addEventListener('click', () => {
            // Change Background
            body.style.background = "linear-gradient(45deg, #ff0a54, #ff7096)";
            
            // Transform Container
            container.classList.add('success');
            noBtn.classList.add('hidden');
            yesBtn.classList.add('hidden');
            
            // Dynamic Marriage Text
            question.innerHTML = "Yay! 🥰<br><span style='font-size: 0.6em; color: white;'>I can't wait to get married to you! 💍</span>";
            
            // Intense celebration particles
            setInterval(() => {
                spawnParticle('🌹');
                spawnParticle('❤️');
                spawnParticle('💖');
                spawnParticle('🥂');
            }, 100);

            // Confetti Blast Effect
            for(let i=0; i<50; i++) {
                setTimeout(() => spawnParticle('🌸'), i * 20);
            }
        });
    </script>
</body>
</html>

