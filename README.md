<img width="1187" height="808" alt="image" src="https://github.com/user-attachments/assets/94536992-a251-491e-950e-929d4e77b610" /><!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta name="description"
        content="Jordan Dudgeon: Designing seamless user experiences, transforming complex technical challenges into simple, efficient solutions for both users and business operations.">

    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link
        href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&family=Playfair+Display:ital,wght@0,400;0,700;1,400&display=swap"
        rel="stylesheet">
    <title>Jordan Dudgeon – Portfolio</title>
    <style>
        /* [CSS Variables remain unchanged] */
        :root {
            --font-family-title: 'Playfair Display', serif;
            --font-family-body: 'Georgia', 'Times New Roman', serif;
            --container-max-width: 800px;
        }

        /* 1. CLASSIC JOURNAL (LIGHT/DEFAULT) */
        body[data-theme='journal'] {
            --bg-color: #fcf8e8;
            --text-color: #3e382d;
            --accent-color: #923a3a;
            --secondary-color: #4a5c68;
            --border-color: #e0d9c6;
            --card-bg: #ffffff;
            --button-bg: #4a5c68;
            --button-hover-bg: #3a4b56;
            --tag-bg: #f0f0f0;
            --tag-color: var(--secondary-color);
            --ornamental-line: linear-gradient(to right, var(--accent-color) 0%, var(--border-color) 50%, var(--accent-color) 100%);
        }

        /* 2. DEEP SEA CODER (DARK/COOL) */
        body[data-theme='deep-sea'] {
            --bg-color: #1e2832;
            --text-color: #e0f7fa;
            --accent-color: #26a69a;
            --secondary-color: #ffb74d;
            --border-color: #37474f;
            --card-bg: #263238;
            --button-bg: #26a69a;
            --button-hover-bg: #00897b;
            --tag-bg: #37474f;
            --tag-color: #e0f7fa;
            --ornamental-line: linear-gradient(to right, var(--accent-color) 0%, var(--border-color) 50%, var(--accent-color) 100%);
        }

        /* 3. MIDNIGHT CRIMSON (DARK/WARM) */
        body[data-theme='midnight-crimson'] {
            --bg-color: #1a0a0a;
            --text-color: #fce4ec;
            --accent-color: #e57373;
            --secondary-color: #ffeb3b;
            --border-color: #420a0a;
            --card-bg: #2b1010;
            --button-bg: #e57373;
            --button-hover-bg: #d32f2f;
            --tag-bg: #420a0a;
            --tag-color: #fce4ec;
            --ornamental-line: linear-gradient(to right, var(--accent-color) 0%, var(--border-color) 50%, var(--accent-color) 100%);
        }

        /* ---------------------------------- */
        /* BASE STYLES */
        /* ---------------------------------- */
        body {
            margin: 0;
            font-family: var(--font-family-body);
            background-color: var(--bg-color);
            color: var(--text-color);
            line-height: 1.7;
            padding-bottom: 70px;
            transition: background-color 0.5s, color 0.5s;
            /* Ensure the main body doesn't scroll horizontally due to header content */
            overflow-x: hidden;
        }

        .container {
            width: 90%;
            max-width: var(--container-max-width);
            margin: 0 auto;
            padding: 40px 0;
        }

        /* ---------------------------------- */
        /* FLOATING METRICS SYSTEM (DEFAULT: DESKTOP) */
        /* ---------------------------------- */
        .floating-metrics-container {
            position: fixed;
            /* DEFAULT: Fixed position for desktop */
            bottom: 100px;
            right: 20px;
            z-index: 99;
            display: flex;
            align-items: flex-end;
            /* Align button and badges to the bottom */
        }

        /* 1. Hide the checkbox input */
        #show-metrics-toggle {
            display: none;
        }

        /* 2. Floating Button Style (The clickable label) */
        .metrics-toggle-link.floating-button {
            cursor: pointer;
            padding: 10px 10px;
            border-radius: 4px;
            background: var(--accent-color);
            color: white;
            text-transform: uppercase;
            font-weight: 700;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
            transition: background 0.2s, transform 0.2s;
            line-height: .5;
            z-index: 100;
        }

        .metrics-toggle-link.floating-button:hover {
            background: var(--button-hover-bg);
            transform: scale(1.05);
        }

        /* Default text for the floating button */
        .metrics-toggle-link.floating-button::after {
            content: "📊 METRICS";
        }

        /* Text when checked */
        #show-metrics-toggle:checked~.metrics-toggle-link.floating-button::after {
            content: "❌ CLOSE";
        }

        /* 3. LIGHTHOUSE BADGES (Hidden by Default) */
        .lighthouse-badges {
            display: none;
            position: absolute;
            /* DEFAULT: Absolute position for desktop */
            right: 0;
            bottom: calc(100% + 10px);

            padding: 10px;
            background-color: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 4px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);

            /* Styles for when it is visible */
            flex-direction: column;
            align-items: flex-end;
            /* Align badges to the right within the box */
        }

        /* 4. KEY: Reveal the badges when the checkbox is checked */
        #show-metrics-toggle:checked~.lighthouse-badges {
            display: flex;
        }

        /* Badge component styling */
        .badge {
            padding: 5px 10px;
            border-radius: 2px;
            font-weight: 700;
            font-size: 0.8em;
            color: white;
            box-shadow: 1px 1px 3px rgba(0, 0, 0, 0.2);
            text-transform: uppercase;
            margin: 4px 0;
            white-space: nowrap;
        }

        /* Score-specific colors */
        .performance {
            background-color: #00c853;
        }

        .accessibility {
            background-color: #00c853;
        }

        .best-practices {
            background-color: #00c853;
        }

        .seo {
            background-color: #ffab00;
        }

        /* ---------------------------------- */
        /* HEADER / PROFILE (Content Updated) */
        /* ---------------------------------- */
        header {
            padding: 30px 0;
            margin-bottom: 30px;
            text-align: center;
            border-bottom: 2px solid var(--accent-color);
            position: relative;
        }

        header h1 {
            font-size: 3em;
            color: var(--accent-color);
            margin: 0 0 5px 0;
            text-transform: uppercase;
            letter-spacing: 0.1em;
            font-family: var(--font-family-title);
        }

        /* NEW: Style the central statement block */
        .statement-purpose {
            max-width: 650px;
            margin: 20px auto;
            padding: 25px 35px;
            background-color: var(--card-bg);
            /* Use the card background for contrast */
            border: 3px double var(--accent-color);
            /* Strong ornamental border */
            border-radius: 4px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        }

        /* h2 style within the new statement block */
        .statement-purpose h2 {
            font-size: 1.2em;
            color: var(--secondary-color);
            margin: 0 auto 10px auto;
            /* Reduced bottom margin */
            font-weight: 400;
            font-variant: small-caps;
            letter-spacing: 0.1em;
            /* Fix: Prevent word wrap on the sub-headline, but allow overflow */
            white-space: nowrap;
        }

        /* profile-summary style within the new statement block */
        .statement-purpose .profile-summary {
            max-width: 100%;
            margin: 10px auto 0 auto;
            color: var(--text-color);
            font-style: normal;
            /* Removed italic */
            font-weight: 700;
            /* Added bold */
            font-size: 1.1em;
        }

        /* THEME SWITCHER STYLES */
        .theme-switcher-container {
            position: absolute;
            top: 10px;
            right: 10px;
            display: flex;
            align-items: center;
            font-size: 0.9em;
        }

        #theme-switcher {
            padding: 5px 10px;
            border: 1px solid var(--border-color);
            background-color: var(--card-bg);
            color: var(--text-color);
            border-radius: 4px;
            margin-left: 5px;
            font-family: var(--font-family-body);
        }

        /* ---------------------------------- */
        /* FOOTER (Unchanged, just cleaner) */
        /* ---------------------------------- */
        footer {
            width: 100%;
            background: var(--card-bg);
            color: var(--secondary-color);
            text-align: center;
            padding: 5px 0 0 0;
            font-size: 0.8em;
            border-top: 2px solid var(--border-color);
            position: fixed;
            bottom: 0;
            left: 0;
            z-index: 10;
        }

        .footer-content {
            padding: 5px 0 10px 0;
        }

        .footer-links a {
            margin: 0 10px;
        }

        /* ---------------------------------- */
        /* MOBILE ENHANCEMENTS */
        /* ---------------------------------- */
        @media (max-width: 600px) {

            /* Footer scrolls on mobile only */
            footer {
                position: static;
                padding: 10px 0;
            }

            .footer-content {
                padding: 5px 0;
            }

            body {
                padding-bottom: 20px;
            }

            /* FIX: Contain horizontal scrolling to the header on small screens */
            header {
                padding: 30px 0;
                margin-bottom: 30px;
                text-align: center;
                border-bottom: 2px solid var(--accent-color);
                position: relative;
                /* NEW: Allow horizontal scroll only in this section */
                overflow-x: auto;
            }

            /* KEY CHANGE: Turn Floating Metrics into a static, centered block */
            .floating-metrics-container {
                position: static;
                /* No longer fixed */
                margin: 30px auto;
                /* Centers the block horizontally in flow */
                right: auto;
                /* Remove fixed right positioning */
                bottom: auto;
                /* Remove fixed bottom positioning */

                /* Reconfigure flex to center its contents (button & badges) */
                flex-direction: column-reverse;
                /* Put the button on the bottom, then the badges */
                align-items: center;
                /* Center the button and badges horizontally */
            }

            /* KEY CHANGE: Make badges appear in static flow above the button */
            .lighthouse-badges {
                position: static;
                /* No longer absolute */
                box-shadow: none;
                /* Make it look integrated, not floating */
                right: auto;
                /* Remove absolute positioning */
                bottom: auto;
                /* Remove absolute positioning */
                margin-bottom: 15px;
                /* Spacing between badges and button */

                /* Adjust alignment for centering */
                align-items: center;
                padding: 15px;
                width: 90%;
                max-width: 300px;
            }

            /* Mobile button refinements */
            .metrics-toggle-link.floating-button {
                width: 100%;
                /* Make the button take up the full width of the badge container's max-width for a block look */
                max-width: 300px;
                text-align: center;
                margin-top: 0;
            }

            /* Smaller badges for mobile density */
            .badge {
                font-size: 0.7em;
                margin: 3px 0;
            }

            header h1 {
                font-size: 2.5em;
            }

            header h2 {
                font-size: 1em;
                /* Prevent sub-headline from shrinking too much and ensure single line */
                min-width: 300px;
                /* NEW: Add padding for visual spacing when scrolling */
                padding: 0 10px;
            }

            .statement-purpose {
                padding: 15px 20px;
                margin: 15px auto;
                border: 2px solid var(--accent-color);
                /* NEW: Prevent the statement block itself from scrolling or causing overflow */
                overflow: hidden;
            }

            .action-button {
                display: block;
                width: 90%;
                margin: 10px auto;
            }

            .theme-switcher-container {
                position: static;
                justify-content: center;
                margin-top: 15px;
            }

            /* Workflow List mobile stack */
            .workflow-list {
                flex-direction: column;
                gap: 15px;
            }

            /* CSS-ONLY FILTER TOGGLE LOGIC (for Projects) */
            .mobile-toggle-button {
                display: block;
                width: 100%;
                text-align: center;
                margin: 0 0 15px 0;
                padding: 10px 0;
                background: var(--secondary-color);
                color: white;
                font-weight: 700;
                cursor: pointer;
                border: 1px solid var(--secondary-color);
            }

            .filter-tags-container {
                display: none;
                overflow-x: visible;
                white-space: normal;
                padding-bottom: 0;
            }

            .filter-tags-container .skill-tag {
                margin-right: 5px;
                margin-bottom: 5px;
            }

            #mobile-filter-toggle:checked~.filter-tags-container {
                display: block;
                padding: 10px 0;
                border-top: 1px dashed var(--border-color);
                margin-bottom: 20px;
            }

            #mobile-filter-toggle:checked~.mobile-toggle-button {
                background: var(--accent-color);
            }
        }

        /* ---------------------------------- */
        /* BUTTONS & LINKS (Unchanged for brevity, but retained in final code) */
        /* ---------------------------------- */
        a {
            color: var(--accent-color);
            text-decoration: underline;
            transition: color 0.2s;
        }

        a:hover {
            color: var(--secondary-color);
        }

        .button-group {
            margin-top: 25px;
        }

        .action-button {
            display: inline-block;
            padding: 10px 20px;
            margin: 5px 10px;
            background: var(--button-bg);
            color: white;
            border-radius: 2px;
            text-transform: uppercase;
            font-weight: 700;
            border: none;
            cursor: pointer;
            box-shadow: 2px 2px 0px rgba(0, 0, 0, 0.2);
            text-shadow: 1px 1px 1px rgba(0, 0, 0, 0.2);
            transition: background 0.2s, box-shadow 0.1s, transform 0.1s;
        }

        .action-button:hover {
            background: var(--button-hover-bg);
            box-shadow: 1px 1px 0px rgba(0, 0, 0, 0.2);
            transform: translateY(1px);
        }

        .action-button:focus {
            outline: 3px solid var(--accent-color);
            outline-offset: 2px;
        }

        /* ORNAMENTAL DIVIDER */
        .ornamental-divider {
            height: 1px;
            background: var(--ornamental-line);
            margin: 30px 0;
            border: none;
        }

        /* NEW WORKFLOW STYLES (Content Updated) */
        #workflow {
            margin-bottom: 30px;
            padding: 30px;
            background-color: var(--card-bg);
            border: 1px solid var(--border-color);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }

        #workflow h3 {
            font-size: 1.8em;
            color: var(--secondary-color);
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 10px;
            margin-top: 0;
            margin-bottom: 25px;
            font-family: var(--font-family-title);
        }

        .workflow-list {
            list-style: none;
            padding: 0;
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            justify-content: space-between;
        }

        .workflow-step {
            flex: 1 1 200px;
            border-left: 3px solid var(--accent-color);
            padding-left: 15px;
            position: relative;
        }

        .workflow-step strong {
            display: block;
            color: var(--accent-color);
            font-size: 1.1em;
            margin-bottom: 5px;
        }

        .workflow-step:before {
            content: counter(step-counter);
            counter-increment: step-counter;
            position: absolute;
            left: -17px;
            top: 0;
            background: var(--accent-color);
            color: white;
            width: 25px;
            height: 25px;
            border-radius: 50%;
            text-align: center;
            line-height: 25px;
            font-size: 0.9em;
            font-weight: 700;
        }

        /* PROJECTS SECTION & CSS FILTER LOGIC (Content Updated) */
        #projects {
            margin-bottom: 30px;
            padding: 30px;
            background-color: var(--card-bg);
            border: 1px solid var(--border-color);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }

        #projects h3 {
            font-size: 1.8em;
            color: var(--secondary-color);
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 10px;
            margin-top: 0;
            margin-bottom: 25px;
            font-family: var(--font-family-title);
        }

        .skill-filter-input {
            display: none;
        }

        .skill-tag {
            background: var(--tag-bg);
            color: var(--tag-color);
            padding: 6px 12px;
            border-radius: 4px;
            font-size: 0.9em;
            border: 1px solid var(--border-color);
            font-weight: 400;
            cursor: pointer;
            display: inline-block;
            margin-right: 8px;
            margin-bottom: 8px;
            transition: background 0.2s, color 0.2s, transform 0.1s;
        }

        .mobile-toggle-button {
            display: none;
        }

        .skill-filter-input+.filter-tags-container>label.skill-tag {
            background: var(--tag-bg);
            color: var(--tag-color);
            border-color: var(--border-color);
        }

        #filter-all:checked~.filter-tags-container>label[for='filter-all'],
        #filter-webdev:checked~.filter-tags-container>label[for='filter-webdev'],
        #filter-analysis:checked~.filter-tags-container>label[for='filter-analysis'],
        #filter-integration:checked~.filter-tags-container>label[for='filter-integration'],
        #filter-design:checked~.filter-tags-container>label[for='filter-design'],
        #filter-freelance:checked~.filter-tags-container>label[for='filter-freelance'],
        #filter-development:checked~.filter-tags-container>label[for='filter-development'] {
            background: var(--accent-color);
            color: white;
            border-color: var(--accent-color);
        }

        .project-list .project-item {
            display: none;
            border-bottom: 1px dashed var(--border-color);
            padding: 20px 0;
            transition: background-color 0.2s, border-left 0.2s, padding-left 0.2s;
        }

        .project-list .project-item:last-child {
            border-bottom: none;
            padding-bottom: 0;
        }

        .project-list .project-item:hover {
            background-color: color-mix(in srgb, var(--card-bg) 95%, var(--accent-color));
            border-left: 5px solid var(--accent-color);
            padding-left: 25px;
        }

        .project-list .project-item h4 {
            font-size: 1.35em;
            font-weight: 700;
            color: var(--accent-color);
            margin: 0 0 5px 0;
            font-family: var(--font-family-title);
        }

        .project-tags-list {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-bottom: 10px;
        }

        .project-tag {
            background: var(--secondary-color);
            color: white;
            padding: 4px 8px;
            border-radius: 2px;
            font-size: 0.75em;
            text-transform: uppercase;
        }

        .project-links a {
            font-weight: 700;
            text-transform: none;
            text-decoration: none;
            border-bottom: 1px dashed var(--accent-color);
            margin-right: 15px;
        }

        #filter-all:checked~.project-list .project-item {
            display: block;
        }

        #filter-webdev:checked~.project-list .webdev {
            display: block;
        }

        #filter-analysis:checked~.project-list .analysis {
            display: block;
        }

        #filter-integration:checked~.project-list .integration {
            display: block;
        }

        #filter-design:checked~.project-list .design {
            display: block;
        }

        #filter-freelance:checked~.project-list .freelance {
            display: block;
        }

        #filter-development:checked~.project-list .development {
            display: block;
        }
    </style>
</head>

<body data-theme="journal">
    <main class="container">
        <header>
            <div class="theme-switcher-container">
                <label for="theme-switcher">Theme:</label>
                <select id="theme-switcher">
                    <option value="journal">Classic Journal</option>
                    <option value="deep-sea">Deep Sea Coder</option>
                    <option value="midnight-crimson">Midnight Crimson</option>
                </select>
            </div>

            <h1>Jordan Dudgeon</h1>


            <div class="statement-purpose">
                <h2>Designing Seamless Experiences.<br>Transforming Complexity.</h2>
                <p class="profile-summary">
                    My focus is building intuitive, high-performance systems that transform complex technical challenges
                    into simple, efficient solutions for both users and business operations.
                </p>
            </div>

            <div class="button-group">
                <a href="https://www.linkedin.com/in/jordan-dudgeon" target="_blank" rel="noopener"
                    class="action-button">LinkedIn</a>
                <a href="mailto:jdudgeon1993@gmail.com" class="action-button">Email Me</a>
            </div>
        </header>

        <div class="ornamental-divider"></div>

        <section id="workflow">
            <h3>Deployment Workflow & Seamless Delivery 🚀</h3>
            <p style="margin-bottom: 25px;">
                A clear, end-to-end process ensuring optimal performance, maintainability, and seamless client alignment
                for every deliverable.
            </p>
            <ul class="workflow-list" style="counter-reset: step-counter;">
                <li class="workflow-step">
                    <strong>Phase 1: Identify & Strategize</strong>
                    User research, complexity analysis, and wireframing to establish the core, intuitive design system.
                </li>
                <li class="workflow-step">
                    <strong>Phase 2: Build & Test Efficiency</strong>
                    Semantic code implementation with rigorous testing to ensure high-performance and highly efficient
                    solutions.
                </li>
                <li class="workflow-step">
                    <strong>Phase 3: Launch & Deliver</strong>
                    Version control, asset optimization, and seamless deployment into the final production environment.
                </li>
                <li class="workflow-step">
                    <strong>Phase 4: Iterate & Optimize</strong>
                    Continuous monitoring (Lighthouse) and iteration to maintain peak performance and the simple,
                    efficient user experience.
                </li>
            </ul>
        </section>

        <div class="ornamental-divider"></div>


        <section id="projects">
            <h3>Projects & Index</h3>

            <input type="radio" id="filter-all" name="skill-filter" class="skill-filter-input" checked>
            <input type="radio" id="filter-webdev" name="skill-filter" class="skill-filter-input">
            <input type="radio" id="filter-analysis" name="skill-filter" class="skill-filter-input">
            <input type="radio" id="filter-integration" name="skill-filter" class="skill-filter-input">
            <input type="radio" id="filter-design" name="skill-filter" class="skill-filter-input">
            <input type="radio" id="filter-freelance" name="skill-filter" class="skill-filter-input">
            <input type="radio" id="filter-development" name="skill-filter" class="skill-filter-input">

            <input type="checkbox" id="mobile-filter-toggle" class="skill-filter-input">

            <label for="mobile-filter-toggle" class="skill-tag mobile-toggle-button">Filter Projects ▼</label>


            <div class="filter-tags-container">
                <label for="filter-all" class="skill-tag">Completed Work</label>
                <label for="filter-webdev" class="skill-tag">Seamless UI/UX Development</label>
                <label for="filter-analysis" class="skill-tag">Complexity Mapping & Analysis</label>
                <label for="filter-integration" class="skill-tag">Efficient System Integration</label>
                <label for="filter-design" class="skill-tag">Intuitive Design Systems</label>
                <label for="filter-freelance" class="skill-tag">Client Solutions</label>
                <label for="filter-development" class="skill-tag">In Development</label>
            </div>

            <div class="project-list" style="margin-top: 20px;">

                <div class="project-item webdev design">
                    <h4>Dynamic Themed Portfolio (Current Site)</h4>
                    <div class="project-tags-list">
                        <span class="project-tag">HTML</span>
                        <span class="project-tag">CSS/SASS</span>
                        <span class="project-tag">JavaScript</span>
                        <span class="project-tag">Design Systems</span>
                    </div>
                    <p>
                        Live demonstration of scalability. Built with modular CSS themes and CSS-only filtering for
                        instant, zero-latency UX and future-proof design systems.
                    </p>
                    <div class="project-links">
                        <a href="https://jdudgeon1993.github.io/jdudgeon1993/" target="_blank" rel="noopener">View
                            Live</a>
                        <a href="https://github.com/jdudgeon1993/jdudgeon1993" target="_blank" rel="noopener">Code</a>
                    </div>
                </div>

                <div class="project-item webdev analysis integration freelance">
                    <h4>Workflow Optimization & Client Website Delivery</h4>
                    <div class="project-tags-list">
                        <span class="project-tag">Business Analysis</span>
                        <span class="project-tag">System Integration</span>
                        <span class="project-tag">Freelance</span>
                        <span class="project-tag">Minimalist UI</span>
                    </div>
                    <p>
                        Complexity transformed. Conducted deep workflow analysis to reduce departmental friction, then
                        delivered a high-speed, minimalist website that maximized client lead conversion.
                    </p>
                    <div class="project-links">
                        <a href="https://github.com/jdudgeon1993/Projects/blob/28454ac426544536ed555853b532563bf96f52a3/Heathers%20Project"
                            target="_blank" rel="noopener">View Report (Analysis)</a>
                        <a href="https://liveweave.com/6v2Mx2" target="_blank" rel="noopener">View Demo (Website)</a>
                    </div>
                </div>

                <div class="project-item development">
                    <h4>TBD Project</h4>
                    <div class="project-tags-list">
                        <span class="project-tag">IN DEVELOPMENT</span>
                    </div>
                    <p>
                        In development. Focused on building a solution that demonstrates full-stack technical efficiency
                        and superior user workflow design.
                    </p>
                    <div class="project-links">
                        <a href="#" onclick="return false;">Link TBD</a>
                    </div>
                </div>

            </div>
        </section>

        <div class="floating-metrics-container">
            <input type="checkbox" id="show-metrics-toggle">

            <div class="lighthouse-badges">
                <span class="badge performance">🚀 100 Performance</span>
                <span class="badge accessibility">♿ 100 Accessibility</span>
                <span class="badge best-practices">✅ 100 Best Practices</span>
                <span class="badge seo">🔎 91 SEO</span>
            </div>

            <label for="show-metrics-toggle" class="metrics-toggle-link floating-button"></label>
        </div>

    </main>

    <footer>
        <div class="footer-content">
            <p>&copy; 2025 Jordan Dudgeon | All Rights Reserved.</p>
            <div class="footer-links">
                <a href="https://www.linkedin.com/in/jordan-dudgeon" target="_blank" rel="noopener">LinkedIn</a>
                <a href="mailto:jdudgeon1993@gmail.com">jdudgeon1993@gmail.com</a>
            </div>
        </div>
    </footer>


    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const themeSwitcher = document.getElementById('theme-switcher');
            const body = document.body;
            const storageKey = 'portfolioTheme';

            // 1. Load theme from local storage
            const storedTheme = localStorage.getItem(storageKey);
            if (storedTheme) {
                body.setAttribute('data-theme', storedTheme);
                themeSwitcher.value = storedTheme;
            } else {
                // If no theme is stored, default to 'journal' and set the attribute
                body.setAttribute('data-theme', 'journal');
                themeSwitcher.value = 'journal';
            }

            // 2. Handle theme change on dropdown selection
            if (themeSwitcher) { 
                 themeSwitcher.addEventListener('change', (event) => {
                    const newTheme = event.target.value;
                    body.setAttribute('data-theme', newTheme);
                    localStorage.setItem(storageKey, newTheme);
                });
            }
        });
    </script>
</body>

</html>
