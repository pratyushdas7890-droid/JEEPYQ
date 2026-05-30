
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
            position: relative;
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

        /* Nav Dropdown Floating Menu */
        .menu-container {
            position: absolute;
            top: 25px;
            right: 25px;
            z-index: 100;
        }

        .three-dot-btn {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid var(--glass-border);
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
            transition: 0.3s;
        }

        .three-dot-btn:hover {
            background: rgba(255, 255, 255, 0.15);
        }

        .three-dot-btn span {
            width: 4px;
            height: 4px;
            background-color: white;
            border-radius: 50%;
        }

        .dropdown-menu {
            display: none;
            position: absolute;
            top: 50px;
            right: 0;
            background: rgba(10, 15, 29, 0.95);
            backdrop-filter: blur(20px);
            border: 1px solid var(--glass-border);
            border-radius: 16px;
            padding: 20px;
            width: 260px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.5);
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

        .admin-login-btn, .logout-btn {
            width: 100%;
            padding: 10px;
            border-radius: 8px;
            border: none;
            cursor: pointer;
            font-weight: 600;
            font-size: 13px;
            transition: 0.3s;
        }

        .admin-login-btn {
            background: rgba(245, 158, 11, 0.1);
            color: #f59e0b;
            border: 1px solid rgba(245, 158, 11, 0.3);
            margin-bottom: 8px;
        }

        .admin-login-btn:hover { background: rgba(245, 158, 11, 0.2); }

        .logout-btn {
            background: rgba(239, 68, 68, 0.1);
            color: #ef4444;
            border: 1px solid rgba(239, 68, 68, 0.3);
        }
        .logout-btn:hover { background: rgba(239, 68, 68, 0.2); }

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
            transition: 0.3s;
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
            transition: 0.3s;
            box-shadow: 0 4px 15px rgba(59, 130, 246, 0.3);
            margin-top: 10px;
        }

        .auth-btn:hover {
            transform: translateY(-2px);
            filter: brightness(1.1);
        }

        .error-msg {
            color: #ef4444;
            font-size: 12px;
            margin-top: 5px;
            display: none;
            font-weight: 500;
        }

        /* Admin Logical Panel Wrapper */
        .admin-panel {
            display: none;
            background: var(--glass-card);
            border: 1px solid #f59e0b;
            border-radius: var(--radius-main);
            padding: 30px;
            margin-top: 30px;
        }

        .admin-table-container {
            width: 100%;
            overflow-x: auto;
            margin-top: 20px;
        }

        .admin-table {
            width: 100%;
            border-collapse: collapse;
            font-size: 14px;
            min-width: 600px;
        }

        .admin-table th, .admin-table td {
            border: 1px solid var(--glass-border);
            padding: 12px;
            text-align: left;
        }

        .admin-table th {
            background: rgba(245, 158, 11, 0.1);
            color: #f59e0b;
        }

        .btn-remove {
            background: rgba(239, 68, 68, 0.15);
            color: #ef4444;
            border: 1px solid rgba(239, 68, 68, 0.3);
            padding: 6px 12px;
            border-radius: 6px;
            cursor: pointer;
            font-size: 12px;
            font-weight: 600;
            transition: 0.2s;
        }

        .btn-remove:hover {
            background: rgba(239, 68, 68, 0.3);
        }

        /* Main Web Content Hidden View Layer */
        #main-content {
            display: none;
        }

        /* Core Elements Classes */
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
            .menu-container { top: 15px; right: 15px; }
            .dropdown-menu { right: -10px; }
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
                    <button class="admin-login-btn" id="admin-login-trigger">Admin Login</button>
                    <button class="logout-btn" id="session-logout">Reset Device</button>
                </div>
            </div>

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

        <div class="admin-panel" id="admin-database-view">
            <h3 style="color:#f59e0b; font-size:22px;">Vault User Database (Admin Mode)</h3>
            <p style="font-size:12px; margin-bottom:15px;">Secure client-side database entry logs for this node.</p>
            
            <div class="admin-table-container">
                <table class="admin-table">
                    <thead>
                        <tr>
                            <th>Student Name</th>
                            <th>Phone Number</th>
                            <th>Email Address</th>
                            <th>Login Timestamp</th>
                            <th>Action</th>
                        </tr>
                    </thead>
                    <tbody id="admin-data-rows">
                        </tbody>
                </table>
            </div>
            <button class="btn-back" style="margin-top:20px; border-color:#f59e0b; color:#f59e0b;" onclick="document.getElementById('admin-database-view').style.display='none'">Close Logs</button>
        </div>

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

        // =================================================================
        // 🔑 [এখানে আপনি স্টুডেন্টদের নাম ও পাসওয়ার্ড নিজের মতো পরিবর্তন/যোগ করুন]
        // নামগুলো টাইপ করার সময় অবশ্যই ছোট হাতের অক্ষরে (lowercase) লিখবেন।
        // =================================================================
        const USER_PASSWORD_DATABASE = {
            "anik": "1111",
            "komol": "2222",
            "arkaprava": "jee2026",
            "testuser": "pass123",
            "sayandip": "sayan5566",
            "pर्जी": "998877"
        };

        // Real-Time Blacklist Security Interceptor
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

        // Cache Device Verification Logic
        let savedUser = localStorage.getItem("vault_user_name");
        let savedPass = localStorage.getItem("vault_user_pass");

        if (!checkBlacklistStatus()) {
            if(savedUser && savedPass) {
                fullLoginForm.style.display = "none";
                quickPassForm.style.display = "block";
                document.getElementById("saved-user-display").innerText = savedUser;
            }
        }

        // Full Validation Node Authentication Process
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

        // Quick Token Password Unlock Verification Node
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

        // Admin Panel Log Recorder Functional Logic
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

        // Dropdown Menu Controllers Matrix
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

        // Admin Node Execution Engine Trigger & Live Table Rendering
        document.getElementById("admin-login-trigger").addEventListener("click", function() {
            let adminPrompt = prompt("Enter 4-Digit Secure Admin Password Pin:");
            if(adminPrompt === "0000") {
                renderAdminLogs();
                const adminPanel = document.getElementById("admin-database-view");
                adminPanel.style.display = "block";
                adminPanel.scrollIntoView({ behavior: 'smooth' });
            } else if (adminPrompt !== null) {
                alert("ACCESS DENIED: Critical Authorization Code Failure.");
            }
        });

        // Function to Draw Admin Database Rows & Delete Action Setup
        window.deleteLogRecord = function(recordId, userName) {
            if(confirm(`Are you sure you want to remove ${userName} and force logout their device?`)) {
                let blacklist = JSON.parse(localStorage.getItem("vault_blacklisted_users")) || [];
                if (!blacklist.includes(userName.toLowerCase())) {
                    blacklist.push(userName.toLowerCase());
                }
                localStorage.setItem("vault_blacklisted_users", JSON.stringify(blacklist));

                let currentLogs = JSON.parse(localStorage.getItem("admin_vault_logs")) || [];
                let filteredLogs = currentLogs.filter(log => log.id !== recordId);
                localStorage.setItem("admin_vault_logs", JSON.stringify(filteredLogs));
                
                renderAdminLogs();
                checkBlacklistStatus();
            }
        }

        function renderAdminLogs() {
            const adminRows = document.getElementById("admin-data-rows");
            let currentLogs = JSON.parse(localStorage.getItem("admin_vault_logs")) || [];
            
            if(currentLogs.length === 0) {
                adminRows.innerHTML = `<tr><td colspan="5" style="text-align:center; color:var(--text-muted);">No login history records found in this system node database.</td></tr>`;
                return;
            }

            let tableHtml = "";
            currentLogs.forEach(log => {
                tableHtml += `
                    <tr>
                        <td><strong>${log.name}</strong></td>
                        <td>${log.phone}</td>
                        <td>${log.email}</td>
                        <td style="color:var(--text-muted); font-size:12px;">${log.time}</td>
                        <td><button class="btn-remove" onclick="deleteLogRecord(${log.id}, '${log.name}')">Remove</button></td>
                    </tr>
                `;
            });
            adminRows.innerHTML = tableHtml;
        }

        // --- COMPACT SUBJECT CHANNELS DATABASE ---
        const chapterDatabase = {
            physics: [
                { ch: "CH-01", name: "Electrostatics", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1EHuENpJPugRugKawpIUW-4fOFKWlW4ZU/view?usp=drivesdk", "https://drive.google.com/file/d/1hYnoeJIW1-CVCqfi3RiuvTgQUqeJFEPU/view?usp=drivesdk", "https://drive.google.com/file/d/1AdLBI4vl7BUO5b9E5xwrJb6FfxdMzNDG/view?usp=drivesdk"] }, 
                { ch: "CH-02", name: "Current Electricity", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1C-48MABN0F9VO0YmIw75pJH3Ryfc7NAu/view?usp=drivesdk"] }, 
                { ch: "CH-03", name: "Magnetic Effects of Current and Magnetism", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1L_AP4uNfbgNbLCCBSRYwnQS9OEHPnTuL/view?usp=drivesdk", "https://drive.google.com/file/d/1IWol_bthljJwylCp48aqhPBbuhG8-n15/view?usp=drivesdk"] }, 
                { ch: "CH-04", name: "Electromagnetic Induction and Alternating Currents", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/10KJcZudJUfzDI60GayixiQrZ3kFEE998/view?usp=drivesdk", "https://drive.google.com/file/d/1qUN4pWVnM2onNbVEL14a1MP9zDqBTNtU/view?usp=drivesdk"] }, 
                { ch: "CH-05", name: "Electromagnetic Waves", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1DL7clF00NPmRCU2VwPK69IldAQxkZ7mE/view?usp=drivesdk"] }, 
                { ch: "CH-06", name: "Optics", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1CXSEWSxPQWh08jpgmwefQ-TwN1ohMOis/view?usp=drivesdk", "https://drive.google.com/file/d/1vis8a41P_4WjmzqRN42zc0D0KLs56aXA/view?usp=drivesdk"] }, 
                { ch: "CH-07", name: "Dual Nature of Matter and Radiation", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1g-OfaOASLIzs01N16aI5OTamgmEysWXv/view?usp=drivesdk"] }, 
                { ch: "CH-08", name: "Atoms and Nuclei", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1uy9hDpsrId3f_8lwq_MZY_2VBA-Ca9qa/view?usp=drivesdk", "https://drive.google.com/file/d/1Kqp4ecMeA0QnEmnZWAV4nl7NFP2nOmwy/view?usp=drivesdk"] }, 
                { ch: "CH-09", name: "Electronic Devices", sub: "PYQ Practice Sheet", moduleLinks: ["https://drive.google.com/file/d/1lfKKYDt4b7g_v-NVMc3qlxIxR1z7KjCf/view?usp=drivesdk"] } 
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

        // Step 1: Subject Selection (Your exact updated dynamic logic)
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
                        <span class="card-title" style="font-size:22px;">${book.display}</span>
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

        // Step 2: Book Selection & Rendering
        function setupBookCards() {
            document.querySelectorAll(".options-grid .option-card").forEach(card => {
                card.style.borderColor = selectedSubject === "physics" ? "#3b82f6" : selectedSubject === "maths" ? "#10b981" : "#f59e0b";
                
                card.addEventListener("click", function() {
                    if (checkBlacklistStatus()) return;
                    const selectedBook = this.getAttribute("data-book");
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
                    } else {
                        chapters = chapterDatabase[selectedSubject];
                    }

                    let chaptersHtml = `
                        <div class="chapters-panel active ${viewClass}">
                            <div class="panel-header">
                                <span class="panel-title" style="color:${titleColor}">${selectedSubject.charAt(0).toUpperCase() + selectedSubject.slice(1)} - ${displayBookName}</span>
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
                                <div class="download-actions-group">
                        `;

                        // 🛑 FIXED: Links rendering rule based on book selection
                        if (selectedBook === "Modules" && item.moduleLinks) {
                            if (item.moduleLinks.length > 1) {
                                item.moduleLinks.forEach((link, idx) => {
                                    chaptersHtml += `<a href="${link}" target="_blank" class="btn-download">Part ${idx + 1}</a>`;
                                });
                            } else if (item.moduleLinks.length === 1) {
                                chaptersHtml += `<a href="${item.moduleLinks[0]}" target="_blank" class="btn-download">Download PDF</a>`;
                            }
                        } else {
                            // Arihant & Cengage sections (or others) will show as standard disabled buttons
                            chaptersHtml += `<a href="#" class="btn-download" style="opacity:0.5; pointer-events:none;">Download PDF</a>`;
                        }

                        chaptersHtml += `</div></div>`;
                    });

                    chaptersHtml += `</div></div>`;
                    chaptersContainer.innerHTML = chaptersHtml;
                    backSubjBtn.style.display = "none";
                    backOptBtn.style.display = "inline-flex";
                    
                    // Hook security verify to file action click
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

        // Back Buttons Logic
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
    const firebaseConfig = {
  apiKey: "AIzaSyCRqGsHmOc5xrg23aEXMtfQzFi8FRVX6Fg",
  authDomain: "jeepqy.firebaseapp.com",
  databaseURL: "https://jeepqy-default-rtdb.firebaseio.com",
  projectId: "jeepqy",
  storageBucket: "jeepqy.firebasestorage.app",
  messagingSenderId: "855581745353",
  appId: "1:855581745353:web:3a76d06ca9f55f55f3ad18",
  measurementId: "G-VPE5F4B496"
};
firebase.initializeApp(firebaseConfig);
  const auth = firebase.auth();
  const database = firebase.database();
  // লগইন করানোর ফাংশন
function loginUser(email, password) {
  auth.signInWithEmailAndPassword(email, password)
    .then((userCredential) => {
      const user = userCredential.user;
      
      // ১. এই ডিভাইসের জন্য একটি ইউনিক সেশন আইডি তৈরি (Random String + Time)
      const currentSessionId = Math.random().toString(36).substring(2, 15) + Date.now();
      
      // ২. এই আইডিটি ব্রাউজারের লোকাল স্টোরেজে সেভ করে রাখা
      localStorage.setItem("device_session_id", currentSessionId);
      
      // ৩. ফায়ারবেস রিয়েল-টাইম ডেটাবেজে এই আইডিটি আপডেট করা
      database.ref('users/' + user.uid).update({
        currentSession: currentSessionId,
        lastLogin: new Date().toISOString(),
        email: user.email
      }).then(() => {
        // লগইন সফল হলে অ্যাডমিন বা ড্যাশবোর্ড পেজে নিয়ে যাওয়া
        window.location.href = "Webadmin.html"; // ⚠️ তোমার অ্যাডমিন পেজের ফাইল নাম দাও
      });

    })
    .catch((error) => {
      console.error("লগইন ব্যর্থ হয়েছে: ", error.message);
      alert("ভুল ইমেইল বা পাসওয়ার্ড! অথবা: " + error.message);
    });
}

</script>
</body>
