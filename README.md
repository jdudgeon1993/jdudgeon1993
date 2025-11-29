<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&family=Playfair+Display:ital,wght@0,400;0,700;1,400&display=swap" rel="stylesheet">
    <title>Jordan Dudgeon – Portfolio</title>
    <style>
        /* ---------------------------------- */
        /* THEME DEFINITIONS (CSS VARIABLES)  */
        /* ---------------------------------- */

        :root {
            --font-family-title: 'Playfair Display', serif;
            --font-family-body: 'Georgia', 'Times New Roman', serif;
            --container-max-width: 800px;
        }

        /* 1. CLASSIC JOURNAL (LIGHT/DEFAULT) */
        body[data-theme='journal'] {
            --bg-color: #fcf8e8; /* Parchment/Cream */
            --text-color: #3e382d; /* Dark Brown/Sepia */
            --accent-color: #923a3a; /* Deep Burgundy/Ink */
            --secondary-color: #4a5c68; /* Old Book Navy */
            --border-color: #e0d9c6; /* Faded paper border */
            --card-bg: #ffffff; /* White page */
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
            --accent-color: #26a69a; /* Teal/Mint */
            --secondary-color: #ffb74d; /* Amber/Orange */
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
            --accent-color: #e57373; /* Muted Red/Crimson */
            --secondary-color: #ffeb3b; /* Gold/Yellow */
            --border-color: #420a0a; 
            --card-bg: #2b1010; 
            --button-bg: #e57373;
            --button-hover-bg: #d32f2f;
            --tag-bg: #420a0a;
            --tag-color: #fce4ec;
            --ornamental-line: linear-gradient(to right, var(--accent-color) 0%, var(--border-color) 50%, var(--accent-color) 100%);
        }

        /* ---------------------------------- */
        /* BASE STYLES (USE CSS VARIABLES)    */
        /* ---------------------------------- */
        body {
            margin: 0;
            font-family: var(--font-family-body); 
            background-color: var(--bg-color);
            color: var(--text-color);
            line-height: 1.7;
            padding-bottom: 70px; /* Needed for fixed footer */
            transition: background-color 0.5s, color 0.5s;
        }

        .container {
            width: 90%;
            max-width: var(--container-max-width);
            margin: 0 auto;
            padding: 40px 0;
        }

        /* ---------------------------------- */
        /* HEADER / PROFILE */
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
        header h2 {
            font-size: 1.2em;
            color: var(--secondary-color);
            margin: 0 0 20px 0;
            font-weight: 400;
            font-variant: small-caps;
            letter-spacing: 0.1em;
        }
        .profile-summary {
            max-width: 600px;
            margin: 0 auto;
            color: var(--text-color); 
            font-style: italic;
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
        /* BUTTONS & LINKS */
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
            text-shadow: 1px 1px 1px rgba(0,0,0,0.2);
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

        /* ---------------------------------- */
        /* PROJECTS SECTION & CSS FILTER LOGIC */
        /* ---------------------------------- */
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
        
        /* 1. Hide the radio inputs */
        .skill-filter-input {
            display: none;
        }
        
        /* 2. Filter Tag Styling */
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
        
        /* Special style for the mobile toggle button */
        .mobile-toggle-button {
            display: none; /* Hidden by default (desktop view) */
        }


        /* 3. Style the active (checked) label */
        /* Reset all tags */
        .skill-filter-input + .filter-tags-container > label.skill-tag {
            background: var(--tag-bg); 
            color: var(--tag-color);
            border-color: var(--border-color);
        }
        /* Highlight the active tag using the sibling selector */
        #filter-all:checked ~ .filter-tags-container > label[for='filter-all'],
        #filter-webdev:checked ~ .filter-tags-container > label[for='filter-webdev'],
        #filter-analysis:checked ~ .filter-tags-container > label[for='filter-analysis'],
        #filter-integration:checked ~ .filter-tags-container > label[for='filter-integration'],
        #filter-design:checked ~ .filter-tags-container > label[for='filter-design'],
        #filter-freelance:checked ~ .filter-tags-container > label[for='filter-freelance'],
        #filter-development:checked ~ .filter-tags-container > label[for='filter-development'] {
            background: var(--accent-color);
            color: white;
            border-color: var(--accent-color);
        }

        .project-tag:hover {
            opacity: 0.8;
            transform: scale(1.05);
        }

        /* PROJECT LIST STYLES */
        .project-list .project-item {
            display: none; /* All hidden initially */
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

        /* CSS FILTER MAGIC: The inputs are now siblings of the project-list! */
        #filter-all:checked ~ .project-list .project-item {
            display: block;
        }
        #filter-webdev:checked ~ .project-list .webdev {
            display: block;
        }
        #filter-analysis:checked ~ .project-list .analysis {
            display: block;
        }
        #filter-integration:checked ~ .project-list .integration {
            display: block;
        }
        #filter-design:checked ~ .project-list .design {
            display: block;
        }
        #filter-freelance:checked ~ .project-list .freelance {
            display: block;
        }
        #filter-development:checked ~ .project-list .development {
            display: block;
        }

        /* FOOTER (FIXED ON DESKTOP) */
        footer {
            width: 100%;
            background: var(--card-bg);
            color: var(--secondary-color);
            text-align: center;
            padding: 20px 0;
            font-size: 0.8em;
            border-top: 2px solid var(--border-color);
            position: fixed; /* Keeps footer fixed on desktop by default */
            bottom: 0;
            left: 0;
            z-index: 10;
        }
        .footer-links a {
            margin: 0 10px;
        }

        /* ---------------------------------- */
        /* MOBILE ENHANCEMENTS (max-width: 600px) */
        /* ---------------------------------- */
        @media (max-width: 600px) {
            
            /* Footer scrolls on mobile only */
            footer {
                position: static; 
            }
            body {
                padding-bottom: 20px; 
            }

            header h1 { font-size: 2.5em; }
            header h2 { font-size: 1em; }
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
            
            /* ---------------------------------- */
            /* CSS-ONLY FILTER TOGGLE LOGIC       */
            /* ---------------------------------- */
            
            /* 1. Show the Mobile Toggle Button */
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

            /* 2. Hide the Filter Tags Container by default */
            .filter-tags-container {
                display: none;
                /* Reset horizontal scrolling for the drop-down effect */
                overflow-x: visible;
                white-space: normal; 
                padding-bottom: 0;
            }
            
            /* Style the individual tags inside the toggled view */
            .filter-tags-container .skill-tag {
                margin-right: 5px;
                margin-bottom: 5px;
            }

            /* 3. Show the Filter Tags Container when the toggle is checked */
            #mobile-filter-toggle:checked ~ .filter-tags-container {
                display: block;
                padding: 10px 0;
                border-top: 1px dashed var(--border-color);
                margin-bottom: 20px;
            }
            
            /* 4. Update the toggle button text when checked */
            #mobile-filter-toggle:checked ~ .mobile-toggle-button {
                background: var(--accent-color);
                content: "Close Filters ▲"; /* Note: content property only works on pseudo-elements, we'll rely on styling for feedback */
            }

        }
    </style>
</head>
<body data-theme="journal">
    <div class="container">
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
            <h2>Bridging Design, Development, and Process Optimization</h2>
            
            <p class="profile-summary">
                I build intuitive, performant interfaces and use technical analysis to **engineer better business workflows.**
            </p>
            
            <div class="button-group">
                <a href="https://www.linkedin.com/in/jordan-dudgeon" target="_blank" rel="noopener" class="action-button">LinkedIn</a>
                <a href="mailto:jdudgeon1993@gmail.com" class="action-button">Email Me</a>
            </div>
        </header>

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
                <label for="filter-webdev" class="skill-tag">Full-Stack UI/UX</label>
                <label for="filter-analysis" class="skill-tag">Process Mapping & Analysis</label>
                <label for="filter-integration" class="skill-tag">System & Data Integration</label>
                <label for="filter-design" class="skill-tag">Scalable Design Systems</label>
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
                        Demonstrating mastery of clean CSS, this portfolio features **CSS-only filtering** and **thematic design systems** for immediate, low-latency UX.
                    </p>
                    <div class="project-links">
                        <a href="https://jdudgeon1993.github.io/jdudgeon1993/" target="_blank" rel="noopener">View Live</a>
                        <a href="https://github.com/jdudgeon1993/jdudgeon1993" target="_blank" rel="noopener">Code</a>
                    </div>
                </div>

                <div class="project-item analysis integration">
                    <h4>Inter-Departmental Project Analysis</h4>
                    <div class="project-tags-list">
                        <span class="project-tag">Business Analysis</span>
                        <span class="project-tag">System Integration</span>
                        <span class="project-tag">Workflow Design</span>
                    </div>
                    <p>
                        Comprehensive business analysis that delivered **actionable system integration** and resource recommendations, **reducing cross-departmental friction.**
                    </p>
                    <div class="project-links">
                        <a href="https://github.com/jdudgeon1993/Projects/blob/28454ac426544536ed555853b532563bf96f52a3/Heathers%20Project" target="_blank" rel="noopener">View Report</a>
