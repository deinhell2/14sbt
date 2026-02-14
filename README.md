<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Seni Seviyorum!</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            background: #000;
            color: #fff;
            font-family: 'Segoe UI', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow: hidden;
            text-align: center;
        }

        /* Arka plan için gizli YouTube Player */
        #player { position: absolute; top: -100px; left: -100px; width: 1px; height: 1px; }

        .content {
            z-index: 10;
            background: rgba(0, 0, 0, 0.7);
            padding: 3rem;
            border-radius: 30px;
            border: 2px solid #ff0055;
            box-shadow: 0 0 30px #ff0055;
            cursor: pointer;
        }

        h1 {
            font-size: 2.5rem;
            margin-bottom: 0.5rem;
            color: #ff0055;
            text-transform: uppercase;
        }

        .lyrics {
            font-style: italic;
            color: #ffd700;
            margin-bottom: 2rem;
        }

        .btn-play {
            background: #ff0055;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 50px;
            font-weight: bold;
            animation: pulse 1.5s infinite;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }

        .heart { position: absolute; color: #ff0055; pointer-events: none; animation: fly linear forwards; }
        @keyframes fly {
            from { transform: translateY(100vh) scale(0); opacity: 1; }
            to { transform: translateY(-10vh) scale(1.5); opacity: 0; }
        }
    </style>
</head>
<body onclick="playMusic()">

    <div id="player"></div>

    <div class="content">
        <p class="lyrics">"Güneşi gülüşüne nasıl sığdırdın? <br> Döndürür kalbimi çöle..."</p>
        <h1>Seni Çok Seviyorum!</h1>
        <p>İyi ki hayatımdasın, iyi ki varsın.</p>
        <div class="btn-play">Müziği Başlatmak İçin Tıkla ❤️</div>
    </div>

    <script src="https://www.youtube.com/iframe_api"></script>
    <script>
        let player;
        function onYouTubeIframeAPIReady() {
            player = new YT.Player('player', {
                height: '0',
                width: '0',
                videoId: '-x5LnDSctk0',
                playerVars: { 'start': 13, 'autoplay': 1, 'controls': 0 },
                events: { 'onReady': onPlayerReady }
            });
        }
        function onPlayerReady(event) { event.target.mute(); event.target.playVideo(); }
        function playMusic() { 
            player.unMute(); 
            document.querySelector('.btn-play').style.display = 'none';
        }

        function createHeart() {
            const heart = document.createElement('div');
            heart.innerHTML = '❤️';
            heart.className = 'heart';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = (Math.random() * 3 + 2) + 's';
            document.body.appendChild(heart);
            setTimeout(() => heart.remove(), 5000);
        }
        setInterval(createHeart, 200);
    </script>
</body>
</html>
