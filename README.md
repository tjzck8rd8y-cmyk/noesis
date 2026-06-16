<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NOESIS — Apprendre à apprendre</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg: #fafaf9;
            --bg-warm: #f5f5f0;
            --bg-card: #ffffff;
            --text: #1c1917;
            --text-secondary: #57534e;
            --text-muted: #a8a29e;
            --border: #e7e5e4;
            --border-light: #f5f5f4;
            --accent: #dc2626;
            --accent-soft: #fef2f2;
            --accent-2: #0d9488;
            --accent-2-soft: #f0fdfa;
            --accent-3: #7c3aed;
            --accent-3-soft: #f5f3ff;
            --accent-4: #d97706;
            --accent-4-soft: #fffbeb;
            --accent-5: #059669;
            --accent-5-soft: #ecfdf5;
            --radius: 16px;
            --radius-sm: 12px;
            --shadow: 0 1px 3px rgba(0,0,0,0.04), 0 1px 2px rgba(0,0,0,0.02);
            --shadow-md: 0 4px 6px -1px rgba(0,0,0,0.04), 0 2px 4px -1px rgba(0,0,0,0.02);
            --shadow-lg: 0 10px 15px -3px rgba(0,0,0,0.04), 0 4px 6px -2px rgba(0,0,0,0.02);
            --transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }
        html { scroll-behavior: smooth; }
        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
            background: var(--bg);
            color: var(--text);
            line-height: 1.65;
            font-size: 16px;
            -webkit-font-smoothing: antialiased;
        }

        /* Scrollbar */
        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-track { background: transparent; }
        ::-webkit-scrollbar-thumb { background: var(--border); border-radius: 3px; }

        /* Layout */
        .container { max-width: 1100px; margin: 0 auto; padding: 0 24px; }
        .container-narrow { max-width: 720px; margin: 0 auto; padding: 0 24px; }

        /* Nav */
        .nav {
            position: sticky;
            top: 0;
            background: rgba(250,250,249,0.92);
            backdrop-filter: blur(12px);
            border-bottom: 1px solid var(--border-light);
            z-index: 100;
            padding: 16px 0;
        }
        .nav-inner {
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        .nav-logo {
            font-size: 22px;
            font-weight: 800;
            letter-spacing: -0.5px;
            color: var(--text);
            text-decoration: none;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        .nav-logo-icon {
            width: 36px;
            height: 36px;
            background: var(--text);
            color: white;
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
            font-size: 16px;
        }
        .nav-links {
            display: flex;
            gap: 32px;
            align-items: center;
        }
        .nav-link {
            font-size: 14px;
            font-weight: 500;
            color: var(--text-secondary);
            text-decoration: none;
            transition: var(--transition);
            cursor: pointer;
            border: none;
            background: none;
            font-family: inherit;
        }
        .nav-link:hover { color: var(--text); }
        .nav-link.active { color: var(--text); font-weight: 600; }
        .nav-cta {
            padding: 8px 18px;
            background: var(--text);
            color: white;
            border-radius: 20px;
            font-size: 13px;
            font-weight: 600;
            border: none;
            cursor: pointer;
            font-family: inherit;
            transition: var(--transition);
        }
        .nav-cta:hover { transform: translateY(-1px); box-shadow: var(--shadow-md); }

        /* Hero */
        .hero {
            padding: 80px 0 60px;
            text-align: center;
        }
        .hero-illustration {
            width: 280px;
            height: auto;
            margin: 0 auto 40px;
            display: block;
        }
        .hero h1 {
            font-size: 48px;
            font-weight: 800;
            letter-spacing: -1.5px;
            line-height: 1.1;
            margin-bottom: 20px;
            color: var(--text);
        }
        .hero p {
            font-size: 20px;
            color: var(--text-secondary);
            max-width: 600px;
            margin: 0 auto 36px;
            line-height: 1.6;
        }
        .hero-cta {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            padding: 14px 28px;
            background: var(--text);
            color: white;
            border-radius: 28px;
            font-size: 15px;
            font-weight: 600;
            border: none;
            cursor: pointer;
            font-family: inherit;
            transition: var(--transition);
            text-decoration: none;
        }
        .hero-cta:hover { transform: translateY(-2px); box-shadow: var(--shadow-lg); }

        /* Sections */
        .section-title {
            font-size: 13px;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 1.5px;
            color: var(--text-muted);
            margin-bottom: 16px;
        }
        .section-heading {
            font-size: 32px;
            font-weight: 700;
            letter-spacing: -0.8px;
            margin-bottom: 12px;
            color: var(--text);
        }
        .section-desc {
            font-size: 17px;
            color: var(--text-secondary);
            max-width: 560px;
            line-height: 1.6;
        }

        /* Cards Grid */
        .cards-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
            margin-top: 40px;
        }
        .card {
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: var(--radius);
            padding: 28px;
            transition: var(--transition);
            cursor: pointer;
        }
        .card:hover {
            border-color: var(--text-muted);
            transform: translateY(-3px);
            box-shadow: var(--shadow-lg);
        }
        .card-icon {
            width: 44px;
            height: 44px;
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 22px;
            margin-bottom: 18px;
        }
        .card h3 {
            font-size: 18px;
            font-weight: 700;
            margin-bottom: 8px;
            letter-spacing: -0.3px;
        }
        .card p {
            font-size: 14px;
            color: var(--text-secondary);
            line-height: 1.6;
        }
        .card-meta {
            display: flex;
            gap: 16px;
            margin-top: 16px;
            font-size: 12px;
            color: var(--text-muted);
            font-weight: 500;
        }

        /* Category sections */
        .category-section {
            padding: 64px 0;
            border-top: 1px solid var(--border-light);
        }
        .category-header {
            display: flex;
            align-items: flex-start;
            gap: 20px;
            margin-bottom: 32px;
        }
        .category-icon {
            width: 48px;
            height: 48px;
            border-radius: 14px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            flex-shrink: 0;
        }

        /* Page sections */
        .page-section {
            display: none;
            padding: 40px 0 80px;
            animation: fadeIn 0.4s ease;
        }
        .page-section.active { display: block; }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(12px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Tool pages */
        .tool-header {
            text-align: center;
            padding: 40px 0 48px;
        }
        .tool-header h1 {
            font-size: 40px;
            font-weight: 800;
            letter-spacing: -1px;
            margin-bottom: 12px;
        }
        .tool-header p {
            font-size: 18px;
            color: var(--text-secondary);
            max-width: 560px;
            margin: 0 auto;
        }

        .tool-card {
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: var(--radius);
            padding: 32px;
            margin-bottom: 24px;
        }
        .tool-card h2 {
            font-size: 20px;
            font-weight: 700;
            margin-bottom: 8px;
            letter-spacing: -0.3px;
        }
        .tool-card .subtitle {
            font-size: 14px;
            color: var(--text-muted);
            margin-bottom: 24px;
        }

        /* Timer */
        .timer-display {
            font-size: 80px;
            font-weight: 800;
            letter-spacing: -3px;
            text-align: center;
            margin: 32px 0;
            color: var(--text);
            font-variant-numeric: tabular-nums;
        }
        .timer-modes {
            display: flex;
            justify-content: center;
            gap: 8px;
            margin-bottom: 28px;
            flex-wrap: wrap;
        }
        .timer-mode {
            padding: 8px 18px;
            border-radius: 20px;
            border: 1px solid var(--border);
            background: var(--bg);
            color: var(--text-secondary);
            font-size: 13px;
            font-weight: 500;
            cursor: pointer;
            font-family: inherit;
            transition: var(--transition);
        }
        .timer-mode:hover { border-color: var(--text-muted); }
        .timer-mode.active {
            background: var(--text);
            color: white;
            border-color: var(--text);
        }
        .timer-controls {
            display: flex;
            justify-content: center;
            gap: 12px;
            margin-bottom: 24px;
        }
        .btn {
            padding: 12px 24px;
            border-radius: 24px;
            border: 1px solid var(--border);
            background: var(--bg-card);
            color: var(--text);
            font-family: inherit;
            font-size: 14px;
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition);
            display: inline-flex;
            align-items: center;
            gap: 6px;
        }
        .btn:hover { background: var(--bg-warm); border-color: var(--text-muted); }
        .btn-primary {
            background: var(--text);
            color: white;
            border-color: var(--text);
        }
        .btn-primary:hover { background: var(--text-secondary); }
        .btn-danger {
            background: var(--accent);
            color: white;
            border-color: var(--accent);
        }
        .btn-danger:hover { background: #b91c1c; }
        .btn-sm { padding: 8px 16px; font-size: 13px; }

        /* Progress ring */
        .progress-ring-wrap {
            display: flex;
            justify-content: center;
            margin: 24px 0;
        }
        .progress-ring-bg { fill: none; stroke: var(--border); stroke-width: 6; }
        .progress-ring-fill { fill: none; stroke: var(--text); stroke-width: 6; stroke-linecap: round; transition: stroke-dashoffset 1s linear; }

        /* Subject chips */
        .chips {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-bottom: 20px;
        }
        .chip {
            padding: 8px 16px;
            border-radius: 20px;
            border: 1px solid var(--border);
            background: var(--bg);
            color: var(--text-secondary);
            font-size: 13px;
            font-weight: 500;
            cursor: pointer;
            transition: var(--transition);
            font-family: inherit;
        }
        .chip:hover { border-color: var(--text-muted); }
        .chip.active {
            background: var(--text);
            color: white;
            border-color: var(--text);
        }

        /* Forms */
        input, select, textarea {
            width: 100%;
            padding: 12px 16px;
            border-radius: var(--radius-sm);
            border: 1px solid var(--border);
            background: var(--bg);
            color: var(--text);
            font-family: inherit;
            font-size: 15px;
            outline: none;
            transition: var(--transition);
        }
        input:focus, select:focus, textarea:focus {
            border-color: var(--text-muted);
            box-shadow: 0 0 0 3px rgba(0,0,0,0.04);
        }
        .form-group { margin-bottom: 20px; }
        .form-label {
            display: block;
            font-size: 13px;
            font-weight: 600;
            color: var(--text-secondary);
            margin-bottom: 6px;
        }

        /* J Timeline */
        .j-timeline {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin: 32px 0;
            position: relative;
            padding: 0 20px;
        }
        .j-timeline::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 40px;
            right: 40px;
            height: 2px;
            background: var(--border);
            z-index: 0;
        }
        .j-node {
            width: 52px;
            height: 52px;
            border-radius: 50%;
            background: var(--bg-card);
            border: 2px solid var(--border);
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
            font-size: 13px;
            position: relative;
            z-index: 1;
            cursor: pointer;
            transition: var(--transition);
            font-variant-numeric: tabular-nums;
        }
        .j-node:hover { border-color: var(--text-muted); transform: scale(1.08); }
        .j-node.current { background: var(--text); border-color: var(--text); color: white; }
        .j-node.completed { background: var(--accent-5); border-color: var(--accent-5); color: white; }
        .j-label {
            position: absolute;
            top: 64px;
            left: 50%;
            transform: translateX(-50%);
            font-size: 11px;
            color: var(--text-muted);
            white-space: nowrap;
            font-weight: 500;
        }

        /* Cornell */
        .cornell-grid {
            display: grid;
            grid-template-columns: 200px 1fr;
            gap: 0;
            border: 1px solid var(--border);
            border-radius: var(--radius-sm);
            overflow: hidden;
            min-height: 400px;
        }
        .cornell-cues {
            border-right: 1px solid var(--border);
            background: var(--bg-warm);
            padding: 20px;
        }
        .cornell-notes { padding: 20px; }
        .cornell-summary {
            grid-column: 1 / -1;
            border-top: 1px solid var(--border);
            padding: 20px;
            background: var(--bg-warm);
        }
        .cornell-textarea {
            width: 100%;
            height: 100%;
            background: transparent;
            border: none;
            color: var(--text);
            font-family: inherit;
            font-size: 15px;
            line-height: 1.7;
            resize: none;
            outline: none;
            min-height: 300px;
        }
        .cornell-textarea::placeholder { color: var(--text-muted); }

        /* Feynman steps */
        .feynman-steps {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 12px;
            margin: 24px 0;
        }
        .feynman-step {
            background: var(--bg);
            border: 1px solid var(--border);
            border-radius: var(--radius-sm);
            padding: 20px;
            text-align: center;
            transition: var(--transition);
            cursor: pointer;
        }
        .feynman-step:hover { border-color: var(--text-muted); }
        .feynman-step.active {
            background: var(--text);
            border-color: var(--text);
            color: white;
        }
        .feynman-step-num {
            width: 32px;
            height: 32px;
            border-radius: 50%;
            background: var(--border);
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
            font-size: 14px;
            margin: 0 auto 12px;
        }
        .feynman-step.active .feynman-step-num { background: rgba(255,255,255,0.2); }
        .feynman-step-title { font-size: 14px; font-weight: 700; margin-bottom: 4px; }
        .feynman-step-desc { font-size: 12px; opacity: 0.7; }

        /* Blank page */
        .blank-area {
            background: var(--bg);
            border: 2px dashed var(--border);
            border-radius: var(--radius);
            padding: 48px;
            text-align: center;
            min-height: 300px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            transition: var(--transition);
        }
        .blank-area:hover { border-color: var(--text-muted); }
        .blank-area.writing { border-style: solid; border-color: var(--text); background: var(--bg-card); }

        /* Interleave */
        .week-grid {
            display: grid;
            grid-template-columns: repeat(7, 1fr);
            gap: 8px;
            margin: 20px 0;
        }
        .week-day {
            background: var(--bg);
            border: 1px solid var(--border);
            border-radius: var(--radius-sm);
            padding: 12px;
            min-height: 140px;
        }
        .week-day-header {
            font-size: 11px;
            font-weight: 700;
            color: var(--text-muted);
            text-align: center;
            margin-bottom: 10px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }
        .week-slot {
            background: var(--bg-card);
            border-radius: 6px;
            padding: 6px 8px;
            font-size: 11px;
            margin-bottom: 4px;
            border: 1px solid var(--border-light);
            cursor: pointer;
            transition: var(--transition);
            font-weight: 500;
        }
        .week-slot:hover { background: var(--text); color: white; border-color: var(--text); }

        /* SR cards */
        .sr-list-item {
            background: var(--bg);
            border: 1px solid var(--border);
            border-radius: var(--radius-sm);
            padding: 16px 20px;
            margin-bottom: 10px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            transition: var(--transition);
            cursor: pointer;
        }
        .sr-list-item:hover { border-color: var(--text-muted); }
        .sr-info h4 { font-size: 15px; font-weight: 600; margin-bottom: 2px; }
        .sr-info p { font-size: 13px; color: var(--text-muted); }
        .sr-badge {
            font-size: 11px;
            font-weight: 700;
            padding: 4px 10px;
            border-radius: 12px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }
        .sr-now { background: var(--accent-soft); color: var(--accent); }
        .sr-soon { background: var(--accent-4-soft); color: var(--accent-4); }
        .sr-later { background: var(--accent-5-soft); color: var(--accent-5); }

        /* Review card */
        .review-card {
            background: var(--bg);
            border-radius: var(--radius);
            padding: 40px;
            text-align: center;
            min-height: 200px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            margin-bottom: 24px;
        }
        .review-front { font-size: 22px; font-weight: 700; margin-bottom: 20px; }
        .review-back {
            display: none;
            margin-top: 20px;
            padding-top: 20px;
            border-top: 1px solid var(--border);
            color: var(--text-secondary);
            font-size: 17px;
            line-height: 1.7;
        }
        .review-rating {
            display: flex;
            justify-content: center;
            gap: 10px;
            flex-wrap: wrap;
        }
        .rating-btn {
            padding: 10px 20px;
            border-radius: 20px;
            border: 1px solid var(--border);
            background: var(--bg-card);
            font-family: inherit;
            font-size: 13px;
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition);
        }
        .rating-btn:hover { transform: translateY(-2px); }
        .rating-again { color: var(--accent); border-color: var(--accent); }
        .rating-again:hover { background: var(--accent-soft); }
        .rating-hard { color: var(--accent-4); border-color: var(--accent-4); }
        .rating-hard:hover { background: var(--accent-4-soft); }
        .rating-good { color: var(--accent-5); border-color: var(--accent-5); }
        .rating-good:hover { background: var(--accent-5-soft); }
        .rating-easy { color: var(--accent-3); border-color: var(--accent-3); }
        .rating-easy:hover { background: var(--accent-3-soft); }

        /* Checklist */
        .checklist-item {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 10px 0;
            border-bottom: 1px solid var(--border-light);
            font-size: 14px;
        }
        .checklist-item:last-child { border-bottom: none; }
        .check-box {
            width: 20px;
            height: 20px;
            border: 2px solid var(--border);
            border-radius: 5px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: var(--transition);
            flex-shrink: 0;
            font-size: 12px;
            color: white;
        }
        .check-box:hover { border-color: var(--text-muted); }
        .check-box.checked { background: var(--accent-5); border-color: var(--accent-5); }

        /* Time bar */
        .time-bar {
            height: 4px;
            background: var(--border);
            border-radius: 2px;
            overflow: hidden;
            margin: 8px 0;
        }
        .time-fill {
            height: 100%;
            border-radius: 2px;
            transition: width 1s linear, background 0.3s;
        }
        .time-good { background: var(--accent-5); }
        .time-warn { background: var(--accent-4); }
        .time-danger { background: var(--accent); }

        /* Log */
        .log-entry {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 10px 0;
            border-bottom: 1px solid var(--border-light);
            font-size: 14px;
        }
        .log-entry:last-child { border-bottom: none; }
        .log-time { font-size: 12px; color: var(--text-muted); font-weight: 500; min-width: 50px; }
        .log-dot { width: 8px; height: 8px; border-radius: 50%; flex-shrink: 0; }
        .log-content { flex: 1; }
        .log-duration { font-size: 12px; color: var(--text-muted); font-weight: 500; }

        /* Stats */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 16px;
            margin: 24px 0;
        }
        .stat-box {
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: var(--radius);
            padding: 24px;
            text-align: center;
        }
        .stat-num {
            font-size: 36px;
            font-weight: 800;
            letter-spacing: -1px;
            margin-bottom: 4px;
        }
        .stat-label { font-size: 13px; color: var(--text-muted); font-weight: 500; }

        /* Bar chart */
        .bar-chart { display: flex; align-items: flex-end; gap: 16px; padding: 20px 0; height: 200px; }
        .bar-item { flex: 1; text-align: center; display: flex; flex-direction: column; align-items: center; }
        .bar-fill {
            width: 100%;
            border-radius: 6px 6px 0 0;
            transition: height 0.5s ease;
            min-height: 4px;
        }
        .bar-label { font-size: 12px; color: var(--text-muted); margin-top: 8px; font-weight: 500; }
        .bar-value { font-size: 14px; font-weight: 700; margin-top: 2px; }

        /* Progress bars */
        .progress-row { margin-bottom: 20px; }
        .progress-header { display: flex; justify-content: space-between; margin-bottom: 6px; font-size: 13px; }
        .progress-header span:first-child { font-weight: 600; }
        .progress-header span:last-child { color: var(--text-muted); }
        .progress-track {
            height: 8px;
            background: var(--border);
            border-radius: 4px;
            overflow: hidden;
        }
        .progress-fill {
            height: 100%;
            border-radius: 4px;
            transition: width 0.5s ease;
        }

        /* Footer */
        .footer {
            border-top: 1px solid var(--border-light);
            padding: 48px 0;
            margin-top: 64px;
            text-align: center;
        }
        .footer p {
            font-size: 14px;
            color: var(--text-muted);
            max-width: 500px;
            margin: 0 auto 24px;
            line-height: 1.6;
        }
        .footer-links {
            display: flex;
            justify-content: center;
            gap: 24px;
            font-size: 13px;
        }
        .footer-links a {
            color: var(--text-secondary);
            text-decoration: none;
            font-weight: 500;
            transition: var(--transition);
        }
        .footer-links a:hover { color: var(--text); }

        /* Toast */
        .toast {
            position: fixed;
            bottom: 24px;
            right: 24px;
            background: var(--text);
            color: white;
            padding: 14px 22px;
            border-radius: var(--radius-sm);
            font-size: 14px;
            font-weight: 500;
            z-index: 1000;
            transform: translateY(100px);
            opacity: 0;
            transition: all 0.3s ease;
            box-shadow: var(--shadow-lg);
        }
        .toast.show { transform: translateY(0); opacity: 1; }

        /* Modal */
        .modal-overlay {
            position: fixed;
            top: 0; left: 0; right: 0; bottom: 0;
            background: rgba(0,0,0,0.3);
            backdrop-filter: blur(4px);
            z-index: 1000;
            display: none;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }
        .modal-overlay.active { display: flex; }
        .modal {
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: var(--radius);
            padding: 32px;
            max-width: 480px;
            width: 100%;
            max-height: 80vh;
            overflow-y: auto;
            box-shadow: var(--shadow-lg);
        }
        .modal h3 { font-size: 20px; font-weight: 700; margin-bottom: 12px; }
        .modal p { font-size: 15px; color: var(--text-secondary); line-height: 1.6; margin-bottom: 24px; }

        /* Responsive */
        @media (max-width: 768px) {
            .nav-links { display: none; }
            .hero h1 { font-size: 32px; }
            .hero p { font-size: 16px; }
            .cards-grid { grid-template-columns: 1fr; }
            .feynman-steps { grid-template-columns: repeat(2, 1fr); }
            .week-grid { grid-template-columns: repeat(3, 1fr); }
            .cornell-grid { grid-template-columns: 1fr; }
            .cornell-cues { border-right: none; border-bottom: 1px solid var(--border); }
            .j-timeline { overflow-x: auto; gap: 16px; padding-bottom: 40px; }
            .j-timeline::before { display: none; }
            .timer-display { font-size: 56px; }
        }

        .hidden { display: none !important; }
    </style>
<base target="_blank">
</head>
<body>

    <!-- Nav -->
    <nav class="nav">
        <div class="container nav-inner">
            <a class="nav-logo" onclick="showPage('home')">
                <div class="nav-logo-icon">N</div>
                NOESIS
            </a>
            <div class="nav-links">
                <button class="nav-link active" onclick="showPage('home')">Accueil</button>
                <button class="nav-link" onclick="showPage('pomodoro')">Pomodoro</button>
                <button class="nav-link" onclick="showPage('jmethod')">Méthode des J</button>
                <button class="nav-link" onclick="showPage('feynman')">Feynman</button>
                <button class="nav-link" onclick="showPage('blankpage')">Feuille Blanche</button>
                <button class="nav-link" onclick="showPage('cornell')">Cornell</button>
                <button class="nav-link" onclick="showPage('spaced')">Flashcards</button>
                <button class="nav-link" onclick="showPage('subjects')">Sujets</button>
            </div>
            <button class="nav-cta" onclick="quickStart()">Démarrer</button>
        </div>
    </nav>

    <!-- HOME -->
    <div id="home" class="page-section active">
        <div class="container">
            <div class="hero">
                <svg class="hero-illustration" viewBox="0 0 400 300" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <rect x="50" y="80" width="120" height="140" rx="12" fill="#f5f5f0" stroke="#1c1917" stroke-width="2"/>
                    <rect x="70" y="100" width="80" height="8" rx="4" fill="#a8a29e"/>
                    <rect x="70" y="120" width="60" height="6" rx="3" fill="#d6d3d1"/>
                    <rect x="70" y="134" width="70" height="6" rx="3" fill="#d6d3d1"/>
                    <rect x="70" y="148" width="50" height="6" rx="3" fill="#d6d3d1"/>
                    <circle cx="110" cy="190" r="16" fill="#dc2626" opacity="0.15"/>
                    <path d="M102 190 L108 196 L118 184" stroke="#dc2626" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"/>
                    <rect x="230" y="60" width="120" height="160" rx="12" fill="#ffffff" stroke="#1c1917" stroke-width="2"/>
                    <rect x="250" y="80" width="80" height="8" rx="4" fill="#a8a29e"/>
                    <rect x="250" y="100" width="60" height="6" rx="3" fill="#d6d3d1"/>
                    <rect x="250" y="114" width="70" height="6" rx="3" fill="#d6d3d1"/>
                    <rect x="250" y="128" width="50" height="6" rx="3" fill="#d6d3d1"/>
                    <rect x="250" y="142" width="65" height="6" rx="3" fill="#d6d3d1"/>
                    <circle cx="290" cy="180" r="20" fill="#059669" opacity="0.15"/>
                    <path d="M280 180 L286 186 L300 172" stroke="#059669" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"/>
                    <path d="M180 140 Q200 120 220 140" stroke="#1c1917" stroke-width="2" fill="none" stroke-linecap="round"/>
                    <polygon points="215,135 220,140 215,145" fill="#1c1917"/>
                    <circle cx="200" cy="200" r="30" fill="#f5f5f0" stroke="#1c1917" stroke-width="2"/>
                    <text x="200" y="208" text-anchor="middle" font-size="20" font-weight="700" fill="#1c1917">?</text>
                </svg>
                <h1>Apprendre à apprendre,<br>ensemble.</h1>
                <p>Nous explorons les méthodes d'étude les plus efficaces, validées par la recherche scientifique, pour aider les étudiants en sciences à construire des connaissances durables.</p>
                <button class="hero-cta" onclick="showPage('pomodoro')">▶ Commencer une session</button>
            </div>
        </div>

        <!-- Temporal Methods -->
        <div class="category-section">
            <div class="container">
                <div class="category-header">
                    <div class="category-icon" style="background: var(--accent-soft);">⏱</div>
                    <div>
                        <div class="section-title">Méthodes Temporelles</div>
                        <h2 class="section-heading">Gérez votre temps et votre planning</h2>
                        <p class="section-desc">Des techniques éprouvées pour structurer vos sessions d'étude et optimiser la rétention à long terme.</p>
                    </div>
                </div>
                <div class="cards-grid">
                    <div class="card" onclick="showPage('pomodoro')">
                        <div class="card-icon" style="background: var(--accent-soft);">🍅</div>
                        <h3>Pomodoro</h3>
                        <p>Cycles de 25 minutes de concentration suivis de pauses courtes. Idéal pour les problèmes scientifiques complexes.</p>
                        <div class="card-meta">
                            <span>🇮🇹 Italie</span>
                            <span>25 min</span>
                            <span>Focus</span>
                        </div>
                    </div>
                    <div class="card" onclick="showPage('jmethod')">
                        <div class="card-icon" style="background: var(--accent-5-soft);">📅</div>
                        <h3>Méthode des J</h3>
                        <p>Révisions planifiées aux jours J0, J1, J3, J7, J15, J30. Basée sur la courbe de l'oubli d'Ebbinghaus.</p>
                        <div class="card-meta">
                            <span>🇫🇷 France</span>
                            <span>30 jours</span>
                            <span>Mémoire</span>
                        </div>
                    </div>
                    <div class="card" onclick="showPage('interleaving')">
                        <div class="card-icon" style="background: var(--accent-3-soft);">🔄</div>
                        <h3>Entrelacement</h3>
                        <p>Alternez entre différents sujets ou types de problèmes. Améliore la discrimination et le transfert.</p>
                        <div class="card-meta">
                            <span>🌍 International</span>
                            <span>Session</span>
                            <span>Adaptation</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Cognitive Methods -->
        <div class="category-section">
            <div class="container">
                <div class="category-header">
                    <div class="category-icon" style="background: var(--accent-2-soft);">🧠</div>
                    <div>
                        <div class="section-title">Méthodes Cognitives</div>
                        <h2 class="section-heading">Comprendre et mémoriser en profondeur</h2>
                        <p class="section-desc">Des approches qui forcent l'apprentissage actif et la compréhension réelle plutôt que la mémorisation passive.</p>
                    </div>
                </div>
                <div class="cards-grid">
                    <div class="card" onclick="showPage('feynman')">
                        <div class="card-icon" style="background: var(--accent-3-soft);">🧠</div>
                        <h3>Technique Feynman</h3>
                        <p>Expliquez un concept simplement, comme à un enfant. Identifiez les lacunes et simplifiez davantage.</p>
                        <div class="card-meta">
                            <span>🇺🇸 USA</span>
                            <span>45 min</span>
                            <span>Compréhension</span>
                        </div>
                    </div>
                    <div class="card" onclick="showPage('blankpage')">
                        <div class="card-icon" style="background: var(--accent-4-soft);">📄</div>
                        <h3>Feuille Blanche</h3>
                        <p>Fermez vos notes et réécrivez tout ce que vous savez. Test de récupération active.</p>
                        <div class="card-meta">
                            <span>🌍 Universel</span>
                            <span>20 min</span>
                            <span>Rappel</span>
                        </div>
                    </div>
                    <div class="card" onclick="showPage('cornell')">
                        <div class="card-icon" style="background: var(--accent-2-soft);">📝</div>
                        <h3>Notes Cornell</h3>
                        <p>Divisez votre page : indices, notes, résumé. Optimisé pour les cours scientifiques.</p>
                        <div class="card-meta">
                            <span>🇺🇸 USA</span>
                            <span>Cours</span>
                            <span>Organisation</span>
                        </div>
                    </div>
                    <div class="card" onclick="showPage('spaced')">
                        <div class="card-icon" style="background: #f3e8ff;">🃏</div>
                        <h3>Répétition Espacée</h3>
                        <p>Réviser les flashcards à des intervalles croissants. Algorithme basé sur la mémoire.</p>
                        <div class="card-meta">
                            <span>🇩🇪 Allemagne</span>
                            <span>Variable</span>
                            <span>Long terme</span>
                        </div>
                    </div>
                    <div class="card" onclick="showInfo('sq3r')">
                        <div class="card-icon" style="background: var(--accent-5-soft);">📖</div>
                        <h3>SQ3R</h3>
                        <p>Survey, Question, Read, Recite, Review. Méthode de lecture active pour manuels scientifiques.</p>
                        <div class="card-meta">
                            <span>🇺🇸 USA</span>
                            <span>Lecture</span>
                            <span>Compréhension</span>
                        </div>
                    </div>
                    <div class="card" onclick="showInfo('loci')">
                        <div class="card-icon" style="background: #fce7f3;">🏛️</div>
                        <h3>Méthode des Loci</h3>
                        <p>Palais mental : associez les concepts à des lieux familiers. Technique millénaire.</p>
                        <div class="card-meta">
                            <span>🇮🇹 Italie</span>
                            <span>30 min</span>
                            <span>Mémorisation</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- About -->
        <div class="category-section">
            <div class="container-narrow" style="text-align: center;">
                <div class="section-title">Notre Mission</div>
                <h2 class="section-heading" style="font-size: 28px;">Des méthodes du monde entier, pour des étudiants en sciences.</h2>
                <p style="font-size: 16px; color: var(--text-secondary); line-height: 1.7; margin-top: 16px;">
                    NOESIS rassemble les techniques d'apprentissage les plus efficaces issues de cultures différentes : le Pomodoro italien, la méthode des J française, la technique Feynman américaine, la répétition espacée allemande, le palais mental chinois, et bien d'autres. Chaque méthode est accompagnée de ses fondements scientifiques et d'outils pratiques pour l'appliquer immédiatement.
                </p>
            </div>
        </div>

        <div class="footer">
            <div class="container-narrow">
                <p>NOESIS est un espace d'apprentissage gratuit dédié aux étudiants universitaires en sciences. Toutes les données restent sur votre appareil.</p>
                <div class="footer-links">
                    <a href="#" onclick="showPage('subjects')">Sujets</a>
                    <a href="#" onclick="showPage('pomodoro')">Pomodoro</a>
                    <a href="#" onclick="showPage('spaced')">Flashcards</a>
                    <a href="#" onclick="showPage('feynman')">Feynman</a>
                </div>
            </div>
        </div>
    </div>

    <!-- POMODORO -->
    <div id="pomodoro" class="page-section">
        <div class="container-narrow">
            <div class="tool-header">
                <h1>Pomodoro</h1>
                <p>Technique de gestion du temps par cycles concentrés. Créée par Francesco Cirillo dans les années 1980.</p>
            </div>

            <div class="tool-card">
                <div class="timer-modes">
                    <button class="timer-mode active" onclick="setTimerMode('pomodoro')">Pomodoro (25 min)</button>
                    <button class="timer-mode" onclick="setTimerMode('short')">Pause courte (5 min)</button>
                    <button class="timer-mode" onclick="setTimerMode('long')">Pause longue (15 min)</button>
                    <button class="timer-mode" onclick="setTimerMode('deep')">Deep Work (50 min)</button>
                </div>
                <div class="progress-ring-wrap">
                    <svg width="200" height="200">
                        <circle class="progress-ring-bg" cx="100" cy="100" r="92"/>
                        <circle class="progress-ring-fill" cx="100" cy="100" r="92" stroke-dasharray="578" stroke-dashoffset="0" id="progress-circle"/>
                    </svg>
                </div>
                <div class="timer-display" id="timer-display">25:00</div>
                <div class="timer-controls">
                    <button class="btn btn-primary" id="timer-toggle" onclick="toggleTimer()">▶ Démarrer</button>
                    <button class="btn" onclick="resetTimer()">↻ Réinitialiser</button>
                    <button class="btn" onclick="skipTimer()">⏭ Sauter</button>
                </div>
                <p style="text-align: center; font-size: 13px; color: var(--text-muted); margin-top: 16px;">
                    Cycle <span id="cycle-count">1</span> sur 4 • Sujet : <span id="current-subject">Non défini</span>
                </p>
            </div>

            <div class="tool-card">
                <h2>Sujet Actif</h2>
                <p class="subtitle">Sélectionnez la matière scientifique</p>
                <div class="chips" id="pomodoro-subjects"></div>
                <div class="form-group">
                    <label class="form-label">Objectif de cette session</label>
                    <input type="text" id="pomodoro-goal" placeholder="Ex: Résoudre 5 problèmes de mécanique quantique...">
                </div>
            </div>

            <div class="tool-card">
                <h2>Session Log</h2>
                <p class="subtitle">Historique de vos cycles Pomodoro</p>
                <div id="pomodoro-log">
                    <div class="log-entry">
                        <span class="log-time">--:--</span>
                        <span class="log-dot" style="background: var(--border)"></span>
                        <span class="log-content">Aucune session enregistrée aujourd'hui</span>
                        <span class="log-duration">--</span>
                    </div>
                </div>
            </div>

            <div class="tool-card">
                <h2>À propos de la technique</h2>
                <p class="subtitle">Recherche scientifique</p>
                <div style="font-size: 15px; color: var(--text-secondary); line-height: 1.7;">
                    <p style="margin-bottom: 12px;">La technique Pomodoro utilise un minuteur pour découper le travail en intervalles de 25 minutes, séparés par de courtes pauses. Chaque intervalle est appelé un <em>pomodoro</em> (italien pour "tomate").</p>
                    <p style="margin-bottom: 12px;"><strong>Étapes :</strong> 1) Choisir la tâche, 2) Régler le timer à 25 minutes, 3) Travailler jusqu'à ce que le timer sonne, 4) Prendre une pause courte (5 min), 5) Après 4 pomodoros, prendre une pause longue (15-30 min).</p>
                    <p>Une revue de 2025 a montré que les interventions Pomodoro améliorent systématiquement la concentration, réduisent la fatigue mentale et améliorent les performances soutenues.</p>
                </div>
            </div>
        </div>
    </div>

    <!-- J METHOD -->
    <div id="jmethod" class="page-section">
        <div class="container-narrow">
            <div class="tool-header">
                <h1>Méthode des J</h1>
                <p>Planification des révisions basée sur la courbe de l'oubli d'Ebbinghaus.</p>
            </div>

            <div class="tool-card">
                <h2>Timeline des Révisions</h2>
                <p class="subtitle">Rythme classique : J0 → J1 → J3 → J7 → J15 → J30</p>
                <div class="j-timeline">
                    <div class="j-node current" onclick="showJInfo(0)">J0<span class="j-label">Cours initial</span></div>
                    <div class="j-node" onclick="showJInfo(1)">J1<span class="j-label">Approfondir</span></div>
                    <div class="j-node" onclick="showJInfo(3)">J3<span class="j-label">Mémoriser</span></div>
                    <div class="j-node" onclick="showJInfo(7)">J7<span class="j-label">Rappel</span></div>
                    <div class="j-node" onclick="showJInfo(15)">J15<span class="j-label">Consolider</span></div>
                    <div class="j-node" onclick="showJInfo(30)">J30<span class="j-label">Maîtriser</span></div>
                </div>
                <div id="j-info" style="margin-top: 48px; padding: 24px; background: var(--bg-warm); border-radius: var(--radius-sm); font-size: 15px; color: var(--text-secondary); line-height: 1.7;">
                    <strong style="color: var(--text);">J0 — Cours Initial</strong><br>
                    Assistez au cours. Relisez vos notes le soir même de manière active. Ne mémorisez pas encore, mais familiarisez-vous avec les grandes lignes et les concepts clés.
                </div>
            </div>

            <div class="tool-card">
                <h2>Ajouter un Cours</h2>
                <p class="subtitle">Planifiez vos révisions automatiquement</p>
                <div class="form-group">
                    <label class="form-label">Titre du cours</label>
                    <input type="text" id="j-title" placeholder="Ex: Thermodynamique - Chapitre 3">
                </div>
                <div class="form-group">
                    <label class="form-label">Matière</label>
                    <select id="j-subject"><option>Physique</option><option>Chimie</option><option>Mathématiques</option><option>Biologie</option><option>Informatique</option><option>Autre</option></select>
                </div>
                <div class="form-group">
                    <label class="form-label">Date du cours (J0)</label>
                    <input type="date" id="j-date">
                </div>
                <div class="form-group">
                    <label class="form-label">Rythme</label>
                    <select id="j-rhythm">
                        <option value="classic">Classique (J0 J1 J3 J7 J15 J30)</option>
                        <option value="light">Léger (J0 J2 J5 J14)</option>
                        <option value="intense">Intensif (J0 J1 J2 J4 J7 J14)</option>
                    </select>
                </div>
                <button class="btn btn-primary" onclick="addJCourse()" style="width: 100%;">📅 Planifier les Révisions</button>
            </div>

            <div class="tool-card">
                <h2>Révisions à Venir</h2>
                <p class="subtitle">Vos prochaines sessions programmées</p>
                <div id="j-upcoming">
                    <div class="sr-list-item">
                        <div class="sr-info"><h4>Aucun cours planifié</h4><p>Ajoutez un cours pour commencer</p></div>
                    </div>
                </div>
            </div>

            <div class="tool-card">
                <h2>Théorie</h2>
                <p class="subtitle">Basée sur les travaux d'Hermann Ebbinghaus</p>
                <div style="font-size: 15px; color: var(--text-secondary); line-height: 1.7;">
                    <p style="margin-bottom: 12px;">La méthode des J s'inspire de la <strong>courbe de l'oubli</strong> d'Ebbinghaus. La mémoire est plus réceptive au fractionnement des séances de révision qu'aux longues sessions concentrées.</p>
                    <p style="margin-bottom: 12px;">Le principe : la "demi-vie" d'un apprentissage est d'un jour, et cette demi-vie double à chaque révision. J1 est crucial car le sommeil joue un rôle clé dans la consolidation de la mémoire.</p>
                    <p><strong>Versions :</strong> Classique, Léger, ou Intensif. J1 est particulièrement important car le sommeil consolide la mémoire.</p>
                </div>
            </div>
        </div>
    </div>

    <!-- FEYNMAN -->
    <div id="feynman" class="page-section">
        <div class="container-narrow">
            <div class="tool-header">
                <h1>Technique Feynman</h1>
                <p>Apprenez en enseignant — méthode du prix Nobel Richard Feynman.</p>
            </div>

            <div class="feynman-steps">
                <div class="feynman-step active" onclick="setFeynmanStep(1)">
                    <div class="feynman-step-num">1</div>
                    <div class="feynman-step-title">Choisir</div>
                    <div class="feynman-step-desc">Sélectionnez un concept</div>
                </div>
                <div class="feynman-step" onclick="setFeynmanStep(2)">
                    <div class="feynman-step-num">2</div>
                    <div class="feynman-step-title">Enseigner</div>
                    <div class="feynman-step-desc">Expliquez simplement</div>
                </div>
                <div class="feynman-step" onclick="setFeynmanStep(3)">
                    <div class="feynman-step-num">3</div>
                    <div class="feynman-step-title">Identifier</div>
                    <div class="feynman-step-desc">Repérez les lacunes</div>
                </div>
                <div class="feynman-step" onclick="setFeynmanStep(4)">
                    <div class="feynman-step-num">4</div>
                    <div class="feynman-step-title">Simplifier</div>
                    <div class="feynman-step-desc">Reformulez plus clairement</div>
                </div>
            </div>

            <div class="tool-card" id="feynman-content">
                <h2>Étape 1 : Choisir le Concept</h2>
                <p class="subtitle">Sélectionnez un sujet scientifique spécifique à maîtriser</p>
                <div class="form-group">
                    <label class="form-label">Concept à étudier</label>
                    <input type="text" id="feynman-concept" placeholder="Ex: Principe d'incertitude de Heisenberg...">
                </div>
                <div class="form-group">
                    <label class="form-label">Matière</label>
                    <select id="feynman-subject"><option>Physique</option><option>Chimie</option><option>Mathématiques</option><option>Biologie</option><option>Informatique</option></select>
                </div>
                <div class="form-group">
                    <label class="form-label">Votre niveau actuel</label>
                    <select id="feynman-level"><option>Débutant sur ce sujet</option><option>Connaissances de base</option><option>Intermédiaire</option><option>Avancé — besoin de perfectionner</option></select>
                </div>
                <button class="btn btn-primary" onclick="nextFeynmanStep()">Continuer →</button>
            </div>

            <div class="tool-card">
                <h2>Conseils de Richard Feynman</h2>
                <p class="subtitle">"The first principle is that you must not fool yourself"</p>
                <div style="font-size: 15px; color: var(--text-secondary); line-height: 1.7;">
                    <p style="margin-bottom: 12px;"><em>"What I cannot create, I do not understand."</em> — Richard Feynman</p>
                    <p style="margin-bottom: 12px;">La technique Feynman repose sur un principe puissant : <strong>si vous ne pouvez pas l'expliquer simplement, vous ne le comprenez pas assez bien</strong>.</p>
                    <p>Cette méthode force l'apprentissage actif, supprime la mémorisation passive, et pousse à explorer les sujets en profondeur. Particulièrement efficace pour les concepts scientifiques complexes.</p>
                </div>
            </div>

            <div class="tool-card">
                <h2>Sessions Feynman</h2>
                <p class="subtitle">Historique de vos explications</p>
                <div id="feynman-sessions">
                    <div class="checklist-item">
                        <div class="check-box"></div>
                        <span style="color: var(--text-muted);">Aucune session enregistrée</span>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- BLANK PAGE -->
    <div id="blankpage" class="page-section">
        <div class="container-narrow">
            <div class="tool-header">
                <h1>Technique de la Feuille Blanche</h1>
                <p>Récupération active — testez votre mémoire sans aide.</p>
            </div>

            <div class="tool-card">
                <h2>Configuration</h2>
                <p class="subtitle">Définissez vos paramètres de session</p>
                <div class="form-group">
                    <label class="form-label">Sujet à réviser</label>
                    <input type="text" id="bp-subject" placeholder="Ex: Mécanique des fluides">
                </div>
                <div class="form-group">
                    <label class="form-label">Temps limité (minutes)</label>
                    <input type="number" id="bp-time" value="20" min="5" max="60">
                </div>
                <div class="form-group">
                    <label class="form-label">Niveau de difficulté</label>
                    <select id="bp-difficulty">
                        <option>Basique — Définitions et concepts</option>
                        <option>Intermédiaire — Formules et applications</option>
                        <option>Avancé — Démonstrations et problèmes</option>
                    </select>
                </div>
                <button class="btn btn-primary" onclick="startBlankPage()" style="width: 100%;">🚀 Démarrer la Session</button>
            </div>

            <div class="tool-card">
                <h2>Instructions</h2>
                <p class="subtitle">Comment utiliser cette technique</p>
                <div class="checklist-item"><div class="check-box checked">✓</div><span>Fermez tous vos livres et notes</span></div>
                <div class="checklist-item"><div class="check-box checked">✓</div><span>Prenez une feuille vierge</span></div>
                <div class="checklist-item"><div class="check-box">✓</div><span>Réécrivez TOUT ce que vous savez</span></div>
                <div class="checklist-item"><div class="check-box">✓</div><span>Ne vous arrêtez pas avant la fin du temps</span></div>
                <div class="checklist-item"><div class="check-box">✓</div><span>Vérifiez ensuite avec vos notes</span></div>
                <div class="checklist-item"><div class="check-box">✓</div><span>Identifiez les lacunes et révisez</span></div>
            </div>

            <div class="tool-card" id="bp-session" style="display: none;">
                <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 16px;">
                    <h2 style="margin: 0;">Session Active</h2>
                    <button class="btn btn-danger btn-sm" onclick="stopBlankPage()">Arrêter</button>
                </div>
                <p class="subtitle" id="bp-timer-display">Temps restant: 20:00</p>
                <div class="time-bar"><div class="time-fill time-good" id="bp-progress" style="width: 100%"></div></div>
                <textarea id="bp-textarea" class="cornell-textarea" style="min-height: 300px; margin-top: 16px; background: var(--bg-warm); border-radius: var(--radius-sm); padding: 20px; border: 1px solid var(--border);" placeholder="Écrivez tout ce que vous savez sur le sujet... Ne regardez PAS vos notes !"></textarea>
            </div>

            <div class="tool-card">
                <h2>Science de la Récupération Active</h2>
                <p class="subtitle">Pourquoi la feuille blanche fonctionne</p>
                <div style="font-size: 15px; color: var(--text-secondary); line-height: 1.7;">
                    <p style="margin-bottom: 12px;">La <strong>récupération active</strong> est l'une des techniques les plus efficaces selon la recherche cognitive. Lire et surligner sont des méthodes passives peu efficaces.</p>
                    <p style="margin-bottom: 12px;">En forçant votre cerveau à récupérer l'information sans aide, vous renforcez les connexions neuronales. C'est l'équivalent d'un test pour votre mémoire.</p>
                    <p>Des études montrent que tester sa mémoire améliore la rétention bien plus que relire le même matériel. La difficulté désirable de cette tâche renforce l'apprentissage.</p>
                </div>
            </div>
        </div>
    </div>

    <!-- CORNELL -->
    <div id="cornell" class="page-section">
        <div class="container-narrow">
            <div class="tool-header">
                <h1>Notes Cornell</h1>
                <p>Système de prise de notes développé à l'Université Cornell.</p>
            </div>

            <div class="tool-card">
                <div style="display: flex; justify-content: space-between; align-items: flex-start; margin-bottom: 20px;">
                    <div>
                        <h2>Nouvelle Page Cornell</h2>
                        <p class="subtitle">Divisez votre page en trois sections</p>
                    </div>
                    <div style="display: flex; gap: 8px;">
                        <button class="btn btn-sm" onclick="clearCornell()">🗑 Effacer</button>
                        <button class="btn btn-primary btn-sm" onclick="saveCornell()">💾 Sauvegarder</button>
                    </div>
                </div>
                <div class="form-group">
                    <input type="text" id="cornell-title" placeholder="Titre du cours / sujet..." style="font-weight: 700; font-size: 17px;">
                </div>
                <div class="cornell-grid">
                    <div class="cornell-cues">
                        <div style="font-size: 11px; font-weight: 700; color: var(--text-muted); margin-bottom: 10px; text-transform: uppercase; letter-spacing: 0.5px;">Colonne d'Indices</div>
                        <textarea class="cornell-textarea" id="cornell-cues" placeholder="Mots-clés&#10;Questions&#10;Indices de rappel&#10;..." style="min-height: 300px;"></textarea>
                    </div>
                    <div class="cornell-notes">
                        <div style="font-size: 11px; font-weight: 700; color: var(--text-muted); margin-bottom: 10px; text-transform: uppercase; letter-spacing: 0.5px;">Zone de Notes</div>
                        <textarea class="cornell-textarea" id="cornell-notes" placeholder="Vos notes de cours détaillées...&#10;&#10;• Points clés&#10;• Formules&#10;• Explications&#10;• Exemples" style="min-height: 300px;"></textarea>
                    </div>
                    <div class="cornell-summary">
                        <div style="font-size: 11px; font-weight: 700; color: var(--text-muted); margin-bottom: 10px; text-transform: uppercase; letter-spacing: 0.5px;">Résumé (2-3 phrases)</div>
                        <textarea class="cornell-textarea" id="cornell-summary" placeholder="Résumez les idées principales de cette page..." style="min-height: 60px;"></textarea>
                    </div>
                </div>
            </div>

            <div class="tool-card">
                <h2>Notes Sauvegardées</h2>
                <p class="subtitle">Vos pages Cornell récentes</p>
                <div id="cornell-saved">
                    <div class="sr-list-item">
                        <div class="sr-info"><h4>Aucune note sauvegardée</h4><p>Créez votre première page Cornell</p></div>
                    </div>
                </div>
            </div>

            <div class="tool-card">
                <h2>Guide Cornell</h2>
                <p class="subtitle">Inventé par Walter Pauk dans les années 1950</p>
                <div style="font-size: 15px; color: var(--text-secondary); line-height: 1.7;">
                    <p style="margin-bottom: 12px;"><strong>Colonne d'indices (gauche, 6cm) :</strong> Mots-clés, questions, indices de rappel. Utilisez-la pour vous auto-questionner.</p>
                    <p style="margin-bottom: 12px;"><strong>Zone de notes (droite) :</strong> Notes détaillées pendant le cours. Soyez sélectif, pas transcriptif.</p>
                    <p style="margin-bottom: 12px;"><strong>Résumé (bas, 5cm) :</strong> Synthèse des idées principales. Rédigez-le après le cours.</p>
                    <p><strong>Pour réviser :</strong> Couvrez la zone de notes, utilisez les indices pour réciter le contenu, vérifiez, puis lisez le résumé.</p>
                </div>
            </div>
        </div>
    </div>

    <!-- SPACED REPETITION -->
    <div id="spaced" class="page-section">
        <div class="container-narrow">
            <div class="tool-header">
                <h1>Répétition Espacée</h1>
                <p>Système de flashcards avec algorithme optimisé.</p>
            </div>

            <div class="tool-card">
                <h2>Nouvelle Flashcard</h2>
                <p class="subtitle">Créez une carte de révision</p>
                <div class="form-group">
                    <label class="form-label">Recto (Question / Concept)</label>
                    <textarea id="sr-front" rows="3" placeholder="Quelle est l'équation de Schrödinger indépendante du temps ?"></textarea>
                </div>
                <div class="form-group">
                    <label class="form-label">Verso (Réponse / Explication)</label>
                    <textarea id="sr-back" rows="3" placeholder="Ĥψ = Eψ&#10;Où Ĥ est l'opérateur hamiltonien..."></textarea>
                </div>
                <div class="form-group">
                    <label class="form-label">Matière</label>
                    <select id="sr-subject"><option>Physique</option><option>Chimie</option><option>Mathématiques</option><option>Biologie</option><option>Informatique</option></select>
                </div>
                <div class="form-group">
                    <label class="form-label">Difficulté estimée</label>
                    <select id="sr-difficulty">
                        <option value="easy">Facile — Définition simple</option>
                        <option value="medium">Moyen — Concept à comprendre</option>
                        <option value="hard">Difficile — Formule / Démonstration</option>
                    </select>
                </div>
                <button class="btn btn-primary" onclick="addFlashcard()" style="width: 100%;">➕ Ajouter la Carte</button>
            </div>

            <div class="tool-card">
                <h2>Cartes à Réviser</h2>
                <p class="subtitle" id="sr-count">0 cartes en attente</p>
                <div id="sr-list">
                    <div class="sr-list-item">
                        <div class="sr-info"><h4>Aucune carte à réviser</h4><p>Ajoutez des flashcards pour commencer</p></div>
                    </div>
                </div>
            </div>

            <div class="tool-card" id="sr-review" style="display: none;">
                <h2>Révision en Cours</h2>
                <p class="subtitle">Évaluez votre réponse honnêtement</p>
                <div class="review-card">
                    <div class="review-front" id="sr-review-front"></div>
                    <button class="btn" onclick="showSrAnswer()" id="sr-show-btn">Afficher la Réponse</button>
                    <div class="review-back" id="sr-review-back"></div>
                </div>
                <div class="review-rating" id="sr-rating" style="display: none;">
                    <button class="rating-btn rating-again" onclick="rateCard('again')">🔴 Encore (1 min)</button>
                    <button class="rating-btn rating-hard" onclick="rateCard('hard')">🟠 Difficile (6 min)</button>
                    <button class="rating-btn rating-good" onclick="rateCard('good')">🟢 Bon (10 min)</button>
                    <button class="rating-btn rating-easy" onclick="rateCard('easy')">🔵 Facile (4 j)</button>
                </div>
            </div>

            <div class="tool-card">
                <h2>Algorithme de Répétition Espacée</h2>
                <p class="subtitle">Basé sur la courbe de l'oubli et le système de Leitner</p>
                <div style="font-size: 15px; color: var(--text-secondary); line-height: 1.7;">
                    <p style="margin-bottom: 12px;">La <strong>répétition espacée</strong> exploite l'effet d'espacement : réviser à des intervalles croissants améliore la rétention à long terme bien plus que la répétition en masse (cramming).</p>
                    <p style="margin-bottom: 12px;"><strong>Intervalles :</strong> Encore (1 min), Difficile (6 min), Bon (10 min), Facile (4 j). Les intervalles doublent à chaque réussite.</p>
                    <p>Rohrer, Dedrick et Burgess (2014) ont montré que l'entrelacement double presque les scores sur un test. Kornell et Bjork (2008) ont démontré que l'entrelacement améliore l'apprentissage inductif.</p>
                </div>
            </div>
        </div>
    </div>

    <!-- INTERLEAVING -->
    <div id="interleaving" class="page-section">
        <div class="container-narrow">
            <div class="tool-header">
                <h1>Entrelacement</h1>
                <p>Alternez les sujets pour une meilleure discrimination et rétention.</p>
            </div>

            <div class="tool-card">
                <h2>Planificateur Hebdomadaire</h2>
                <p class="subtitle">Alternez vos matières scientifiques</p>
                <div class="week-grid">
                    <div class="week-day"><div class="week-day-header">Lundi</div><div id="mon-slots"></div></div>
                    <div class="week-day"><div class="week-day-header">Mardi</div><div id="tue-slots"></div></div>
                    <div class="week-day"><div class="week-day-header">Mercredi</div><div id="wed-slots"></div></div>
                    <div class="week-day"><div class="week-day-header">Jeudi</div><div id="thu-slots"></div></div>
                    <div class="week-day"><div class="week-day-header">Vendredi</div><div id="fri-slots"></div></div>
                    <div class="week-day"><div class="week-day-header">Samedi</div><div id="sat-slots"></div></div>
                    <div class="week-day"><div class="week-day-header">Dimanche</div><div id="sun-slots"></div></div>
                </div>
                <div style="margin-top: 20px; display: flex; gap: 10px;">
                    <button class="btn btn-primary" onclick="generateInterleave()">🔄 Générer un Planning</button>
                    <button class="btn" onclick="clearInterleave()">Effacer</button>
                </div>
            </div>

            <div class="tool-card">
                <h2>Sujets à Alterner</h2>
                <p class="subtitle">Sélectionnez vos matières scientifiques</p>
                <div class="chips" id="interleave-subjects"></div>
                <div class="form-group" style="margin-top: 16px;">
                    <label class="form-label">Durée par bloc (minutes)</label>
                    <input type="number" id="interleave-block" value="30" min="15" max="60">
                </div>
            </div>

            <div class="tool-card">
                <h2>Pourquoi l'Entrelacement ?</h2>
                <p class="subtitle">Recherche scientifique</p>
                <div style="font-size: 15px; color: var(--text-secondary); line-height: 1.7;">
                    <p style="margin-bottom: 12px;">L'entrelacement consiste à mélanger différents sujets ou types de problèmes pendant une session d'étude, plutôt que de se concentrer sur un seul sujet à la fois (pratique bloquée).</p>
                    <p style="margin-bottom: 12px;"><strong>Avantages :</strong> Meilleure discrimination entre concepts similaires, pratique espacée naturelle, difficulté désirable, et meilleur transfert des connaissances.</p>
                    <p><strong>Exemple scientifique :</strong> Au lieu de résoudre 20 problèmes d'algèbre puis 20 de géométrie, alternez les types. Cela force votre cerveau à identifier LA bonne stratégie pour CHAQUE problème.</p>
                </div>
            </div>
        </div>
    </div>

    <!-- SUBJECTS -->
    <div id="subjects" class="page-section">
        <div class="container-narrow">
            <div class="tool-header">
                <h1>Cours & Sujets</h1>
                <p>Gérez vos matières scientifiques.</p>
            </div>

            <div class="tool-card">
                <h2>Sujets Scientifiques</h2>
                <p class="subtitle">Activez les matières que vous étudiez</p>
                <div class="chips" id="subjects-all"></div>
            </div>

            <div class="tool-card">
                <h2>Ajouter un Sujet Personnalisé</h2>
                <p class="subtitle">Créez votre propre matière</p>
                <div class="form-group">
                    <label class="form-label">Nom du sujet</label>
                    <input type="text" id="custom-subject" placeholder="Ex: Astrophysique, Biologie moléculaire...">
                </div>
                <div class="form-group">
                    <label class="form-label">Couleur</label>
                    <select id="custom-color">
                        <option value="indigo">Indigo</option>
                        <option value="purple">Violet</option>
                        <option value="cyan">Cyan</option>
                        <option value="emerald">Émeraude</option>
                        <option value="amber">Ambre</option>
                        <option value="rose">Rose</option>
                    </select>
                </div>
                <button class="btn btn-primary" onclick="addCustomSubject()" style="width: 100%;">➕ Ajouter</button>
            </div>

            <div class="tool-card">
                <h2>Sujets Actifs</h2>
                <p class="subtitle">Vue d'ensemble de vos matières</p>
                <div id="subjects-active-list">
                    <div class="sr-list-item">
                        <div class="sr-info"><h4>Aucun sujet sélectionné</h4><p>Activez au moins un sujet pour commencer</p></div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Toast -->
    <div class="toast" id="toast"></div>

    <!-- Modal -->
    <div class="modal-overlay" id="modal">
        <div class="modal">
            <h3 id="modal-title">Titre</h3>
            <p id="modal-body">Contenu</p>
            <button class="btn btn-primary" onclick="closeModal()">Fermer</button>
        </div>
    </div>

    <script>
        // ==================== DATA ====================
        const defaultSubjects = [
            { id: 'physics', name: 'Physique', active: true },
            { id: 'chemistry', name: 'Chimie', active: true },
            { id: 'math', name: 'Mathématiques', active: true },
            { id: 'biology', name: 'Biologie', active: false },
            { id: 'cs', name: 'Informatique', active: false },
            { id: 'astro', name: 'Astrophysique', active: false },
            { id: 'geo', name: 'Géologie', active: false },
            { id: 'stat', name: 'Statistiques', active: false },
        ];

        let subjects = JSON.parse(localStorage.getItem('noesis_subjects')) || [...defaultSubjects];
        let timerInterval = null, timerSeconds = 25 * 60, timerRunning = false, timerMode = 'pomodoro', cycleCount = 1;
        let pomodoroLog = JSON.parse(localStorage.getItem('noesis_pomodoro_log')) || [];
        let jCourses = JSON.parse(localStorage.getItem('noesis_j_courses')) || [];
        let flashcards = JSON.parse(localStorage.getItem('noesis_flashcards')) || [];
        let cornellNotes = JSON.parse(localStorage.getItem('noesis_cornell')) || [];
        let feynmanSessions = JSON.parse(localStorage.getItem('noesis_feynman')) || [];
        let currentSrIndex = 0, currentReviewCard = null;
        let bpTimerInterval = null, bpSeconds = 0;
        let selectedInterleave = [];
        let feynmanStep = 1;
        let currentPomodoroSubject = 'Non défini';

        const timerSettings = { pomodoro: 25, short: 5, long: 15, deep: 50 };

        // ==================== NAVIGATION ====================
        function showPage(id) {
            document.querySelectorAll('.page-section').forEach(s => s.classList.remove('active'));
            document.getElementById(id).classList.add('active');
            document.querySelectorAll('.nav-link').forEach(n => n.classList.remove('active'));
            document.querySelectorAll('.nav-link').forEach(n => {
                if (n.textContent.toLowerCase().includes(id === 'home' ? 'accueil' : id === 'jmethod' ? 'méthode' : id === 'blankpage' ? 'feuille' : id === 'spaced' ? 'flashcards' : id === 'interleaving' ? 'entrelacement' : id)) {
                    n.classList.add('active');
                }
            });
            window.scrollTo(0, 0);
            if (id === 'subjects') renderSubjects();
            if (id === 'pomodoro') renderPomodoroSubjects();
            if (id === 'interleaving') renderInterleaveSubjects();
        }

        function quickStart() { showPage('pomodoro'); }

        // ==================== SUBJECTS ====================
        function renderSubjects() {
            const container = document.getElementById('subjects-all');
            container.innerHTML = subjects.map(s => `
                <button class="chip ${s.active ? 'active' : ''}" onclick="toggleSubject('${s.id}')">${s.name}</button>
            `).join('');

            const activeList = document.getElementById('subjects-active-list');
            const active = subjects.filter(s => s.active);
            if (active.length === 0) {
                activeList.innerHTML = `<div class="sr-list-item"><div class="sr-info"><h4>Aucun sujet sélectionné</h4><p>Activez au moins un sujet pour commencer</p></div></div>`;
            } else {
                activeList.innerHTML = active.map(s => `
                    <div class="sr-list-item"><div class="sr-info"><h4>${s.name}</h4><p>En cours d'étude</p></div><span class="sr-badge sr-now">Actif</span></div>
                `).join('');
            }
        }

        function renderPomodoroSubjects() {
            const container = document.getElementById('pomodoro-subjects');
            const active = subjects.filter(s => s.active);
            container.innerHTML = active.map(s => `
                <button class="chip" onclick="selectPomodoroSubject('${s.name}')">${s.name}</button>
            `).join('') || '<span style="color: var(--text-muted); font-size: 13px;">Activez des sujets dans Configuration</span>';
        }

        function renderInterleaveSubjects() {
            const container = document.getElementById('interleave-subjects');
            const active = subjects.filter(s => s.active);
            container.innerHTML = active.map(s => `
                <button class="chip" onclick="toggleInterleaveSubject(this, '${s.name}')">${s.name}</button>
            `).join('') || '<span style="color: var(--text-muted); font-size: 13px;">Activez des sujets dans Configuration</span>';
        }

        function toggleSubject(id) {
            const s = subjects.find(x => x.id === id);
            if (s) s.active = !s.active;
            localStorage.setItem('noesis_subjects', JSON.stringify(subjects));
            renderSubjects();
            renderPomodoroSubjects();
            renderInterleaveSubjects();
        }

        function addCustomSubject() {
            const name = document.getElementById('custom-subject').value.trim();
            if (!name) return showToast('Veuillez entrer un nom de sujet');
            subjects.push({ id: 'custom_' + Date.now(), name, active: true });
            localStorage.setItem('noesis_subjects', JSON.stringify(subjects));
            document.getElementById('custom-subject').value = '';
            renderSubjects();
            showToast('Sujet ajouté !');
        }

        function toggleInterleaveSubject(el, name) {
            el.classList.toggle('active');
            if (el.classList.contains('active')) selectedInterleave.push(name);
            else selectedInterleave = selectedInterleave.filter(n => n !== name);
        }

        function generateInterleave() {
            if (selectedInterleave.length < 2) { showToast('Sélectionnez au moins 2 sujets'); return; }
            const days = ['mon', 'tue', 'wed', 'thu', 'fri', 'sat', 'sun'];
            const blockTime = parseInt(document.getElementById('interleave-block').value) || 30;
            days.forEach(day => {
                const container = document.getElementById(day + '-slots');
                container.innerHTML = '';
                const slots = 3 + Math.floor(Math.random() * 2);
                for (let i = 0; i < slots; i++) {
                    const subject = selectedInterleave[Math.floor(Math.random() * selectedInterleave.length)];
                    const start = 8 + i * (blockTime / 60 + 0.5);
                    const startH = Math.floor(start);
                    const startM = Math.round((start - startH) * 60);
                    const timeStr = `${startH.toString().padStart(2,'0')}:${startM.toString().padStart(2,'0')}`;
                    container.innerHTML += `<div class="week-slot">${timeStr} ${subject}</div>`;
                }
            });
            showToast('Planning généré !');
        }

        function clearInterleave() {
            ['mon','tue','wed','thu','fri','sat','sun'].forEach(d => document.getElementById(d + '-slots').innerHTML = '');
            document.querySelectorAll('#interleave-subjects .chip').forEach(el => el.classList.remove('active'));
            selectedInterleave = [];
        }

        // ==================== POMODORO ====================
        function selectPomodoroSubject(name) {
            currentPomodoroSubject = name;
            document.getElementById('current-subject').textContent = name;
            document.querySelectorAll('#pomodoro-subjects .chip').forEach(el => {
                el.classList.toggle('active', el.textContent.trim() === name);
            });
        }

        function setTimerMode(mode) {
            timerMode = mode;
            timerSeconds = timerSettings[mode] * 60;
            updateTimerDisplay();
            document.querySelectorAll('.timer-mode').forEach(b => b.classList.remove('active'));
            event.target.classList.add('active');
            resetTimer();
        }

        function updateTimerDisplay() {
            const m = Math.floor(timerSeconds / 60);
            const s = timerSeconds % 60;
            document.getElementById('timer-display').textContent = `${m.toString().padStart(2,'0')}:${s.toString().padStart(2,'0')}`;
            const total = timerSettings[timerMode] * 60;
            const progress = timerSeconds / total;
            const circumference = 2 * Math.PI * 92;
            const offset = circumference * (1 - progress);
            document.getElementById('progress-circle').style.strokeDashoffset = offset;
        }

        function toggleTimer() {
            if (timerRunning) {
                clearInterval(timerInterval);
                timerRunning = false;
                document.getElementById('timer-toggle').textContent = '▶ Reprendre';
            } else {
                timerInterval = setInterval(() => {
                    if (timerSeconds > 0) { timerSeconds--; updateTimerDisplay(); }
                    else timerComplete();
                }, 1000);
                timerRunning = true;
                document.getElementById('timer-toggle').textContent = '⏸ Pause';
            }
        }

        function resetTimer() {
            clearInterval(timerInterval);
            timerRunning = false;
            timerSeconds = timerSettings[timerMode] * 60;
            updateTimerDisplay();
            document.getElementById('timer-toggle').textContent = '▶ Démarrer';
        }

        function skipTimer() { timerComplete(); }

        function timerComplete() {
            clearInterval(timerInterval);
            timerRunning = false;
            if (timerMode === 'pomodoro' || timerMode === 'deep') {
                cycleCount++;
                document.getElementById('cycle-count').textContent = cycleCount;
                const goal = document.getElementById('pomodoro-goal').value;
                pomodoroLog.push({ time: new Date().toLocaleTimeString('fr-FR', {hour:'2-digit', minute:'2-digit'}), subject: currentPomodoroSubject, goal, duration: timerSettings[timerMode] });
                localStorage.setItem('noesis_pomodoro_log', JSON.stringify(pomodoroLog));
                renderPomodoroLog();
                showToast('Pomodoro terminé ! Prenez une pause.');
                if (cycleCount % 4 === 0) { setTimerMode('long'); document.querySelectorAll('.timer-mode')[2].classList.add('active'); }
                else { setTimerMode('short'); document.querySelectorAll('.timer-mode')[1].classList.add('active'); }
            } else {
                showToast('Pause terminée ! Retour au travail.');
                setTimerMode('pomodoro');
                document.querySelectorAll('.timer-mode')[0].classList.add('active');
            }
            document.getElementById('timer-display').classList.add('pulse');
            setTimeout(() => document.getElementById('timer-display').classList.remove('pulse'), 2000);
        }

        function renderPomodoroLog() {
            const container = document.getElementById('pomodoro-log');
            if (pomodoroLog.length === 0) {
                container.innerHTML = `<div class="log-entry"><span class="log-time">--:--</span><span class="log-dot" style="background: var(--border)"></span><span class="log-content">Aucune session enregistrée aujourd'hui</span><span class="log-duration">--</span></div>`;
                return;
            }
            container.innerHTML = pomodoroLog.slice(-10).reverse().map(log => `
                <div class="log-entry"><span class="log-time">${log.time}</span><span class="log-dot" style="background: var(--text)"></span><span class="log-content">${log.subject}${log.goal ? ' — ' + log.goal : ''}</span><span class="log-duration">${log.duration}min</span></div>
            `).join('');
        }

        // ==================== J METHOD ====================
        function showJInfo(day) {
            const info = {
                0: '<strong style="color: var(--text);">J0 — Cours Initial</strong><br>Assistez au cours. Relisez vos notes le soir même de manière active. Ne mémorisez pas encore, mais familiarisez-vous avec les grandes lignes.',
                1: '<strong style="color: var(--text);">J1 — Approfondir</strong><br>Le lendemain du cours. Approfondissez les concepts et revoyez les idées générales. J1 est crucial car le sommeil a consolidé la mémoire.',
                3: '<strong style="color: var(--text);">J3 — Mémoriser</strong><br>Il est temps d'apprendre par cœur les définitions, formules et concepts clés. Utilisez des flashcards.',
                7: '<strong style="color: var(--text);">J7 — Rappel</strong><br>Piqûre de rappel hebdomadaire. Testez-vous avec des QCM ou la feuille blanche. Identifiez les lacunes.',
                15: '<strong style="color: var(--text);">J15 — Consolider</strong><br>Révision à mi-parcours. Reliez ce cours aux autres concepts du même chapitre. Faites des exercices d'application.',
                30: '<strong style="color: var(--text);">J30 — Maîtriser</strong><br>Révision finale avant l'examen. Vous devriez pouvoir expliquer ce cours à quelqu'un d'autre (technique Feynman).'
            };
            document.getElementById('j-info').innerHTML = info[day] || info[0];
            document.querySelectorAll('.j-node').forEach(n => { n.classList.remove('current'); if (n.textContent.trim() === 'J' + day) n.classList.add('current'); });
        }

        function addJCourse() {
            const title = document.getElementById('j-title').value.trim();
            const subject = document.getElementById('j-subject').value;
            const date = document.getElementById('j-date').value;
            const rhythm = document.getElementById('j-rhythm').value;
            if (!title || !date) return showToast('Veuillez remplir tous les champs');
            const rhythms = { classic: [0, 1, 3, 7, 15, 30], light: [0, 2, 5, 14], intense: [0, 1, 2, 4, 7, 14] };
            const j0 = new Date(date);
            const revisions = rhythms[rhythm].map(d => { const rev = new Date(j0); rev.setDate(rev.getDate() + d); return { day: d, date: rev.toISOString().split('T')[0] }; });
            jCourses.push({ title, subject, date, rhythm, revisions });
            localStorage.setItem('noesis_j_courses', JSON.stringify(jCourses));
            document.getElementById('j-title').value = '';
            renderJUpcoming();
            showToast('Cours planifié avec succès !');
        }

        function renderJUpcoming() {
            const container = document.getElementById('j-upcoming');
            const today = new Date().toISOString().split('T')[0];
            let upcoming = [];
            jCourses.forEach(c => c.revisions.forEach(r => { if (r.date >= today) upcoming.push({ ...r, title: c.title, subject: c.subject }); }));
            upcoming.sort((a, b) => a.date.localeCompare(b.date));
            if (upcoming.length === 0) {
                container.innerHTML = `<div class="sr-list-item"><div class="sr-info"><h4>Aucune révision à venir</h4><p>Ajoutez un cours pour commencer</p></div></div>`;
                return;
            }
            container.innerHTML = upcoming.slice(0, 10).map(u => {
                const isToday = u.date === today;
                const dueClass = isToday ? 'sr-now' : 'sr-soon';
                const dueText = isToday ? 'AUJOURD'HUI' : `J${u.day}`;
                return `<div class="sr-list-item"><div class="sr-info"><h4>${u.title}</h4><p>${u.subject} • ${u.date}</p></div><span class="sr-badge ${dueClass}">${dueText}</span></div>`;
            }).join('');
        }

        // ==================== FEYNMAN ====================
        function setFeynmanStep(step) {
            feynmanStep = step;
            document.querySelectorAll('.feynman-step').forEach((s, i) => s.classList.toggle('active', i + 1 === step));
            const contents = {
                1: { title: 'Étape 1 : Choisir le Concept', subtitle: 'Sélectionnez un sujet scientifique spécifique à maîtriser', html: '<div class="form-group"><label class="form-label">Concept à étudier</label><input type="text" id="feynman-concept" placeholder="Ex: Principe d'incertitude de Heisenberg..."></div><div class="form-group"><label class="form-label">Matière</label><select id="feynman-subject"><option>Physique</option><option>Chimie</option><option>Mathématiques</option><option>Biologie</option><option>Informatique</option></select></div><div class="form-group"><label class="form-label">Votre niveau actuel</label><select id="feynman-level"><option>Débutant sur ce sujet</option><option>Connaissances de base</option><option>Intermédiaire</option><option>Avancé — besoin de perfectionner</option></select></div><button class="btn btn-primary" onclick="nextFeynmanStep()">Continuer →</button>' },
                2: { title: 'Étape 2 : Enseigner à un Enfant', subtitle: 'Expliquez le concept avec des mots simples, sans jargon', html: '<div class="form-group"><label class="form-label">Votre explication simple</label><textarea id="feynman-explain" rows="6" placeholder="Expliquez comme si vous parliez à un enfant de 12 ans...&#10;&#10;Utilisez des analogies et des exemples concrets. Évitez les termes techniques."></textarea></div><button class="btn btn-primary" onclick="nextFeynmanStep()">Continuer →</button>' },
                3: { title: 'Étape 3 : Identifier les Lacunes', subtitle: 'Repérez ce que vous n'avez pas pu expliquer clairement', html: '<div class="form-group"><label class="form-label">Qu'avez-vous eu du mal à expliquer ?</label><textarea id="feynman-gaps" rows="4" placeholder="Listez les points où vous avez hésité, utilisé des mots vagues, ou dû revenir à vos notes..."></textarea></div><div class="form-group"><label class="form-label">Termes techniques non simplifiés</label><input type="text" id="feynman-terms" placeholder="Ex: hamiltonien, isomorphe, tensoriel..."></div><button class="btn btn-primary" onclick="nextFeynmanStep()">Continuer →</button>' },
                4: { title: 'Étape 4 : Simplifier et Analogies', subtitle: 'Reformulez avec des analogies et des exemples plus simples', html: '<div class="form-group"><label class="form-label">Explication finale simplifiée</label><textarea id="feynman-final" rows="6" placeholder="Réécrivez votre explication en intégrant les corrections...&#10;&#10;Ajoutez des analogies :&#10;- 'C'est comme...'&#10;- 'Imaginez que...'"></textarea></div><button class="btn btn-primary" onclick="saveFeynmanSession()">✓ Terminer la Session</button>' }
            };
            const c = contents[step];
            const card = document.getElementById('feynman-content');
            card.innerHTML = `<h2>${c.title}</h2><p class="subtitle">${c.subtitle}</p>${c.html}`;
        }

        function nextFeynmanStep() { if (feynmanStep < 4) setFeynmanStep(feynmanStep + 1); }

        function saveFeynmanSession() {
            const concept = document.getElementById('feynman-concept')?.value || 'Concept sans titre';
            feynmanSessions.push({ concept, date: new Date().toLocaleDateString('fr-FR'), completed: true });
            localStorage.setItem('noesis_feynman', JSON.stringify(feynmanSessions));
            renderFeynmanSessions();
            showToast('Session Feynman enregistrée !');
            setFeynmanStep(1);
        }

        function renderFeynmanSessions() {
            const container = document.getElementById('feynman-sessions');
            if (feynmanSessions.length === 0) {
                container.innerHTML = `<div class="checklist-item"><div class="check-box"></div><span style="color: var(--text-muted);">Aucune session enregistrée</span></div>`;
                return;
            }
            container.innerHTML = feynmanSessions.slice(-5).reverse().map(s => `
                <div class="checklist-item"><div class="check-box checked">✓</div><span>${s.concept} <span style="color: var(--text-muted);">— ${s.date}</span></span></div>
            `).join('');
        }

        // ==================== BLANK PAGE ====================
        function startBlankPage() {
            const subject = document.getElementById('bp-subject').value;
            const time = parseInt(document.getElementById('bp-time').value) || 20;
            if (!subject) return showToast('Veuillez entrer un sujet');
            document.getElementById('bp-session').style.display = 'block';
            bpSeconds = time * 60;
            document.getElementById('bp-textarea').value = '';
            document.getElementById('bp-textarea').focus();
            bpTimerInterval = setInterval(() => {
                if (bpSeconds > 0) {
                    bpSeconds--;
                    const m = Math.floor(bpSeconds / 60);
                    const s = bpSeconds % 60;
                    document.getElementById('bp-timer-display').textContent = `Temps restant: ${m}:${s.toString().padStart(2,'0')}`;
                    const total = time * 60;
                    const pct = (bpSeconds / total) * 100;
                    const bar = document.getElementById('bp-progress');
                    bar.style.width = pct + '%';
                    bar.className = 'time-fill ' + (pct > 50 ? 'time-good' : pct > 20 ? 'time-warn' : 'time-danger');
                } else {
                    stopBlankPage();
                    showToast('Temps écoulé ! Vérifiez vos notes maintenant.');
                }
            }, 1000);
            showToast('Session démarrée ! Ne regardez PAS vos notes.');
        }

        function stopBlankPage() { clearInterval(bpTimerInterval); document.getElementById('bp-session').style.display = 'none'; }

        // ==================== CORNELL ====================
        function clearCornell() {
            document.getElementById('cornell-title').value = '';
            document.getElementById('cornell-cues').value = '';
            document.getElementById('cornell-notes').value = '';
            document.getElementById('cornell-summary').value = '';
        }

        function saveCornell() {
            const note = { title: document.getElementById('cornell-title').value || 'Sans titre', cues: document.getElementById('cornell-cues').value, notes: document.getElementById('cornell-notes').value, summary: document.getElementById('cornell-summary').value, date: new Date().toLocaleDateString('fr-FR') };
            cornellNotes.push(note);
            localStorage.setItem('noesis_cornell', JSON.stringify(cornellNotes));
            renderCornellSaved();
            showToast('Note Cornell sauvegardée !');
        }

        function renderCornellSaved() {
            const container = document.getElementById('cornell-saved');
            if (cornellNotes.length === 0) {
                container.innerHTML = `<div class="sr-list-item"><div class="sr-info"><h4>Aucune note sauvegardée</h4><p>Créez votre première page Cornell</p></div></div>`;
                return;
            }
            container.innerHTML = cornellNotes.slice(-5).reverse().map(n => `
                <div class="sr-list-item" style="cursor: pointer;" onclick="loadCornell('${n.date}')"><div class="sr-info"><h4>${n.title}</h4><p>${n.date} • ${n.notes.length} caractères</p></div></div>
            `).join('');
        }

        function loadCornell(date) {
            const note = cornellNotes.find(n => n.date === date);
            if (!note) return;
            document.getElementById('cornell-title').value = note.title;
            document.getElementById('cornell-cues').value = note.cues;
            document.getElementById('cornell-notes').value = note.notes;
            document.getElementById('cornell-summary').value = note.summary;
            showToast('Note chargée !');
        }

        // ==================== SPACED REPETITION ====================
        function addFlashcard() {
            const front = document.getElementById('sr-front').value.trim();
            const back = document.getElementById('sr-back').value.trim();
            const subject = document.getElementById('sr-subject').value;
            const difficulty = document.getElementById('sr-difficulty').value;
            if (!front || !back) return showToast('Veuillez remplir les deux faces');
            const intervals = { easy: 4, medium: 1, hard: 0.5 };
            const nextReview = new Date();
            nextReview.setMinutes(nextReview.getMinutes() + intervals[difficulty]);
            flashcards.push({ id: Date.now(), front, back, subject, difficulty, nextReview: nextReview.toISOString(), interval: intervals[difficulty], reviews: 0 });
            localStorage.setItem('noesis_flashcards', JSON.stringify(flashcards));
            document.getElementById('sr-front').value = '';
            document.getElementById('sr-back').value = '';
            renderSrList();
            showToast('Flashcard ajoutée !');
        }

        function renderSrList() {
            const container = document.getElementById('sr-list');
            const now = new Date();
            const due = flashcards.filter(f => new Date(f.nextReview) <= now);
            const upcoming = flashcards.filter(f => new Date(f.nextReview) > now);
            document.getElementById('sr-count').textContent = `${due.length} cartes en attente`;
            if (flashcards.length === 0) {
                container.innerHTML = `<div class="sr-list-item"><div class="sr-info"><h4>Aucune carte à réviser</h4><p>Ajoutez des flashcards pour commencer</p></div></div>`;
                return;
            }
            container.innerHTML = due.slice(0, 5).map(f => `
                <div class="sr-list-item" style="cursor: pointer;" onclick="startSrReview(${f.id})"><div class="sr-info"><h4>${f.front.substring(0, 50)}${f.front.length > 50 ? '...' : ''}</h4><p>${f.subject} • ${f.reviews} révisions</p></div><span class="sr-badge sr-now">À RÉVISER</span></div>
            `).join('') + upcoming.slice(0, 3).map(f => {
                const mins = Math.ceil((new Date(f.nextReview) - now) / 60000);
                const dueClass = mins < 60 ? 'sr-soon' : 'sr-later';
                const dueText = mins < 60 ? `${mins}min` : `${Math.ceil(mins/60)}h`;
                return `<div class="sr-list-item"><div class="sr-info"><h4>${f.front.substring(0, 50)}${f.front.length > 50 ? '...' : ''}</h4><p>${f.subject}</p></div><span class="sr-badge ${dueClass}">${dueText}</span></div>`;
            }).join('');
        }

        function startSrReview(id) {
            const card = flashcards.find(f => f.id === id);
            if (!card) return;
            currentReviewCard = card;
            document.getElementById('sr-review').style.display = 'block';
            document.getElementById('sr-review-front').textContent = card.front;
            document.getElementById('sr-review-back').style.display = 'none';
            document.getElementById('sr-show-btn').style.display = 'inline-flex';
            document.getElementById('sr-rating').style.display = 'none';
            document.getElementById('sr-review').scrollIntoView({ behavior: 'smooth' });
        }

        function showSrAnswer() {
            document.getElementById('sr-review-back').textContent = currentReviewCard.back;
            document.getElementById('sr-review-back').style.display = 'block';
            document.getElementById('sr-show-btn').style.display = 'none';
            document.getElementById('sr-rating').style.display = 'flex';
        }

        function rateCard(rating) {
            if (!currentReviewCard) return;
            const multipliers = { again: 0.5, hard: 1.2, good: 2.5, easy: 4 };
            const card = flashcards.find(f => f.id === currentReviewCard.id);
            card.interval *= multipliers[rating];
            card.reviews++;
            const next = new Date();
            next.setMinutes(next.getMinutes() + card.interval);
            card.nextReview = next.toISOString();
            localStorage.setItem('noesis_flashcards', JSON.stringify(flashcards));
            document.getElementById('sr-review').style.display = 'none';
            renderSrList();
            showToast('Carte mise à jour ! Prochaine révision dans ' + Math.round(card.interval) + 'min');
        }

        // ==================== UTILS ====================
        function showToast(msg) {
            const toast = document.getElementById('toast');
            toast.textContent = msg;
            toast.classList.add('show');
            setTimeout(() => toast.classList.remove('show'), 3000);
        }

        function showInfo(method) {
            const info = {
                sq3r: { title: 'SQ3R — Méthode de Lecture Active', body: 'Survey (Parcourir): Parcourez le chapitre pour avoir une vue d'ensemble. Question (Questionner): Formulez des questions sur le titre et les sous-titres. Read (Lire): Lisez activement en cherchant les réponses. Recite (Réciter): Fermez le livre et récitez ce que vous avez retenu. Review (Réviser): Relisez pour vérifier et compléter.' },
                loci: { title: 'Méthode des Loci (Palais Mental)', body: 'Technique de mémorisation millénaire utilisée par les orateurs romains. Associez chaque concept à un lieu familier (votre maison, votre université). Pour réviser, "marchez" mentalement dans ces lieux et récupérez les informations. Particulièrement efficace pour mémoriser des séquences, des formules, ou des classifications.' }
            };
            const i = info[method];
            if (i) { document.getElementById('modal-title').textContent = i.title; document.getElementById('modal-body').textContent = i.body; document.getElementById('modal').classList.add('active'); }
        }

        function closeModal() { document.getElementById('modal').classList.remove('active'); }

        function renderAll() {
            renderSubjects();
            renderPomodoroSubjects();
            renderInterleaveSubjects();
            renderPomodoroLog();
            renderJUpcoming();
            renderFeynmanSessions();
            renderCornellSaved();
            renderSrList();
        }

        document.addEventListener('DOMContentLoaded', () => {
            renderAll();
            updateTimerDisplay();
            document.getElementById('j-date').value = new Date().toISOString().split('T')[0];
        });

        document.addEventListener('keydown', (e) => {
            if (e.code === 'Space' && document.getElementById('pomodoro').classList.contains('active')) { e.preventDefault(); toggleTimer(); }
        });
    </script>
</body>
</html>
