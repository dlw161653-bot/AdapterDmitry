Dmitry Mirnak Adapter
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dmitry Mirnak | Hub</title>
    <style>
        :root {
            --bg: #030712; --bg2: #0c1222; --card: rgba(15, 23, 42, 0.78);
            --line: rgba(148, 163, 184, 0.18); --txt: #f1f5f9; --muted: #94a3b8;
            --accent: #38bdf8; --accent2: #818cf8;
        }
        * { box-sizing: border-box; margin: 0; padding: 0; }
        body {
            font-family: "Segoe UI", system-ui, sans-serif; color: var(--txt);
            background: radial-gradient(ellipse 900px 500px at 10% -10%, rgba(56, 189, 248, 0.18), transparent),
                        radial-gradient(ellipse 700px 400px at 100% 20%, rgba(129, 140, 248, 0.15), transparent),
                        linear-gradient(165deg, var(--bg), var(--bg2));
            min-height: 100vh; display: flex; align-items: center; justify-content: center;
            padding: 24px; margin: 0;
        }
        .wrap {
            max-width: 680px; width: 100%; margin: 0 auto; border-radius: 32px;
            border: 1px solid var(--line); box-shadow: 0 25px 80px rgba(0, 0, 0, 0.45), inset 0 1px 0 rgba(255,255,255,0.04);
            background: linear-gradient(145deg, rgba(17, 24, 39, 0.92), rgba(15, 23, 42, 0.75));
            padding: 36px 32px 40px; backdrop-filter: blur(14px);
        }
        .hero { text-align: center; margin-bottom: 36px; }
        h1 {
            font-size: 2.4rem; font-weight: 800; letter-spacing: -0.02em;
            background: linear-gradient(105deg, #e0f2fe, #a5b4fc, #67e8f9);
            -webkit-background-clip: text; -webkit-text-fill-color: transparent;
            background-clip: text; margin-bottom: 8px;
        }
        .hero-sub { color: var(--muted); font-size: 15px; font-weight: 500; border-bottom: 1px solid var(--line); padding-bottom: 22px; }
        .nav-grid { display: flex; flex-direction: column; gap: 14px; }
        .link-btn {
            display: flex; align-items: center; justify-content: space-between;
            width: 100%; padding: 18px 24px; background: rgba(30, 41, 59, 0.45);
            border: 1px solid var(--line); border-radius: 20px; color: var(--txt);
            text-decoration: none; font-weight: 600; font-size: 18px;
            backdrop-filter: blur(8px); transition: all 0.25s;
            box-shadow: 0 8px 12px -6px rgba(0, 0, 0, 0.3);
        }
        .link-btn:hover { background: rgba(56, 189, 248, 0.12); border-color: rgba(56, 189, 248, 0.5); transform: translateY(-3px); }
        .link-btn i { color: var(--accent); font-size: 22px; transition: transform 0.2s; }
        .link-btn:hover i { transform: translateX(6px); }
        .btn-left { display: flex; align-items: center; gap: 16px; }
        .btn-left span:first-child { font-size: 24px; width: 32px; text-align: center; }
        .footer-note { margin-top: 32px; text-align: center; color: var(--muted); font-size: 13px; border-top: 1px solid var(--line); padding-top: 22px; }
        @media (max-width: 480px) { body { padding: 12px; } .wrap { padding: 28px 18px 30px; } h1 { font-size: 2rem; } .link-btn { padding: 16px 18px; font-size: 16px; } }
    </style>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
</head>
<body>
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
        <div class="footer-note"><i class="fas fa-link"></i> dmitrymirnak • 2026</div>
    </div>
</body>
</html>
