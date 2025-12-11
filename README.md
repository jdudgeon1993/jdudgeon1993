<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Jordan Dudgeon - Full-stack developer specializing in intuitive UI/UX, system integration, and high-performance web applications.">
    <meta name="author" content="Jordan Dudgeon">
    <meta name="keywords" content="web developer, UI/UX, system integration, portfolio, Denver developer">
    
    <!-- Open Graph / Social Media -->
    <meta property="og:title" content="Jordan Dudgeon - Portfolio">
    <meta property="og:description" content="Designing seamless experiences. Transforming complexity into elegant solutions.">
    <meta property="og:type" content="website">
    
    <!-- Preconnect to fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Crimson+Pro:ital,wght@0,400;0,600;1,400&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
    
    <title>Jordan Dudgeon – Portfolio</title>
    
    <style>
        /* =====================================================
           CSS CUSTOM PROPERTIES & THEME SYSTEM
           ===================================================== */
        :root {
            /* Typography */
            --font-display: 'Space Mono', monospace;
            --font-body: 'Crimson Pro', Georgia, serif;
            
            /* Spacing & Layout */
            --container-width: 800px;
            --spacing-xs: 0.5rem;
            --spacing-sm: 1rem;
            --spacing-md: 1.5rem;
            --spacing-lg: 2.5rem;
            --spacing-xl: 4rem;
            
            /* Timing */
            --transition-fast: 150ms;
            --transition-base: 250ms;
            --transition-slow: 400ms;
            
            /* Borders & Shadows */
            --radius-sm: 3px;
            --shadow-sm: 0 2px 8px rgba(0, 0, 0, 0.1);
            --shadow-md: 0 4px 16px rgba(0, 0, 0, 0.15);
        }

        /* =====================================================
           THEME VARIATIONS
           ===================================================== */
        
        /* Classic Journal (Default Light) */
        body[data-theme='journal'] {
            --bg-primary: #fcf8e8;
            --bg-secondary: #ffffff;
            --text-primary: #2d2416;
            --text-secondary: #5a4d3a;
            --accent-primary: #c84545;
            --accent-secondary: #3d5467;
            --border-color: #e0d9c6;
            --tag-bg: #f5f0e1;
        }

        /* Deep Sea (Dark Cool) */
        body[data-theme='deep-sea'] {
            --bg-primary: #0f1419;
            --bg-secondary: #1a2332;
            --text-primary: #e0f7fa;
            --text-secondary: #b0c4d4;
            --accent-primary: #26a69a;
            --accent-secondary: #ffb74d;
            --border-color: #2a3f52;
            --tag-bg: #1e2d3f;
        }

        /* Midnight Crimson (Dark Warm) */
        body[data-theme='crimson'] {
            --bg-primary: #0d0405;
            --bg-secondary: #1a0808;
            --text-primary: #fce4ec;
            --text-secondary: #d4b4be;
            --accent-primary: #e57373;
            --accent-secondary: #ffd54f;
            --border-color: #3a1515;
            --tag-bg: #251010;
        }

        /* Minimal Blue (Light Professional) */
        body[data-theme='minimal'] {
            --bg-primary: #f8f9fa;
            --bg-secondary: #ffffff;
            --text-primary: #212529;
            --text-secondary: #495057;
            --accent-primary: #0066cc;
            --accent-secondary: #004494;
            --border-color: #dee2e6;
            --tag-bg: #f1f3f5;
        }

        /* High Contrast (Accessibility) */
        body[data-theme='contrast'] {
            --bg-primary: #000000;
            --bg-secondary: #0a0a0a;
            --text-primary: #ffffff;
            --text-secondary: #e0e0e0;
            --accent-primary: #00ffff;
            --accent-secondary: #ff00ff;
            --border-color: #333333;
            --tag-bg: #1a1a1a;
        }

        /* =====================================================
           BASE STYLES & RESET
           ===================================================== */
        *, *::before, *::after {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            font-family: var(--font-body);
            font-size: 1.125rem;
            line-height: 1.7;
            color: var(--text-primary);
            background-color: var(--bg-primary);
            transition: background-color var(--transition-slow), 
                        color var(--transition-slow);
            padding-bottom: 80px;
        }

        ::selection {
            background: var(--accent-primary);
            color: var(--bg-primary);
        }

        /* Skip to main content link for accessibility */
        .skip-link {
            position: absolute;
            top: -40px;
            left: 0;
            background: var(--accent-primary);
            color: var(--bg-primary);
            padding: 8px 16px;
            text-decoration: none;
            font-weight: 700;
            z-index: 100;
        }
        .skip-link:focus {
            top: 0;
        }

        /* =====================================================
           LAYOUT
           ===================================================== */
        .container {
            width: min(90%, var(--container-width));
            margin: 0 auto;
            padding: var(--spacing-lg) 0;
        }

        /* =====================================================
           TYPOGRAPHY
           ===================================================== */
        h1, h2, h3, h4 {
            font-family: var(--font-display);
            font-weight: 700;
            line-height: 1.2;
        }

        h1 {
            font-size: clamp(2rem, 5vw, 3.5rem);
            color: var(--accent-primary);
            text-transform: uppercase;
            letter-spacing: 0.05em;
            margin-bottom: var(--spacing-sm);
        }

        h2 {
            font-size: clamp(1rem, 3vw, 1.25rem);
            color: var(--accent-secondary);
            font-weight: 400;
            letter-spacing: 0.08em;
            text-transform: uppercase;
        }

        h3 {
            font-size: clamp(1.5rem, 3vw, 2rem);
            color: var(--accent-secondary);
            margin-bottom: var(--spacing-md);
        }

        h4 {
            font-size: 1.25rem;
            color: var(--accent-primary);
            margin-bottom: var(--spacing-xs);
        }

        p {
            margin-bottom: var(--spacing-sm);
            color: var(--text-secondary);
        }

        /* =====================================================
           COMPONENTS
           ===================================================== */
        
        /* Links */
        a {
            color: var(--accent-primary);
            text-decoration: none;
            border-bottom: 1px solid transparent;
            transition: border-color var(--transition-fast);
        }
        a:hover, a:focus {
            border-bottom-color: var(--accent-primary);
        }
        a:focus {
            outline: 2px solid var(--accent-primary);
            outline-offset: 3px;
        }

        /* Buttons */
        .btn {
            display: inline-block;
            padding: 0.75rem 1.5rem;
            font-family: var(--font-display);
            font-size: 0.875rem;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 0.05em;
            color: var(--bg-primary);
            background: var(--accent-secondary);
            border: none;
            border-radius: var(--radius-sm);
            cursor: pointer;
            transition: transform var(--transition-fast),
                        box-shadow var(--transition-fast);
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
        }
        .btn:hover, .btn:focus {
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
            border-bottom-color: transparent;
        }
        .btn:active {
            transform: translateY(0);
        }

        /* Cards */
        .card {
            background: var(--bg-secondary);
            border: 1px solid var(--border-color);
            border-radius: var(--radius-sm);
            padding: var(--spacing-lg);
            box-shadow: var(--shadow-sm);
            transition: border-color var(--transition-base);
        }

        /* Divider */
        .divider {
            height: 1px;
            background: linear-gradient(
                to right,
                transparent,
                var(--border-color) 20%,
                var(--border-color) 80%,
                transparent
            );
            margin: var(--spacing-xl) 0;
            border: none;
        }

        /* Tags */
        .tag {
            display: inline-block;
            padding: 0.25rem 0.75rem;
            font-size: 0.75rem;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.05em;
            background: var(--tag-bg);
            color: var(--text-secondary);
            border: 1px solid var(--border-color);
            border-radius: var(--radius-sm);
            margin: 0.25rem 0.25rem 0.25rem 0;
        }
        .tag.active {
            background: var(--accent-primary);
            color: var(--bg-primary);
            border-color: var(--accent-primary);
        }

        /* =====================================================
           HEADER
           ===================================================== */
        header {
            text-align: center;
            padding: var(--spacing-xl) 0 var(--spacing-lg);
            border-bottom: 2px solid var(--accent-primary);
            position: relative;
        }

        .hero-statement {
            max-width: 650px;
            margin: var(--spacing-lg) auto;
            padding: var(--spacing-lg);
            background: var(--bg-secondary);
            border: 2px solid var(--accent-primary);
            border-radius: var(--radius-sm);
            box-shadow: var(--shadow-md);
        }

        .hero-statement h2 {
            margin-bottom: var(--spacing-sm);
        }

        .hero-statement p {
            font-size: 1.125rem;
            font-weight: 600;
            color: var(--text-primary);
            line-height: 1.6;
        }

        .cta-group {
            display: flex;
            gap: var(--spacing-sm);
            justify-content: center;
            flex-wrap: wrap;
            margin-top: var(--spacing-lg);
        }

        /* Theme Switcher */
        .theme-switcher {
            position: absolute;
            top: var(--spacing-sm);
            right: var(--spacing-sm);
            display: flex;
            align-items: center;
            gap: var(--spacing-xs);
            font-size: 0.875rem;
            font-family: var(--font-display);
        }

        .theme-switcher select {
            padding: 0.5rem;
            font-family: var(--font-display);
            font-size: 0.75rem;
            color: var(--text-primary);
            background: var(--bg-secondary);
            border: 1px solid var(--border-color);
            border-radius: var(--radius-sm);
            cursor: pointer;
        }

        /* =====================================================
           SECTIONS
           ===================================================== */
        section {
            margin-bottom: var(--spacing-xl);
        }

        .workflow-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: var(--spacing-lg);
            margin-top: var(--spacing-lg);
        }

        .workflow-step {
            padding-left: var(--spacing-md);
            border-left: 3px solid var(--accent-primary);
        }

        .workflow-step strong {
            display: block;
            font-family: var(--font-display);
            color: var(--accent-primary);
            font-size: 0.9rem;
            margin-bottom: var(--spacing-xs);
        }

        .workflow-step p {
            font-size: 0.95rem;
        }

        /* Project Filter */
        .filter-container {
            display: flex;
            flex-wrap: wrap;
            gap: var(--spacing-xs);
            margin-bottom: var(--spacing-lg);
        }

        .filter-container label {
            cursor: pointer;
            transition: transform var(--transition-fast);
        }
        .filter-container label:hover {
            transform: scale(1.05);
        }

        .filter-input {
            display: none;
        }

        /* Project Items */
        .project-item {
            display: none;
            padding: var(--spacing-lg) 0;
            border-bottom: 1px dashed var(--border-color);
            transition: padding-left var(--transition-base);
        }
        .project-item:last-child {
            border-bottom: none;
        }
        .project-item.show {
            display: block;
        }
        .project-item:hover {
            padding-left: var(--spacing-md);
            border-left: 3px solid var(--accent-primary);
        }

        .project-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
            margin: var(--spacing-sm) 0;
        }

        .project-tag {
            background: var(--accent-secondary);
            color: var(--bg-primary);
            padding: 0.25rem 0.625rem;
            font-size: 0.7rem;
            font-weight: 700;
            text-transform: uppercase;
            border-radius: var(--radius-sm);
        }

        .project-links {
            margin-top: var(--spacing-sm);
        }
        .project-links a {
            font-weight: 600;
            margin-right: var(--spacing-md);
        }

        /* =====================================================
           METRICS TOGGLE
           ===================================================== */
        .metrics-container {
            position: fixed;
            bottom: 100px;
            right: 20px;
            z-index: 100;
        }

        .metrics-toggle {
            display: none;
        }

        .metrics-btn {
            padding: 0.75rem 1rem;
            font-family: var(--font-display);
            font-size: 0.75rem;
            font-weight: 700;
            text-transform: uppercase;
            background: var(--accent-primary);
            color: var(--bg-primary);
            border: none;
            border-radius: var(--radius-sm);
            cursor: pointer;
            box-shadow: var(--shadow-md);
            transition: transform var(--transition-fast);
        }
        .metrics-btn:hover {
            transform: scale(1.05);
        }

        .metrics-panel {
            display: none;
            position: absolute;
            bottom: calc(100% + 10px);
            right: 0;
            padding: var(--spacing-md);
            background: var(--bg-secondary);
            border: 1px solid var(--border-color);
            border-radius: var(--radius-sm);
            box-shadow: var(--shadow-md);
            min-width: 200px;
        }

        .metrics-toggle:checked ~ .metrics-panel {
            display: block;
            animation: slideUp 0.3s ease-out;
        }

        @keyframes slideUp {
            from {
                opacity: 0;
                transform: translateY(10px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .metric-badge {
            display: block;
            padding: 0.5rem 0.75rem;
            margin: 0.25rem 0;
            font-size: 0.75rem;
            font-weight: 700;
            text-align: center;
            color: white;
            border-radius: var(--radius-sm);
        }
        .metric-badge.green { background: #00c853; }
        .metric-badge.yellow { background: #ffab00; }

        /* =====================================================
           FOOTER
           ===================================================== */
        footer {
            position: fixed;
            bottom: 0;
            left: 0;
            width: 100%;
            padding: var(--spacing-md) 0;
            background: var(--bg-secondary);
            border-top: 1px solid var(--border-color);
            text-align: center;
            font-size: 0.875rem;
            z-index: 50;
        }

        footer p {
            margin-bottom: 0.5rem;
            color: var(--text-secondary);
        }

        .footer-links {
            display: flex;
            justify-content: center;
            gap: var(--spacing-md);
            flex-wrap: wrap;
        }

        /* =====================================================
           RESPONSIVE DESIGN
           ===================================================== */
        @media (max-width: 768px) {
            body {
                font-size: 1rem;
                padding-bottom: 60px;
            }

            .container {
                padding: var(--spacing-md) 0;
            }

            header {
                padding: var(--spacing-lg) 0;
            }

            .theme-switcher {
                position: static;
                justify-content: center;
                margin-bottom: var(--spacing-md);
            }

            .hero-statement {
                padding: var(--spacing-md);
            }

            .cta-group {
                flex-direction: column;
                align-items: stretch;
            }

            .btn {
                width: 100%;
                text-align: center;
            }

            .workflow-grid {
                grid-template-columns: 1fr;
                gap: var(--spacing-md);
            }

            .filter-container {
                justify-content: center;
            }

            .metrics-container {
                position: static;
                margin: var(--spacing-lg) auto;
                display: flex;
                flex-direction: column;
                align-items: center;
                gap: var(--spacing-sm);
            }

            .metrics-panel {
                position: static;
                width: 100%;
                max-width: 300px;
            }

            footer {
                position: static;
            }
        }

        @media (max-width: 480px) {
            h1 {
                letter-spacing: 0.02em;
            }

            h2 {
                letter-spacing: 0.04em;
            }

            .hero-statement p {
                font-size: 1rem;
            }

            .filter-container {
                gap: 0.25rem;
            }

            .tag {
                font-size: 0.65rem;
                padding: 0.25rem 0.5rem;
            }
        }

        /* =====================================================
           PRINT STYLES
           ===================================================== */
        @media print {
            body {
                background: white;
                color: black;
            }

            header, footer, .metrics-container, .theme-switcher, .filter-container {
                display: none;
            }

            .project-item {
                display: block !important;
                page-break-inside: avoid;
            }

            a {
                text-decoration: underline;
            }
        }
    </style>
</head>
<body data-theme="journal">
    <!-- Skip to main content for screen readers -->
    <a href="#main-content" class="skip-link">Skip to main content</a>

    <main class="container" id="main-content">
        <header>
            <div class="theme-switcher">
                <label for="theme-select">Theme:</label>
                <select id="theme-select" aria-label="Choose color theme">
                    <option value="journal">Classic Journal</option>
                    <option value="deep-sea">Deep Sea</option>
                    <option value="crimson">Midnight Crimson</option>
                    <option value="minimal">Minimal Blue</option>
                    <option value="contrast">High Contrast</option>
                </select>
            </div>

            <h1>Jordan Dudgeon</h1>

            <div class="hero-statement">
                <h2>Designing Seamless Experiences.<br>Transforming Complexity.</h2>
                <p>
                    Building intuitive, high-performance systems that transform complex technical 
                    challenges into simple, efficient solutions for users and business operations.
                </p>
            </div>

            <div class="cta-group">
                <a href="https://www.linkedin.com/in/jordan-dudgeon" 
                   target="_blank" 
                   rel="noopener noreferrer" 
                   class="btn"
                   aria-label="Visit Jordan's LinkedIn profile">
                    LinkedIn
                </a>
                <a href="mailto:jdudgeon1993@gmail.com" 
                   class="btn"
                   aria-label="Send email to Jordan">
                    Email Me
                </a>
            </div>
        </header>

        <hr class="divider" aria-hidden="true">

        <section id="workflow" class="card">
            <h3>Transforming Complexity: The Four-Phase Workflow</h3>
            <p>
                A structured approach to building intuitive, high-performance systems that scale effortlessly.
            </p>

            <div class="workflow-grid">
                <div class="workflow-step">
                    <strong>Phase 1: Analysis & Strategy 🧠</strong>
                    <p>Define the problem, map complexity, and blueprint the core, intuitive solution.</p>
                </div>

                <div class="workflow-step">
                    <strong>Phase 2: System Development 💻</strong>
                    <p>Build semantic, high-performance code with rigorous testing for efficiency.</p>
                </div>

                <div class="workflow-step">
                    <strong>Phase 3: Scalable Deployment 📦</strong>
                    <p>Optimize assets and deploy future-proof solutions with robust pipelines.</p>
                </div>

                <div class="workflow-step">
                    <strong>Phase 4: Continuous Optimization 📈</strong>
                    <p>Monitor performance and iterate quickly to maintain peak efficiency.</p>
                </div>
            </div>
        </section>

        <hr class="divider" aria-hidden="true">

        <section id="projects" class="card">
            <h3>Projects & Portfolio</h3>

            <div class="filter-container" role="group" aria-label="Filter projects by category">
                <input type="radio" 
                       id="filter-all" 
                       name="filter" 
                       class="filter-input" 
                       value="all" 
                       checked>
                <label for="filter-all" class="tag active">All Projects</label>

                <input type="radio" 
                       id="filter-webdev" 
                       name="filter" 
                       class="filter-input" 
                       value="webdev">
                <label for="filter-webdev" class="tag">Web Development</label>

                <input type="radio" 
                       id="filter-analysis" 
                       name="filter" 
                       class="filter-input" 
                       value="analysis">
                <label for="filter-analysis" class="tag">Analysis</label>

                <input type="radio" 
                       id="filter-integration" 
                       name="filter" 
                       class="filter-input" 
                       value="integration">
                <label for="filter-integration" class="tag">Integration</label>

                <input type="radio" 
                       id="filter-freelance" 
                       name="filter" 
                       class="filter-input" 
                       value="freelance">
                <label for="filter-freelance" class="tag">Client Work</label>
            </div>

            <div class="project-list">
                <article class="project-item show" data-categories="webdev design">
                    <h4>Dynamic Themed Portfolio</h4>
                    <div class="project-tags">
                        <span class="project-tag">HTML</span>
                        <span class="project-tag">CSS</span>
                        <span class="project-tag">JavaScript</span>
                        <span class="project-tag">Design Systems</span>
                    </div>
                    <p>
                        Live demonstration of scalability. Built with modular CSS themes and 
                        zero-latency UX for future-proof design systems.
                    </p>
                    <div class="project-links">
                        <a href="https://jdudgeon1993.github.io/jdudgeon1993/" 
                           target="_blank" 
                           rel="noopener noreferrer">
                            View Live →
                        </a>
                        <a href="https://github.com/jdudgeon1993/jdudgeon1993" 
                           target="_blank" 
                           rel="noopener noreferrer">
                            Source Code →
                        </a>
                    </div>
                </article>

                <article class="project-item show" data-categories="webdev analysis integration freelance">
                    <h4>Workflow Optimization & Client Website</h4>
                    <div class="project-tags">
                        <span class="project-tag">Business Analysis</span>
                        <span class="project-tag">System Integration</span>
                        <span class="project-tag">Freelance</span>
                        <span class="project-tag">UI/UX</span>
                    </div>
                    <p>
                        Conducted deep workflow analysis to reduce friction, then delivered a 
                        high-speed, minimalist website maximizing client lead conversion.
                    </p>
                    <div class="project-links">
                        <a href="https://github.com/jdudgeon1993/Projects/blob/28454ac426544536ed555853b532563bf96f52a3/Heathers%20Project" 
                           target="_blank" 
                           rel="noopener noreferrer">
                            Analysis Report →
                        </a>
                        <a href="https://jdudgeon1993.github.io/Project_HR_Portfolio/#" 
                           target="_blank" 
                           rel="noopener noreferrer">
                            Website Demo →
                        </a>
                    </div>
                </article>

                <article class="project-item show" data-categories="development">
                    <h4>Full-Stack Application</h4>
                    <div class="project-tags">
                        <span class="project-tag">In Development</span>
                    </div>
                    <p>
                        Currently building a solution demonstrating full-stack technical efficiency 
                        and superior user workflow design.
                    </p>
                    <div class="project-links">
                        <span style="color: var(--text-secondary);">Coming Soon</span>
                    </div>
                </article>
            </div>
        </section>

        <!-- Lighthouse Metrics Toggle -->
        <div class="metrics-container">
            <input type="checkbox" id="metrics-toggle" class="metrics-toggle">
            <label for="metrics-toggle" class="metrics-btn">📊 Metrics</label>
            <div class="metrics-panel">
                <span class="metric-badge green">🚀 100 Performance</span>
                <span class="metric-badge green">♿ 100 Accessibility</span>
                <span class="metric-badge green">✅ 100 Best Practices</span>
                <span class="metric-badge yellow">🔎 91 SEO</span>
            </div>
        </div>
    </main>

    <footer>
        <p>&copy; 2025 Jordan Dudgeon. All Rights Reserved.</p>
        <nav class="footer-links" aria-label="Footer navigation">
            <a href="https://www.linkedin.com/in/jordan-dudgeon" 
               target="_blank" 
               rel="noopener noreferrer">
                LinkedIn
            </a>
            <a href="mailto:jdudgeon1993@gmail.com">
                jdudgeon1993@gmail.com
            </a>
        </nav>
    </footer>

    <script>
        // Theme Management
        const themeSelect = document.getElementById('theme-select');
        const body = document.body;
        const THEME_KEY = 'portfolio-theme';

        // Load saved theme
        const savedTheme = localStorage.getItem(THEME_KEY) || 'journal';
        body.setAttribute('data-theme', savedTheme);
        themeSelect.value = savedTheme;

        // Handle theme changes
        themeSelect.addEventListener('change', (e) => {
            const newTheme = e.target.value;
            body.setAttribute('data-theme', newTheme);
            localStorage.setItem(THEME_KEY, newTheme);
        });

        // Project Filtering
        const filterInputs = document.querySelectorAll('.filter-input');
        const projectItems = document.querySelectorAll('.project-item');
        const filterLabels = document.querySelectorAll('.filter-container label');

        function filterProjects(category) {
            projectItems.forEach(item => {
                if (category === 'all') {
                    item.classList.add('show');
                } else {
                    const categories = item.dataset.categories.split(' ');
                    if (categories.includes(category)) {
                        item.classList.add('show');
                    } else {
                        item.classList.remove('show');
                    }
                }
            });

            // Update active tag styling
            filterLabels.forEach(label => {
                label.classList.remove('active');
            });
            document.querySelector(`label[for="${category === 'all' ? 'filter-all' : 'filter-' + category}"]`).classList.add('active');
        }

        filterInputs.forEach(input => {
            input.addEventListener('change', (e) => {
                filterProjects(e.target.value);
            });
        });

        // Add keyboard navigation for filter tags
        filterLabels.forEach(label => {
            label.setAttribute('tabindex', '0');
            label.addEventListener('keypress', (e) => {
                if (e.key === 'Enter' || e.key === ' ') {
                    e.preventDefault();
                    label.click();
                }
            });
        });
    </script>
</body>
</html>
