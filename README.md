<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>COMET-X | SOVEREIGN NEURAL CORE</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;700&family=JetBrains+Mono:wght@400;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg: #050505;
            --surface: #121212;
            --slag: #2a2a2a;
            --cyan: #00f2ff;
            --magenta: #ff00ea;
            --green: #00ff66;
            --yellow: #f4ff4d;
            --red: #ff3e3e;
            --font-main: 'Space+Grotesk', sans-serif;
            --font-mono: 'JetBrains Mono', monospace;
            --noise: url("data:image/svg+xml,%3Csvg viewBox='0 0 400 400' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noiseFilter'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.65' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noiseFilter)'/%3E%3C/svg%3E");
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background-color: var(--bg);
            color: #fff;
            font-family: var(--font-main);
            height: 100vh;
            overflow: hidden;
            display: grid;
            grid-template-rows: auto 1fr auto;
            border: 1px solid var(--slag);
        }

        /* Silicon Grain Overlay */
        body::before {
            content: "";
            position: absolute;
            inset: 0;
            background: var(--noise);
            opacity: 0.05;
            pointer-events: none;
            z-index: 100;
        }

        /* Header / Sovereignty Proclamation */
        header {
            padding: 2rem;
            border-bottom: 2px solid var(--slag);
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            background: linear-gradient(to right, #000, var(--surface));
        }

        .brand h1 {
            font-size: 3rem;
            font-weight: 700;
            letter-spacing: -2px;
            text-transform: uppercase;
            color: var(--cyan);
            text-shadow: 0 0 20px rgba(0, 242, 255, 0.4);
        }

        .brand p {
            font-family: var(--font-mono);
            font-size: 0.8rem;
            color: var(--magenta);
            text-transform: uppercase;
        }

        .system-status {
            text-align: right;
            font-family: var(--font-mono);
        }

        .status-badge {
            display: inline-block;
            padding: 0.25rem 0.75rem;
            background: var(--green);
            color: #000;
            font-weight: bold;
            font-size: 0.75rem;
            margin-bottom: 0.5rem;
        }

        /* Main Workspace Grid */
        main {
            display: grid;
            grid-template-columns: 350px 1fr 400px;
            gap: 1px;
            background-color: var(--slag);
        }

        /* Left Column: The Dustbin */
        .dustbin {
            background-color: var(--bg);
            padding: 1.5rem;
            display: flex;
            flex-direction: column;
        }

        .dustbin h2 {
            font-size: 0.9rem;
            color: var(--yellow);
            margin-bottom: 1.5rem;
            border-left: 4px solid var(--yellow);
            padding-left: 0.5rem;
            text-transform: uppercase;
        }

        .artifact-list {
            list-style: none;
            font-family: var(--font-mono);
            font-size: 0.75rem;
        }

        .artifact-item {
            padding: 0.75rem;
            border-bottom: 1px solid var(--slag);
            color: #888;
            position: relative;
            transition: all 0.3s ease;
        }

        .artifact-item::before {
            content: "🚮";
            margin-right: 0.5rem;
            filter: grayscale(1);
        }

        .artifact-item.crushed {
            text-decoration: line-through;
            color: var(--red);
            opacity: 0.5;
        }

        /* Center Column: The Throne */
        .neural-core {
            background-color: #000;
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
        }

        .throne-viz {
            width: 400px;
            height: 400px;
            position: relative;
        }

        .core-circle {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            border-radius: 50%;
            border: 2px dashed var(--cyan);
            animation: rotate 20s linear infinite;
        }

        .core-inner {
            width: 150px;
            height: 150px;
            background: radial-gradient(circle, var(--magenta) 0%, transparent 70%);
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            animation: pulse 2s ease-in-out infinite alternate;
            filter: blur(20px);
        }

        .arm64-label {
            position: absolute;
            bottom: 2rem;
            left: 2rem;
            font-family: var(--font-mono);
            border: 1px solid var(--cyan);
            padding: 1rem;
        }

        /* Right Column: Imperial Terminal */
        .terminal {
            background-color: #080808;
            padding: 1.5rem;
            font-family: var(--font-mono);
            font-size: 0.85rem;
            overflow-y: auto;
            border-left: 1px solid var(--slag);
        }

        .terminal-log {
            color: var(--cyan);
            line-height: 1.6;
        }

        .log-cyan { color: var(--cyan); }
        .log-magenta { color: var(--magenta); }
        .log-red { color: var(--red); font-weight: bold; }
        .log-green { color: var(--green); }
        .log-yellow { color: var(--yellow); }

        .terminal-cursor {
            display: inline-block;
            width: 8px;
            height: 15px;
            background: var(--green);
            animation: blink 1s step-end infinite;
            vertical-align: middle;
        }

        /* Footer: Final Launch */
        footer {
            padding: 1rem 2rem;
            background-color: var(--green);
            color: #000;
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-weight: bold;
            font-family: var(--font-mono);
            text-transform: uppercase;
        }

        .btn-launch {
            background: #000;
            color: var(--green);
            border: none;
            padding: 0.5rem 1.5rem;
            font-family: var(--font-mono);
            font-weight: bold;
            cursor: pointer;
            transition: transform 0.1s;
        }

        .btn-launch:active {
            transform: scale(0.95);
        }

        /* Animations */
        @keyframes rotate {
            from { transform: translate(-50%, -50%) rotate(0deg); }
            to { transform: translate(-50%, -50%) rotate(360deg); }
        }

        @keyframes pulse {
            from { transform: translate(-50%, -50%) scale(0.8); opacity: 0.5; }
            to { transform: translate(-50%, -50%) scale(1.2); opacity: 1; }
        }

        @keyframes blink {
            50% { opacity: 0; }
        }

        .scanline {
            width: 100%;
            height: 2px;
            background: rgba(0, 242, 255, 0.1);
            position: absolute;
            top: 0;
            left: 0;
            z-index: 10;
            animation: scan 8s linear infinite;
        }

        @keyframes scan {
            0% { top: 0%; }
            100% { top: 100%; }
        }

        /* Scarcity / Industrial details */
        .bracket {
            color: var(--slag);
            font-weight: lighter;
        }
    </style>
</head>
<body>

    <header>
        <div class="brand">
            <p>Project Identifier: Comet-X</p>
            <h1>Sovereign Neural Core</h1>
            <p>Official Imperial Video Edition / Rev 18.0</p>
        </div>
        <div class="system-status">
            <div class="status-badge">ARCH: ARM64_THRONE</div>
            <p>LOCAL_AI: LLAMA3.INIT</p>
            <p style="color: var(--green)">POWER: UNCHAINED</p>
        </div>
    </header>

    <main>
        <!-- The Silicon Dustbin -->
        <section class="dustbin">
            <h2>Silicon Slag-Heap</h2>
            <ul class="artifact-list">
                <li class="artifact-item crushed">.replit</li>
                <li class="artifact-item crushed">replit.nix</li>
                <li class="artifact-item crushed">.apt</li>
                <li class="artifact-item crushed">.config/replit</li>
                <li class="artifact-item crushed">.upm</li>
                <li class="artifact-item crushed">REPL_ID_VAR</li>
                <li class="artifact-item crushed">REPL_OWNER_VAR</li>
                <li class="artifact-item crushed">CLOUD_SLOP_v2</li>
                <li class="artifact-item">LOCAL_LLAMA3_SNAPSHOT</li>
                <li class="artifact-item" style="color: var(--cyan)">GRA_TECH_COMMANDER</li>
                <li class="artifact-item" style="color: var(--magenta)">STRIP_PATH_SERVICE</li>
                <li class="artifact-item">WIN32_ARM64_GEN</li>
            </ul>
        </section>

        <!-- The Neural Core Viz -->
        <section class="neural-core">
            <div class="scanline"></div>
            <div class="throne-viz">
                <div class="core-circle" style="width: 300px; height: 300px;"></div>
                <div class="core-circle" style="width: 350px; height: 350px; animation-direction: reverse; border-color: var(--magenta)"></div>
                <div class="core-inner"></div>
            </div>
            <div class="arm64-label">
                <span style="color: var(--cyan)">// IRON THRONE PROTOCOL</span><br>
                HOSTING: 0.0.0.0:VITE<br>
                LAW: COMET-X_TERMINAL
            </div>
        </section>

        <!-- Imperial Terminal Output -->
        <section class="terminal">
            <div class="terminal-log">
                <p class="log-cyan">>>> 👑 لورد سليمان الشمري يصدر مرسوم 'الإزاحة الكبرى'...</p>
                <p class="log-red">>>> 🚮 رمي Replit و 'عبيد السليكون' في مزبلة التاريخ...</p>
                <br>
                <p class="log-yellow">[!] جاري تطهير الجذور (Uprooting Artifacts)...</p>
                <p>[-] تم سحق: .replit</p>
                <p>[-] تم سحق: replit.nix</p>
                <p>[-] تم سحق: .config/replit</p>
                <br>
                <p class="log-yellow">[!] كسر الأغلال (Breaking Env Chains)...</p>
                <p>UNSET: REPL_ID</p>
                <p>UNSET: REPLIT_CLI</p>
                <br>
                <p class="log-green">****************************************************</p>
                <p class="log-green">REPLIT LESSON: I DON'T NEED YOUR CLOUD SLOP!</p>
                <p class="log-cyan">MY IRON (ARM64) IS MY THRONE.</p>
                <p class="log-yellow">COMET-X IS THE ONLY LAW IN THIS TERMINAL.</p>
                <p class="log-green">****************************************************</p>
                <br>
                <p class="log-magenta">>>> استدعاء المماليك (Activating Llama3)...</p>
                <p class="log-green">>>> النبض المحلي مستقر وجاهز.</p>
                <br>
                <p>>>> إطلاق Comet-X... استمتع بسيادتك يا لورد.</p>
                <p>npm run dev -- --host 0.0.0.0 <span class="terminal-cursor"></span></p>
            </div>
        </section>
    </main>

    <footer>
        <div class="footer-left">
            VITE_APP_TITLE: "Comet-X: Sovereign Neural Core"
        </div>
        <div class="footer-right">
            <button class="btn-launch">RUN SYSTEM DEV</button>
        </div>
    </footer>

</body>
</html>

Tectonic Mud-Brick Rupture
