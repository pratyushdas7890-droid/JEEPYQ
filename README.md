
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

        /* --- লক স্ক্রিন স্টাইল --- */
        #lock-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            background: var(--bg-dark);
            background-image: radial-gradient(at 50% 50%, rgba(59, 130, 246, 0.15) 0px, transparent 50%);
            z-index: 99999;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }

        .lock-container {
            background: var(--glass-card);
            backdrop-filter: blur(25px);
            -webkit-backdrop-filter: blur(25px);
            border: 1px solid var(--glass-border);
            padding: 40px 30px;
            border-radius: var(--radius-main);
            max-width: 400px;
            width: 100%;
            text-align: center;
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.5);
        }

        .lock-container h2 {
            font-size: 28px;
            font-weight: 800;
            margin-bottom: 10px;
            background: linear-gradient(to right, #ffffff, #a5f3fc);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .lock-container p {
            color: var(--text-muted);
            font-size: 14px;
            margin-bottom: 25px;
        }

        .lock-input {
            width: 100%;
            padding: 16px;
            background: rgba(255, 255, 255, 0.04);
            border: 1px solid var(--glass-border);
            border-radius: var(--radius-btn);
            color: white;
            font-size: 16px;
            text-align: center;
            outline: none;
            margin-bottom: 15px;
            transition: border-color 0.3s;
        }

        .lock-input:focus {
            border-color: #3b82f6;
        }

        .lock-btn {
            width: 100%;
            padding: 16px;
            background: var(--physics-glow);
            border: none;
            border-radius: var(--radius-btn);
            color: white;
            font-size: 15px;
            font-weight: 700;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(59, 130, 246, 0.3);
            transition: transform 0.2s;
        }

        .lock-btn:hover {
            transform: translateY(-2px);
            filter: brightness(1.1);
        }

        .error-msg {
            color: #ef4444;
            font-size: 13px;
            font-weight: 600;
            margin-top: 10px;
            display: none;
            line-height: 1.4;
        }

        #main-content {
            display: none;
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
        .subject-card[data-target="chemistry"]:hover, .option-card[data-type="chemistry"]:hover { border-color: #f59e0b; box-shadow: 0 0 30px rgba(245, 158, 11, 0.25); }
        .subject-card[data-target="maths"]:hover, .option-card[data-type="maths"]:hover { border-color: #10b981; box-shadow: 0 0 30px rgba(16, 185, 129, 0.25); }

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

        .subject-card svg {
            margin: 8px 0;
            transition: transform 0.3s ease;
        }
        .subject-card:hover svg {
            transform: scale(1.1) rotate(5deg);
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

        .download-actions-group {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
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
            .download-actions-group { width: 100%; }
            .btn-download { width: 100%; text-align: center; padding: 14px; }
        }
    </style>
</head>
<body>

<!-- লক স্ক্রিন ইন্টারফেস -->
<div id="lock-screen">
    <div class="lock-container">
        <h2>JEE PYQ</h2>
        <p>Enter Password & Unlock</p>
        <input type="password" id="vault-pass" class="lock-input" placeholder="Enter password">
        <button id="unlock-btn" class="lock-btn">Unlock</button>
        <div id="lock-error" class="error-msg">Wrong password or this password already registered in another device</div>
    </div>
</div>

<!-- মূল কন্টেন্ট -->
<div id="main-content" class="container">
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
            <svg width="42" height="42" viewBox="0 0 24 24" fill="none" stroke="#3b82f6" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <ellipse cx="12" cy="12" rx="3" ry="9" transform="rotate(45 12 12)"></ellipse>
                <ellipse cx="12" cy="12" rx="3" ry="9" transform="rotate(-45 12 12)"></ellipse>
                <circle cx="12" cy="12" r="1" fill="#3b82f6"></circle>
            </svg>
            <span class="card-title" style="color: #3b82f6;">Physics</span>
        </div>
        <div class="subject-card" data-target="chemistry">
            <span class="card-icon-tag">Subject 02</span>
            <svg width="42" height="42" viewBox="0 0 24 24" fill="none" stroke="#f59e0b" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M6 3h12M14 3v5.5l5.5 10.3a2 2 0 0 1-1.7 2.9H6.2a2 2 0 0 1-1.7-2.9L10 8.5V3M8 14h8"></path>
            </svg>
            <span class="card-title" style="color: #f59e0b;">Chemistry</span>
        </div>
        <div class="subject-card" data-target="maths">
            <span class="card-icon-tag">Subject 03</span>
            <svg width="42" height="42" viewBox="0 0 24 24" fill="none" stroke="#10b981" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M18 4H6l7 8-7 8h12"></path>
            </svg>
            <span class="card-title" style="color: #10b981;">Mathematics</span>
        </div>
    </div>

    <div class="options-grid" id="options-grid"></div>
    <div id="chapters-container"></div>
</div>

<script>
    // ----------------------------------------------------
    // 🔑 পাসওয়ার্ড বুক কনফিগারেশন (নতুন পাসওয়ার্ড যুক্ত করা হয়েছে)
    // ----------------------------------------------------
    const PASSWORD_BOOK = {
        "ADMIN100": "Admin",
        "PRATYUSH77": "Pratyush",
        "ANISH55": "Anish",
        "JEE2026": "Guest",
        "1234": "pratyush",
        "0000": "komol"
    };

    function checkSecurity() {
        const lockScreen = document.getElementById("lock-screen");
        const mainContent = document.getElementById("main-content");
        const passInput = document.getElementById("vault-pass");
        const unlockBtn = document.getElementById("unlock-btn");
        const lockError = document.getElementById("lock-error");

        // ইউজারের ব্রাউজার এবং স্ক্রিনের ডেটা মিলিয়ে একটি অনন্য ডিভাইস আইডি তৈরি করা হচ্ছে
        const deviceFingerprint = btoa(navigator.userAgent + navigator.language + screen.colorDepth + (screen.width * screen.height));

        // যদি অলরেডি লগইন করা থাকে এবং ডিভাইস টোকেন ম্যাচ করে
        if (localStorage.getItem("vault_unlocked") === "true" && localStorage.getItem("registered_device") === deviceFingerprint) {
            lockScreen.style.display = "none";
            mainContent.style.display = "block";
            return;
        }

        unlockBtn.addEventListener("click", function() {
            const enteredPass = passInput.value.trim();

            // চেক করা হচ্ছে টাইপ করা পাসওয়ার্ডটি আমাদের ডিকশনারিতে আছে কিনা
            if (PASSWORD_BOOK.hasOwnProperty(enteredPass)) {
                
                // লোকাল স্টোরেজে চেক করা হচ্ছে এই নির্দিষ্ট পাসওয়ার্ডটি দিয়ে অন্য কোনো ডিভাইস অলরেডি রেজিস্টার করেছে কিনা
                const savedTokenForThisPass = localStorage.getItem("token_" + enteredPass);

                if (savedTokenForThisPass && savedTokenForThisPass !== deviceFingerprint) {
                    lockError.innerHTML = "এই পাসওয়ার্ডটি অলরেডি অন্য ফোনে ব্যবহৃত হয়েছে! শেয়ারিং অনুমোদিত নয়।";
                    lockError.style.display = "block";
                    return;
                }

                // সফল লগইন: পাসওয়ার্ডের সাথে ইউজারের বর্তমান ডিভাইসটি চিরতরে লক করে দেওয়া হলো
                localStorage.setItem("vault_unlocked", "true");
                localStorage.setItem("registered_device", deviceFingerprint);
                localStorage.setItem("token_" + enteredPass, deviceFingerprint); // পাসওয়ার্ড ম্যাপিং লক
                
                lockScreen.style.display = "none";
                mainContent.style.display = "block";
                renderApp(); // অ্যাপ্লিকেশন ইন্টারফেস লোড করার জন্য
            } else {
                lockError.innerHTML = "ভুল পাসওয়ার্ড! সঠিক পাসওয়ার্ডটি সাবধানে টাইপ করুন।";
                lockError.style.display = "block";
            }
        });

        passInput.addEventListener("keypress", function(e) {
            if (e.key === "Enter") unlockBtn.click();
        });
    }

    function renderApp() {
        const subjectGrid = document.getElementById("subject-grid");
        const optionsGrid = document.getElementById("options-grid");
        const controlBar = document.getElementById("control-bar");
        const backSubjBtn = document.getElementById("back-subj-btn");
        const chaptersContainer = document.getElementById("chapters-container");
        
        let selectedSubject = "";

        const chapterDatabase = {
            physics: [
                { ch: "CH-01", name: "Electrostatics", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1EHuENpJPugRugKawpIUW-4fOFKWlW4ZU/view?usp=drivesdk", "https://drive.google.com/file/d/1hYnoeJIW1-CVCqfi3RiuvTgQUqeJFEPU/view?usp=drivesdk"] }
            ],
            chemistry: [
                { ch: "CH-01", name: "Solid State", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1AdLBI4vl7BUO5b9E5xwrJb6Ffxd"] }
            ],
            maths: [
                { ch: "CH-01", name: "Relations and Functions", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1AdLBI4vl7BUO5b9E5xwrJb6Ffxd"] }
            ]
        };

        // সাবজেক্ট কার্ড ক্লিকে চ্যাপ্টার প্যানেল দেখানোর লজিক
        document.querySelectorAll('.subject-card').forEach(card => {
            card.addEventListener('click', function() {
                selectedSubject = this.getAttribute('data-target');
                subjectGrid.style.display = 'none';
                controlBar.classList.add('active');
                backSubjBtn.style.display = 'inline-flex';
                
                // ডাইনামিক ক্লাস অ্যাপ্লাই করার জন্য ভিউ কন্টেইনার তৈরি
                chaptersContainer.className = selectedSubject + "-view";
                
                let chaptersHtml = `
                    <div class="chapters-panel active">
                        <div class="panel-header">
                            <span class="panel-title">${selectedSubject.charAt(0).toUpperCase() + selectedSubject.slice(1)} Chapters</span>
                            <span class="total-badge">${chapterDatabase[selectedSubject].length} Modules Available</span>
                        </div>
                        <div class="chapter-list">
                `;

                chapterDatabase[selectedSubject].forEach(chapter => {
                    chaptersHtml += `
                        <div class="chapter-item">
                            <div class="chapter-details">
                                <span class="chapter-title-text">${chapter.ch}: ${chapter.name}</span>
                                <span class="chapter-subtitle-text">${chapter.sub}</span>
                            </div>
                            <div class="download-actions-group">
                    `;
                    
                    chapter.moduleLinks.forEach((link, index) => {
                        chaptersHtml += `<a href="${link}" target="_blank" class="btn-download">Download Part 0${index + 1}</a>`;
                    });

                    chaptersHtml += `
                            </div>
                        </div>
                    `;
                });

                chaptersHtml += `</div></div>`;
                chaptersContainer.innerHTML = chaptersHtml;
            });
        });

        // ব্যাক বাটনের ফাংশনালিটি
        backSubjBtn.addEventListener('click', function() {
            chaptersContainer.innerHTML = "";
            controlBar.classList.remove('active');
            backSubjBtn.style.display = 'none';
            subjectGrid.style.display = 'grid';
        });
    }

    document.addEventListener("DOMContentLoaded", function() {
        checkSecurity();
        if (localStorage.getItem("vault_unlocked") === "true") {
            renderApp();
        }
    });
</script>
</body>