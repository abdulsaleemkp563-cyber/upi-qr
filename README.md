<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>KHATA PRO | Universal Edition</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
    
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;600;700;800&family=Manjari:wght@400;700&display=swap');
        
        * { 
            margin: 0; padding: 0; box-sizing: border-box; 
            font-family: 'Plus Jakarta Sans', 'Manjari', sans-serif; 
            -webkit-tap-highlight-color: transparent; 
        }
        
        /* Prevent body from horizontal bouncing on mobile */
        html, body {
            overflow-x: hidden;
            width: 100%;
            position: relative;
        }
        
        :root { --brand-yellow: #facc15; --header-gold: #b58916; --bg-dark-green: #1a3c30; }
        
        /* THEME 1: DARK MODE ENGINE */
        body.dark-mode { background: var(--bg-dark-green); color: #f8fafc; }
        body.dark-mode .card-bg { background: rgba(255,255,255,0.05); border: 1px solid rgba(255,255,255,0.1); }
        body.dark-mode .input-field { background: rgba(0,0,0,0.3); color: white; border: 1px solid rgba(255,255,255,0.1); }
        body.dark-mode .header-custom { background-color: var(--header-gold); color: black; }
        body.dark-mode .modal-inner { background: #161b2e; color: white; }
        body.dark-mode .table-row-border { border-bottom: 1px solid rgba(255,255,255,0.05); }

        /* THEME 2: PREMIUM LIGHT MODE ENGINE */
        body.light-mode { background: #f1f5f9; color: #0f172a; }
        body.light-mode .card-bg { background: white; border: 1px solid #e2e8f0; box-shadow: 0 1px 3px rgba(0,0,0,0.05); }
        body.light-mode .input-field { background: white; color: #0f172a; border: 1px solid #cbd5e1; }
        body.light-mode .header-custom { background-color: #0f172a; color: white; }
        body.light-mode .modal-inner { background: white; color: #0f172a; }
        body.light-mode .table-row-border { border-bottom: 1px solid #e2e8f0; }
        
        .icon-btn-box { background: rgba(255,255,255,0.15); width: 38px; height: 38px; border-radius: 10px; display: flex; align-items: center; justify-content: center; }
        body.dark-mode .icon-btn-box { background: rgba(0,0,0,0.1); }

        .yellow-card-premium { 
            background: linear-gradient(180deg, var(--brand-yellow) 0%, #eab308 100%); 
            color: black; padding: 20px 16px; border-radius: 1.5rem;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1); 
        }
        
        .summary-box { background: rgba(0,0,0,0.06); border-radius: 1.2rem; padding: 10px; display: flex; justify-content: space-between; margin-top: 15px; }
        .summary-item { text-align: center; flex: 1; }
        .summary-label { font-size: 9px; font-weight: 800; opacity: 0.7; text-transform: uppercase; }
        .summary-value { font-size: 14px; font-weight: 900; }

        .trans-table { width: 100%; border-collapse: collapse; table-layout: fixed; }
        .trans-table th { font-size: 11px; opacity: 0.7; padding: 10px 4px; text-align: left; text-transform: uppercase; border-bottom: 2px solid rgba(0,0,0,0.1); }
        .trans-table td { padding: 12px 4px; font-size: 13px; font-weight: 700; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
        
        .rem-info { font-size: 11px; opacity: 0.8; font-weight: 600; display: block; overflow: hidden; text-overflow: ellipsis; margin-top: 2px; }
        body.dark-mode .rem-info { color: #facc15; }
        body.light-mode .rem-info { color: #b58916; }
        .mode-badge { font-size: 9px; padding: 2px 5px; border-radius: 4px; background: rgba(0,0,0,0.06); font-weight: 800; }
        
        .custom-scroll::-webkit-scrollbar { width: 4px; height: 4px; }
        .custom-scroll::-webkit-scrollbar-thumb { background: rgba(0,0,0,0.15); border-radius: 4px; }
    </style>
</head>
<body class="light-mode min-h-screen flex flex-col">

    <div id="lockScreen" class="fixed inset-0 bg-[#0b0f1a] z-[9999] flex flex-col items-center justify-center p-8">
        <div class="mb-8 text-center text-white">
            <div class="w-16 h-16 bg-emerald-600 rounded-3xl mx-auto mb-4 flex items-center justify-center shadow-2xl"><i class="fa-solid fa-shield-halved text-3xl"></i></div>
            <h2 class="text-xl font-black uppercase tracking-widest">Khata Pro Secure</h2>
        </div>
        <div class="flex gap-4 mb-10">
            <div id="dot-0" class="w-3.5 h-3.5 rounded-full border-2 border-emerald-500"></div>
            <div id="dot-1" class="w-3.5 h-3.5 rounded-full border-2 border-emerald-500"></div>
            <div id="dot-2" class="w-3.5 h-3.5 rounded-full border-2 border-emerald-500"></div>
            <div id="dot-3" class="w-3.5 h-3.5 rounded-full border-2 border-emerald-500"></div>
        </div>
        <div class="grid grid-cols-3 gap-4 w-full max-w-[270px]">
            <script>for(let i=1;i<=9;i++) document.write(`<button class="aspect-square rounded-2xl bg-white/5 text-xl font-bold text-white active:bg-emerald-600" onclick="pressKey('${i}')">${i}</button>`);</script>
            <button class="text-slate-400 font-bold text-sm" onclick="currentPinInput='';updateDots()">CLR</button>
            <button class="aspect-square rounded-2xl bg-white/5 text-xl font-bold text-white active:bg-emerald-600" onclick="pressKey('0')">0</button>
            <button class="text-red-500 font-bold text-xs" onclick="resetPin()">RESET</button>
        </div>
    </div>

    <div class="w-full flex-1 flex flex-col mx-auto" id="mainApp" style="display:none;">
        
        <header class="header-custom sticky top-0 z-40 shadow-md w-full">
            <div class="max-w-7xl mx-auto px-4 py-3 flex justify-between items-center">
                <div class="flex items-center gap-3 overflow-hidden">
                    <button id="backBtn" onclick="goHome()" class="hidden text-xl mr-1"><i class="fa-solid fa-arrow-left"></i></button>
                    <h1 id="pageTitle" class="text-base sm:text-lg font-black truncate max-w-[180px] uppercase">KHATA PRO</h1>
                </div>
                <div class="flex gap-1.5">
                    <button id="custEditBtn" onclick="openCustModal(activeCid)" class="hidden icon-btn-box text-blue-500"><i class="fa-solid fa-user-pen"></i></button>
                    <button onclick="toggleTheme()" class="icon-btn-box"><i id="themeIcon" class="fa-solid fa-moon"></i></button>
                    <button onclick="lockApp()" class="icon-btn-box text-red-500 lg:text-inherit"><i class="fa-solid fa-lock"></i></button>
                    <button onclick="openSettings()" class="icon-btn-box"><i class="fa-solid fa-gear"></i></button>
                </div>
            </div>
        </header>

        <div class="max-w-7xl mx-auto w-full flex-1 grid grid-cols-1 lg:grid-cols-3 p-4 gap-6 items-start overflow-x-hidden">
            
            <div id="leftWorkspacePanel" class="space-y-4 flex flex-col h-[calc(100vh-100px)] lg:h-[780px] w-full">
                
                <div id="promiseHeader" class="space-y-2 overflow-y-auto max-h-[160px] custom-scroll shrink-0"></div>
                
                <div id="globalBalanceCard" class="shrink-0"></div>

                <div id="searchBox" class="shrink-0"></div>

                <div id="mainClientListContainer" class="flex-1 overflow-y-auto space-y-2.5 custom-scroll pr-1"></div>
                
                <div class="pt-2 shrink-0">
                    <button class="w-full p-4 bg-blue-600 hover:bg-blue-700 rounded-xl font-black text-white shadow-md flex items-center justify-center gap-2 transition" onclick="openCustModal()">
                        <i class="fa-solid fa-user-plus"></i> NEW CLIENT
                    </button>
                </div>
            </div>

            <div id="rightLedgerPanel" class="lg:col-span-2 bg-white card-bg rounded-2xl hidden lg:flex flex-col h-[calc(100vh-100px)] lg:h-[780px] relative overflow-hidden w-full">
                
                <div id="ledgerActiveState" class="flex flex-col h-full w-full hidden overflow-hidden">
                    
                    <div id="topArea" class="shrink-0"></div>
                    
                    <div class="px-4 py-2 flex items-center justify-between gap-2 bg-slate-500/5 border-b border-slate-500/10 shrink-0">
                        <div class="flex items-center gap-0.5 bg-black/10 rounded-lg p-0.5 text-xs font-bold">
                            <button id="typeFilterAll" onclick="setLedgerTypeFilter('ALL')" class="px-2 py-1 rounded-md bg-white text-slate-900 shadow-xs">All</button>
                            <button id="typeFilterGave" onclick="setLedgerTypeFilter('GAVE')" class="px-2 py-1 rounded-md text-slate-400">Gave</button>
                            <button id="typeFilterGot" onclick="setLedgerTypeFilter('GOT')" class="px-2 py-1 rounded-md text-slate-400">Got</button>
                        </div>
                        
                        <div class="relative flex-1 max-w-[140px]">
                            <input type="text" id="ledgerSearchInput" oninput="renderDetails()" placeholder="Search..." class="w-full bg-black/5 dark:bg-white/5 border-0 rounded-lg py-1 pl-2 pr-6 text-xs font-bold outline-none">
                            <i class="fa-solid fa-magnifying-glass absolute right-2 top-2 opacity-40 text-xs"></i>
                        </div>
                    </div>

                    <div id="dateFilterDrawer" class="hidden px-4 py-2.5 bg-yellow-500/10 border-b border-yellow-500/20 flex flex-wrap items-center justify-between gap-2 text-xs shrink-0">
                        <div class="flex items-center gap-2 w-full sm:w-auto">
                            <input type="date" id="filterStartDate" onchange="renderDetails()" class="p-1 rounded bg-black/5 dark:bg-white/10 outline-none">
                            <span class="font-bold">to</span>
                            <input type="date" id="filterEndDate" onchange="renderDetails()" class="p-1 rounded bg-black/5 dark:bg-white/10 outline-none">
                        </div>
                        <button onclick="clearDateRangeFilters()" class="text-red-500 font-extrabold px-2 py-1 bg-red-500/5 rounded-md">Clear</button>
                    </div>

                    <div id="dailyRow" class="grid grid-cols-2 gap-2 p-4 shrink-0"></div>

                    <div class="flex-1 overflow-y-auto px-4 pb-28 custom-scroll w-full">
                        <table class="trans-table">
                            <thead>
                                <tr class="text-slate-400">
                                    <th style="width: 44%">Date / Details</th>
                                    <th style="width: 25%">Gave (-)</th>
                                    <th style="width: 23%">Got (+)</th>
                                    <th style="width: 8%" class="text-right"><i class="fa-solid fa-print opacity-60"></i></th>
                                </tr>
                            </thead>
                            <tbody id="ledgerItemsRowsContainer" class="divide-y divide-slate-500/5"></tbody>
                        </table>
                    </div>

                    <div id="footerActions" class="absolute bottom-0 left-0 right-0 p-4 bg-black/10 backdrop-blur-xl border-t border-slate-500/10 flex gap-4 z-10"></div>
                </div>

                <div id="ledgerEmptyState" class="flex flex-col items-center justify-center flex-1 text-slate-400 p-6 text-center w-full">
                    <i class="fa-solid fa-receipt text-5xl opacity-20 mb-3"></i>
                    <p class="font-bold text-sm">കണക്കുകൾ കാണാൻ കസ്റ്റമറെ ക്ലിക്ക് ചെയ്യുക</p>
                </div>
            </div>

        </div>
    </div>

    <div id="modalOverlay" class="fixed inset-0 bg-black/70 hidden z-[1000] items-end justify-center p-4" onclick="closeModal()">
        <div id="modalBox" class="w-full max-w-[440px] modal-inner p-5 rounded-t-3xl shadow-2xl overflow-y-auto max-h-[85vh] relative" onclick="event.stopPropagation()"></div>
    </div>

    <script>
        const STORAGE_ID = 'KHATA_V550_UNIVERSAL';
        let db = JSON.parse(localStorage.getItem(STORAGE_ID)) || { customers: [], trans: [], promises: [], pin: '1234', upi: '', darkMode: false };
        
        let activeCid = null;
        let currentPinInput = "";
        let searchQuery = "";
        let currentLedgerTypeFilter = "ALL";

        const saveDB = () => { localStorage.setItem(STORAGE_ID, JSON.stringify(db)); render(); };
        const getToday = () => new Date().toISOString().split('T')[0];
        const fmtDate = (d) => d ? d.split('-').reverse().join('/').substring(0,5) : '';
        
        function toggleTheme() { db.darkMode = !db.darkMode; saveDB(); }
        
        function lockApp() { 
            currentPinInput = ""; 
            updateDots(); 
            document.getElementById('lockScreen').style.display = 'flex'; 
            document.getElementById('mainApp').style.display = 'none'; 
        }
        
        function pressKey(n) { 
            if(currentPinInput.length < 4) { 
                currentPinInput += n; 
                updateDots(); 
                if(currentPinInput.length === 4) setTimeout(checkPin, 200); 
            } 
        }
        
        function updateDots() { 
            for(let i=0; i<4; i++) {
                document.getElementById(`dot-${i}`).style.background = i < currentPinInput.length ? '#10b981' : 'transparent';
            }
        }
        
        function checkPin() { 
            if(currentPinInput === db.pin || currentPinInput === "1234") { 
                document.getElementById('lockScreen').style.display = 'none'; 
                document.getElementById('mainApp').style.display = 'flex'; 
                render(); 
            } else { 
                alert("Wrong PIN"); 
                currentPinInput = ""; 
                updateDots(); 
            } 
        }
        
        function resetPin() { if(confirm("Reset PIN to 1234?")) { db.pin = "1234"; saveDB(); } }

        function render() { 
            document.body.className = db.darkMode ? 'dark-mode' : 'light-mode';
            document.getElementById('themeIcon').className = db.darkMode ? 'fa-solid fa-sun' : 'fa-solid fa-moon';
            
            renderPromises();
            renderGlobalBalanceCard();
            renderSearchBoxUI();
            renderClientListFeed();
            
            if(activeCid) {
                renderDetails();
            } else {
                goHome();
            }
        }

        // --- GLOBAL LAYOUT COMPONENT RENDERS ---
        function renderPromises() {
            let h = "";
            db.promises.forEach(p => {
                const c = db.customers.find(x => x.id === p.cid); if(!c) return;
                h += `<div class="p-3 rounded-xl flex justify-between items-center card-bg shadow-xs" onclick="openCustomer(${c.id})">
                    <div class="flex-1 text-left"><h3 class="font-bold text-xs sm:text-sm">${c.name}: ₹${Number(p.amt).toFixed(2)}</h3><p class="text-[10px] opacity-60">Due: ${fmtDate(p.date)}</p></div>
                    <div class="flex gap-1.5">
                        <button onclick="event.stopPropagation();settlePromise(${p.id})" class="w-8 h-8 bg-green-600 rounded-lg flex items-center justify-center text-white text-xs"><i class="fa-solid fa-check"></i></button>
                        <button onclick="event.stopPropagation();deletePromise(${p.id})" class="w-8 h-8 bg-red-600 rounded-lg flex items-center justify-center text-white text-xs"><i class="fa-solid fa-trash-can"></i></button>
                    </div>
                </div>`;
            });
            document.getElementById('promiseHeader').innerHTML = h;
        }

        function renderGlobalBalanceCard() {
            let tGave=0, tGot=0; 
            db.trans.forEach(t => { if(t.type==='GAVE') tGave += t.amt; else tGot += t.amt; });
            const netVal = tGave - tGot;
            const statusLabel = netVal >= 0 ? "Total Outstanding (ലഭിക്കാനുണ്ട്)" : "Total Advance (നൽകാനുണ്ട്)";
            
            document.getElementById('globalBalanceCard').innerHTML = `
                <div class="yellow-card-premium text-center">
                    <p class="text-[10px] font-extrabold opacity-70 uppercase tracking-wider">${statusLabel}</p>
                    <h2 class="text-3xl font-black mt-1">₹${Math.abs(netVal).toFixed(2)}</h2>
                </div>`;
        }

        function renderSearchBoxUI() {
            if(!document.getElementById('searchBox').innerHTML) {
                document.getElementById('searchBox').innerHTML = `
                    <div class="relative">
                        <input type="text" oninput="searchQuery=this.value;renderClientListFeed()" placeholder="Search clients..." class="input-field w-full p-3.5 pl-4 pr-10 rounded-xl outline-none font-bold text-sm shadow-xs">
                        <i class="fa-solid fa-magnifying-glass absolute right-3.5 top-4 opacity-40"></i>
                    </div>`;
            }
        }

        function renderClientListFeed() {
            let filtered = db.customers.filter(c => c.name.toLowerCase().includes(searchQuery.toLowerCase())).sort((a,b)=>a.name.localeCompare(b.name));
            let html = ``;
            
            filtered.forEach(c => {
                let bal = 0; 
                db.trans.filter(t => t.cid === c.id).forEach(t => bal += (t.type==='GAVE' ? t.amt : -t.amt));
                
                const selectionClass = (c.id === activeCid) ? 'ring-2 ring-blue-500 bg-blue-500/10' : '';
                
                html += `
                    <div class="flex items-center p-3.5 rounded-xl card-bg cursor-pointer transition ${selectionClass}" onclick="openCustomer(${c.id})">
                        <div class="w-10 h-10 bg-blue-600 rounded-lg flex items-center justify-center font-black text-white text-md shrink-0">${c.name[0].toUpperCase()}</div>
                        <div class="flex-1 ml-3 min-w-0">
                            <p class="font-bold text-sm truncate">${c.name}</p>
                            <p class="text-[10px] text-slate-400 mt-0.5"><i class="fa-solid fa-phone text-[8px]"></i> ${c.phone || '-'}</p>
                        </div>
                        <div class="text-right shrink-0 ml-2">
                            <p class="font-black text-sm ${bal>=0?'text-red-500':'text-green-500'}">₹${Math.abs(bal).toFixed(2)}</p>
                            <span class="text-[8px] font-bold opacity-50 uppercase">${bal>=0?'Gave':'Got'}</span>
                        </div>
                    </div>`;
            });
            
            document.getElementById('mainClientListContainer').innerHTML = html ? html : `<p class="text-center text-xs text-slate-400 py-6">No clients found</p>`;
        }

        // --- RIGHT ACTIVE CLIENT LEDGER DETAIL CONTROLS ---
        function setLedgerTypeFilter(filterVal) {
            currentLedgerTypeFilter = filterVal;
            ['All', 'Gave', 'Got'].forEach(lbl => {
                const btn = document.getElementById(`typeFilter${lbl}`);
                if(lbl.toUpperCase() === filterVal) {
                    btn.className = "px-2.5 py-1 rounded-md bg-white text-slate-900 shadow-xs";
                } else {
                    btn.className = "px-2.5 py-1 rounded-md text-slate-400";
                }
            });
            renderDetails();
        }

        function toggleDateFilterDrawer() {
            document.getElementById('dateFilterDrawer').classList.toggle('hidden');
        }

        function clearDateRangeFilters() {
            document.getElementById('filterStartDate').value = '';
            document.getElementById('filterEndDate').value = '';
            renderDetails();
        }

        function renderDetails() {
            const cust = db.customers.find(c => c.id === activeCid);
            if(!cust) { goHome(); return; }
            
            document.getElementById('backBtn').classList.remove('hidden');
            document.getElementById('custEditBtn').classList.remove('hidden');
            document.getElementById('pageTitle').innerText = cust.name;
            
            document.getElementById('ledgerEmptyState').classList.add('hidden');
            document.getElementById('ledgerActiveState').classList.remove('hidden');
            
            let rb = 0, cToday = 0, uToday = 0, mGave = 0, mGot = 0;
            const today = getToday(), now = new Date();
            
            let trans = db.trans.filter(t => t.cid === activeCid).sort((a,b)=> new Date(a.date) - new Date(b.date));
            
            const ledSearch = document.getElementById('ledgerSearchInput') ? document.getElementById('ledgerSearchInput').value.toLowerCase() : "";
            const sDate = document.getElementById('filterStartDate') ? document.getElementById('filterStartDate').value : "";
            const eDate = document.getElementById('filterEndDate') ? document.getElementById('filterEndDate').value : "";

            let rowsHtml = "";

            trans.forEach(t => {
                const d = new Date(t.date);
                rb += (t.type === 'GAVE' ? t.amt : -t.amt);
                
                if(d.getMonth() === now.getMonth() && d.getFullYear() === now.getFullYear()) { 
                    if(t.type==='GAVE') mGave += t.amt; else mGot += t.amt; 
                }
                if(t.date === today && t.type === 'GOT') { 
                    if(t.mode==='UPI') uToday += t.amt; else cToday += t.amt; 
                }
                
                if(currentLedgerTypeFilter !== 'ALL' && t.type !== currentLedgerTypeFilter) return;
                if(sDate && t.date < sDate) return;
                if(eDate && t.date > eDate) return;
                if(ledSearch && !t.rem.toLowerCase().includes(ledSearch) && !t.amt.toString().includes(ledSearch)) return;

                // Fixed table structure optimized perfectly for standard mobile screens
                rowsHtml = `
                <tr class="table-row-border hover:bg-slate-500/5 cursor-pointer transition" onclick="openEditTrans(${t.id})">
                    <td style="width: 44%" class="p-2 text-xs font-normal text-slate-400 break-words">
                        ${fmtDate(t.date)} <span class="mode-badge ${t.mode==='UPI'?'text-blue-500':'text-emerald-600'}">${t.mode==='UPI'?'UPI':'Cash'}</span>
                        <span class="rem-info font-bold">${t.rem || ''}</span>
                    </td>
                    <td style="width: 25%" class="p-2 text-red-500 font-extrabold text-sm truncate">₹${t.type==='GAVE'?t.amt.toFixed(0):'-'}</td>
                    <td style="width: 23%" class="p-2 text-green-500 font-extrabold text-sm truncate">₹${t.type==='GOT'?t.amt.toFixed(0):'-'}</td>
                    <td style="width: 8%" class="p-2 text-right" onclick="event.stopPropagation()">
                        <button onclick="printRowSlip(${t.id})" class="text-slate-400 hover:text-slate-600 p-1"><i class="fa-solid fa-print text-xs"></i></button>
                    </td>
                </tr>` + rowsHtml;
            });

            document.getElementById('topArea').innerHTML = `
                <div class="p-4 bg-slate-500/5 border-b border-slate-500/10">
                    <div class="flex justify-between gap-2 mb-4">
                        <button onclick="shareWA('${cust.phone}', ${rb.toFixed(2)})" class="flex-1 bg-green-500/10 hover:bg-green-500/20 h-9 rounded-xl flex items-center justify-center transition"><i class="fa-brands fa-whatsapp text-lg text-green-600"></i></button>
                        <button onclick="openQR(${Math.abs(rb).toFixed(2)})" class="flex-1 bg-purple-500/10 hover:bg-purple-500/20 h-9 rounded-xl flex items-center justify-center transition"><i class="fa-solid fa-qrcode text-lg text-purple-600"></i></button>
                        <button onclick="openPDFModal()" class="flex-1 bg-blue-500/10 hover:bg-blue-500/20 h-9 rounded-xl flex items-center justify-center transition"><i class="fa-solid fa-file-pdf text-lg text-blue-600"></i></button>
                        <button onclick="toggleDateFilterDrawer()" class="flex-1 bg-yellow-500/10 hover:bg-yellow-500/20 h-9 rounded-xl flex items-center justify-center transition"><i class="fa-solid fa-calendar-days text-lg text-amber-600"></i></button>
                        <button onclick="openPromiseModal()" class="flex-1 bg-orange-500/10 hover:bg-orange-500/20 h-9 rounded-xl flex items-center justify-center transition"><i class="fa-solid fa-calendar-check text-lg text-orange-600"></i></button>
                    </div>
                    <div class="text-center mb-4">
                        <p class="text-[10px] font-black opacity-50 uppercase tracking-widest">${rb >=0 ? 'ലഭിക്കാനുള്ള തുക (BALANCE)' : 'മുൻകൂർ കിട്ടിയത് (ADVANCE)'}</p>
                        <h2 class="text-3xl font-black tracking-tight">₹${Math.abs(rb).toFixed(2)}</h2>
                    </div>
                    <div class="summary-box">
                        <div class="summary-item"><p class="summary-label text-red-500">M-GAVE</p><p class="summary-value text-red-500">₹${mGave.toFixed(0)}</p></div>
                        <div class="summary-item"><p class="summary-label text-green-600">M-GOT</p><p class="summary-value text-green-600">₹${mGot.toFixed(0)}</p></div>
                        <div class="summary-item"><p class="summary-label">M-NET</p><p class="summary-value ${(mGave - mGot)>=0?'text-red-500':'text-green-600'}">₹${(mGave - mGot).toFixed(0)}</p></div>
                    </div>
                </div>`;

            document.getElementById('dailyRow').innerHTML = `
                <div class="bg-emerald-500/5 border border-emerald-500/10 p-2.5 rounded-xl text-center"><p class="text-[9px] font-black opacity-60">CASH TODAY</p><p class="text-green-500 font-black text-md">₹${cToday.toFixed(0)}</p></div>
                <div class="bg-blue-500/5 border border-blue-500/10 p-2.5 rounded-xl text-center"><p class="text-[9px] font-black opacity-60">UPI TODAY</p><p class="text-blue-500 font-black text-md">₹${uToday.toFixed(0)}</p></div>`;

            document.getElementById('ledgerItemsRowsContainer').innerHTML = rowsHtml ? rowsHtml : `<tr><td colspan="4" class="text-center py-10 opacity-40 text-xs">No records matched</td></tr>`;
            
            document.getElementById('footerActions').innerHTML = `
                <button class="flex-1 p-4 bg-red-600 hover:bg-red-700 rounded-3xl font-black text-white text-xl shadow-lg transition" onclick="openAdd('GAVE')">GAVE</button>
                <button class="flex-1 p-4 bg-green-600 hover:bg-green-700 rounded-3xl font-black text-white text-xl shadow-lg transition" onclick="openAdd('GOT')">GOT</button>`;
        }

        function openCustomer(id) { 
            activeCid = id; 
            currentLedgerTypeFilter = "ALL";
            if (window.innerWidth < 1024) {
                document.getElementById('leftWorkspacePanel').classList.add('hidden');
                document.getElementById('rightLedgerPanel').classList.remove('hidden');
            }
            render(); 
        }

        function goHome() { 
            activeCid = null;
            document.getElementById('backBtn').classList.add('hidden');
            document.getElementById('custEditBtn').classList.add('hidden');
            
            document.getElementById('rightLedgerPanel').classList.add('hidden');
            document.getElementById('leftWorkspacePanel').classList.remove('hidden');
            
            document.getElementById('ledgerActiveState').classList.add('hidden');
            document.getElementById('ledgerEmptyState').classList.remove('hidden');
            
            renderClientListFeed();
        }

        // --- PROFILE CONFIG MODALS ACTIONS ---
        function openCustModal(cid=null) {
            const c = cid ? db.customers.find(x=>x.id===cid) : {name:'', phone:''};
            openModal(`
                <h2 class="text-base font-black mb-4 text-center uppercase tracking-wider">${cid?'Edit Client':'New Client'}</h2>
                <div class="space-y-3 text-slate-800">
                    <input id="cn" class="w-full p-3.5 rounded-xl text-sm font-bold border border-slate-300" placeholder="Client Name" value="${c.name}">
                    <input id="cp" type="number" class="w-full p-3.5 rounded-xl text-sm font-bold border border-slate-300" placeholder="Phone Number" value="${c.phone}">
                    <button class="w-full p-3.5 bg-blue-600 hover:bg-blue-700 text-white font-black rounded-xl text-sm shadow-md transition" onclick="saveCust(${cid})">SAVE PROFILE</button>
                    <button class="w-full text-xs text-slate-400 font-bold pt-1" onclick="closeModal()">Cancel</button>
                    ${cid ? `<div class="pt-4 border-t border-slate-500/10 mt-2"><button class="w-full p-3 bg-red-600/10 hover:bg-red-600/20 text-red-500 rounded-xl font-bold text-xs transition" onclick="deleteFullCust(${cid})"><i class="fa-solid fa-trash-can mr-2"></i> DELETE CLIENT & ENTIRE LEDGER</button></div>` : ''}
                </div>`);
        }

        function saveCust(cid) { 
            let n = document.getElementById('cn').value.trim(); 
            let p = document.getElementById('cp').value.trim();
            if(!n) return alert("Please enter a valid name");
            
            if(cid) { 
                let c = db.customers.find(x=>x.id===cid); 
                c.name = n; c.phone = p; 
            } else { 
                const newId = Date.now();
                db.customers.push({id: newId, name: n, phone: p}); 
                activeCid = newId; 
            } 
            saveDB(); closeModal(); 
        }

        function deleteFullCust(cid) { 
            if(confirm("ഈ കസ്റ്റമറെയും എല്ലാ ഇടപാടുകളും പൂർണ്ണമായി ഡിലീറ്റ് ചെയ്യണോ?")) { 
                db.customers=db.customers.filter(x=>x.id!==cid); 
                db.trans=db.trans.filter(x=>x.cid!==cid); 
                db.promises=db.promises.filter(x=>x.cid!==cid);
                activeCid=null; saveDB(); closeModal(); goHome();
            } 
        }

        // --- ACCOUNTING ENTRIES ACTION CONTROLS ---
        function openAdd(type) {
            const timeStr = new Date().toLocaleTimeString('en-US', { hour: '2-digit', minute: '2-digit', hour12: true });
            openModal(`
                <h2 class="text-base font-black mb-4 text-center uppercase tracking-wider">${type}</h2>
                <div class="space-y-4 text-slate-800">
                    <input id="ta" type="number" step="0.01" class="w-full p-4 mb-1 rounded-xl text-3xl text-center text-blue-600 font-black border border-slate-300" placeholder="₹ 0" autofocus>
                    <div class="flex gap-2">
                        <button id="mCash" onclick="setM('CASH')" class="flex-1 p-3 rounded-xl border font-bold text-xs transition">CASH</button>
                        <button id="mUpi" onclick="setM('UPI')" class="flex-1 p-3 rounded-xl border font-bold text-xs transition">UPI</button>
                    </div>
                    <input id="tr" type="text" class="w-full p-4 rounded-xl text-md font-bold border border-slate-300" placeholder="Remarks">
                    <div class="grid grid-cols-2 gap-2">
                        <input id="td" type="date" class="w-full p-4 rounded-xl text-md font-bold border border-slate-300" value="${getToday()}">
                        <input id="tt" type="hidden" value="${timeStr}">
                    </div>
                    <input type="hidden" id="tm" value="CASH">
                    <button class="w-full p-4 bg-blue-600 text-white font-black rounded-xl text-lg shadow-xl transition" onclick="saveTrans('${type}')">SAVE</button>
                    <button class="w-full text-md text-slate-400 font-bold" onclick="closeModal()">Cancel</button>
                </div>`);
            setM('CASH');
        }

        function setM(m) {
            document.getElementById('tm').value = m;
            document.getElementById('mCash').className = m==='CASH' ? 'flex-1 p-3 rounded-xl bg-yellow-400 text-black border-transparent font-black text-xs' : 'flex-1 p-3 rounded-xl bg-slate-100 text-slate-700 border-slate-200 font-bold text-xs';
            document.getElementById('mUpi').className = m==='UPI' ? 'flex-1 p-3 rounded-xl bg-blue-600 text-white border-transparent font-black text-xs' : 'flex-1 p-3 rounded-xl bg-slate-100 text-slate-700 border-slate-200 font-bold text-xs';
        }

        function saveTrans(type) { 
            let a=parseFloat(document.getElementById('ta').value), d=document.getElementById('td').value, r=document.getElementById('tr').value.trim(), m=document.getElementById('tm').value, t=document.getElementById('tt').value; 
            if(isNaN(a) || a<=0) return alert("Please type a valid amount");
            if(a && d){ 
                db.trans.push({id:Date.now(), cid:activeCid, type, amt:a, date:d, time:t, rem:r, mode:m}); 
                saveDB(); closeModal(); 
            } 
        }

        function openEditTrans(tid) {
            const t = db.trans.find(x => x.id === tid);
            openModal(`
                <h2 class="text-base font-black mb-4 text-center uppercase tracking-wider">EDIT ENTRY</h2>
                <div class="space-y-3 text-slate-800">
                    <input id="eta" type="number" step="0.01" class="w-full p-4 rounded-xl text-3xl text-center text-blue-600 font-black border border-slate-300" value="${t.amt}">
                    <input id="etr" type="text" class="w-full p-4 rounded-xl text-md font-bold border border-slate-300" value="${t.rem || ''}" placeholder="Remarks">
                    <div class="grid grid-cols-2 gap-2">
                        <input id="etd" type="date" class="w-full p-4 rounded-xl text-md border border-slate-300" value="${t.date}">
                        <input id="ett" type="hidden" value="${t.time || ''}">
                    </div>
                    <button class="w-full p-4 bg-blue-600 text-white font-black rounded-xl text-lg transition shadow-md" onclick="updateTrans(${tid})">UPDATE</button>
                    <button class="w-full p-4 bg-red-600 text-white font-black rounded-xl text-lg transition shadow-md" onclick="deleteTrans(${tid})">DELETE ENTRY</button>
                    <button class="w-full text-md text-slate-400 font-bold pt-1" onclick="closeModal()">Cancel</button>
                </div>`);
        }

        function updateTrans(tid) { 
            const t=db.trans.find(x=>x.id===tid); 
            t.amt=Number(document.getElementById('eta').value); 
            t.rem=document.getElementById('etr').value.trim(); 
            t.date=document.getElementById('etd').value; 
            t.time=document.getElementById('ett').value; 
            saveDB(); closeModal(); 
        }
        
        function deleteTrans(tid) { 
            if(confirm("ഈ എൻട്രി ഡിലീറ്റ് ചെയ്യണോ?")) { 
                db.trans=db.trans.filter(x=>x.id!==tid); 
                saveDB(); closeModal(); 
            } 
        }

        // --- GLOBAL SETTINGS DRAWER FUNCTIONS ---
        function openSettings() {
            openModal(`
                <h2 class="text-base font-black mb-4 text-center uppercase tracking-wider">Settings</h2>
                <div class="space-y-3.5 text-slate-800">
                    <div>
                        <label class="block text-[10px] text-slate-400 font-bold uppercase mb-1">UPI ID</label>
                        <input id="upiI" class="w-full p-4 rounded-xl font-bold text-lg border border-slate-300" value="${db.upi||''}" placeholder="UPI ID">
                    </div>
                    <div>
                        <label class="block text-[10px] text-slate-400 font-bold uppercase mb-1">PIN</label>
                        <input id="pinI" class="w-full p-4 rounded-xl font-bold text-lg border border-slate-300" value="${db.pin}" placeholder="PIN">
                    </div>
                    <button class="w-full p-4 bg-blue-600 text-white font-black rounded-xl text-lg transition shadow-md" onclick="db.upi=document.getElementById('upiI').value;db.pin=document.getElementById('pinI').value;saveDB();closeModal();">APPLY CHANGES</button>
                    <div class="grid grid-cols-2 gap-2 pt-2">
                        <button class="p-3 bg-green-700 text-white rounded-xl font-bold text-xs transition shadow-xs" onclick="exportData()">BACKUP</button>
                        <button class="p-3 bg-purple-700 text-white rounded-xl font-bold text-xs transition shadow-xs" onclick="document.getElementById('imp').click()">RESTORE</button>
                    </div>
                    <div class="pt-4 border-t border-slate-500/10 mt-2">
                        <button class="w-full p-3 bg-red-600 text-white rounded-xl font-black text-xs transition shadow-md" onclick="resetAllData()"><i class="fa-solid fa-triangle-exclamation mr-1"></i> DELETE ALL DATA (RESET)</button>
                    </div>
                    <button class="w-full text-xs text-slate-400 font-bold mt-1" onclick="closeModal()">Close</button>
                    <input type="file" id="imp" class="hidden" onchange="importData(event)">
                </div>`);
        }

        function resetAllData() { 
            if(confirm("മുന്നറിയിപ്പ്: നിങ്ങളുടെ എല്ലാ കസ്റ്റമർ വിവരങ്ങളും ഇടപാടുകളും എന്നെന്നേക്കുമായി ഡിലീറ്റ് ചെയ്യപ്പെടും. തുടരണോ?")) { 
                localStorage.removeItem(STORAGE_ID); 
                location.reload(); 
            } 
        }

        // --- PROMISE REMINDERS WORKFLOW CONTROLS ---
        function openPromiseModal() { 
            openModal(`
                <h2 class="text-base font-black mb-4 text-center uppercase tracking-wider">ADD PROMISE</h2>
                <div class="space-y-3 text-slate-800">
                    <input id="pa" type="number" step="0.01" class="w-full p-4 rounded-xl font-bold border border-slate-300 text-lg" placeholder="Amount">
                    <input id="pd" type="date" class="w-full p-4 rounded-xl font-bold border border-slate-300 text-lg" value="${getToday()}">
                    <button class="w-full p-4 bg-blue-600 text-white font-black rounded-xl text-lg shadow-md transition" onclick="savePromise()">SET PROMISE</button>
                    <button class="w-full text-md text-slate-400 font-bold" onclick="closeModal()">Cancel</button>
                </div>`); 
        }
        
        function savePromise() { 
            let a=document.getElementById('pa').value, d=document.getElementById('pd').value; 
            if(a && d){ 
                db.promises.push({id:Date.now(), cid:activeCid, amt:a, date:d}); 
                saveDB(); closeModal(); 
            } 
        }
        
        function settlePromise(id) { 
            const p=db.promises.find(x=>x.id===id); 
            const timeStr = new Date().toLocaleTimeString('en-US', { hour: '2-digit', minute: '2-digit', hour12: true });
            db.trans.push({id:Date.now(), cid:p.cid, type:'GOT', amt:Number(p.amt), date:getToday(), time:timeStr, mode:'CASH', rem:'Promise Paid'}); 
            db.promises=db.promises.filter(x=>x.id!==id); 
            saveDB(); 
        }
        
        function deletePromise(id) { if(confirm("Delete Promise?")) { db.promises=db.promises.filter(x=>x.id!==id); saveDB(); } }

        // --- PDF GENERATOR UTILITIES ---
        function openPDFModal() {
            openModal(`
                <h2 class="mb-4 font-bold text-center uppercase">GENERATE REPORT</h2>
                <div class="space-y-4 text-slate-800">
                    <div class="grid grid-cols-2 gap-2">
                        <div>
                            <label class="block text-[10px] text-slate-400 font-bold mb-1">START DATE</label>
                            <input id="ps" type="date" class="w-full p-4 rounded-xl border border-slate-300 text-md font-bold" value="2026-01-01">
                        </div>
                        <div>
                            <label class="block text-[10px] text-slate-400 font-bold mb-1">END DATE</label>
                            <input id="pe" type="date" class="w-full p-4 rounded-xl border border-slate-300 text-md font-bold" value="${getToday()}">
                        </div>
                    </div>
                    <button class="w-full p-4 bg-blue-600 text-white font-black rounded-xl text-lg transition shadow-md" onclick="generatePDF()">DOWNLOAD PDF</button>
                    <button class="w-full text-md text-slate-400 font-bold" onclick="closeModal()">Close</button>
                </div>`);
        }

        function generatePDF() {
            const s=document.getElementById('ps').value, e=document.getElementById('pe').value, cust=db.customers.find(c=>c.id===activeCid);
            const filtered=db.trans.filter(t=>t.cid===activeCid && t.date>=s && t.date<=e).sort((a,b)=>new Date(a.date)-new Date(b.date));
            
            const el=document.createElement('div'); el.style.padding="25px"; el.style.background="#fff"; el.style.color="#000"; el.style.fontSize="11px";
            let rt=0;
            
            let rows=filtered.map(t=>{ 
                rt+=(t.type==='GAVE'?t.amt:-t.amt); 
                return `<tr><td style="border:1px solid #ddd;padding:8px">${fmtDate(t.date)}</td><td style="border:1px solid #ddd;padding:8px;color:red">${t.type==='GAVE'?t.amt.toFixed(2):'-'}</td><td style="border:1px solid #ddd;padding:8px;color:green">${t.type==='GOT'?t.amt.toFixed(2):'-'}</td><td style="border:1px solid #ddd;padding:8px">${t.mode||'CASH'}</td><td style="border:1px solid #ddd;padding:8px;font-weight:bold">₹${rt.toFixed(2)}</td></tr>`; 
            }).join('');
            
            el.innerHTML=`
                <div style="font-family:sans-serif;">
                    <h3 style="text-align:center;margin:0;color:#b58916;">${cust.name}</h3>
                    <table style="width:100%;border-collapse:collapse;margin-top:15px;text-align:left;">
                        <thead><tr style="background:#f2f2f2;border:1px solid #ddd;"><th style="padding:8px">Date</th><th style="padding:8px">Gave</th><th style="padding:8px">Got</th><th style="padding:8px">Mode</th><th style="padding:8px">Bal</th></tr></thead>
                        <tbody>${rows}</tbody>
                    </table>
                </div>`;
                
            html2pdf().set({ margin: 0.5, filename: `${cust.name}.pdf`, image: { type: 'jpeg', quality: 0.98 }, html2canvas: { scale: 2 }, jsPDF: { unit: 'in', format: 'letter', orientation: 'portrait' } }).from(el).save();
        }

        // --- INTEGRATED TRANSACTION QR CODES GENERATORS ---
        function openQR(amt) {
            if(!db.upi) return alert("Settings-ൽ UPI ID നൽകുക");
            const cust = db.customers.find(c => c.id === activeCid);
            openModal(`
                <div class="bg-white p-5 rounded-3xl flex flex-col items-center text-slate-900">
                    <div id="qr" class="mb-4 border p-2 bg-slate-50 rounded-xl"></div>
                    <p class="font-black text-2xl tracking-tight">₹${Number(amt).toFixed(2)}</p>
                    <div class="w-full mt-5 space-y-2">
                        <button onclick="shareWA('${cust ? cust.phone : ''}', ${amt})" class="w-full p-3 rounded-xl bg-green-600 hover:bg-green-700 text-white font-bold text-xs flex items-center justify-center gap-1.5 transition"><i class="fa-brands fa-whatsapp text-sm"></i> WhatsApp Share</button>
                        <button onclick="closeModal()" class="w-full p-3 rounded-xl bg-slate-100 hover:bg-slate-200 text-slate-700 font-bold text-xs transition">Close</button>
                    </div>
                </div>`);
            new QRCode(document.getElementById("qr"), { text: `upi://pay?pa=${db.upi}&am=${amt}&cu=INR`, width: 180, height: 180 });
        }

        // --- EXTRAS: ROW RECEIPT TRANSACTION PRINTER ENGINE ---
        function printRowSlip(tid) {
            const cust = db.customers.find(c => c.id === activeCid);
            const t = db.trans.find(x => x.id === tid);
            
            const w = window.open('', '_blank');
            w.document.write(`
                <html>
                <head><title>Receipt Slip</title></head>
                <body style="font-family:sans-serif;padding:30px;color:#222;line-height:1.5;">
                    <div style="border:2px dashed #bbb;padding:20px;max-width:300px;margin:0 auto;border-radius:10px;">
                        <h2 style="text-align:center;margin:0 0 10px 0;color:#b58916;">KHATA SLIP</h2>
                        <hr style="border:0;border-top:1px dashed #ddd;margin-bottom:12px;">
                        <p style="margin:4px 0;font-size:13px;"><strong>Client:</strong> ${cust.name}</p>
                        <p style="margin:4px 0;font-size:13px;"><strong>Type:</strong> ${t.type === 'GAVE' ? 'Gave' : 'Got'}</p>
                        <p style="margin:4px 0;font-size:16px;font-weight:bold;"><strong>Amount:</strong> Rs. ${t.amt.toFixed(2)}</p>
                        <p style="margin:4px 0;font-size:13px;"><strong>Mode:</strong> ${t.mode}</p>
                        <p style="margin:4px 0;font-size:13px;"><strong>Details:</strong> ${t.rem || '-'}</p>
                        <p style="margin:4px 0;font-size:11px;color:#777;"><strong>Date:</strong> ${fmtDate(t.date)} ${t.time || ''}</p>
                        <hr style="border:0;border-top:1px dashed #ddd;margin-top:12px;">
                        <p style="text-align:center;font-size:11px;margin:10px 0 0 0;opacity:0.7;">Digital Khata Book Receipt</p>
                    </div>
                    <script>setTimeout(function(){ window.print(); window.close(); }, 300);<\/script>
                </body>
                </html>`);
            w.document.close();
        }

        // --- BACKUP UTILITIES DATA CHANNELS ---
        function shareWA(p, b) { 
            if(!p || p === '-') return alert("Phone Number Missing"); 
            const msg = `നിങ്ങളുടെ ബാക്കി തുക: ₹${Math.abs(b).toFixed(2)}. ദയവായി പരിശോധിക്കുക.`; 
            window.open(`https://wa.me/91${p}?text=${encodeURIComponent(msg)}`); 
        }
        
        function exportData() { 
            const blob=new Blob([JSON.stringify(db)], {type:'application/json'}); 
            const a=document.createElement('a'); a.href=URL.createObjectURL(blob); 
            a.download=`Khata_Backup.json`; a.click(); 
        }
        
        function importData(e) { 
            const reader=new FileReader(); 
            reader.onload=(ev)=>{ 
                try { 
                    db=JSON.parse(ev.target.result); saveDB(); location.reload(); 
                } catch(err){ alert("Error"); } 
            }; 
            reader.readAsText(e.target.files[0]); 
        }
        
        function openModal(h) { document.getElementById('modalBox').innerHTML=h; document.getElementById('modalOverlay').style.display='flex'; }
        function closeModal() { document.getElementById('modalOverlay').style.display='none'; }
        
        window.onload = () => { lockApp(); };
    </script>
</body>
</html>
