# Valentine-
"A special surprise for the most amazing girl in the world. ❤️"
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>A Message For You ❤️</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            font-family: 'Georgia', serif;
            background: linear-gradient(135deg, #ffc1cc, #ffafbd);
            overflow: hidden;
            transition: background 1.5s ease;
        }

        #main-card {
            background: rgba(255, 255, 255, 0.4);
            padding: 40px;
            border-radius: 30px;
            backdrop-filter: blur(10px);
            box-shadow: 0 10px 30px rgba(214, 51, 132, 0.2);
            text-align: center;
            z-index: 10;
            border: 2px solid rgba(255, 255, 255, 0.5);
        }

        h1 {
            color: #d63384;
            font-size: 2.5rem;
            margin-bottom: 30px;
            text-shadow: 1px 1px 2px white;
        }

        .btn-container {
            display: flex;
            justify-content: center;
            gap: 20px;
            height: 60px;
            position: relative;
        }

        button {
            padding: 12px 35px;
            font-size: 1.2rem;
            border-radius: 50px;
            border: none;
            cursor: pointer;
            font-weight: bold;
            transition: transform 0.2s ease;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        #yesBtn {
            background-color: #ff4d6d;
            color: white;
        }

        #noBtn {
            background-color: #ffffff;
            color: #ff4d6d;
            position: absolute;
            left: 170px; /* Initial position */
        }

        /* Floating Animation */
        .floating {
            position: absolute;
            pointer-events: none;
            z-index: 1;
            animation: floatUp 4s linear infinite;
        }

        @keyframes floatUp {
            0% { transform: translateY(110vh) rotate(0deg); opacity: 1; }
            100% { transform: translateY(-10vh) rotate(360deg); opacity: 0; }
        }

        /* Celebration Screen */
        .celebration-bg {
            background: linear-gradient(135deg, #ff0a54, #ff7096) !important;
        }

        .celebration-text {
            color: white !important;
            font-family: 'Brush Script MT', cursive;
            font-size: 3.5rem !important;
            line-height: 1.2;
        }
    </style>
</head>
<body id="body">

    <div id="main-card">
        <h1 id="headline">Will you be my Valentine? ❤️</h1>
        <div class="btn-container">
            <button id="yesBtn" onclick="accept()">Yes</button>
            <button id="noBtn">No</button>
        </div>
    </div>

    <script>
        const noBtn = document.getElementById('noBtn');
        const body = document.getElementById('body');
        const card = document.getElementById('main-card');
        const headline = document.getElementById('headline');

        // Logic to make "No" button dodge the cursor
        noBtn.addEventListener('mouseover', () => {
            const x = Math.random() * (window.innerWidth - noBtn.offsetWidth);
            const y = Math.random() * (window.innerHeight - noBtn.offsetHeight);
            
            noBtn.style.left = `${x}px`;
            noBtn.style.top = `${y}px`;
            noBtn.style.position = 'fixed'; // Allows it to move anywhere on screen
        });

        // Function to create floating elements (hearts/roses)
        function spawnFloating(symbol) {
            const el = document.createElement('div');
            el.innerHTML = symbol;
            el.classList.add('floating');
            el.style.left = Math.random() * 100 + 'vw';
            el.style.fontSize = (Math.random() * 20 + 20) + 'px';
            el.style.animationDuration = (Math.random() * 2 + 3) + 's';
            document.body.appendChild(el);
            
            setTimeout(() => el.remove(), 4000);
        }

        // Start with a few hearts
        setInterval(() => spawnFloating('❤️'), 500);

        // What happens when she clicks YES
        function accept() {
            body.classList.add('celebration-bg');
            card.style.background = "transparent";
            card.style.border = "none";
            card.style.boxShadow = "none";
            
            headline.innerHTML = "Can't wait to get married to you! 💍";
            headline.classList.add('celebration-text');
            
            // Hide buttons
            document.querySelector('.btn-container').style.display = 'none';

            // Rain down roses and hearts heavily
            setInterval(() => spawnFloating('🌹'), 150);
            setInterval(() => spawnFloating('❤️'), 200);
            setInterval(() => spawnFloating('💖'), 300);
        }
    </script>
</body>
</html>
