<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JEE PYQ</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --bg-dark: #0a0f1d;
            --glass-card: rgba(255, 255, 255, 0.02);
            --glass-border: rgba(255, 255, 255, 0.06);
            --text-white: #ffffff;
            --text-muted: #8a99ad;
            
            --physics-glow: linear-gradient(135deg, #3b82f6 0%, #1d4ed8 100%);
            --chemistry-glow: linear-gradient(135deg, #f59e0b 0%, #d97706 100%);
            --maths-glow: linear-gradient(135deg, #10b981 0%, #059669 100%);
            
            --radius-main: 24px;
            --radius-btn: 12px;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Plus Jakarta Sans', sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background-color: var(--bg-dark);
            color: var(--text-white);
            min-height: 100vh;
            padding: 40px 20px;
            overflow-x: hidden;
            background-image: 
                radial-gradient(at 0% 0%, rgba(59, 130, 246, 0.18) 0px, transparent 50%),
                radial-gradient(at 100% 100%, rgba(16, 185, 129, 0.12) 0px, transparent 50%),
                radial-gradient(at 50% 50%, rgba(245, 158, 11, 0.04) 0px, transparent 50%);
            background-attachment: fixed;
        }

        .container {
            max-width: 850px;
            margin: 0 auto;
        }

        header {
            background: var(--glass-card);
            backdrop-filter: blur(25px);
            -webkit-backdrop-filter: blur(25px);
            padding: 45px 30px;
            border-radius: var(--radius-main);
            text-align: center;
            margin-bottom: 35px;
            border: 1px solid var(--glass-border);
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.3), inset 0 1px 0 rgba(255,255,255,0.05);
        }

        header h1 {
            font-size: 44px;
            font-weight: 800;
            letter-spacing: -1.5px;
            margin-bottom: 10px;
            background: linear-gradient(to right, #ffffff, #a5f3fc);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        header p {
            color: var(--text-muted);
            font-size: 15px;
            font-weight: 500;
            line-height: 1.6;
        }

        .control-bar {
            display: none;
            margin-bottom: 25px;
            opacity: 0;
            transform: translateY(-10px);
            transition: opacity 0.4s cubic-bezier(0.25, 1, 0.5, 1), transform 0.4s cubic-bezier(0.25, 1, 0.5, 1);
        }

        .control-bar.active {
            display: flex;
            gap: 12px;
            opacity: 1;
            transform: translateY(0);
        }

        .btn-back {
            background: linear-gradient(145deg, rgba(255,255,255,0.06) 0%, rgba(255,255,255,0.01) 100%);
            border: 1px solid rgba(255, 255, 255, 0.1);
            color: var(--text-white);
            padding: 14px 28px;
            font-size: 14px;
            font-weight: 700;
            border-radius: var(--radius-btn);
            cursor: pointer;
            display: inline-flex;
            align-items: center;
            gap: 10px;
            transition: all 0.3s cubic-bezier(0.25, 1, 0.5, 1);
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
        }

        .btn-back:hover {
            background: linear-gradient(145deg, rgba(255,255,255,0.1) 0%, rgba(255,255,255,0.03) 100%);
            border-color: rgba(255, 255, 255, 0.25);
            transform: translateX(-4px) translateY(-2px);
            box-shadow: 0 8px 20px rgba(0,0,0,0.2);
        }

        .subject-grid, .options-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
            transition: opacity 0.4s cubic-bezier(0.25, 1, 0.5, 1), transform 0.4s cubic-bezier(0.25, 1, 0.5, 1);
        }

        .options-grid {
            display: none;
        }

        .subject-card, .option-card {
            background: linear-gradient(145deg, rgba(255, 255, 255, 0.04) 0%, rgba(255, 255, 255, 0.01) 100%);
            backdrop-filter: blur(15px);
            -webkit-backdrop-filter: blur(15px);
            border: 1px solid rgba(255, 255, 255, 0.08);
            border-radius: var(--radius-main);
            padding: 50px 25px;
            text-align: center;
            cursor: pointer;
            transition: all 0.4s cubic-bezier(0.25, 1, 0.5, 1);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            gap: 14px;
            box-shadow: 0 15px 35px rgba(0,0,0,0.2), inset 0 1px 1px rgba(255,255,255,0.1);
            position: relative;
            overflow: hidden; 
        }

        .subject-card::before, .option-card::before {
            content: '';
            position: absolute;
            top: 0; left: -100%;
            width: 50%; height: 100%;
            background: linear-gradient(to right, transparent, rgba(255,255,255,0.06), transparent);
            transform: skewX(-25deg);
            transition: 0.6s ease;
        }

        .subject-card:hover::before, .option-card:hover::before { left: 125%; }
        .subject-card:hover, .option-card:hover { transform: translateY(-8px); }
        .subject-card:active, .option-card:active { transform: translateY(2px) scale(0.96); }

        .subject-card[data-target="physics"]:hover, .option-card[data-type="physics"]:hover { 
            border-color: rgba(59, 130, 246, 0.5); 
            background: linear-gradient(145deg, rgba(59, 130, 246, 0.08) 0%, rgba(255, 255, 255, 0.01) 100%);
            box-shadow: 0 20px 40px rgba(59, 130, 246, 0.15), inset 0 1px 1px rgba(255,255,255,0.2); 
        }
        
        .subject-card[data-target="chemistry"]:hover, .option-card[data-type="chemistry"]:hover { 
            border-color: rgba(245, 158, 11, 0.5); 
            background: linear-gradient(145deg, rgba(245, 158, 11, 0.08) 0%, rgba(255, 255, 255, 0.01) 100%);
            box-shadow: 0 20px 40px rgba(245, 158, 11, 0.15), inset 0 1px 1px rgba(255,255,255,0.2); 
        }
        
        .subject-card[data-target="maths"]:hover, .option-card[data-type="maths"]:hover { 
            border-color: rgba(16, 185, 129, 0.5); 
            background: linear-gradient(145deg, rgba(16, 185, 129, 0.08) 0%, rgba(255, 255, 255, 0.01) 100%);
            box-shadow: 0 20px 40px rgba(16, 185, 129, 0.15), inset 0 1px 1px rgba(255,255,255,0.2); 
        }

        .subject-card svg { filter: drop-shadow(0 4px 6px rgba(0,0,0,0.4)); transition: transform 0.4s cubic-bezier(0.25, 1, 0.5, 1); }
        .subject-card:hover svg { transform: scale(1.15) translateY(-2px); }

        .card-icon-tag {
            font-size: 11px;
            font-weight: 700;
            color: var(--text-muted);
            text-transform: uppercase;
            letter-spacing: 2.5px;
            background: rgba(255,255,255,0.05);
            padding: 4px 10px;
            border-radius: 20px;
            border: 1px solid rgba(255,255,255,0.03);
        }

        .card-title {
            font-size: 26px;
            font-weight: 800;
            letter-spacing: -0.5px;
            text-shadow: 0 2px 10px rgba(0,0,0,0.3);
        }

        .chapters-panel {
            display: none;
            background: linear-gradient(180deg, rgba(255,255,255,0.03) 0%, rgba(255,255,255,0.01) 100%);
            border: 1px solid var(--glass-border);
            border-radius: var(--radius-main);
            padding: 35px;
            box-shadow: 0 30px 60px rgba(0, 0, 0, 0.3), inset 0 1px 0 rgba(255,255,255,0.05);
            opacity: 0;
            transform: translateY(24px);
            transition: opacity 0.5s cubic-bezier(0.25, 1, 0.5, 1), transform 0.5s cubic-bezier(0.25, 1, 0.5, 1);
        }

        .chapters-panel.active { display: block; opacity: 1; transform: translateY(0); }

        .panel-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
            padding-bottom: 15px;
            border-bottom: 1px solid var(--glass-border);
        }

        .panel-title {
            font-size: 28px;
            font-weight: 800;
            letter-spacing: -0.5px;
            text-shadow: 0 2px 10px rgba(0,0,0,0.5);
        }

        .total-badge {
            font-size: 12px;
            font-weight: 700;
            background: rgba(255, 255, 255, 0.08);
            padding: 6px 14px;
            border-radius: 30px;
            color: #ffffff;
            border: 1px solid rgba(255,255,255,0.1);
        }

        .chapter-list { display: flex; flex-direction: column; gap: 15px; }

        .chapter-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 24px;
            background: linear-gradient(90deg, rgba(255, 255, 255, 0.01) 0%, transparent 100%);
            border-radius: 16px;
            border: 1px solid var(--glass-border);
            transition: all 0.3s cubic-bezier(0.25, 1, 0.5, 1);
        }

        .chapter-item:hover {
            background: rgba(255, 255, 255, 0.04);
            border-color: rgba(255, 255, 255, 0.2);
            transform: translateX(6px);
            box-shadow: -5px 5px 20px rgba(0,0,0,0.15);
        }

        .chapter-details { display: flex; flex-direction: column; gap: 6px; padding-right: 20px; }
        .chapter-title-text { font-size: 16px; font-weight: 700; color: var(--text-white); line-height: 1.4; }
        .chapter-subtitle-text { font-size: 13px; color: var(--text-muted); font-weight: 600; }

        /* ----- Professional Button Alignment Fixes ----- */
        .download-actions-group { 
            display: flex; 
            gap: 10px; 
            flex-wrap: wrap; 
            align-items: center; /* Ensures perfect vertical alignment */
            justify-content: flex-end;
        }

        .btn-download {
            text-decoration: none;
            color: #ffffff;
            padding: 12px 22px;
            font-size: 12px;
            font-weight: 800;
            border-radius: var(--radius-btn);
            white-space: nowrap;
            letter-spacing: 1px;
            text-transform: uppercase;
            transition: all 0.3s cubic-bezier(0.25, 1, 0.5, 1);
            position: relative;
            overflow: hidden;
            border: 1px solid rgba(255,255,255,0.25);
            display: inline-flex; /* Fixes block layout issues */
            align-items: center;
            justify-content: center;
            height: 42px; /* Standardize button heights perfectly */
            box-shadow: inset 0 1px 1px rgba(255,255,255,0.3), 0 4px 15px rgba(0,0,0,0.2);
            backdrop-filter: blur(5px);
        }

        .btn-download::before {
            content: '';
            position: absolute;
            top: 0; left: -100%;
            width: 100%; height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            transition: 0.5s;
        }

        .btn-download:hover::before { left: 100%; }
        .btn-download:hover { transform: translateY(-3px); filter: brightness(1.15); box-shadow: inset 0 1px 1px rgba(255,255,255,0.3), 0 8px 20px rgba(0,0,0,0.3); }
        .btn-download:active { transform: translateY(1px); }

        .physics-view .btn-download { background: var(--physics-glow); }
        .chemistry-view .btn-download { background: var(--chemistry-glow); }
        .maths-view .btn-download { background: var(--maths-glow); }

        @media (max-width: 768px) {
            body { padding: 25px 12px; }
            header { padding: 35px 20px; margin-bottom: 25px; }
            header h1 { font-size: 36px; }
            .subject-grid, .options-grid { grid-template-columns: 1fr; gap: 15px; }
            .subject-card, .option-card { padding: 40px 20px; }
            .chapters-panel { padding: 20px; }
            .panel-title { font-size: 24px; }
            
            .chapter-item { flex-direction: column; align-items: flex-start; gap: 20px; padding: 20px; }
            .download-actions-group { width: 100%; justify-content: flex-start; }
            
            /* On mobile, make buttons flexible but look organized */
            .btn-download { flex: 1; min-width: calc(50% - 5px); }
            /* If there are 3 parts, the 3rd one takes full width. 1 or 2 parts align perfectly side by side */
        }
    </style>
</head>
<body>

<div class="container">
    
    <header id="main-header">
        <h1>JEE PYQ</h1>
        <p>Complete Chapter-wise Previous Year Questions for JEE Main & Advanced Entrance Preparation.</p>
    </header>

    <div class="control-bar" id="control-bar">
        <button class="btn-back" id="back-subj-btn" style="display: none;">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><line x1="19" y1="12" x2="5" y2="12"></line><polyline points="12 19 5 12 12 5"></polyline></svg>
            Back to Subjects
        </button>
        <button class="btn-back" id="back-opt-btn" style="display: none;">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><line x1="19" y1="12" x2="5" y2="12"></line><polyline points="12 19 5 12 12 5"></polyline></svg>
            Back to Books
        </button>
    </div>

    <div class="subject-grid" id="subject-grid">
        
        <div class="subject-card" data-target="physics">
            <svg xmlns="http://www.w3.org/2000/svg" width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="#3b82f6" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
                <circle cx="12" cy="12" r="2"></circle>
                <ellipse cx="12" cy="12" rx="10" ry="4" transform="rotate(45 12 12)"></ellipse>
                <ellipse cx="12" cy="12" rx="10" ry="4" transform="rotate(-45 12 12)"></ellipse>
            </svg>
            <span class="card-icon-tag">Subject 01</span>
            <span class="card-title" style="color: #3b82f6;">Physics</span>
        </div>
        
        <div class="subject-card" data-target="chemistry">
            <svg xmlns="http://www.w3.org/2000/svg" width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="#f59e0b" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
                <path d="M9 3H15"></path>
                <path d="M10 15H14"></path>
                <path d="M8.5 21H15.5C16.8807 21 18 19.8807 18 18.5V17L14.5 11V3H9.5V11L6 17V18.5C6 19.8807 7.11929 21 8.5 21Z"></path>
            </svg>
            <span class="card-icon-tag">Subject 02</span>
            <span class="card-title" style="color: #f59e0b;">Chemistry</span>
        </div>
        
        <div class="subject-card" data-target="maths">
            <svg xmlns="http://www.w3.org/2000/svg" width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="#10b981" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
                <path d="M18 7V4H6l6 8-6 8h12v-3"></path>
            </svg>
            <span class="card-icon-tag">Subject 03</span>
            <span class="card-title" style="color: #10b981;">Mathematics</span>
        </div>

    </div>

    <div class="options-grid" id="options-grid"></div>

    <div id="chapters-container"></div>

</div>

<script>
    document.addEventListener("DOMContentLoaded", function() {
        const subjectGrid = document.getElementById("subject-grid");
        const optionsGrid = document.getElementById("options-grid");
        const controlBar = document.getElementById("control-bar");
        const backSubjBtn = document.getElementById("back-subj-btn");
        const backOptBtn = document.getElementById("back-opt-btn");
        const chaptersContainer = document.getElementById("chapters-container");
        
        let selectedSubject = "";

        const chapterDatabase = {
            physics: [
                { ch: "CH-01", name: "Electrostatics", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1EHuENpJPugRugKawpIUW-4fOFKWlW4ZU/view?usp=drivesdk", "https://drive.google.com/file/d/1hYnoeJIW1-CVCqfi3RiuvTgQUqeJFEPU/view?usp=drivesdk", "https://drive.google.com/file/d/1AdLBI4vl7BUO5b9E5xwrJb6FfxdMzNDG/view?usp=drivesdk"] }, 
                { ch: "CH-02", name: "Current Electricity", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1C-48MABN0F9VO0YmIw75pJH3Ryfc7NAu/view?usp=drivesdk"] }, 
                { ch: "CH-03", name: "Magnetic Effects of Current and Magnetism", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1L_AP4uNfbgNbLCCBSRYwnQS9OEHPnTuL/view?usp=drivesdk", "https://drive.google.com/file/d/1IWol_bthljJwylCp48aqhPBbuhG8-n15/view?usp=drivesdk"] }, 
                { ch: "CH-04", name: "Electromagnetic Induction and Alternating Currents", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/10KJcZudJUfzDI60GayixiQrZ3kFEE998/view?usp=drivesdk", "https://drive.google.com/file/d/1qUN4pWVnM2onNbVEL14a1MP9zDqBTNtU/view?usp=drivesdk"] }, 
                { ch: "CH-05", name: "Electromagnetic Waves", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1DL7clF00NPmRCU2VwPK69IldAQxkZ7mE/view?usp=drivesdk"] }, 
                { ch: "CH-06", name: "Optics", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1CXSEWSxPQWh08jpgmwefQ-TwN1ohMOis/view?usp=drivesdk", "https://drive.google.com/file/d/1vis8a41P_4WjmzqRN42zc0D0KLs56aXA/view?usp=drivesdk"] }, 
                { ch: "CH-07", name: "Dual Nature of Matter and Radiation", sub: "PYQ Practice Sheet", moduleLinks: ["#link"] }, 
                { ch: "CH-08", name: "Atoms and Nuclei", sub: "PYQ Practice Sheet", moduleLinks: ["#link1", "#link2"] }, 
                { ch: "CH-09", name: "Electronic Devices", sub: "PYQ Practice Sheet", moduleLinks: ["#link"] } 
            ],
            chemistry: [
                { ch: "CH-01", name: "Solutions", sub: "PYQ Practice Sheet" },
                { ch: "CH-02", name: "Electrochemistry", sub: "PYQ Practice Sheet" },
                { ch: "CH-03", name: "Chemical Kinetics", sub: "PYQ Practice Sheet" },
                { ch: "CH-04", name: "d- and f-Block Elements", sub: "PYQ Practice Sheet" },
                { ch: "CH-05", name: "Coordination Compounds", sub: "PYQ Practice Sheet" },
                { ch: "CH-06", name: "Haloalkanes and Haloarenes", sub: "PYQ Practice Sheet" },
                { ch: "CH-07", name: "Alcohols, Phenols and Ethers", sub: "PYQ Practice Sheet" },
                { ch: "CH-08", name: "Aldehydes, Ketones and Carboxylic Acids", sub: "PYQ Practice Sheet" },
                { ch: "CH-09", name: "Amines", sub: "PYQ Practice Sheet" },
                { ch: "CH-10", name: "Biomolecules", sub: "PYQ Practice Sheet" }
            ],
            maths: [
                { ch: "CH-01", name: "Relations and Functions", sub: "PYQ Practice Sheet" },
                { ch: "CH-02", name: "Inverse Trigonometric Functions", sub: "PYQ Practice Sheet" },
                { ch: "CH-03", name: "Matrices", sub: "PYQ Practice Sheet" },
                { ch: "CH-04", name: "Determinants", sub: "PYQ Practice Sheet" },
                { ch: "CH-05", name: "Continuity and Differentiability", sub: "PYQ Practice Sheet" },
                { ch: "CH-06", name: "Application of Derivatives", sub: "PYQ Practice Sheet" },
                { ch: "CH-07", name: "Integrals", sub: "PYQ Practice Sheet" },
                { ch: "CH-08", name: "Application of Integrals", sub: "PYQ Practice Sheet" },
                { ch: "CH-09", name: "Differential Equations", sub: "PYQ Practice Sheet" },
                { ch: "CH-10", name: "Vector Algebra", sub: "PYQ Practice Sheet" },
                { ch: "CH-11", name: "Three Dimensional Geometry", sub: "PYQ Practice Sheet" },
                { ch: "CH-12", name: "Linear Programming", sub: "PYQ Practice Sheet" },
                { ch: "CH-13", name: "Probability", sub: "PYQ Practice Sheet" }
            ]
        };

        // Step 1: Subject Selection (Tier 1 -> Tier 2)
        document.querySelectorAll(".subject-grid .subject-card").forEach(card => {
            card.addEventListener("click", function() {
                selectedSubject = this.getAttribute("data-target");
                
                subjectGrid.style.display = "none";
                optionsGrid.innerHTML = ""; 

                let books = [
                    { original: "Modules", display: "Modules (Practice)" },
                    { original: "Arihant", display: "Arihant (PYQ)" },
                    { original: "Cengage", display: "Cengage (Practice)" }
                ];
                
                if (selectedSubject === "maths") {
                    books = [
                        { original: "Modules", display: "Modules (Practice)" },
                        { original: "Arihant", display: "Arihant (PYQ)" }
                    ]; 
                }

                books.forEach((book, index) => {
                    const optionCard = document.createElement("div");
                    optionCard.className = "option-card";
                    optionCard.setAttribute("data-type", selectedSubject);
                    optionCard.setAttribute("data-book", book.original);
                    optionCard.setAttribute("data-display-book", book.display);
                    optionCard.innerHTML = `
                        <span class="card-icon-tag">Resource 0${index + 1}</span>
                        <span class="card-title">${book.display}</span>
                    `;
                    optionsGrid.appendChild(optionCard);
                });

                optionsGrid.style.display = "grid";
                controlBar.classList.add("active");
                backSubjBtn.style.display = "inline-flex";
                backOptBtn.style.display = "none";

                setupBookCards();
            });
        });

        // Step 2: Book Selection (Tier 2 -> Tier 3)
        function setupBookCards() {
            document.querySelectorAll(".options-grid .option-card").forEach(card => {
                card.addEventListener("click", function() {
                    const selectedBook = this.getAttribute("data-book");
                    const displayBookName = this.getAttribute("data-display-book");
                    optionsGrid.style.display = "none";

                    let titleColor = "#3b82f6";
                    let viewClass = "physics-view";
                    if (selectedSubject === "chemistry") { titleColor = "#f59e0b"; viewClass = "chemistry-view"; }
                    if (selectedSubject === "maths") { titleColor = "#10b981"; viewClass = "maths-view"; }

                    const chapters = chapterDatabase[selectedSubject];

                    let chaptersHtml = `
                        <div id="active-panel" class="chapters-panel ${viewClass} active">
                            <div class="panel-header">
                                <span class="panel-title" style="color: ${titleColor};">${selectedSubject.charAt(0).toUpperCase() + selectedSubject.slice(1)} - ${displayBookName}</span>
                                <span class="total-badge">${chapters.length} Chapters</span>
                            </div>
                            <div class="chapter-list">
                    `;

                    chapters.forEach(item => {
                        let buttonsHtml = '';

                        // Only for Physics AND Modules, generate part-wise links
                        if (selectedSubject === 'physics' && selectedBook === 'Modules' && item.moduleLinks && item.moduleLinks.length > 0) {
                            if (item.moduleLinks.length === 1) {
                                buttonsHtml = `<a href="${item.moduleLinks[0]}" class="btn-download" target="_blank">Download</a>`;
                            } else {
                                item.moduleLinks.forEach((link, idx) => {
                                    buttonsHtml += `<a href="${link}" class="btn-download" target="_blank">Part ${idx + 1}</a>`;
                                });
                            }
                        } else {
                            // Normal single download button for everything else
                            buttonsHtml = `<a href="#" class="btn-download">Download</a>`;
                        }

                        chaptersHtml += `
                            <div class="chapter-item">
                                <div class="chapter-details">
                                    <span class="chapter-title-text">${item.ch}: ${item.name}</span>
                                    <span class="chapter-subtitle-text">${item.sub}</span>
                                </div>
                                <div class="download-actions-group">
                                    ${buttonsHtml}
                                </div>
                            </div>
                        `;
                    });

                    chaptersHtml += `</div></div>`;
                    chaptersContainer.innerHTML = chaptersHtml;
                    
                    backSubjBtn.style.display = "none";
                    backOptBtn.style.display = "inline-flex";
                });
            });
        }

        backSubjBtn.addEventListener("click", function() {
            optionsGrid.style.display = "none";
            subjectGrid.style.display = "grid";
            controlBar.classList.remove("active");
            setTimeout(() => {
                backSubjBtn.style.display = "none";
            }, 400);
        });

        backOptBtn.addEventListener("click", function() {
            chaptersContainer.innerHTML = "";
            optionsGrid.style.display = "grid";
            backOptBtn.style.display = "none";
            backSubjBtn.style.display = "inline-flex";
        });
    });
</script>
</body>