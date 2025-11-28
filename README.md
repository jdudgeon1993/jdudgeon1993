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
        /* THE CLASSIC JOURNAL (BOOKISH) THEME */
        /* ---------------------------------- */

        :root {
            --bg-color: #fcf8e8; /* Parchment/Cream */
            --text-color: #3e382d; /* Dark Brown/Sepia */
            --accent-color: #923a3a; /* Deep Burgundy/Ink */
            --secondary-color: #4a5c68; /* Old Book Navy */
            --border-color: #e0d9c6; /* Faded paper border */
            --card-bg: #ffffff; /* White page */
            --button-bg: #4a5c68; 
            --button-hover-bg: #3a4b56;
        }

        body {
            margin: 0;
            font-family: 'Georgia', 'Times New Roman', serif; 
            background-color: var(--bg-color);
            color: var(--text-color);
            line-height: 1.7;
            padding-bottom: 70px;
        }

        .container {
            width: 90%;
            max-width: 800px;
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
        }
        header h1 {
            font-size: 3em;
            color: var(--accent-color);
            margin: 0 0 5px 0;
            text-transform: capitalize;
            font-family: 'Playfair Display', serif;
        }
        header h2 {
            /* Updated wording for H2 */
            font-size: 1.2em;
            color: var(--secondary-color);
            margin: 0 0 20px 0;
            font-weight: 400;
        }
        .profile-summary {
            max-width: 600px;
            margin: 0 auto;
            color: var(--text-color); 
            font-style: italic;
            font-size: 1.1em;
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
            transition: background 0.2s, box-shadow 0.1s, transform 0.1s;
        }
        .action-button:hover {
            background: var(--button-hover-bg);
            box-shadow: 1px 1px 0px rgba(0, 0, 0, 0.2);
            transform: translateY(1px);
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
            font-family: 'Playfair Display', serif;
        }
        
        /* 1. Hide the radio inputs */
        .skill-filter-input {
            display: none;
        }

        /* 2. Style the labels (which are the clickable skill tags) */
        .skill-tag {
            background: #f0f0f0;
            color: var(--secondary-color);
            padding: 6px 12px;
            border-radius: 4px;
            font-size: 0.9em;
            border: 1px solid var(--border-color);
            font-weight: 400;
            cursor: pointer;
            display: inline-block;
            margin-right: 8px;
            margin-bottom: 8px;
            transition: background 0.2s, color 0.2s;
        }

        /* 3. Style the active (checked) label */
        .skill-filter-input:checked + .skill-tag {
            background: var(--accent-color);
            color: white;
            border-color: var(--accent-color);
        }

        /* PROJECT LIST STYLES */
        /* 4. HIDE ALL PROJECT ITEMS BY DEFAULT */
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
            background-color: #faf7eb;
            border-left: 5px solid var(--accent-color);
            padding-left: 25px;
        }
        .project-list .project-item h4 {
            font-size: 1.3em;
            color: var(--accent-color);
            margin: 0 0 5px 0;
            font-family: 'Playfair Display', serif;
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

        /* 5. CSS FILTER MAGIC (using the general sibling selector ~) */
        
        /* Show ALL projects when the 'All' radio button is checked */
        #filter-all:checked ~ .project-list .project-item {
            display: block;
        }

        /* Show projects matching filter-class when checked */
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
        /* NEW FILTER LOGIC */
        #filter-development:checked ~ .project-list .development {
            display: block;
        }

        /* FOOTER */
        footer {
            width: 100%;
            background: var(--card-bg);
            color: var(--secondary-color);
            text-align: center;
            padding: 20px 0;
            font-size: 0.8em;
            border-top: 2px solid var(--border-color);
            position: fixed; 
            bottom: 0;
            left: 0;
            z-index: 10;
        }
        .footer-links a {
            margin: 0 10px;
        }

        /* Mobile Adjustments */
        @media (max-width: 600px) {
            header h1 { font-size: 2.5em; }
            header h2 { font-size: 1em; }
            .action-button {
                display: block;
                width: 90%;
                margin: 10px auto;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
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

        <hr style="border: 0; height: 1px; background: var(--border-color); margin: 30px 0;">

        <section id="projects">
            <h3>Projects & Index</h3>

            <input type="radio" id="filter-all" name="skill-filter" class="skill-filter-input" checked>
            <label for="filter-all" class="skill-tag">All Projects</label>

            <input type="radio" id="filter-webdev" name="skill-filter" class="skill-filter-input">
            <label for="filter-webdev" class="skill-tag">Full-Stack UI/UX</label>

            <input type="radio" id="filter-analysis" name="skill-filter" class="skill-filter-input">
            <label for="filter-analysis" class="skill-tag">Process Mapping & Analysis</label>

            <input type="radio" id="filter-integration" name="skill-filter" class="skill-filter-input">
            <label for="filter-integration" class="skill-tag">System & Data Integration</label>
            
            <input type="radio" id="filter-design" name="skill-filter" class="skill-filter-input">
            <label for="filter-design" class="skill-tag">Scalable Design Systems</label>
            
            <input type="radio" id="filter-freelance" name="skill-filter" class="skill-filter-input">
            <label for="filter-freelance" class="skill-tag">Client Solutions</label>
            
            <input type="radio" id="filter-development" name="skill-filter" class="skill-filter-input">
            <label for="filter-development" class="skill-tag">In Development</label>
            
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
                    </div>
                </div>

                <div class="project-item webdev freelance">
                    <h4>Business Card Website for CAD Designer</h4>
                    <div class="project-tags-list">
                        <span class="project-tag">HTML</span>
                        <span class="project-tag">CSS</span>
                        <span class="project-tag">Freelance</span>
                    </div>
                    <p>
                        Delivered a high-speed, minimalist website optimized for a **CAD design client**, ensuring **maximum conversion** and lead capture efficiency.
                    </p>
                    <div class="project-links">
                        <a href="https://liveweave.com/6v2Mx2" target="_blank" rel="noopener">View Demo</a>
                    </div>
                </div>

                <div class="project-item development">
                    <h4>TBD for each new one (Project 1)</h4>
                    <div class="project-tags-list">
                        <span class="project-tag">IN DEVELOPMENT</span>
                    </div>
                    <p>In Development</p>
                    <div class="project-links">
                        <a href="#" onclick="return false;">Link TBD</a>
                    </div>
                </div>
                
                <div class="project-item development">
                    <h4>TBD for each new one (Project 2)</h4>
                    <div class="project-tags-list">
                        <span class="project-tag">IN DEVELOPMENT</span>
                    </div>
                    <p>In Development</p>
                    <div class="project-links">
                        <a href="#" onclick="return false;">Link TBD</a>
                    </div>
                </div>
                
                <div class="project-item development">
                    <h4>TBD for each new one (Project 3)</h4>
                    <div class="project-tags-list">
                        <span class="project-tag">IN DEVELOPMENT</span>
                    </div>
                    <p>In Development</p>
                    <div class="project-links">
                        <a href="#" onclick="return false;">Link TBD</a>
                    </div>
                </div>
                
                <div class="project-item development">
                    <h4>TBD for each new one (Project 4)</h4>
                    <div class="project-tags-list">
                        <span class="project-tag">IN DEVELOPMENT</span>
                    </div>
                    <p>In Development</p>
                    <div class="project-links">
                        <a href="#" onclick="return false;">Link TBD</a>
                    </div>
                </div>
                
                <div class="project-item development">
                    <h4>TBD for each new one (Project 5)</h4>
                    <div class="project-tags-list">
                        <span class="project-tag">IN DEVELOPMENT</span>
                    </div>
                    <p>In Development</p>
                    <div class="project-links">
                        <a href="#" onclick="return false;">Link TBD</a>
                    </div>
                </div>
                
                <div class="project-item development">
                    <h4>TBD for each new one (Project 6)</h4>
                    <div class="project-tags-list">
                        <span class="project-tag">IN DEVELOPMENT</span>
                    </div>
                    <p>In Development</p>
                    <div class="project-links">
                        <a href="#" onclick="return false;">Link TBD</a>
                    </div>
                </div>
                
                <div class="project-item development">
                    <h4>TBD for each new one (Project 7)</h4>
                    <div class="project-tags-list">
                        <span class="project-tag">IN DEVELOPMENT</span>
                    </div>
                    <p>In Development</p>
                    <div class="project-links">
                        <a href="#" onclick="return false;">Link TBD</a>
                    </div>
                </div>
                
                <div class="project-item development">
                    <h4>TBD for each new one (Project 8)</h4>
                    <div class="project-tags-list">
                        <span class
