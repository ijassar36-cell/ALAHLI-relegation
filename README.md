<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
    <title>⏳ عداد هبوط الأهلي | دوري يلو</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
            touch-action: manipulation;
        }

        html {
            height: 100%;
            background: #010a08;
        }

        body {
            margin: 0;
            min-height: 100vh;
            min-height: 100dvh;
            padding-top: calc(16.5vh + env(safe-area-inset-top) + 8px);
            padding-left: env(safe-area-inset-left);
            padding-right: env(safe-area-inset-right);
            background: radial-gradient(ellipse at 30% 40%, #0a2f2a, #010a08);
            font-family: 'Segoe UI', 'Tahoma', 'Cairo', system-ui, -apple-system, BlinkMacSystemFont, sans-serif;
            display: flex;
            align-items: flex-start;
            justify-content: center;
            overflow-x: hidden;
            -webkit-text-size-adjust: 100%;
            position: relative;
        }

        /* ----- البار العلوي: خلفية الصورة + مربع مميز ----- */
        .top-bar {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: auto;
            min-height: 30.3vh;
            background: url('https://i.ibb.co/XfY4TcH7/EC3-DE5-E1-58-D1-4-F19-831-D-28142868695-A.png') no-repeat center center;
            background-size: cover;
            border-bottom: 2px solid rgba(0, 255, 200, 0.35);
            box-shadow: 0 6px 14px rgba(0, 0, 0, 0.5);
            display: flex;
            align-items: flex-end;
            justify-content: center;
            z-index: 9999;
            padding-bottom: 12px;
            padding-top: env(safe-area-inset-top);
            box-sizing: border-box;
            pointer-events: none;
        }
        
        .top-bar .highlight-box {
            pointer-events: auto;
            background: rgba(0, 15, 12, 0.8);
            backdrop-filter: blur(12px);
            border-radius: 50px;
            padding: 10px 22px;
            margin-bottom: 12px;
            border: 1px solid rgba(0, 255, 200, 0.7);
            box-shadow: 0 0 14px rgba(0, 255, 200, 0.4), inset 0 0 6px rgba(0, 255, 200, 0.2);
        }
        
        .top-bar .highlight-box span {
            font-weight: bold;
            color: #eafff0;
            font-size: clamp(0.85rem, 4.4vw, 1.1rem);
            text-align: center;
            text-shadow: 0 0 5px #00ccaa;
            letter-spacing: 0.3px;
            line-height: 1.45;
        }

        /* شبكة خلفية */
        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: repeating-linear-gradient(45deg, rgba(0,255,200,0.02) 0px, rgba(0,255,200,0.02) 2px, transparent 2px, transparent 8px);
            pointer-events: none;
            z-index: 0;
        }

        .card {
            position: relative;
            z-index: 2;
            background: rgba(5, 25, 22, 0.72);
            backdrop-filter: blur(18px);
            border-radius: 48px;
            padding: 22px 20px 28px;
            max-width: 600px;
            width: 100%;
            margin: 0px 16px 24px 16px;
            text-align: center;
            box-shadow: 0 35px 55px rgba(0, 0, 0, 0.6), 0 0 0 1.5px rgba(0, 255, 200, 0.3), 0 0 20px rgba(0, 255, 200, 0.3);
            border: 1px solid rgba(0, 255, 200, 0.4);
        }

        .logo-area {
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 8px;
        }
        .club-logo {
            max-width: 27px;
            width: 100%;
            height: auto;
            filter: drop-shadow(0 0 8px #00ffcc) contrast(1.05) brightness(1.02);
            transition: transform 0.2s ease;
            border-radius: 20px;
            background: transparent;
            mix-blend-mode: multiply;
        }
        .club-logo:active {
            transform: scale(0.97);
        }

        .counter-box {
            background: rgba(0, 20, 18, 0.7);
            backdrop-filter: blur(8px);
            padding: 22px 12px;
            border-radius: 40px;
            margin: 12px 0 16px;
            box-shadow: inset 0 0 15px #00000055, 0 12px 28px rgba(0, 0, 0, 0.5), 0 0 0 1px rgba(0, 255, 200, 0.4);
            border: 1px solid rgba(0, 255, 200, 0.5);
        }

        /* العداد: الأرقام ثم الكلمة (يوم، ساعة، دقيقة، ثانية) */
        .counter {
            font-size: clamp(1.6rem, 5vw, 2.8rem);
            font-weight: bold;
            font-family: 'Fira Mono', 'Courier New', 'Cascadia Code', monospace;
            line-height: 1.6;
            color: #ebfff9;
            text-shadow: 0 0 8px #00ffc3, 0 0 2px #00ccaa;
            word-break: break-word;
            letter-spacing: 1px;
            animation: subtleGlow 2s infinite alternate;
            direction: ltr;      /* الأرقام ثم النص العربي يظهر بشكل طبيعي */
            text-align: center;
        }

        .counter br {
            display: block;
            margin: 5px 0;
        }

        .contact-area {
            margin-top: 20px;
            background: rgba(0, 30, 26, 0.7);
            backdrop-filter: blur(8px);
            border-radius: 60px;
            padding: 12px 16px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 12px;
            flex-wrap: wrap;
            border: 0.5px solid rgba(0, 255, 200, 0.4);
        }
        .contact-text {
            font-size: 0.85rem;
            color: #effffa;
            font-weight: 500;
        }
        .whatsapp-icon {
            width: 24px;
            height: 24px;
            filter: drop-shadow(0 0 3px #25D366);
        }
        .whatsapp-link {
            display: inline-flex;
            align-items: center;
            gap: 6px;
            text-decoration: none;
            background: #075e5440;
            padding: 6px 14px;
            border-radius: 40px;
            transition: all 0.2s;
            border: 0.5px solid #6effdc60;
        }
        .whatsapp-link:active {
            transform: scale(0.97);
            background: #25d36640;
        }
        .whatsapp-link span {
            color: #dafef2;
            font-weight: 600;
            font-size: 0.85rem;
            direction: ltr;
        }

        .forever-note {
            font-size: 0.72rem;
            margin-top: 12px;
            color: #d2fff0;
            background: rgba(0,0,0,0.3);
            display: inline-block;
            padding: 5px 16px;
            border-radius: 50px;
            backdrop-filter: blur(4px);
            font-weight: 500;
        }

        .footnote {
            margin-top: 16px;
            font-size: 0.6rem;
            opacity: 0.7;
            border-top: 1px dashed #2effcf60;
            padding-top: 12px;
            color: #e1fff2;
        }

        @media (max-width: 550px) {
            body {
                padding-top: calc(17vh + env(safe-area-inset-top) + 5px);
            }
            .card {
                padding: 18px 14px 24px;
                border-radius: 40px;
                margin: 0 12px 20px 12px;
            }
            .club-logo {
                max-width: 38px;
            }
            .counter {
                font-size: clamp(1.4rem, 4.8vw, 2.3rem);
            }
            .contact-area {
                padding: 10px 12px;
                gap: 8px;
            }
            .whatsapp-link {
                padding: 4px 12px;
            }
            .whatsapp-link span {
                font-size: 0.75rem;
            }
            .contact-text {
                font-size: 0.75rem;
            }
            .forever-note {
                font-size: 0.65rem;
            }
            .top-bar .highlight-box {
                padding: 6px 16px;
                margin-bottom: 8px;
            }
        }

        @media (max-width: 400px) {
            .counter {
                font-size: clamp(1.3rem, 4.5vw, 2rem);
            }
        }

        @keyframes subtleGlow {
            0% { text-shadow: 0 0 4px #00ffcc; }
            100% { text-shadow: 0 0 14px #00ffe0; }
        }
    </style>
</head>
<body>

<div class="top-bar">
    <div class="highlight-box">
        <span>📉 عداد هبوط نادي الأهلي إلى دوري يلو منذ ٢٧ يونيو ٢٠٢٢</span>
    </div>
</div>

<div class="card">
    <div class="logo-area">
        <img class="club-logo" src="https://i.ibb.co/HptMgQ2j/background-removed-background-removed.png" 
             alt="شعار النادي الأهلي السعودي" 
             title="النادي الأهلي">
    </div>
    
    <div class="counter-box">
        <div class="counter" id="counter">⏳ جارٍ التحميل...</div>
    </div>
    
    <div class="forever-note">
        🏴 عار الهبوط سيظل إلى الأبد
    </div>
    
    <div class="contact-area">
        <span class="contact-text">📞 للاستفسار والتواصل:</span>
        <strong style="color:#eafff0;">أحمد العتيبي</strong>
        <a href="https://wa.me/966551162550" target="_blank" class="whatsapp-link" rel="noopener noreferrer">
            <img class="whatsapp-icon" src="https://upload.wikimedia.org/wikipedia/commons/6/6b/WhatsApp.svg" alt="WhatsApp">
            <span>055 116 2550</span>
        </a>
    </div>
    <div class="footnote">
        🕒 تحديث دقيق لكل ثانية · توقيت الرياض
    </div>
</div>

<script>
    (function() {
        const RELEGATION_DATE_STR = "2022-06-27T00:00:00+03:00";
        let relegationTime = new Date(RELEGATION_DATE_STR);
        if (isNaN(relegationTime.getTime())) {
            const fallbackUTC = Date.UTC(2022, 5, 26, 21, 0, 0);
            relegationTime = new Date(fallbackUTC);
        }
        
        const counterEl = document.getElementById("counter");
        let lastSyncedRiyadhTime = null;
        let lastSyncPerf = null;
        let hasValidSync = false;
        
        function getCurrentRiyadhTime() {
            if (hasValidSync && lastSyncedRiyadhTime && lastSyncPerf !== null) {
                const elapsedMs = performance.now() - lastSyncPerf;
                return new Date(lastSyncedRiyadhTime.getTime() + elapsedMs);
            }
            const nowDevice = new Date();
            return new Date(nowDevice.getTime() + (3 * 60 * 60 * 1000));
        }
        
        function computeTimeDifference(riyadhNow) {
            if (!riyadhNow || isNaN(riyadhNow.getTime())) return null;
            const diffMs = riyadhNow - relegationTime;
            if (diffMs < 0) return { days: 0, hours: 0, minutes: 0, seconds: 0 };
            const totalSeconds = Math.floor(diffMs / 1000);
            const days = Math.floor(totalSeconds / 86400);
            const hours = Math.floor((totalSeconds % 86400) / 3600);
            const minutes = Math.floor((totalSeconds % 3600) / 60);
            const seconds = totalSeconds % 60;
            return { days, hours, minutes, seconds };
        }
        
        function renderCounter(diff) {
            if (!diff) {
                counterEl.innerHTML = "⚠️ خطأ في التوقيت";
                return;
            }
            const daysNum = diff.days;
            const hoursNum = diff.hours;
            const minutesNum = diff.minutes;
            const secondsNum = diff.seconds;
            const hoursStr = hoursNum < 10 ? '0' + hoursNum : hoursNum.toString();
            const minutesStr = minutesNum < 10 ? '0' + minutesNum : minutesNum.toString();
            const secondsStr = secondsNum < 10 ? '0' + secondsNum : secondsNum.toString();
            // الأرقام ثم الكلمات (بعد الرقم مباشرة)
            counterEl.innerHTML = `${daysNum} يوم<br>${hoursStr} ساعة<br>${minutesStr} دقيقة<br>${secondsStr} ثانية`;
        }
        
        function updateDisplay() {
            const currentRiyadh = getCurrentRiyadhTime();
            const diff = computeTimeDifference(currentRiyadh);
            renderCounter(diff);
        }
        
        async function syncWithAPITime() {
            try {
                const controller = new AbortController();
                const timeoutId = setTimeout(() => controller.abort(), 7000);
                const response = await fetch("https://worldtimeapi.org/api/timezone/Asia/Riyadh", {
                    signal: controller.signal,
                    cache: "no-store",
                    headers: { "Accept": "application/json" }
                });
                clearTimeout(timeoutId);
                if (!response.ok) throw new Error(`HTTP ${response.status}`);
                const data = await response.json();
                if (!data || !data.utc_datetime) throw new Error("no utc_datetime");
                const utcDate = new Date(data.utc_datetime);
                if (isNaN(utcDate.getTime())) throw new Error("invalid utc");
                const riyadhTime = new Date(utcDate.getTime() + (3 * 60 * 60 * 1000));
                lastSyncedRiyadhTime = riyadhTime;
                lastSyncPerf = performance.now();
                hasValidSync = true;
                updateDisplay();
                return true;
            } catch (error) {
                updateDisplay();
                return false;
            }
        }
        
        let displayInterval = null;
        let syncInterval = null;
        
        function startDisplayTicker() {
            if (displayInterval) clearInterval(displayInterval);
            displayInterval = setInterval(() => updateDisplay(), 1000);
        }
        
        function startPeriodicSync() {
            if (syncInterval) clearInterval(syncInterval);
            syncInterval = setInterval(async () => { await syncWithAPITime(); }, 30000);
        }
        
        async function init() {
            startDisplayTicker();
            startPeriodicSync();
            await syncWithAPITime();
            document.addEventListener("visibilitychange", () => {
                if (!document.hidden && (!hasValidSync)) {
                    syncWithAPITime();
                } else if (!document.hidden && hasValidSync) {
                    updateDisplay();
                }
            });
        }
        
        init();
    })();
</script>
</body>
</html>
