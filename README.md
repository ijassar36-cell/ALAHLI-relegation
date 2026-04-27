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
            /* منع تغطية البار العلوي الثابت بالمحتوى */
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

        /* ----- البار العلوي: بخلفية الصورة مع طبقة تعتيم لضمان قراءة النص ----- */
        .top-bar {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: auto;
            min-height: 30.3vh;
            /* إزالة الخلفية السابقة (التدرج) */
            background: none;
            border-bottom: 2px solid rgba(0, 255, 200, 0.5);
            box-shadow: 0 6px 14px rgba(0, 0, 0, 0.6);
            display: flex;
            align-items: flex-end;
            justify-content: center;
            z-index: 9999;
            padding-bottom: 12px;
            padding-top: env(safe-area-inset-top);
            box-sizing: border-box;
            pointer-events: none;
            position: relative;
            overflow: hidden;
        }

        /* صورة الخلفية الرئيسية */
        .top-bar::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url('https://i.ibb.co/XfY4TcH7/EC3-DE5-E1-58-D1-4-F19-831-D-28142868695-A.png');
            background-size: cover;
            background-position: center 30%;
            background-repeat: no-repeat;
            z-index: 0;
            pointer-events: none;
        }

        /* طبقة تعتيم شفافة لتحسين تباين النص والحد من شدة الصورة */
        .top-bar::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 8, 6, 0.65);
            backdrop-filter: brightness(0.85) blur(0.8px);
            z-index: 1;
            pointer-events: none;
        }

        /* النص داخل البار العلوي – يظهر فوق الطبقات مع خلفية مدمجة لقراءة فائقة */
        .top-bar span {
            position: relative;
            z-index: 3;
            font-weight: bold;
            color: #f0fffc;
            font-size: clamp(0.85rem, 4.4vw, 1.1rem);
            text-align: center;
            padding: 8px 18px;
            text-shadow: 0 0 8px #00ccaa, 0 0 3px #006655;
            letter-spacing: 0.3px;
            line-height: 1.45;
            pointer-events: auto;
            background: rgba(2, 20, 16, 0.7);
            backdrop-filter: blur(12px);
            border-radius: 60px;
            border: 1px solid rgba(0, 255, 200, 0.5);
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.3);
            margin: 8px 12px;
            width: auto;
            max-width: 90%;
            display: inline-block;
        }

        /* تأثير الخلفية (شبكة خفيفة) */
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
        /* تصغير الشعار – محافظ على النسبة */
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
            padding: 20px 12px;
            border-radius: 40px;
            margin: 12px 0 16px;
            box-shadow: inset 0 0 15px #00000055, 0 12px 28px rgba(0, 0, 0, 0.5), 0 0 0 1px rgba(0, 255, 200, 0.4);
            border: 1px solid rgba(0, 255, 200, 0.5);
        }

        /* عداد بأرقام إنجليزية (لاتينية) وتبقي النصوص العربية في سطور منفصلة */
        .counter {
            font-size: clamp(1.6rem, 5vw, 2.8rem);
            font-weight: bold;
            font-family: 'Fira Mono', 'Courier New', 'Cascadia Code', monospace;
            line-height: 1.45;
            color: #ebfff9;
            text-shadow: 0 0 8px #00ffc3, 0 0 2px #00ccaa;
            word-break: break-word;
            letter-spacing: 1px;
            animation: subtleGlow 2s infinite alternate;
            direction: ltr;   /* الأرقام باتجاه عربي/لاتيني صحيح */
        }

        /* ضمان أن النص العربي (يوم، ساعة…) يظهر بشكل منفصل مع الأرقام */
        .counter br {
            display: block;
            content: "";
            margin: 4px 0;
        }

        .units {
            display: flex;
            justify-content: center;
            gap: 1.3rem;
            flex-wrap: wrap;
            margin-top: 12px;
            font-size: 0.85rem;
            font-weight: 600;
            color: #bcffee;
            text-transform: uppercase;
            letter-spacing: 1px;
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

        /* تحسينات الجوال */
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
            .units {
                gap: 0.9rem;
                font-size: 0.75rem;
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
            .top-bar span {
                padding: 6px 14px;
                font-size: clamp(0.75rem, 4vw, 0.95rem);
                backdrop-filter: blur(10px);
            }
        }

        @media (max-width: 400px) {
            .units {
                gap: 0.7rem;
                font-size: 0.7rem;
            }
            .counter {
                font-size: clamp(1.3rem, 4.5vw, 2rem);
            }
            .top-bar {
                min-height: 32vh;
            }
            .top-bar span {
                padding: 5px 12px;
                max-width: 95%;
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
    <span>📉 عداد هبوط نادي الأهلي إلى دوري يلو منذ ٢٧ يونيو ٢٠٢٢</span>
</div>

<div class="card">
    <div class="logo-area">
        <img class="club-logo" src="https://i.ibb.co/HptMgQ2j/background-removed-background-removed.png" 
             alt="شعار النادي الأهلي السعودي" 
             title="النادي الأهلي">
    </div>
    
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
        // تاريخ الهبوط الرسمي – 27 يونيو 2022 بتوقيت الرياض (+03:00)
        const RELEGATION_DATE_STR = "2022-06-27T00:00:00+03:00";
        let relegationTime = new Date(RELEGATION_DATE_STR);
        if (isNaN(relegationTime.getTime())) {
            // Fallback آمن (توقيت UTC+3 نفس الـ 27 يونيو 2022)
            const fallbackUTC = Date.UTC(2022, 5, 26, 21, 0, 0);
            relegationTime = new Date(fallbackUTC);
        }
        
        const counterEl = document.getElementById("counter");
        
        // متغيرات تزامن الوقت مع API (آلية الاحتفاظ بالدقة)
        let lastSyncedRiyadhTime = null;
        let lastSyncPerf = null;
        let hasValidSync = false;
        
        // الحصول على الوقت الحالي في الرياض (توقيت +3)
        function getCurrentRiyadhTime() {
            if (hasValidSync && lastSyncedRiyadhTime && lastSyncPerf !== null) {
                const elapsedMs = performance.now() - lastSyncPerf;
                return new Date(lastSyncedRiyadhTime.getTime() + elapsedMs);
            }
            // احتياطي: استخدام وقت الجهاز مع إزاحة +3 ساعات (توقيت الرياض)
            const nowDevice = new Date();
            return new Date(nowDevice.getTime() + (3 * 60 * 60 * 1000));
        }
        
        // حساب الفرق منذ الهبوط (أيام وساعات ودقائق وثواني)
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
        
        // عرض العداد بأرقام إنجليزية (لاتينية) خصوصاً بعد عبارة "يوم"
        function renderCounter(diff) {
            if (!diff) {
                counterEl.innerHTML = "⚠️ خطأ في التوقيت";
                return;
            }
            // استخدام الأرقام الإنجليزية (الأساسية) عبر toString()
            const daysNum = diff.days;
            const hoursNum = diff.hours;
            const minutesNum = diff.minutes;
            const secondsNum = diff.seconds;
            
            const hoursStr = hoursNum < 10 ? '0' + hoursNum : hoursNum.toString();
            const minutesStr = minutesNum < 10 ? '0' + minutesNum : minutesNum.toString();
            const secondsStr = secondsNum < 10 ? '0' + secondsNum : secondsNum.toString();
            
            // تنسيق يوضح الأرقام بلغة لاتينية مع الكلمات العربية بعد كل رقم
            counterEl.innerHTML = `${daysNum} يوم<br>${hoursStr} ساعة<br>${minutesStr} دقيقة<br>${secondsStr} ثانية`;
        }
        
        function updateDisplay() {
            const currentRiyadh = getCurrentRiyadhTime();
            const diff = computeTimeDifference(currentRiyadh);
            renderCounter(diff);
        }
        
        // مزامنة دقيقة عبر API worldtimeapi (توقيت الرياض الرسمي)
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
                // تحويل إلى توقيت الرياض (UTC+3)
                const riyadhTime = new Date(utcDate.getTime() + (3 * 60 * 60 * 1000));
                
                lastSyncedRiyadhTime = riyadhTime;
                lastSyncPerf = performance.now();
                hasValidSync = true;
                updateDisplay();
                return true;
            } catch (error) {
                // في حالة فشل الـ API، يستمر العرض بالتقدير المحلي (مع احترام إزاحة الرياض)
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
            // مزامنة كل 30 ثانية للحفاظ على دقة زمنية فائقة
            syncInterval = setInterval(async () => { await syncWithAPITime(); }, 30000);
        }
        
        async function init() {
            startDisplayTicker();
            startPeriodicSync();
            await syncWithAPITime();   // محاولة أولية للحصول على توقيت الخادم
            // في حال العودة إلى الصفحة بعد تصغير المتصفح، نتأكد من المزامنة
            document.addEventListener("visibilitychange", () => {
                if (!document.hidden && (!hasValidSync)) {
                    syncWithAPITime();
                } else if (!document.hidden && hasValidSync) {
                    // تحديث فوري للتأكد من الدقة عند العودة
                    updateDisplay();
                }
            });
        }
        
        init();
    })();
</script>
</body>
</html>
