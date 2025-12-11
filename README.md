<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Jordan Dudgeon - Developer & System Architect. Transforming complexity into elegant technical solutions.">
    <title>JORDAN.DUDGEON_v2.5.1 // SYSTEM ONLINE</title>
    
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@400;500;600;700&family=Orbitron:wght@700;900&display=swap" rel="stylesheet">
    
    <style>
        /* ============================================
           TERMINAL HACKER AESTHETIC
           ============================================ */
        
        :root {
            /* Color Palette */
            --terminal-bg: #0a0e0f;
            --terminal-primary: #00ff41;
            --terminal-secondary: #00d4ff;
            --terminal-accent: #ff2a6d;
            --terminal-warning: #ffd000;
            --terminal-muted: #1a2f35;
            --terminal-text: #c7f0d8;
            --terminal-dim: #4a6f7a;
            
            /* Typography */
            --font-mono: 'IBM Plex Mono', 'Courier New', monospace;
            --font-display: 'Orbitron', monospace;
            
            /* Effects */
            --glow-primary: 0 0 10px var(--terminal-primary),
                            0 0 20px var(--terminal-primary),
                            0 0 30px var(--terminal-primary);
            --glow-accent: 0 0 10px var(--terminal-accent),
                           0 0 20px var(--terminal-accent);
            --scanline-opacity: 0.03;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: var(--font-mono);
            background: var(--terminal-bg);
            color: var(--terminal-text);
            line-height: 1.6;
            overflow-x: hidden;
            position: relative;
        }

        /* ============================================
           CRT MONITOR EFFECTS
           ============================================ */
        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: repeating-linear-gradient(
                0deg,
                rgba(0, 0, 0, 0.15),
                rgba(0, 0, 0, 0.15) 1px,
                transparent 1px,
                transparent 2px
            );
            pointer-events: none;
            z-index: 9999;
            opacity: var(--scanline-opacity);
            animation: scanlines 10s linear infinite;
        }

        @keyframes scanlines {
            0% { transform: translateY(0); }
            100% { transform: translateY(10px); }
        }

        /* Animated background grid */
        .grid-background {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: 
                linear-gradient(rgba(0, 255, 65, 0.03) 1px, transparent 1px),
                linear-gradient(90deg, rgba(0, 255, 65, 0.03) 1px, transparent 1px);
            background-size: 50px 50px;
            animation: gridMove 20s linear infinite;
            z-index: 0;
        }

        @keyframes gridMove {
            0% { transform: translate(0, 0); }
            100% { transform: translate(50px, 50px); }
        }

        /* Floating code snippets background */
        .code-rain {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            z-index: 1;
            opacity: 0.15;
            pointer-events: none;
        }

        .code-rain span {
            position: absolute;
            top: -100%;
            font-size: 12px;
            color: var(--terminal-primary);
            animation: fall linear infinite;
            font-family: var(--font-mono);
            text-shadow: 0 0 5px var(--terminal-primary);
        }

        @keyframes fall {
            to { top: 110%; }
        }

        /* ============================================
           BOOT SEQUENCE OVERLAY
           ============================================ */
        .boot-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: var(--terminal-bg);
            z-index: 10000;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: flex-start;
            padding: 2rem 10%;
            animation: fadeOut 0.5s ease-out 3s forwards;
        }

        .boot-line {
            font-size: 0.9rem;
            color: var(--terminal-primary);
            margin: 0.2rem 0;
            opacity: 0;
            animation: bootText 0.1s ease-in forwards;
        }

        .boot-line.error {
            color: var(--terminal-accent);
        }

        .boot-line.warning {
            color: var(--terminal-warning);
        }

        .boot-line:nth-child(1) { animation-delay: 0.1s; }
        .boot-line:nth-child(2) { animation-delay: 0.3s; }
        .boot-line:nth-child(3) { animation-delay: 0.5s; }
        .boot-line:nth-child(4) { animation-delay: 0.8s; }
        .boot-line:nth-child(5) { animation-delay: 1.2s; }
        .boot-line:nth-child(6) { animation-delay: 1.5s; }
        .boot-line:nth-child(7) { animation-delay: 1.8s; }
        .boot-line:nth-child(8) { animation-delay: 2.2s; }

        @keyframes bootText {
            to { opacity: 1; }
        }

        @keyframes fadeOut {
            to { 
                opacity: 0;
                visibility: hidden;
            }
        }

        /* ============================================
           MAIN CONTENT CONTAINER
           ============================================ */
        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 2rem;
            position: relative;
            z-index: 10;
            opacity: 0;
            animation: contentFadeIn 1s ease-out 3s forwards;
        }

        @keyframes contentFadeIn {
            to { opacity: 1; }
        }

        /* ============================================
           HEADER / TERMINAL WINDOW
           ============================================ */
        .terminal-window {
            background: rgba(10, 14, 15, 0.95);
            border: 2px solid var(--terminal-primary);
            border-radius: 8px;
            box-shadow: 
                0 0 20px rgba(0, 255, 65, 0.3),
                inset 0 0 60px rgba(0, 255, 65, 0.05);
            margin-bottom: 2rem;
            position: relative;
            overflow: hidden;
        }

        .terminal-header {
            background: linear-gradient(180deg, #1a2f35 0%, #0f1a1d 100%);
            padding: 0.8rem 1rem;
            display: flex;
            align-items: center;
            justify-content: space-between;
            border-bottom: 1px solid var(--terminal-primary);
        }

        .terminal-buttons {
            display: flex;
            gap: 0.5rem;
        }

        .terminal-button {
            width: 14px;
            height: 14px;
            border-radius: 50%;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .terminal-button.close { background: #ff5f57; }
        .terminal-button.minimize { background: #ffbd2e; }
        .terminal-button.maximize { background: #28ca42; }

        .terminal-title {
            font-family: var(--font-mono);
            font-size: 0.85rem;
            color: var(--terminal-primary);
            text-transform: uppercase;
            letter-spacing: 0.05em;
        }

        .terminal-body {
            padding: 2rem;
        }

        /* ============================================
           HERO SECTION
           ============================================ */
        .hero {
            margin-bottom: 3rem;
        }

        .glitch-wrapper {
            position: relative;
            display: inline-block;
        }

        h1 {
            font-family: var(--font-display);
            font-size: clamp(2.5rem, 8vw, 5rem);
            font-weight: 900;
            color: var(--terminal-primary);
            text-transform: uppercase;
            letter-spacing: 0.1em;
            margin-bottom: 1rem;
            text-shadow: var(--glow-primary);
            position: relative;
            animation: glitchFlicker 3s infinite alternate;
        }

        @keyframes glitchFlicker {
            0%, 100% { opacity: 1; }
            92% { opacity: 0.98; }
            93% { opacity: 0.95; }
            95% { opacity: 1; }
        }

        .glitch-wrapper::before,
        .glitch-wrapper::after {
            content: attr(data-text);
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            opacity: 0.8;
        }

        .glitch-wrapper::before {
            color: var(--terminal-accent);
            animation: glitch1 2.5s infinite;
            clip-path: polygon(0 0, 100% 0, 100% 45%, 0 45%);
        }

        .glitch-wrapper::after {
            color: var(--terminal-secondary);
            animation: glitch2 2.5s infinite;
            clip-path: polygon(0 55%, 100% 55%, 100% 100%, 0 100%);
        }

        @keyframes glitch1 {
            0%, 100% { transform: translate(0); }
            20% { transform: translate(-2px, 2px); }
            40% { transform: translate(-2px, -2px); }
            60% { transform: translate(2px, 2px); }
            80% { transform: translate(2px, -2px); }
        }

        @keyframes glitch2 {
            0%, 100% { transform: translate(0); }
            20% { transform: translate(2px, -2px); }
            40% { transform: translate(2px, 2px); }
            60% { transform: translate(-2px, -2px); }
            80% { transform: translate(-2px, 2px); }
        }

        .status-line {
            font-size: 1rem;
            color: var(--terminal-secondary);
            margin: 0.5rem 0;
            font-weight: 500;
        }

        .status-line::before {
            content: '> ';
            color: var(--terminal-primary);
            animation: blink 1s infinite;
        }

        @keyframes blink {
            0%, 50%, 100% { opacity: 1; }
            25%, 75% { opacity: 0; }
        }

        .typing-text {
            font-size: 1.1rem;
            color: var(--terminal-text);
            margin: 1.5rem 0;
            line-height: 1.8;
            border-left: 3px solid var(--terminal-accent);
            padding-left: 1.5rem;
        }

        /* ============================================
           ACTION BUTTONS / LINKS
           ============================================ */
        .action-bar {
            display: flex;
            gap: 1rem;
            flex-wrap: wrap;
            margin-top: 2rem;
        }

        .btn {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            padding: 0.9rem 1.8rem;
            font-family: var(--font-mono);
            font-size: 0.9rem;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.08em;
            text-decoration: none;
            background: transparent;
            color: var(--terminal-primary);
            border: 2px solid var(--terminal-primary);
            position: relative;
            overflow: hidden;
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: var(--terminal-primary);
            transition: left 0.3s ease;
            z-index: -1;
        }

        .btn:hover {
            color: var(--terminal-bg);
            box-shadow: 0 0 20px var(--terminal-primary);
        }

        .btn:hover::before {
            left: 0;
        }

        .btn.secondary {
            border-color: var(--terminal-accent);
            color: var(--terminal-accent);
        }

        .btn.secondary::before {
            background: var(--terminal-accent);
        }

        .btn.secondary:hover {
            box-shadow: 0 0 20px var(--terminal-accent);
        }

        /* ============================================
           SYSTEM STATS / METRICS
           ============================================ */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1.5rem;
            margin: 2rem 0;
        }

        .stat-card {
            background: rgba(0, 255, 65, 0.05);
            border: 1px solid var(--terminal-primary);
            padding: 1.5rem;
            position: relative;
            overflow: hidden;
            transition: all 0.3s ease;
        }

        .stat-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 3px;
            background: var(--terminal-primary);
            transform: scaleX(0);
            transition: transform 0.3s ease;
        }

        .stat-card:hover {
            background: rgba(0, 255, 65, 0.1);
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0, 255, 65, 0.2);
        }

        .stat-card:hover::before {
            transform: scaleX(1);
        }

        .stat-label {
            font-size: 0.75rem;
            color: var(--terminal-dim);
            text-transform: uppercase;
            letter-spacing: 0.1em;
            margin-bottom: 0.5rem;
        }

        .stat-value {
            font-size: 2rem;
            font-weight: 700;
            color: var(--terminal-primary);
            font-family: var(--font-display);
        }

        .stat-unit {
            font-size: 0.9rem;
            color: var(--terminal-secondary);
            margin-left: 0.3rem;
        }

        /* ============================================
           WORKFLOW SECTION
           ============================================ */
        .section-title {
            font-family: var(--font-display);
            font-size: clamp(1.5rem, 4vw, 2.5rem);
            color: var(--terminal-secondary);
            text-transform: uppercase;
            margin-bottom: 1.5rem;
            position: relative;
            display: inline-block;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 100%;
            height: 2px;
            background: linear-gradient(90deg, 
                var(--terminal-secondary) 0%, 
                transparent 100%);
        }

        .workflow-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
            margin: 2rem 0;
        }

        .workflow-card {
            background: rgba(0, 212, 255, 0.05);
            border-left: 4px solid var(--terminal-secondary);
            padding: 1.5rem;
            position: relative;
            transition: all 0.3s ease;
        }

        .workflow-card:hover {
            background: rgba(0, 212, 255, 0.1);
            transform: translateX(10px);
            box-shadow: -5px 0 20px rgba(0, 212, 255, 0.3);
        }

        .workflow-number {
            font-family: var(--font-display);
            font-size: 3rem;
            color: var(--terminal-secondary);
            opacity: 0.2;
            position: absolute;
            top: 0.5rem;
            right: 0.5rem;
        }

        .workflow-title {
            font-size: 1.1rem;
            font-weight: 600;
            color: var(--terminal-secondary);
            margin-bottom: 0.8rem;
            text-transform: uppercase;
            letter-spacing: 0.05em;
        }

        .workflow-desc {
            font-size: 0.95rem;
            color: var(--terminal-text);
            line-height: 1.6;
        }

        /* ============================================
           PROJECTS SECTION
           ============================================ */
        .filter-bar {
            display: flex;
            gap: 1rem;
            flex-wrap: wrap;
            margin: 2rem 0;
            padding: 1rem;
            background: rgba(255, 255, 255, 0.02);
            border: 1px solid var(--terminal-muted);
        }

        .filter-btn {
            padding: 0.6rem 1.2rem;
            font-family: var(--font-mono);
            font-size: 0.8rem;
            font-weight: 500;
            text-transform: uppercase;
            background: transparent;
            color: var(--terminal-dim);
            border: 1px solid var(--terminal-dim);
            cursor: pointer;
            transition: all 0.2s ease;
        }

        .filter-btn:hover,
        .filter-btn.active {
            background: var(--terminal-primary);
            color: var(--terminal-bg);
            border-color: var(--terminal-primary);
            box-shadow: 0 0 15px var(--terminal-primary);
        }

        .projects-grid {
            display: grid;
            gap: 2rem;
        }

        .project-card {
            background: rgba(255, 255, 255, 0.02);
            border: 1px solid var(--terminal-muted);
            padding: 2rem;
            position: relative;
            transition: all 0.3s ease;
            opacity: 0;
            transform: translateY(20px);
            animation: projectSlideIn 0.5s ease-out forwards;
        }

        .project-card:nth-child(1) { animation-delay: 0.1s; }
        .project-card:nth-child(2) { animation-delay: 0.2s; }
        .project-card:nth-child(3) { animation-delay: 0.3s; }

        @keyframes projectSlideIn {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .project-card.hidden {
            display: none;
        }

        .project-card:hover {
            border-color: var(--terminal-accent);
            box-shadow: 0 10px 40px rgba(255, 42, 109, 0.2);
            transform: scale(1.02);
        }

        .project-header {
            display: flex;
            justify-content: space-between;
            align-items: start;
            margin-bottom: 1rem;
        }

        .project-title {
            font-family: var(--font-display);
            font-size: 1.5rem;
            color: var(--terminal-accent);
            text-transform: uppercase;
            margin-bottom: 0.5rem;
        }

        .project-status {
            font-size: 0.7rem;
            padding: 0.3rem 0.8rem;
            background: var(--terminal-primary);
            color: var(--terminal-bg);
            text-transform: uppercase;
            font-weight: 600;
            letter-spacing: 0.05em;
        }

        .project-status.wip {
            background: var(--terminal-warning);
        }

        .project-tags {
            display: flex;
            gap: 0.5rem;
            flex-wrap: wrap;
            margin: 1rem 0;
        }

        .project-tag {
            font-size: 0.7rem;
            padding: 0.3rem 0.8rem;
            background: rgba(0, 212, 255, 0.1);
            color: var(--terminal-secondary);
            border: 1px solid var(--terminal-secondary);
            text-transform: uppercase;
            font-weight: 500;
        }

        .project-desc {
            color: var(--terminal-text);
            line-height: 1.8;
            margin: 1rem 0;
        }

        .project-links {
            display: flex;
            gap: 1rem;
            margin-top: 1.5rem;
        }

        .project-link {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            font-size: 0.85rem;
            font-weight: 600;
            color: var(--terminal-primary);
            text-decoration: none;
            text-transform: uppercase;
            transition: all 0.2s ease;
        }

        .project-link:hover {
            color: var(--terminal-accent);
            text-shadow: 0 0 10px var(--terminal-accent);
            transform: translateX(5px);
        }

        /* ============================================
           CONTACT SECTION
           ============================================ */
        .contact-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.5rem;
            margin: 2rem 0;
        }

        .contact-card {
            background: rgba(255, 42, 109, 0.05);
            border: 1px solid var(--terminal-accent);
            padding: 1.5rem;
            text-align: center;
            transition: all 0.3s ease;
        }

        .contact-card:hover {
            background: rgba(255, 42, 109, 0.1);
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(255, 42, 109, 0.3);
        }

        .contact-icon {
            font-size: 2rem;
            margin-bottom: 1rem;
        }

        .contact-label {
            font-size: 0.8rem;
            color: var(--terminal-dim);
            text-transform: uppercase;
            margin-bottom: 0.5rem;
        }

        .contact-value {
            color: var(--terminal-accent);
            font-weight: 600;
            word-break: break-all;
        }

        /* ============================================
           FOOTER
           ============================================ */
        footer {
            margin-top: 4rem;
            padding: 2rem 0;
            border-top: 1px solid var(--terminal-muted);
            text-align: center;
            color: var(--terminal-dim);
            font-size: 0.85rem;
        }

        .footer-ascii {
            font-size: 0.6rem;
            color: var(--terminal-primary);
            opacity: 0.3;
            margin-bottom: 1rem;
            line-height: 1;
        }

        /* ============================================
           RESPONSIVE
           ============================================ */
        @media (max-width: 768px) {
            .container {
                padding: 1rem;
            }

            h1 {
                font-size: 2rem;
            }

            .terminal-body {
                padding: 1.5rem;
            }

            .stats-grid,
            .workflow-grid,
            .contact-grid {
                grid-template-columns: 1fr;
            }

            .action-bar {
                flex-direction: column;
            }

            .btn {
                width: 100%;
                justify-content: center;
            }

            .filter-bar {
                justify-content: center;
            }

            .boot-overlay {
                padding: 1rem 5%;
                font-size: 0.75rem;
            }
        }

        /* ============================================
           CUSTOM CURSOR (OPTIONAL)
           ============================================ */
        .custom-cursor {
            width: 20px;
            height: 20px;
            border: 2px solid var(--terminal-primary);
            border-radius: 50%;
            position: fixed;
            pointer-events: none;
            z-index: 9998;
            transition: transform 0.15s ease, border-color 0.15s ease;
            mix-blend-mode: difference;
        }

        .custom-cursor.hover {
            transform: scale(1.5);
            border-color: var(--terminal-accent);
        }
    </style>
</head>
<body>
    <!-- Boot Sequence Overlay -->
    <div class="boot-overlay">
        <div class="boot-line">INITIALIZING PORTFOLIO SYSTEM v2.5.1...</div>
        <div class="boot-line">LOADING CORE MODULES........................[OK]</div>
        <div class="boot-line">ESTABLISHING SECURE CONNECTION..............[OK]</div>
        <div class="boot-line warning">WARNING: CREATIVITY LEVELS EXCEEDING NORMAL PARAMETERS</div>
        <div class="boot-line">COMPILING PROJECT DATABASE..................[OK]</div>
        <div class="boot-line">INITIALIZING UI COMPONENTS..................[OK]</div>
        <div class="boot-line">AUTHENTICATING USER: GUEST..................[OK]</div>
        <div class="boot-line">SYSTEM READY. WELCOME TO THE MATRIX.</div>
    </div>

    <!-- Animated Grid Background -->
    <div class="grid-background"></div>

    <!-- Code Rain Effect -->
    <div class="code-rain" id="codeRain"></div>

    <!-- Custom Cursor -->
    <div class="custom-cursor" id="customCursor"></div>

    <!-- Main Content -->
    <div class="container">
        <!-- Hero Terminal Window -->
        <div class="terminal-window">
            <div class="terminal-header">
                <div class="terminal-buttons">
                    <div class="terminal-button close"></div>
                    <div class="terminal-button minimize"></div>
                    <div class="terminal-button maximize"></div>
                </div>
                <div class="terminal-title">jordan@dudgeon:~$ ./portfolio.sh --execute</div>
            </div>
            <div class="terminal-body">
                <div class="hero">
                    <div class="glitch-wrapper" data-text="JORDAN DUDGEON">
                        <h1>JORDAN DUDGEON</h1>
                    </div>
                    <div class="status-line">STATUS: TRANSFORMING COMPLEXITY</div>
                    <div class="status-line">ROLE: DEVELOPER // SYSTEM ARCHITECT</div>
                    
                    <div class="typing-text">
                        <strong>// MISSION STATEMENT</strong><br>
                        Building intuitive, high-performance systems that transform complex technical 
                        challenges into elegant solutions. Specializing in API integration, real-time data 
                        visualization, and seamless user experiences that just work.
                    </div>

                    <div class="action-bar">
                        <a href="https://www.linkedin.com/in/jordan-dudgeon" target="_blank" rel="noopener" class="btn">
                            <span>📡</span> LINKEDIN
                        </a>
                        <a href="mailto:jdudgeon1993@gmail.com" class="btn secondary">
                            <span>📨</span> INITIATE CONTACT
                        </a>
                        <a href="https://github.com/jdudgeon1993" target="_blank" rel="noopener" class="btn">
                            <span>💾</span> GITHUB
                        </a>
                    </div>
                </div>

                <!-- System Stats -->
                <div class="stats-grid">
                    <div class="stat-card">
                        <div class="stat-label">Lighthouse Score</div>
                        <div class="stat-value">100<span class="stat-unit">/100</span></div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-label">Performance</div>
                        <div class="stat-value">OPTIMAL</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-label">APIs Integrated</div>
                        <div class="stat-value">15<span class="stat-unit">+</span></div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-label">System Uptime</div>
                        <div class="stat-value">99.9<span class="stat-unit">%</span></div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Workflow Section -->
        <div class="terminal-window">
            <div class="terminal-header">
                <div class="terminal-buttons">
                    <div class="terminal-button close"></div>
                    <div class="terminal-button minimize"></div>
                    <div class="terminal-button maximize"></div>
                </div>
                <div class="terminal-title">workflow_system.log</div>
            </div>
            <div class="terminal-body">
                <h2 class="section-title">// TRANSFORMATION PROTOCOL</h2>
                <p style="color: var(--terminal-dim); margin-bottom: 2rem;">
                    Four-phase methodology for converting chaos into clarity
                </p>

                <div class="workflow-grid">
                    <div class="workflow-card">
                        <div class="workflow-number">01</div>
                        <div class="workflow-title">🧠 ANALYSIS & MAPPING</div>
                        <div class="workflow-desc">
                            Deep-dive into requirements. Map complexity. Identify bottlenecks. 
                            Blueprint the optimal architecture before writing a single line.
                        </div>
                    </div>

                    <div class="workflow-card">
                        <div class="workflow-number">02</div>
                        <div class="workflow-title">💻 DEVELOPMENT & TESTING</div>
                        <div class="workflow-desc">
                            Build semantic, maintainable code. Implement real-time features. 
                            Conduct rigorous testing across devices and use cases.
                        </div>
                    </div>

                    <div class="workflow-card">
                        <div class="workflow-number">03</div>
                        <div class="workflow-title">🚀 DEPLOYMENT & SCALING</div>
                        <div class="workflow-desc">
                            Optimize assets for speed. Deploy with CI/CD pipelines. 
                            Ensure infrastructure scales effortlessly under load.
                        </div>
                    </div>

                    <div class="workflow-card">
                        <div class="workflow-number">04</div>
                        <div class="workflow-title">📊 MONITOR & ITERATE</div>
                        <div class="workflow-desc">
                            Track performance metrics. Gather user feedback. 
                            Continuously refine and optimize for peak efficiency.
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Projects Section -->
        <div class="terminal-window">
            <div class="terminal-header">
                <div class="terminal-buttons">
                    <div class="terminal-button close"></div>
                    <div class="terminal-button minimize"></div>
                    <div class="terminal-button maximize"></div>
                </div>
                <div class="terminal-title">projects_database.db</div>
            </div>
            <div class="terminal-body">
                <h2 class="section-title">// DEPLOYED SYSTEMS</h2>

                <div class="filter-bar">
                    <button class="filter-btn active" data-filter="all">ALL</button>
                    <button class="filter-btn" data-filter="webdev">WEB DEV</button>
                    <button class="filter-btn" data-filter="integration">INTEGRATION</button>
                    <button class="filter-btn" data-filter="analysis">ANALYSIS</button>
                    <button class="filter-btn" data-filter="realtime">REAL-TIME</button>
                </div>

                <div class="projects-grid">
                    <!-- Project 1: Commute Dashboard -->
                    <div class="project-card" data-categories="webdev integration realtime">
                        <div class="project-header">
                            <div>
                                <div class="project-title">REAL-TIME COMMUTE DASHBOARD</div>
                                <div class="project-tags">
                                    <span class="project-tag">HTML/CSS/JS</span>
                                    <span class="project-tag">API INTEGRATION</span>
                                    <span class="project-tag">GTFS</span>
                                    <span class="project-tag">REAL-TIME DATA</span>
                                </div>
                            </div>
                            <span class="project-status">LIVE</span>
                        </div>
                        <div class="project-desc">
                            Comprehensive single-page application integrating multiple live APIs 
                            (OpenWeather, Google Routes, custom RTD GTFS server). Features dynamic 
                            time-based modes, focus mode, color-coded transit alerts, and live countdown 
                            timers. Built custom GTFS server hosted on Render for N Line train schedules.
                        </div>
                        <div class="project-links">
                            <a href="#" class="project-link">VIEW DEMO →</a>
                            <a href="#" class="project-link">SOURCE CODE →</a>
                        </div>
                    </div>

                    <!-- Project 2: Portfolio -->
                    <div class="project-card" data-categories="webdev">
                        <div class="project-header">
                            <div>
                                <div class="project-title">TERMINAL PORTFOLIO v2.5</div>
                                <div class="project-tags">
                                    <span class="project-tag">HTML/CSS</span>
                                    <span class="project-tag">ANIMATIONS</span>
                                    <span class="project-tag">UX DESIGN</span>
                                </div>
                            </div>
                            <span class="project-status">LIVE</span>
                        </div>
                        <div class="project-desc">
                            Cyberpunk-inspired portfolio with CRT scanlines, glitch effects, animated 
                            boot sequences, and interactive elements. Built with vanilla HTML/CSS/JS 
                            for maximum performance. Demonstrates creative frontend capabilities while 
                            maintaining accessibility standards.
                        </div>
                        <div class="project-links">
                            <a href="https://jdudgeon1993.github.io/jdudgeon1993/" class="project-link">VIEW LIVE →</a>
                            <a href="https://github.com/jdudgeon1993/jdudgeon1993" class="project-link">SOURCE CODE →</a>
                        </div>
                    </div>

                    <!-- Project 3: Client Work -->
                    <div class="project-card" data-categories="webdev analysis integration">
                        <div class="project-header">
                            <div>
                                <div class="project-title">WORKFLOW OPTIMIZATION SYSTEM</div>
                                <div class="project-tags">
                                    <span class="project-tag">BUSINESS ANALYSIS</span>
                                    <span class="project-tag">SYSTEM DESIGN</span>
                                    <span class="project-tag">CLIENT WORK</span>
                                </div>
                            </div>
                            <span class="project-status">DEPLOYED</span>
                        </div>
                        <div class="project-desc">
                            Deep workflow analysis to reduce departmental friction. Delivered 
                            high-speed, minimalist website maximizing client lead conversion. 
                            Comprehensive documentation and strategic recommendations implemented.
                        </div>
                        <div class="project-links">
                            <a href="https://github.com/jdudgeon1993/Projects/blob/28454ac426544536ed555853b532563bf96f52a3/Heathers%20Project" class="project-link">ANALYSIS REPORT →</a>
                            <a href="https://jdudgeon1993.github.io/Project_HR_Portfolio/#" class="project-link">WEBSITE DEMO →</a>
                        </div>
                    </div>

                    <!-- Project 4: In Development -->
                    <div class="project-card" data-categories="webdev integration">
                        <div class="project-header">
                            <div>
                                <div class="project-title">CLASSIFIED PROJECT_ALPHA</div>
                                <div class="project-tags">
                                    <span class="project-tag">FULL-STACK</span>
                                    <span class="project-tag">DATABASE</span>
                                    <span class="project-tag">REST API</span>
                                </div>
                            </div>
                            <span class="project-status wip">IN DEV</span>
                        </div>
                        <div class="project-desc">
                            Full-stack application demonstrating technical efficiency and superior 
                            workflow design. Features include real-time data synchronization, 
                            advanced state management, and optimized database queries.
                        </div>
                        <div class="project-links">
                            <span style="color: var(--terminal-dim);">// COMING_SOON.exe</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Contact Section -->
        <div class="terminal-window">
            <div class="terminal-header">
                <div class="terminal-buttons">
                    <div class="terminal-button close"></div>
                    <div class="terminal-button minimize"></div>
                    <div class="terminal-button maximize"></div>
                </div>
                <div class="terminal-title">contact_channels.cfg</div>
            </div>
            <div class="terminal-body">
                <h2 class="section-title">// INITIATE CONNECTION</h2>
                <p style="color: var(--terminal-dim); margin-bottom: 2rem;">
                    Multiple communication protocols available
                </p>

                <div class="contact-grid">
                    <div class="contact-card">
                        <div class="contact-icon">📧</div>
                        <div class="contact-label">Email Protocol</div>
                        <a href="mailto:jdudgeon1993@gmail.com" class="contact-value">
                            jdudgeon1993@gmail.com
                        </a>
                    </div>

                    <div class="contact-card">
                        <div class="contact-icon">🔗</div>
                        <div class="contact-label">LinkedIn Network</div>
                        <a href="https://www.linkedin.com/in/jordan-dudgeon" target="_blank" rel="noopener" class="contact-value">
                            /jordan-dudgeon
                        </a>
                    </div>

                    <div class="contact-card">
                        <div class="contact-icon">💾</div>
                        <div class="contact-label">GitHub Repository</div>
                        <a href="https://github.com/jdudgeon1993" target="_blank" rel="noopener" class="contact-value">
                            /jdudgeon1993
                        </a>
                    </div>

                    <div class="contact-card">
                        <div class="contact-icon">📍</div>
                        <div class="contact-label">Location</div>
                        <div class="contact-value">Denver Metro, CO</div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Footer -->
        <footer>
            <pre class="footer-ascii">
 ██╗ ██████╗ ██████╗ ██████╗  █████╗ ███╗   ██╗
 ██║██╔═══██╗██╔══██╗██╔══██╗██╔══██╗████╗  ██║
 ██║██║   ██║██████╔╝██║  ██║███████║██╔██╗ ██║
██╔╝██║   ██║██╔══██╗██║  ██║██╔══██║██║╚██╗██║
██║ ╚██████╔╝██║  ██║██████╔╝██║  ██║██║ ╚████║
╚═╝  ╚═════╝ ╚═╝  ╚═╝╚═════╝ ╚═╝  ╚═╝╚═╝  ╚═══╝
            </pre>
            <p>&copy; 2025 JORDAN DUDGEON // ALL SYSTEMS OPERATIONAL</p>
            <p style="margin-top: 0.5rem; font-size: 0.75rem;">
                BUILT WITH: HTML + CSS + JS // NO FRAMEWORKS // MAXIMUM PERFORMANCE
            </p>
        </footer>
    </div>

    <script>
        // ============================================
        // CODE RAIN EFFECT
        // ============================================
        const codeRain = document.getElementById('codeRain');
        const codeChars = '01アイウエオカキクケコサシスセソタチツテトナニヌネノハヒフヘホマミムメモヤユヨラリルレロワヲン';
        
        function createRainDrop() {
            const span = document.createElement('span');
            const char = codeChars[Math.floor(Math.random() * codeChars.length)];
            span.textContent = char;
            span.style.left = Math.random() * 100 + '%';
            span.style.animationDuration = (Math.random() * 3 + 2) + 's';
            span.style.animationDelay = Math.random() * 2 + 's';
            codeRain.appendChild(span);
            
            setTimeout(() => span.remove(), 5000);
        }

        // Create initial raindrops
        for (let i = 0; i < 30; i++) {
            setTimeout(createRainDrop, Math.random() * 2000);
        }

        // Continuously create new raindrops
        setInterval(createRainDrop, 300);

        // ============================================
        // CUSTOM CURSOR
        // ============================================
        const cursor = document.getElementById('customCursor');
        let mouseX = 0, mouseY = 0;
        let cursorX = 0, cursorY = 0;

        document.addEventListener('mousemove', (e) => {
            mouseX = e.clientX;
            mouseY = e.clientY;
        });

        function animateCursor() {
            const speed = 0.2;
            cursorX += (mouseX - cursorX) * speed;
            cursorY += (mouseY - cursorY) * speed;
            
            cursor.style.left = cursorX + 'px';
            cursor.style.top = cursorY + 'px';
            
            requestAnimationFrame(animateCursor);
        }
        animateCursor();

        // Cursor hover effect
        document.querySelectorAll('a, button, .project-card, .stat-card, .workflow-card').forEach(el => {
            el.addEventListener('mouseenter', () => cursor.classList.add('hover'));
            el.addEventListener('mouseleave', () => cursor.classList.remove('hover'));
        });

        // ============================================
        // PROJECT FILTERING
        // ============================================
        const filterBtns = document.querySelectorAll('.filter-btn');
        const projectCards = document.querySelectorAll('.project-card');

        filterBtns.forEach(btn => {
            btn.addEventListener('click', () => {
                const filter = btn.dataset.filter;
                
                // Update active button
                filterBtns.forEach(b => b.classList.remove('active'));
                btn.classList.add('active');
                
                // Filter projects
                projectCards.forEach(card => {
                    if (filter === 'all') {
                        card.classList.remove('hidden');
                    } else {
                        const categories = card.dataset.categories.split(' ');
                        if (categories.includes(filter)) {
                            card.classList.remove('hidden');
                        } else {
                            card.classList.add('hidden');
                        }
                    }
                });
            });
        });

        // ============================================
        // THEME PERSISTENCE
        // ============================================
        const savedTheme = localStorage.getItem('portfolio-theme');
        if (savedTheme) {
            document.body.setAttribute('data-theme', savedTheme);
        }

        // ============================================
        // SMOOTH SCROLL
        // ============================================
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({ behavior: 'smooth' });
                }
            });
        });

        // ============================================
        // KONAMI CODE EASTER EGG
        // ============================================
        let konamiCode = ['ArrowUp', 'ArrowUp', 'ArrowDown', 'ArrowDown', 'ArrowLeft', 'ArrowRight', 'ArrowLeft', 'ArrowRight', 'b', 'a'];
        let konamiIndex = 0;

        document.addEventListener('keydown', (e) => {
            if (e.key === konamiCode[konamiIndex]) {
                konamiIndex++;
                if (konamiIndex === konamiCode.length) {
                    activateMatrixMode();
                    konamiIndex = 0;
                }
            } else {
                konamiIndex = 0;
            }
        });

        function activateMatrixMode() {
            document.body.style.animation = 'glitchFlicker 0.1s infinite';
            setTimeout(() => {
                document.body.style.animation = '';
                alert('🎮 CHEAT CODE ACTIVATED // SYSTEM OVERCLOCKED TO 200%');
            }, 2000);
        }

        // ============================================
        // PERFORMANCE MONITORING
        // ============================================
        window.addEventListener('load', () => {
            if (window.performance) {
                const loadTime = window.performance.timing.domContentLoadedEventEnd - window.performance.timing.navigationStart;
                console.log(`%c⚡ PAGE LOADED IN ${loadTime}ms`, 'color: #00ff41; font-size: 16px; font-weight: bold;');
                console.log('%c🚀 SYSTEM PERFORMANCE: OPTIMAL', 'color: #00d4ff; font-size: 14px;');
                console.log('%c💾 REPOSITORY: https://github.com/jdudgeon1993', 'color: #ff2a6d; font-size: 14px;');
            }
        });
    </script>
</body>
</html>
