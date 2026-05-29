
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
<script>
(() => {

    const ADMIN_PASSWORD = "0000";

    function getDeviceId() {
        return btoa(
            navigator.userAgent +
            navigator.platform +
            screen.width +
            screen.height +
            new Date().getTimezoneOffset()
        );
    }

    const currentDevice = getDeviceId();

    function getUsers() {
        return JSON.parse(localStorage.getItem("jee_users") || "[]");
    }

    function saveUsers(users) {
        localStorage.setItem("jee_users", JSON.stringify(users));
    }

    function getBlockedUsers() {
        return JSON.parse(localStorage.getItem("jee_blocked_users") || "[]");
    }

    function saveBlockedUsers(users) {
        localStorage.setItem("jee_blocked_users", JSON.stringify(users));
    }

    function renderAdminPanel() {

        const users = getUsers();
        const blocked = getBlockedUsers();

        const adminHTML = `
            <div id="adminPanelOverlay" style="
                position:fixed;
                inset:0;
                background:rgba(0,0,0,0.65);
                z-index:99999;
                display:flex;
                align-items:center;
                justify-content:center;
                padding:20px;
            ">

                <div style="
                    width:100%;
                    max-width:700px;
                    max-height:90vh;
                    overflow:auto;
                    background:#101827;
                    border:1px solid rgba(255,255,255,0.08);
                    border-radius:28px;
                    padding:30px;
                    color:white;
                    font-family:'Plus Jakarta Sans',sans-serif;
                ">

                    <div style="
                        display:flex;
                        justify-content:space-between;
                        align-items:center;
                        margin-bottom:25px;
                    ">
                        <h1 style="font-size:32px;font-weight:800;">
                            Admin Panel
                        </h1>

                        <button id="closeAdminPanel" style="
                            background:none;
                            border:none;
                            color:white;
                            font-size:28px;
                            cursor:pointer;
                        ">
                            ×
                        </button>
                    </div>

                    <div style="
                        display:flex;
                        flex-direction:column;
                        gap:15px;
                    ">

                        ${users.map((u, index) => `

                            <div style="
                                padding:20px;
                                border-radius:20px;
                                background:rgba(255,255,255,0.04);
                                border:1px solid rgba(255,255,255,0.08);
                            ">

                                <div style="margin-bottom:8px;">
                                    <b>Name:</b> ${u.name}
                                </div>

                                <div style="margin-bottom:8px;">
                                    <b>Phone:</b> ${u.phone}
                                </div>

                                <div style="margin-bottom:15px;">
                                    <b>Email:</b> ${u.email}
                                </div>

                                ${
                                    blocked.includes(u.device)
                                    ?
                                    `
                                    <button 
                                        class="unblockUserBtn"
                                        data-device="${u.device}"
                                        style="
                                            padding:12px 20px;
                                            border:none;
                                            border-radius:12px;
                                            background:#10b981;
                                            color:white;
                                            font-weight:700;
                                            cursor:pointer;
                                        "
                                    >
                                        Unblock User
                                    </button>
                                    `
                                    :
                                    `
                                    <button 
                                        class="blockUserBtn"
                                        data-device="${u.device}"
                                        style="
                                            padding:12px 20px;
                                            border:none;
                                            border-radius:12px;
                                            background:#ef4444;
                                            color:white;
                                            font-weight:700;
                                            cursor:pointer;
                                        "
                                    >
                                        Remove Access
                                    </button>
                                    `
                                }

                            </div>

                        `).join("")}

                    </div>

                </div>

            </div>
        `;

        document.body.insertAdjacentHTML("beforeend", adminHTML);

        document
            .getElementById("closeAdminPanel")
            .addEventListener("click", () => {

                document
                    .getElementById("adminPanelOverlay")
                    .remove();
            });

        document
            .querySelectorAll(".blockUserBtn")
            .forEach(btn => {

                btn.addEventListener("click", () => {

                    const device =
                        btn.getAttribute("data-device");

                    let blockedUsers =
                        getBlockedUsers();

                    blockedUsers.push(device);

                    saveBlockedUsers(blockedUsers);

                    location.reload();
                });
            });

        document
            .querySelectorAll(".unblockUserBtn")
            .forEach(btn => {

                btn.addEventListener("click", () => {

                    const device =
                        btn.getAttribute("data-device");

                    let blockedUsers =
                        getBlockedUsers();

                    blockedUsers =
                        blockedUsers.filter(
                            d => d !== device
                        );

                    saveBlockedUsers(blockedUsers);

                    location.reload();
                });
            });
    }

    document.addEventListener("DOMContentLoaded", () => {

        const blockedUsers = getBlockedUsers();

      if (blockedUsers.includes(currentDevice)) {

    document.body.innerHTML = `
        <div style="
            min-height:100vh;
            display:flex;
            align-items:center;
            justify-content:center;
            background:#0a0f1d;
            padding:20px;
            font-family:'Plus Jakarta Sans',sans-serif;
        ">

            <div style="
                width:100%;
                max-width:420px;
                background:rgba(255,255,255,0.04);
                border:1px solid rgba(255,255,255,0.08);
                border-radius:28px;
                padding:40px 30px;
                text-align:center;
                color:white;
            ">

                <h1 style="
                    font-size:38px;
                    margin-bottom:15px;
                    font-weight:800;
                ">
                    Access Removed
                </h1>

                <p style="
                    color:#8a99ad;
                    line-height:1.7;
                    margin-bottom:28px;
                ">
                    Your access was removed by admin.
                </p>

                <button 
                    id="loginAgainBtn"
                    style="
                        width:100%;
                        padding:15px;
                        border:none;
                        border-radius:14px;
                        background:linear-gradient(135deg,#3b82f6,#1d4ed8);
                        color:white;
                        font-size:15px;
                        font-weight:700;
                        cursor:pointer;
                    "
                >
                    Login Again
                </button>

            </div>

        </div>
    `;

    document
        .getElementById("loginAgainBtn")
        .addEventListener("click", () => {

            let blocked =
                getBlockedUsers();

            blocked =
                blocked.filter(
                    d => d !== currentDevice
                );

            saveBlockedUsers(blocked);

            localStorage.removeItem(
                "jee_logged_in"
            );

            localStorage.removeItem(
                "jee_profile"
            );

            location.reload();
        });

    return;
}

        const loggedIn =
            localStorage.getItem("jee_logged_in");

        if (!loggedIn) {

            document.body.innerHTML = `
                <div style="
                    min-height:100vh;
                    display:flex;
                    align-items:center;
                    justify-content:center;
                    background:#0a0f1d;
                    padding:20px;
                    font-family:'Plus Jakarta Sans',sans-serif;
                ">

                    <div style="
                        width:100%;
                        max-width:420px;
                        background:rgba(255,255,255,0.04);
                        border:1px solid rgba(255,255,255,0.08);
                        border-radius:28px;
                        padding:40px 30px;
                        backdrop-filter:blur(25px);
                        color:white;
                    ">

                        <h1 style="
                            text-align:center;
                            font-size:38px;
                            margin-bottom:10px;
                            font-weight:800;
                        ">
                            JEE PYQ
                        </h1>

                        <p style="
                            text-align:center;
                            color:#8a99ad;
                            margin-bottom:35px;
                        ">
                            Student Login
                        </p>

                        <input 
                            type="text"
                            id="loginName"
                            placeholder="Full Name"
                            style="
                                width:100%;
                                padding:16px;
                                margin-bottom:18px;
                                border-radius:14px;
                                border:none;
                                outline:none;
                                background:rgba(255,255,255,0.06);
                                color:white;
                            "
                        >

                        <input 
                            type="tel"
                            id="loginPhone"
                            placeholder="Phone Number"
                            style="
                                width:100%;
                                padding:16px;
                                margin-bottom:18px;
                                border-radius:14px;
                                border:none;
                                outline:none;
                                background:rgba(255,255,255,0.06);
                                color:white;
                            "
                        >

                        <input 
                            type="email"
                            id="loginEmail"
                            placeholder="Email Address"
                            style="
                                width:100%;
                                padding:16px;
                                margin-bottom:22px;
                                border-radius:14px;
                                border:none;
                                outline:none;
                                background:rgba(255,255,255,0.06);
                                color:white;
                            "
                        >

                        <button 
                            id="enterWebsiteBtn"
                            style="
                                width:100%;
                                padding:16px;
                                border:none;
                                border-radius:14px;
                                background:linear-gradient(135deg,#3b82f6,#1d4ed8);
                                color:white;
                                font-size:15px;
                                font-weight:700;
                                cursor:pointer;
                            "
                        >
                            Enter Website
                        </button>

                    </div>

                </div>
            `;

            document
                .getElementById("enterWebsiteBtn")
                .addEventListener("click", () => {

                    const name =
                        document
                        .getElementById("loginName")
                        .value.trim();

                    const phone =
                        document
                        .getElementById("loginPhone")
                        .value.trim();

                    const email =
                        document
                        .getElementById("loginEmail")
                        .value.trim();

                    if (!name || !phone || !email) {

                        alert(
                            "Please fill all details"
                        );

                        return;
                    }
                    if (!/^[0-9]{10}$/.test(phone)) {

    alert(
        "Phone number must be exactly 10 digits"
    );

    return;
}
                    if (
    !/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email)
) {

    alert(
        "Enter a valid email address"
    );

    return;
}
                    const userData = {
                        name,
                        phone,
                        email,
                        device: currentDevice
                    };

                    let users = getUsers();

                users = users.filter(
    u => u.device !== currentDevice
);

users.push(userData);

                    saveUsers(users);

                    localStorage.setItem(
                        "jee_logged_in",
                        "true"
                    );

                    localStorage.setItem(
                        "jee_profile",
                        JSON.stringify(userData)
                    );

                    location.reload();
                });

            return;
        }

        // ===== WEBSITE SHOW =====
        document.body.style.display = "block";

        // ===== 3 DOT MENU =====
        const profile =
            JSON.parse(
                localStorage.getItem("jee_profile")
            );

        const menuHTML = `
            <div style="
                position:fixed;
                top:18px;
                right:18px;
                z-index:9999;
            ">

                <button 
                    id="menuBtn"
                    style="
                        width:52px;
                        height:52px;
                        border:none;
                        border-radius:16px;
                        background:rgba(255,255,255,0.06);
                        backdrop-filter:blur(20px);
                        color:white;
                        font-size:24px;
                        cursor:pointer;
                    "
                >
                    ⋮
                </button>

                <div 
                    id="menuDropdown"
                    style="
                        position:absolute;
                        right:0;
                        top:65px;
                        width:280px;
                        background:#101827;
                        border:1px solid rgba(255,255,255,0.08);
                        border-radius:22px;
                        padding:20px;
                        display:none;
                        color:white;
                        font-family:'Plus Jakarta Sans',sans-serif;
                    "
                >

                    <div style="margin-bottom:8px;">
                        <b>${profile.name}</b>
                    </div>

                    <div style="
                        color:#8a99ad;
                        font-size:14px;
                        margin-bottom:5px;
                    ">
                        ${profile.phone}
                    </div>

                    <div style="
                        color:#8a99ad;
                        font-size:14px;
                        margin-bottom:25px;
                    ">
                        ${profile.email}
                    </div>

                    <div 
                        id="adminLoginBtn"
                        style="
                            font-size:11px;
                            color:#6b7280;
                            cursor:pointer;
                            text-align:center;
                        "
                    >
                        Admin Login
                    </div>

                </div>

            </div>
        `;

        document.body.insertAdjacentHTML(
            "beforeend",
            menuHTML
        );

        const menuBtn =
            document.getElementById("menuBtn");

        const menuDropdown =
            document.getElementById("menuDropdown");

        menuBtn.addEventListener("click", () => {

            menuDropdown.style.display =
                menuDropdown.style.display === "block"
                ? "none"
                : "block";
        });

        document
            .getElementById("adminLoginBtn")
            .addEventListener("click", () => {

                const pass =
                    prompt("Enter Admin Password");

                if (pass === ADMIN_PASSWORD) {

                    renderAdminPanel();

                } else {

                    alert("Wrong Password");
                }
            });

    });

})();
</script>
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

        // Step 1: Subject Selection
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

        // Step 2: Book Selection
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

                    // Fix: Dynamic database selection logic for Chemistry
                    let chapters = [];
                    if (selectedSubject === "chemistry") {
                        chapters = selectedBook === "Modules" ? chapterDatabase.chemistry_modules : chapterDatabase.chemistry_others;
                    } else {
                        chapters = chapterDatabase[selectedSubject];
                    }

                    let chaptersHtml = `
                        <div id="active-panel" class="chapters-panel ${viewClass} active">
                            <div class="panel-header">
                                <span class="panel-title" style="color: ${titleColor};">${selectedSubject.charAt(0).toUpperCase() + selectedSubject.slice(1)} - ${displayBookName}</span>
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

                        // Render Logic for Download Buttons
                        if (selectedBook === "Modules" && item.moduleLinks) {
                            if (item.moduleLinks.length > 1) {
                                item.moduleLinks.forEach((link, idx) => {
                                    chaptersHtml += `<a href="${link}" target="_blank" class="btn-download">Part ${idx + 1}</a>`;
                                });
                            } else if (item.moduleLinks.length === 1) {
                                chaptersHtml += `<a href="${item.moduleLinks[0]}" target="_blank" class="btn-download">Download PDF</a>`;
                            }
                        } else {
                            chaptersHtml += `<a href="#download" class="btn-download">Download PDF</a>`;
                        }

                        chaptersHtml += `
                                </div>
                            </div>
                        `;
                    });

                    chaptersHtml += `
                            </div>
                        </div>
                    `;

                    chaptersContainer.innerHTML = chaptersHtml;
                    backSubjBtn.style.display = "none";
                    backOptBtn.style.display = "inline-flex";
                });
            });
        }

        // Back Buttons Logic
        backSubjBtn.addEventListener("click", function() {
            subjectGrid.style.display = "grid";
            optionsGrid.style.display = "none";
            controlBar.classList.remove("active");
            backSubjBtn.style.display = "none";
        });

        backOptBtn.addEventListener("click", function() {
            optionsGrid.style.display = "grid";
            chaptersContainer.innerHTML = "";
            backSubjBtn.style.display = "inline-flex";
            backOptBtn.style.display = "none";
        });
    });
</script>
</body>
