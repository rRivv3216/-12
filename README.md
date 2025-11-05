# c1
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>منصة الكيمياء التفاعلية - الاختبارات والمحاكاة</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        :root {
            --primary: #4a6baf;
            --secondary: #6d28d9;
            --accent: #06d6a0;
            --light: #f8fafc;
            --dark: #1e293b;
            --success: #10b981;
            --warning: #f59e0b;
            --danger: #ef4444;
            --card-bg: rgba(255, 255, 255, 0.95);
            --transition: all 0.3s ease;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
            min-height: 100vh;
            color: var(--dark);
        }

        .app-container {
            display: flex;
            min-height: 100vh;
        }

        /* الشريط الجانبي */
        .sidebar {
            width: 280px;
            background: linear-gradient(180deg, var(--primary), var(--secondary));
            color: white;
            padding: 20px 0;
            box-shadow: 5px 0 15px rgba(0, 0, 0, 0.1);
            z-index: 100;
        }

        .logo {
            text-align: center;
            padding: 20px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.2);
            margin-bottom: 20px;
        }

        .logo h1 {
            font-size: 1.5em;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .logo i {
            margin-left: 10px;
            font-size: 1.8em;
        }

        .nav-menu {
            list-style: none;
            padding: 0 15px;
        }

        .nav-item {
            margin-bottom: 8px;
        }

        .nav-link {
            display: flex;
            align-items: center;
            padding: 15px 20px;
            color: white;
            text-decoration: none;
            border-radius: 10px;
            transition: var(--transition);
        }

        .nav-link:hover, .nav-link.active {
            background: rgba(255, 255, 255, 0.2);
            transform: translateX(5px);
        }

        .nav-link i {
            margin-left: 15px;
            font-size: 1.2em;
        }

        .user-section {
            padding: 20px;
            border-top: 1px solid rgba(255, 255, 255, 0.2);
            margin-top: 20px;
        }

        .user-info {
            display: flex;
            align-items: center;
        }

        .user-avatar {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: var(--accent);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5em;
            margin-left: 15px;
        }

        /* المحتوى الرئيسي */
        .main-content {
            flex: 1;
            padding: 20px;
            overflow-y: auto;
        }

        .header {
            background: var(--card-bg);
            border-radius: 15px;
            padding: 20px 30px;
            margin-bottom: 25px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .header h2 {
            color: var(--primary);
            display: flex;
            align-items: center;
        }

        .header h2 i {
            margin-left: 15px;
        }

        .user-actions {
            display: flex;
            gap: 15px;
        }

        /* البطاقات */
        .cards-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 25px;
            margin-bottom: 30px;
        }

        .card {
            background: var(--card-bg);
            border-radius: 15px;
            padding: 25px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            transition: var(--transition);
            cursor: pointer;
        }

        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
        }

        .card-header {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
        }

        .card-icon {
            width: 60px;
            height: 60px;
            border-radius: 12px;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.8em;
            color: white;
            margin-left: 15px;
        }

        .card h3 {
            color: var(--dark);
            font-size: 1.3em;
        }

        .card p {
            color: #666;
            line-height: 1.6;
            margin-bottom: 20px;
        }

        /* الأزرار */
        .btn {
            padding: 12px 25px;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            font-size: 1em;
            font-weight: bold;
            transition: var(--transition);
            display: inline-flex;
            align-items: center;
            justify-content: center;
        }

        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(74, 107, 175, 0.4);
        }

        .btn i {
            margin-left: 8px;
        }

        .btn-success {
            background: linear-gradient(135deg, var(--success), #059669);
        }

        .btn-warning {
            background: linear-gradient(135deg, var(--warning), #d97706);
        }

        .btn-danger {
            background: linear-gradient(135deg, var(--danger), #dc2626);
        }

        .btn-outline {
            background: transparent;
            border: 2px solid var(--primary);
            color: var(--primary);
        }

        /* الشاشات */
        .screen {
            display: none;
        }

        .screen.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* شاشة الترحيب */
        .welcome-screen {
            text-align: center;
            padding: 40px 20px;
        }

        .welcome-icon {
            font-size: 5em;
            color: var(--primary);
            margin-bottom: 20px;
        }

        .welcome-screen h1 {
            color: var(--dark);
            margin-bottom: 15px;
            font-size: 2.5em;
        }

        .welcome-screen p {
            color: #666;
            font-size: 1.2em;
            max-width: 600px;
            margin: 0 auto 30px;
            line-height: 1.6;
        }

        /* شاشة الإعدادات */
        .settings-container {
            background: var(--card-bg);
            border-radius: 15px;
            padding: 30px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }

        .settings-group {
            margin-bottom: 30px;
        }

        .settings-group h3 {
            color: var(--primary);
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid #f1f5f9;
            display: flex;
            align-items: center;
        }

        .settings-group h3 i {
            margin-left: 10px;
        }

        .setting-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 0;
            border-bottom: 1px solid #f1f5f9;
        }

        .setting-info h4 {
            color: var(--dark);
            margin-bottom: 5px;
        }

        .setting-info p {
            color: #666;
            font-size: 0.9em;
        }

        /* عناصر الإعدادات */
        .toggle-switch {
            position: relative;
            display: inline-block;
            width: 60px;
            height: 30px;
        }

        .toggle-switch input {
            opacity: 0;
            width: 0;
            height: 0;
        }

        .slider {
            position: absolute;
            cursor: pointer;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-color: #ccc;
            transition: .4s;
            border-radius: 34px;
        }

        .slider:before {
            position: absolute;
            content: "";
            height: 22px;
            width: 22px;
            left: 4px;
            bottom: 4px;
            background-color: white;
            transition: .4s;
            border-radius: 50%;
        }

        input:checked + .slider {
            background-color: var(--success);
        }

        input:checked + .slider:before {
            transform: translateX(30px);
        }

        select, input[type="number"] {
            padding: 10px 15px;
            border: 2px solid #e1e5f1;
            border-radius: 8px;
            font-size: 1em;
            background: white;
        }

        select:focus, input[type="number"]:focus {
            border-color: var(--primary);
            outline: none;
        }

        /* العناصر الكيميائية */
        .chemistry-elements {
            position: fixed;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            pointer-events: none;
            z-index: -1;
        }

        .element {
            position: absolute;
            font-size: 1.5em;
            opacity: 0.03;
            animation: floatElement 20s infinite linear;
        }

        @keyframes floatElement {
            0% { transform: translateY(0) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(180deg); }
            100% { transform: translateY(0) rotate(360deg); }
        }

        .element:nth-child(1) { top: 10%; left: 5%; animation-duration: 25s; }
        .element:nth-child(2) { top: 20%; right: 10%; animation-duration: 30s; }
        .element:nth-child(3) { bottom: 15%; left: 15%; animation-duration: 20s; }
        .element:nth-child(4) { bottom: 25%; right: 5%; animation-duration: 35s; }
        .element:nth-child(5) { top: 50%; left: 20%; animation-duration: 28s; }
        .element:nth-child(6) { top: 60%; right: 20%; animation-duration: 32s; }

        /* التكيف مع الشاشات الصغيرة */
        @media (max-width: 768px) {
            .app-container {
                flex-direction: column;
            }
            
            .sidebar {
                width: 100%;
                height: auto;
            }
            
            .nav-menu {
                display: flex;
                overflow-x: auto;
                padding-bottom: 10px;
            }
            
            .nav-item {
                flex-shrink: 0;
                margin-bottom: 0;
                margin-left: 10px;
            }
            
            .cards-container {
                grid-template-columns: 1fr;
            }
            
            .header {
                flex-direction: column;
                gap: 15px;
                text-align: center;
            }
            
            .user-actions {
                justify-content: center;
            }
        }
    </style>
</head>
<body>
    <!-- العناصر الكيميائية العائمة -->
    <div class="chemistry-elements">
        <div class="element">H₂O</div>
        <div class="element">CO₂</div>
        <div class="element">NaCl</div>
        <div class="element">CH₄</div>
        <div class="element">C₆H₁₂O₆</div>
        <div class="element">H₂SO₄</div>
    </div>

    <div class="app-container">
        <!-- الشريط الجانبي -->
        <div class="sidebar">
            <div class="logo">
                <h1><i class="fas fa-atom"></i> كيمياء</h1>
            </div>
            
            <ul class="nav-menu">
                <li class="nav-item">
                    <a href="#" class="nav-link active" data-screen="welcome">
                        <i class="fas fa-home"></i>
                        <span>الرئيسية</span>
                    </a>
                </li>
                <li class="nav-item">
                    <a href="#" class="nav-link" data-screen="quiz">
                        <i class="fas fa-file-alt"></i>
                        <span>الاختبارات</span>
                    </a>
                </li>
                <li class="nav-item">
                    <a href="#" class="nav-link" data-screen="simulation">
                        <i class="fas fa-vial"></i>
                        <span>المحاكاة</span>
                    </a>
                </li>
                <li class="nav-item">
                    <a href="#" class="nav-link" data-screen="progress">
                        <i class="fas fa-chart-line"></i>
                        <span>التقدم</span>
                    </a>
                </li>
                <li class="nav-item">
                    <a href="#" class="nav-link" data-screen="leaderboard">
                        <i class="fas fa-trophy"></i>
                        <span>المتصدرين</span>
                    </a>
                </li>
                <li class="nav-item">
                    <a href="#" class="nav-link" data-screen="settings">
                        <i class="fas fa-cog"></i>
                        <span>الإعدادات</span>
                    </a>
                </li>
            </ul>
            
            <div class="user-section">
                <div class="user-info">
                    <div class="user-avatar">
                        <i class="fas fa-user"></i>
                    </div>
                    <div>
                        <h4>طالب كيمياء</h4>
                        <p>المستوى: مبتدئ</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- المحتوى الرئيسي -->
        <div class="main-content">
            <!-- شاشة الترحيب -->
            <div class="screen active" id="welcome">
                <div class="header">
                    <h2><i class="fas fa-home"></i> الرئيسية</h2>
                    <div class="user-actions">
                        <button class="btn btn-outline">
                            <i class="fas fa-bell"></i> الإشعارات
                        </button>
                        <button class="btn">
                            <i class="fas fa-user"></i> الملف الشخصي
                        </button>
                    </div>
                </div>
                
                <div class="welcome-screen">
                    <div class="welcome-icon">
                        <i class="fas fa-atom"></i>
                    </div>
                    <h1>مرحباً بك في منصة الكيمياء التفاعلية</h1>
                    <p>منصة شاملة لتعلم الكيمياء من خلال الاختبارات التفاعلية، المحاكاة، والتجارب الافتراضية</p>
                    
                    <div class="cards-container">
                        <div class="card" data-screen="quiz">
                            <div class="card-header">
                                <div class="card-icon">
                                    <i class="fas fa-file-alt"></i>
                                </div>
                                <h3>الاختبارات التفاعلية</h3>
                            </div>
                            <p>اختبر معرفتك في الكيمياء من خلال اختبارات تفاعلية مع تصحيح فوري وتحليل مفصل للأداء</p>
                            <button class="btn">ابدأ الاختبار</button>
                        </div>
                        
                        <div class="card" data-screen="simulation">
                            <div class="card-header">
                                <div class="card-icon">
                                    <i class="fas fa-vial"></i>
                                </div>
                                <h3>المحاكاة والتجارب</h3>
                            </div>
                            <p>قم بتجربة التفاعلات الكيميائية افتراضياً في مختبر آمن مع شرح مفصل للنتائج</p>
                            <button class="btn btn-success">ابدأ المحاكاة</button>
                        </div>
                        
                        <div class="card" data-screen="progress">
                            <div class="card-header">
                                <div class="card-icon">
                                    <i class="fas fa-chart-line"></i>
                                </div>
                                <h3>تتبع التقدم</h3>
                            </div>
                            <p>راجع إحصائيات أدائك، تتبع تقدمك التعليمي، واحصل على توصيات مخصصة للتحسين</p>
                            <button class="btn btn-warning">عرض التقارير</button>
                        </div>
                        
                        <div class="card" data-screen="leaderboard">
                            <div class="card-header">
                                <div class="card-icon">
                                    <i class="fas fa-trophy"></i>
                                </div>
                                <h3>لوحة المتصدرين</h3>
                            </div>
                            <p>تنافس مع زملائك، احصل على نقاط، وارتقِ في لوحة المتصدرين لتصير الأفضل</p>
                            <button class="btn btn-danger">عرض المتصدرين</button>
                        </div>
                    </div>
                </div>
            </div>

            <!-- شاشة الإعدادات -->
            <div class="screen" id="settings">
                <div class="header">
                    <h2><i class="fas fa-cog"></i> الإعدادات</h2>
                </div>
                
                <div class="settings-container">
                    <div class="settings-group">
                        <h3><i class="fas fa-user-cog"></i> إعدادات الحساب</h3>
                        
                        <div class="setting-item">
                            <div class="setting-info">
                                <h4>الاسم</h4>
                                <p>اسم المستخدم المعروض في المنصة</p>
                            </div>
                            <input type="text" value="طالب كيمياء" class="setting-control">
                        </div>
                        
                        <div class="setting-item">
                            <div class="setting-info">
                                <h4>البريد الإلكتروني</h4>
                                <p>للاستلام الإشعارات والتحديثات</p>
                            </div>
                            <input type="email" value="student@chemistry.com" class="setting-control">
                        </div>
                        
                        <div class="setting-item">
                            <div class="setting-info">
                                <h4>كلمة المرور</h4>
                                <p>تغيير كلمة المرور الحالية</p>
                            </div>
                            <button class="btn btn-outline">تغيير كلمة المرور</button>
                        </div>
                    </div>
                    
                    <div class="settings-group">
                        <h3><i class="fas fa-palette"></i> الإعدادات العامة</h3>
                        
                        <div class="setting-item">
                            <div class="setting-info">
                                <h4>الوضع الليلي</h4>
                                <p>تفعيل الوضع المظلم للراحة البصرية</p>
                            </div>
                            <label class="toggle-switch">
                                <input type="checkbox">
                                <span class="slider"></span>
                            </label>
                        </div>
                        
                        <div class="setting-item">
                            <div class="setting-info">
                                <h4>الإشعارات</h4>
                                <p>تلقي إشعارات حول الاختبارات والتحديثات</p>
                            </div>
                            <label class="toggle-switch">
                                <input type="checkbox" checked>
                                <span class="slider"></span>
                            </label>
                        </div>
                        
                        <div class="setting-item">
                            <div class="setting-info">
                                <h4>صعوبة الاختبارات</h4>
                                <p>اختر مستوى الصعوبة الافتراضي للاختبارات</p>
                            </div>
                            <select class="setting-control">
                                <option>سهل</option>
                                <option selected>متوسط</option>
                                <option>صعب</option>
                            </select>
                        </div>
                        
                        <div class="setting-item">
                            <div class="setting-info">
                                <h4>عدد الأسئلة</h4>
                                <p>عدد الأسئلة الافتراضي في كل اختبار</p>
                            </div>
                            <input type="number" value="20" min="5" max="50" class="setting-control">
                        </div>
                    </div>
                    
                    <div class="settings-group">
                        <h3><i class="fas fa-language"></i> إعدادات اللغة</h3>
                        
                        <div class="setting-item">
                            <div class="setting-info">
                                <h4>لغة الواجهة</h4>
                                <p>اختر اللغة المعروضة في المنصة</p>
                            </div>
                            <select class="setting-control">
                                <option selected>العربية</option>
                                <option>English</option>
                                <option>Français</option>
                            </select>
                        </div>
                        
                        <div class="setting-item">
                            <div class="setting-info">
                                <h4>لغة المصطلحات العلمية</h4>
                                <p>اختر لغة المصطلحات الكيميائية</p>
                            </div>
                            <select class="setting-control">
                                <option selected>العربية</option>
                                <option>English</option>
                                <option>مختلط</option>
                            </select>
                        </div>
                    </div>
                    
                    <div class="settings-group">
                        <h3><i class="fas fa-download"></i> البيانات والخصوصية</h3>
                        
                        <div class="setting-item">
                            <div class="setting-info">
                                <h4>حفظ النتائج تلقائياً</h4>
                                <p>حفظ نتائج الاختبارات تلقائياً على الجهاز</p>
                            </div>
                            <label class="toggle-switch">
                                <input type="checkbox" checked>
                                <span class="slider"></span>
                            </label>
                        </div>
                        
                        <div class="setting-item">
                            <div class="setting-info">
                                <h4>تصدير البيانات</h4>
                                <p>تحميل جميع نتائجك وتقاريرك</p>
                            </div>
                            <button class="btn btn-outline">تصدير البيانات</button>
                        </div>
                        
                        <div class="setting-item">
                            <div class="setting-info">
                                <h4>مسح البيانات</h4>
                                <p>حذف جميع البيانات المحفوظة على الجهاز</p>
                            </div>
                            <button class="btn btn-danger">مسح البيانات</button>
                        </div>
                    </div>
                </div>
            </div>

            <!-- شاشات أخرى (سيتم إضافتها لاحقاً) -->
            <div class="screen" id="quiz">
                <div class="header">
                    <h2><i class="fas fa-file-alt"></i> الاختبارات</h2>
                </div>
                <div class="welcome-screen">
                    <h1>شاشة الاختبارات</h1>
                    <p>هنا يمكنك اختيار والبدء في الاختبارات التفاعلية</p>
                    <button class="btn" onclick="showScreen('welcome')">العودة للرئيسية</button>
                </div>
            </div>
            
            <div class="screen" id="simulation">
                <div class="header">
                    <h2><i class="fas fa-vial"></i> المحاكاة</h2>
                </div>
                <div class="welcome-screen">
                    <h1>شاشة المحاكاة</h1>
                    <p>هنا يمكنك تجربة التفاعلات الكيميائية افتراضياً</p>
                    <button class="btn" onclick="showScreen('welcome')">العودة للرئيسية</button>
                </div>
            </div>
            
            <div class="screen" id="progress">
                <div class="header">
                    <h2><i class="fas fa-chart-line"></i> التقدم</h2>
                </div>
                <div class="welcome-screen">
                    <h1>شاشة التقدم</h1>
                    <p>هنا يمكنك رؤية إحصائيات أدائك وتقدمك</p>
                    <button class="btn" onclick="showScreen('welcome')">العودة للرئيسية</button>
                </div>
            </div>
            
            <div class="screen" id="leaderboard">
                <div class="header">
                    <h2><i class="fas fa-trophy"></i> المتصدرين</h2>
                </div>
                <div class="welcome-screen">
                    <h1>شاشة المتصدرين</h1>
                    <p>هنا يمكنك رؤية ترتيبك بين المستخدمين الآخرين</p>
                    <button class="btn" onclick="showScreen('welcome')">العودة للرئيسية</button>
                </div>
            </div>
        </div>
    </div>

    <script>
        // إدارة التنقل بين الشاشات
        function showScreen(screenId) {
            // إخفاء جميع الشاشات
            document.querySelectorAll('.screen').forEach(screen => {
                screen.classList.remove('active');
            });
            
            // إزالة النشاط من جميع روابط التنقل
            document.querySelectorAll('.nav-link').forEach(link => {
                link.classList.remove('active');
            });
            
            // إظهار الشاشة المطلوبة
            document.getElementById(screenId).classList.add('active');
            
            // تفعيل رابط التنقل المناسب
            document.querySelector(`.nav-link[data-screen="${screenId}"]`).classList.add('active');
        }

        // إضافة مستمعي الأحداث للروابط
        document.querySelectorAll('.nav-link').forEach(link => {
            link.addEventListener('click', function(e) {
                e.preventDefault();
                const screenId = this.getAttribute('data-screen');
                showScreen(screenId);
            });
        });

        // إضافة مستمعي الأحداث للبطاقات
        document.querySelectorAll('.card').forEach(card => {
            card.addEventListener('click', function() {
                const screenId = this.getAttribute('data-screen');
                showScreen(screenId);
            });
        });

        // تهيئة الإعدادات
        function initializeSettings() {
            // تحميل الإعدادات من localStorage إن وجدت
            const savedSettings = localStorage.getItem('chemistryAppSettings');
            if (savedSettings) {
                const settings = JSON.parse(savedSettings);
                // تطبيق الإعدادات المحفوظة
                // يمكن إضافة المزيد من التعليمات هنا
            }
        }

        // حفظ الإعدادات
        function saveSettings() {
            const settings = {
                username: document.querySelector('input[type="text"]').value,
                email: document.querySelector('input[type="email"]').value,
                darkMode: document.querySelector('input[type="checkbox"]').checked,
                notifications: document.querySelectorAll('input[type="checkbox"]')[1].checked,
                difficulty: document.querySelector('select').value,
                questionCount: document.querySelector('input[type="number"]').value,
                language: document.querySelectorAll('select')[1].value,
                termsLanguage: document.querySelectorAll('select')[2].value,
                autoSave: document.querySelectorAll('input[type="checkbox"]')[2].checked
            };
            
            localStorage.setItem('chemistryAppSettings', JSON.stringify(settings));
            alert('تم حفظ الإعدادات بنجاح!');
        }

        // إضافة مستمعي الأحداث لحفظ الإعدادات
        document.querySelectorAll('.setting-control').forEach(control => {
            control.addEventListener('change', saveSettings);
        });

        document.querySelectorAll('input[type="checkbox"]').forEach(checkbox => {
            checkbox.addEventListener('change', saveSettings);
        });

        // تهيئة التطبيق عند التحميل
        document.addEventListener('DOMContentLoaded', function() {
            initializeSettings();
            
            // إضافة تأثيرات للبطاقات
            document.querySelectorAll('.card').forEach((card, index) => {
                card.style.animationDelay = `${index * 0.1}s`;
            });
        });

        // وظائف إضافية للواجهة
        function exportData() {
            alert('سيتم تصدير بياناتك قريباً...');
            // هنا يمكن إضافة كود لتصدير البيانات
        }

        function clearData() {
            if (confirm('هل أنت متأكد من رغبتك في مسح جميع البيانات؟ لا يمكن التراجع عن هذا الإجراء.')) {
                localStorage.removeItem('chemistryAppSettings');
                alert('تم مسح البيانات بنجاح!');
            }
        }

        // إضافة مستمعي الأحداث للأزرار
        document.querySelector('.btn-danger').addEventListener('click', clearData);
        document.querySelector('.btn-outline').addEventListener('click', exportData);
    </script>
</body>
</html>
