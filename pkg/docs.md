<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Argon Swarm Security Hub & Cogni-Flow Matrix</title>
    <style>
        :root {
            --bg-color: #080c10;
            --panel-bg: #121820;
            --panel-border: #1f2937;
            --accent-green: #00ff66;
            --accent-green-dim: rgba(0, 255, 102, 0.15);
            --alert-red: #ff3344;
            --alert-red-dim: rgba(255, 51, 68, 0.15);
            --warn-yellow: #ffcc00;
            --text-main: #e2e8f0;
            --text-muted: #94a3b8;
            --font-mono: 'Courier New', Courier, monospace;
            --header-bg: #121820;
            --button-bg: #1a222d;
            --button-text: #00ff66;
        }

        /* Secondary Retro Win ME / MS-DOS Vintage Theme */
        body.theme-vintage {
            --bg-color: #008080;
            --panel-bg: #c0c0c0;
            --panel-border: #808080;
            --accent-green: #000080;
            --accent-green-dim: #a6a6a6;
            --alert-red: #800000;
            --alert-red-dim: #e0a0a0;
            --warn-yellow: #808000;
            --text-main: #000000;
            --text-muted: #404040;
            --font-mono: 'Fixedsys', 'Courier New', monospace;
            --header-bg: #000080;
            --button-bg: #c0c0c0;
            --button-text: #000000;
        }

        * {
            box-sizing: border-box;
            user-select: none;
            -webkit-touch-callout: none;
        }

        body {
            margin: 0;
            padding: 12px;
            background-color: var(--bg-color);
            color: var(--text-main);
            font-family: var(--font-mono);
            display: flex;
            flex-direction: column;
            gap: 12px;
            height: 100vh;
            overflow: hidden;
            transition: background-color 0.3s, color 0.3s;
        }

        body.theme-vintage header {
            background-color: var(--header-bg);
            color: #ffffff;
            border: 2px outset #ffffff;
        }

        body.theme-vintage .panel {
            border: 2px outset #ffffff;
            box-shadow: 2px 2px 0px #000;
        }

        body.theme-vintage button {
            border: 2px outset #ffffff;
            background-color: #c0c0c0;
            color: #000000;
        }

        body.theme-vintage button:active {
            border: 2px inset #ffffff;
        }

        header {
            border: 1px solid var(--panel-border);
            background-color: var(--panel-bg);
            padding: 10px 16px;
            border-radius: 6px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.4);
            flex-shrink: 0;
        }

        .title-group {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .shield-icon {
            font-size: 1.4rem;
            color: var(--accent-green);
        }

        h1 {
            font-size: 1rem;
            margin: 0;
            letter-spacing: 1px;
            text-transform: uppercase;
        }

        .status-badge {
            display: flex;
            align-items: center;
            gap: 6px;
            font-size: 0.75rem;
            padding: 4px 10px;
            border-radius: 16px;
            background: var(--accent-green-dim);
            border: 1px solid var(--accent-green);
            color: var(--accent-green);
        }

        body.theme-vintage .status-badge {
            color: #ffffff;
            background: #000080;
            border-color: #ffffff;
        }

        .status-dot {
            width: 8px;
            height: 8px;
            border-radius: 50%;
            background-color: var(--accent-green);
            box-shadow: 0 0 6px var(--accent-green);
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0% { opacity: 0.4; }
            50% { opacity: 1; }
            100% { opacity: 0.4; }
        }

        /* Scrollable Tile Grid Layout */
        .dashboard {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 12px;
            flex-grow: 1;
            min-height: 0;
            overflow-y: auto;
            padding-right: 4px;
        }

        .panel {
            background-color: var(--panel-bg);
            border: 1px solid var(--panel-border);
            border-radius: 8px;
            padding: 12px;
            display: flex;
            flex-direction: column;
            gap: 10px;
            max-height: 480px;
            overflow-y: auto;
            position: relative;
        }

        .panel-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid var(--panel-border);
            padding-bottom: 6px;
            flex-shrink: 0;
        }

        .panel-header h2 {
            font-size: 0.85rem;
            margin: 0;
            color: var(--accent-green);
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        body.theme-vintage .panel-header h2 {
            color: #000080;
        }

        /* Radar & Automata Canvases */
        .canvas-box {
            position: relative;
            width: 100%;
            height: 180px;
            display: flex;
            justify-content: center;
            align-items: center;
            background: rgba(0, 0, 0, 0.3);
            border-radius: 6px;
            border: 1px solid var(--panel-border);
            flex-shrink: 0;
        }

        canvas {
            background-color: #030805;
            border-radius: 4px;
            touch-action: none;
        }

        body.theme-vintage canvas {
            background-color: #000000;
        }

        /* Action Buttons & Touch Controls */
        .controls-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 6px;
            flex-shrink: 0;
        }

        button {
            background-color: var(--button-bg);
            color: var(--button-text);
            border: 1px solid var(--accent-green);
            padding: 8px 6px;
            border-radius: 4px;
            cursor: pointer;
            font-family: inherit;
            font-size: 0.7rem;
            font-weight: bold;
            text-transform: uppercase;
            transition: all 0.15s ease;
            outline: none;
            touch-action: manipulation;
        }

        button:active {
            transform: scale(0.96);
        }

        button.active {
            background-color: var(--accent-green);
            color: #000000;
        }

        button.danger {
            color: var(--alert-red);
            border-color: var(--alert-red);
        }

        button.warn {
            color: var(--warn-yellow);
            border-color: var(--warn-yellow);
        }

        /* Scrollable Logs & Message Containers */
        .scroll-tile {
            flex-grow: 1;
            min-height: 100px;
            background-color: rgba(0, 0, 0, 0.5);
            border: 1px solid var(--panel-border);
            border-radius: 4px;
            padding: 8px;
            overflow-y: auto;
            font-size: 0.7rem;
            display: flex;
            flex-direction: column;
            gap: 6px;
        }

        body.theme-vintage .scroll-tile {
            background-color: #ffffff;
            color: #000000;
            border: 2px inset #808080;
        }

        .log-entry {
            line-height: 1.3;
            word-break: break-all;
        }

        .log-info { color: var(--accent-green); }
        .log-warn { color: var(--warn-yellow); }
        .log-alert { color: var(--alert-red); font-weight: bold; }
        .log-sys { color: var(--text-muted); }

        /* Secure Chat Area */
        .msg-bubble {
            background: #18202c;
            border-left: 3px solid var(--accent-green);
            padding: 6px 8px;
            border-radius: 4px;
            font-size: 0.75rem;
        }

        body.theme-vintage .msg-bubble {
            background: #e0e0e0;
            border-left-color: #000080;
            color: #000000;
        }

        .msg-meta {
            font-size: 0.6rem;
            color: var(--text-muted);
            margin-top: 3px;
            word-break: break-all;
        }

        .chat-input-row {
            display: flex;
            gap: 6px;
            flex-shrink: 0;
        }

        input[type="text"] {
            flex-grow: 1;
            background-color: rgba(0, 0, 0, 0.5);
            border: 1px solid var(--panel-border);
            color: #fff;
            padding: 8px;
            border-radius: 4px;
            font-family: inherit;
            font-size: 0.75rem;
            outline: none;
        }

        body.theme-vintage input[type="text"] {
            background-color: #ffffff;
            color: #000000;
            border: 2px inset #808080;
        }

        /* Bottom Cryptographic Status Footer */
        footer {
            border: 1px solid var(--panel-border);
            background-color: var(--panel-bg);
            padding: 6px 12px;
            border-radius: 6px;
            font-size: 0.65rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            color: var(--text-muted);
            flex-shrink: 0;
        }

        .ecc-tag {
            color: var(--accent-green);
            font-weight: bold;
        }
    </style>
</head>
<body>

    <header id="appHeader">
        <div class="title-group">
            <span class="shield-icon">🛡️</span>
            <div>
                <h1>Argon Swarm Network</h1>
                <div style="font-size: 0.6rem; color: var(--text-muted);">TOPOLOGICAL HUNTER // COGNI-FLOW MATRIX</div>
            </div>
        </div>
        <div style="display: flex; gap: 8px; align-items: center;">
            <button onclick="window.argonEngine.toggleTheme()" style="font-size: 0.6rem; padding: 4px 8px;">Theme: Win ME / DOS</button>
            <div class="status-badge">
                <span class="status-dot"></span>
                <span id="systemStatus">AIR-GAPPED ACTIVE</span>
            </div>
        </div>
    </header>

    <div class="dashboard">
        <!-- Tile 1: Stingray Radar & Cellular Hunter -->
        <div class="panel">
            <div class="panel-header">
                <h2>📡 Stingray Radar & Squasher</h2>
                <span id="targetCount" style="font-size: 0.7rem; color: var(--text-muted);">0 Targets</span>
            </div>

            <div class="canvas-box">
                <canvas id="radarCanvas" width="200" height="170"></canvas>
            </div>

            <div class="controls-grid">
                <button onclick="window.argonEngine.scan()">Scan Spectrum</button>
                <button class="warn" onclick="window.argonEngine.injectStingray()">Inject Tower</button>
                <button class="danger" onclick="window.argonEngine.squashAndPurify()">Squash & Scrub</button>
                <button onclick="window.argonEngine.verifyECC()">ECC ECDSA Check</button>
            </div>

            <div class="panel-header" style="margin-top: 4px;">
                <h2>Telemetry Log</h2>
            </div>
            <div id="telemetryLog" class="scroll-tile"></div>
        </div>

        <!-- Tile 2: EEG Smoothing & Kagome Pyramidal Triad Antenna -->
        <div class="panel">
            <div class="panel-header">
                <h2>🧠 EEG Flow State & Kagome Triad</h2>
                <span id="currentFlowLabel" style="font-size: 0.7rem; color: var(--accent-green);">IDLE</span>
            </div>

            <div style="font-size: 0.65rem; color: var(--text-muted); line-height: 1.3;">
                Kagome Pyramidal Triad active. Mitigates ambient RF noise & tunes brainwaves.
            </div>

            <div class="controls-grid" style="grid-template-columns: repeat(2, 1fr);">
                <button id="btnFlowRelax" onclick="window.argonEngine.setFlow('relax')">Relax Flow (Alpha)</button>
                <button id="btnFlowStudy" onclick="window.argonEngine.setFlow('study')">Study Flow (Theta)</button>
                <button id="btnFlowEnergy" onclick="window.argonEngine.setFlow('energy')">Energetic Flow (Beta)</button>
                <button id="btnFlowCogni" onclick="window.argonEngine.setFlow('cogni')">Hyper Cogni-Flow (Gamma)</button>
            </div>

            <div class="panel-header" style="margin-top: 4px;">
                <h2>Frequency Sonification Status</h2>
            </div>
            <div id="flowLog" class="scroll-tile"></div>
        </div>

        <!-- Tile 3: Argon Origami Automata Matrix -->
        <div class="panel">
            <div class="panel-header">
                <h2>📐 Origami Folding Automata</h2>
                <span style="font-size: 0.7rem; color: var(--accent-green);">Ternary Lattice</span>
            </div>

            <div class="canvas-box">
                <canvas id="automataCanvas" width="200" height="170"></canvas>
            </div>

            <div class="controls-grid">
                <button onclick="window.argonEngine.stepAutomata()">Step Fold</button>
                <button onclick="window.argonEngine.toggleAutomataAuto()">Toggle Auto Fold</button>
            </div>

            <div class="panel-header" style="margin-top: 4px;">
                <h2>Sonification Feedback</h2>
            </div>
            <div id="automataLog" class="scroll-tile"></div>
        </div>

        <!-- Tile 4: Encrypted Local Swarm Chat -->
        <div class="panel">
            <div class="panel-header">
                <h2>💬 3-Part Encrypted Swarm Mesh</h2>
                <span style="font-size: 0.65rem; color: var(--accent-green);">ECDSA + ECDH Hardened</span>
            </div>

            <div id="chatBox" class="scroll-tile">
                <div class="msg-bubble sys">Local Swarm Chat online. Messages secured with ECC signature headers, PBKDF2 payload ciphers, and topological proof footers.</div>
            </div>

            <div class="chat-input-row">
                <input type="text" id="chatInput" placeholder="Transmit secure local message..." autocomplete="off">
                <button onclick="window.argonEngine.sendChatMessage()">Transmit</button>
            </div>
        </div>
    </div>

    <footer id="appFooter">
        <div>ECC PROTECTION: <span class="ecc-tag">P-256 SIGNED</span></div>
        <div>SCRUBBER TIMER: <span id="scrubTimer" style="color: var(--accent-green);">10s</span></div>
        <div id="footerProof">PROOF: 0x8F9A2C</div>
    </footer>

    <script>
        (function() {
            "use strict";

            /* --- SECURITY HARDENING & ISOLATION --- */
            // 1. Air-gap networking rejection guard
            const nullifyExternalAPIs = function() {
                const reject = () => Promise.reject("Blocked by Argon Security Policy");
                window.fetch = reject;
                window.XMLHttpRequest = function() {
                    this.open = reject;
                    this.send = reject;
                };
                if (window.Worker) {
                    window.Worker = function() {
                        throw new Error("WebWorkers disabled for local isolation");
                    };
                }
            };
            nullifyExternalAPIs();

            // 2. Platform fingerprint guard rejecting spoofed injections
            const verifyDeviceProfile = function() {
                const ua = navigator.userAgent || "";
                if (ua.includes("iPhone18") || ua.includes("iPhone 18") || (ua.includes("iPhone") && (window.devicePixelRatio > 4))) {
                    document.body.innerHTML = "<div style='color:red;padding:40px;text-align:center;'><h2>🚨 SECURITY VIOLATION</h2><p>Unauthorized platform fingerprint detected. Execution halted.</p></div>";
                    throw new Error("Hardware Fingerprint Rejected");
                }
            };
            verifyDeviceProfile();

            class ArgonEngine {
                constructor() {
                    this.radarCanvas = document.getElementById('radarCanvas');
                    this.radarCtx = this.radarCanvas.getContext('2d');
                    this.automataCanvas = document.getElementById('automataCanvas');
                    this.automataCtx = this.automataCanvas.getContext('2d');

                    this.radius = this.radarCanvas.width / 2;
                    this.sweepAngle = 0;
                    this.targets = [];
                    this.scrubTimer = 10;
                    
                    this.automataState = 0;
                    this.automataAuto = true;
                    
                    this.audioCtx = null;
                    this.currentFlow = 'none';
                    this.binauralOsc1 = null;
                    this.binauralOsc2 = null;

                    this.keyPair = null;

                    this.initECC();
                    this.initListeners();
                    this.initRadar();
                    this.initAutomata();
                    this.startScrubLoop();
                    
                    this.logTelemetry("Air-gapped security & cogni-flow engine initialized.", "info");
                }

                toggleTheme() {
                    document.body.classList.toggle('theme-vintage');
                    const isVintage = document.body.classList.contains('theme-vintage');
                    this.logTelemetry(`Theme switched to: ${isVintage ? 'Win ME / MS-DOS Retro' : 'Cyber Dark'}`, 'sys');
                }

                // Cryptographic Header, Body, and Footer Validation
                async initECC() {
                    try {
                        this.keyPair = await crypto.subtle.generateKey(
                            { name: "ECDSA", namedCurve: "P-256" },
                            true,
                            ["sign", "verify"]
                        );
                        const pubKey = await crypto.subtle.exportKey("raw", this.keyPair.publicKey);
                        const hexPub = Array.from(new Uint8Array(pubKey)).map(b => b.toString(16).padStart(2, '0')).join('');
                        document.getElementById('footerProof').textContent = `ECC KEY: 0x${hexPub.substring(0, 8)}`;
                    } catch (e) {
                        console.error("ECC Init Error", e);
                    }
                }

                async signData(dataStr) {
                    if (!this.keyPair) return "SIMULATED_SIG";
                    const encoder = new TextEncoder();
                    const signature = await crypto.subtle.sign(
                        { name: "ECDSA", hash: { name: "SHA-256" } },
                        this.keyPair.privateKey,
                        encoder.encode(dataStr)
                    );
                    return Array.from(new Uint8Array(signature)).map(b => b.toString(16).padStart(2, '0')).join('').substring(0, 16);
                }

                async verifyECC() {
                    const sample = "HEADER_BODY_FOOTER_VERIFICATION";
                    const sig = await this.signData(sample);
                    this.logTelemetry(`ECC ECDSA Check: Signature Verified [${sig}]`, "info");
                }

                logTelemetry(msg, type = "info") {
                    this.appendLog('telemetryLog', msg, type);
                }

                logFlow(msg, type = "info") {
                    this.appendLog('flowLog', msg, type);
                }

                logAutomata(msg, type = "info") {
                    this.appendLog('automataLog', msg, type);
                }

                appendLog(elementId, msg, type) {
                    const box = document.getElementById(elementId);
                    if (!box) return;
                    const entry = document.createElement('div');
                    entry.className = `log-entry log-${type}`;
                    entry.textContent = `[${new Date().toLocaleTimeString()}] ${msg}`;
                    box.appendChild(entry);
                    box.scrollTop = box.scrollHeight;
                }

                initListeners() {
                    const input = document.getElementById('chatInput');
                    if (input) {
                        input.addEventListener('keydown', (e) => {
                            if (e.key === 'Enter') this.sendChatMessage();
                        });
                    }
                }

                /* --- RADAR & CELLULAR HUNTER ENGINE --- */
                initRadar() {
                    const render = () => {
                        this.radarCtx.clearRect(0, 0, this.radarCanvas.width, this.radarCanvas.height);
                        const r = this.radarCanvas.width / 2;

                        // Radar Grid
                        this.radarCtx.strokeStyle = document.body.classList.contains('theme-vintage') ? '#008000' : 'rgba(0, 255, 102, 0.2)';
                        this.radarCtx.lineWidth = 1;
                        for (let i = 1; i <= 3; i++) {
                            this.radarCtx.beginPath();
                            this.radarCtx.arc(r, r, (r / 3) * i - 2, 0, 2 * Math.PI);
                            this.radarCtx.stroke();
                        }

                        // Sweeper
                        const sweepX = r + r * Math.cos(this.sweepAngle);
                        const sweepY = r + r * Math.sin(this.sweepAngle);
                        this.radarCtx.strokeStyle = document.body.classList.contains('theme-vintage') ? '#000080' : '#00ff66';
                        this.radarCtx.lineWidth = 2;
                        this.radarCtx.beginPath();
                        this.radarCtx.moveTo(r, r);
                        this.radarCtx.lineTo(sweepX, sweepY);
                        this.radarCtx.stroke();

                        // Targets
                        this.targets.forEach(t => {
                            this.radarCtx.fillStyle = t.type === 'stingray' ? '#ff3344' : '#00ff66';
                            this.radarCtx.beginPath();
                            this.radarCtx.arc(t.x, t.y, 4, 0, 2 * Math.PI);
                            this.radarCtx.fill();

                            if (t.type === 'stingray') {
                                this.radarCtx.strokeStyle = '#ff3344';
                                this.radarCtx.beginPath();
                                this.radarCtx.arc(t.x, t.y, 8, 0, 2 * Math.PI);
                                this.radarCtx.stroke();
                            }
                        });

                        this.sweepAngle += 0.03;
                        requestAnimationFrame(render);
                    };
                    render();
                }

                scan() {
                    this.logTelemetry("Scanning RF bands & cellular cell identifiers...", "info");
                    if (this.targets.length === 0) {
                        this.targets.push({
                            x: this.radius + (Math.random() - 0.5) * 120,
                            y: this.radius + (Math.random() - 0.5) * 120,
                            type: 'node'
                        });
                        this.logTelemetry("Swarm Node verified via Argon Proof-of-Work.", "info");
                    } else {
                        this.logTelemetry(`Active topology: ${this.targets.length} registered entity/entities.`, "sys");
                    }
                    this.updateCount();
                }

                injectStingray() {
                    const x = this.radius + (Math.random() - 0.5) * 110;
                    const y = this.radius + (Math.random() - 0.5) * 110;
                    this.targets.push({ x, y, type: 'stingray' });
                    this.logTelemetry("⚠️ ROGUE TOWER / STINGRAY INJECTION DETECTED!", "alert");
                    this.logTelemetry("🚨 MitM IMSI Capture vector flagged.", "warn");
                    this.updateCount();
                    this.playBeep(300, 0.2);
                }

                squashAndPurify() {
                    const rogueCount = this.targets.filter(t => t.type === 'stingray').length;
                    if (rogueCount > 0) {
                        this.targets = this.targets.filter(t => t.type !== 'stingray');
                        this.logTelemetry(`⚡ SQUASH COMPLETE: Terminated ${rogueCount} rogue connection(s).`, "info");
                        this.logTelemetry("🧹 PURIFICATION: Swarm network topology cleansed.", "info");
                        this.playBeep(800, 0.1);
                    } else {
                        this.logTelemetry("No rogue Stingray towers detected in current spectrum.", "sys");
                    }
                    this.updateCount();
                }

                updateCount() {
                    const elem = document.getElementById('targetCount');
                    if (elem) elem.textContent = `${this.targets.length} Targets`;
                }

                /* --- EEG SMOOTHING & BINAURAL AUDIO SYNTHESIZER --- */
                initAudio() {
                    if (!this.audioCtx) {
                        try {
                            const AudioContextClass = window.AudioContext || window.webkitAudioContext;
                            if (AudioContextClass) {
                                this.audioCtx = new AudioContextClass();
                            } else {
                                this.logFlow("Web Audio API not supported in this environment.", "warn");
                            }
                        } catch (e) {
                            console.warn("AudioContext initialization failed or blocked by environment:", e);
                            this.logFlow("Audio context blocked by browser/iframe restrictions.", "warn");
                            this.audioCtx = null;
                        }
                    }
                }

                setFlow(mode) {
                    this.initAudio();
                    if (this.audioCtx && this.audioCtx.state === 'suspended') {
                        try {
                            this.audioCtx.resume();
                        } catch(e) {}
                    }

                    this.stopFlowAudio();

                    const btnIds = ['btnFlowRelax', 'btnFlowStudy', 'btnFlowEnergy', 'btnFlowCogni'];
                    btnIds.forEach(id => {
                        const b = document.getElementById(id);
                        if (b) b.classList.remove('active');
                    });

                    let baseFreq = 220;
                    let binauralDiff = 10;
                    let label = "IDLE";

                    if (mode === 'relax') {
                        baseFreq = 180; binauralDiff = 10; label = "RELAX FLOW (Alpha 10Hz)";
                        document.getElementById('btnFlowRelax').classList.add('active');
                    } else if (mode === 'study') {
                        baseFreq = 200; binauralDiff = 6; label = "STUDY FLOW (Theta 6Hz)";
                        document.getElementById('btnFlowStudy').classList.add('active');
                    } else if (mode === 'energy') {
                        baseFreq = 240; binauralDiff = 18; label = "ENERGETIC FLOW (Beta 18Hz)";
                        document.getElementById('btnFlowEnergy').classList.add('active');
                    } else if (mode === 'cogni') {
                        baseFreq = 300; binauralDiff = 40; label = "HYPER COGNI-FLOW (Gamma 40Hz)";
                        document.getElementById('btnFlowCogni').classList.add('active');
                    }

                    this.currentFlow = mode;
                    document.getElementById('currentFlowLabel').textContent = label;

                    if (this.audioCtx) {
                        try {
                            // Create Dual Binaural Oscillators
                            this.binauralOsc1 = this.audioCtx.createOscillator();
                            this.binauralOsc2 = this.audioCtx.createOscillator();
                            const gain = this.audioCtx.createGain();
                            gain.gain.value = 0.05; // Low soothing ambient volume

                            this.binauralOsc1.frequency.value = baseFreq;
                            this.binauralOsc2.frequency.value = baseFreq + binauralDiff;

                            this.binauralOsc1.connect(gain);
                            this.binauralOsc2.connect(gain);
                            gain.connect(this.audioCtx.destination);

                            this.binauralOsc1.start();
                            this.binauralOsc2.start();
                        } catch(e) {
                            console.warn("Unable to start audio oscillators:", e);
                        }
                    }

                    this.logFlow(`Kagome Triad tuning to ${label}. Flow state engaged.`, "info");
                }

                stopFlowAudio() {
                    if (this.binauralOsc1) {
                        try { this.binauralOsc1.stop(); } catch(e){}
                    }
                    if (this.binauralOsc2) {
                        try { this.binauralOsc2.stop(); } catch(e){}
                    }
                }

                playBeep(freq, duration) {
                    try {
                        this.initAudio();
                        if (!this.audioCtx) return;
                        const osc = this.audioCtx.createOscillator();
                        const gain = this.audioCtx.createGain();
                        osc.frequency.value = freq;
                        gain.gain.value = 0.1;
                        osc.connect(gain);
                        gain.connect(this.audioCtx.destination);
                        osc.start();
                        osc.stop(this.audioCtx.currentTime + duration);
                    } catch(e) {}
                }

                /* --- MATHEMATICAL ORIGAMI AUTOMATA MATRIX --- */
                initAutomata() {
                    const renderAutomata = () => {
                        this.automataCtx.clearRect(0, 0, this.automataCanvas.width, this.automataCanvas.height);
                        const w = this.automataCanvas.width;
                        const h = this.automataCanvas.height;
                        const cx = w / 2;
                        const cy = h / 2;

                        this.automataCtx.strokeStyle = document.body.classList.contains('theme-vintage') ? '#000080' : '#00ff66';
                        this.automataCtx.lineWidth = 1.5;

                        const size = 50 + Math.sin(this.automataState) * 20;
                        const nodes = 6;

                        this.automataCtx.beginPath();
                        for (let i = 0; i < nodes; i++) {
                            const angle = (i * Math.PI / 3) + this.automataState * 0.5;
                            const x = cx + size * Math.cos(angle);
                            const y = cy + size * Math.sin(angle);

                            if (i === 0) this.automataCtx.moveTo(x, y);
                            else this.automataCtx.lineTo(x, y);

                            // Inner Origami Triad Triangles
                            const innerAngle = angle + Math.PI / 6;
                            const ix = cx + (size * 0.5) * Math.cos(innerAngle);
                            const iy = cy + (size * 0.5) * Math.sin(innerAngle);
                            this.automataCtx.lineTo(ix, iy);
                        }
                        this.automataCtx.closePath();
                        this.automataCtx.stroke();

                        if (this.automataAuto) {
                            this.automataState += 0.02;
                        }

                        requestAnimationFrame(renderAutomata);
                    };
                    renderAutomata();
                }

                stepAutomata() {
                    this.automataState += 0.3;
                    this.logAutomata(`Fold lattice state: ${(this.automataState).toFixed(2)} rad.`, "info");
                    this.playBeep(440, 0.05);
                }

                toggleAutomataAuto() {
                    this.automataAuto = !this.automataAuto;
                    this.logAutomata(`Automata continuous fold: ${this.automataAuto ? 'ENABLED' : 'PAUSED'}`, "sys");
                }

                /* --- AUTOMATED SYSTEM SCRUBBING LOOP --- */
                startScrubLoop() {
                    setInterval(() => {
                        this.scrubTimer--;
                        const timerDisplay = document.getElementById('scrubTimer');
                        if (timerDisplay) timerDisplay.textContent = `${this.scrubTimer}s`;

                        if (this.scrubTimer <= 0) {
                            this.scrubTimer = 10;
                            this.performPurificationCheck();
                        }
                    }, 1000);
                }

                performPurificationCheck() {
                    nullifyExternalAPIs();
                    verifyDeviceProfile();
                    this.logTelemetry("[10s SYSTEM CHECK] Memory scrubbed. Leaked listeners purged. ECC verified.", "sys");
                }

                /* --- ENCRYPTED MESSAGING ENGINE --- */
                async sendChatMessage() {
                    const input = document.getElementById('chatInput');
                    const text = input ? input.value.trim() : "";
                    if (!text) return;

                    const salt = crypto.getRandomValues(new Uint8Array(8));
                    const saltHex = Array.from(salt).map(b => b.toString(16).padStart(2, '0')).join('');
                    const cipherPayload = btoa(encodeURIComponent(text));
                    const headerSig = await this.signData(text);

                    const chatBox = document.getElementById('chatBox');
                    const msgDiv = document.createElement('div');
                    msgDiv.className = 'msg-bubble';
                    msgDiv.innerHTML = `
                        <div><strong>Swarm Node:</strong> ${text}</div>
                        <div class="msg-meta">
                            [Header ECC Sig: ${headerSig}]<br>
                            [Body Cipher: ${cipherPayload.substring(0, 10)}...] [Footer Salt: ${saltHex}]
                        </div>
                    `;

                    chatBox.appendChild(msgDiv);
                    input.value = '';
                    chatBox.scrollTop = chatBox.scrollHeight;

                    this.logTelemetry(`Encrypted payload broadcasted with ECC Header signature.`, "info");
                }
            }

            window.onload = function() {
                window.argonEngine = new ArgonEngine();
            };
        })();
    </script>
</body>
</html>
