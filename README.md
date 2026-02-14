<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sevgililer Günümüz Kutlu Olsun!</title>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Montserrat:wght@300;700&display=swap" rel="stylesheet">
    <style>
        body {
            margin: 0;
            padding: 0;
            background: #050505;
            color: #fff;
            font-family: 'Montserrat', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow: hidden;
            text-align: center;
        }

        #player { position: absolute; top: -100px; left: -100px; width: 1px; height: 1px; }

        .container {
            z-index: 10;
            background: rgba(20, 20, 20, 0.8);
            padding: 3rem;
            border-radius: 20px;
            border: 1px solid #ff0055;
            box-shadow: 0 0 40px rgba(255, 0, 85, 0.4);
            backdrop-filter: blur(10px);
            max-width: 80%;
        }

        h1 {
            font-family: 'Dancing Script', cursive;
            font-size: 3.5rem;
            margin-bottom: 1rem;
            background: linear-gradient(to right, #ff0055, #ff7700);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .message {
            font-size: 1.2rem;
            line-height: 1.8;
            color: #eee;
            margin-bottom: 2rem;
        }

        .highlight {
            color: #ff0055;
            font-weight: 700;
        }

        .btn-start {
            background: #ff0055;
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 50px;
            font-size: 1rem;
            font-weight: bold;
            cursor: pointer;
            transition: 0.3s;
            box-shadow: 0 5px 15px rgba(255, 0, 85, 0.4);
        }

        .btn-start:hover { transform: scale(1.05); background: #e6004c; }

        .heart {
            position: absolute;
            color: #ff0055;
            user-select: none;
            pointer-events: none;
            animation: moveHeart linear forwards;
        }

        @keyframes moveHeart {
            0% { transform: translateY(100vh) scale(0); opacity: 1; }
            100% { transform: translateY(-10vh) scale(1.2); opacity: 0; }
        }
    </style>
</head>
<body onclick="startSurprise()">

    <div id="player"></div>

    <div class="container" id="mainCard">
        <h1>Sevgililer Günümüz Kutlu Olsun!</h1>
        <div class="message">
            "Güneşi gülüşüne nasıl sığdırdın?" diye başlıyor şarkı... <br>
            Benim güneşim de, neşem de, her şeyim de <span class="highlight">sensin</span>. <br>
            Belki her şeyi vaktinde yetiştiremiyorum ama seni sevmeyi asla ihmal etmiyorum. <br>
            <b>İyi ki benimlesin, iyi ki hayatımdasın.</b>
        </div>
        <button class="btn-start">Sürprizi Başlat ❤️</button>
    </div>

    <script src="https://www.youtube.com/iframe_api"></script>
    <script>
        let player;
        function onYouTubeIframeAPIReady() {
            player = new YT.Player('player', {
                height: '0',
                width: '0',
                videoId: '-x5LnDSctk0', // Ezhel - Felaket
                playerVars: { 
                    'start': 13, 
                    'autoplay': 1, 
                    'controls': 0, 
                    'modestbranding': 1,
                    'loop': 1
                },
                events: { 'onReady': (e) => { e.target.mute(); e.target.playVideo(); } }
            });
        }

        function startSurprise() {
            if(player) {
                player.unMute();
                player.setVolume(80);
            }
            document.querySelector('.btn-start').innerHTML = "Seni Çok Seviyorum!";
            setInterval(createHeart, 150);
        }

        function createHeart() {
            const heart = document.createElement('div');
            heart.innerHTML = '❤️';
            heart.className = 'heart';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.fontSize = (Math.random() * 20 + 10) + 'px';
            heart.style.animationDuration = (Math.random() * 3 + 2) + 's';
            heart.style.opacity = Math.random();
            document.body.appendChild(heart);
            setTimeout(() => heart.remove(), 5000);
        }
    </script>
</body>
</html>
