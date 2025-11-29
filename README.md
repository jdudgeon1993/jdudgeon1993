<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta name="description" content="Jordan Dudgeon: Designing seamless user experiences, transforming complex technical challenges into simple, efficient solutions for both users and business operations.">
    
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&family=Playfair+Display:ital,wght@0,400;0,700;1,400&display=swap" rel="stylesheet">
    <title>Jordan Dudgeon – Portfolio</title>
    <style>
        /* [CSS Styles remain unchanged] */
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
        /* BASE STYLES (USE CSS VARIABLES)    */
        /* ---------------------------------- */
        body {
            margin: 0;
            font-family: var(--font-family-body); 
            background-color: var(--bg-color);
            color: var(--text-color);
            line-height: 1.7;
            padding-bottom: 70px;
            transition: background-color 0.5s, color 0.5s;
        }

        .container {
            width: 90%;
            max-width: var(--container-max-width);
            margin: 0 auto;
            padding: 40px 0;
        }

        /* ---------------------------------- */
        /* LIGHTHOUSE BADGES (New Position & Spacing)    */
        /* ---------------------------------- */
        .lighthouse-badges {
            margin: 0 auto 10px; /* Reduced top margin, added space below for separation */
            padding-top: 10px; /* Added internal top padding */
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 10px;
        }

        .badge {
            padding: 8px 12px;
            border-radius: 4px;
            font-weight: 700;
            font-size: 0.9em;
            color: white; 
            box-shadow: 1px 1px 3px rgba(0, 0, 0, 0.2);
        }

        /* Score-specific colors for high visibility */
        .performance { background-color: #00c853; /* Green for 100 */ }
        .accessibility { background-color: #00c853; /* Green for 100 */ }
        .best-practices { background-color: #00c853; /* Green for 100 */ }
        .seo { background-color: #ffab00; /* Amber for 91 */ }

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
