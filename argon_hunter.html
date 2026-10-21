<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Argon Swarm: Stingray & Clone Hunter</title>
    <style>
        :root {
            --bg-color: #0d1117;
            --panel-bg: #161b22;
            --accent-green: #238636;
            --radar-green: #00ff66;
            --alert-red: #ff3333;
            --text-color: #c9d1d9;
            --border-color: #30363d;
        }

        body {
            margin: 0;
            padding: 20px;
            background-color: var(--bg-color);
            color: var(--text-color);
            font-family: 'Courier New', Courier, monospace;
            display: flex;
            flex-direction: column;
            gap: 20px;
            height: 95vh;
        }

        header {
            border-bottom: 2px solid var(--accent-green);
            padding-bottom: 10px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .dashboard {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
            flex-grow: 1;
            min-height: 0;
        }

        .panel {
            background-color: var(--panel-bg);
            border: 1px solid var(--border-color);
            border-radius: 8px;
            padding: 15px;
            display: flex;
            flex-direction: column;
            overflow: hidden;
        }

        /* Radar Styling */
        .radar-container {
            position: relative;
            width: 100%;
            height: 300px;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        canvas#radarCanvas {
            background-color: #051105;
            border-radius: 50%;
            border: 2px solid var(--radar-green);
            box-shadow: 0 0 15px rgba(0, 255, 102, 0.2);
        }

        /* Controls & Logs */
        .controls {
            margin-top: 15px;
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
        }

        button {
            background-color: #21262d;
            color: var(--radar-green);
            border: 1px solid var(--radar-green);
            padding: 8px 12px;
            border-radius: 4px;
            cursor: pointer;
            font-family: inherit;
            font-weight: bold;
        }

        button:hover {
            background-color: var(--radar-green);
            color: #000;
        }

        button.danger {
            color: var(--alert-red);
            border-color: var(--alert-red);
        }

        button.danger:hover {
            background-color: var(--alert-red);
            color: #fff;
        }

        .log-box {
            flex-grow: 1;
            background-color: #000;
            border: 1px solid var(--border-color);
            padding: 10px;
            margin-top: 10px;
            overflow-y: auto;
            font-size: 0.85em;
        }

        .log-entry { margin-bottom: 4px; }
        .log-alert { color: var(--alert-red); font-weight: bold; }
        .log-info { color: var(--radar-green); }

        /* Chat Styling */
        .chat-messages {
            flex-grow: 1;
            background-color: #0d1117;
            border: 1px solid var(--border-color);
            padding: 10px;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 8px;
        }

        .message {
            background: #21262d;
            padding: 8px 12px;
            border-radius: 6px;
            max-width: 80%;
        }

        .message.system {
            align-self: center;
            background: transparent;
            color: #8b949e;
            font-style: italic;
        }

        .chat-input-group {
            display: flex;
            gap: 10px;
            margin-top: 10px;
        }

        input[type="text"] {
            flex-grow: 1;
            background-color: #0d1117;
            border: 1px solid var(--border-color);
            color: #fff;
            padding: 8px;
            border-radius: 4px;
            font-family: inherit;
        }
    </style>
</head>
<body>

    <header>
        <h2>🛡️ ARGON SWARM // TURING-COMPLETE CELLULAR AGENT</h2>
        <div>STATUS: <span id="swarm-status" style="color:var(--radar-green)">ACTIVE NET</span></div>
    </header>

    <div class="dashboard">
        <!-- Panel 1: Radar & Squasher -->
        <div class="panel">
            <h3>📡 STINGRAY RADAR & CELLULAR HUNTER</h3>
            <div class="radar-container">
                <canvas id="radarCanvas" width="280" height="280"></canvas>
            </div>
            <div class="controls">
                <button onclick="scanNetwork()">Scan Frequencies</button>
                <button onclick="simulateStingray()" class="danger">Inject Stingray Signal</button>
                <button onclick="squashThreats()" class="danger">Squash & Purify</button>
            </div>
            <h4>System Telemetry & Scrubbing Log</h4>
            <div id="telemetryLog" class="log-box"></div>
        </div>

        <!-- Panel 2: Secure Chat & Encryption -->
        <div class="panel">
            <h3>💬 3-PART ENCRYPTED SWARM CHAT</h3>
            <div id="chatMessages" class="chat-messages">
                <div class="message system">Node initialized. 3-Part Argon Net Key Active.</div>
            </div>
            <div class="chat-input-group">
                <input type="text" id="chatInput" placeholder="Broadcast encrypted payload..." onkeydown="if(event.key==='Enter') sendMessage()">
                <button onclick="sendMessage()">Transmit</button>
            </div>
        </div>
    </div>

    <script>
        // --- 1. RADAR & TELEMETRY ENGINE ---
        const canvas = document.getElementById('radarCanvas');
        const ctx = canvas.getContext('2d');
        const radius = canvas.width / 2;
        let sweepAngle = 0;
        let targets = [];

        function drawRadar() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);

            // Draw Radar Circles
            ctx.strokeStyle = '#005522';
            ctx.lineWidth = 1;
            for (let i = 1; i <= 3; i++) {
                ctx.beginPath();
                ctx.arc(radius, radius, (radius / 3) * i - 2, 0, 2 * Math.PI);
                ctx.stroke();
            }

            // Draw Crosshairs
            ctx.beginPath();
            ctx.moveTo(radius, 0); ctx.lineTo(radius, canvas.height);
            ctx.moveTo(0, radius); ctx.lineTo(canvas.width, radius);
            ctx.stroke();

            // Draw Sweep Line
            const sweepX = radius + radius * Math.cos(sweepAngle);
            const sweepY = radius + radius * Math.sin(sweepAngle);
            ctx.strokeStyle = '#00ff66';
            ctx.lineWidth = 2;
            ctx.beginPath();
            ctx.moveTo(radius, radius);
            ctx.lineTo(sweepX, sweepY);
            ctx.stroke();

            // Draw Targets
            targets.forEach(target => {
                ctx.fillStyle = target.type === 'stingray' ? '#ff3333' : '#00ff66';
                ctx.beginPath();
                ctx.arc(target.x, target.y, 5, 0, 2 * Math.PI);
                ctx.fill();
                
                if(target.type === 'stingray') {
                    ctx.strokeStyle = '#ff3333';
                    ctx.arc(target.x, target.y, 9, 0, 2 * Math.PI);
                    ctx.stroke();
                }
            });

            sweepAngle += 0.03;
            requestAnimationFrame(drawRadar);
        }
        drawRadar();

        function logTelemetry(msg, isAlert = false) {
            const logBox = document.getElementById('telemetryLog');
            const entry = document.createElement('div');
            entry.className = `log-entry ${isAlert ? 'log-alert' : 'log-info'}`;
            entry.textContent = `[${new Date().toLocaleTimeString()}] ${msg}`;
            logBox.appendChild(entry);
            logBox.scrollTop = logBox.scrollHeight;
        }

        function scanNetwork() {
            logTelemetry("Scanning cellular band (IMSI Catcher / IMSI Guard Check)...");
            if (targets.length === 0) {
                targets.push({
                    x: radius + (Math.random() - 0.5) * 180,
                    y: radius + (Math.random() - 0.5) * 180,
                    type: 'friendly'
                });
                logTelemetry("Swarm Node verified via Argon Proof-of-Work.");
            }
        }

        function simulateStingray() {
            const x = radius + (Math.random() - 0.5) * 160;
            const y = radius + (Math.random() - 0.5) * 160;
            targets.push({ x, y, type: 'stingray' });
            logTelemetry("⚠️ WARNING: Rogue Tower/IMSI Catcher detected! (MitM attempt)", true);
            logTelemetry("🚨 Downgrade attack flagged (2G/3G force detected).", true);
        }

        function squashThreats() {
            const rogueCount = targets.filter(t => t.type === 'stingray').length;
            if (rogueCount > 0) {
                targets = targets.filter(t => t.type !== 'stingray');
                logTelemetry(`⚡ SQUASH COMPLETE: Terminated ${rogueCount} rogue connection(s).`);
                logTelemetry("🧹 PURIFICATION: Swarm network topology cleansed.");
            } else {
                logTelemetry("No rogue towers detected to squash.");
            }
        }

        // --- 2. THREE-PART ENCRYPTION & SCRUBBING SIMULATOR ---
        // Part 1: Salt Hash | Part 2: Payload Cipher | Part 3: Topological Proof
        async function threePartEncrypt(text) {
            const encoder = new TextEncoder();
            const salt = crypto.getRandomValues(new Uint8Array(16));
            
            // Generate Key via Argon-like Hash Simulation (WebCrypto SHA-256 derivation)
            const keyData = encoder.encode(text + Array.from(salt).join(''));
            const hashBuffer = await crypto.subtle.digest('SHA-256', keyData);
            const hashArray = Array.from(new Uint8Array(hashBuffer));
            const hexHash = hashArray.map(b => b.toString(16).padStart(2, '0')).join('');

            return {
                part1_salt: Array.from(salt).map(b => b.toString(16)).join(''),
                part2_cipher: btoa(text), // Base64 simulated cipher
                part3_topoProof: hexHash.substring(0, 16)
            };
        }

        async function sendMessage() {
            const input = document.getElementById('chatInput');
            const text = input.value.trim();
            if (!text) return;

            const chatMessages = document.getElementById('chatMessages');

            // Encrypt
            const encrypted = await threePartEncrypt(text);

            // Display sent message
            const msgDiv = document.createElement('div');
            msgDiv.className = 'message';
            msgDiv.innerHTML = `<strong>You:</strong> ${text}<br>
                <small style="color:#8b949e">Encrypted Parts: [Salt: ${encrypted.part1_salt.substring(0,6)}...] [Cipher: ${encrypted.part2_cipher}] [Proof: ${encrypted.part3_topoProof}]</small>`;
            
            chatMessages.appendChild(msgDiv);
            input.value = '';
            chatMessages.scrollTop = chatMessages.scrollHeight;

            logTelemetry(`Payload transmitted. Swarm Proof Token: ${encrypted.part3_topoProof}`);
        }
    </script>
</body>
</html>
