Dmitry Mirnak Adapter
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
    <title>Dmitry Mirnak | Adapter</title>
    <style>
        :root {
            --bg: #000000;
            --bg2: #0a0a0a;
            --card: rgba(20, 20, 20, 0.85);
            --line: rgba(100, 100, 100, 0.2);
            --txt: #ffffff;
            --muted: #a0a0a0;
            --accent: #38bdf8;
            --accent2: #818cf8;
            --btn-bg: rgba(40, 40, 40, 0.6);
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: "Segoe UI", system-ui, sans-serif;
            color: var(--txt);
            background: radial-gradient(ellipse 900px 500px at 10% -10%, rgba(56, 189, 248, 0.15), transparent),
                        radial-gradient(ellipse 700px 400px at 100% 20%, rgba(129, 140, 248, 0.12), transparent),
                        linear-gradient(165deg, var(--bg), var(--bg2));
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 24px;
            margin: 0;
            transition: background 0.5s ease, color 0.3s ease;
            position: relative;
        }

        .video-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            object-fit: cover;
            z-index: -2;
        }

        .overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            z-index: -1;
            pointer-events: none;
        }

        body.custom-bg-active {
            background: var(--custom-bg-url) center/cover fixed !important;
        }

        body.custom-bg-active::before {
            content: "";
            position: fixed;
            top: 0; left: 0; right: 0; bottom: 0;
            background: rgba(0, 0, 0, 0.4);
            pointer-events: none;
            z-index: 0;
        }

        .wrap {
            max-width: 720px;
            width: 100%;
            margin: 0 auto;
            border-radius: 32px;
            border: 1px solid var(--line);
            box-shadow: 0 25px 80px rgba(0, 0, 0, 0.6), inset 0 1px 0 rgba(255,255,255,0.05);
            background: linear-gradient(145deg, var(--card), rgba(10, 10, 10, 0.8));
            padding: 30px 28px 28px;
            backdrop-filter: blur(16px);
            position: relative;
            z-index: 2;
        }

        .hero {
            text-align: center;
            margin-bottom: 28px;
        }

        h1 {
            font-size: 2.3rem;
            font-weight: 800;
            letter-spacing: -0.02em;
            background: linear-gradient(105deg, #ffffff, var(--accent2), var(--accent));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 8px;
        }

        .hero-sub {
            color: var(--muted);
            font-size: 14px;
            font-weight: 500;
            border-bottom: 1px solid var(--line);
            padding-bottom: 18px;
        }

        .nav-grid {
            display: flex;
            flex-direction: column;
            gap: 12px;
            margin-bottom: 24px;
        }

        .link-btn {
            display: flex;
            align-items: center;
            justify-content: space-between;
            width: 100%;
            padding: 16px 22px;
            background: var(--btn-bg);
            border: 1px solid var(--line);
            border-radius: 20px;
            color: var(--txt);
            text-decoration: none;
            font-weight: 600;
            font-size: 17px;
            backdrop-filter: blur(8px);
            transition: all 0.25s;
            box-shadow: 0 8px 12px -6px rgba(0, 0, 0, 0.4);
        }

        .link-btn:hover {
            background: rgba(56, 189, 248, 0.15);
            border-color: var(--accent);
            transform: translateY(-3px);
        }

        .link-btn i {
            color: var(--accent);
            font-size: 20px;
            transition: transform 0.2s;
        }

        .link-btn:hover i {
            transform: translateX(6px);
        }

        .btn-left {
            display: flex;
            align-items: center;
            gap: 16px;
        }

        .btn-left span:first-child {
            font-size: 22px;
            width: 28px;
            text-align: center;
        }

        .control-panel {
            margin-top: 16px;
            border-top: 1px solid var(--line);
            padding-top: 22px;
            display: flex;
            flex-wrap: wrap;
            align-items: center;
            justify-content: center;
            gap: 12px;
        }

        .ctrl-btn {
            background: var(--btn-bg);
            border: 1px solid var(--line);
            color: var(--txt);
            padding: 10px 16px;
            border-radius: 40px;
            font-size: 14px;
            font-weight: 600;
            cursor: pointer;
            backdrop-filter: blur(8px);
            transition: all 0.2s;
            display: inline-flex;
            align-items: center;
            gap: 8px;
        }

        .ctrl-btn:hover {
            background: var(--accent);
            color: #000;
            border-color: var(--accent);
        }

        .ctrl-btn.active {
            background: var(--accent);
            color: #000;
        }

        .file-upload-wrapper {
            position: relative;
            display: inline-block;
        }

        .file-upload-wrapper input {
            position: absolute;
            left: 0;
            top: 0;
            opacity: 0;
            width: 100%;
            height: 100%;
            cursor: pointer;
        }

        .audio-player {
            margin: 10px 0 0;
            width: 100%;
        }

        audio {
            width: 100%;
            height: 40px;
            border-radius: 40px;
            background: var(--btn-bg);
            backdrop-filter: blur(8px);
        }

        audio::-webkit-media-controls-panel {
            background: var(--card);
        }

        .custom-bg-panel {
            margin-top: 14px;
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .file-row {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
        }

        .file-btn {
            flex: 1;
            min-width: 140px;
        }

        .footer-note {
            margin-top: 20px;
            text-align: center;
            color: var(--muted);
            font-size: 13px;
            border-top: 1px solid var(--line);
            padding-top: 18px;
        }

        .reset-bg-btn {
            background: rgba(239, 68, 68, 0.3);
            border-color: rgba(239, 68, 68, 0.5);
        }

        .status-badge {
            font-size: 11px;
            margin-left: 8px;
            opacity: 0.8;
        }

        @media (max-width: 480px) {
            body { padding: 12px; }
            .wrap { padding: 24px 16px 20px; }
            h1 { font-size: 2rem; }
            .link-btn { padding: 14px 16px; font-size: 16px; }
            .control-panel { gap: 8px; }
            .ctrl-btn { padding: 8px 12px; font-size: 13px; }
        }
    </style>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
</head>
<body id="mainBody">
    <video id="videoBackground" class="video-bg" style="display: none;" loop muted playsinline></video>
    <div class="overlay" id="bgOverlay" style="display: none;"></div>

    <div class="wrap">
        <div class="hero">
            <h1>Dmitry Mirnak</h1>
            <div class="hero-sub">официальные ресурсы • official hub</div>
        </div>

        <div class="nav-grid">
            <a href="https://t.me/+EcKt9k-7qYAxNjYy" target="_blank" class="link-btn"><div class="btn-left"><span>📢</span><span>Официальный канал</span></div><i class="fas fa-arrow-right"></i></a>
            <a href="https://t.me/+TnG7x-J649wwYzVi" target="_blank" class="link-btn"><div class="btn-left"><span>📣</span><span>Второй канал</span></div><i class="fas fa-arrow-right"></i></a>
            <a href="https://t.me/+zzwkuey14-RlNTEy" target="_blank" class="link-btn"><div class="btn-left"><span>💬</span><span>Форум группа</span></div><i class="fas fa-arrow-right"></i></a>
            <a href="https://t.me/+dCKPaHcRcjNlY2Uy" target="_blank" class="link-btn"><div class="btn-left"><span>⭐</span><span>Отзывы</span></div><i class="fas fa-arrow-right"></i></a>
            <a href="https://t.me/psyhopizza" target="_blank" class="link-btn"><div class="btn-left"><span>🤖</span><span>Переходник на бот</span></div><i class="fas fa-arrow-right"></i></a>
            <a href="https://t.me/toncools" target="_blank" class="link-btn"><div class="btn-left"><span>👤</span><span>Официальный аккаунт</span></div><i class="fas fa-arrow-right"></i></a>
        </div>

        <div class="control-panel">
            <div class="file-upload-wrapper">
                <button class="ctrl-btn"><i class="fas fa-music"></i> Загрузить трек</button>
                <input type="file" id="audioUpload" accept="audio/*">
            </div>
            
            <button class="ctrl-btn" id="themeDark"><i class="fas fa-moon"></i> Тёмная</button>
            <button class="ctrl-btn" id="themeLight"><i class="fas fa-sun"></i> Светлая</button>
            <button class="ctrl-btn" id="themeCustom"><i class="fas fa-image"></i> Кастом</button>
            
            <button class="ctrl-btn" id="randomColorBtn"><i class="fas fa-dice"></i> Авто-цвет <span class="status-badge" id="autoColorStatus">⚪</span></button>
        </div>

        <div id="audioPlayerContainer" class="audio-player" style="display: none;">
            <audio id="audioPlayer" controls></audio>
        </div>

        <div id="customBgPanel" class="custom-bg-panel" style="display: none;">
            <div class="file-row">
                <div class="file-upload-wrapper file-btn">
                    <button class="ctrl-btn" style="width: 100%;"><i class="fas fa-image"></i> Фото из галереи</button>
                    <input type="file" id="imageUpload" accept="image/*">
                </div>
                <div class="file-upload-wrapper file-btn">
                    <button class="ctrl-btn" style="width: 100%;"><i class="fas fa-video"></i> Видео из галереи</button>
                    <input type="file" id="videoUpload" accept="video/*">
                </div>
            </div>
            
            <div style="display: flex; gap: 10px;">
                <button class="ctrl-btn reset-bg-btn" id="resetBgBtn" style="flex: 1;"><i class="fas fa-times"></i> Сбросить фон</button>
            </div>
            <p style="font-size: 12px; color: var(--muted); margin-top: 6px; text-align: center;">Видео без звука • Фото растягивается</p>
        </div>

        <div class="footer-note"><i class="fas fa-link"></i> dmitrymirnak • 2026 • v4.0</div>
    </div>

    <script>
        (function() {
            "use strict";

            const body = document.getElementById('mainBody');
            const root = document.documentElement;
            const videoBg = document.getElementById('videoBackground');
            const bgOverlay = document.getElementById('bgOverlay');
            
            // === СОХРАНЕНИЕ В LOCALSTORAGE ===
            const STORAGE_KEYS = {
                THEME: 'dmitry_theme',
                BG_TYPE: 'dmitry_bg_type',
                BG_DATA: 'dmitry_bg_data',
                AUDIO_SRC: 'dmitry_audio_src',
                AUDIO_TIME: 'dmitry_audio_time',
                AUTO_COLOR: 'dmitry_auto_color'
            };

            let autoColorInterval = null;
            let isAutoColorActive = false;

            // === 1. ЗАГРУЗКА ПЕСНИ С СОХРАНЕНИЕМ ===
            const audioUpload = document.getElementById('audioUpload');
            const audioContainer = document.getElementById('audioPlayerContainer');
            const audioPlayer = document.getElementById('audioPlayer');

            // Сохраняем позицию перед уходом
            window.addEventListener('beforeunload', function() {
                if (audioPlayer.src && !audioPlayer.paused) {
                    localStorage.setItem(STORAGE_KEYS.AUDIO_TIME, audioPlayer.currentTime);
                }
                if (audioPlayer.src) {
                    localStorage.setItem(STORAGE_KEYS.AUDIO_SRC, audioPlayer.src);
                }
            });

            // Восстанавливаем аудио
            const savedAudioSrc = localStorage.getItem(STORAGE_KEYS.AUDIO_SRC);
            const savedAudioTime = localStorage.getItem(STORAGE_KEYS.AUDIO_TIME);
            
            if (savedAudioSrc) {
                audioPlayer.src = savedAudioSrc;
                audioContainer.style.display = 'block';
                if (savedAudioTime) {
                    audioPlayer.currentTime = parseFloat(savedAudioTime);
                }
            }

            audioUpload.addEventListener('change', function(e) {
                const file = e.target.files[0];
                if (file) {
                    const url = URL.createObjectURL(file);
                    audioPlayer.src = url;
                    audioContainer.style.display = 'block';
                    audioPlayer.play();
                    localStorage.setItem(STORAGE_KEYS.AUDIO_SRC, url);
                }
            });

            // Автосохранение позиции каждые 5 секунд
            setInterval(() => {
                if (audioPlayer.src && !audioPlayer.paused) {
                    localStorage.setItem(STORAGE_KEYS.AUDIO_TIME, audioPlayer.currentTime);
                }
            }, 5000);

            // === 2. ТЕМЫ (ТЁМНАЯ ТЕМНЕЕ / СВЕТЛАЯ СВЕТЛЕЕ) ===
            const themeDark = document.getElementById('themeDark');
            const themeLight = document.getElementById('themeLight');
            const themeCustom = document.getElementById('themeCustom');
            const customBgPanel = document.getElementById('customBgPanel');
            const resetBgBtn = document.getElementById('resetBgBtn');
            const imageUpload = document.getElementById('imageUpload');
            const videoUpload = document.getElementById('videoUpload');

            function resetBackground() {
                videoBg.pause();
                videoBg.src = '';
                videoBg.style.display = 'none';
                bgOverlay.style.display = 'none';
                body.classList.remove('custom-bg-active');
                body.style.removeProperty('--custom-bg-url');
                localStorage.removeItem(STORAGE_KEYS.BG_TYPE);
                localStorage.removeItem(STORAGE_KEYS.BG_DATA);
            }

            function setDarkTheme() {
                resetBackground();
                root.style.setProperty('--bg', '#000000');
                root.style.setProperty('--bg2', '#050505');
                root.style.setProperty('--card', 'rgba(15, 15, 15, 0.9)');
                root.style.setProperty('--line', 'rgba(80, 80, 80, 0.2)');
                root.style.setProperty('--txt', '#ffffff');
                root.style.setProperty('--muted', '#999999');
                root.style.setProperty('--btn-bg', 'rgba(30, 30, 30, 0.7)');
                customBgPanel.style.display = 'none';
                localStorage.setItem(STORAGE_KEYS.THEME, 'dark');
            }

            function setLightTheme() {
                resetBackground();
                root.style.setProperty('--bg', '#ffffff');
                root.style.setProperty('--bg2', '#f5f5f5');
                root.style.setProperty('--card', 'rgba(255, 255, 255, 0.95)');
                root.style.setProperty('--line', 'rgba(0, 0, 0, 0.1)');
                root.style.setProperty('--txt', '#111111');
                root.style.setProperty('--muted', '#555555');
                root.style.setProperty('--accent', '#0066cc');
                root.style.setProperty('--accent2', '#5533cc');
                root.style.setProperty('--btn-bg', 'rgba(240, 240, 240, 0.8)');
                customBgPanel.style.display = 'none';
                localStorage.setItem(STORAGE_KEYS.THEME, 'light');
            }

            function showCustomPanel() {
                customBgPanel.style.display = 'flex';
            }

            function setImageBackground(url) {
                resetBackground();
                body.classList.add('custom-bg-active');
                body.style.setProperty('--custom-bg-url', `url('${url}')`);
                root.style.setProperty('--card', 'rgba(20, 20, 20, 0.7)');
                root.style.setProperty('--btn-bg', 'rgba(30, 30, 30, 0.7)');
                root.style.setProperty('--txt', '#ffffff');
                root.style.setProperty('--muted', '#cccccc');
                localStorage.setItem(STORAGE_KEYS.BG_TYPE, 'image');
                localStorage.setItem(STORAGE_KEYS.BG_DATA, url);
            }

            function setVideoBackground(url) {
                resetBackground();
                videoBg.src = url;
                videoBg.style.display = 'block';
                bgOverlay.style.display = 'block';
                videoBg.play();
                root.style.setProperty('--card', 'rgba(20, 20, 20, 0.7)');
                root.style.setProperty('--btn-bg', 'rgba(30, 30, 30, 0.7)');
                root.style.setProperty('--txt', '#ffffff');
                root.style.setProperty('--muted', '#cccccc');
                localStorage.setItem(STORAGE_KEYS.BG_TYPE, 'video');
                localStorage.setItem(STORAGE_KEYS.BG_DATA, url);
            }

            // Загрузка файлов из галереи
            imageUpload.addEventListener('change', function(e) {
                const file = e.target.files[0];
                if (file) {
                    const url = URL.createObjectURL(file);
                    setImageBackground(url);
                }
            });

            videoUpload.addEventListener('change', function(e) {
                const file = e.target.files[0];
                if (file) {
                    const url = URL.createObjectURL(file);
                    setVideoBackground(url);
                }
            });

            resetBgBtn.addEventListener('click', function() {
                setDarkTheme();
            });

            // Восстановление фона
            const savedBgType = localStorage.getItem(STORAGE_KEYS.BG_TYPE);
            const savedBgData = localStorage.getItem(STORAGE_KEYS.BG_DATA);
            
            if (savedBgType === 'image' && savedBgData) {
                setImageBackground(savedBgData);
            } else if (savedBgType === 'video' && savedBgData) {
                setVideoBackground(savedBgData);
            } else {
                const savedTheme = localStorage.getItem(STORAGE_KEYS.THEME) || 'dark';
                if (savedTheme === 'light') {
                    setLightTheme();
                } else {
                    setDarkTheme();
                }
            }

            themeDark.addEventListener('click', setDarkTheme);
            themeLight.addEventListener('click', setLightTheme);
            themeCustom.addEventListener('click', showCustomPanel);

            // === 3. АВТО-СМЕНА ЦВЕТА (RANDOM) ===
            const randomBtn = document.getElementById('randomColorBtn');
            const autoColorStatus = document.getElementById('autoColorStatus');
            
            function generateRandomColor() {
                const h = Math.floor(Math.random() * 360);
                const h2 = (h + 40) % 360;
                const accent = `hsl(${h}, 85%, 55%)`;
                const accent2 = `hsl(${h2}, 80%, 60%)`;
                root.style.setProperty('--accent', accent);
                root.style.setProperty('--accent2', accent2);
            }

            function startAutoColor() {
                if (autoColorInterval) clearInterval(autoColorInterval);
                autoColorInterval = setInterval(generateRandomColor, 5000);
                isAutoColorActive = true;
                autoColorStatus.textContent = '🟢';
                randomBtn.classList.add('active');
                localStorage.setItem(STORAGE_KEYS.AUTO_COLOR, 'on');
            }

            function stopAutoColor() {
                if (autoColorInterval) {
                    clearInterval(autoColorInterval);
                    autoColorInterval = null;
                }
                isAutoColorActive = false;
                autoColorStatus.textContent = '⚪';
                randomBtn.classList.remove('active');
                localStorage.setItem(STORAGE_KEYS.AUTO_COLOR, 'off');
            }

            function toggleAutoColor() {
                if (isAutoColorActive) {
                    stopAutoColor();
                } else {
                    startAutoColor();
                }
            }

            randomBtn.addEventListener('click', toggleAutoColor);

            // Восстановление авто-цвета
            const savedAutoColor = localStorage.getItem(STORAGE_KEYS.AUTO_COLOR);
            if (savedAutoColor === 'on') {
                startAutoColor();
            } else {
                stopAutoColor();
            }

            // Ручная смена цвета при двойном клике
            randomBtn.addEventListener('dblclick', function() {
                generateRandomColor();
            });

        })();
    </script>
</body>
</html>
