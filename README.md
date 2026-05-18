
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

        #back-opt-btn {
            display: none;
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
        <button class="btn-back" id="back-subj-btn">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><line x1="19" y1="12" x2="5" y2="12"></line><polyline points="12 19 5 12 12 5"></polyline></svg>
            Back to Subjects
        </button>
        <button class="btn-back" id="back-opt-btn">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><line x1="19" y1="12" x2="5" y2="12"></line><polyline points="12 19 5 12 12 5"></polyline></svg>
            Back to Options
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
        <!-- Will be filled by JavaScript based on chosen subject -->
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
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-05: Semiconductor Electronics: Materials Devices and Simple Circuits</span><span class="chapter-subtitle-text">PYQ Practice Sheet</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
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
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-01: Solutions</span><span class="chapter-subtitle-text">Raoult's Law, Colligative Properties & Van't Hoff Factor</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-02: Electrochemistry</span><span class="chapter-subtitle-text">Nernst Equation, Conductance, Kohlrausch's Law & Fuel Cells</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-03: Chemical Kinetics</span><span class="chapter-subtitle-text">Rate Law, Order & Molecularity, Integrated Rate Equations & Arrhenius Theory</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-04: d- and f-Block Elements</span><span class="chapter-subtitle-text">Transition Metals, Lanthanoid Contraction, KMnO4 & K2Cr2O7</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-05: Coordination Compounds</span><span class="chapter-subtitle-text">IUPAC Nomenclature, Werner's Theory, VBT & CFT</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-06: Haloalkanes and Haloarenes</span><span class="chapter-subtitle-text">Nomenclature, SN1/SN2 Mechanisms & Optical Rotation</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-07: Alcohols, Phenols and Ethers</span><span class="chapter-subtitle-text">Identification Tests, Dehydration Mechanisms & Electrophilic Substitution</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-08: Aldehydes, Ketones and Carboxylic Acids</span><span class="chapter-subtitle-text">Nucleophilic Addition, Aldol Condensation & Cannizzaro Reaction</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-09: Amines</span><span class="chapter-subtitle-text">Basicity Sequence, Diazonium Salts Chemistry & Hoffmann Degradation</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-10: Biomolecules</span><span class="chapter-subtitle-text">Carbohydrates Structure, Amino Acids, Peptide Bonds & Nucleic Acids</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
        </div>
    </div>

    <!-- MATHEMATICS PANEL -->
    <div id="maths" class="chapters-panel maths-view">
        <div class="panel-header">
            <span class="panel-title" id="maths-panel-title" style="color: #10b981;">Mathematics Chapters</span>
            <span class="total-badge">10 Chapters</span>
        </div>
        <div class="chapter-list">
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-01: Relations and Functions</span><span class="chapter-subtitle-text">Equivalence Relations, One-One & Onto Functions Mapping</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-02: Inverse Trigonometric Functions</span><span class="chapter-subtitle-text">Principal Value Branch Graphs, Domain, Range & Base Properties</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-03: Matrices</span><span class="chapter-subtitle-text">Types of Matrices, Matrix Operations & Determinants</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-04: Continuity and Differentiability</span><span class="chapter-subtitle-text">Continuity Tests, Chain Rule, Parametric Forms & Rolle's Theorem</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-05: Application of Derivatives</span><span class="chapter-subtitle-text">Rate of Change, Increasing/Decreasing Functions, Maxima & Minima</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-06: Integrals</span><span class="chapter-subtitle-text">Definite & Indefinite Integrals, Substitution, Parts & Properties</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-07: Application of Integrals</span><span class="chapter-subtitle-text">Area Under Simple Curves, Lines & Parabolas</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-08: Differential Equations</span><span class="chapter-subtitle-text">Order & Degree, Variable Separable, Homogeneous & Linear Equations</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-09: Vector Algebra</span><span class="chapter-subtitle-text">Scalar & Vector Products, Direction Cosines & Position Vectors</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-10: Three Dimensional Geometry</span><span class="chapter-subtitle-text">Direction Ratios, Shortest Distance Between Lines & Equations of Lines</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
        </div>
    </div>

</div>

<script {RULE 1: STRICT COMPLETION}>
    const subjectGrid = document.getElementById('subject-grid');
    const optionsGrid = document.getElementById('options-grid');
    const controlBar = document.getElementById('control-bar');
    const backSubjBtn = document.getElementById('back-subj-btn');
    const backOptBtn = document.getElementById('back-opt-btn');
    const panels = document.querySelectorAll('.chapters-panel');

    let currentSubject = '';

    // Step 1: Click Subject Card
    document.querySelectorAll('.subject-card').forEach(card => {
        card.addEventListener('click', () => {
            currentSubject = card.getAttribute('data-target');
            renderOptions(currentSubject);
        });
    });

    // Render Options dynamically based on Subject
    function renderOptions(subject) {
        subjectGrid.style.display = 'none';
        optionsGrid.innerHTML = '';
        optionsGrid.style.display = 'grid';
        
        controlBar.classList.add('active');
        backSubjBtn.style.display = 'inline-flex';
        backOptBtn.style.display = 'none';

        let options = [];
        let color = '';
        
        if (subject === 'physics') {
            options = ['Module', 'Arihant', 'Cengage'];
            color = '#3b82f6';
        } else if (subject === 'chemistry') {
            options = ['Module', 'Arihant', 'Cengage'];
            color = '#f59e0b';
        } else if (subject === 'maths') {
            options = ['Module', 'Arihant'];
            color = '#10b981';
        }

        options.forEach((opt, idx) => {
            const optCard = document.createElement('div');
            optCard.className = 'option-card';
            optCard.setAttribute('data-type', subject);
            optCard.setAttribute('data-name', opt);
            optCard.innerHTML = `
                <span class="card-icon-tag">Resource 0${idx + 1}</span>
                <span class="card-title" style="color: ${color};">${opt}</span>
            `;
            
            // Step 2: Click Option Card
            optCard.addEventListener('click', () => {
                openChapters(subject, opt);
            });

            optionsGrid.appendChild(optCard);
        });
    }

    // Step 3: Open Final Chapters Panel
    function openChapters(subject, optionName) {
        optionsGrid.style.display = 'none';
        backSubjBtn.style.display = 'none';
        backOptBtn.style.display = 'inline-flex';

        // Update Panel Title
        const panelTitle = document.getElementById(`${subject}-panel-title`);
        let subNameFormatted = subject.charAt(0).toUpperCase() + subject.slice(1);
        if(subNameFormatted === 'Maths') subNameFormatted = 'Mathematics';
        panelTitle.innerText = `${subNameFormatted} (${optionName})`;

        const targetPanel = document.getElementById(subject);
        targetPanel.classList.add('active');
    }

    // Back to Subjects Action
    backSubjBtn.addEventListener('click', () => {
        optionsGrid.style.display = 'none';
        controlBar.classList.remove('active');
        subjectGrid.style.display = 'grid';
    });

    // Back to Options Action
    backOptBtn.addEventListener('click', () => {
        panels.forEach(p => p.classList.remove('active'));
        renderOptions(currentSubject);
    });
</script>

</body>
