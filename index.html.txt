<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Will You Be My Valentine? 💕</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@400;700&family=Poppins:wght@300;400;600&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 50%, #fecfef 100%);
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
            animation: sparkle 3s ease-in-out infinite alternate;
        }
        
        @keyframes sparkle {
            0% { background-position: 0% 50%; }
            100% { background-position: 100% 50%; }
        }
        
        .container {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
            position: relative;
            z-index: 10;
        }
        
        .heart {
            position: absolute;
            width: 20px;
            height: 18px;
            background: #ff6b9d;
            transform: rotate(-45deg);
            animation: float 6s ease-in-out infinite;
        }
        
        .heart:before,
        .heart:after {
            content: '';
            width: 20px;
            height: 18px;
            position: absolute;
            background: #ff6b9d;
            border-radius: 50% 50% 50% 50% / 60% 60% 40% 40%;
            transform: rotate(-45deg);
            transform-origin: 0 100%;
        }
        
        .heart:before {
            transform: rotate(-90deg) translate(-11px, -5px);
        }
        
        .heart:after {
            left: 10px;
            transform: rotate(90deg) translate(0px, -11px);
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(-45deg); opacity: 0; }
            10%, 90% { opacity: 1; }
            50% { transform: translateY(-20px) rotate(-45deg); }
        }
        
        .title {
            font-family: 'Dancing Script', cursive;
            font-size: clamp(2.5rem, 8vw, 6rem);
            font-weight: 700;
            color: #fff;
            text-shadow: 0 4px 8px rgba(0,0,0,0.3);
            text-align: center;
            margin-bottom: 40px;
            animation: bounce 2s ease-in-out infinite;
            position: relative;
            z-index: 20;
        }
        
        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
            40% { transform: translateY(-10px); }
            60% { transform: translateY(-5px); }
        }
        
        .buttons {
            display: flex;
            flex-direction: column;
            gap: 25px;
            align-items: center;
        }
        
        .btn {
            padding: 18px 40px;
            font-size: 1.3rem;
            font-weight: 600;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s cubic-bezier(0.68, -0.55, 0.265, 1.55);
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
            position: relative;
            overflow: hidden;
            text-decoration: none;
            display: inline-block;
            min-width: 150px;
            text-align: center;
        }
        
        .btn-yes {
            background: linear-gradient(45deg, #ff6b9d, #c44569);
            color: white;
        }
        
        .btn-yes:hover {
            transform: translateY(-5px) scale(1.05);
            box-shadow: 0 20px 40px rgba(255, 107, 157, 0.4);
        }
        
        .btn-no {
            background: linear-gradient(45deg, #f093fb, #f5576c);
            color: white;
            animation: wiggle 0.5s ease-in-out infinite alternate;
        }
        
        @keyframes wiggle {
            0% { transform: translateX(0) rotate(0deg); }
            100% { transform: translateX(5px) rotate(2deg); }
        }
        
        .btn-no.moving {
            position: fixed;
            z-index: 100;
            animation: dodge 0.5s ease-in-out infinite alternate;
            pointer-events: auto;
        }
        
        @keyframes dodge {
            0% {
                transform: translate(0, 0) rotate(0deg);
            }
            25% {
                transform: translate(20px, -20px) rotate(5deg);
            }
            50% {
                transform: translate(-10px, 10px) rotate(-3deg);
            }
            75% {
                transform: translate(15px, 15px) rotate(2deg);
            }
            100% {
                transform: translate(-5px, -10px) rotate(-1deg);
            }
        }
        
        .success {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 40px;
            border-radius: 25px;
            text-align: center;
            font-size: 1.5rem;
            box-shadow: 0 20px 60px rgba(0,0,0,0.5);
            z-index: 1000;
            animation: popIn 0.5s ease-out;
            max-width: 90vw;
        }
        
        @keyframes popIn {
            0% { transform: translate(-50%, -50%) scale(0); opacity: 0; }
            100% { transform: translate(-50%, -50%) scale(1); opacity: 1; }
        }
        
        .hearts-explosion {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            pointer-events: none;
            z-index: 999;
        }
        
        .heart-explosion {
            position: absolute;
            font-size: 24px;
            animation: explode 2s ease-out forwards;
        }
        
        @keyframes explode {
            0% {
                transform: scale(0) rotate(0deg);
                opacity: 1;
            }
            100% {
                transform: scale(2) rotate(720deg) translate(var(--dx), var(--dy));
                opacity: 0;
            }
        }
        
        @media (max-width: 768px) {
            .title { margin-bottom: 30px; }
            .btn { padding: 15px 30px; font-size: 1.1rem; }
        }
    </style>
</head>
<body>
    <!-- Floating hearts background -->
    <div class="heart" style="left: 10%; animation-delay: 0s;"></div>
    <div class="heart" style="left: 20%; animation-delay: 1s;"></div>
    <div class="heart" style="left: 80%; animation-delay: 2s;"></div>
    <div class="heart" style="left: 90%; animation-delay: 3s;"></div>
    <div class="heart" style="left: 30%; animation-delay: 4s;"></div>
    <div class="heart" style="left: 60%; animation-delay: 5s;"></div>

    <div class="container">
        <h1 class="title">Will you be my Valentine? 💕✨</h1>
        <div class="buttons">
            <a href="#yes" class="btn btn-yes" onclick="showYes()">💖 Yes! 💖</a>
            <button class="btn btn-no" id="noBtn" onclick="showNo()">😅 No...</button>
        </div>
    </div>

    <script>
        let noClicked = false;
        
        function showYes() {
            document.body.innerHTML = `
                <div class="success">
                    <div style="font-size: 3rem; margin-bottom: 20px;">🎉 YAYYY! 🎉</div>
                    <div style="font-size: 1.3rem; line-height: 1.6;">
                        You made my heart skip a beat! 💓<br>
                        Let's make this Valentine's magical! ✨
                    </div>
                </div>
                <div class="hearts-explosion" id="heartsExplosion"></div>
            `;
            
            // Create hearts explosion
            const explosion = document.getElementById('heartsExplosion');
            const hearts = ['💖', '💕', '💗', '💝', '🌹', '✨'];
            for (let i = 0; i < 30; i++) {
                const heart = document.createElement('div');
                heart.className = 'heart-explosion';
                heart.innerHTML = hearts[Math.floor(Math.random() * hearts.length)];
                heart.style.left = Math.random() * 100 + '%';
                heart.style.top = Math.random() * 100 + '%';
                heart.style.setProperty('--dx', (Math.random() - 0.5) * 200 + 'px');
                heart.style.setProperty('--dy', (Math.random() - 0.5) * 200 + 'px');
                heart.style.animationDelay = Math.random() * 0.5 + 's';
                explosion.appendChild(heart);
            }
        }
        
        function showNo() {
            if (noClicked) return;
            noClicked = true;
            
            const noBtn = document.getElementById('noBtn');
            noBtn.classList.add('moving');
            noBtn.innerHTML = '💔 Try again? 💔';
            
            // Reset after 3 seconds
            setTimeout(() => {
                noBtn.classList.remove('moving');
                noBtn.innerHTML = '😅 No...';
                noClicked = false;
            }, 3000);
        }
        
        // Make No button follow mouse (elusive!)
        document.addEventListener('mousemove', (e) => {
            const noBtn = document.getElementById('noBtn');
            if (noBtn.classList.contains('moving')) {
                const rect = noBtn.getBoundingClientRect();
                const btnCenterX = rect.left + rect.width / 2;
                const btnCenterY = rect.top + rect.height / 2;
                
                const distX = e.clientX - btnCenterX;
                const distY = e.clientY - btnCenterY;
                const distance = Math.sqrt(distX * distX + distY * distY);
                
                if (distance < 100) {
                    noBtn.style.transform = `translate(${20 - distX / 10}px, ${20 - distY / 10}px) rotate(${distX / 20}deg)`;
                }
            }
        });
    </script>
</body>
</html>
