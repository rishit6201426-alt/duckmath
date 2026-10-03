<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Minimal Arcade</title>
    <style>
        :root {
            --bg-color: #121212;
            --card-bg: #1e1e1e;
            --text-color: #ffffff;
            --accent-color: #3b82f6;
        }

        body {
            font-family: system-ui, -apple-system, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            margin: 0;
            padding: 20px;
        }

        header {
            text-align: center;
            margin-bottom: 40px;
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 20px;
            max-width: 1200px;
            margin: 0 auto;
        }

        .card {
            background-color: var(--card-bg);
            border-radius: 8px;
            padding: 15px;
            text-align: center;
            cursor: pointer;
            transition: transform 0.2s, box-shadow 0.2s;
            border: 1px solid #333;
        }

        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(59, 130, 246, 0.4);
        }

        .card h3 {
            margin: 10px 0 0 0;
            font-size: 1.1rem;
        }

        /* Fullscreen Game Frame Overlay */
        #game-container {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            background: #000;
            z-index: 1000;
        }

        iframe {
            width: 100%;
            height: 100%;
            border: none;
        }

        #close-btn {
            position: absolute;
            top: 20px;
            right: 20px;
            background: var(--accent-color);
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 5px;
            cursor: pointer;
            font-weight: bold;
            z-index: 1001;
        }
    </style>
</head>
<body>

    <header>
        <h1>My Custom Game Hub</h1>
        <p>Select a game to play instantly.</p>
    </header>

    <!-- Game Grid -->
    <div class="grid">
        <!-- Game 1 -->
        <div class="card" onclick="playGame('https://pacman.com')">
            <h3>Pac-Man</h3>
        </div>
        
        <!-- Game 2 (Example using a local repository relative folder) -->
        <div class="card" onclick="playGame('./games/snake/index.html')">
            <h3>Snake (Local)</h3>
        </div>
    </div>

    <!-- Active Game Viewport -->
    <div id="game-container">
        <button id="close-btn" onclick="closeGame()">✕ Close Game</button>
        <iframe id="game-frame" src="" sandbox="allow-scripts allow-same-origin allow-forms"></iframe>
    </div>

    <script>
        function playGame(url) {
            const container = document.getElementById('game-container');
            const frame = document.getElementById('game-frame');
            frame.src = url;
            container.style.display = 'block';
        }

        function closeGame() {
            const container = document.getElementById('game-container');
            const frame = document.getElementById('game-frame');
            frame.src = '';
            container.style.display = 'none';
        }
    </script>
</body>
</html>
