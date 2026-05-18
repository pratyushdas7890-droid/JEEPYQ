
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
            /* Premium Deep Cosmic Dark UI Background instead of pure black */
            --bg-dark: #0a0f1d;
            --glass-card: rgba(255, 255, 255, 0.02);
            --glass-border: rgba(255, 255, 255, 0.06);
            --text-white: #ffffff;
            --text-muted: #8a99ad;
            
            /* Premium Neon Gradients */
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
            /* Ultra-Smooth Premium Ambient Background */
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

        /* Glassmorphism Header */
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

        /* Control Bar for Back Buttons */
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

        /* Subject Cards Grid Layout */
        .subject-grid, .options-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
            transition: opacity 0.4s cubic-bezier(0.25, 1, 0.5, 1), transform 0.4s cubic-bezier(0.25, 1, 0.5, 1);
        }

        .options-grid {
            display: none;
            grid-template-columns: repeat(2, 1fr); /* 2 options: Class 11 & Class 12 */
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

        /* Border Glow effects */
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

        /* Chapter Screen Panels with Ultra-Smooth Animation */
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

        /* Premium Rows Structuring */
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

        /* View/Open PDF Premium Buttons */
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

        /* Mobile Optimization */
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

    <!-- Navigation Control Bar -->
    <div class="control-bar" id="control-bar">
        <button class="btn-back" id="back-subj-btn" style="display: none;">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><line x1="19" y1="12" x2="5" y2="12"></line><polyline points="12 19 5 12 12 5"></polyline></svg>
            Back to Subjects
        </button>
        <button class="btn-back" id="back-opt-btn" style="display: none;">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><line x1="19" y1="12" x2="5" y2="12"></line><polyline points="12 19 5 12 12 5"></polyline></svg>
            Back to Classes
        </button>
    </div>

    <!-- Tier 1: Subject Selection Grid -->
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

    <!-- Tier 2: Resource Options Grid (Dynamic) -->
    <div class="options-grid" id="options-grid">
        <!-- Filled dynamically by JS -->
    </div>

    <!-- Tier 3: Chapters Content Panels -->
    <!-- PHYSICS PANEL -->
    <div id="physics" class="chapters-panel physics-view">
        <div class="panel-header">
            <span class="panel-title" id="physics-panel-title" style="color: #3b82f6;">Physics Chapters</span>
            <span class="total-badge">14 Chapters</span>
        </div>
        <div class="chapter-list">
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-01: Electrostatic Potential and Capacitance</span><span class="chapter-subtitle-text">PYQ Practice Sheet</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-02: Moving Charges and Magnetism</span><span class="chapter-subtitle-text">PYQ Practice Sheet</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-03: Dual Nature of Radiation and Matter</span><span class="chapter-subtitle-text">PYQ Practice Sheet</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-04: Ray Optics and Optical Instruments</span><span class="chapter-subtitle-text">PYQ Practice Sheet</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-05: Semiconductor Electronics</span><span class="chapter-subtitle-text">PYQ Practice Sheet</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-06: Electric Charges and Fields</span><span class="chapter-subtitle-text">PYQ Practice Sheet</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-07: Atomic Physics</span><span class="chapter-subtitle-text">PYQ Practice Sheet</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-08: Electromagnetic Waves</span><span class="chapter-subtitle-text">PYQ Practice Sheet</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-09: Wave Optics</span><span class="chapter-subtitle-text">PYQ Practice Sheet</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-10: Nuclear Physics</span><span class="chapter-subtitle-text">PYQ Practice Sheet</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-11: Electromagnetic Induction</span><span class="chapter-subtitle-text">PYQ Practice Sheet</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-12: Magnetism and Matter</span><span class="chapter-subtitle-text">PYQ Practice Sheet</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-13: Alternating Current</span><span class="chapter-subtitle-text">PYQ Practice Sheet</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-14: Current Electricity</span><span class="chapter-subtitle-text">PYQ Practice Sheet</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
        </div>
    </div>

    <!-- CHEMISTRY PANEL -->
    <div id="chemistry" class="chapters-panel chemistry-view">
        <div class="panel-header">
            <span class="panel-title" id="chemistry-panel-title" style="color: #f59e0b;">Chemistry Chapters</span>
            <span class="total-badge">10 Chapters</span>
        </div>
        <div class="chapter-list">
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-01: Solutions</span><span class="chapter-subtitle-text">Raoult's Law & Colligative Properties</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-02: Electrochemistry</span><span class="chapter-subtitle-text">Nernst Equation & Conductance</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-03: Chemical Kinetics</span><span class="chapter-subtitle-text">Rate Law & Integrated Equations</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-04: d- and f-Block Elements</span><span class="chapter-subtitle-text">Transition Metals & Lanthanoid Contraction</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-05: Coordination Compounds</span><span class="chapter-subtitle-text">IUPAC Nomenclature, VBT & CFT</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-06: Haloalkanes and Haloarenes</span><span class="chapter-subtitle-text">SN1/SN2 Mechanisms</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-07: Alcohols, Phenols and Ethers</span><span class="chapter-subtitle-text">Dehydration & Electrophilic Substitution</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-08: Aldehydes, Ketones and Carboxylic Acids</span><span class="chapter-subtitle-text">Aldol & Cannizzaro Reactions</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-09: Amines</span><span class="chapter-subtitle-text">Basicity & Diazonium Salts</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-10: Biomolecules</span><span class="chapter-subtitle-text">Carbohydrates & Proteins Structure</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
        </div>
    </div>

    <!-- MATHEMATICS PANEL -->
    <div id="maths" class="chapters-panel maths-view">
        <div class="panel-header">
            <span class="panel-title" id="maths-panel-title" style="color: #10b981;">Mathematics Chapters</span>
            <span class="total-badge">8 Chapters</span>
        </div>
        <div class="chapter-list">
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-01: Matrices and Determinants</span><span class="chapter-subtitle-text">Cramer's Rule & Inverse of Matrix</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-02: Relations and Functions</span><span class="chapter-subtitle-text">Types of Relations & Composite Functions</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-03: Inverse Trigonometric Functions</span><span class="chapter-subtitle-text">Principal Value & Properties</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-04: Continuity and Differentiability</span><span class="chapter-subtitle-text">Mean Value Theorems & Chain Rule</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-05: Application of Derivatives</span><span class="chapter-subtitle-text">Maxima, Minima & Tangents</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-06: Integrals</span><span class="chapter-subtitle-text">Definite & Indefinite Integration</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-07: Differential Equations</span><span class="chapter-subtitle-text">Variable Separable & Linear DE</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-08: Vector Algebra</span><span class="chapter-subtitle-text">Dot Product & Cross Product</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
        </div>
    </div>

</div>

<!-- SMART NAVIGATION JAVASCRIPT -->
<script>
    document.addEventListener("DOMContentLoaded", function() {
        // Elements Definition
        const subjectGrid = document.getElementById("subject-grid");
        const optionsGrid = document.getElementById("options-grid");
        const controlBar = document.getElementById("control-bar");
        const backSubjBtn = document.getElementById("back-subj-btn");
        const backOptBtn = document.getElementById("back-opt-btn");
        const panels = document.querySelectorAll(".chapters-panel");
        
        let selectedSubject = "";

        // Step 1: Subject Card Selection Click
        document.querySelectorAll(".subject-card").forEach(card => {
            card.addEventListener("click", function() {
                selectedSubject = this.getAttribute("data-target");
                const subjectName = this.querySelector(".card-title").innerText;
                
                // Hide Subjects Grid
                subjectGrid.style.display = "none";
                
                // Build dynamic Class Options grid (Tier 2) based on selection
                optionsGrid.innerHTML = `
                    <div class="option-card" data-type="${selectedSubject}" data-class="11">
                        <span class="card-icon-tag">Class XI</span>
                        <span class="card-title">Class 11 PYQs</span>
                    </div>
                    <div class="option-card" data-type="${selectedSubject}" data-class="12">
                        <span class="card-icon-tag">Class XII</span>
                        <span class="card-title">Class 12 PYQs</span>
                    </div>
                `;
                
                // Show Options Grid with proper grid display
                optionsGrid.style.display = "grid";
                
                // Adjust Control Navbar Buttons
                controlBar.classList.add("active");
                backSubjBtn.style.display = "inline-flex";
                backOptBtn.style.display = "none";

                // Add active click listeners to the new dynamic option cards
                setupOptionCards();
            });
        });

        // Step 2: Handle Tier 2 Options Click (Class 11 or 12 Selection)
        function setupOptionCards() {
            document.querySelectorAll(".option-card").forEach(card => {
                card.addEventListener("click", function() {
                    const chosenClass = this.getAttribute("data-class");
                    
                    // Hide the Class options
                    optionsGrid.style.display = "none";
                    
                    // Toggle Active Chapter Panel (Tier 3)
                    panels.forEach(p => p.classList.remove("active"));
                    const targetPanel = document.getElementById(selectedSubject);
                    
                    if (targetPanel) {
                        targetPanel.classList.add("active");
                        // Dynamically update the heading to show chosen class context
                        const panelTitle = document.getElementById(`${selectedSubject}-panel-title`);
                        if(panelTitle) {
                            panelTitle.innerText = `${selectedSubject.charAt(0).toUpperCase() + selectedSubject.slice(1)} - Class ${chosenClass} Chapters`;
                        }
                    }

                    // Update Back Bar Navigation state
                    backSubjBtn.style.display = "none";
                    backOptBtn.style.display = "inline-flex";
                });
            });
        }

        // Navigation Back Actions
        // Back from Options to Subject Grid
        backSubjBtn.addEventListener("click", function() {
            optionsGrid.style.display = "none";
            subjectGrid.style.display = "grid";
            controlBar.classList.remove("active");
            backSubjBtn.style.display = "none";
        });

        // Back from Chapters Panel to Options Grid
        backOptBtn.addEventListener("click", function() {
            panels.forEach(p => p.classList.remove("active"));
            optionsGrid.style.display = "grid";
            backOptBtn.style.display = "none";
            backSubjBtn.style.display = "inline-flex";
        });
    });
</script>

</body>