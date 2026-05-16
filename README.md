# survival-race-2026
survival race 2026
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
    <title>Гонки на выживание</title>
    <style>
        :root {
            --bg-primary: #0a0a14;
            --bg-secondary: #12122a;
            --accent: #e94560;
            --gold: #f9ca24;
            --text: #e0e0e0;
            --text-secondary: #8888aa;
            --card-bg: rgba(20, 20, 40, 0.9);
            --border: rgba(255, 255, 255, 0.1);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
            -webkit-user-select: none;
            user-select: none;
            -webkit-touch-callout: none;
        }

        body {
            background: #0a0a14;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            height: 100dvh;
            font-family: 'Inter', 'Segoe UI', system-ui, sans-serif;
            overflow: hidden;
        }

        .desktop-layout {
            display: flex;
            gap: 20px;
            align-items: stretch;
        }

        .side-panel {
            display: flex;
            flex-direction: column;
            gap: 12px;
            min-width: 220px;
            max-width: 220px;
        }

        .panel-card {
            background: var(--card-bg);
            border: 1px solid var(--border);
            border-radius: 16px;
            padding: 18px;
            backdrop-filter: blur(20px);
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
        }

        .panel-title {
            font-size: 10px;
            text-transform: uppercase;
            letter-spacing: 3px;
            color: var(--text-secondary);
            margin-bottom: 12px;
            font-weight: 600;
        }

        .stat-row {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
        }

        .stat-label {
            color: var(--text-secondary);
            font-size: 13px;
            font-weight: 500;
        }

        .stat-value {
            font-size: 24px;
            font-weight: 700;
            color: #fff;
        }
        .stat-value.accent { color: var(--accent); }
        .stat-value.gold { color: var(--gold); font-size: 18px; }
        .stat-value.small { font-size: 18px; }
        .stat-value.armor { color: #5dade2; font-size: 18px; }

        .level-badge {
            display: inline-block;
            background: rgba(233, 69, 96, 0.2);
            border: 1px solid var(--accent);
            border-radius: 20px;
            padding: 4px 14px;
            color: var(--accent);
            font-weight: 700;
            font-size: 14px;
        }

        .armor-bar-container {
            width: 100%;
            height: 8px;
            background: rgba(255,255,255,0.1);
            border-radius: 4px;
            margin-top: 6px;
            overflow: hidden;
        }

        .armor-bar-fill {
            height: 100%;
            background: linear-gradient(90deg, #3498db, #5dade2);
            border-radius: 4px;
            transition: width 0.3s ease;
        }

        .location-info {
            margin-top: 8px;
            padding-top: 10px;
            border-top: 1px solid var(--border);
        }
        .location-name {
            color: #fff;
            font-size: 14px;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 6px;
        }
        .location-icon { font-size: 20px; }
        .weather-status {
            font-size: 11px;
            color: var(--text-secondary);
            margin-top: 4px;
        }
        .weather-active {
            color: #f0932b;
            font-weight: 600;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.5; }
        }

        .car-mini-preview {
            width: 100%;
            height: 80px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 8px 0;
        }
        .car-details {
            font-size: 11px;
            color: var(--text-secondary);
            text-align: center;
        }
        .car-details span { color: #fff; font-weight: 600; }

        .desktop-controls-hint {
            display: flex;
            gap: 12px;
            justify-content: center;
            font-size: 11px;
            color: var(--text-secondary);
            margin-top: 8px;
            flex-wrap: wrap;
        }
        .key-hint {
            background: rgba(255, 255, 255, 0.08);
            padding: 4px 10px;
            border-radius: 6px;
            font-weight: 600;
            color: #fff;
            font-size: 11px;
        }

        .game-container-desktop {
            position: relative;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 20px 60px rgba(0,0,0,0.5), 0 0 60px rgba(233,69,96,0.15);
            border: 2px solid rgba(255,255,255,0.06);
        }

        /* МОБИЛЬНЫЙ */
        .mobile-layout {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 8px;
            width: 100%;
            max-width: 500px;
            height: 100vh;
            height: 100dvh;
            padding: 8px;
        }

        .top-panel {
            display: flex;
            gap: 6px;
            width: 100%;
            flex-shrink: 0;
        }

        .stat-chip {
            flex: 1;
            background: var(--card-bg);
            border: 1px solid var(--border);
            border-radius: 12px;
            padding: 8px 10px;
            text-align: center;
        }
        .stat-chip-label {
            font-size: 9px;
            text-transform: uppercase;
            letter-spacing: 1.5px;
            color: var(--text-secondary);
            margin-bottom: 2px;
            font-weight: 600;
        }
        .stat-chip-value {
            font-size: 18px;
            font-weight: 700;
            color: #fff;
        }
        .stat-chip-value.accent { color: var(--accent); }
        .stat-chip-value.gold { color: var(--gold); font-size: 15px; }
        .stat-chip-value.small { font-size: 14px; }
        .stat-chip-value.armor { color: #5dade2; font-size: 14px; }

        .mobile-armor-bar {
            width: 100%;
            height: 4px;
            background: rgba(255,255,255,0.1);
            border-radius: 2px;
            margin-top: 2px;
            overflow: hidden;
        }
        .mobile-armor-fill {
            height: 100%;
            background: linear-gradient(90deg, #3498db, #5dade2);
            border-radius: 2px;
            transition: width 0.3s ease;
        }

        .game-container-mobile {
            position: relative;
            width: 100%;
            flex: 1;
            min-height: 0;
            border-radius: 16px;
            overflow: hidden;
            border: 2px solid rgba(255,255,255,0.08);
            box-shadow: 0 10px 40px rgba(0,0,0,0.5);
        }

        canvas {
            display: block;
            width: 100%;
            height: 100%;
            border-radius: 14px;
        }

        .game-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            background: rgba(0,0,0,0.9);
            z-index: 10;
            border-radius: 14px;
            padding: 15px;
        }
        .game-overlay.hidden { display: none; }

        .overlay-title {
            font-size: 30px;
            font-weight: 800;
            color: var(--accent);
            text-shadow: 0 0 30px rgba(233,69,96,0.5);
            letter-spacing: 2px;
            margin-bottom: 4px;
        }
        .overlay-subtitle {
            font-size: 10px;
            color: var(--text-secondary);
            letter-spacing: 3px;
            text-transform: uppercase;
            margin-bottom: 18px;
        }
        .overlay-balance {
            background: rgba(249,202,36,0.15);
            border: 1px solid rgba(249,202,36,0.3);
            padding: 6px 16px;
            border-radius: 16px;
            color: var(--gold);
            font-weight: 600;
            font-size: 13px;
            margin-bottom: 14px;
        }

        .car-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 6px;
            margin-bottom: 14px;
            width: 100%;
            max-width: 300px;
        }
        .car-card-mini {
            background: rgba(255,255,255,0.03);
            border: 2px solid rgba(255,255,255,0.06);
            border-radius: 10px;
            padding: 6px;
            cursor: pointer;
            text-align: center;
            transition: all 0.15s ease;
        }
        .car-card-mini:active { transform: scale(0.95); }
        .car-card-mini.selected {
            border-color: var(--accent);
            background: rgba(233,69,96,0.2);
            box-shadow: 0 0 15px rgba(233,69,96,0.3);
        }
        .car-card-mini.locked { opacity: 0.4; filter: grayscale(40%); }
        .car-card-mini canvas { width: 40px; height: 48px; margin: 0 auto 2px; display: block; }
        .car-card-name {
            font-size: 8px;
            color: #fff;
            font-weight: 600;
        }
        .car-card-price { font-size: 8px; color: var(--gold); }
        .car-card-owned { font-size: 8px; color: #4ecdc4; }

        .difficulty-row {
            display: flex;
            gap: 8px;
            margin-bottom: 14px;
        }
        .diff-dot {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            border: 2px solid rgba(255,255,255,0.2);
            background: rgba(255,255,255,0.03);
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 18px;
            transition: all 0.15s ease;
            position: relative;
        }
        .diff-dot:active { transform: scale(0.9); }
        .diff-dot.selected {
            border-color: var(--accent);
            background: rgba(233,69,96,0.2);
            box-shadow: 0 0 12px rgba(233,69,96,0.3);
        }
        .diff-warning {
            position: absolute;
            bottom: -16px;
            font-size: 7px;
            color: #ff6b6b;
            white-space: nowrap;
            font-weight: 600;
        }

        .btn {
            padding: 10px 20px;
            border: 1px solid var(--border);
            border-radius: 20px;
            background: rgba(255,255,255,0.04);
            color: #fff;
            font-size: 13px;
            cursor: pointer;
            transition: all 0.15s ease;
            font-weight: 500;
            font-family: inherit;
        }
        .btn:active { transform: scale(0.95); }
        .btn.primary {
            background: var(--accent);
            border: none;
            font-weight: 600;
            font-size: 15px;
            padding: 12px 30px;
            box-shadow: 0 4px 15px rgba(233,69,96,0.3);
        }
        .btn.shop-btn {
            background: rgba(249,202,36,0.15);
            border-color: rgba(249,202,36,0.3);
            color: var(--gold);
            font-size: 12px;
            padding: 8px 16px;
        }
        .btn.restart-btn {
            background: rgba(255,255,255,0.06);
            border-color: rgba(255,255,255,0.15);
            width: 100%;
            padding: 10px;
            font-size: 13px;
        }

        .btn-group {
            display: flex;
            gap: 8px;
            margin-bottom: 10px;
        }

        .controls-hint {
            display: flex;
            gap: 8px;
            justify-content: center;
            font-size: 10px;
            color: var(--text-secondary);
            flex-wrap: wrap;
        }

        .controls-bar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            width: 100%;
            flex-shrink: 0;
            gap: 10px;
            padding: 0 5px;
        }

        .arrow-btn {
            width: 70px;
            height: 70px;
            border-radius: 50%;
            background: rgba(255,255,255,0.06);
            border: 2px solid rgba(255,255,255,0.2);
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.1s ease;
            touch-action: manipulation;
        }
        .arrow-btn:active, .arrow-btn.pressed {
            background: rgba(233,69,96,0.3);
            border-color: var(--accent);
            transform: scale(0.9);
            box-shadow: 0 0 20px rgba(233,69,96,0.4);
        }
        .arrow-icon { font-size: 32px; color: #fff; pointer-events: none; }

        .center-btns {
            display: flex;
            flex-direction: column;
            gap: 8px;
            align-items: center;
        }
        .action-btn {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: rgba(255,255,255,0.06);
            border: 2px solid rgba(255,255,255,0.2);
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.1s ease;
            font-size: 20px;
            color: #fff;
        }
        .action-btn:active { background: rgba(255,255,255,0.15); transform: scale(0.9); }
        .action-label { font-size: 8px; color: var(--text-secondary); text-align: center; }

        @media (max-height: 700px) {
            .arrow-btn { width: 55px; height: 55px; }
            .arrow-icon { font-size: 26px; }
            .action-btn { width: 40px; height: 40px; font-size: 16px; }
        }
        @media (min-width: 420px) {
            .arrow-btn { width: 80px; height: 80px; }
            .arrow-icon { font-size: 36px; }
        }
    </style>
</head>
<body>
    <div class="desktop-layout" id="desktopLayout">
        <div class="side-panel">
            <div class="panel-card">
                <div class="panel-title">📊 Статистика</div>
                <div class="stat-row"><span class="stat-label">Очки</span><span class="stat-value accent" id="dScore">0</span></div>
                <div class="stat-row"><span class="stat-label">Монеты</span><span class="stat-value gold" id="dCoins">🪙 0</span></div>
                <div class="stat-row"><span class="stat-label">Рекорд</span><span class="stat-value small" id="dHighScore">0</span></div>
                <div class="stat-row"><span class="stat-label">Скорость</span><span class="stat-value small" id="dSpeed">0 км/ч</span></div>
                <div class="stat-row"><span class="stat-label">Броня</span><span class="stat-value armor" id="dArmor">🛡️ 0</span></div>
                <div class="armor-bar-container"><div class="armor-bar-fill" id="dArmorBar" style="width:100%"></div></div>
                <div class="stat-row" style="margin-top:8px;padding-top:8px;border-top:1px solid var(--border);">
                    <span class="stat-label">Уровень</span><span class="level-badge" id="dLevel">1</span>
                </div>
            </div>
            <div class="panel-card">
                <div class="panel-title">🏎️ Машина</div>
                <div class="car-mini-preview"><canvas id="dCarPreview" width="180" height="70"></canvas></div>
                <div class="car-details" id="dCarDetails"><span>Спорт</span></div>
            </div>
            <div class="panel-card location-info">
                <div class="panel-title">📍 Локация</div>
                <div class="location-name"><span class="location-icon" id="dLocIcon">🏙️</span><span id="dLocName">Город</span></div>
                <div class="weather-status" id="dWeather">☀️ Ясно</div>
            </div>
            <button class="btn restart-btn" id="dRestartBtn">🔄 Перезапустить</button>
        </div>
        <div class="game-container-desktop" style="width:500px;height:700px;">
            <canvas id="desktopCanvas"></canvas>
            <div class="game-overlay" id="dMenuOverlay">
                <div class="overlay-title">ГОНКИ</div>
                <div class="overlay-subtitle">Бесконечные уровни</div>
                <div class="overlay-balance" id="dMenuBalance">🪙 0 монет</div>
                <div class="difficulty-row" id="dDifficultyRow">
                    <div class="diff-dot" data-diff="0">😊</div>
                    <div class="diff-dot selected" data-diff="1">😎</div>
                    <div class="diff-dot" data-diff="2">🔥</div>
                    <div class="diff-dot" data-diff="3">💀<span class="diff-warning">СБРОС</span></div>
                </div>
                <div class="car-grid" id="dCarGrid"></div>
                <div class="btn-group">
                    <button class="btn shop-btn" id="dShopBtn">🏪 Магазин</button>
                    <button class="btn primary" id="dPlayBtn">▶ ИГРАТЬ</button>
                </div>
                <div class="desktop-controls-hint">
                    <span class="key-hint">← →</span> или <span class="key-hint">A D</span>
                    <span class="key-hint">R</span> рестарт
                    <span class="key-hint">ПРОБЕЛ</span> пауза
                    <span class="key-hint">ESC</span> меню
                </div>
            </div>
            <div class="game-overlay hidden" id="dShopOverlay">
                <div style="position:absolute;top:10px;left:10px;"><button class="btn" style="padding:6px 12px;font-size:11px;" id="dShopBackBtn">← Назад</button></div>
                <div class="overlay-title" style="font-size:24px;">МАГАЗИН</div>
                <div class="overlay-subtitle">Покупай машины</div>
                <div class="overlay-balance" id="dShopBalance">🪙 0 монет</div>
                <div class="car-grid" id="dShopCarGrid" style="grid-template-columns:repeat(3,1fr);max-width:280px;"></div>
            </div>
            <div class="game-overlay hidden" id="dPauseOverlay">
                <div class="overlay-title" style="font-size:28px;">ПАУЗА</div>
                <div style="color:var(--text-secondary);margin-bottom:16px;font-size:13px;">ПРОБЕЛ — продолжить</div>
                <div class="btn-group">
                    <button class="btn" id="dPauseRestartBtn">🔄 Рестарт</button>
                    <button class="btn" id="dPauseMenuBtn">🏠 Меню</button>
                </div>
            </div>
        </div>
    </div>

    <div class="mobile-layout" id="mobileLayout">
        <div class="top-panel">
            <div class="stat-chip"><div class="stat-chip-label">Очки</div><div class="stat-chip-value accent" id="mScore">0</div></div>
            <div class="stat-chip"><div class="stat-chip-label">Монеты</div><div class="stat-chip-value gold" id="mCoins">🪙 0</div></div>
            <div class="stat-chip"><div class="stat-chip-label">Рекорд</div><div class="stat-chip-value small" id="mHighScore">0</div></div>
            <div class="stat-chip"><div class="stat-chip-label">Уровень</div><div class="stat-chip-value small" id="mLevel" style="color:#e94560;">1</div></div>
            <div class="stat-chip">
                <div class="stat-chip-label">Броня</div>
                <div class="stat-chip-value armor" id="mArmor">🛡️ 0</div>
                <div class="mobile-armor-bar"><div class="mobile-armor-fill" id="mArmorBar" style="width:100%"></div></div>
            </div>
        </div>
        <div class="game-container-mobile">
            <canvas id="mobileCanvas"></canvas>
            <div class="game-overlay" id="mMenuOverlay">
                <div class="overlay-title">ГОНКИ</div>
                <div class="overlay-subtitle">Выживание</div>
                <div class="overlay-balance" id="mMenuBalance">🪙 0 монет</div>
                <div class="difficulty-row" id="mDifficultyRow">
                    <div class="diff-dot" data-diff="0">😊</div>
                    <div class="diff-dot selected" data-diff="1">😎</div>
                    <div class="diff-dot" data-diff="2">🔥</div>
                    <div class="diff-dot" data-diff="3">💀<span class="diff-warning">СБРОС</span></div>
                </div>
                <div class="car-grid" id="mCarGrid"></div>
                <div class="btn-group">
                    <button class="btn shop-btn" id="mShopBtn">🏪 Магазин</button>
                    <button class="btn primary" id="mPlayBtn">▶ ИГРАТЬ</button>
                </div>
                <div class="controls-hint">
                    <span class="key-hint">← →</span> стрелки
                    <span class="key-hint">⏯</span> пауза
                    <span class="key-hint">🔄</span> рестарт
                </div>
            </div>
            <div class="game-overlay hidden" id="mShopOverlay">
                <div style="position:absolute;top:10px;left:10px;"><button class="btn" style="padding:6px 12px;font-size:11px;" id="mShopBackBtn">← Назад</button></div>
                <div class="overlay-title" style="font-size:24px;">МАГАЗИН</div>
                <div class="overlay-subtitle">Покупай машины</div>
                <div class="overlay-balance" id="mShopBalance">🪙 0 монет</div>
                <div class="car-grid" id="mShopCarGrid" style="grid-template-columns:repeat(3,1fr);max-width:280px;"></div>
            </div>
            <div class="game-overlay hidden" id="mPauseOverlay">
                <div class="overlay-title" style="font-size:28px;">ПАУЗА</div>
                <div style="color:var(--text-secondary);margin-bottom:16px;font-size:13px;">Нажми ⏯ для продолжения</div>
                <div class="btn-group">
                    <button class="btn" id="mPauseRestartBtn">🔄 Рестарт</button>
                    <button class="btn" id="mPauseMenuBtn">🏠 Меню</button>
                </div>
            </div>
        </div>
        <div class="controls-bar">
            <button class="arrow-btn" id="mLeftBtn"><span class="arrow-icon">◀</span></button>
            <div class="center-btns"><button class="action-btn restart" id="mRestartBtn">🔄</button><span class="action-label">РЕСТАРТ</span></div>
            <div class="center-btns"><button class="action-btn pause" id="mPauseBtn">⏯</button><span class="action-label">ПАУЗА</span></div>
            <button class="arrow-btn" id="mRightBtn"><span class="arrow-icon">▶</span></button>
        </div>
    </div>

    <script>
        function isMobileDevice() {
            const isWindows = /Windows/i.test(navigator.userAgent);
            const isMac = /Macintosh/i.test(navigator.userAgent) && !/iPhone|iPad|iPod/i.test(navigator.userAgent);
            const isLinuxDesktop = /Linux/i.test(navigator.userAgent) && !/Android/i.test(navigator.userAgent);
            if (isWindows || isMac || isLinuxDesktop) return false;
            const isAndroid = /Android/i.test(navigator.userAgent);
            const isIOS = /iPhone|iPad|iPod/i.test(navigator.userAgent);
            if (isAndroid || isIOS) return true;
            return window.innerWidth < 768;
        }

        const mobileDevice = isMobileDevice();
        document.getElementById('desktopLayout').style.display = mobileDevice ? 'none' : 'flex';
        document.getElementById('mobileLayout').style.display = mobileDevice ? 'flex' : 'none';

        const prefix = mobileDevice ? 'm' : 'd';
        const canvas = document.getElementById(mobileDevice ? 'mobileCanvas' : 'desktopCanvas');
        const gameWrapper = canvas.parentElement;

        let WIDTH, HEIGHT;

        function resizeCanvas() {
            if (mobileDevice) {
                const rect = gameWrapper.getBoundingClientRect();
                const dpr = Math.min(window.devicePixelRatio || 1, 2);
                WIDTH = rect.width;
                HEIGHT = rect.height;
                canvas.width = WIDTH * dpr;
                canvas.height = HEIGHT * dpr;
                canvas.style.width = WIDTH + 'px';
                canvas.style.height = HEIGHT + 'px';
                canvas.getContext('2d').setTransform(1, 0, 0, 1, 0, 0);
                canvas.getContext('2d').scale(dpr, dpr);
            } else {
                WIDTH = 500;
                HEIGHT = 700;
                canvas.width = WIDTH;
                canvas.height = HEIGHT;
                canvas.style.width = WIDTH + 'px';
                canvas.style.height = HEIGHT + 'px';
            }
        }

        window.addEventListener('resize', resizeCanvas);
        window.addEventListener('orientationchange', () => setTimeout(resizeCanvas, 150));
        resizeCanvas();

        function gE(id) { return document.getElementById(prefix + id); }

        // ============ ИГРОВЫЕ ПЕРЕМЕННЫЕ ============
        let score = 0;
        let highScore = parseInt(localStorage.getItem('racingGameHS2') || '0');
        let coins = parseInt(localStorage.getItem('racingGameCoins2') || '0');
        let gameOver = true;
        let gameStarted = false;
        let gamePaused = false;
        let gameSpeed = 5;
        let frameCount = 0;
        let roadOffset = 0;
        let selectedCarIndex = 0;
        let difficulty = 1;
        let currentLocation = 0;
        let sandstormActive = false;
        let sandstormTimer = 0;
        let sandstormAlpha = 0;
        let locationTimer = 0;
        let nextLocationChange = 600;
        let currentLevel = 1;
        const levelScoreThreshold = 100;
        let levelTransition = false;
        let levelTransitionTimer = 0;
        let invulnerabilityTimer = 0;
        let armor = 0;
        let maxArmor = 0;

        const difficultySettings = [
            { name: 'Легко', baseSpeed: 4, speedIncrease: 0.2, spawnRate: 75, freqIncrease: 1.2, coinMult: 0.5, levelSpeedBoost: 0.3, deathPenalty: 1 },
            { name: 'Средне', baseSpeed: 5, speedIncrease: 0.4, spawnRate: 55, freqIncrease: 2, coinMult: 1, levelSpeedBoost: 0.5, deathPenalty: 1 },
            { name: 'Сложно', baseSpeed: 6.5, speedIncrease: 0.65, spawnRate: 38, freqIncrease: 2.8, coinMult: 1.8, levelSpeedBoost: 0.8, deathPenalty: 2 },
            { name: 'Экстрим', baseSpeed: 8, speedIncrease: 1, spawnRate: 25, freqIncrease: 3.5, coinMult: 3, levelSpeedBoost: 1.2, deathPenalty: 999 }
        ];

        const allCars = [
            { id: 0, name: 'Спорт', color: '#e94560', speed: 7, handling: 1.0, w: 50, h: 90, price: 0, owned: true, armor: 0, desc: 'Сбалансированный' },
            { id: 1, name: 'Маслкар', color: '#f9ca24', speed: 8.5, handling: 0.65, w: 58, h: 98, price: 350, owned: false, armor: 0, desc: 'Мощный' },
            { id: 2, name: 'Дрифт', color: '#4ecdc4', speed: 6, handling: 1.4, w: 46, h: 85, price: 250, owned: false, armor: 0, desc: 'Маневренный' },
            { id: 3, name: 'Внедорожник', color: '#27ae60', speed: 5.5, handling: 1.0, w: 68, h: 115, price: 550, owned: false, armor: 2, desc: 'Широкий, +2 брони' },
            { id: 4, name: 'Лимузин', color: '#8e44ad', speed: 4.5, handling: 0.7, w: 48, h: 140, price: 900, owned: false, armor: 1, desc: 'Длинный, +1 брони' },
            { id: 5, name: 'Грузовик', color: '#e67e22', speed: 3.5, handling: 0.55, w: 65, h: 125, price: 450, owned: false, armor: 2, desc: 'Большой, +2 брони' },
            { id: 6, name: 'Монстр-трак', color: '#c0392b', speed: 4, handling: 0.8, w: 75, h: 120, price: 1200, owned: false, armor: 3, desc: 'Огромный, +3 брони' },
            { id: 7, name: 'Гоночный', color: '#3498db', speed: 10.5, handling: 1.15, w: 44, h: 100, price: 1800, owned: false, armor: 0, desc: 'Макс. скорость' },
            { id: 8, name: 'Кабриолет', color: '#1abc9c', speed: 7.5, handling: 1.25, w: 54, h: 102, price: 700, owned: false, armor: 1, desc: 'Быстрый, +1 брони' },
            { id: 9, name: 'Броневик', color: '#556b7a', speed: 3, handling: 0.5, w: 70, h: 110, price: 2500, owned: false, armor: 5, desc: '🛡️ Танк! +5 брони' }
        ];

        function loadData() {
            const ownedData = localStorage.getItem('racingGameOwned2');
            if (ownedData) {
                JSON.parse(ownedData).forEach(id => { const c = allCars.find(x => x.id === id); if (c) c.owned = true; });
            }
            allCars[0].owned = true;
        }

        function saveData() {
            localStorage.setItem('racingGameOwned2', JSON.stringify(allCars.filter(c => c.owned).map(c => c.id)));
            localStorage.setItem('racingGameCoins2', coins.toString());
            localStorage.setItem('racingGameHS2', highScore.toString());
        }

        loadData();

        function applyCarStats() {
            const car = allCars[selectedCarIndex];
            player.speed = car.speed;
            player.handling = car.handling;
            player.color = car.color;
            player.width = car.w;
            player.height = car.h;
            maxArmor = car.armor;
            armor = maxArmor;
            updateArmorUI();
        }

        const player = { x: WIDTH/2-25, y: HEIGHT-160, width: 50, height: 90, speed: 7, handling: 1.0, color: '#e94560' };
        let obstacles = [];
        const keys = { left: false, right: false };
        const obstacleColors = ['#ff6b6b','#a29bfe','#fd79a8','#00b894','#e17055','#0984e3','#6c5ce7','#fdcb6e','#e84393','#00cec9'];
        const locations = [
            { name: 'Город', roadGradient: ['#1a1a1a','#2d2d2d','#1a1a1a'], borderColor: '#ff4444', markingColor: '#fff', bgBuildings: true },
            { name: 'Пустыня', roadGradient: ['#b8953a','#d4b36a','#b8953a'], borderColor: '#8b6914', markingColor: '#f0d890', bgBuildings: false }
        ];

        function changeLocation() {
            currentLocation = (currentLocation+1)%2;
            locationTimer=0;
            nextLocationChange=400+Math.floor(Math.random()*400);
            sandstormActive = (currentLocation===1 && Math.random()<0.3);
            if (sandstormActive) sandstormTimer=300+Math.floor(Math.random()*500);
            else { sandstormTimer=0; sandstormAlpha=0; }
            updateLocationUI();
        }

        function updateLocationUI() {
            const icon = gE('LocIcon'); if (icon) icon.textContent = currentLocation===0?'🏙️':'🏜️';
            const name = gE('LocName'); if (name) name.textContent = locations[currentLocation].name;
            const w = gE('Weather');
            if (w) {
                if (sandstormActive) w.innerHTML='<span class="weather-active">🌪️ Песчаная буря!</span>';
                else w.textContent = currentLocation===1?'☀️ Солнечно':'☁️ Облачно';
            }
        }

        function updateArmorUI() {
            const armorEl = gE('Armor'); if (armorEl) armorEl.textContent = `🛡️ ${armor}`;
            const armorBar = gE('ArmorBar');
            if (armorBar) {
                const pct = maxArmor > 0 ? (armor / maxArmor) * 100 : 0;
                armorBar.style.width = pct + '%';
                if (pct > 60) armorBar.style.background = 'linear-gradient(90deg, #3498db, #5dade2)';
                else if (pct > 30) armorBar.style.background = 'linear-gradient(90deg, #f39c12, #f1c40f)';
                else armorBar.style.background = 'linear-gradient(90deg, #e74c3c, #c0392b)';
            }
        }

        function levelUp() {
            currentLevel++;
            levelTransition=true; levelTransitionTimer=90;
            gameSpeed+=difficultySettings[difficulty].levelSpeedBoost;
            obstacles=[];
            coins+=Math.floor(currentLevel*5*difficultySettings[difficulty].coinMult);
            // Восстановление брони при повышении уровня
            armor = Math.min(maxArmor, armor + 1);
            saveData(); updateAllUI();
        }

        function handleDeath() {
            const ds=difficultySettings[difficulty];
            if (difficulty===3) { fullReset(); return; }
            
            // Если есть броня - теряем броню вместо уровня
            if (armor > 0) {
                armor--;
                invulnerabilityTimer = 90;
                obstacles = [];
                player.x = WIDTH/2 - player.width/2;
                gameOver = false;
                gameStarted = true;
                levelTransition = false;
                updateArmorUI();
                updateAllUI();
                return;
            }
            
            // Нет брони - штраф уровня
            currentLevel=Math.max(1, currentLevel-ds.deathPenalty);
            score=(currentLevel-1)*levelScoreThreshold;
            gameSpeed=Math.max(ds.baseSpeed, gameSpeed-ds.levelSpeedBoost*ds.deathPenalty*2);
            obstacles=[]; invulnerabilityTimer=120;
            player.x=WIDTH/2-player.width/2;
            armor = maxArmor;
            gameOver=false; gameStarted=true; levelTransition=false;
            updateArmorUI();
            updateAllUI();
        }

        function fullReset() {
            currentLevel=1; score=0; gameSpeed=difficultySettings[difficulty].baseSpeed;
            obstacles=[]; invulnerabilityTimer=0; levelTransition=false;
            applyCarStats();
            player.x=WIDTH/2-player.width/2;
            gameOver=false; gameStarted=true; gamePaused=false;
            sandstormActive=false; sandstormAlpha=0; locationTimer=0;
            updateAllUI(); updateLocationUI();
        }

        function resetLevel() {
            currentLevel=1; score=0; invulnerabilityTimer=0;
            applyCarStats();
            player.x=WIDTH/2-player.width/2;
            obstacles=[]; gameSpeed=difficultySettings[difficulty].baseSpeed;
            frameCount=0; gameOver=false; gameStarted=true; gamePaused=false;
            levelTransition=false; sandstormActive=false; sandstormAlpha=0; locationTimer=0;
            updateAllUI(); updateLocationUI();
            gE('MenuOverlay').classList.add('hidden');
            gE('ShopOverlay').classList.add('hidden');
            gE('PauseOverlay').classList.add('hidden');
        }

        // ============ ОТРИСОВКА ============
        function rR(x,y,w,h,r) {
            const ctx=canvas.getContext('2d');
            ctx.beginPath(); ctx.moveTo(x+r,y); ctx.lineTo(x+w-r,y);
            ctx.quadraticCurveTo(x+w,y,x+w,y+r); ctx.lineTo(x+w,y+h-r);
            ctx.quadraticCurveTo(x+w,y+h,x+w-r,y+h); ctx.lineTo(x+r,y+h);
            ctx.quadraticCurveTo(x,y+h,x,y+h-r); ctx.lineTo(x,y+r);
            ctx.quadraticCurveTo(x,y,x+r,y); ctx.closePath();
        }

        function lC(hex,p) {
            const n=parseInt(hex.replace('#',''),16);
            return `rgb(${Math.min(255,(n>>16)+p)},${Math.min(255,((n>>8)&0xFF)+p)},${Math.min(255,(n&0xFF)+p)})`;
        }

        function drawBackground() {
            const ctx=canvas.getContext('2d');
            const loc=locations[currentLocation];
            if (loc.bgBuildings) {
                const g=ctx.createLinearGradient(0,0,0,HEIGHT);
                g.addColorStop(0,'#0a0a1a'); g.addColorStop(0.3,'#1a1a3a'); g.addColorStop(1,'#2d2d4a');
                ctx.fillStyle=g; ctx.fillRect(0,0,WIDTH,HEIGHT);
                ctx.fillStyle='#111122';
                for (let i=0;i<8;i++) { const bx=i*65; if(bx>WIDTH)break; ctx.fillRect(bx,HEIGHT-120-(i%3)*40,35,100+(i%3)*60); }
            } else {
                const g=ctx.createLinearGradient(0,0,0,HEIGHT);
                g.addColorStop(0,'#f7d794'); g.addColorStop(0.3,'#f5cd79'); g.addColorStop(1,'#d4a853');
                ctx.fillStyle=g; ctx.fillRect(0,0,WIDTH,HEIGHT);
                ctx.fillStyle='#b8956a'; ctx.beginPath(); ctx.moveTo(0,HEIGHT-120);
                for (let i=0;i<=WIDTH;i+=40) ctx.lineTo(i,HEIGHT-140-Math.sin(i*0.02)*50);
                ctx.lineTo(WIDTH,HEIGHT); ctx.lineTo(0,HEIGHT); ctx.fill();
                ctx.fillStyle='#fff9e6'; ctx.beginPath(); ctx.arc(Math.min(400,WIDTH-60),70,40,0,Math.PI*2); ctx.fill();
            }
        }

        function drawRoad() {
            const ctx=canvas.getContext('2d');
            const loc=locations[currentLocation];
            const g=ctx.createLinearGradient(0,0,0,HEIGHT);
            g.addColorStop(0,loc.roadGradient[0]); g.addColorStop(0.5,loc.roadGradient[1]); g.addColorStop(1,loc.roadGradient[2]);
            ctx.fillStyle=g; ctx.fillRect(WIDTH*0.06,0,WIDTH*0.88,HEIGHT);
            ctx.fillStyle='#1a1a1a'; ctx.fillRect(0,0,WIDTH*0.06,HEIGHT); ctx.fillRect(WIDTH*0.94,0,WIDTH*0.06,HEIGHT);
            ctx.fillStyle=loc.borderColor; ctx.fillRect(WIDTH*0.055,0,WIDTH*0.01,HEIGHT); ctx.fillRect(WIDTH*0.935,0,WIDTH*0.01,HEIGHT);
            roadOffset=(roadOffset+gameSpeed*1.5)%50;
            ctx.strokeStyle=loc.markingColor; ctx.lineWidth=mobileDevice?1.5:2;
            ctx.setLineDash([18,28]); ctx.lineDashOffset=-roadOffset;
            [WIDTH*0.38,WIDTH*0.62].forEach(lx=>{ctx.beginPath();ctx.moveTo(lx,0);ctx.lineTo(lx,HEIGHT);ctx.stroke();});
            ctx.setLineDash([]);
        }

        function drawCar(x,y,w,h,color,isP=false,isInv=false,showArmor=false) {
            const ctx=canvas.getContext('2d');
            ctx.save();
            if (isInv && Math.floor(Date.now()/100)%2===0) ctx.globalAlpha=0.5;
            ctx.shadowColor='rgba(0,0,0,0.5)'; ctx.shadowBlur=10; ctx.shadowOffsetY=4;
            
            // Броня - свечение
            if (showArmor && armor > 0) {
                ctx.shadowColor = 'rgba(52, 152, 219, 0.6)';
                ctx.shadowBlur = 15 + armor * 3;
            }
            
            const bg=ctx.createLinearGradient(x,y,x+w,y);
            bg.addColorStop(0,color); bg.addColorStop(0.5,lC(color,30)); bg.addColorStop(1,color);
            ctx.fillStyle=bg; rR(x,y,w,h,6); ctx.fill();
            
            // Бронепластины для бронированных машин
            if (showArmor && armor >= 3) {
                ctx.fillStyle = 'rgba(100, 110, 120, 0.4)';
                ctx.fillRect(x + 2, y + h*0.2, w - 4, h*0.15);
                ctx.fillRect(x + 2, y + h*0.65, w - 4, h*0.15);
            }
            
            ctx.fillStyle='rgba(0,0,0,0.15)'; rR(x+w*0.2,y+h*0.15,w*0.6,h*0.55,3); ctx.fill();
            ctx.fillStyle='#a8d8ea'; ctx.shadowBlur=2; rR(x+w*0.12,y+h*0.1,w*0.76,h*0.16,2); ctx.fill();
            ctx.fillStyle='#fffde7'; ctx.shadowColor='#fffde7'; ctx.shadowBlur=8;
            ctx.fillRect(x+w*0.08,y+2,w*0.18,h*0.05); ctx.fillRect(x+w*0.74,y+2,w*0.18,h*0.05);
            ctx.fillStyle='#ff4444'; ctx.shadowColor='#ff4444'; ctx.shadowBlur=4;
            ctx.fillRect(x+w*0.08,y+h-h*0.06,w*0.18,h*0.04); ctx.fillRect(x+w*0.74,y+h-h*0.06,w*0.18,h*0.04);
            ctx.fillStyle='#1a1a1a'; ctx.fillRect(x+w*0.3,y+1,w*0.4,h*0.04);
            
            ctx.fillStyle='#1a1a1a'; ctx.shadowBlur=3;
            const ww=w*0.2, wh=h*0.22;
            ctx.fillRect(x-ww*0.5,y+h*0.18,ww,wh); ctx.fillRect(x+w-ww*0.5,y+h*0.18,ww,wh);
            ctx.fillRect(x-ww*0.5,y+h-wh-h*0.08,ww,wh); ctx.fillRect(x+w-ww*0.5,y+h-wh-h*0.08,ww,wh);
            ctx.fillStyle='#aaa'; ctx.shadowBlur=1;
            const dw=ww*0.45, dh=wh*0.4;
            ctx.fillRect(x-ww*0.5+ww*0.28,y+h*0.18+wh*0.3,dw,dh);
            ctx.fillRect(x+w-ww*0.5+ww*0.28,y+h*0.18+wh*0.3,dw,dh);
            
            ctx.restore();
        }

        function drawSandstorm() {
            if (!sandstormActive) return;
            const ctx=canvas.getContext('2d');
            for (let l=0;l<2;l++) {
                ctx.fillStyle=`rgba(210,180,140,${sandstormAlpha*(0.1-l*0.04)})`; ctx.fillRect(0,0,WIDTH,HEIGHT);
            }
            ctx.fillStyle=`rgba(194,163,90,${sandstormAlpha*0.25})`;
            for (let i=0;i<sandstormAlpha*40;i++) {
                const px=(Math.sin(frameCount*0.02+i*7)*250+WIDTH/2+i*35)%WIDTH;
                const py=(frameCount*3+i*25)%(HEIGHT+40)-20;
                ctx.beginPath(); ctx.arc(px,py,1.5+Math.random()*2,0,Math.PI*2); ctx.fill();
            }
        }

        function drawLevelTransition() {
            if (!levelTransition) return;
            const ctx=canvas.getContext('2d');
            const a=levelTransitionTimer/90;
            ctx.fillStyle=`rgba(0,0,0,${a*0.7})`; ctx.fillRect(0,0,WIDTH,HEIGHT);
            ctx.fillStyle=`rgba(255,255,255,${a})`; ctx.font='bold 32px Inter'; ctx.textAlign='center';
            ctx.fillText(`УРОВЕНЬ ${currentLevel}`,WIDTH/2,HEIGHT/2-5);
            ctx.fillStyle=`rgba(249,202,36,${a})`; ctx.font='15px Inter';
            ctx.fillText(`+${Math.floor(currentLevel*5*difficultySettings[difficulty].coinMult)} монет!`,WIDTH/2,HEIGHT/2+28);
        }

        function avoidCollisions() {
            for (let i=0;i<obstacles.length;i++) {
                for (let j=i+1;j<obstacles.length;j++) {
                    const a=obstacles[i], b=obstacles[j];
                    const ox=Math.max(0,Math.min(a.x+a.width,b.x+b.width)-Math.max(a.x,b.x));
                    const oy=Math.max(0,Math.min(a.y+a.height,b.y+b.height)-Math.max(a.y,b.y));
                    if (ox>0&&oy>0) {
                        if (ox<oy) {
                            const px=ox/2+2;
                            if (a.x+a.width/2<b.x+b.width/2) {
                                a.x=Math.max(WIDTH*0.07,a.x-px); b.x=Math.min(WIDTH*0.93-b.width,b.x+px);
                            } else {
                                a.x=Math.min(WIDTH*0.93-a.width,a.x+px); b.x=Math.max(WIDTH*0.07,b.x-px);
                            }
                        } else { if (a.y<b.y){a.y-=3;b.y+=3;} else {a.y+=3;b.y-=3;} }
                    }
                }
            }
        }

        function spawnObstacle() {
            const margin=WIDTH*0.08;
            const cw=(30+Math.random()*35)*(WIDTH/500);
            const ch=(65+Math.random()*55)*(HEIGHT/700);
            let x, attempts=0, valid=false;
            while (!valid&&attempts<20) {
                x=margin+Math.random()*(WIDTH-margin*2-cw); valid=true;
                for (const obs of obstacles) {
                    if (obs.y<-ch+80 && Math.abs((x+cw/2)-(obs.x+obs.width/2))<(cw+obs.width)/2+10) {
                        valid=false; break;
                    }
                }
                attempts++;
            }
            if (!valid) x=margin+Math.random()*(WIDTH-margin*2-cw);
            const mult=1+(currentLevel-1)*0.15;
            obstacles.push({x, y:-ch-25, width:cw, height:ch, speed:(gameSpeed+Math.random()*5+1.5)*mult, color:obstacleColors[Math.floor(Math.random()*obstacleColors.length)]});
        }

        function checkCollision(p,obs) {
            return p.x<obs.x+obs.width && p.x+p.width>obs.x && p.y<obs.y+obs.height && p.y+p.height>obs.y;
        }

        function update() {
            if (!gameStarted||gameOver||gamePaused) return;
            if (levelTransition) { levelTransitionTimer--; if (levelTransitionTimer<=0) levelTransition=false; return; }
            if (invulnerabilityTimer>0) invulnerabilityTimer--;
            frameCount++;
            if (score>=currentLevel*levelScoreThreshold&&!levelTransition) levelUp();
            locationTimer++; if (locationTimer>nextLocationChange) changeLocation();
            if (sandstormActive) {
                if (sandstormTimer>0) { sandstormTimer--; sandstormAlpha=Math.min(0.75,sandstormAlpha+0.02); }
                else { sandstormAlpha=Math.max(0,sandstormAlpha-0.015); if (sandstormAlpha<=0) sandstormActive=false; }
            }
            const ds=difficultySettings[difficulty];
            if (frameCount%130===0) gameSpeed+=ds.speedIncrease;
            const move=player.speed*player.handling;
            const margin=WIDTH*0.07;
            if (keys.left&&player.x>margin) player.x-=move;
            if (keys.right&&player.x<WIDTH-player.width-margin) player.x+=move;
            const spawnRate=Math.max(14,ds.spawnRate-Math.floor(gameSpeed*ds.freqIncrease)-currentLevel*2);
            if (frameCount%spawnRate===0||(obstacles.length===0&&frameCount>20)) {
                spawnObstacle();
                if (gameSpeed>8&&Math.random()<0.3) spawnObstacle();
                if (gameSpeed>11&&Math.random()<0.2) spawnObstacle();
            }
            avoidCollisions();
            for (let i=obstacles.length-1;i>=0;i--) {
                obstacles[i].y+=obstacles[i].speed;
                if (invulnerabilityTimer<=0&&checkCollision(player,obstacles[i])) {
                    if (score>highScore) { highScore=score; saveData(); }
                    if (difficulty===3) { gameOver=true; gameStarted=false; fullReset(); gameOver=true; gameStarted=false; }
                    else handleDeath();
                    updateAllUI(); break;
                }
                if (obstacles[i].y>HEIGHT+140) {
                    obstacles.splice(i,1); score+=10;
                    coins+=Math.floor(3*ds.coinMult*(1+(currentLevel-1)*0.2));
                    saveData(); if (score>highScore) { highScore=score; saveData(); }
                    updateAllUI();
                }
            }
        }

        function draw() {
            const ctx=canvas.getContext('2d');
            ctx.clearRect(0,0,WIDTH,HEIGHT);
            if (gameStarted||!gameOver) {
                drawBackground(); drawRoad();
                obstacles.forEach(o=>drawCar(o.x,o.y,o.width,o.height,o.color,false,false,false));
                if (!gameOver&&!levelTransition) {
                    drawCar(player.x,player.y,player.width,player.height,player.color,true,invulnerabilityTimer>0,true);
                    // Индикатор брони над машиной
                    if (armor > 0) {
                        ctx.fillStyle='rgba(0,0,0,0.6)'; rR(player.x, player.y-22, player.width, 14, 4); ctx.fill();
                        ctx.fillStyle='#5dade2'; ctx.font='bold 10px Inter'; ctx.textAlign='center';
                        ctx.fillText('🛡️'.repeat(armor), player.x+player.width/2, player.y-11);
                    }
                }
                if (sandstormActive) drawSandstorm();
                if (levelTransition) drawLevelTransition();
                if (gameOver) {
                    ctx.fillStyle='rgba(0,0,0,0.85)'; ctx.fillRect(0,0,WIDTH,HEIGHT);
                    ctx.fillStyle='#fff'; ctx.font='bold 36px Inter'; ctx.textAlign='center';
                    ctx.fillText(difficulty===3?'ПОЛНЫЙ СБРОС!':'АВАРИЯ!',WIDTH/2,HEIGHT/2-20);
                    ctx.fillStyle='#aaa'; ctx.font='12px Inter';
                    ctx.fillText('Нажми 🔄 для рестарта',WIDTH/2,HEIGHT/2+42);
                }
                if (!gameOver||levelTransition) {
                    ctx.fillStyle='rgba(0,0,0,0.5)'; rR(WIDTH-90,8,80,25,6); ctx.fill();
                    ctx.fillStyle='#f9ca24'; ctx.font='bold 12px Inter'; ctx.textAlign='center';
                    ctx.fillText(`⚡ ${Math.floor(gameSpeed*18)}`,WIDTH-50,25);
                }
            }
            updatePanelStats();
        }

        function updatePanelStats() {
            const s=gE('Score'); if(s) s.textContent=score;
            const c=gE('Coins'); if(c) c.textContent=`🪙 ${coins}`;
            const h=gE('HighScore'); if(h) h.textContent=highScore;
            const l=gE('Level'); if(l) l.textContent=currentLevel;
            const sp=gE('Speed'); if(sp) sp.textContent=`${Math.floor(gameSpeed*18)} км/ч`;
            updateArmorUI();
        }

        function updateAllUI() {
            updatePanelStats();
            const mb=gE('MenuBalance'); if(mb) mb.textContent=`🪙 ${coins} монет`;
            const sb=gE('ShopBalance'); if(sb) sb.textContent=`🪙 ${coins} монет`;
        }

        function drawCarPreviewOnCanvas(cvs,car,locked=false) {
            if(!cvs)return;
            const pctx=cvs.getContext('2d');
            pctx.clearRect(0,0,cvs.width,cvs.height);
            if(locked)pctx.globalAlpha=0.35;
            const s=Math.min(cvs.width/car.w,cvs.height/car.h)*0.8;
            const cw=car.w*s,ch=car.h*s,cx=(cvs.width-cw)/2,cy=(cvs.height-ch)/2;
            pctx.fillStyle=car.color; pctx.fillRect(cx,cy,cw,ch);
            pctx.fillStyle='#a8d8ea'; pctx.fillRect(cx+cw*0.15,cy+ch*0.08,cw*0.7,ch*0.14);
            pctx.fillStyle='#1a1a1a';
            pctx.fillRect(cx-cw*0.08,cy+ch*0.2,cw*0.18,ch*0.2);
            pctx.fillRect(cx+cw*0.9,cy+ch*0.2,cw*0.18,ch*0.2);
            // Броня на превью
            if (car.armor >= 3) {
                pctx.fillStyle='rgba(100,110,120,0.5)';
                pctx.fillRect(cx+2,cy+ch*0.25,cw-4,ch*0.12);
                pctx.fillRect(cx+2,cy+ch*0.6,cw-4,ch*0.12);
            }
            pctx.globalAlpha=1;
        }

        function renderCarGrid() {
            const grid=gE('CarGrid'); if(!grid)return;
            grid.innerHTML='';
            allCars.forEach((car,i)=>{
                const card=document.createElement('div');
                card.className='car-card-mini';
                if(i===selectedCarIndex)card.classList.add('selected');
                if(!car.owned)card.classList.add('locked');
                const cvs=document.createElement('canvas');cvs.width=40;cvs.height=48;card.appendChild(cvs);
                const nm=document.createElement('div');nm.className='car-card-name';nm.textContent=car.name;card.appendChild(nm);
                const inf=document.createElement('div');
                inf.className=car.owned?'car-card-owned':'car-card-price';
                inf.textContent=car.owned?'✅':`🪙${car.price}`;
                card.appendChild(inf);
                if (car.armor > 0) {
                    const arm=document.createElement('div');
                    arm.style.cssText='font-size:7px;color:#5dade2;';
                    arm.textContent='🛡️'+car.armor;
                    card.appendChild(arm);
                }
                card.addEventListener('click',()=>{
                    if(car.owned){selectedCarIndex=i;renderCarGrid();updateCarPreview();applyCarStats();}
                    else if(coins>=car.price){
                        if(confirm(`Купить "${car.name}" за ${car.price} монет?\nБроня: ${car.armor}`)){
                            coins-=car.price;car.owned=true;selectedCarIndex=i;
                            saveData();renderCarGrid();renderShopGrid();updateAllUI();updateCarPreview();applyCarStats();
                        }
                    }else alert(`Не хватает ${car.price-coins} монет!`);
                });
                grid.appendChild(card);
                setTimeout(()=>drawCarPreviewOnCanvas(cvs,car,!car.owned),30);
            });
        }

        function renderShopGrid() {
            const grid=gE('ShopCarGrid'); if(!grid)return;
            grid.innerHTML='';
            allCars.forEach(car=>{
                const card=document.createElement('div');
                card.className='car-card-mini';
                if(!car.owned)card.classList.add('locked');
                const cvs=document.createElement('canvas');cvs.width=40;cvs.height=48;card.appendChild(cvs);
                const nm=document.createElement('div');nm.className='car-card-name';nm.textContent=car.name;card.appendChild(nm);
                const inf=document.createElement('div');
                inf.className=car.owned?'car-card-owned':'car-card-price';
                inf.textContent=car.owned?'✅':`🪙${car.price}`;
                card.appendChild(inf);
                if (car.armor > 0) {
                    const arm=document.createElement('div');
                    arm.style.cssText='font-size:7px;color:#5dade2;';
                    arm.textContent='🛡️'+car.armor;
                    card.appendChild(arm);
                }
                card.addEventListener('click',()=>{
                    if(!car.owned&&coins>=car.price){
                        if(confirm(`Купить "${car.name}" за ${car.price} монет?\nБроня: ${car.armor}`)){
                            coins-=car.price;car.owned=true;
                            saveData();renderCarGrid();renderShopGrid();updateAllUI();updateCarPreview();applyCarStats();
                        }
                    }else if(!car.owned)alert(`Не хватает ${car.price-coins} монет!`);
                });
                grid.appendChild(card);
                setTimeout(()=>drawCarPreviewOnCanvas(cvs,car,!car.owned),30);
            });
        }

        function updateCarPreview() {
            const cvs=gE('CarPreview');
            if(cvs)drawCarPreviewOnCanvas(cvs,allCars[selectedCarIndex],false);
            const det=gE('CarDetails');
            if(det)det.innerHTML=`<span>${allCars[selectedCarIndex].name}</span> | 🛡️${allCars[selectedCarIndex].armor}`;
        }

        // ============ УПРАВЛЕНИЕ ============
        applyCarStats();

        if (mobileDevice) {
            const lb=document.getElementById('mLeftBtn');
            const rb=document.getElementById('mRightBtn');
            [lb,rb].forEach((btn,idx)=>{
                if(!btn)return;
                btn.addEventListener('pointerdown',(e)=>{
                    e.preventDefault();
                    if(idx===0)keys.left=true; else keys.right=true;
                    btn.classList.add('pressed');
                });
                btn.addEventListener('pointerup',(e)=>{
                    e.preventDefault();
                    if(idx===0)keys.left=false; else keys.right=false;
                    btn.classList.remove('pressed');
                });
                btn.addEventListener('pointerleave',()=>{keys.left=false;keys.right=false;btn.classList.remove('pressed');});
                btn.addEventListener('pointercancel',()=>{keys.left=false;keys.right=false;btn.classList.remove('pressed');});
            });
            document.getElementById('mRestartBtn').addEventListener('click',()=>{if(gameStarted||gameOver)resetLevel();});
            document.getElementById('mPauseBtn').addEventListener('click',()=>{
                if(!gameStarted||gameOver)return;
                gamePaused=!gamePaused;
                if(gamePaused)gE('PauseOverlay').classList.remove('hidden');
                else gE('PauseOverlay').classList.add('hidden');
            });
            document.getElementById('mPlayBtn').addEventListener('click',resetLevel);
            document.getElementById('mShopBtn').addEventListener('click',()=>{
                gE('ShopOverlay').classList.remove('hidden'); gE('MenuOverlay').classList.add('hidden');
                renderShopGrid(); updateAllUI();
            });
            document.getElementById('mShopBackBtn').addEventListener('click',()=>{
                gE('ShopOverlay').classList.add('hidden'); gE('MenuOverlay').classList.remove('hidden');
            });
            document.getElementById('mPauseRestartBtn').addEventListener('click',()=>{
                gE('PauseOverlay').classList.add('hidden'); resetLevel();
            });
            document.getElementById('mPauseMenuBtn').addEventListener('click',()=>{
                gameStarted=false; gameOver=true; gamePaused=false;
                gE('PauseOverlay').classList.add('hidden'); gE('MenuOverlay').classList.remove('hidden');
                updateAllUI();
            });
            document.querySelectorAll('#mDifficultyRow .diff-dot').forEach(d=>{
                d.addEventListener('click',()=>{
                    document.querySelectorAll('#mDifficultyRow .diff-dot').forEach(x=>x.classList.remove('selected'));
                    d.classList.add('selected'); difficulty=parseInt(d.dataset.diff);
                });
            });
        } else {
            document.getElementById('dPlayBtn').addEventListener('click',resetLevel);
            document.getElementById('dRestartBtn').addEventListener('click',()=>{if(gameStarted||gameOver)resetLevel();});
            document.getElementById('dShopBtn').addEventListener('click',()=>{
                gE('ShopOverlay').classList.remove('hidden'); gE('MenuOverlay').classList.add('hidden');
                renderShopGrid(); updateAllUI();
            });
            document.getElementById('dShopBackBtn').addEventListener('click',()=>{
                gE('ShopOverlay').classList.add('hidden'); gE('MenuOverlay').classList.remove('hidden');
            });
            document.getElementById('dPauseRestartBtn').addEventListener('click',()=>{
                gE('PauseOverlay').classList.add('hidden'); resetLevel();
            });
            document.getElementById('dPauseMenuBtn').addEventListener('click',()=>{
                gameStarted=false; gameOver=true; gamePaused=false;
                gE('PauseOverlay').classList.add('hidden'); gE('MenuOverlay').classList.remove('hidden');
                updateAllUI();
            });
            document.querySelectorAll('#dDifficultyRow .diff-dot').forEach(d=>{
                d.addEventListener('click',()=>{
                    document.querySelectorAll('#dDifficultyRow .diff-dot').forEach(x=>x.classList.remove('selected'));
                    d.classList.add('selected'); difficulty=parseInt(d.dataset.diff);
                });
            });
        }

        document.addEventListener('keydown',(e)=>{
            if (e.key==='ArrowLeft'||e.key==='a'||e.key==='A'){keys.left=true;e.preventDefault();}
            if (e.key==='ArrowRight'||e.key==='d'||e.key==='D'){keys.right=true;e.preventDefault();}
            if (e.key===' '||e.key==='Spacebar'){
                if(gameOver)resetLevel();
                else if(gameStarted){
                    gamePaused=!gamePaused;
                    if(gamePaused)gE('PauseOverlay').classList.remove('hidden');
                    else gE('PauseOverlay').classList.add('hidden');
                }
                e.preventDefault();
            }
            if (e.key==='r'||e.key==='R'){if(gameStarted||gameOver)resetLevel();e.preventDefault();}
            if (e.key==='Escape'){
                gameStarted=false;gameOver=true;gamePaused=false;
                gE('MenuOverlay').classList.remove('hidden');
                gE('ShopOverlay').classList.add('hidden');
                gE('PauseOverlay').classList.add('hidden');
                updateAllUI();updateLocationUI();e.preventDefault();
            }
        });

        document.addEventListener('keyup',(e)=>{
            if (e.key==='ArrowLeft'||e.key==='a'||e.key==='A'){keys.left=false;e.preventDefault();}
            if (e.key==='ArrowRight'||e.key==='d'||e.key==='D'){keys.right=false;e.preventDefault();}
        });

        // ============ ЗАПУСК ============
        renderCarGrid();
        updateCarPreview();
        updateAllUI();
        updateLocationUI();

        function gameLoop() {
            update();
            draw();
            requestAnimationFrame(gameLoop);
        }
        gameLoop();
    </script>
</body>
</html>   
