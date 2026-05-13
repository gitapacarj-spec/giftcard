
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kartu Ucapan Selamat</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #828fc9 0%, #e68ccb 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
        }
 
        .card-container {
            perspective: 1000px;
        }

        .card {
            width: 350px;
            height: 500px;
            position: relative;
            transform-style: preserve-3d;
            transition: transform 0.8s;
            cursor: pointer;
        }

        .card.flipped {
            transform: rotateY(180deg);
        }

        .card-front, .card-back {
            position: absolute;
            width: 100%;
            height: 100%;
            backface-visibility: hidden;
            border-radius: 20px;
            box-shadow: 0 20px 40px rgb(240, 173, 196);
            overflow: hidden;
            background: linear-gradient(135deg, #ffeaa7, #fab1a0); color: #eca5cd;
        }

        .card-front {
            background: linear-gradient(45deg, #eda8a8, #acd6e7, #ff9ff3, #54a0ff);
            background-size: 400% 400%;
            animation: gradientShift 3s ease infinite;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            color: white;
        }

        .card-back {
            background: linear-gradient(135deg, #a8edea 0%, #fed6e3 100%);
            transform: rotateY(180deg);
            padding: 40px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        .confetti {
            position: absolute;
            width: 10px;
            height: 10px;
            background: #ff6b6b;
            animation: confetti-fall 3s linear infinite;
        }

        .confetti:nth-child(2) { background: #feca57; left: 20%; animation-delay: 0.5s; }
        .confetti:nth-child(3) { background: #54a0ff; left: 40%; animation-delay: 1s; }
        .confetti:nth-child(4) { background: #ff9ff3; left: 60%; animation-delay: 1.5s; }
        .confetti:nth-child(5) { background: #5f27cd; left: 80%; animation-delay: 2s; }

        h1 {
            font-size: 2.5em;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgb(236, 141, 190);
            animation: bounce 2s infinite;
        }

        .emoji {
            font-size: 4em;
            margin-bottom: 20px;
            animation: float 3s ease-in-out infinite;
        }

        .btn-flip {
            background: rgba(255,255,255,0.2);
            border: none;
            padding: 15px 30px;
            border-radius: 50px;
            color: white;
            font-size: 18px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            backdrop-filter: blur(10px);
        }

        .btn-flip:hover {
            background: rgba(255,255,255,0.3);
            transform: scale(1.05);
        }

        .message {
            font-size: 1.3em;
            line-height: 1.6;
            margin-bottom: 20px;
            text-align: center;
        }

        .sender {
            font-size: 1.1em;
            color: #d04c4c;
            text-align: right;
            font-style: italic;
        }

        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        @keyframes confetti-fall {
            0% {
                transform: translateY(-100vh) rotate(0deg);
                opacity: 1;
            }
            100% {
                transform: translateY(100vh) rotate(720deg);
                opacity: 0;
            }
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
            40% { transform: translateY(-10px); }
            60% { transform: translateY(-5px); }
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-20px); }
        }

        @media (max-width: 400px) {
            .card {
                width: 300px;
                height: 450px;
            }
            h1 { font-size: 2em; }
        }
    </style>
</head>
<body>
    <div class="card-container">
        <div class="card" id="card">
            <!-- FRONT SIDE -->
            <div class="card-front">
                <div class="confetti"></div>
                <div class="confetti"></div>
                <div class="confetti"></div>
                <div class="confetti"></div>
                <div class="confetti"></div>
                
                <div class="emoji">❤️✨</div>
                <h1>Halo sayangkuu</h1>
                <p style="font-size: 1.2em; margin-bottom: 30px;">
                    click for gift me love! <br>
                    Supricess! 🎊🎁
                </p>
                <button class="btn-flip" onclick="flipCard()">OPEN❤️</button>
            </div>

            <!-- BACK SIDE -->
            <div class="card-back">
                <div>
                    <div style="font-size: 2.5em; margin-bottom: 20px; text-align: center;">❤️❤️❤️</div>
                    <div class="message">
                        I love u so muchh, sayangku! 
                        <br><br>
                        Semoga sukses terus dan semoga di tahun ini menjadi awal dari 
                        <strong>banyak keberhasilan lainnya!</strong> 
                        <br><br>
                        Tetap semangat dan jaga konsistensi! 💪✨❤️
                    </div>
                </div>
                <div class="sender">
                    - from your lovee ❤️
                </div>
            </div>
        </div>
    </div>

    <script>
        
    let isFlipped = false;

    function flipCard() {
        const card = document.getElementById('card');
        card.classList.toggle('flipped');
        isFlipped = !isFlipped;
        
        // Hanya buat konfeti sekali saat pertama flip
        if (!isFlipped) {
            createConfetti();
        }
    }

    function createConfetti() {
        for (let i = 0; i < 50; i++) {
            setTimeout(() => {
                const confetti = document.createElement('div');
                confetti.className = 'confetti';
                confetti.style.left = Math.random() * 100 + '%';
                confetti.style.backgroundColor = `hsl(${Math.random() * 360}, 70%, 60%)`;
                confetti.style.animationDuration = (Math.random() * 3 + 2) + 's';
                document.body.appendChild(confetti);
                
                setTimeout(() => confetti.remove(), 5000);
            }, i * 20);
        }
    }

    
</script>
</body>
</html>
