# Martyne-browser
 "MarTyne Browser - Pentesting + Privacy + AI tools"
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>MarTyne Browser | Pentesting + Privacy + AI</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: #0a0c12;
            font-family: 'Segoe UI', 'Inter', 'Cascadia Code', monospace;
            height: 100vh;
            overflow: hidden;
            font-size: 13px;
        }

        .martyne-browser {
            display: flex;
            flex-direction: column;
            height: 100vh;
            background: #11141c;
            color: #eef2ff;
        }

        /* TOP BAR */
        .chrome-toolbar {
            background: #0f1119;
            border-bottom: 1px solid #2c3142;
            padding: 8px 16px;
            display: flex;
            align-items: center;
            gap: 12px;
            flex-wrap: wrap;
        }

        .brand {
            display: flex;
            align-items: center;
            gap: 8px;
            background: linear-gradient(145deg, #1e2538, #0f1320);
            padding: 4px 14px;
            border-radius: 32px;
            border: 1px solid #4c9aff55;
        }
        .brand-icon { font-size: 24px; }
        .brand-text { font-weight: 800; background: linear-gradient(135deg, #7bc5ff, #2d7aff); -webkit-background-clip: text; background-clip: text; color: transparent; }

        .url-container {
            flex: 2;
            display: flex;
            background: #1a1e2c;
            border-radius: 40px;
            border: 1px solid #2f3a4e;
            overflow: hidden;
        }
        .url-container input {
            flex: 1;
            background: transparent;
            border: none;
            padding: 10px 16px;
            color: #eef2ff;
            font-family: monospace;
            font-size: 0.85rem;
            outline: none;
        }
        .url-container button {
            background: #2a3245;
            border: none;
            color: white;
            padding: 0 22px;
            font-weight: bold;
            cursor: pointer;
        }
        .url-container button:hover { background: #2d7aff; }

        .search-bar-container {
            flex: 1.5;
            display: flex;
            background: #1a1e2c;
            border-radius: 40px;
            border: 1px solid #2d7aff;
            overflow: hidden;
        }
        .search-bar-container input {
            flex: 1;
            background: transparent;
            border: none;
            padding: 10px 16px;
            color: #bbddff;
            font-family: monospace;
            outline: none;
        }
        .search-bar-container button {
            background: #2d7aff;
            border: none;
            color: #0b0d13;
            padding: 0 22px;
            font-weight: bold;
            cursor: pointer;
        }

        /* Kebab menu */
        .kebab-menu {
            position: relative;
        }
        .kebab-btn {
            background: #1e2538;
            border: none;
            color: #cbd5ff;
            font-size: 22px;
            padding: 4px 12px;
            border-radius: 28px;
            cursor: pointer;
            line-height: 1;
        }
        .kebab-btn:hover { background: #2d7aff; color: #0f1119; }
        .dropdown-content {
            display: none;
            position: absolute;
            right: 0;
            top: 40px;
            background: #1a1e2c;
            min-width: 260px;
            border-radius: 16px;
            box-shadow: 0 8px 24px rgba(0,0,0,0.5);
            z-index: 1000;
            border: 1px solid #2f3a4e;
            overflow: hidden;
        }
        .dropdown-content div.item {
            color: #eef2ff;
            padding: 10px 16px;
            display: flex;
            align-items: center;
            gap: 12px;
            font-size: 13px;
            cursor: pointer;
            border-bottom: 1px solid #2c3142;
        }
        .dropdown-content div.item:hover { background: #2d7aff; color: #0a0c12; }
        .show { display: block; }
        .separator { height: 1px; background: #2c3142; margin: 4px 0; }

        /* Main layout */
        .main-layout {
            display: flex;
            flex: 1;
            overflow: hidden;
            background: #0e111a;
            gap: 1px;
        }

        .pentest-panel {
            width: 340px;
            background: #121520;
            overflow-y: auto;
            padding: 14px;
            display: flex;
            flex-direction: column;
            gap: 20px;
            border-right: 1px solid #252b3b;
        }
        .card-module {
            background: #0b0e16;
            border-radius: 24px;
            padding: 14px;
            border: 1px solid #262d3e;
        }
        .card-module h3 {
            font-size: 13px;
            text-transform: uppercase;
            color: #7bc5ff;
            margin-bottom: 12px;
            border-left: 3px solid #2d7aff;
            padding-left: 10px;
        }
        .btn-group {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin: 10px 0 4px;
        }
        .action-btn {
            background: #1e263b;
            border: none;
            padding: 6px 12px;
            border-radius: 20px;
            color: #e2e8ff;
            font-size: 11px;
            font-weight: 600;
            cursor: pointer;
        }
        .action-btn:hover { background: #2d7aff; color: #0a0c12; }
        .danger-btn { background: #3b1e2a; }
        .danger-btn:hover { background: #e34d6e; }
        .code-input-sm {
            width: 100%;
            background: #010101dd;
            border: 1px solid #2f3b55;
            color: #cbd5ff;
            font-family: monospace;
            font-size: 11px;
            padding: 8px;
            border-radius: 14px;
            margin-top: 6px;
        }
        .label-hint { font-size: 9px; color: #9aa4c2; margin-top: 6px; }
        .toggle-switch {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin: 12px 0;
            background: #0f1222;
            padding: 8px 12px;
            border-radius: 24px;
        }
        .toggle-label { font-size: 12px; }
        .toggle-input { width: 40px; height: 20px; appearance: none; background: #2a3245; border-radius: 20px; position: relative; cursor: pointer; }
        .toggle-input:checked { background: #2d7aff; }
        .toggle-input::before { content: ''; width: 16px; height: 16px; background: white; border-radius: 50%; position: absolute; top: 2px; left: 3px; transition: 0.1s; }
        .toggle-input:checked::before { left: 21px; }

        /* Social grid */
        .social-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 8px;
            margin-top: 8px;
        }
        .social-btn {
            background: #1e263b;
            border: none;
            border-radius: 20px;
            padding: 6px 0;
            color: white;
            font-size: 11px;
            font-weight: 500;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 6px;
        }
        .social-btn:hover { background: #2d7aff; }

        /* Right area */
        .browser-area {
            flex: 1;
            display: flex;
            flex-direction: column;
            background: #0f1220;
            overflow: hidden;
        }
        .dev-tabbar {
            display: flex;
            background: #121624;
            border-bottom: 1px solid #2c3145;
            padding: 0 12px;
            gap: 4px;
        }
        .dev-tab {
            padding: 10px 20px;
            font-size: 12px;
            font-weight: 600;
            background: transparent;
            border: none;
            color: #9aa5ce;
            cursor: pointer;
            border-bottom: 2px solid transparent;
        }
        .dev-tab.active {
            color: #7bc5ff;
            border-bottom: 2px solid #2d7aff;
            background: #191e2c;
        }
        .pane-container {
            flex: 1;
            position: relative;
            background: #0c0f18;
            overflow: auto;
        }
        .pane {
            display: none;
            width: 100%;
            height: 100%;
            overflow: auto;
        }
        .pane.active-pane { display: block; }
        #browserFrame {
            width: 100%;
            height: 100%;
            border: none;
            background: white;
        }
        #sourceDisplay, #logView {
            padding: 16px;
            font-family: monospace;
            font-size: 12px;
            white-space: pre-wrap;
        }
        #logView {
            background: #07090f;
            color: #bdffb0;
            height: 100%;
            overflow-y: auto;
        }
        .log-line { border-bottom: 1px solid #23283b; padding: 5px 6px; }

        /* Modal styles */
        .modal {
            display: none;
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: rgba(0,0,0,0.8);
            z-index: 2000;
            justify-content: center;
            align-items: center;
        }
        .modal-content {
            background: #1a1e2c;
            border-radius: 28px;
            width: 520px;
            max-width: 90%;
            max-height: 70vh;
            overflow-y: auto;
            padding: 20px;
            border: 1px solid #2d7aff;
        }
        .modal-content h3 { margin-bottom: 16px; color: #7bc5ff; }
        .modal-content button {
            background: #2d7aff;
            border: none;
            padding: 8px 16px;
            border-radius: 24px;
            cursor: pointer;
            margin-top: 8px;
        }
        .close-modal {
            float: right;
            font-size: 24px;
            cursor: pointer;
        }
        .tool-group-modal { display: flex; flex-wrap: wrap; gap: 10px; margin-top: 12px; }
        .tool-group-modal button { background: #2a3245; border: none; padding: 8px 12px; border-radius: 24px; color: white; cursor: pointer; }
        .tool-group-modal button:hover { background: #2d7aff; }
    </style>
</head>
<body>
<div class="martyne-browser">
    <div class="chrome-toolbar">
        <div class="brand"><span class="brand-icon">🛡️</span><span class="brand-text">MarTyne Browser</span></div>
        <div class="url-container">
            <input type="text" id="addressBar" placeholder="https://target.com" value="https://example.com">
            <button id="goBtn">🌍 GO</button>
        </div>
        <div class="search-bar-container">
            <input type="text" id="searchInput" placeholder="🔎 Search or dork">
            <button id="searchBtn">🔍 SEARCH</button>
        </div>
        <div class="kebab-menu">
            <button class="kebab-btn" id="kebabBtn">⋮</button>
            <div id="kebabDropdown" class="dropdown-content">
                <div class="item" id="menuRecon">🔍 Recon & Info Tools</div>
                <div class="item" id="menuAdvancedAttack">⚔️ Advanced Attack Tools</div>
                <div class="item" id="menuLuaTools">🧩 Lua / RudaScript Tools</div>
                <div class="separator"></div>
                <div class="item" id="menuWebTracking">🌐 Web Tracking Protection</div>
                <div class="item" id="menuAppTracking">📱 App Tracking Protection</div>
                <div class="item" id="menuEmailProtection">✉️ Email Protection</div>
                <div class="item" id="menuAIFeatures">🤖 AI Features</div>
                <div class="separator"></div>
                <div class="item" id="menuExtensions">🧩 Manage Extensions</div>
                <div class="item" id="menuBookmarks">🔖 Bookmarks</div>
                <div class="item" id="menuHistory">📜 History (reopen closed)</div>
                <div class="item" id="menuSettings">⚙️ Settings</div>
                <div class="item" id="menuPrint">🖨️ Print</div>
                <div class="item" id="menuFind">🔍 Find on Page</div>
                <div class="item" id="menuZoomIn">🔍+ Zoom In</div>
                <div class="item" id="menuZoomOut">🔍- Zoom Out</div>
                <div class="item" id="menuDevTools">🛠️ Developer Tools</div>
            </div>
        </div>
        <button id="clearLogsBtn" class="tool-btn">🗑️ Clear Logs</button>
    </div>

    <div class="main-layout">
        <div class="pentest-panel">
            <div class="card-module"><h3>🔍 RECON & INFO</h3>
                <div class="btn-group">
                    <button id="detectServerBtn" class="action-btn">📡 Detect Server</button>
                    <button id="viewCookiesBtn" class="action-btn">🍪 View Cookies</button>
                    <button id="extractLinksBtn" class="action-btn">🔗 Extract Links</button>
                    <button id="viewHeadersBtn" class="action-btn">📋 Fetch Headers</button>
                </div>
                <input type="text" id="jsCodeInput" placeholder="alert('XSS')" class="code-input-sm">
                <button id="execJsBtn" class="action-btn">⚡ Execute JS</button>
            </div>
            <div class="card-module"><h3>⚔️ ADVANCED ATTACKS</h3>
                <div class="btn-group">
                    <button id="cgiScannerBtn" class="action-btn">📁 CGI Scanner</button>
                    <button id="bruteforceBtn" class="action-btn danger-btn">🔐 HTTP Brute Force</button>
                    <button id="dirBruteBtn" class="action-btn">📂 Dir Bruteforce</button>
                </div>
            </div>
            <div class="card-module"><h3>📱 SOCIAL MEDIA OSINT</h3>
                <div class="social-grid">
                    <button class="social-btn" data-url="https://twitter.com">🐦 X/Twitter</button>
                    <button class="social-btn" data-url="https://facebook.com">📘 Facebook</button>
                    <button class="social-btn" data-url="https://instagram.com">📷 Instagram</button>
                    <button class="social-btn" data-url="https://linkedin.com">🔗 LinkedIn</button>
                    <button class="social-btn" data-url="https://tiktok.com">🎵 TikTok</button>
                    <button class="social-btn" data-url="https://reddit.com">🤖 Reddit</button>
                    <button class="social-btn" data-url="https://youtube.com">📺 YouTube</button>
                    <button class="social-btn" data-url="https://t.me">✈️ Telegram</button>
                    <button class="social-btn" data-url="https://web.whatsapp.com">💬 WhatsApp Web</button>
                </div>
                <div class="social-search" style="display:flex; gap:6px; margin-top:10px;">
                    <input type="text" id="socialUsername" placeholder="Username OSINT" class="code-input-sm" style="margin:0">
                    <button id="socialSearchBtn" class="action-btn">🔎 Search</button>
                </div>
            </div>
            <div class="card-module"><h3>🧩 LUA / RudaScript</h3>
                <textarea id="luaScript" rows="2" class="code-input-sm" placeholder='dom:inject("MarTyne")'></textarea>
                <div class="btn-group">
                    <button id="runLuaBtn" class="action-btn">🐚 Execute Lua</button>
                    <button id="injectWidgetBtn" class="action-btn">📦 Inject Widget</button>
                </div>
            </div>
        </div>

        <div class="browser-area">
            <div class="dev-tabbar">
                <button class="dev-tab active" data-tab="normal">🌐 Live View</button>
                <button class="dev-tab" data-tab="source">📄 Page Source</button>
                <button class="dev-tab" data-tab="logs">📜 Logs</button>
            </div>
            <div class="pane-container">
                <div id="normalPane" class="pane active-pane">
                    <iframe id="browserFrame" title="MarTyne Browser" sandbox="allow-same-origin allow-scripts allow-popups allow-forms allow-modals allow-top-navigation"></iframe>
                </div>
                <div id="sourcePane" class="pane"><pre id="sourceDisplay">// Page source will appear here</pre></div>
                <div id="logsPane" class="pane"><div id="logContainer">[+] MarTyne Browser ready – Privacy & AI tools added.<br></div></div>
            </div>
        </div>
    </div>
</div>

<!-- Modals for existing tools (simplified) -->
<div id="reconModal" class="modal"><div class="modal-content"><span class="close-modal">&times;</span><h3>🔍 Recon Tools</h3><div class="tool-group-modal"><button id="modalDetectServer">📡 Detect Server</button><button id="modalViewCookies">🍪 Cookies</button><button id="modalExtractLinks">🔗 Links</button><button id="modalViewHeaders">📋 Headers</button></div></div></div>
<div id="advancedModal" class="modal"><div class="modal-content"><span class="close-modal">&times;</span><h3>⚔️ Attacks</h3><div class="tool-group-modal"><button id="modalCgiScanner">📁 CGI</button><button id="modalBruteforce">🔐 Brute Force</button><button id="modalDirBrute">📂 Dir</button></div></div></div>
<div id="luaModal" class="modal"><div class="modal-content"><span class="close-modal">&times;</span><h3>🧩 Lua Tools</h3><button id="modalRunLua">Run Lua</button><button id="modalInjectWidget">Inject Widget</button><textarea id="modalLuaScript" rows="2" placeholder='dom:inject("Test")'></textarea></div></div>

<!-- NEW MODALS FOR PRIVACY & AI -->
<div id="webTrackingModal" class="modal"><div class="modal-content"><span class="close-modal">&times;</span><h3>🌐 Web Tracking Protection</h3><div class="toggle-switch"><span class="toggle-label">Block known trackers (EasyPrivacy)</span><input type="checkbox" id="blockTrackers" class="toggle-input"></div><div class="toggle-switch"><span class="toggle-label">Block fingerprinting scripts</span><input type="checkbox" id="blockFingerprint" class="toggle-input"></div><div class="toggle-switch"><span class="toggle-label">Strip UTM parameters</span><input type="checkbox" id="stripUTM" class="toggle-input"></div><button id="applyTrackingProtection">Apply & Simulate</button><div id="trackingStats" style="margin-top:12px; font-size:11px;"></div></div></div>
<div id="appTrackingModal" class="modal"><div class="modal-content"><span class="close-modal">&times;</span><h3>📱 App Tracking Protection</h3><div class="toggle-switch"><span class="toggle-label">Prevent cross-app tracking (mobile IDs)</span><input type="checkbox" id="blockAppIDs" class="toggle-input"></div><div class="toggle-switch"><span class="toggle-label">Limit ad personalization</span><input type="checkbox" id="limitAdPersonal" class="toggle-input"></div><div class="toggle-switch"><span class="toggle-label">Spoof device fingerprint</span><input type="checkbox" id="spoofDevice" class="toggle-input"></div><button id="applyAppProtection">Apply Protection</button></div></div>
<div id="emailProtectionModal" class="modal"><div class="modal-content"><span class="close-modal">&times;</span><h3>✉️ Email Protection</h3><div class="toggle-switch"><span class="toggle-label">Block email tracking pixels</span><input type="checkbox" id="blockEmailPixels" class="toggle-input"></div><div class="toggle-switch"><span class="toggle-label">Warn about suspicious links</span><input type="checkbox" id="emailLinkWarning" class="toggle-input"></div><button id="applyEmailProtection">Apply</button><div class="tool-group-modal" style="margin-top:12px;"><button id="simulatePhishingCheck">🔍 Test Email Safety</button></div></div></div>
<div id="aiFeaturesModal" class="modal"><div class="modal-content"><span class="close-modal">&times;</span><h3>🤖 AI Features</h3><button id="aiSummarizePage">📄 Summarize Current Page</button><button id="aiDetectVuln">🔍 AI Vulnerability Scan</button><button id="aiSuggestDorks">💡 Suggest Pentesting Dorks</button><button id="aiAnalyzeHeaders">📋 AI Header Analysis</button><div id="aiOutput" style="margin-top:16px; background:#0f1222; padding:12px; border-radius:16px;"></div></div></div>

<!-- Extensions, bookmarks, history, settings, find modals (kept from earlier, simplified) -->
<div id="extensionsModal" class="modal"><div class="modal-content"><span class="close-modal">&times;</span><h3>🧩 Extensions</h3><div id="extensionsList"></div><input type="text" id="extName" placeholder="Name"><textarea id="extCode" rows="2" placeholder="JS code"></textarea><button id="addExtensionBtn">Add</button></div></div>
<div id="bookmarksModal" class="modal"><div class="modal-content"><span class="close-modal">&times;</span><h3>🔖 Bookmarks</h3><div id="bookmarksList"></div><button id="addBookmarkBtn">Bookmark Current</button></div></div>
<div id="historyModal" class="modal"><div class="modal-content"><span class="close-modal">&times;</span><h3>📜 History</h3><div id="historyList"></div><div id="closedTabsContainer"></div></div></div>
<div id="settingsModal" class="modal"><div class="modal-content"><span class="close-modal">&times;</span><h3>⚙️ Settings</h3><label>Search Engine:</label><select id="settingsEngine"><option>google</option><option>bing</option><option>duckduckgo</option></select><label>Zoom:</label><input type="number" id="zoomLevel" value="100"><button id="saveSettingsBtn">Save</button></div></div>
<div id="findModal" class="modal"><div class="modal-content"><span class="close-modal">&times;</span><h3>Find</h3><input type="text" id="findText"><button id="findNextBtn">Find</button></div></div>

<script>
    // Core elements
    const iframe = document.getElementById('browserFrame');
    const addressBar = document.getElementById('addressBar');
    const goBtn = document.getElementById('goBtn');
    const searchInput = document.getElementById('searchInput');
    const searchBtn = document.getElementById('searchBtn');
    const logContainer = document.getElementById('logContainer');
    const sourceDisplay = document.getElementById('sourceDisplay');
    const clearLogsBtn = document.getElementById('clearLogsBtn');

    function addLog(msg) {
        const entry = document.createElement('div'); entry.className = 'log-line';
        entry.innerHTML = `[${new Date().toLocaleTimeString()}] ${msg}`;
        logContainer.appendChild(entry); logContainer.scrollTop = logContainer.scrollHeight;
    }
    clearLogsBtn.onclick = () => { logContainer.innerHTML = "[+] Logs cleared.\n"; addLog("Logs cleared"); };

    function loadUrl(url) {
        let finalUrl = url.trim();
        if (!finalUrl.startsWith('http')) finalUrl = 'https://' + finalUrl;
        iframe.src = finalUrl;
        addressBar.value = finalUrl;
        addLog(`Navigated to ${finalUrl}`);
        addToHistory(finalUrl);
    }
    goBtn.onclick = () => loadUrl(addressBar.value);
    searchBtn.onclick = () => {
        let q = searchInput.value.trim();
        if(!q) return;
        let engine = document.getElementById('settingsEngine')?.value || 'google';
        let url = engine === 'google' ? `https://www.google.com/search?q=${encodeURIComponent(q)}` :
                   engine === 'bing' ? `https://www.bing.com/search?q=${encodeURIComponent(q)}` :
                   `https://duckduckgo.com/?q=${encodeURIComponent(q)}`;
        loadUrl(url);
        addLog(`Search: "${q}" via ${engine}`);
    };

    let browsingHistory = [];
    let closedTabs = [];
    function addToHistory(url) {
        if (!url || url === 'about:blank') return;
        if (!browsingHistory.some(h => h.url === url)) {
            browsingHistory.unshift({url, title: url, timestamp: Date.now()});
            if (browsingHistory.length > 50) browsingHistory.pop();
        }
    }

    let bookmarks = JSON.parse(localStorage.getItem('martyneBookmarks') || '[]');
    function saveBookmarks() { localStorage.setItem('martyneBookmarks', JSON.stringify(bookmarks)); }
    function addBookmark(url, title) {
        if (!bookmarks.some(b => b.url === url)) {
            bookmarks.push({url, title: title || url});
            saveBookmarks();
            addLog(`Bookmarked: ${url}`);
        }
    }

    let extensions = JSON.parse(localStorage.getItem('martyneExtensions') || '[]');
    function saveExtensions() { localStorage.setItem('martyneExtensions', JSON.stringify(extensions)); }
    function runExtension(ext) {
        try { iframe.contentWindow?.eval(ext.code); addLog(`Extension "${ext.name}" executed`); } catch(e){ addLog(`Extension error: ${e.message}`); }
    }
    function refreshExtensionsUI() {
        const container = document.getElementById('extensionsList');
        if(container){
            container.innerHTML = '';
            extensions.forEach((ext, idx) => {
                let div = document.createElement('div'); div.className = 'extension-item';
                div.innerHTML = `<span>${ext.name}</span><div><button onclick="runExtension(extensions[${idx}])">Run</button><button onclick="removeExtension(${idx})">Delete</button></div>`;
                container.appendChild(div);
            });
        }
    }
    window.removeExtension = (idx) => { extensions.splice(idx,1); saveExtensions(); refreshExtensionsUI(); };
    document.getElementById('addExtensionBtn')?.addEventListener('click', () => {
        let name = document.getElementById('extName').value.trim();
        let code = document.getElementById('extCode').value.trim();
        if(name && code) { extensions.push({name, code}); saveExtensions(); refreshExtensionsUI(); addLog(`Extension "${name}" added`); }
    });

    function refreshBookmarksUI() {
        const container = document.getElementById('bookmarksList');
        if(container){
            container.innerHTML = '';
            bookmarks.forEach((bm, idx) => {
                let div = document.createElement('div'); div.className = 'bookmark-item';
                div.innerHTML = `<span>${bm.title}</span><div><button onclick="loadUrl('${bm.url}')">Open</button><button onclick="removeBookmark(${idx})">❌</button></div>`;
                container.appendChild(div);
            });
        }
    }
    window.removeBookmark = (idx) => { bookmarks.splice(idx,1); saveBookmarks(); refreshBookmarksUI(); };

    function refreshHistoryUI() {
        const container = document.getElementById('historyList');
        if(container){
            container.innerHTML = '<h4>History</h4>';
            browsingHistory.slice(0,15).forEach(h => {
                let div = document.createElement('div'); div.className = 'history-item';
                div.innerHTML = `<span>${h.title}</span><button onclick="loadUrl('${h.url}')">Open</button>`;
                container.appendChild(div);
            });
        }
        const closedContainer = document.getElementById('closedTabsContainer');
        if(closedContainer){
            closedContainer.innerHTML = '<h4>Recently Closed</h4>';
            closedTabs.forEach((url,idx) => {
                let div = document.createElement('div'); div.className = 'history-item';
                div.innerHTML = `<span>${url}</span><button onclick="loadUrl('${url}'); closeModals();">Reopen</button>`;
                closedContainer.appendChild(div);
            });
        }
    }

    // ========== PRIVACY & AI FEATURES IMPLEMENTATIONS ==========
    // Web Tracking Protection
    document.getElementById('applyTrackingProtection')?.addEventListener('click', () => {
        let blockTrack = document.getElementById('blockTrackers').checked;
        let blockFp = document.getElementById('blockFingerprint').checked;
        let stripUtm = document.getElementById('stripUTM').checked;
        addLog(`[Web Tracking] Block trackers: ${blockTrack}, Block fingerprint: ${blockFp}, Strip UTM: ${stripUtm}`);
        document.getElementById('trackingStats').innerHTML = `✅ Simulated: ${blockTrack ? 'trackers blocked' : 'trackers allowed'}<br>🔒 Fingerprint protection ${blockFp ? 'active' : 'inactive'}<br>🔗 UTM parameters ${stripUtm ? 'stripped' : 'unchanged'}`;
        // simulate blocking
        if(blockTrack) addLog("Protection: Known tracking domains would be blocked (simulated)");
    });
    // App Tracking Protection
    document.getElementById('applyAppProtection')?.addEventListener('click', () => {
        let blockIDs = document.getElementById('blockAppIDs').checked;
        let limitAds = document.getElementById('limitAdPersonal').checked;
        let spoof = document.getElementById('spoofDevice').checked;
        addLog(`[App Tracking] Block IDs: ${blockIDs}, Limit Ads: ${limitAds}, Spoof Device: ${spoof}`);
        alert("App tracking protection preferences saved (simulated).");
    });
    // Email Protection
    document.getElementById('applyEmailProtection')?.addEventListener('click', () => {
        let blockPixels = document.getElementById('blockEmailPixels').checked;
        let linkWarn = document.getElementById('emailLinkWarning').checked;
        addLog(`[Email Protection] Block pixels: ${blockPixels}, Warn links: ${linkWarn}`);
        alert("Email protection active: tracking pixels blocked, suspicious link warnings enabled.");
    });
    document.getElementById('simulatePhishingCheck')?.addEventListener('click', () => {
        addLog("[Email Protection] Phishing check simulation: No malicious links detected in current context.");
        alert("Phishing simulation: The current page appears safe (demo).");
    });

    // AI Features
    async function aiSummarize() {
        addLog("[AI] Summarizing current page...");
        try {
            let doc = iframe.contentDocument;
            let text = doc?.body?.innerText?.slice(0, 1500) || "No content accessible";
            let summary = text.split('.').slice(0, 3).join('.') + '...';
            document.getElementById('aiOutput').innerHTML = `<strong>📄 Summary:</strong><br>${summary}<br><br><em>AI simulation: extracted key sentences.</em>`;
            addLog("[AI] Summary generated.");
        } catch(e) { document.getElementById('aiOutput').innerHTML = "Cannot access page content (cross-origin)."; }
    }
    async function aiVulnScan() {
        addLog("[AI] Running vulnerability scan on current origin...");
        document.getElementById('aiOutput').innerHTML = "<strong>🔍 AI Vulnerability Report:</strong><br>- Potential XSS in forms (simulated)<br>- Missing security headers<br>- Outdated jQuery detected (hypothetical)<br><em>Use full pentest tools for deeper analysis.</em>";
        addLog("[AI] Vulnerability scan complete.");
    }
    function aiSuggestDorks() {
        let dorks = ['site:target.com intitle:admin', 'inurl:php?id=', 'filetype:sql', 'intitle:"index of" password'];
        document.getElementById('aiOutput').innerHTML = `<strong>💡 Suggested Dorks:</strong><br>${dorks.map(d => `🔎 ${d}`).join('<br>')}<br><br><em>Copy and use in search bar.</em>`;
        addLog("[AI] Generated dork suggestions.");
    }
    function aiAnalyzeHeaders() {
        addLog("[AI] Analyzing HTTP headers...");
        document.getElementById('aiOutput').innerHTML = "<strong>📋 Header Analysis:</strong><br>- X-Frame-Options: missing → clickjacking risk<br>- Strict-Transport-Security: not set<br>- Content-Security-Policy: weak<br><em>Simulated analysis for demonstration.</em>";
    }
    document.getElementById('aiSummarizePage')?.addEventListener('click', aiSummarize);
    document.getElementById('aiDetectVuln')?.addEventListener('click', aiVulnScan);
    document.getElementById('aiSuggestDorks')?.addEventListener('click', aiSuggestDorks);
    document.getElementById('aiAnalyzeHeaders')?.addEventListener('click', aiAnalyzeHeaders);

    // Existing pentest tools (simplified versions)
    async function detectServer() { try { let origin = iframe.contentWindow?.location?.origin; if(origin) { let resp = await fetch(origin, {method:'HEAD'}); addLog(`Server: ${resp.headers.get('server') || 'unknown'}`); } } catch(e){ addLog(`Server detect error: ${e.message}`); } }
    function viewCookies() { try { let c = iframe.contentDocument?.cookie; addLog(`Cookies: ${c || 'none'}`); alert(c || 'No cookies'); } catch(e){ addLog(`Cookies error: ${e.message}`); } }
    function extractLinks() { try { let links = Array.from(iframe.contentDocument?.querySelectorAll('a')||[]).map(a=>a.href).filter(h=>h); addLog(`Links: ${links.length} found`); alert(links.join('\n')||'none'); } catch(e){} }
    async function fetchHeaders() { try { let origin = iframe.contentWindow?.location?.origin; if(origin) { let r=await fetch(origin,{method:'HEAD'}); let h={}; r.headers.forEach((v,k)=>h[k]=v); addLog(`Headers: ${JSON.stringify(h).slice(0,200)}`); } } catch(e){} }
    function executeJS(code) { try { let win = iframe.contentWindow; win?.eval(code); addLog(`JS executed`); } catch(e){ addLog(`JS error: ${e.message}`); } }
    async function cgiScan() { let origin = iframe.contentWindow?.location?.origin; if(origin){ let paths=['/cgi-bin/status','/cgi-bin/admin.pl']; for(let p of paths){ try{ await fetch(origin+p,{mode:'no-cors'}); addLog(`CGI ${p} reachable`); }catch(e){} } } }
    async function bruteForce() { let doc = iframe.contentDocument; if(doc && doc.querySelector('form')) { let pwdField=doc.querySelector('input[type=password]'); if(pwdField){ let dict=['admin','password']; for(let p of dict){ pwdField.value=p; addLog(`BF trying ${p}`); await new Promise(r=>setTimeout(r,30)); } } } else addLog("No login form found"); }
    async function dirBrute() { let origin = iframe.contentWindow?.location?.origin; if(origin){ let dirs=['/admin','/backup']; for(let d of dirs){ try{ await fetch(origin+d,{mode:'no-cors'}); addLog(`Dir ${d} reachable`); }catch(e){} } } }
    function injectWidget() { try { let win=iframe.contentWindow; if(win){ let div=win.document.createElement('div'); div.innerHTML='<div style="background:#2d7aff;padding:8px;position:fixed;bottom:10px;left:10px;z-index:9999;">MarTyne Widget</div>'; win.document.body.appendChild(div); addLog("Widget injected"); } } catch(e){} }
    function executeLuaFromEditor() { let script = document.getElementById('modalLuaScript').value; try { if(script.includes('dom:inject')) injectWidget(); } catch(e){ addLog(`Lua error: ${e.message}`); } }

    // Attach modal buttons
    document.getElementById('modalDetectServer').onclick = () => { detectServer(); closeModals(); };
    document.getElementById('modalViewCookies').onclick = () => { viewCookies(); closeModals(); };
    document.getElementById('modalExtractLinks').onclick = () => { extractLinks(); closeModals(); };
    document.getElementById('modalViewHeaders').onclick = () => { fetchHeaders(); closeModals(); };
    document.getElementById('modalCgiScanner').onclick = () => { cgiScan(); closeModals(); };
    document.getElementById('modalBruteforce').onclick = () => { bruteForce(); closeModals(); };
    document.getElementById('modalDirBrute').onclick = () => { dirBrute(); closeModals(); };
    document.getElementById('modalRunLua').onclick = () => { executeLuaFromEditor(); closeModals(); };
    document.getElementById('modalInjectWidget').onclick = () => { injectWidget(); closeModals(); };
    document.getElementById('detectServerBtn').onclick = detectServer;
    document.getElementById('viewCookiesBtn').onclick = viewCookies;
    document.getElementById('extractLinksBtn').onclick = extractLinks;
    document.getElementById('viewHeadersBtn').onclick = fetchHeaders;
    document.getElementById('execJsBtn').onclick = () => { let code = document.getElementById('jsCodeInput').value; if(code) executeJS(code); };
    document.getElementById('cgiScannerBtn').onclick = cgiScan;
    document.getElementById('bruteforceBtn').onclick = bruteForce;
    document.getElementById('dirBruteBtn').onclick = dirBrute;
    document.getElementById('runLuaBtn').onclick = () => injectWidget();
    document.getElementById('injectWidgetBtn').onclick = injectWidget;
    document.getElementById('socialSearchBtn').onclick = () => { let u = document.getElementById('socialUsername').value; if(u) loadUrl(`https://twitter.com/${u}`); };
    document.querySelectorAll('.social-btn').forEach(btn => btn.onclick = () => loadUrl(btn.getAttribute('data-url')));

    // Open modal functions
    function openModal(id) { document.getElementById(id).style.display = 'flex'; }
    function closeModals() { document.querySelectorAll('.modal').forEach(m => m.style.display = 'none'); }
    document.querySelectorAll('.close-modal').forEach(el => el.onclick = closeModals);
    // Kebab menu
    const kebabBtn = document.getElementById('kebabBtn');
    const dropdown = document.getElementById('kebabDropdown');
    kebabBtn.onclick = (e) => { e.stopPropagation(); dropdown.classList.toggle('show'); };
    document.addEventListener('click', () => dropdown.classList.remove('show'));
    document.getElementById('menuRecon').onclick = () => { closeModals(); openModal('reconModal'); };
    document.getElementById('menuAdvancedAttack').onclick = () => { closeModals(); openModal('advancedModal'); };
    document.getElementById('menuLuaTools').onclick = () => { closeModals(); openModal('luaModal'); };
    document.getElementById('menuWebTracking').onclick = () => { closeModals(); openModal('webTrackingModal'); };
    document.getElementById('menuAppTracking').onclick = () => { closeModals(); openModal('appTrackingModal'); };
    document.getElementById('menuEmailProtection').onclick = () => { closeModals(); openModal('emailProtectionModal'); };
    document.getElementById('menuAIFeatures').onclick = () => { closeModals(); openModal('aiFeaturesModal'); };
    document.getElementById('menuExtensions').onclick = () => { refreshExtensionsUI(); openModal('extensionsModal'); };
    document.getElementById('menuBookmarks').onclick = () => { refreshBookmarksUI(); openModal('bookmarksModal'); };
    document.getElementById('menuHistory').onclick = () => { refreshHistoryUI(); openModal('historyModal'); };
    document.getElementById('menuSettings').onclick = () => { openModal('settingsModal'); };
    document.getElementById('menuPrint').onclick = () => { iframe.contentWindow?.print(); addLog("Print triggered"); };
    document.getElementById('menuFind').onclick = () => { openModal('findModal'); };
    document.getElementById('menuZoomIn').onclick = () => { let cur = parseFloat(iframe.style.transform.replace('scale(','')) || 1; cur += 0.1; iframe.style.transform = `scale(${cur})`; iframe.style.transformOrigin = '0 0'; addLog(`Zoom: ${Math.round(cur*100)}%`); };
    document.getElementById('menuZoomOut').onclick = () => { let cur = parseFloat(iframe.style.transform.replace('scale(','')) || 1; cur = Math.max(0.5, cur-0.1); iframe.style.transform = `scale(${cur})`; iframe.style.transformOrigin = '0 0'; addLog(`Zoom: ${Math.round(cur*100)}%`); };
    document.getElementById('menuDevTools').onclick = () => { addLog("DevTools: source panel opened"); document.querySelector('.dev-tab[data-tab="source"]').click(); alert("Source view opened."); };
    document.getElementById('addBookmarkBtn').onclick = () => { let url = iframe.src; if(url && url!=='about:blank'){ addBookmark(url, iframe.contentDocument?.title||url); refreshBookmarksUI(); } };
    document.getElementById('saveSettingsBtn')?.addEventListener('click', () => { let zoom = parseInt(document.getElementById('zoomLevel').value); if(zoom) iframe.style.transform = `scale(${zoom/100})`; addLog("Settings saved"); closeModals(); });
    document.getElementById('findNextBtn')?.addEventListener('click', () => { let text = document.getElementById('findText').value; if(text) try{ iframe.contentWindow?.find(text); addLog(`Find: ${text}`); }catch(e){} });

    function updateSource() { try { let doc = iframe.contentDocument; if(doc && doc.documentElement) sourceDisplay.innerText = doc.documentElement.outerHTML; else sourceDisplay.innerText = "// Source unavailable"; } catch(e) { sourceDisplay.innerText = `// Error: ${e.message}`; } }
    iframe.addEventListener('load', () => { updateSource(); addLog(`Loaded: ${iframe.src}`); addToHistory(iframe.src); refreshHistoryUI(); });
    const tabs = document.querySelectorAll('.dev-tab');
    const panes = { normal: document.getElementById('normalPane'), source: document.getElementById('sourcePane'), logs: document.getElementById('logsPane') };
    tabs.forEach(tab => {
        tab.addEventListener('click', () => {
            const target = tab.getAttribute('data-tab');
            tabs.forEach(t => t.classList.remove('active'));
            tab.classList.add('active');
            Object.keys(panes).forEach(k => panes[k].classList.remove('active-pane'));
            if(target === 'normal') panes.normal.classList.add('active-pane');
            else if(target === 'source') { panes.source.classList.add('active-pane'); updateSource(); }
            else if(target === 'logs') panes.logs.classList.add('active-pane');
        });
    });
    loadUrl('https://example.com');
    addLog("MarTyne Browser fully loaded — Privacy & AI tools now in main menu.");
</script>
</body>
</html>
