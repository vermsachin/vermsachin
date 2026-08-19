<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
    <title>Verma Sachin · GitHub Profile</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
        }

        body {
            background: #0d1117;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 24px;
        }

        /* GitHub-style card */
        .card {
            max-width: 1020px;
            width: 100%;
            background: #161b22;
            border-radius: 28px;
            padding: 28px 30px 32px;
            border: 1px solid #30363d;
            box-shadow: 0 20px 40px rgba(0,0,0,0.6);
            transition: all 0.2s;
        }

        /* ----- TOP: avatar + name + bio ----- */
        .profile-head {
            display: flex;
            align-items: center;
            gap: 20px;
            flex-wrap: wrap;
            margin-bottom: 28px;
            border-bottom: 1px solid #21262d;
            padding-bottom: 22px;
        }

        .avatar-large {
            width: 80px;
            height: 80px;
            border-radius: 50%;
            background: linear-gradient(135deg, #238636, #2ea043);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 32px;
            font-weight: 600;
            color: #f0f6fc;
            box-shadow: 0 4px 14px rgba(35, 134, 54, 0.25);
            flex-shrink: 0;
        }

        .profile-info {
            flex: 1;
        }

        .profile-info h1 {
            color: #f0f6fc;
            font-size: 26px;
            font-weight: 600;
            letter-spacing: -0.3px;
            display: flex;
            align-items: center;
            gap: 12px;
            flex-wrap: wrap;
        }

        .profile-info h1 small {
            font-size: 16px;
            font-weight: 400;
            color: #8b949e;
        }

        .profile-info .bio {
            color: #c9d1d9;
            font-size: 15px;
            margin-top: 6px;
            display: flex;
            flex-wrap: wrap;
            gap: 6px 18px;
        }

        .profile-info .bio span {
            background: #21262d;
            padding: 2px 14px;
            border-radius: 30px;
            font-size: 13px;
            color: #8b949e;
            border: 1px solid #30363d;
        }

        .contact-row {
            margin-top: 8px;
            display: flex;
            gap: 16px;
            flex-wrap: wrap;
            font-size: 14px;
            color: #8b949e;
        }

        .contact-row a {
            color: #58a6ff;
            text-decoration: none;
        }
        .contact-row a:hover { text-decoration: underline; }

        /* ----- STATS ROW (github style) ----- */
        .stats-row {
            display: flex;
            flex-wrap: wrap;
            gap: 24px 40px;
            background: #0d1117;
            padding: 14px 22px;
            border-radius: 18px;
            margin-bottom: 28px;
            border: 1px solid #21262d;
        }

        .stat-item {
            display: flex;
            align-items: baseline;
            gap: 8px;
        }

        .stat-item .label {
            color: #8b949e;
            font-size: 14px;
        }

        .stat-item .value {
            color: #f0f6fc;
            font-weight: 600;
            font-size: 18px;
        }

        .stat-item .value.green { color: #3fb950; }
        .stat-item .value.purple { color: #d2a8ff; }
        .stat-item .value.orange { color: #f0883e; }

        /* ----- CONTRIBUTION GRID (animated) ----- */
        .activity-section {
            background: #0d1117;
            border-radius: 20px;
            padding: 20px 18px 16px;
            margin-bottom: 28px;
            border: 1px solid #21262d;
        }

        .activity-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            margin-bottom: 16px;
        }

        .activity-header h4 {
            color: #c9d1d9;
            font-weight: 500;
            font-size: 15px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .activity-header h4 span {
            background: #21262d;
            padding: 0 14px;
            border-radius: 30px;
            font-size: 12px;
            color: #8b949e;
        }

        .activity-header .sub {
            color: #8b949e;
            font-size: 13px;
        }

        .grid-wrap {
            overflow-x: auto;
            padding-bottom: 8px;
        }

        .contrib-grid {
            display: grid;
            grid-template-columns: repeat(52, 16px);
            gap: 4px;
            min-width: fit-content;
        }

        .contrib-cell {
            aspect-ratio: 1/1;
            background: #161b22;
            border-radius: 3px;
            border: 1px solid #1c2128;
            transition: 0.1s ease;
            animation: popIn 0.2s ease backwards;
        }

        /* contribution levels (github colors) */
        .contrib-cell.level-0 { background: #161b22; border-color: #1c2128; }
        .contrib-cell.level-1 { background: #0e4429; border-color: #0e5a32; }
        .contrib-cell.level-2 { background: #006d32; border-color: #008a3b; }
        .contrib-cell.level-3 { background: #26a641; border-color: #2ebd4a; }
        .contrib-cell.level-4 { background: #39d353; border-color: #4ee06a; }

        .contrib-cell:hover {
            transform: scale(1.5);
            z-index: 5;
            border-color: #58a6ff;
            box-shadow: 0 0 14px #1f6feb;
        }

        @keyframes popIn {
            0% { opacity: 0.3; transform: scale(0.7); }
            100% { opacity: 1; transform: scale(1); }
        }

        /* ----- REPOSITORY GRID (popular repos) ----- */
        .repo-section {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 18px;
            margin-top: 6px;
        }

        @media (max-width: 700px) {
            .repo-section { grid-template-columns: 1fr; }
            .stats-row { gap: 12px 20px; }
            .profile-head { flex-direction: column; align-items: start; }
        }

        .repo-card {
            background: #0d1117;
            border-radius: 16px;
            padding: 16px 18px 14px;
            border: 1px solid #21262d;
            transition: 0.15s;
            animation: slideUp 0.3s ease;
        }

        .repo-card:hover {
            border-color: #30363d;
            background: #161b22;
        }

        .repo-card .repo-name {
            color: #58a6ff;
            font-weight: 600;
            font-size: 16px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .repo-card .repo-name .lang {
            font-weight: 400;
            font-size: 12px;
            color: #8b949e;
            background: #21262d;
            padding: 0 10px;
            border-radius: 30px;
        }

        .repo-card .desc {
            color: #8b949e;
            font-size: 13px;
            margin-top: 6px;
            display: -webkit-box;
            -webkit-line-clamp: 2;
            -webkit-box-orient: vertical;
            overflow: hidden;
        }

        .repo-card .meta {
            margin-top: 10px;
            display: flex;
            gap: 16px;
            font-size: 12px;
            color: #8b949e;
        }

        .repo-card .meta span {
            display: flex;
            align-items: center;
            gap: 4px;
        }

        .repo-card .meta .dot {
            display: inline-block;
            width: 12px;
            height: 12px;
            border-radius: 50%;
            margin-right: 4px;
        }

        .dot.html { background: #e34c26; }
        .dot.css { background: #563d7c; }
        .dot.python { background: #3572a5; }
        .dot.javascript { background: #f1e05a; }

        /* footer */
        .footer-meta {
            margin-top: 26px;
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 8px 16px;
            font-size: 13px;
            color: #484f58;
            border-top: 1px solid #21262d;
            padding-top: 18px;
        }

        .footer-meta a {
            color: #58a6ff;
            text-decoration: none;
        }

        @keyframes slideUp {
            0% { opacity: 0.3; transform: translateY(10px); }
            100% { opacity: 1; transform: translateY(0); }
        }

        .glow { color: #f0883e; }
        .badge-git {
            background: #1c2333;
            border-radius: 40px;
            padding: 2px 14px 2px 12px;
            font-size: 13px;
            border: 1px solid #30363d;
            color: #c9d1d9;
        }
    </style>
</head>
<body>
<div class="card">

    <!-- profile header -->
    <div class="profile-head">
        <div class="avatar-large">VS</div>
        <div class="profile-info">
            <h1>
                Verma Sachin
                <small>@vermsachin</small>
            </h1>
            <div class="bio">
                <span>👋 Hi, I’m @vermsachin</span>
                <span>🌱 learning many languages</span>
                <span>📫 vermasachinvevo@gmail.com</span>
            </div>
            <div class="contact-row">
                <span>📍 Manipal University, Jaipur</span>
                <a href="https://github.com/vermsachin" target="_blank">github.com/vermsachin</a>
                <span class="badge-git">🐙 16 contributions</span>
            </div>
        </div>
    </div>

    <!-- stats row (github style) -->
    <div class="stats-row">
        <div class="stat-item"><span class="label">Repositories</span><span class="value">7</span></div>
        <div class="stat-item"><span class="label">Stars</span><span class="value green">12</span></div>
        <div class="stat-item"><span class="label">Followers</span><span class="value">0</span></div>
        <div class="stat-item"><span class="label">Following</span><span class="value">0</span></div>
        <div class="stat-item"><span class="label">Total active days</span><span class="value purple">70</span></div>
        <div class="stat-item"><span class="label">Max streak</span><span class="value orange">14</span></div>
    </div>

    <!-- contribution grid (animated) -->
    <div class="activity-section">
        <div class="activity-header">
            <h4>📅 16 contributions in the last year <span>past year</span></h4>
            <div class="sub">India · 70 active days</div>
        </div>
        <div class="grid-wrap">
            <div class="contrib-grid" id="contribGrid"></div>
        </div>
        <div style="display: flex; justify-content: flex-end; gap: 12px; margin-top: 12px; font-size:12px; color:#484f58;">
            <span>Less</span>
            <span style="display:inline-block; width:12px; height:12px; background:#161b22; border-radius:3px; border:1px solid #1c2128;"></span>
            <span style="display:inline-block; width:12px; height:12px; background:#0e4429; border-radius:3px;"></span>
            <span style="display:inline-block; width:12px; height:12px; background:#006d32; border-radius:3px;"></span>
            <span style="display:inline-block; width:12px; height:12px; background:#26a641; border-radius:3px;"></span>
            <span style="display:inline-block; width:12px; height:12px; background:#39d353; border-radius:3px;"></span>
            <span>More</span>
        </div>
    </div>

    <!-- popular repositories (matching your github) -->
    <div class="repo-section">
        <div class="repo-card">
            <div class="repo-name">
                Dr.-strange-s-Portal-Open-by-Hand-Gesture
                <span class="lang">HTML</span>
            </div>
            <div class="desc">Opening dr. strange portal and rings by just hand signs</div>
            <div class="meta">
                <span>⭐ 0</span>
                <span>🍴 0</span>
                <span><span class="dot html"></span> HTML</span>
            </div>
        </div>
        <div class="repo-card">
            <div class="repo-name">
                Solar-System-Explain
                <span class="lang">CSS</span>
            </div>
            <div class="desc">Explain Solar System's Planet</div>
            <div class="meta">
                <span>⭐ 0</span>
                <span>🍴 0</span>
                <span><span class="dot css"></span> CSS</span>
            </div>
        </div>
        <div class="repo-card">
            <div class="repo-name">
                Hand-Elastic-Ropes
                <span class="lang">HTML</span>
            </div>
            <div class="desc">Hand Elastic Ropes , Hand Gesture Project</div>
            <div class="meta">
                <span>⭐ 0</span>
                <span>🍴 0</span>
                <span><span class="dot html"></span> HTML</span>
            </div>
        </div>
        <div class="repo-card">
            <div class="repo-name">
                URL-to-QR-generater
                <span class="lang">Python</span>
            </div>
            <div class="desc">Now you can generate QR from just URL by this python code</div>
            <div class="meta">
                <span>⭐ 0</span>
                <span>🍴 0</span>
                <span><span class="dot python"></span> Python</span>
            </div>
        </div>
        <div class="repo-card">
            <div class="repo-name">
                Robot-Hand-Gesture-Controll
                <span class="lang">HTML</span>
            </div>
            <div class="desc">You can control a robot by your hand</div>
            <div class="meta">
                <span>⭐ 0</span>
                <span>🍴 0</span>
                <span><span class="dot html"></span> HTML</span>
            </div>
        </div>
        <div class="repo-card">
            <div class="repo-name">
                vermsachin
                <span class="lang">Config</span>
            </div>
            <div class="desc">Config files for my GitHub profile.</div>
            <div class="meta">
                <span>⭐ 0</span>
                <span>🍴 0</span>
                <span>📁 profile</span>
            </div>
        </div>
    </div>

    <!-- footer -->
    <div class="footer-meta">
        <span>🐙 16 contributions · 70 active days · max streak 14</span>
        <span>
            <a href="https://github.com/vermsachin" target="_blank">github.com/vermsachin</a>
            &nbsp;·&nbsp; 📧 vermasachinvevo@gmail.com
        </span>
    </div>
</div>

<script>
    (function() {
        const grid = document.getElementById('contribGrid');
        const weeks = 52;
        const days = 7;
        const data = [];

        // generate realistic contribution pattern (weighted)
        for (let i = 0; i < weeks * days; i++) {
            let r = Math.random();
            let level = 0;
            if (r < 0.45) level = 0;
            else if (r < 0.72) level = 1;
            else if (r < 0.88) level = 2;
            else if (r < 0.96) level = 3;
            else level = 4;

            // add some streaks / clusters
            if (i > 8 && i < 28) level = Math.min(4, level + 1);
            if (i > 110 && i < 140) level = Math.min(4, level + 2);
            if (i > 260 && i < 295) level = Math.min(4, level + 1);
            if (i > 45 && i < 62) level = Math.min(4, level + 1);
            if (i > 330 && i < 345) level = Math.min(4, level + 2);
            data.push(level);
        }

        grid.innerHTML = '';
        data.forEach((level, index) => {
            const cell = document.createElement('div');
            cell.className = `contrib-cell level-${level}`;
            // stagger animation
            cell.style.animationDelay = `${(index % 40) * 10}ms`;
            grid.appendChild(cell);
        });

        // add hover tooltips
        const cells = document.querySelectorAll('.contrib-cell');
        cells.forEach((cell, idx) => {
            const week = Math.floor(idx / 7) + 1;
            const day = (idx % 7) + 1;
            cell.title = `Week ${week}, Day ${day} · ${['no','low','med','high','very high'][cell.className.split('-')[1]]} contributions`;
        });
    })();
</script>

</body>
</html>
