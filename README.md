Argon Swarm Security Hub & Cogni-Flow Matrix

<svg width="180" height="180" viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg">
    <defs>
      <radialGradient id="logoGrad" cx="50%" cy="50%" r="50%">
        <stop offset="0%" stop-color="#00ff66" stop-opacity="0.8" />
        <stop offset="100%" stop-color="#080c10" stop-opacity="1" />
      </radialGradient>
      <linearGradient id="shieldGrad" x1="0%" y1="0%" x2="100%" y2="100%">
        <stop offset="0%" stop-color="#00ff66" />
        <stop offset="100%" stop-color="#008080" />
      </linearGradient>
    </defs>
    <circle cx="100" cy="100" r="90" fill="url(#logoGrad)" stroke="#00ff66" stroke-width="2" />
    <path d="M 100 30 L 150 60 L 150 110 C 150 145 100 170 100 170 C 100 170 50 145 50 110 L 50 60 Z" fill="none" stroke="url(#shieldGrad)" stroke-width="6" />
    <polygon points="100,55 115,85 145,100 115,115 100,145 85,115 55,100 85,85" fill="none" stroke="#00ff66" stroke-width="3" />
    <circle cx="100" cy="100" r="10" fill="#00ff66" />
  </svg>

🛡️ Overview

The Argon Swarm Security Hub is a single-file, air-gapped web engine built for topological swarm defense, cellular IMSI-catcher (Stingray) squashing, EEG binaural brainwave sonification via a Kagome Pyramidal Triad, and local encrypted mesh communications.

Authored by j-mosij, this repository provides zero-dependency deployment with rigorous client-side Elliptic Curve Cryptography (ECC P-256 / ECDSA).

✨ Features

📡 Stingray Radar & Cellular Hunter: Real-time canvas radar for detecting rogue cellular towers and squashing MitM vectors.

🧠 EEG Flow State & Kagome Triad Engine: Dual-oscillator binaural sonification synthesizer supporting Alpha (10Hz), Theta (6Hz), Beta (18Hz), and Gamma Cogni-Flow (40Hz).

📐 Mathematical Origami Automata Matrix: Continuous 2D/3D folding geometric lattice with step sonification feedback.

💬 3-Part Encrypted Local Swarm Chat: ECDSA-signed headers, PBKDF2 payload ciphers, and salt footers via WebCrypto API.

🕹️ Dual Themes: Cyber Dark HUD and Retro Windows ME / MS-DOS Vintage interface.

🔒 Air-Gapped Security Enforcement: Nullified network wrappers (fetch, XHR, Worker), memory sanitization loops, and fingerprint protection.

🚀 Quick Start

Option 1: Direct Browser Launch

Since the application is zero-dependency single-file HTML, simply clone and open:

git clone https://github.com/j-mosij/argon-swarm-security-hub.git
cd argon-swarm-security-hub
open index.html


Option 2: Local Development Server

# Install dependencies
npm install

# Start local dev server
npm start


🏗️ Architecture

argon-swarm-security-hub/
├── index.html              # Main single-file application
├── package.json            # Node metadata & dev scripts
├── .gitignore              # Version control exclusions
├── .github/
│   └── workflows/
│       └── ci-cd.yml       # Automated GitHub Actions CI/CD pipeline
└── README.md               # Project documentation


🔒 Security Hardening

Note on Public Safety & Secrets: This codebase contains NO hardcoded secrets, API tokens, or private credentials. All cryptographic keys are generated ephemeral-in-memory via client-side window.crypto.subtle.

Network Isolation: Blocks unexpected outbound network traffic at runtime.

Auto-Scrubber: 10-second background memory purge loop to clear detached nodes and verify ECC signature integrity.

Air-Gap Compliance: Designed to run entirely offline on air-gapped hardware.

📄 License
