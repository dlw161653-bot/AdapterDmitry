Dmitry Mirnak Adapter
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
    <title>Dmitry Mirnak | Adapter</title>
    <style>
        /* === БАЗОВЫЕ ПЕРЕМЕННЫЕ (будут меняться через JS) === */
        :root {
            --bg: #030712;
            --bg2: #0c1222;
            --card: rgba(15, 23, 42, 0.78);
            --line: rgba(148, 163, 184, 0.18);
            --txt: #f1f5f9;
            --muted: #94a3b8;
            --accent: #38bdf8;
            --accent2: #818cf8;
            --btn-bg: rgba(30, 41, 59, 0.45);
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: "Segoe UI", system-ui, sans-serif;
            color: var(--txt);
            background: radial-gradient(ellipse 900px 500px at 10% -10%, rgba(56, 189, 248, 0.18), transparent),
                        radial-gradient(ellipse 700px 400px at 100% 20%, rgba(129, 140, 248, 0.15), transparent),
                        linear-gradient(165deg, var(--bg), var(--bg2));
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 24px;
            margin: 0;
            transition: background 0.3s ease, color 0.2s ease;
            position: relative;
        }

        /* Видео-фон */
        .video-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            object-fit: cover;
            z-index: -2;
        }

        /* Затемнение для читаемости */
        .overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.45);
            z-index: -1;
            pointer-events: none;
        }

        /* Кастомный фон — изображение */
        body.custom-bg-active {
            background: var(--custom-bg-url) center/cover fixed !important;
        }

        body.custom-bg-active::before {
            content: "";
            position: fixed;
            top: 0; left: 0; right: 0; bottom: 0;
            background: rgba(0, 0, 0, 0.35);
            pointer-events: none;
            z-index: 0;
        }

        .wrap {
            max-width: 720px;
            width: 100%;
            margin: 0 auto;
            border-radius: 32px;
            border: 1px solid var(--line);
            box-shadow: 0 25px 80px rgba(0, 0, 0, 0.45), inset 0 1px 0 rgba(255,255,255,0.04);
            background: linear-gradient(145deg, var(--card), rgba(15, 23, 42, 0.75));
            padding: 30px 28px 28px;
            backdrop-filter: blur(14px);
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
            background: linear-gradient(105deg, #e0f2fe, var(--accent2), #67e8f9);
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
            box-shadow: 0 8px 12px -6px rgba(0, 0, 0, 0.3);
        }

        .link-btn:hover {
            background: rgba(56, 189, 248, 0.12);
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

        /* === ПАНЕЛЬ УПРАВЛЕНИЯ === */
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
            color: #0f172a;
            border-color: var(--accent);
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
            height: 36px;
            border-radius: 40px;
            background: var(--btn-bg);
            backdrop-filter: blur(8px);
        }

        audio::-webkit-media-controls-panel {
            background: var(--card);
        }

        /* Блок кастомного фона */
        .custom-bg-panel {
            margin-top: 14px;
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .custom-bg-panel input[type="text"] {
            width: 100%;
            padding: 12px 16px;
            border-radius: 40px;
            border: 1px solid var(--line);
            background: var(--btn-bg);
            color: var(--txt);
            backdrop-filter: blur(8px);
            outline: none;
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

        /* Кнопка сброса фона */
        .reset-bg-btn {
            background: rgba(239, 68, 68, 0.3);
            border-color: rgba(239, 68, 68, 0.5);
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
    <!-- Видео-фон (будет добавляться динамически) -->
    <video id="videoBackground" class="video-bg" style="display: none;" loop muted playsinline></video>
    <div class="overlay" id="bgOverlay" style="display: none;"></div>

    <div class="wrap">
        <div class="hero">
            <h1>Dmitry Mirnak</h1>
            <div class="hero-sub">официальные ресурсы • official hub</div>
        </div>

        <!-- Основные кнопки навигации -->
        <div class="nav-grid">
            <a href="https://t.me/+EcKt9k-7qYAxNjYy" target="_blank" class="link-btn"><div class="btn-left"><span>📢</span><span>Официальный канал</span></div><i class="fas fa-arrow-right"></i></a>
            <a href="https://t.me/+TnG7x-J649wwYzVi" target="_blank" class="link-btn"><div class="btn-left"><span>📣</span><span>Второй канал</span></div><i class="fas fa-arrow-right"></i></a>
            <a href="https://t.me/+zzwkuey14-RlNTEy" target="_blank" class="link-btn"><div class="btn-left"><span>💬</span><span>Форум группа</span></div><i class="fas fa-arrow-right"></i></a>
            <a href="https://t.me/+dCKPaHcRcjNlY2Uy" target="_blank" class="link-btn"><div class="btn-left"><span>⭐</span><span>Отзывы</span></div><i class="fas fa-arrow-right"></i></a>
            <a href="https://t.me/psyhopizza" target="_blank" class="link-btn"><div class="btn-left"><span>🤖</span><span>Переходник на бот</span></div><i class="fas fa-arrow-right"></i></a>
            <a href="https://t.me/toncools" target="_blank" class="link-btn"><div class="btn-left"><span>👤</span><span>Официальный аккаунт</span></div><i class="fas fa-arrow-right"></i></a>
        </div>

        <!-- === ПАНЕЛЬ УПРАВЛЕНИЯ === -->
        <div class="control-panel">
            <!-- Кнопка загрузки песни -->
            <div class="file-upload-wrapper">
                <button class="ctrl-btn"><i class="fas fa-music"></i> Загрузить трек</button>
                <input type="file" id="audioUpload" accept="audio/*">
            </div>
            
            <!-- Кнопки тем -->
            <button class="ctrl-btn" id="themeDark"><i class="fas fa-moon"></i> Тёмная</button>
            <button class="ctrl-btn" id="themeLight"><i class="fas fa-sun"></i> Светлая</button>
            <button class="ctrl-btn" id="themeCustom"><i class="fas fa-image"></i> Кастом фон</button>
            
            <!-- Кнопка Random цвета -->
            <button class="ctrl-btn" id="randomColorBtn"><i class="fas fa-dice"></i> Random</button>
        </div>

        <!-- Аудио плеер -->
        <div id="audioPlayerContainer" class="audio-player" style="display: none;">
            <audio id="audioPlayer" controls></audio>
        </div>

        <!-- === ПАНЕЛЬ КАСТОМНОГО ФОНА === -->
        <div id="customBgPanel" class="custom-bg-panel" style="display: none;">
            <!-- Ссылка на картинку -->
            <input type="text" id="bgUrlInput" placeholder="🔗 Вставь ссылку на картинку (URL)">
            
            <!-- Загрузка из галереи -->
            <div class="file-row">
                <div class="file-upload-wrapper file-btn">
                    <button class="ctrl-btn" style="width: 100%;"><i class="fas fa-image"></i> Картинка из галереи</button>
                    <input type="file" id="imageUpload" accept="image/*">
                </div>
                <div class="file-upload-wrapper file-btn">
                    <button class="ctrl-btn" style="width: 100%;"><i class="fas fa-video"></i> Видео из галереи</button>
                    <input type="file" id="videoUpload" accept="video/*">
                </div>
            </div>
            
            <!-- Кнопки управления -->
            <div style="display: flex; gap: 10px;">
                <button class="ctrl-btn" id="applyBgBtn" style="flex: 1;"><i class="fas fa-check"></i> Применить</button>
                <button class="ctrl-btn reset-bg-btn" id="resetBgBtn" style="flex: 1;"><i class="fas fa-times"></i> Сбросить</button>
            </div>
            <p style="font-size: 12px; color: var(--muted); margin-top: 6px;">Видео будет проигрываться без звука на фоне</p>
        </div>

        <div class="footer-note"><i class="fas fa-link"></i> dmitrymirnak • 2026 • v3.0</div>
    </div>

    <script>
        (function() {
            "use strict";

            const body = document.getElementById('mainBody');
            const root = document.documentElement;
            const videoBg = document.getElementById('videoBackground');
            const bgOverlay = document.getElementById('bgOverlay');
            
            // === 1. ЗАГРУЗКА ПЕСНИ ===
            const audioUpload = document.getElementById('audioUpload');
            const audioContainer = document.getElementById('audioPlayerContainer');
            const audioPlayer = document.getElementById('audioPlayer');

            audioUpload.addEventListener('change', function(e) {
                const file = e.target.files[0];
                if (file) {
                    const url = URL.createObjectURL(file);
                    audioPlayer.src = url;
                    audioContainer.style.display = 'block';
                    audioPlayer.play();
                }
            });

            // === 2. ТЕМЫ ===
            const themeDark = document.getElementById('themeDark');
            const themeLight = document.getElementById('themeLight');
            const themeCustom = document.getElementById('themeCustom');
            const customBgPanel = document.getElementById('customBgPanel');
            const bgUrlInput = document.getElementById('bgUrlInput');
            const applyBgBtn = document.getElementById('applyBgBtn');
            const resetBgBtn = document.getElementById('resetBgBtn');
            const imageUpload = document.getElementById('imageUpload');
            const videoUpload = document.getElementById('videoUpload');

            // Сброс фона (убирает видео и картинку)
            function resetBackground() {
                // Останавливаем видео
                videoBg.pause();
                videoBg.src = '';
                videoBg.style.display = 'none';
                bgOverlay.style.display = 'none';
                
                // Убираем класс кастомного фона
                body.classList.remove('custom-bg-active');
                body.style.removeProperty('--custom-bg-url');
                
                // Возвращаем тёмную тему как базу
                setDarkTheme();
            }

            // Тёмная тема
            function setDarkTheme() {
                resetBackground();
                root.style.setProperty('--bg', '#030712');
                root.style.setProperty('--bg2', '#0c1222');
                root.style.setProperty('--card', 'rgba(15, 23, 42, 0.78)');
                root.style.setProperty('--line', 'rgba(148, 163, 184, 0.18)');
                root.style.setProperty('--txt', '#f1f5f9');
                root.style.setProperty('--muted', '#94a3b8');
                root.style.setProperty('--accent', '#38bdf8');
                root.style.setProperty('--accent2', '#818cf8');
                root.style.setProperty('--btn-bg', 'rgba(30, 41, 59, 0.45)');
                customBgPanel.style.display = 'none';
            }

            // Светлая тема
            function setLightTheme() {
                resetBackground();
                root.style.setProperty('--bg', '#f8fafc');
                root.style.setProperty('--bg2', '#e2e8f0');
                root.style.setProperty('--card', 'rgba(255, 255, 255, 0.85)');
                root.style.setProperty('--line', 'rgba(100, 116, 139, 0.2)');
                root.style.setProperty('--txt', '#0f172a');
                root.style.setProperty('--muted', '#475569');
                root.style.setProperty('--accent', '#2563eb');
                root.style.setProperty('--accent2', '#7c3aed');
                root.style.setProperty('--btn-bg', 'rgba(203, 213, 225, 0.6)');
                customBgPanel.style.display = 'none';
            }

            // Показать панель кастомного фона
            function showCustomPanel() {
                customBgPanel.style.display = 'flex';
            }

            // Применить КАРТИНКУ как фон (URL или файл)
            function setImageBackground(url) {
                resetBackground();
                body.classList.add('custom-bg-active');
                body.style.setProperty('--custom-bg-url', `url('${url}')`);
                root.style.setProperty('--card', 'rgba(15, 23, 42, 0.65)');
                root.style.setProperty('--btn-bg', 'rgba(15, 23, 42, 0.7)');
                root.style.setProperty('--txt', '#ffffff');
                root.style.setProperty('--muted', '#cbd5e1');
            }

            // Применить ВИДЕО как фон
            function setVideoBackground(url) {
                resetBackground();
                videoBg.src = url;
                videoBg.style.display = 'block';
                bgOverlay.style.display = 'block';
                videoBg.play();
                root.style.setProperty('--card', 'rgba(15, 23, 42, 0.65)');
                root.style.setProperty('--btn-bg', 'rgba(15, 23, 42, 0.7)');
                root.style.setProperty('--txt', '#ffffff');
                root.style.setProperty('--muted', '#cbd5e1');
            }

            // Обработчики загрузки файлов
            imageUpload.addEventListener('change', function(e) {
                const file = e.target.files[0];
                if (file) {
                    const url = URL.createObjectURL(file);
                    bgUrlInput.value = ''; // очищаем поле URL
                    setImageBackground(url);
                }
            });

            videoUpload.addEventListener('change', function(e) {
                const file = e.target.files[0];
                if (file) {
                    const url = URL.createObjectURL(file);
                    bgUrlInput.value = '';
                    setVideoBackground(url);
                }
            });

            // Применить по кнопке (если вставлен URL)
            applyBgBtn.addEventListener('click', function() {
                const url = bgUrlInput.value.trim();
                if (url) {
                    // Проверяем, видео это или картинка (по расширению)
                    const videoExt = ['.mp4', '.webm', '.ogg', '.mov'];
                    const isVideo = videoExt.some(ext => url.toLowerCase().includes(ext));
                    
                    if (isVideo) {
                        setVideoBackground(url);
                    } else {
                        setImageBackground(url);
                    }
                } else {
                    alert('Загрузи файл или вставь ссылку');
                }
            });

            // Сброс фона
            resetBgBtn.addEventListener('click', function() {
                setDarkTheme();
                bgUrlInput.value = '';
            });

            // Привязка кнопок тем
            themeDark.addEventListener('click', setDarkTheme);
            themeLight.addEventListener('click', setLightTheme);
            themeCustom.addEventListener('click', showCustomPanel);

            // === 3. RANDOM ЦВЕТ ===
            const randomBtn = document.getElementById('randomColorBtn');
            
            function randomColor() {
                const h = Math.floor(Math.random() * 360);
                const h2 = (h + 40) % 360;
                const accent = `hsl(${h}, 80%, 60%)`;
                const accent2 = `hsl(${h2}, 75%, 65%)`;
                root.style.setProperty('--accent', accent);
                root.style.setProperty('--accent2', accent2);
                
                const bgHue = (h + 180) % 360;
                root.style.setProperty('--bg', `hsl(${bgHue}, 25%, 6%)`);
                root.style.setProperty('--bg2', `hsl(${bgHue}, 20%, 10%)`);
            }

            randomBtn.addEventListener('click', randomColor);

            // Enter в поле URL
            bgUrlInput.addEventListener('keypress', function(e) {
                if(e.key === 'Enter') {
                    applyBgBtn.click();
                }
            });

        })();
    </script>
</body>
</html>
