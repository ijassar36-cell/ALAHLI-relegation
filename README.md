<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes, viewport-fit=cover">
    <title>⏳ عداد هبوط الأهلي | دوري يلو</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            min-height: 100vh;
            background: radial-gradient(ellipse at 30% 40%, #0a2f2a, #010a08);
            font-family: 'Segoe UI', 'Tahoma', 'Cairo', system-ui, -apple-system, BlinkMacSystemFont, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 16px;
            position: relative;
            overflow-x: hidden;
        }

        /* خلفية متحركة خفيفة */
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
            background: rgba(5, 25, 22, 0.7);
            backdrop-filter: blur(18px);
            border-radius: 48px;
            padding: 24px 20px 28px;
            max-width: 600px;
            width: 100%;
            text-align: center;
            box-shadow: 0 35px 55px rgba(0, 0, 0, 0.6), 0 0 0 1.5px rgba(0, 255, 200, 0.25), 0 0 20px rgba(0, 255, 200, 0.3);
            transition: all 0.3s ease;
            border: 1px solid rgba(0, 255, 200, 0.3);
        }

        .logo-area {
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 8px;
        }
        .club-logo {
            max-width: 150px;
            width: 100%;
            height: auto;
            filter: drop-shadow(0 0 12px #00ffcc) brightness(1.05);
            transition: transform 0.25s ease, filter 0.3s;
            border-radius: 20px;
        }
        .club-logo:hover {
            transform: scale(1.02);
            filter: drop-shadow(0 0 18px #66ffdd);
        }

        h1 {
            font-size: 1.6rem;
            font-weight: 800;
            background: linear-gradient(135deg, #e0fff5, #00f2d0);
            background-clip: text;
            -webkit-background-clip: text;
            color: transparent;
            letter-spacing: -0.3px;
            margin-bottom: 16px;
            text-shadow: 0 0 8px rgba(0,255,200,0.4);
            line-height: 1.3;
            padding: 0 4px;
        }

        .counter-box {
            background: rgba(0, 20, 18, 0.7);
            backdrop-filter: blur(8px);
            padding: 20px 12px;
            border-radius: 40px;
            margin: 12px 0 16px;
            box-shadow: inset 0 0 15px #00000055, 0 12px 28px rgba(0, 0, 0, 0.5), 0 0 0 1px rgba(0, 255, 200, 0.4);
            border: 1px solid rgba(0, 255, 200, 0.5);
        }

        .counter {
            font-size: 2.8rem;
            font-weight: bold;
            font-family: 'Fira Mono', 'Courier New', 'Cascadia Code', monospace;
            line-height: 1.4;
            color: #cafff5;
            text-shadow: 0 0 8px #00ffc3, 0 0 2px #00ccaa;
            word-break: break-word;
            letter-spacing: 1px;
        }

        .units {
            display: flex;
            justify-content: center;
            gap: 1.2rem;
            flex-wrap: wrap;
            margin-top: 12px;
            font-size: 0.85rem;
            font-weight: 600;
            color: #b2ffe6;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        /* تم إخفاء عنصر الحالة نهائياً */
        .status-area {
            display: none;
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
        .whatsapp-link:hover {
            background: #25d36630;
            transform: scale(1.02);
            border-color: #25D366;
        }
        .whatsapp-link span {
            color: #dafef2;
            font-weight: 600;
            font-size: 0.85rem;
            direction: ltr;
        }

        .forever-note {
            font-size: 0.7rem;
            margin-top: 12px;
            color: #bdffea;
            background: rgba(0,0,0,0.25);
            display: inline-block;
            padding: 5px 14px;
            border-radius: 50px;
            backdrop-filter: blur(4px);
        }

        .footnote {
            margin-top: 16px;
            font-size: 0.6rem;
            opacity: 0.65;
            border-top: 1px dashed #2effcf60;
            padding-top: 12px;
            color: #bbffee;
        }

        /* تحسينات الجوال */
        @media (max-width: 550px) {
            body {
                padding: 12px;
                align-items: flex-start;
                padding-top: 24px;
            }
            .card {
                padding: 20px 16px 24px;
                border-radius: 40px;
            }
            .counter {
                font-size: 2.2rem;
            }
            h1 {
                font-size: 1.35rem;
            }
            .club-logo {
                max-width: 120px;
            }
            .units {
                gap: 0.9rem;
                font-size: 0.75rem;
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
        }

        /* للأجهزة الصغيرة جداً */
        @media (max-width: 400px) {
            .counter {
                font-size: 1.8rem;
            }
            h1 {
                font-size: 1.2rem;
            }
            .units {
                gap: 0.7rem;
                font-size: 0.7rem;
            }
        }

        /* منع التكبير الزائد عبر اللمس (مع بقاء إمكانية التكبير اليدوي البسيط) */
        input, textarea, button, a {
            touch-action: manipulation;
        }

        /* تأثير وميض خفيف على العداد */
        @keyframes subtleGlow {
            0% { text-shadow: 0 0 4px #00ffcc; }
            100% { text-shadow: 0 0 12px #00ffe0; }
        }
        .counter {
            animation: subtleGlow 2s infinite alternate;
        }
    </style>
</head>
<body>
<div class="card">
    <div class="logo-area">
        <img class="club-logo" src="https://i.ibb.co/HptMgQ2j/background-removed-background-removed.png" 
             alt="شعار النادي الأهلي السعودي" 
             title="النادي الأهلي">
    </div>
    <h1>📉 عداد هبوط نادي الأهلي إلى دوري يلو<br>منذ ٢٧ يونيو ٢٠٢٢</h1>
    
    <div class="counter-box">
        <div class="counter" id="counter">⏳ جارٍ التحميل...</div>
        <div class="units">
            <span>📆 أيام</span>  <span>⏰ ساعات</span>  <span>⏱️ دقائق</span>  <span>⚡ ثواني</span>
        </div>
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
        // تاريخ الهبوط: 27 يونيو 2022 - 00:00:00 توقيت الرياض
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
            // خلفية آمنة (توقيت الجهاز +3) بدون رسائل
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
                counterEl.innerHTML = "⚠️ خطأ";
                return;
            }
            const daysStr = diff.days.toLocaleString('ar-EG');
            const hoursStr = diff.hours < 10 ? '0' + diff.hours : diff.hours;
            const minutesStr = diff.minutes < 10 ? '0' + diff.minutes : diff.minutes;
            const secondsStr = diff.seconds < 10 ? '0' + diff.seconds : diff.seconds;
            counterEl.innerHTML = `${daysStr} يوم<br>${hoursStr} ساعة<br>${minutesStr} دقيقة<br>${secondsStr} ثانية`;
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
                console.log("API sync failed, using local estimate");
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
                if (!document.hidden && (!hasValidSync)) syncWithAPITime();
            });
        }
        
        init();
    })();
</script>
</body>
</html>
