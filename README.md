
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Edufinity Vault Pro | JEE PYQ</title>
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
            --radius-btn: 14px;
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
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.3);
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
            background: rgba(255, 255, 255, 0.04);
            border: 1px solid var(--glass-border);
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
        }

        .btn-back:hover {
            background: rgba(255, 255, 255, 0.1);
            border-color: rgba(255, 255, 255, 0.18);
            transform: translateX(-4px);
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
            background: var(--glass-card);
            border: 1px solid var(--glass-border);
            border-radius: var(--radius-main);
            padding: 50px 25px;
            text-align: center;
            cursor: pointer;
            transition: transform 0.4s cubic-bezier(0.25, 1, 0.5, 1), border-color 0.3s ease, box-shadow 0.3s ease;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            gap: 12px;
            box-shadow: 0 15px 35px rgba(0,0,0,0.2);
        }

        .subject-card:active, .option-card:active {
            transform: scale(0.95);
        }

        .subject-card[data-target="physics"]:hover, .option-card[data-type="physics"]:hover { border-color: #3b82f6; box-shadow: 0 0 30px rgba(59, 130, 246, 0.25); }
        .subject-card[data-target="chemistry"]:hover, .option-card[data-type="chemistry"]:hover { border-color: #f59e0b; box-shadow: 0 0 30px rgba(245, 158, 11, 0.2); }
        .subject-card[data-target="maths"]:hover, .option-card[data-type="maths"]:hover { border-color: #10b981; box-shadow: 0 0 30px rgba(16, 185, 129, 0.2); }

        .card-icon-tag {
            font-size: 11px;
            font-weight: 700;
            color: var(--text-muted);
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .card-title {
            font-size: 26px;
            font-weight: 800;
            letter-spacing: -0.5px;
        }

        .chapters-panel {
            display: none;
            background: var(--glass-card);
            border: 1px solid var(--glass-border);
            border-radius: var(--radius-main);
            padding: 35px;
            box-shadow: 0 30px 60px rgba(0, 0, 0, 0.3);
            opacity: 0;
            transform: translateY(24px);
            transition: opacity 0.5s cubic-bezier(0.25, 1, 0.5, 1), transform 0.5s cubic-bezier(0.25, 1, 0.5, 1);
        }

        .chapters-panel.active {
            display: block;
            opacity: 1;
            transform: translateY(0);
        }

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
        }

        .total-badge {
            font-size: 12px;
            font-weight: 700;
            background: rgba(255, 255, 255, 0.06);
            padding: 6px 14px;
            border-radius: 30px;
            color: var(--text-muted);
        }

        .chapter-list {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .chapter-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 24px;
            background: rgba(255, 255, 255, 0.005);
            border-radius: 16px;
            border: 1px solid var(--glass-border);
            transition: background 0.3s cubic-bezier(0.25, 1, 0.5, 1), border-color 0.3s ease, transform 0.3s cubic-bezier(0.25, 1, 0.5, 1);
        }

        .chapter-item:hover {
            background: rgba(255, 255, 255, 0.03);
            border-color: rgba(255, 255, 255, 0.15);
            transform: scale(1.01);
        }

        .chapter-details {
            display: flex;
            flex-direction: column;
            gap: 5px;
            padding-right: 15px;
        }

        .chapter-title-text {
            font-size: 16px;
            font-weight: 700;
            color: var(--text-white);
        }

        .chapter-subtitle-text {
            font-size: 13px;
            color: var(--text-muted);
            font-weight: 500;
        }

        .btn-download {
            text-decoration: none;
            color: #ffffff;
            padding: 12px 24px;
            font-size: 13px;
            font-weight: 700;
            border-radius: var(--radius-btn);
            white-space: nowrap;
            letter-spacing: 0.3px;
            transition: transform 0.2s cubic-bezier(0.25, 1, 0.5, 1), filter 0.2s ease, box-shadow 0.2s ease;
        }

        .btn-download:hover {
            transform: translateY(-2px);
            filter: brightness(1.15);
        }

        .physics-view .btn-download { background: var(--physics-glow); box-shadow: 0 4px 15px rgba(59, 130, 246, 0.3); }
        .chemistry-view .btn-download { background: var(--chemistry-glow); box-shadow: 0 4px 15px rgba(245, 158, 11, 0.25); }
        .maths-view .btn-download { background: var(--maths-glow); box-shadow: 0 4px 15px rgba(16, 185, 129, 0.25); }

        @media (max-width: 768px) {
            body { padding: 25px 12px; }
            header { padding: 35px 20px; margin-bottom: 25px; }
            header h1 { font-size: 36px; }
            .subject-grid, .options-grid { grid-template-columns: 1fr; gap: 15px; }
            .subject-card, .option-card { padding: 40px 20px; }
            .chapters-panel { padding: 20px; }
            .panel-title { font-size: 24px; }
            .chapter-item { flex-direction: column; align-items: flex-start; gap: 16px; padding: 18px; }
            .btn-download { width: 100%; text-align: center; padding: 14px; }
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
            <span class="card-icon-tag">Subject 01</span>
            <span class="card-title" style="color: #3b82f6;">Physics</span>
        </div>
        <div class="subject-card" data-target="chemistry">
            <span class="card-icon-tag">Subject 02</span>
            <span class="card-title" style="color: #f59e0b;">Chemistry</span>
        </div>
        <div class="subject-card" data-target="maths">
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

        // Unit numbers removed, only names kept intact
        const chapterDatabase = {
            physics: [
                { ch: "CH-01", name: "Electrostatics", sub: "PYQ Practice Sheet" },
                { ch: "CH-02", name: "Current Electricity", sub: "PYQ Practice Sheet" },
                { ch: "CH-03", name: "Magnetic Effects of Current and Magnetism", sub: "PYQ Practice Sheet" },
                { ch: "CH-04", name: "Electromagnetic Induction and Alternating Currents", sub: "PYQ Practice Sheet" },
                { ch: "CH-05", name: "Electromagnetic Waves", sub: "PYQ Practice Sheet" },
                { ch: "CH-06", name: "Optics", sub: "PYQ Practice Sheet" },
                { ch: "CH-07", name: "Dual Nature of Matter and Radiation", sub: "PYQ Practice Sheet" },
                { ch: "CH-08", name: "Atoms and Nuclei", sub: "PYQ Practice Sheet" },
                { ch: "CH-09", name: "Electronic Devices", sub: "PYQ Practice Sheet" }
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

                let books = ["Modules", "Arihant", "Cengage"];
                if (selectedSubject === "maths") {
                    books = ["Modules", "Arihant"]; 
                }

                books.forEach((book, index) => {
                    const optionCard = document.createElement("div");
                    optionCard.className = "option-card";
                    optionCard.setAttribute("data-type", selectedSubject);
                    optionCard.setAttribute("data-book", book);
                    optionCard.innerHTML = `
                        <span class="card-icon-tag">Resource 0${index + 1}</span>
                        <span class="card-title">${book}</span>
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
                    optionsGrid.style.display = "none";

                    let titleColor = "#3b82f6";
                    let viewClass = "physics-view";
                    if (selectedSubject === "chemistry") { titleColor = "#f59e0b"; viewClass = "chemistry-view"; }
                    if (selectedSubject === "maths") { titleColor = "#10b981"; viewClass = "maths-view"; }

                    const chapters = chapterDatabase[selectedSubject];

                    let chaptersHtml = `
                        <div id="active-panel" class="chapters-panel ${viewClass} active">
                            <div class="panel-header">
                                <span class="panel-title" style="color: ${titleColor};">${selectedSubject.charAt(0).toUpperCase() + selectedSubject.slice(1)} - ${selectedBook}</span>
                                <span class="total-badge">${chapters.length} Chapters</span>
                            </div>
                            <div class="chapter-list">
                    `;

                    chapters.forEach(item => {
                        chaptersHtml += `
                            <div class="chapter-item">
                                <div class="chapter-details">
                                    <span class="chapter-title-text">${item.ch}: ${item.name}</span>
                                    <span class="chapter-subtitle-text">${item.sub}</span>
                                </div>
                                <a href="#" target="_blank" class="btn-download">Open PDF</a>
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

        // Navigation Controllers
        backSubjBtn.addEventListener("click", function() {
            optionsGrid.style.display = "none";
            subjectGrid.style.display = "grid";
            controlBar.classList.remove("active");
            backSubjBtn.style.display = "none";
        });

        backOptBtn.addEventListener("click", function() {
            chaptersContainer.innerHTML = "";
            optionsGrid.style.display = "grid";
            backSubjBtn.style.display = "inline-flex";
            backOptBtn.style.display = "none";
        });
    });
</script>

</body>
