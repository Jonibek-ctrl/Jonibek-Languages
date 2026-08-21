# Jonibek-Languages
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>@jonibekk0 | Languages & Translation</title>
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
    <style>
        :root { --bg: #f8f9fa; --bg-card: #ffffff; --text: #333; --text-muted: #666; --accent: #007bff; --border: #e0e0e0; --shadow: 0 4px 12px rgba(0,0,0,0.08); }
        body.dark-mode { --bg: #121212; --bg-card: #1e1e1e; --text: #f5f5f5; --text-muted: #aaa; --accent: #4dabf7; --border: #333; --shadow: 0 4px 12px rgba(0,0,0,0.4); }
        
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif; }
        body { background: var(--bg); color: var(--text); transition: 0.3s; padding-bottom: 60px; }
        a { text-decoration: none; color: var(--accent); }

        /* NAVBAR */
        .navbar { position: sticky; top: 0; background: var(--bg-card); border-bottom: 1px solid var(--border); padding: 15px 20px; display: flex; justify-content: space-between; align-items: center; z-index: 10; box-shadow: var(--shadow); }
        .logo { font-size: 20px; font-weight: 800; color: var(--accent); }
        .nav-right { display: flex; gap: 10px; align-items: center; }
        select, .theme-btn { background: var(--bg); border: 1px solid var(--border); border-radius: 8px; padding: 8px; color: var(--text); cursor: pointer; }

        /* HERO SECTION */
        .hero { position: relative; height: 300px; display: flex; justify-content: center; align-items: center; text-align: center; overflow: hidden; }
        .hero img { position: absolute; top: 0; left: 0; width: 100%; height: 100%; object-fit: cover; opacity: 0.6; }
        .hero-content { position: relative; z-index: 2; padding: 20px; background: rgba(0,0,0,0.5); border-radius: 16px; color: white; max-width: 80%; }
        .hero-content h1 { font-size: 32px; margin-bottom: 10px; }
        .hero-content p { font-size: 16px; margin-bottom: 20px; }

        /* CTA BUTTON */
        .btn-main { background: var(--accent); border: none; color: white; padding: 12px 24px; border-radius: 10px; font-size: 16px; font-weight: bold; cursor: pointer; }
        .btn-main:hover { opacity: 0.9; }

        /* SERVICES SECTION */
        .section { padding: 20px; max-width: 600px; margin: 0 auto; }
        .section-title { text-align: center; font-size: 24px; margin-bottom: 20px; }
        .grid-cards { display: grid; grid-template-columns: 1fr 1fr; gap: 15px; }
        .card { background: var(--bg-card); padding: 20px; border-radius: 16px; box-shadow: var(--shadow); border: 1px solid var(--border); }
        .card h3 { margin-bottom: 10px; font-size: 18px; color: var(--accent); }
        .card p { font-size: 14px; color: var(--text-muted); }

        /* BOOKING SECTION / TABS */
        .tabs { display: flex; margin-bottom: 20px; background: var(--bg-card); border-radius: 12px; padding: 5px; border: 1px solid var(--border); }
        .tab-btn { flex: 1; padding: 12px; border: none; background: transparent; color: var(--text-muted); font-weight: bold; border-radius: 8px; cursor: pointer; }
        .tab-btn.active { background: var(--accent); color: white; }
        
        .form-section { background: var(--bg-card); padding: 20px; border-radius: 16px; box-shadow: var(--shadow); border: 1px solid var(--border); display: none; }
        .form-section.active { display: block; }

        /* CALENDAR & TIME */
        .month-nav { display: flex; justify-content: space-between; align-items: center; margin-bottom: 15px; }
        .days-grid { display: grid; grid-template-columns: repeat(7, 1fr); gap: 5px; margin-bottom: 15px; }
        .day { aspect-ratio: 1; display: flex; justify-content: center; align-items: center; border-radius: 8px; cursor: pointer; border: 1px solid transparent; }
        .day.selected { background: var(--accent); color: white; }
        .day.disabled { opacity: 0.3; cursor: default; }
        .day.empty { visibility: hidden; }
        .time-slot { display: inline-block; padding: 10px 15px; border: 1px solid var(--border); border-radius: 8px; margin: 5px; cursor: pointer; }

        /* COMPANY FORM INPUTS */
        input, select, textarea { width: 100%; padding: 12px; margin-bottom: 15px; border: 1px solid var(--border); border-radius: 8px; background: var(--bg); color: var(--text); font-size: 16px; }
        label { font-weight: bold; font-size: 14px; margin-bottom: 5px; display: block; }

        /* MODAL */
        .modal-overlay { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.5); display: flex; justify-content: center; align-items: center; opacity: 0; visibility: hidden; transition: 0.3s; }
        .modal-overlay.active { opacity: 1; visibility: visible; }
        .modal-box { background: var(--bg-card); padding: 30px; border-radius: 16px; text-align: center; width: 90%; max-width: 400px; }
    </style>
</head>
<body>

    <!-- NAVBAR -->
    <div class="navbar">
        <div class="logo">@jonibekk0</div>
        <div class="nav-right">
            <select id="langSelect">
                <option value="en">EN</option>
                <option value="ru">RU</option>
                <option value="tj">TJ</option>
                <option value="zh">中文</option>
            </select>
            <button class="theme-btn" onclick="toggleDarkMode()">🌙</button>
        </div>
    </div>

    <!-- HERO -->
    <div class="hero">
        <!-- REPLACE THE URL BELOW WITH YOUR OWN IMAGE -->
        <img src="https://images.unsplash.com/photo-1546410531-bb4caa6b424d?q=80&w=1200&auto=format&fit=crop" alt="Languages">
        <div class="hero-content">
            <h1 id="heroTitle">Master Languages. Translate Everything.</h1>
            <p id="heroSub">Online Classes & Professional Translation Services</p>
            <button class="btn-main" onclick="scrollToBooking()" id="ctaText">Get Started</button>
        </div>
    </div>

    <!-- SERVICES -->
    <div class="section">
        <h2 class="section-title" id="servicesTitle">My Services</h2>
        <div class="grid-cards">
            <div class="card">
                <h3 id="svc1Title">Language Classes</h3>
                <p id="svc1Desc">Online courses for English, Russian, and Chinese for students of all levels.</p>
            </div>
            <div class="card">
                <h3 id="svc2Title">Corporate Translation</h3>
                <p id="svc2Desc">Professional document, legal, and video translation. RU, EN, ZH, TJ.</p>
            </div>
        </div>
    </div>

    <!-- BOOKING SECTION -->
    <div class="section">
        <div class="tabs">
            <button class="tab-btn active" onclick="switchTab('student')" id="tabStudent">Student Classes</button>
            <button class="tab-btn" onclick="switchTab('company')" id="tabCompany">Company Quotes</button>
        </div>

        <!-- STUDENT FORM -->
        <div class="form-section active" id="studentForm">
            <h2 id="studentTitle">Book a Lesson</h2>
            <label>Select Course</label>
            <select id="courseSelect">
                <option id="courseEng">English</option>
                <option id="courseRus">Russian</option>
                <option id="courseChn">Chinese</option>
            </select>
            <label id="dateLabel">Date</label>
            <div id="calendar"></div>
            <label id="timeLabel">Time</label>
            <div id="times"></div>
            <button class="btn-main" style="width:100%; margin-top:10px;" onclick="confirmBooking('student')" id="bookBtn">Book Now</button>
        </div>

        <!-- COMPANY FORM -->
        <div class="form-section" id="companyForm">
            <h2 id="companyTitle">Request a Translation Quote</h2>
            <label id="typeLabel">Service Type</label>
            <select id="transType">
                <option id="typeDoc">Document Translation</option>
                <option id="typeInt">Interpreting</option>
                <option id="typeVid">Video/Subtitles</option>
            </select>
            <label id="sourceLabel">Source Language</label>
            <select id="sourceLang">
                <option>English</option>
                <option>Russian</option>
                <option>Chinese</option>
                <option>Tajik</option>
            </select>
            <label id="targetLabel">Target Language</label>
            <select id="targetLang">
                <option>English</option>
                <option>Russian</option>
                <option>Chinese</option>
                <option>Tajik</option>
            </select>
            <label id="projectLabel">Project Details</label>
            <textarea rows="4" placeholder="Describe your project..." id="projectDetails"></textarea>
            <button class="btn-main" style="width:100%;" onclick="confirmBooking('company')" id="quoteBtn">Request Quote</button>
        </div>
    </div>

    <!-- MODAL -->
    <div class="modal-overlay" id="modal">
        <div class="modal-box">
            <h3 id="modalTitle"></h3>
            <p id="modalText"></p>
            <button class="btn-main" onclick="closeModal()" id="closeBtn">OK</button>
        </div>
    </div>

    <script>
        // LANGUAGES
        const translations = {
            en: { heroTitle: "Master Languages. Translate Everything.", heroSub: "Online Classes & Professional Translation Services", ctaText: "Get Started", servicesTitle: "My Services", svc1Title: "Language Classes", svc1Desc: "Online courses for English, Russian, and Chinese for students of all levels.", svc2Title: "Corporate Translation", svc2Desc: "Professional document, legal, and video translation. RU, EN, ZH, TJ.", tabStudent: "Student Classes", tabCompany: "Company Quotes", studentTitle: "Book a Lesson", courseEng: "English", courseRus: "Russian", courseChn: "Chinese", dateLabel: "Date", timeLabel: "Time", bookBtn: "Book Now", companyTitle: "Request a Translation Quote", typeLabel: "Service Type", typeDoc: "Document Translation", typeInt: "Interpreting", typeVid: "Video/Subtitles", sourceLabel: "Source Language", targetLabel: "Target Language", projectLabel: "Project Details", quoteBtn: "Request Quote", modalTitle: "Booking Confirmed!", modalText: "Your request has been sent. I will contact you soon!", closeBtn: "OK", selectDateTime: "Please select date and time!" },
            ru: { heroTitle: "Освойте языки. Переведите всё.", heroSub: "Онлайн-занятия и профессиональные переводческие услуги", ctaText: "Начать", servicesTitle: "Мои услуги", svc1Title: "Языковые курсы", svc1Desc: "Онлайн-курсы по английскому, русскому и китайскому языкам для студентов любого уровня.", svc2Title: "Корпоративный перевод", svc2Desc: "Профессиональный перевод документов, юридических текстов и видео. RU, EN, ZH, TJ.", tabStudent: "Занятия", tabCompany: "Для компаний", studentTitle: "Записаться на урок", courseEng: "Английский", courseRus: "Русский", courseChn: "Китайский", dateLabel: "Дата", timeLabel: "Время", bookBtn: "Записаться", companyTitle: "Запросить стоимость перевода", typeLabel: "Тип услуги", typeDoc: "Перевод документов", typeInt: "Устный перевод", typeVid: "Видео/Субтитры", sourceLabel: "Исходный язык", targetLabel: "Целевой язык", projectLabel: "Детали проекта", quoteBtn: "Запросить расчёт", modalTitle: "Запись подтверждена!", modalText: "Ваш запрос отправлен. Я свяжусь с вами в ближайшее время!", closeBtn: "ОК", selectDateTime: "Пожалуйста, выберите дату и время!" },
            tj: { heroTitle: "Забонҳоро аз худ кунед. Ҳама чизро тарҷума кунед.", heroSub: "Дарсҳои онлайн ва хадамоти касбии тарҷума", ctaText: "Оғоз", servicesTitle: "Хизматҳои ман", svc1Title: "Курсҳои забон", svc1Desc: "Курсҳои онлайн барои забони англисӣ, русӣ ва чинӣ барои донишҷӯёни ҳама сатҳҳо.", svc2Title: "Тарҷумаи корпоративӣ", svc2Desc: "Тарҷумаи касбии ҳуҷҷатҳо, матнҳои ҳуқуқӣ ва видео. RU, EN, ZH, TJ.", tabStudent: "Дарсҳо", tabCompany: "Барои ширкатҳо", studentTitle: "Сабти дарс", courseEng: "Англисӣ", courseRus: "Русӣ", courseChn: "Чинӣ", dateLabel: "Сана", timeLabel: "Вақт", bookBtn: "Сабт кардан", companyTitle: "Дархости тарҷума", typeLabel: "Навъи хизмат", typeDoc: "Тарҷумаи ҳуҷҷат", typeInt: "Тарҷумони шифоҳӣ", typeVid: "Видео/Субтитрҳо", sourceLabel: "Забони аслӣ", targetLabel: "Забони мақсаднок", projectLabel: "Тафсилоти лоиҳа", quoteBtn: "Дархост фиристодан", modalTitle: "Сабт тасдиқ шуд!", modalText: "Дархости шумо фиристода шуд. Ман ба зудӣ бо шумо тамос мегирам!", closeBtn: "ОК", selectDateTime: "Лутфан сана ва вақтро интихоб кунед!" },
            zh: { heroTitle: "掌握语言。翻译万物。", heroSub: "在线课程与专业翻译服务", ctaText: "开始", servicesTitle: "我的服务", svc1Title: "语言课程", svc1Desc: "面向各水平学生的英语、俄语和中文在线课程。", svc2Title: "企业翻译", svc2Desc: "专业的文件、法律和视频翻译。支持俄语、英语、中文、塔吉克语。", tabStudent: "学生课程", tabCompany: "企业询价", studentTitle: "预订课程", courseEng: "英语", courseRus: "俄语", courseChn: "中文", dateLabel: "日期", timeLabel: "时间", bookBtn: "立即预订", companyTitle: "索取翻译报价", typeLabel: "服务类型", typeDoc: "文件翻译", typeInt: "口译", typeVid: "视频/字幕", sourceLabel: "源语言", targetLabel: "目标语言", projectLabel: "项目详情", quoteBtn: "索取报价", modalTitle: "预约成功！", modalText: "您的请求已发送。我会尽快与您联系！", closeBtn: "确定", selectDateTime: "请选择日期和时间！" }
        };

        let currentLang = 'en';
        let selectedDate = null;
        let selectedTime = null;
        let currentMonth = new Date().getMonth();
        let currentYear = new Date().getFullYear();

        // Dark Mode
        function toggleDarkMode() {
            document.body.classList.toggle('dark-mode');
            document.getElementById('themeBtn').innerText = document.body.classList.contains('dark-mode') ? '☀️' : '🌙';
        }

        // Language Switching
        document.getElementById('langSelect').addEventListener('change', (e) => {
            currentLang = e.target.value;
            applyTranslations();
            renderCalendar();
        });

        function applyTranslations() {
            const t = translations[currentLang];
            document.getElementById('heroTitle').innerText = t.heroTitle;
            document.getElementById('heroSub').innerText = t.heroSub;
            document.getElementById('ctaText').innerText = t.ctaText;
            document.getElementById('servicesTitle').innerText = t.servicesTitle;
            document.getElementById('svc1Title').innerText = t.svc1Title;
            document.getElementById('svc1Desc').innerText = t.svc1Desc;
            document.getElementById('svc2Title').innerText = t.svc2Title;
            document.getElementById('svc2Desc').innerText = t.svc2Desc;
            document.getElementById('tabStudent').innerText = t.tabStudent;
            document.getElementById('tabCompany').innerText = t.tabCompany;
            document.getElementById('studentTitle').innerText = t.studentTitle;
            document.getElementById('courseEng').innerText = t.courseEng;
            document.getElementById('courseRus').innerText = t.courseRus;
            document.getElementById('courseChn').innerText = t.courseChn;
            document.getElementById('dateLabel').innerText = t.dateLabel;
            document.getElementById('timeLabel').innerText = t.timeLabel;
            document.getElementById('bookBtn').innerText = t.bookBtn;
            document.getElementById('companyTitle').innerText = t.companyTitle;
            document.getElementById('typeLabel').innerText = t.typeLabel;
            document.getElementById('typeDoc').innerText = t.typeDoc;
            document.getElementById('typeInt').innerText = t.typeInt;
            document.getElementById('typeVid').innerText = t.typeVid;
            document.getElementById('sourceLabel').innerText = t.sourceLabel;
            document.getElementById('targetLabel').innerText = t.targetLabel;
            document.getElementById('projectLabel').innerText = t.projectLabel;
            document.getElementById('quoteBtn').innerText = t.quoteBtn;
            document.getElementById('modalTitle').innerText = t.modalTitle;
            document.getElementById('modalText').innerText = t.modalText;
            document.getElementById('closeBtn').innerText = t.closeBtn;
        }

        // Tabs
        function switchTab(tab) {
            document.querySelectorAll('.tab-btn').forEach(btn => btn.classList.remove('active'));
            document.querySelectorAll('.form-section').forEach(sec => sec.classList.remove('active'));
            if (tab === 'student') {
                document.getElementById('tabStudent').classList.add('active');
                document.getElementById('studentForm').classList.add('active');
            } else {
                document.getElementById('tabCompany').classList.add('active');
                document.getElementById('companyForm').classList.add('active');
            }
        }

        // Calendar Logic
        function renderCalendar() {
            const t = translations[currentLang];
            const cal = document.getElementById('calendar');
            const firstDay = new Date(currentYear, currentMonth, 1).getDay();
            const daysInMonth = new Date(currentYear, currentMonth + 1, 0).getDate();
            const adjustedStart = (firstDay === 0) ? 6 : firstDay - 1;
            
            let html = `<div class="month-nav">
                <button onclick="changeMonth(-1)">‹</button>
                <span>${currentMonth + 1} / ${currentYear}</span>
                <button onclick="changeMonth(1)">›</button>
            </div><div class="days-grid">`;
            
            // Weekdays
            const dayNames = currentLang === 'ru' ? ['Пн','Вт','Ср','Чт','Пт','Сб','Вс'] : currentLang === 'tj' ? ['Дш','Сш','Чш','Пш','Ҷм','Шб','Як'] : currentLang === 'zh' ? ['一','二','三','四','五','六','日'] : ['Mo','Tu','We','Th','Fr','Sa','Su'];
            dayNames.forEach(day => html += `<div style="text-align:center;font-weight:bold;font-size:12px;">${day}</div>`);

            // Empty cells
            for (let i = 0; i < adjustedStart; i++) html += `<div class="day empty"></div>`;

            // Days
            const today = new Date();
            for (let i = 1; i <= daysInMonth; i++) {
                let isPast = (i < today.getDate() && currentMonth === today.getMonth() && currentYear === today.getFullYear());
                let selectable = isPast ? 'disabled' : '';
                html += `<div class="day ${selectable}" onclick="selectDate(this, '${currentYear}-${currentMonth + 1}-${i}')">${i}</div>`;
            }
            html += `</div>`;

            // Time slots
            html += `<div id="times">`;
            ['09:00','12:00','15:00','18:00'].forEach(time => {
                html += `<div class="time-slot" onclick="selectTime(this, '${time}')">${time}</div>`;
            });
            html += `</div>`;

            cal.innerHTML = html;
        }

        function changeMonth(offset) {
            currentMonth += offset;
            if (currentMonth < 0) { currentMonth = 11; currentYear--; }
            if (currentMonth > 11) { currentMonth = 0; currentYear++; }
            renderCalendar();
        }

        function selectDate(el, date) {
            document.querySelectorAll('.day').forEach(d => d.classList.remove('selected'));
            el.classList.add('selected');
            selectedDate = date;
        }

        function selectTime(el, time) {
            document.querySelectorAll('.time-slot').forEach(t => t.classList.remove('selected'));
            el.classList.add('selected');
            selectedTime = time;
        }

        // Confirm Booking
        function confirmBooking(type) {
            const t = translations[currentLang];

            if (type === 'student') {
                if (!selectedDate || !selectedTime) {
                    alert(t.selectDa
