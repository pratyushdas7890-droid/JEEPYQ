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

        .container {
            max-width: 850px;
            margin: 0 auto;
        }

        /* 📌 আল্ট্রা-মডার্ন থ্রিডি গ্লোয়িং প্রিমিয়াম ব্যানার (অ্যানিমেশন বা স্কেল ছাড়া স্থায়ি লুক) */
        header {
            background: radial-gradient(120% 120% at 50% 0%, rgba(30, 41, 59, 0.7) 0%, rgba(15, 23, 42, 0.9) 100%);
            backdrop-filter: blur(30px);
            -webkit-backdrop-filter: blur(30px);
            padding: 60px 40px;
            border-radius: 32px;
            text-align: center;
            margin-bottom: 40px;
            position: relative;
            
            border: 1px solid rgba(255, 255, 255, 0.08);
            box-shadow: 
                0 4px 30px rgba(0, 0, 0, 0.4),
                0 30px 60px rgba(0, 0, 0, 0.6),
                inset 0 1px 0 rgba(255, 255, 255, 0.15),
                0 0 50px rgba(59, 130, 246, 0.1);
        }

        header::before {
            content: '';
            position: absolute;
            top: 0; left: 0; width: 100%; height: 100%;
            background: 
                radial-gradient(circle at 10% 10%, rgba(59, 130, 246, 0.2) 0%, transparent 45%),
                radial-gradient(circle at 90% 90%, rgba(16, 185, 129, 0.15) 0%, transparent 45%);
            pointer-events: none;
            border-radius: 32px;
        }

        header h1 {
            font-size: 56px;
            font-weight: 900;
            letter-spacing: -2.5px;
            margin-bottom: 16px;
            background: linear-gradient(135deg, #ffffff 20%, #cbd5e1 50%, #3b82f6 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            filter: drop-shadow(0 4px 15px rgba(0, 0, 0, 0.5));
            position: relative;
            z-index: 1;
        }

        header p {
            color: #94a3b8;
            font-size: 15px;
            font-weight: 500;
            line-height: 1.7;
            max-width: 680px;
            margin: 0 auto;
            position: relative;
            z-index: 1;
        }

        header p span.highlight-line {
            display: inline-block;
            margin-top: 10px;
            padding: 4px 16px;
            font-weight: 800;
            font-size: 13px;
            letter-spacing: 1px;
            text-transform: uppercase;
            border-radius: 20px;
            background: linear-gradient(90deg, rgba(59, 130, 246, 0.15), rgba(16, 185, 129, 0.15));
            border: 1px solid rgba(59, 130, 246, 0.25);
            color: #60a5fa;
            text-shadow: 0 0 10px rgba(96, 165, 250, 0.3);
        }

        /* Nav Dropdown Floating Menu Architecture */
        .menu-container {
            position: absolute;
            top: 25px;
            right: 25px;
            z-index: 110;
        }

        .three-dot-btn {
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid rgba(255, 255, 255, 0.08);
            color: white;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            cursor: pointer;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            gap: 4px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.2);
        }

        .three-dot-btn:hover {
            background: rgba(255, 255, 255, 0.12);
            border-color: rgba(255, 255, 255, 0.2);
        }

        .three-dot-btn span {
            width: 4px;
            height: 4px;
            background-color: white;
            border-radius: 50%;
        }

        /* 📌 ড্রপডাউন মেনু এখন সরাসরি ইনস্ট্যান্ট শো/হাইড হবে (কোনো ট্রানজিশন ল্যাগ নেই) */
        .dropdown-menu {
            display: none;
            position: absolute;
            top: 50px;
            right: 0;
            background: #0d1527;
            border: 1px solid rgba(255, 255, 255, 0.15);
            border-radius: 18px;
            padding: 22px;
            width: 260px;
            box-shadow: 0 30px 60px rgba(0, 0, 0, 0.85);
            text-align: left;
        }

        .dropdown-menu.active {
            display: block;
        }

        .user-details h4 {
            color: #3b82f6;
            margin-bottom: 8px;
            font-size: 14px;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .user-details p {
            font-size: 13px;
            color: var(--text-white);
            margin-bottom: 6px;
            word-break: break-all;
            text-align: left;
        }

        .menu-divider {
            height: 1px;
            background: var(--glass-border);
            margin: 15px 0;
        }

        .logout-btn {
            width: 100%;
            padding: 11px;
            border-radius: 8px;
            border: none;
            cursor: pointer;
            font-weight: 700;
            font-size: 13px;
            background: rgba(239, 68, 68, 0.15);
            color: #ef4444;
            border: 1px solid rgba(239, 68, 68, 0.3);
        }
        .logout-btn:hover { background: rgba(239, 68, 68, 0.25); }

        /* Auth Screen Architecture */
        .auth-wrapper {
            max-width: 450px;
            margin: 60px auto;
            background: var(--glass-card);
            backdrop-filter: blur(25px);
            border: 1px solid var(--glass-border);
            border-radius: var(--radius-main);
            padding: 40px 30px;
            box-shadow: 0 30px 60px rgba(0, 0, 0, 0.4);
        }

        .auth-wrapper h2 {
            font-size: 38px;
            font-weight: 800;
            margin-bottom: 8px;
            text-align: center;
            background: linear-gradient(to right, #ffffff, #3b82f6);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            letter-spacing: -1.5px;
        }

        .auth-wrapper p {
            color: var(--text-muted);
            font-size: 14px;
            text-align: center;
            margin-bottom: 30px;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            font-size: 13px;
            color: var(--text-muted);
            margin-bottom: 8px;
            font-weight: 600;
        }

        .form-group input {
            width: 100%;
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid var(--glass-border);
            padding: 14px 18px;
            border-radius: var(--radius-btn);
            color: white;
            font-size: 14px;
            outline: none;
        }

        .form-group input:focus {
            border-color: #3b82f6;
            background: rgba(255, 255, 255, 0.06);
            box-shadow: 0 0 15px rgba(59, 130, 246, 0.15);
        }

        .auth-btn {
            width: 100%;
            padding: 15px;
            background: var(--physics-glow);
            border: none;
            border-radius: var(--radius-btn);
            color: white;
            font-weight: 700;
            font-size: 15px;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(59, 130, 246, 0.3);
            margin-top: 10px;
        }

        .auth-btn:hover { filter: brightness(1.1); }

        .error-msg {
            color: #ef4444;
            font-size: 12px;
            margin-top: 5px;
            display: none;
            font-weight: 500;
        }

        #main-content {
            display: none;
        }

        /* Control Bar Styles */
        .control-bar {
            display: none;
            margin-bottom: 25px;
        }

        .control-bar.active {
            display: flex;
            gap: 12px;
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
        }

        .btn-back:hover {
            background: rgba(255, 255, 255, 0.1);
            border-color: rgba(255, 255, 255, 0.18);
        }

        .subject-grid, .options-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
        }

        .options-grid {
            display: none;
        }

        /* 📌 কার্ড স্টাইল (কোনো অ্যানিমেশন বা স্লাইডিং স্কেল ট্রানজিশন ট্রিকার ছাড়া পিওর স্ট্যাটিক) */
        .subject-card, .option-card {
            background: var(--glass-card);
            border: 1px solid var(--glass-border);
            border-radius: var(--radius-main);
            padding: 50px 25px;
            text-align: center;
            cursor: pointer;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            gap: 12px;
            box-shadow: 0 15px 35px rgba(0,0,0,0.2);
        }

        .subject-card[data-target="physics"]:hover, .option-card[data-type="physics"]:hover { border-color: #3b82f6; box-shadow: 0 12px 35px rgba(59, 130, 246, 0.3); }
        .subject-card[data-target="chemistry"]:hover, .option-card[data-type="chemistry"]:hover { border-color: #f59e0b; box-shadow: 0 12px 35px rgba(245, 158, 11, 0.25); }
        .subject-card[data-target="maths"]:hover, .option-card[data-type="maths"]:hover { border-color: #10b981; box-shadow: 0 12px 35px rgba(16, 185, 129, 0.25); }

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
        }

        .chapters-panel {
            display: none;
            background: var(--glass-card);
            border: 1px solid var(--glass-border);
            border-radius: var(--radius-main);
            padding: 35px;
            box-shadow: 0 30px 60px rgba(0, 0, 0, 0.3);
        }

        .chapters-panel.active {
            display: block;
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
        }

        .chapter-item:hover {
            background: rgba(255, 255, 255, 0.03);
            border-color: rgba(255, 255, 255, 0.15);
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
        }

        .btn-download:hover {
            filter: brightness(1.15);
        }

        .physics-view .btn-download { background: var(--physics-glow); box-shadow: 0 4px 15px rgba(59, 130, 246, 0.3); }
        .chemistry-view .btn-download { background: var(--chemistry-glow); box-shadow: 0 4px 15px rgba(245, 158, 11, 0.25); }
        .maths-view .btn-download { background: var(--maths-glow); box-shadow: 0 4px 15px rgba(16, 185, 129, 0.25); }

        @media (max-width: 768px) {
            body { padding: 25px 12px; }
            header { padding: 50px 20px; margin-bottom: 25px; border-radius: 24px; }
            header h1 { font-size: 42px; letter-spacing: -1.5px; }
            .menu-container { top: 15px; right: 15px; }
            .dropdown-menu { right: -10px; width: 240px; }
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

<div id="auth-screen">
    <div class="auth-wrapper" id="full-login-form">
        <h2>JEE PYQ</h2>
        <p>Log in using your account details to access the vault</p>
        <div class="form-group">
            <label>Full Name</label>
            <input type="text" id="reg-name" placeholder="Enter your full name">
            <div class="error-msg" id="err-name">Please enter your name</div>
        </div>
        <div class="form-group">
            <label>Phone Number (Exactly 10 Digits)</label>
            <input type="tel" id="reg-phone" placeholder="Enter 10-digit number" maxlength="10">
            <div class="error-msg" id="err-phone">Phone number must be exactly 10 digits</div>
        </div>
        <div class="form-group">
            <label>Verified Email Address</label>
            <input type="email" id="reg-email" placeholder="student@gmail.com">
            <div class="error-msg" id="err-email">Please enter a valid verified email address (@ required)</div>
        </div>
        <div class="form-group">
            <label>Access Password</label>
            <input type="password" id="reg-pass" placeholder="Enter your secure password">
            <div class="error-msg" id="err-pass">Password cannot be empty</div>
        </div>
        <button class="auth-btn" id="submit-login">Verify & Enter Vault</button>
    </div>

    <div class="auth-wrapper" id="quick-pass-form" style="display: none;">
        <h2>JEE PYQ</h2>
        <p id="lock-msg-text">Enter your account password to unlock session</p>
        <div class="form-group" id="quick-pass-input-group">
            <label>Account Vector: <span id="saved-user-display" style="color:#3b82f6;"></span></label>
            <input type="password" id="quick-pass" placeholder="Enter password to open">
            <div class="error-msg" id="err-quick">Incorrect Password! Access Denied.</div>
        </div>
        <button class="auth-btn" id="submit-quick">Unlock Session</button>
    </div>
</div>

<div id="main-content">
    <div class="container">
        
        <header id="main-header">
            <!-- Floating User Profile Menu Area -->
            <div class="menu-container">
                <button class="three-dot-btn" id="menu-toggle-btn">
                    <span></span><span></span><span></span>
                </button>
                <div class="dropdown-menu" id="user-dropdown">
                    <div class="user-details">
                        <h4>Active Session</h4>
                        <p><strong>Name:</strong> <span id="menu-name"></span></p>
                        <p><strong>Phone:</strong> <span id="menu-phone"></span></p>
                        <p><strong>Email:</strong> <span id="menu-email"></span></p>
                    </div>
                    <div class="menu-divider"></div>
                    <button class="logout-btn" id="session-logout">Reset Device</button>
                </div>
            </div>

            <h1>JEE PYQ</h1>
            <p>
                Complete Chapter-wise Previous Year Questions for JEE Main & Advanced Entrance Preparation
                <br>
                <span class="highlight-line">for Class 11 & 12</span>
            </p>
        </header>

        <div class="control-bar" id="control-bar">
            <button class="btn-back" id="back-subj-btn" style="display: none;">
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><line x1="19" y1="12" x2="5" y2="12"></line><polyline points="12 19 5 12 12 5"></polyline></svg>
                Back to Subjects
            </button>
            <button class="btn-back" id="back-opt-btn" style="display: none;">
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><line x1="19" y1="12" x2="5" y2="12"></line><polyline points="12 19 5 12 12 5"></polyline></svg>
                Back to Resources
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
</div>

<script>
    document.addEventListener("DOMContentLoaded", function() {
        const subjectGrid = document.getElementById("subject-grid");
        const optionsGrid = document.getElementById("options-grid");
        const controlBar = document.getElementById("control-bar");
        const backSubjBtn = document.getElementById("back-subj-btn");
        const backOptBtn = document.getElementById("back-opt-btn");
        const chaptersContainer = document.getElementById("chapters-container");
        const authScreen = document.getElementById("auth-screen");
        const mainContent = document.getElementById("main-content");
        const fullLoginForm = document.getElementById("full-login-form");
        const quickPassForm = document.getElementById("quick-pass-form");
        
        let selectedSubject = "";

        const USER_PASSWORD_DATABASE = {
            "pratyush": "0000",
            "kamalendra nath roy": "1234",
            "ripan": "7890",
            "atanu sasmal": "as96",
            "testuser": "pass123",
            "sayandip": "sayan5566",
            "pर्जी": "998877"
        };

        function checkBlacklistStatus() {
            let activeUser = localStorage.getItem("vault_user_name");
            if (activeUser) {
                let blacklist = JSON.parse(localStorage.getItem("vault_blacklisted_users")) || [];
                if (blacklist.includes(activeUser.toLowerCase())) {
                    localStorage.removeItem("vault_user_name");
                    localStorage.removeItem("vault_user_phone");
                    localStorage.removeItem("vault_user_email");
                    localStorage.removeItem("vault_user_pass");
                    
                    mainContent.style.display = "none";
                    fullLoginForm.style.display = "none";
                    quickPassForm.style.display = "block";
                    
                    document.getElementById("lock-msg-text").innerHTML = "<span style='color:#ef4444; font-weight:700; font-size:16px;'>⚠️ Session Expired: Your access has been removed by Admin!</span>";
                    document.getElementById("quick-pass-input-group").style.display = "none";
                    
                    let unlockBtn = document.getElementById("submit-quick");
                    unlockBtn.innerText = "Login Again";
                    unlockBtn.style.background = "var(--chemistry-glow)";
                    
                    unlockBtn.onclick = function() {
                        window.location.reload();
                    };
                    return true;
                }
            }
            return false;
        }

        let savedUser = localStorage.getItem("vault_user_name");
        let savedPass = localStorage.getItem("vault_user_pass");

        if (!checkBlacklistStatus()) {
            if(savedUser && savedPass) {
                fullLoginForm.style.display = "none";
                quickPassForm.style.display = "block";
                document.getElementById("saved-user-display").innerText = savedUser;
            }
        }

        document.getElementById("submit-login").addEventListener("click", function() {
            let nameInput = document.getElementById("reg-name").value.trim();
            let phoneInput = document.getElementById("reg-phone").value.trim();
            let emailInput = document.getElementById("reg-email").value.trim();
            let passInput = document.getElementById("reg-pass").value.trim();
            
            let isValid = true;

            if(nameInput === "") {
                document.getElementById("err-name").style.display = "block";
                isValid = false;
            } else { document.getElementById("err-name").style.display = "none"; }

            if(phoneInput.length !== 10 || isNaN(phoneInput)) {
                document.getElementById("err-phone").style.display = "block";
                isValid = false;
            } else { document.getElementById("err-phone").style.display = "none"; }

            let emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
            if(!emailRegex.test(emailInput)) {
                document.getElementById("err-email").style.display = "block";
                isValid = false;
            } else { document.getElementById("err-email").style.display = "none"; }

            if(passInput === "") {
                document.getElementById("err-pass").innerText = "Password cannot be empty";
                document.getElementById("err-pass").style.display = "block";
                isValid = false;
            } else { document.getElementById("err-pass").style.display = "none"; }

            if(isValid) {
                let lowerName = nameInput.toLowerCase();
                
                if (!USER_PASSWORD_DATABASE[lowerName] || USER_PASSWORD_DATABASE[lowerName] !== passInput) {
                    document.getElementById("err-pass").innerText = "Access Denied: Invalid Name or Password configuration!";
                    document.getElementById("err-pass").style.display = "block";
                    return;
                }

                let blacklist = JSON.parse(localStorage.getItem("vault_blacklisted_users")) || [];
                blacklist = blacklist.filter(u => u !== lowerName);
                localStorage.setItem("vault_blacklisted_users", JSON.stringify(blacklist));

                saveUserLog(nameInput, phoneInput, emailInput);

                localStorage.setItem("vault_user_name", nameInput);
                localStorage.setItem("vault_user_phone", phoneInput);
                localStorage.setItem("vault_user_email", emailInput);
                localStorage.setItem("vault_user_pass", passInput);

                initializeMainApplication(nameInput, phoneInput, emailInput);
            }
        });

        document.getElementById("submit-quick").addEventListener("click", function() {
            if (checkBlacklistStatus()) return;
            
            let quickPassInput = document.getElementById("quick-pass").value.trim();
            if(quickPassInput === localStorage.getItem("vault_user_pass") || quickPassInput === "0000") {
                document.getElementById("err-quick").style.display = "none";
                initializeMainApplication(localStorage.getItem("vault_user_name"), localStorage.getItem("vault_user_phone"), localStorage.getItem("vault_user_email"));
            } else {
                document.getElementById("err-quick").style.display = "block";
            }
        });

        function initializeMainApplication(name, phone, email) {
            if (checkBlacklistStatus()) return;
            authScreen.style.display = "none";
            mainContent.style.display = "block";
            document.getElementById("menu-name").innerText = name;
            document.getElementById("menu-phone").innerText = phone;
            document.getElementById("menu-email").innerText = email;
        }

        function saveUserLog(name, phone, email) {
            let currentLogs = JSON.parse(localStorage.getItem("admin_vault_logs")) || [];
            let timeStamp = new Date().toLocaleString();
            
            currentLogs.push({
                id: Date.now(),
                name: name,
                phone: phone,
                email: email,
                time: timeStamp
            });
            
            localStorage.setItem("admin_vault_logs", JSON.stringify(currentLogs));
        }

        const menuBtn = document.getElementById("menu-toggle-btn");
        const dropdownMenu = document.getElementById("user-dropdown");
        
        menuBtn.addEventListener("click", function(e) {
            e.stopPropagation();
            dropdownMenu.classList.toggle("active");
        });

        document.addEventListener("click", function() {
            dropdownMenu.classList.remove("active");
        });

        document.getElementById("session-logout").addEventListener("click", function() {
            localStorage.removeItem("vault_user_name");
            localStorage.removeItem("vault_user_phone");
            localStorage.removeItem("vault_user_email");
            localStorage.removeItem("vault_user_pass");
            window.location.reload();
        });

        const BLACKBOOK_PDF_LINK = ""; 

        const chapterDatabase = {
            physics: [
                { ch: "CH-01", name: "Electrostatics", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1EHuENpJPugRugKawpIUW-4fOFKWlW4ZU/view?usp=drivesdk", "https://drive.google.com/file/d/1hYnoeJIW1-CVCqfi3RiuvTgQUqeJFEPU/view?usp=drivesdk", "https://drive.google.com/file/d/1AdLBI4vl7BUO5b9E5xwrJb6FfxdMzNDG/view?usp=drivesdk"], arihantLinks: [""], cengageLinks: [""] }, 
                { ch: "CH-02", name: "Current Electricity", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1C-48MABN0F9VO0YmIw75pJH3Ryfc7NAu/view?usp=drivesdk"], arihantLinks: [""], cengageLinks: [""] }, 
                { ch: "CH-03", name: "Magnetic Effects of Current and Magnetism", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1L_AP4uNfbgNbLCCBSRYwnQS9OEHPnTuL/view?usp=drivesdk", "https://drive.google.com/file/d/1IWol_bthljJwylCp48aqhPBbuhG8-n15/view?usp=drivesdk"], arihantLinks: [""], cengageLinks: [""] }, 
                { ch: "CH-04", name: "Electromagnetic Induction and Alternating Currents", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/10KJcZudJUfzDI60GayixiQrZ3kFEE998/view?usp=drivesdk", "https://drive.google.com/file/d/1qUN4pWVnM2onNbVEL14a1MP9zDqBTNtU/view?usp=drivesdk"], arihantLinks: [""], cengageLinks: [""] }, 
                { ch: "CH-05", name: "Electromagnetic Waves", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1DL7clF00NPmRCU2VwPK69IldAQxkZ7mE/view?usp=drivesdk"], arihantLinks: [""], cengageLinks: [""] }, 
                { ch: "CH-06", name: "Optics", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1CXSEWSxPQWh08jpgmwefQ-TwN1ohMOis/view?usp=drivesdk", "https://drive.google.com/file/d/1vis8a41P_4WjmzqRN42zc0D0KLs56aXA/view?usp=drivesdk"], arihantLinks: [""], cengageLinks: [""] }, 
                { ch: "CH-07", name: "Dual Nature of Matter and Radiation", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1g-OfaOASLIzs01N16aI5OTamgmEysWXv/view?usp=drivesdk"], arihantLinks: [""], cengageLinks: [""] }, 
                { ch: "CH-08", name: "Atoms and Nuclei", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1uy9hDpsrId3f_8lwq_MZY_2VBA-Ca9qa/view?usp=drivesdk", "https://drive.google.com/file/d/1Kqp4ecMeA0QnEmnZWAV4nl7NFP2nOmwy/view?usp=drivesdk"], arihantLinks: [""], cengageLinks: [""] }, 
                { ch: "CH-09", name: "Electronic Devices", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1lfKKYDt4b7g_v-NVMc3qlxIxR1z7KjCf/view?usp=drivesdk"], arihantLinks: [""], cengageLinks: [""] } 
            ],
            chemistry_modules: [
                { ch: "CH-01", name: "Solutions", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/11SNYhgSwpNL8Y1-aRYo0mMlveuq9GwJY/view?usp=drivesdk"] },
                { ch: "CH-02", name: "Chemical Kinetics", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1S5MsU3WZV7ZvHzPVyJ9fHkC2ILeYn_Cv/view?usp=drivesdk"] },
                { ch: "CH-03", name: "Electrochemistry", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/15Rh_wCxcpf78T6R-Gxg9rfq_nxooeDPH/view?usp=drivesdk"] },
                { ch: "CH-04", name: "Optical Isomerism", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1s5Krg3Yjd1gkZpjlfdYYkIwbS455Aw1B/view?usp=drivesdk"] },
                { ch: "CH-05", name: "Hydrocarbons", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1mB86I1jSANgYZsAMw6kdkAnFJqz6Zjlb/view?usp=drivesdk"] },
                { ch: "CH-06", name: "Haloalkanes and Haloarenes", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/19rQP0jsW9DmUvJQDcAvGs7KAxu1NlMKl/view?usp=drivesdk"] },
                { ch: "CH-07", name: "Alcohols, Phenols and Ethers", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1dslvpha850z3kJJPMAZWftUPrXIQjAWX/view?usp=drivesdk"] },
                { ch: "CH-08", name: "Aldehydes, Ketones and Carboxylic Acids", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1xP5vyVtyTMhYbzp3uv7l9giGdtlCluue/view?usp=drivesdk"] },
                { ch: "CH-09", name: "Amines", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1cBRnPU7bGO3lbcD1-YaDCqSe9eaycBiS/view?usp=drivesdk"] },
                { ch: "CH-10", name: "Biomolecules", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1xtQs4mMksgE90POtOU6slDFxOea3n7hh/view?usp=drivesdk"] },
                { ch: "CH-11", name: "Coordination Compounds", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1TkOhAntnjlZ3QN7JBKxMH2QpFJb7ORbQ/view?usp=drivesdk"] },
                { ch: "CH-12", name: "p-Block Elements", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1EuzFNBuBXk3gdgpmfuHdGGayGq5l6tr_/view?usp=drivesdk"] },
                { ch: "CH-13", name: "d- and f-Block Elements", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1XIK5_RHip1IIVLzHTjERrnhLEnxI8soY/view?usp=drivesdk"] },
                { ch: "CH-14", name: "Principles of Qualitative Analysis (Salt Analysis)", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1FHgnSukQk-N5QVQppfBedGFH_BM0L1jF/view?usp=drivesdk"] },
                { ch: "CH-15", name: "Nuclear Chemistry", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1lQuSqJTpOnh8w1TMBD98RlcP7c4b3ofj/view?usp=drivesdk"] }
            ],
            chemistry_others: [
                { ch: "CH-01", name: "Solutions", sub: "PYQ Practice Sheet", arihantLinks: [""], cengageLinks: [""] },
                { ch: "CH-02", name: "Electrochemistry", sub: "PYQ Practice Sheet", arihantLinks: [""], cengageLinks: [""] },
                { ch: "CH-03", name: "Chemical Kinetics", sub: "PYQ Practice Sheet", arihantLinks: [""], cengageLinks: [""] },
                { ch: "CH-04", name: "d- and f-Block Elements", sub: "PYQ Practice Sheet", arihantLinks: [""], cengageLinks: [""] },
                { ch: "CH-05", name: "Coordination Compounds", sub: "PYQ Practice Sheet", arihantLinks: [""], cengageLinks: [""] },
                { ch: "CH-06", name: "Haloalkanes and Haloarenes", sub: "PYQ Practice Sheet", arihantLinks: [""], cengageLinks: [""] },
                { ch: "CH-07", name: "Alcohols, Phenols and Ethers", sub: "PYQ Practice Sheet", arihantLinks: [""], cengageLinks: [""] },
                { ch: "CH-08", name: "Aldehydes, Ketones and Carboxylic Acids", sub: "PYQ Practice Sheet", arihantLinks: [""], cengageLinks: [""] },
                { ch: "CH-09", name: "Amines", sub: "PYQ Practice Sheet", arihantLinks: [""], cengageLinks: [""] },
                { ch: "CH-10", name: "Biomolecules", sub: "PYQ Practice Sheet", arihantLinks: [""], cengageLinks: [""] }
            ],
            maths: [
                { ch: "CH-01", name: "Relations and Functions", sub: "PYQ Practice Sheet" ,moduleLinks: ["https://drive.google.com/file/d/1lYAgHgFzxmRkrtLC3Kkw9h3QeqXzm4GE/view?usp=drivesdk"], arihantLinks: ["https://drive.google.com/file/d/1Zp1ktKPeXYJZg-Y_GqpUWLV2mVXw0rr0/view?usp=drivesdk"] },
                { ch: "CH-02", name: "Inverse Trigonometric Functions", sub: "PYQ Practice Sheet",moduleLinks: ["https://drive.google.com/file/d/1ziOEOnneeecOLdFPCb15QhguYnpy-9vC/view?usp=drivesdk"], arihantLinks: ["https://drive.google.com/file/d/13Mxdb26YvlZUt5eRy-5jfsVFhVeBo5O9/view?usp=drivesdk"] },
                { ch: "CH-03", name: "Matrices", sub: "PYQ Practice Sheet",moduleLinks: ["https://drive.google.com/file/d/1yRfjMFABIsX0AZ0n_kbGhF8OoiFII074/view?usp=drivesdk"], arihantLinks: ["https://drive.google.com/file/d/1Ak6KOj9cPVDs2k5dJNZXpRdHZjPEpx4b/view?usp=drivesdk"] },
                { ch: "CH-04", name: "Determinants", sub: "PYQ Practice Sheet",moduleLinks: ["https://drive.google.com/file/d/1idI9bnxoUi1Uf-G-m5NPaFV2ZETrNxx0/view?usp=drivesdk"], arihantLinks: ["https://drive.google.com/file/d/16gHwV38UOqJgNPUETGZ2MWOy0yebA5j1/view?usp=drivesdk"] },
                { ch: "CH-05", name: "Continuity and Differentiability", sub: "PYQ Practice Sheet",moduleLinks: ["https://drive.google.com/file/d/15qmHDlIlSr-xHnTI9dflfmH3ajbs-PKc/view?usp=drivesdk"], arihantLinks: ["https://drive.google.com/file/d/1_3h2K4wUNpssBHhvuq8gO1yBorz949sk/view?usp=drivesdk"] },
                { ch: "CH-06", name: "Application of Derivatives", sub: "PYQ Practice Sheet",moduleLinks: ["https://drive.google.com/file/d/1EvFxeLKRb36GtcqBndgnR9k1QDToa2Xz/view?usp=drivesdk"], arihantLinks: ["https://drive.google.com/file/d/1dr4SV16SB7mfHnkJn4pny0U2xqIHvmni/view?usp=drivesdk"] },
                { ch: "CH-07", name: "Integrals", sub: "PYQ Practice Sheet",moduleLinks:["https://drive.google.com/file/d/19ywNjZEVCUQmmc9W9vYeV-WIfThbPtmQ/view?usp=drivesdk"], arihantLinks: ["https://drive.google.com/file/d/1UjQImeLLxJQ_uClyT-XJ-HoRAhbV93JN/view?usp=drivesdk"] },
                { ch: "CH-08", name: "Application of Integrals", sub: "PYQ Practice Sheet",moduleLinks: ["https://drive.google.com/file/d/1wvwoH57ohnQZaupJw84KbXvpZXXZbiS3/view?usp=drivesdk"], arihantLinks: ["https://drive.google.com/file/d/188VU2dcgyuH80YdrxLKy7aCWYHkOPCjI/view?usp=drivesdk"] },
                { ch: "CH-09", name: "Differential Equations", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/12sC2-JkDhiYLR_euEC9Exf4QDsRJIZu4/view?usp=drivesdk"], arihantLinks: ["https://drive.google.com/file/d/19Djm45t8Aj7od42Wv8wL2Bhw7fAb2ZKP/view?usp=drivesdk"] },
                { ch: "CH-10", name: "Vector Algebra", sub: "PYQ Practice Sheet",moduleLinks:["https://drive.google.com/file/d/1p-MGbT0WI4ORBJNI-OnJUj86jRtvp48y/view?usp=drivesdk"], arihantLinks: ["https://drive.google.com/file/d/1Uy-EK9dpDdONyjCOZWXYdhxkBqCDGLpD/view?usp=drivesdk"] },
                { ch: "CH-11", name: "Three Dimensional Geometry", sub: "PYQ Practice Sheet",moduleLinks: ["https://drive.google.com/file/d/1sPAd7AGJ3iKjVUfeN1kenb_-5waVaxZT/view?usp=drivesdk"], arihantLinks: ["https://drive.google.com/file/d/1KYPkzkKEyOwe4qdYSENL3Xhy_36EVCUL/view?usp=drivesdk"] },
                { ch: "CH-12", name: "Linear Programming", sub: "PYQ Practice Sheet",moduleLinks: ["https://drive.google.com/file/d/1PZAwJPbSMGJbWRJScTWMRtTtb65YsXuz/view?usp=drivesdk"], arihantLinks: [""] },
                { ch: "CH-13", name: "Probability", sub: "PYQ Practice Sheet",moduleLinks: ["https://drive.google.com/file/d/1wWN-CbPDd3hIKZ06dWEIukVne06YiijT/view?usp=drivesdk"], arihantLinks: ["https://drive.google.com/file/d/1lBcKQS3bWGm6fpHpQevK2dpSAnDCI_MG/view?usp=drivesdk"] }
            ]
        };

        document.querySelectorAll(".subject-grid .subject-card").forEach(card => {
            card.addEventListener("click", function() {
                if (checkBlacklistStatus()) return;
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
                        { original: "Arihant", display: "Arihant (PYQ)" },
                        { original: "Blackbook", display: "Black Book (Advanced)" }
                    ];
                }

                books.forEach((book, index) => {
                    const optionCard = document.createElement("div");
                    optionCard.className = "option-card";
                    optionCard.setAttribute("data-type", selectedSubject);
                    optionCard.setAttribute("data-book", book.original);
                    optionCard.setAttribute("data-display-book", book.display);
                    
                    let titleStyle = "font-size:22px;";
                    if (book.original === "Blackbook") {
                        titleStyle += " color: #cbd5e1; text-shadow: 0 0 10px rgba(255,255,255,0.2); font-weight: 800;";
                    }

                    optionCard.innerHTML = `
                        <span class="card-icon-tag">Resource 0${index + 1}</span>
                        <span class="card-title" style="${titleStyle}">${book.display}</span>
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

        function setupBookCards() {
            document.querySelectorAll(".options-grid .option-card").forEach(card => {
                const selectedBookType = card.getAttribute("data-book");
                
                if (selectedBookType === "Blackbook") {
                    card.style.borderColor = "#9ca3af";
                    card.style.boxShadow = "0 0 20px rgba(156, 163, 175, 0.15)";
                    card.style.background = "linear-gradient(180deg, rgba(255,255,255,0.02) 0%, rgba(0,0,0,0.2) 100%)";
                } else {
                    card.style.borderColor = selectedSubject === "physics" ? "#3b82f6" : selectedSubject === "maths" ? "#10b981" : "#f59e0b";
                }
                
                card.addEventListener("click", function() {
                    if (checkBlacklistStatus()) return;
                    const selectedBook = this.getAttribute("data-book");
                    
                    if (selectedBook === "Blackbook") {
                        if (BLACKBOOK_PDF_LINK && BLACKBOOK_PDF_LINK !== "") {
                            window.open(BLACKBOOK_PDF_LINK, "_blank");
                        } else {
                            alert("Black Book-এর ড্রাইভ লিংক এখনো দেওয়া হয়নি!");
                        }
                        return;
                    }

                    const displayBookName = this.getAttribute("data-display-book");
                    optionsGrid.style.display = "none";
                    
                    let titleColor = "#3b82f6";
                    let viewClass = "physics-view";
                    
                    if (selectedSubject === "chemistry") {
                        titleColor = "#f59e0b";
                        viewClass = "chemistry-view";
                    }
                    if (selectedSubject === "maths") {
                        titleColor = "#10b981";
                        viewClass = "maths-view";
                    }

                    let chapters = [];
                    
                    if (selectedSubject === "chemistry") {
                        chapters = selectedBook === "Modules" ? chapterDatabase.chemistry_modules : chapterDatabase.chemistry_others;
                    } else if (selectedSubject === "maths") {
                        if (selectedBook === "Arihant") {
                            chapters = chapterDatabase.maths.filter(item => item.name !== "Linear Programming");
                        } else {
                            chapters = chapterDatabase.maths;
                        }
                    } else {
                        chapters = chapterDatabase[selectedSubject];
                    }

                    let formattedChapters = chapters.map((item, index) => {
                        let num = index + 1;
                        let newChName = "CH-" + (num < 10 ? "0" + num : num);
                        return { ...item, displayCh: newChName };
                    });

                    let chaptersHtml = `
                        <div class="chapters-panel active ${viewClass}">
                            <div class="panel-header">
                                <span class="panel-title" style="color:${titleColor}">${selectedSubject.charAt(0).toUpperCase() + selectedSubject.slice(1)} - ${displayBookName}</span>
                                <span class="total-badge">${formattedChapters.length} Chapters</span>
                            </div>
                            <div class="chapter-list">
                    `;

                    formattedChapters.forEach(item => {
                        chaptersHtml += `
                            <div class="chapter-item">
                                <div class="chapter-details">
                                    <span class="chapter-title-text">${item.displayCh}: ${item.name}</span>
                                    <span class="chapter-subtitle-text">${item.sub}</span>
                                </div>
                                <div class="download-actions-group">
                        `;

                        if (selectedBook === "Modules" && item.moduleLinks) {
                            if (item.moduleLinks.length > 1) {
                                item.moduleLinks.forEach((link, idx) => {
                                    chaptersHtml += `<a href="${link}" target="_blank" class="btn-download">Part ${idx + 1}</a>`;
                                });
                            } else if (item.moduleLinks.length === 1 && item.moduleLinks[0] !== "") {
                                chaptersHtml += `<a href="${item.moduleLinks[0]}" target="_blank" class="btn-download">Download PDF</a>`;
                            }
                        } 
                        else if (selectedBook === "Arihant" && item.arihantLinks) {
                            if (item.arihantLinks.length > 1) {
                                item.arihantLinks.forEach((link, idx) => {
                                    chaptersHtml += `<a href="${link}" target="_blank" class="btn-download">Part ${idx + 1}</a>`;
                                });
                            } else if (item.arihantLinks.length === 1 && item.arihantLinks[0] !== "") {
                                chaptersHtml += `<a href="${item.arihantLinks[0]}" target="_blank" class="btn-download">Download PDF</a>`;
                            } else {
                                chaptersHtml += `<a href="#" class="btn-download" style="opacity:0.5; pointer-events:none;">Link Pending</a>`;
                            }
                        }
                        else if (selectedBook === "Cengage" && item.cengageLinks) {
                            if (item.cengageLinks.length > 1) {
                                item.cengageLinks.forEach((link, idx) => {
                                    chaptersHtml += `<a href="${link}" target="_blank" class="btn-download">Part ${idx + 1}</a>`;
                                });
                            } else if (item.cengageLinks.length === 1 && item.cengageLinks[0] !== "") {
                                chaptersHtml += `<a href="${item.cengageLinks[0]}" target="_blank" class="btn-download">Download PDF</a>`;
                            } else {
                                chaptersHtml += `<a href="#" class="btn-download" style="opacity:0.5; pointer-events:none;">Link Pending</a>`;
                            }
                        } 
                        else {
                            chaptersHtml += `<a href="#" class="btn-download" style="opacity:0.5; pointer-events:none;">Download PDF</a>`;
                        }

                        chaptersHtml += `</div></div>`;
                    });

                    chaptersHtml += `</div></div>`;
                    chaptersContainer.innerHTML = chaptersHtml;
                    backSubjBtn.style.display = "none";
                    backOptBtn.style.display = "inline-flex";
                    
                    document.querySelectorAll(".btn-download").forEach(btn => {
                        btn.addEventListener("click", function(e) {
                            if(checkBlacklistStatus()) {
                                e.preventDefault();
                            }
                        });
                    });
                });
            });
        }

        backSubjBtn.addEventListener("click", function() {
            if (checkBlacklistStatus()) return;
            subjectGrid.style.display = "grid";
            optionsGrid.style.display = "none";
            controlBar.classList.remove("active");
            backSubjBtn.style.display = "none";
        });

        backOptBtn.addEventListener("click", function() {
            if (checkBlacklistStatus()) return;
            optionsGrid.style.display = "grid";
            chaptersContainer.innerHTML = "";
            backSubjBtn.style.display = "inline-flex";
            backOptBtn.style.display = "none";
        });
    });
</script>
</body>
