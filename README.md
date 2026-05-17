
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
            --bg-dark: #070a13;
            --glass-bg: rgba(255, 255, 255, 0.03);
            --glass-border: rgba(255, 255, 255, 0.07);
            --text-white: #ffffff;
            --text-muted: #94a3b8;
            --physics-gradient: linear-gradient(135deg, #3b82f6 0%, #1d4ed8 100%);
            --chemistry-gradient: linear-gradient(135deg, #f59e0b 0%, #d97706 100%);
            --maths-gradient: linear-gradient(135deg, #10b981 0%, #059669 100%);
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
            background-image: 
                radial-gradient(at 0% 0%, rgba(59, 130, 246, 0.12) 0px, transparent 40%),
                radial-gradient(at 100% 100%, rgba(16, 185, 129, 0.08) 0px, transparent 40%);
            background-attachment: fixed;
        }

        .container {
            max-width: 850px;
            margin: 0 auto;
        }

        header {
            background: var(--glass-bg);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            padding: 40px 30px;
            border-radius: var(--radius-main);
            text-align: center;
            margin-bottom: 35px;
            border: 1px solid var(--glass-border);
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.3);
        }

        header h1 {
            font-size: 42px;
            font-weight: 800;
            letter-spacing: -1.5px;
            margin-bottom: 10px;
            background: linear-gradient(to right, #ffffff, #93c5fd);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        header p {
            color: var(--text-muted);
            font-size: 15px;
            font-weight: 500;
        }

        .control-bar {
            display: none;
            margin-bottom: 25px;
        }

        .btn-back {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid var(--glass-border);
            color: var(--text-white);
            padding: 12px 24px;
            font-size: 14px;
            font-weight: 700;
            border-radius: var(--radius-btn);
            cursor: pointer;
            display: inline-flex;
            align-items: center;
            gap: 8px;
        }

        .subject-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
        }

        .subject-card {
            background: var(--glass-bg);
            border: 1px solid var(--glass-border);
            border-radius: var(--radius-main);
            padding: 45px 25px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .subject-card:hover {
            transform: translateY(-5px);
        }

        .subject-card[data-target="physics"]:hover { border-color: #3b82f6; }
        .subject-card[data-target="chemistry"]:hover { border-color: #f59e0b; }
        .subject-card[data-target="maths"]:hover { border-color: #10b981; }

        .card-icon-tag {
            font-size: 11px;
            font-weight: 700;
            color: var(--text-muted);
            text-transform: uppercase;
            letter-spacing: 1.5px;
        }

        .card-title {
            font-size: 24px;
            font-weight: 800;
        }

        .chapters-panel {
            display: none;
            background: var(--glass-bg);
            border: 1px solid var(--glass-border);
            border-radius: var(--radius-main);
            padding: 35px;
            box-shadow: 0 25px 55px rgba(0, 0, 0, 0.4);
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
            font-size: 26px;
            font-weight: 800;
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
            background: rgba(255, 255, 255, 0.01);
            border-radius: 16px;
            border: 1px solid var(--glass-border);
        }

        .chapter-details {
            display: flex;
            flex-direction: column;
            gap: 4px;
            padding-right: 15px;
        }

        .chapter-title-text {
            font-size: 16px;
            font-weight: 700;
        }

        .chapter-subtitle-text {
            font-size: 13px;
            color: var(--text-muted);
        }

        .btn-download {
            text-decoration: none;
            color: #ffffff;
            padding: 12px 24px;
            font-size: 13px;
            font-weight: 700;
            border-radius: var(--radius-btn);
            white-space: nowrap;
            transition: all 0.2s ease;
        }

        #physics .btn-download { background: var(--physics-gradient); }
        #chemistry .btn-download { background: var(--chemistry-gradient); }
        #maths .btn-download { background: var(--maths-gradient); }

        @media (max-width: 768px) {
            .subject-grid { grid-template-columns: 1fr; }
            .chapter-item { flex-direction: column; align-items: flex-start; gap: 16px; }
            .btn-download { width: 100%; text-align: center; }
        }
    </style>
</head>
<body>

<div class="container">
    
    <header>
        <h1>JEE PYQ</h1>
        <p>Complete Chapter-wise Previous Year Questions for Class 12 Boards & Entrance Preparation.</p>
    </header>

    <!-- Back Button Control Bar -->
    <div class="control-bar" id="control-bar">
        <button class="btn-back" onclick="goBackHome()">
            ← Back to Subjects
        </button>
    </div>

    <!-- HOME VIEW: Subject Selectors -->
    <div class="subject-grid" id="subject-grid">
        <div class="subject-card" data-target="physics" onclick="openSubject('physics')">
            <span class="card-icon-tag">Subject 01</span>
            <span class="card-title" style="color: #3b82f6;">Physics</span>
        </div>
        <div class="subject-card" data-target="chemistry" onclick="openSubject('chemistry')">
            <span class="card-icon-tag">Subject 02</span>
            <span class="card-title" style="color: #f59e0b;">Chemistry</span>
        </div>
        <div class="subject-card" data-target="maths" onclick="openSubject('maths')">
            <span class="card-icon-tag">Subject 03</span>
            <span class="card-title" style="color: #10b981;">Mathematics</span>
        </div>
    </div>

    <!-- PHYSICS PANEL -->
    <div id="physics" class="chapters-panel">
        <div class="panel-header">
            <span class="panel-title" style="color: #3b82f6;">Physics Chapters</span>
            <span class="total-badge">10 Chapters</span>
        </div>
        <div class="chapter-list">
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-01: Electric Charges and Fields</span><span class="chapter-subtitle-text">Coulomb's Law, Electric Field Lines & Gauss's Theorem</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-02: Electrostatic Potential and Capacitance</span><span class="chapter-subtitle-text">Potential Difference, Equipotential Surfaces & Capacitors</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-03: Current Electricity</span><span class="chapter-subtitle-text">Drift Velocity, Kirchhoff's Laws, Potentiometer & Wheatstone Bridge</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-04: Moving Charges and Magnetism</span><span class="chapter-subtitle-text">Biot-Savart Law, Ampere's Law & Moving Coil Galvanometer</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-05: Magnetism and Matter</span><span class="chapter-subtitle-text">Magnetic Dipole, Earth's Magnetic Elements & Magnetic Materials</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-06: Electromagnetic Induction</span><span class="chapter-subtitle-text">Faraday's & Lenz's Law, Induced EMF, Self & Mutual Inductance</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-07: Alternating Current</span><span class="chapter-subtitle-text">Reactance, Impedance, LCR Series Circuit, Resonance & Wattless Current</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-08: Electromagnetic Waves</span><span class="chapter-subtitle-text">Displacement Current, Maxwell's Equations & EM Spectrum</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-09: Optics (Ray Optics & Wave Optics)</span><span class="chapter-subtitle-text">Spherical Mirrors, Lenses, Optical Instruments, Interference & Diffraction</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
            <div class="chapter-item"><div class="chapter-details"><span class="chapter-title-text">CH-10: Modern Physics & Semiconductors</span><span class="chapter-subtitle-text">Photoelectric Effect, Bohr's Model, Radioactivity & Logic Gates</span></div><a href="#" target="_blank" class="btn-download">Open PDF</a></div>
        </div>
    </div>

    <!-- CHEMISTRY PANEL -->
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

    <!-- MATHEMATICS PANEL -->
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
    // direct inline function to ensure execution
    function openSubject(subjectId) {
        // 1. Hide Grid
        document.getElementById('subject-grid').style.display = 'none';
        
        // 2. Show Target Panel
        document.getElementById(subjectId).style.display = 'block';
        
        // 3. Show Control bar
        document.getElementById('control-bar').style.display = 'block';
        
        window.scrollTo({ top: 0, behavior: 'smooth' });
    }

    function goBackHome() {
        // Hide all panels
        document.getElementById('physics').style.display = 'none';
        document.getElementById('chemistry').style.display = 'none';
        document.getElementById('maths').style.display = 'none';
        
        // Hide control bar
        document.getElementById('control-bar').style.display = 'none';
        
        // Show home grid
        document.getElementById('subject-grid').style.display = 'grid';
        
        window.scrollTo({ top: 0, behavior: 'smooth' });
    }
</script>

</body>
