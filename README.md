
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
            --bg-dark: #04060d;
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
                radial-gradient(at 0% 0%, rgba(59, 130, 246, 0.16) 0px, transparent 45%),
                radial-gradient(at 100% 100%, rgba(16, 185, 129, 0.1) 0px, transparent 45%),
                radial-gradient(at 50% 50%, rgba(245, 158, 11, 0.03) 0px, transparent 50%);
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
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.4);
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

        /* Control Bar for Back Button */
        .control-bar {
            display: none;
            margin-bottom: 25px;
            opacity: 0;
            transform: translateY(-10px);
            transition: opacity 0.4s cubic-bezier(0.25, 1, 0.5, 1), transform 0.4s cubic-bezier(0.25, 1, 0.5, 1);
        }

        .control-bar.active {
            display: block;
            opacity: 1;
            transform: translateY(0);
        }

        .btn-back {
            background: rgba(255, 255, 255, 0.05);
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
            background: rgba(255, 255, 255, 0.12);
            border-color: rgba(255, 255, 255, 0.2);
            transform: translateX(-4px);
        }

        /* Subject Cards Grid Layout */
        .subject-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
            transition: opacity 0.4s cubic-bezier(0.25, 1, 0.5, 1), transform 0.4s cubic-bezier(0.25, 1, 0.5, 1);
        }

        .subject-card {
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
            box-shadow: 0 15px 35px rgba(0,0,0,0.3);
        }

        .subject-card:active {
            transform: scale(0.95);
        }

        .subject-card[data-target="physics"]:hover { border-color: #3b82f6; box-shadow: 0 0 30px rgba(59, 130, 246, 0.25); }
        .subject-card[data-target="chemistry"]:hover { border-color: #f59e0b; box-shadow: 0 0 30px rgba(245, 158, 11, 0.2); }
        .subject-card[data-target="maths"]:hover { border-color: #10b981; box-shadow: 0 0 30px rgba(16, 185, 129, 0.2); }

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
            box-shadow: 0 30px 60px rgba(0, 0, 0, 0.5);
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
            background: rgba(255, 255, 255, 0.08);
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
            background: rgba(255, 255, 255, 0.01);
            border-radius: 16px;
            border: 1px solid var(--glass-border);
            transition: background 0.3s cubic-bezier(0.25, 1, 0.5, 1), border-color 0.3s ease, transform 0.3s cubic-bezier(0.25, 1, 0.5, 1);
        }

        .chapter-item:hover {
            background: rgba(255, 255, 255, 0.04);
            border-color: rgba(255, 255, 255, 0.18);
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

        #physics .btn-download { background: var(--physics-glow); box-shadow: 0 4px 15px rgba(59, 130, 246, 0.3); }
        #chemistry .btn-download { background: var(--chemistry-glow); box-shadow: 0 4px 15px rgba(245, 158, 11, 0.25); }
        #maths .btn-download { background: var(--maths-gradient); box-shadow: 0 4px 15px rgba(16, 185, 129, 0.25); }

        /* Mobile Optimization */
        @media (max-width: 768px) {
            body { padding: 25px 12px; }
            header { padding: 35px 20px; margin-bottom: 25px; }
            header h1 { font-size: 36px; }
            .subject-grid { grid-template-columns: 1fr; gap: 15px; }
            .subject-card { padding: 40px 20px; }
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
        <p>Complete Chapter-wise Previous Year Questions for Class 12 Boards & Entrance Preparation.</p>
    </header>

    <div class="control-bar" id="control-bar">
        <button class="btn-back" id="back-btn">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><line x1="19" y1="12" x2="5" y2="12"></line><polyline points="12 19 5 12 12 5"></polyline></svg>
            Back to Subjects
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

    <div id="physics" class="chapters-panel">
        <div class="panel-header">
            <span class="panel-title" style="color: #3b82f6;">Physics Chapters</span>
            <span class="total-badge">14 Chapters</span>
        </div>
        <div class="chapter-list">
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-01: Electrostatic Potential and Capacitance</span><span class="chapter-subtitle-text">PYQ Practice Sheet ~ Physics</span></div><a href="https://drive.google.com/file/d/19o1A0KhLXBJCKUeU-BicPdJvwtp-ChUW/view?usp=drivesdk" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-02: Moving Charges and Magnetism</span><span class="chapter-subtitle-text">PYQ Practice Sheet ~ Physics</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-03: Dual Nature of Radiation and Matter</span><span class="chapter-subtitle-text">PYQ Practice Sheet ~ Physics</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-04: Ray Optics and Optical Instruments</span><span class="chapter-subtitle-text">PYQ Practice Sheet ~ Physics</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-05: Semiconductor Electronics: Materials Devices and Simple Circuits</span><span class="chapter-subtitle-text">PYQ Practice Sheet</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-06: Electric Charges and Fields</span><span class="chapter-subtitle-text">PYQ Practice Sheet ~ Physics</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-07: Atomic Physics</span><span class="chapter-subtitle-text">PYQ Practice Sheet ~ Physics</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-08: Electromagnetic Waves</span><span class="chapter-subtitle-text">PYQ Practice Sheet ~ Physics</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-09: Wave Optics</span><span class="chapter-subtitle-text">PYQ Practice Sheet ~ Physics</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-10: Nuclear Physics</span><span class="chapter-subtitle-text">PYQ Practice Sheet ~ Physics</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-11: Electromagnetic Induction</span><span class="chapter-subtitle-text">PYQ Practice Sheet ~ Physics</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-12: Magnetism and Matter</span><span class="chapter-subtitle-text">PYQ Practice Sheet ~ Physics</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-13: Alternating Current</span><span class="chapter-subtitle-text">PYQ Practice Sheet ~ Physics</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-14: Current Electricity</span><span class="chapter-subtitle-text">PYQ Practice Sheet ~ Physics</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
        </div>
    </div>

    <div id="chemistry" class="chapters-panel">
        <div class="panel-header">
            <span class="panel-title" style="color: #f59e0b;">Chemistry Chapters</span>
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

    <div id="maths" class="chapters-panel">
        <div class="panel-header">
            <span class="panel-title" style="color: #10b981;">Mathematics Chapters</span>
            <span class="total-badge">10 Chapters</span>
        </div>
        <div class="chapter-list">
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-01: Relations and Functions</span><span class="chapter-subtitle-text">Equivalence Relations, One-One & Onto Functions Mapping</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-02: Inverse Trigonometric Functions</span><span class="chapter-subtitle-text">Principal Value Branch Graphs, Domain, Range & Base Properties</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-03: Matrices</span><span class="chapter-subtitle-text">Types of Matrices, Matrix Operations, Symmetric & Skew-Symmetric Matrices</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-04: Determinants</span><span class="chapter-subtitle-text">Minors, Co-factors, Adjoint, Inverse & Cramer's Rule Linear Solutions</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-05: Continuity and Differentiability</span><span class="chapter-subtitle-text">Continuity Parameters, Implicit/Parametric Differentiation & MVT</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-06: Applications of Derivatives (AOD)</span><span class="chapter-subtitle-text">Rate Measurement, Tangents & Normals, Monotonicity & Maxima-Minima</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-07: Integrals</span><span class="chapter-subtitle-text">Indefinite Integral Methods, Definite Integrals & Base Properties Evaluations</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-08: Applications of Integrals (AOI)</span><span class="chapter-subtitle-text">Area Computation Bound Under Standard Curves, Parabolas & Circles</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-09: Differential Equations & Vectors</span><span class="chapter-subtitle-text">Variable Separable, Homogeneous/Linear Equations & Dot/Cross Products</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-10: Three Dimensional Geometry & Probability</span><span class="chapter-subtitle-text">Shortest Distance Lines, Planes Routing, Conditional Probability & Bayes Theorem</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
        </div>
    </div>

</div>

<script>
    document.addEventListener("DOMContentLoaded", function () {
        const cards = document.querySelectorAll('.subject-card');
        const panels = document.querySelectorAll('.chapters-panel');
        const grid = document.getElementById('subject-grid');
        const controlBar = document.getElementById('control-bar');
        const backBtn = document.getElementById('back-btn');

        // Dynamic Open Animation Loop
        cards.forEach(function (card) {
            card.addEventListener('click', function () {
                const targetId = card.getAttribute('data-target');
                
                grid.style.display = 'none';
                
                panels.forEach(function (panel) {
                    if (panel.id === targetId) {
                        panel.style.display = 'block';
                        // Clean frame thread execution for hardware accelerated animation
                        requestAnimationFrame(() => {
                            panel.classList.add('active');
                        });
                    } else {
                        panel.style.display = 'none';
                        panel.classList.remove('active');
                    }
                });
                
                controlBar.style.display = 'block';
                requestAnimationFrame(() => {
                    controlBar.classList.add('active');
                });

                window.scrollTo({ top: 0, behavior: 'smooth' });
            });
        });

        // Safe Reset Navigation View Action
        backBtn.addEventListener('click', function () {
            panels.forEach(function (panel) {
                panel.classList.remove('active');
                panel.style.display = 'none';
            });
            
            controlBar.classList.remove('active');
            controlBar.style.display = 'none';
            
            grid.style.display = 'grid';
            window.scrollTo({ top: 0, behavior: 'smooth' });
        });
    });
</script>

</body>
