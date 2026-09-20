<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SHE Core Sentinel | Intelligent Safety Network</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        @keyframes pulse-red {
            0%, 100% { transform: scale(1); opacity: 1; }
            50% { transform: scale(1.05); opacity: 0.8; shadow: 0 0 20px #ef4444; }
        }
        .emergency-active { animation: pulse-red 1s infinite; border: 2px solid #ef4444; }
        .bg-grid { background-image: radial-gradient(#2d2d2d 1px, transparent 1px); background-size: 20px 20px; }
    </style>
</head>
<body class="bg-black text-slate-200 font-sans bg-grid">

    <nav class="p-6 border-b border-white/10 flex justify-between items-center backdrop-blur-md sticky top-0 z-50">
        <div class="flex items-center gap-2">
            <i data-lucide="shield-alert" class="text-red-600 w-8 h-8"></i>
            <span class="font-bold text-xl tracking-tighter">SHE CORE <span class="text-red-600">SENTINEL</span></span>
        </div>
        <div class="flex gap-6 text-sm uppercase tracking-widest text-slate-400">
            <span class="text-green-500 flex items-center gap-1"><i data-lucide="wifi"></i> System: Online</span>
        </div>
    </nav>

    <section class="max-w-6xl mx-auto px-6 py-20 grid lg:grid-cols-2 gap-12 items-center">
        <div>
            <h2 class="text-red-500 font-mono mb-4 text-sm tracking-[0.3em] uppercase underline decoration-2 underline-offset-8">Response time kills.</h2>
            <h1 class="text-6xl font-black leading-none mb-6">NOT JUST AN ALERT SYSTEM. <br><span class="text-white/40">A SYSTEM THAT ACTS.</span></h1>
            <p class="text-slate-400 text-lg mb-8 max-w-md">Autonomous, layered protection that triggers, alerts, and coordinates rescue—even when the network fails.</p>
            <button onclick="document.getElementById('demo').scrollIntoView({behavior: 'smooth'})" class="bg-red-600 hover:bg-red-700 text-white px-8 py-4 font-bold rounded-sm transition-all uppercase tracking-widest shadow-lg shadow-red-900/20">
                Test the Failsafe
            </button>
        </div>
        
        <div class="relative flex justify-center items-center h-[400px]">
            <div class="absolute w-80 h-80 border border-white/5 rounded-full"></div>
            <div class="absolute w-60 h-60 border border-white/10 rounded-full"></div>
            <div class="absolute w-40 h-40 border border-red-500/20 rounded-full animate-ping"></div>
            <div class="relative z-10 bg-black p-6 border-2 border-red-600 rounded-xl shadow-2xl shadow-red-900/40 text-center">
                <i data-lucide="user" class="w-12 h-12 mx-auto mb-2 text-white"></i>
                <p class="text-[10px] font-mono uppercase text-red-500">Sentinel Active</p>
            </div>
        </div>
    </section>

    <section id="demo" class="max-w-6xl mx-auto px-6 py-20 border-t border-white/10">
        <div class="grid lg:grid-cols-3 gap-8">
            
            <div class="bg-zinc-900/50 p-8 border border-white/5 rounded-lg">
                <h3 class="font-bold mb-6 flex items-center gap-2"><i data-lucide="zap" class="text-yellow-500"></i> SIMULATION TRIGGERS</h3>
                <div class="space-y-4">
                    <button onclick="triggerAlert('FALL_DETECTED')" class="w-full text-left p-4 bg-white/5 hover:bg-red-600/20 border border-white/10 rounded transition-colors group">
                        <span class="block font-bold group-hover:text-red-400">Impact Detected</span>
                        <span class="text-xs text-slate-500 uppercase">MPU6050 > 4G Threshold</span>
                    </button>
                    <button onclick="triggerAlert('PANIC')" class="w-full text-left p-4 bg-white/5 hover:bg-red-600/20 border border-white/10 rounded transition-colors group">
                        <span class="block font-bold group-hover:text-red-400">Panic Press</span>
                        <span class="text-xs text-slate-500 uppercase">Manual Hardware Trigger</span>
                    </button>
                    <button onclick="resetSystem()" class="w-full p-2 text-xs text-slate-500 hover:text-white underline uppercase">Reset System</button>
                </div>
            </div>

            <div id="status-card" class="lg:col-span-2 bg-zinc-900/80 p-8 border border-white/10 rounded-lg">
                <div class="flex justify-between items-center mb-6">
                    <h3 class="font-bold flex items-center gap-2"><i data-lucide="activity"></i> CONFIDENCE ENGINE</h3>
                    <div id="threat-level" class="text-green-500 font-mono text-sm">THREAT: 0%</div>
                </div>
                
                <div id="log-container" class="font-mono text-sm space-y-2 h-48 overflow-y-auto mb-6 p-4 bg-black/50 rounded border border-white/5">
                    <div class="text-blue-400">[SYSTEM] Initialization complete...</div>
                    <div class="text-slate-500">[IDLE] Monitoring MPU6050 & GSM Heartbeat...</div>
                </div>

                <div class="grid grid-cols-3 gap-4">
                    <div id="wifi-stat" class="p-3 bg-white/5 border border-white/10 rounded text-center opacity-50">
                        <i data-lucide="cloud" class="w-5 h-5 mx-auto mb-1"></i>
                        <span class="text-[10px] uppercase font-bold">Cloud (WiFi)</span>
                    </div>
                    <div id="gsm-stat" class="p-3 bg-white/5 border border-white/10 rounded text-center opacity-50">
                        <i data-lucide="radio" class="w-5 h-5 mx-auto mb-1"></i>
                        <span class="text-[10px] uppercase font-bold">GSM (Sim800)</span>
                    </div>
                    <div id="zigbee-stat" class="p-3 bg-white/5 border border-white/10 rounded text-center opacity-50">
                        <i data-lucide="network" class="w-5 h-5 mx-auto mb-1"></i>
                        <span class="text-[10px] uppercase font-bold">Zigbee (Mesh)</span>
                    </div>
                </div>
            </div>

        </div>
    </section>

    <section class="max-w-6xl mx-auto px-6 py-20 border-t border-white/10 text-center">
        <h2 class="text-2xl font-bold mb-12">SYSTEM ARCHITECTURE</h2>
        <div class="grid md:grid-cols-3 gap-0 border border-white/10 rounded-xl overflow-hidden">
            <div class="p-8 border-r border-white/10 bg-white/[0.02]">
                <h4 class="text-red-500 text-xs font-bold uppercase mb-4 tracking-widest">Perception</h4>
                <p class="font-bold">MPU6050 / Tamper</p>
                <p class="text-sm text-slate-500 mt-2">Continuous gait & impact monitoring via I2C.</p>
            </div>
            <div class="p-8 border-r border-white/10 bg-white/[0.04]">
                <h4 class="text-red-500 text-xs font-bold uppercase mb-4 tracking-widest">Logic</h4>
                <p class="font-bold">ESP32 Core</p>
                <p class="text-sm text-slate-500 mt-2">Local decision making with confidence scoring.</p>
            </div>
            <div class="p-8 bg-white/[0.02]">
                <h4 class="text-red-500 text-xs font-bold uppercase mb-4 tracking-widest">Transport</h4>
                <p class="font-bold">Triple-Redundancy</p>
                <p class="text-sm text-slate-500 mt-2">GSM + Zigbee Mesh + WiFi Fallback.</p>
            </div>
        </div>
    </section>

    <script>
        // Initialize Lucide Icons
        lucide.createIcons();

        function addLog(message, color = "text-slate-400") {
            const container = document.getElementById('log-container');
            const time = new Date().toLocaleTimeString([], { hour12: false });
            container.innerHTML += `<div class="${color}">[${time}] ${message}</div>`;
            container.scrollTop = container.scrollHeight;
        }

        function triggerAlert(type) {
            const statusCard = document.getElementById('status-card');
            const threatText = document.getElementById('threat-level');
            
            statusCard.classList.add('emergency-active');
            threatText.innerHTML = "THREAT: 98.4%";
            threatText.className = "text-red-500 font-bold font-mono text-sm";

            if(type === 'FALL_DETECTED') {
                addLog("CRITICAL: High-G Impact Detected!", "text-red-500 font-bold");
                addLog("ENGINE: Processing movement patterns...", "text-yellow-500 text-xs");
            } else {
                addLog("ALERT: SOS Manual Trigger Activated!", "text-red-500 font-bold");
            }

            // Simulate the Layered Protocol Logic
            setTimeout(() => {
                addLog("TRANSPORT: WiFi Connection timed out (Simulated Jamming).", "text-orange-400");
                document.getElementById('wifi-stat').classList.add('bg-red-900/20', 'border-red-500');
            }, 800);

            setTimeout(() => {
                addLog("TRANSPORT: Switching to GSM Protocol...", "text-green-400");
                document.getElementById('gsm-stat').classList.remove('opacity-50');
                document.getElementById('gsm-stat').classList.add('bg-green-900/20', 'border-green-500');
            }, 1800);

            setTimeout(() => {
                addLog("SUCCESS: Coordinates sent to Local Police & SOS Contacts.", "text-green-400 font-bold");
                addLog("ZIGBEE: Local Mesh Nodes notified for tracking.", "text-green-400");
                document.getElementById('zigbee-stat').classList.remove('opacity-50');
                document.getElementById('zigbee-stat').classList.add('bg-green-900/20', 'border-green-500');
            }, 3000);
        }

        function resetSystem() {
            location.reload();
        }
    </script>
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/10.7.1/firebase-app.js";
        import { getDatabase, ref, onValue } from "https://www.gstatic.com/firebasejs/10.7.1/firebase-database.js";

        // 1. Replace the URL below with your actual Firebase Database URL
        const firebaseConfig = {
            databaseURL: "https://she-sentinel-default-rtdb.firebaseio.com", 
        };

        // 2. Initialize Firebase
        const app = initializeApp(firebaseConfig);
        const db = getDatabase(app);

        // 3. Listen for changes from your ESP32
        const statusRef = ref(db, 'system/');
        onValue(statusRef, (snapshot) => {
            const data = snapshot.val();
            
            // If the ESP32 sends "EMERGENCY_TRIGGERED", start the website animation
            if (data && data.status === "EMERGENCY_TRIGGERED") {
                triggerAlert('FALL_DETECTED'); 
                
                // Update the threat level based on what the sensor says
                if(data.threatLevel) {
                    document.getElementById('threat-level').innerText = `THREAT: ${data.threatLevel}%`;
                }
            }
            
            // If the status is "IDLE", you can manually reset the UI
            if (data && data.status === "IDLE") {
                addLog("System Status: Monitoring...", "text-blue-400");
            }
        });
    </script>
</body>
</html>
