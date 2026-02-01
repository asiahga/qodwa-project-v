here<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>مبادرة قدوة ملهمة – متوسطة الأولى بتيماء</title>

<link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;700;900&family=El+Messiri:wght@600;700&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

<style>
* { box-sizing: border-box; margin: 0; padding: 0; }
body { font-family: 'Tajawal', sans-serif; background: #f4f6f5; color: #333; }

/* ===== نظام تسجيل الدخول ===== */
#loginOverlay {
    position: fixed; inset: 0;
    background: linear-gradient(135deg, #0b5d4b, #0f7661);
    display: flex; align-items: center; justify-content: center;
    z-index: 10000;
}
.login-box {
    background: white; padding: 40px; border-radius: 20px;
    width: 90%; max-width: 400px; text-align: center;
    box-shadow: 0 10px 30px rgba(0,0,0,0.2);
}
.login-box h2 { color: #0b5d4b; margin-bottom: 25px; }
.login-box input {
    width: 100%; padding: 12px; margin-bottom: 15px;
    border: 2px solid #ddd; border-radius: 8px;
    font-size: 16px; transition: border 0.3s;
}
.login-box input:focus { border-color: #0b5d4b; outline: none; }
.login-btn {
    background: #d4af37; color: #000; font-weight: bold;
    padding: 12px 30px; border: none; border-radius: 8px;
    cursor: pointer; width: 100%; font-size: 16px;
}
.login-btn:hover { background: #c19b2d; }

/* ===== الترحيب ===== */
#welcomeOverlay {
    position: fixed; inset: 0;
    background: linear-gradient(135deg, #0b5d4b, #0f7661);
    display: flex; align-items: center; justify-content: center;
    z-index: 9999;
}
.welcome-box {
    background: white; padding: 50px; border-radius: 22px;
    text-align: center; max-width: 520px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.2);
}
.welcome-box h1 { color: #0b5d4b; font-size: 34px; margin-bottom: 20px; }
.welcome-box button {
    margin-top: 20px; padding: 12px 35px;
    background: #d4af37; border: none; border-radius: 10px;
    font-weight: bold; font-size: 16px; cursor: pointer;
}

/* ===== الهيدر ===== */
header {
    background: #0b5d4b; color: white;
    padding: 15px 20px;
    display: flex; justify-content: space-between;
    align-items: center; flex-wrap: wrap;
}
.header-right { font-weight: bold; font-size: 18px; }
.header-center { font-size: 22px; font-weight: bold; text-align: center; flex-grow: 1; }
.header-left { display: flex; align-items: center; gap: 15px; }
.header-left img { width: 55px; height: 55px; border-radius: 50%; }
.admin-controls { display: flex; gap: 10px; align-items: center; }
.admin-btn {
    background: #d4af37; color: #000; padding: 8px 15px;
    border-radius: 6px; text-decoration: none; font-weight: bold;
}

/* ===== التخطيط ===== */
.main { display: flex; min-height: calc(100vh - 120px); }
.sidebar {
    width: 240px; background: white; padding: 15px;
    border-left: 6px solid #d4af37; min-height: 100%;
}
.sidebar button {
    width: 100%; margin-bottom: 10px; padding: 12px;
    border: none; border-radius: 10px;
    background: #0b5d4b; color: white; font-weight: bold;
    cursor: pointer; text-align: right; font-size: 16px;
    display: flex; align-items: center; gap: 10px;
}
.sidebar button.home { background: #d4af37; color: black; }
.sidebar button:hover { opacity: 0.9; transform: translateX(-5px); }

.container { flex: 1; padding: 20px; }
.section { display: none; }
.section.active { display: block; }

.section-title {
    color: #0b5d4b; border-right: 5px solid #d4af37;
    padding-right: 15px; margin-bottom: 25px;
    font-size: 24px; display: flex; justify-content: space-between;
    align-items: center;
}
.action-buttons { display: flex; gap: 10px; }
.btn { padding: 8px 15px; border-radius: 6px; border: none; cursor: pointer; }
.btn-primary { background: #0b5d4b; color: white; }
.btn-warning { background: #d4af37; color: black; }
.btn-danger { background: #c62828; color: white; }

/* ===== القاعات ===== */
.rooms-container {
    display: grid; grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    gap: 20px; margin-top: 20px;
}
.room-card {
    background: white; padding: 20px; border-radius: 15px;
    box-shadow: 0 4px 10px rgba(0,0,0,.08);
    text-align: center; transition: transform 0.3s;
}
.room-card:hover { transform: translateY(-5px); }
.room-name { font-size: 18px; font-weight: bold; margin-bottom: 10px; }
.status { font-weight: bold; padding: 8px; border-radius: 8px; margin-top: 10px; }
.status.empty { background: #ffebee; color: #c62828; } /* أحمر - فارغة */
.status.occupied { background: #e8f5e9; color: #2e7d32; } /* أخضر - مشغولة */
.status.closed { background: #fff3e0; color: #ef6c00; } /* أصفر - مقفلة */

/* ===== بيانات الموظفات ===== */
.staff-container {
    display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 20px; margin-top: 20px;
}
.staff-card {
    background: white; padding: 20px; border-radius: 12px;
    box-shadow: 0 4px 8px rgba(0,0,0,.1); position: relative;
}
.staff-actions {
    position: absolute; top: 15px; left: 15px;
    display: flex; gap: 8px;
}
.staff-name { font-size: 20px; color: #0b5d4b; margin-bottom: 10px; }
.staff-info { margin-bottom: 8px; }
.password-field {
    background: #f5f5f5; padding: 8px; border-radius: 6px;
    font-family: monospace; display: flex; justify-content: space-between;
}
.password-field span { color: #666; }

/* ===== النماذج ===== */
.form-group { margin-bottom: 20px; }
.form-group label {
    display: block; margin-bottom: 8px; font-weight: bold;
    color: #0b5d4b;
}
.form-control {
    width: 100%; padding: 12px; border: 2px solid #ddd;
    border-radius: 8px; font-size: 16px; transition: border 0.3s;
}
.form-control:focus { border-color: #0b5d4b; outline: none; }
textarea.form-control { min-height: 120px; resize: vertical; }

/* ===== البطاقات الأسبوعية ===== */
.weekly-cards-container {
    display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 20px; margin-top: 20px;
}
.weekly-card {
    background: linear-gradient(135deg, #0b5d4b, #1fa37a);
    color: white; padding: 25px; border-radius: 15px;
    border: 5px solid #d4af37; text-align: center;
}

/* ===== الشهادات ===== */
.certificate {
    background: linear-gradient(135deg, #0b5d4b, #1fa37a);
    border: 10px solid #d4af37;
    color: white; padding: 35px; border-radius: 22px;
    text-align: center; max-width: 800px; margin: 20px auto;
    position: relative;
}
.certificate h3 { font-size: 28px; margin-bottom: 15px; }
.certificate p { font-size: 18px; line-height: 1.9; }
.cert-actions {
    position: absolute; top: 15px; left: 15px;
    display: flex; gap: 10px;
}

/* ===== الباركود ===== */
.barcode-section { text-align: center; margin: 30px 0; }
.barcode-container {
    background: white; padding: 20px; border-radius: 12px;
    display: inline-block; margin: 20px 0;
}
#barcodeCanvas { border: 2px solid #ddd; }
.status-indicator {
    width: 50px; height: 50px; border-radius: 50%;
    margin: 20px auto; transition: background 0.5s;
}
.status-red { background: #c62828; }
.status-green { background: #2e7d32; }

/* ===== توقيع الصفحة الرئيسية ===== */
.home-credit {
    position: fixed; bottom: 10px; left: 15px;
    font-size: 14px; color: #555; opacity: 0.8;
}

/* ===== الصفحة الرئيسية ===== */
#weeklyDisplay { margin-top: 30px; }
.weekly-card-home {
    background: linear-gradient(135deg, #0b5d4b, #1fa37a);
    color: white; padding: 20px; border-radius: 12px;
    margin-bottom: 15px; border-left: 8px solid #d4af37;
}

/* ===== التنبيهات ===== */
.alert-box {
    background: #fff3cd; border: 1px solid #ffeaa7;
    color: #856404; padding: 15px; border-radius: 8px;
    margin: 15px 0; display: flex; justify-content: space-between;
    align-items: center;
}

/* ===== الفوتر ===== */
footer {
    text-align: center; padding: 20px; color: #666;
    background: white; border-top: 2px solid #0b5d4b;
    margin-top: 30px;
}

/* ===== Responsive ===== */
@media (max-width: 768px) {
    .main { flex-direction: column; }
    .sidebar { width: 100%; border-left: none; border-top: 6px solid #d4af37; }
    .sidebar button { margin-bottom: 8px; }
    header { flex-direction: column; text-align: center; gap: 10px; }
    .header-center { order: -1; }
    .rooms-container, .staff-container { grid-template-columns: 1fr; }
}
</style>
</head>

<body>

<!-- شاشة تسجيل الدخول للمسؤول -->
<div id="loginOverlay">
    <div class="login-box">
        <h2>تسجيل دخول المسؤول</h2>
        <input type="text" id="adminUsername" placeholder="اسم المستخدم">
        <input type="password" id="adminPassword" placeholder="كلمة المرور">
        <button class="login-btn" onclick="loginAdmin()">دخول</button>
        <p style="margin-top: 15px; color: #666; font-size: 14px;">
            * الدخول متاح فقط للإدارة المدرسية
        </p>
    </div>
</div>

<!-- شاشة الترحيب -->
<div id="welcomeOverlay" style="display: none;">
    <div class="welcome-box">
        <h1>أهلًا بكم بمبادرة قدوة ملهمة</h1>
        <p>نظام إدارة القاعات والشهادات والبطاقات التقديرية</p>
        <button onclick="closeWelcome()">الدخول للموقع</button>
    </div>
</div>

<!-- الهيدر -->
<header style="display: none;">
    <div class="header-right">المدرسة المتوسطة الأولى بتيماء</div>
    <div class="header-center">مبادرة قدوة ملهمة</div>
    <div class="header-left">
        <img src="logo.png" alt="شعار المدرسة">
        <div class="admin-controls" id="adminControls" style="display: none;">
            <button class="admin-btn" onclick="showAdminPanel()">
                <i class="fas fa-cog"></i> لوحة التحكم
            </button>
            <button class="admin-btn" onclick="logout()">
                <i class="fas fa-sign-out-alt"></i> خروج
            </button>
        </div>
    </div>
</header>

<div class="main" style="display: none;">
    <!-- القائمة الجانبية -->
    <div class="sidebar">
        <button class="home" onclick="showSection('home')">
            <i class="fas fa-home"></i> الرئيسية
        </button>
        <button onclick="showSection('rooms')">
            <i class="fas fa-door-open"></i> القاعات الدراسية
        </button>
        <button onclick="showSection('staff')">
            <i class="fas fa-users"></i> بيانات الموظفات
        </button>
        <button onclick="showSection('thanks')">
            <i class="fas fa-heart"></i> رسائل الشكر
        </button>
        <button onclick="showSection('weekly')">
            <i class="fas fa-star"></i> البطاقات الأسبوعية
        </button>
        <button onclick="showSection('certificates')">
            <i class="fas fa-certificate"></i> شهادات الشكر
        </button>
        <button onclick="showSection('barcode')">
            <i class="fas fa-qrcode"></i> باركود الحصص
        </button>
        <button onclick="showSection('alerts')">
            <i class="fas fa-bell"></i> تنبيهات التأخير
        </button>
        <button onclick="showSection('stories')">
            <i class="fas fa-book-open"></i> قصص ملهمة
        </button>
    </div>

    <!-- المحتوى الرئيسي -->
    <div class="container">
        <!-- الصفحة الرئيسية -->
        <div class="section active" id="home">
            <h2 class="section-title">لوحة الإعلانات والتميز</h2>
            <div style="background: white; padding: 25px; border-radius: 15px; box-shadow: 0 4px 10px rgba(0,0,0,.05);">
                <h3 style="color: #0b5d4b; margin-bottom: 15px;">إعلانات اليوم</h3>
                <p style="line-height: 1.8;">
                    نرحب بجميع منسوبات المدرسة في مبادرة "قدوة ملهمة". نهدف من خلال هذا النظام إلى تعزيز روح التميز والتقدير وتسهيل إدارة القاعات الدراسية.
                </p>
                
                <div id="weeklyDisplay">
                    <h3 style="color: #0b5d4b; margin: 25px 0 15px;">نجوم الأسبوع 🎖️</h3>
                    <div id="weeklyCardsHome"></div>
                </div>
            </div>
            <div class="home-credit">تصميم وتطوير: وفاء السلامة</div>
        </div>

        <!-- القاعات الدراسية -->
        <div class="section" id="rooms">
            <h2 class="section-title">حالة القاعات الدراسية</h2>
            <div class="rooms-container" id="roomsList"></div>
        </div>

        <!-- بيانات الموظفات -->
        <div class="section" id="staff">
            <h2 class="section-title">
                بيانات الموظفات
                <div class="action-buttons" id="staffActions" style="display: none;">
                    <button class="btn btn-primary" onclick="showStaffForm()">
                        <i class="fas fa-plus"></i> إضافة موظفة
                    </button>
                </div>
            </h2>
            
            <div id="staffList" class="staff-container"></div>

            <!-- نموذج إضافة/تعديل موظفة -->
            <div id="staffForm" style="display: none; background: white; padding: 25px; border-radius: 12px; margin-top: 20px;">
                <h3 id="staffFormTitle" style="color: #0b5d4b; margin-bottom: 20px;">إضافة موظفة جديدة</h3>
                <div class="form-group">
                    <label>الاسم الكامل</label>
                    <input type="text" id="staffName" class="form-control">
                </div>
                <div class="form-group">
                    <label>التخصص / المسمى الوظيفي</label>
                    <input type="text" id="staffSpecialty" class="form-control">
                </div>
                <div class="form-group">
                    <label>رقم الجوال</label>
                    <input type="text" id="staffPhone" class="form-control">
                </div>
                <div class="form-group">
                    <label>البريد الإلكتروني</label>
                    <input type="email" id="staffEmail" class="form-control">
                </div>
                <div class="form-group">
                    <label>كلمة المرور (للدخول الخاص)</label>
                    <input type="text" id="staffPassword" class="form-control">
                </div>
                <div class="form-group">
                    <label>ملاحظات</label>
                    <textarea id="staffNotes" class="form-control"></textarea>
                </div>
                <div class="action-buttons">
                    <button class="btn btn-primary" onclick="saveStaff()">حفظ البيانات</button>
                    <button class="btn btn-warning" onclick="hideStaffForm()">إلغاء</button>
                </div>
            </div>
        </div>

        <!-- رسائل الشكر -->
        <div class="section" id="thanks">
            <h2 class="section-title">
                رسائل الشكر والتقدير
                <div class="action-buttons">
                    <button class="btn btn-primary" onclick="showThankForm()">
                        <i class="fas fa-pen"></i> كتابة رسالة شكر
                    </button>
                </div>
            </h2>
            
            <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px;">
                <div>
                    <h3 style="color: #0b5d4b; margin-bottom: 15px;">رسائل الطالبات 👩‍🎓</h3>
                    <div id="studentThanks"></div>
                </div>
                <div>
                    <h3 style="color: #0b5d4b; margin-bottom: 15px;">رسائل أولياء الأمور 👨‍👩‍👧</h3>
                    <div id="parentThanks"></div>
                </div>
            </div>

            <!-- نموذج رسالة شكر -->
            <div id="thankForm" style="display: none; background: white; padding: 25px; border-radius: 12px; margin-top: 20px;">
                <h3 style="color: #0b5d4b; margin-bottom: 20px;">إرسال رسالة شكر</h3>
                <div class="form-group">
                    <label>أنا (طالبة / ولي أمر)</label>
                    <select id="senderType" class="form-control" onchange="toggleSenderFields()">
                        <option value="student">طالبة</option>
                        <option value="parent">ولي أمر</option>
                    </select>
                </div>
                <div id="studentField" class="form-group">
                    <label>اسم الطالبة</label>
                    <input type="text" id="studentName" class="form-control">
                </div>
                <div id="parentField" class="form-group" style="display: none;">
                    <label>اسم ولي الأمر</label>
                    <input type="text" id="parentName" class="form-control">
                </div>
                <div class="form-group">
                    <label>إلى المعلمة / الموظفة</label>
                    <select id="teacherSelect" class="form-control"></select>
                </div>
                <div class="form-group">
                    <label>نص الرسالة</label>
                    <textarea id="thankMessage" class="form-control" rows="4"></textarea>
                </div>
                <div class="action-buttons">
                    <button class="btn btn-primary" onclick="submitThank()">إرسال الرسالة</button>
                    <button class="btn btn-warning" onclick="cancelThankForm()">إلغاء</button>
                </div>
            </div>
        </div>

        <!-- البطاقات الأسبوعية -->
        <div class="section" id="weekly">
            <h2 class="section-title">
                البطاقات الأسبوعية
                <div class="action-buttons" id="weeklyActions" style="display: none;">
                    <button class="btn btn-primary" onclick="addWeeklyCard()">
                        <i class="fas fa-plus"></i> إضافة بطاقة
                    </button>
                </div>
            </h2>
            <div id="weeklyCards" class="weekly-cards-container"></div>
        </div>

        <!-- شهادات الشكر -->
        <div class="section" id="certificates">
            <h2 class="section-title">شهادات الشكر والتقدير</h2>
            
            <!-- نموذج إنشاء شهادة (للمسؤول) -->
            <div id="certForm" style="display: none; background: white; padding: 25px; border-radius: 12px; margin-bottom: 30px; border: 2px dashed #0b5d4b;">
                <h3 style="color: #0b5d4b; margin-bottom: 20px;">إصدار شهادة شكر جديدة</h3>
                <div class="form-group">
                    <label>نوع الشهادة</label>
                    <select id="certType" class="form-control">
                        <option value="teacher">شهادة معلمة</option>
                        <option value="staff">شهادة موظفة</option>
                        <option value="student">شهادة طالبة</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>اسم المكرمة</label>
                    <input type="text" id="certName" class="form-control" placeholder="اسم المكرمة">
                </div>
                <div class="form-group">
                    <label>سبب التكريم</label>
                    <textarea id="certReason" class="form-control" placeholder="سبب التكريم والإنجاز" rows="3"></textarea>
                </div>
                <div class="action-buttons">
                    <button class="btn btn-primary" onclick="createCertificate()">
                        <i class="fas fa-certificate"></i> إنشاء الشهادة
                    </button>
                    <button class="btn btn-warning" onclick="cancelCertForm()">
                        <i class="fas fa-times"></i> إلغاء
                    </button>
                </div>
            </div>
            
            <!-- عرض الشهادات -->
            <div id="certificatesList"></div>
        </div>

        <!-- باركود الحصص -->
        <div class="section" id="barcode">
            <h2 class="section-title">نظام باركود الحصص</h2>
            <div class="barcode-section">
                <p style="margin-bottom: 20px; font-size: 18px;">
                    قم بمسح الباركود عند دخول الحصة لتغيير حالة القاعة
                </p>
                
                <div class="barcode-container">
                    <canvas id="barcodeCanvas" width="300" height="100"></canvas>
                </div>
                
                <div>
                    <p>حالة الحصة الحالية:</p>
                    <div class="status-indicator status-red" id="classStatus"></div>
                    <p id="statusText" style="font-weight: bold; margin-top: 10px;">الحصة لم تبدأ بعد</p>
                </div>
                
                <button class="btn btn-primary" onclick="scanBarcode()" style="margin-top: 20px; padding: 12px 30px;">
                    <i class="fas fa-qrcode"></i> محاكاة مسح الباركود
                </button>
            </div>
            
            <div style="background: #f5f5f5; padding: 20px; border-radius: 12px; margin-top: 30px;">
                <h4 style="color: #0b5d4b; margin-bottom: 15px;">تعليمات الاستخدام:</h4>
                <ol style="line-height: 2; padding-right: 20px;">
                    <li>عند بداية الحصة، تذهب المعلمة للقاعة وتقوم بمسح الباركود</li>
                    <li>يتغير لون القاعة من الأحمر إلى الأخضر تلقائياً</li>
                    <li>عند انتهاء الحصة، يتم مسح الباركود مرة أخرى لإعادة الحالة</li>
                    <li>يمكن للمسؤول رؤية حالة جميع القاعات في صفحة القاعات</li>
                </ol>
            </div>
        </div>

        <!-- تنبيهات التأخير -->
        <div class="section" id="alerts">
            <h2 class="section-title">
                تنبيهات التأخير
                <div class="action-buttons" id="alertActions" style="display: none;">
                    <button class="btn btn-primary" onclick="sendDelayAlert()">
                        <i class="fas fa-bell"></i> إرسال تنبيه تأخير
                    </button>
                </div>
            </h2>
            
            <div id="alertsList"></div>
            
            <!-- نموذج إرسال تنبيه -->
            <div id="alertForm" style="display: none; background: white; padding: 25px; border-radius: 12px; margin-top: 20px;">
                <h3 style="color: #0b5d4b; margin-bottom: 20px;">إرسال تنبيه تأخير</h3>
                <div class="form-group">
                    <label>اسم المعلمة</label>
                    <select id="alertTeacher" class="form-control">
                        <option value="">اختر المعلمة</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>سبب التأخير</label>
                    <select id="delayReason" class="form-control">
                        <option value="اجتماع">اجتماع طارئ</option>
                        <option value="ظرف صحي">ظرف صحي</option>
                        <option value="مواصلات">تأخر في المواصلات</option>
                        <option value="آخر">سبب آخر</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>التفاصيل (اختياري)</label>
                    <textarea id="alertDetails" class="form-control" placeholder="تفاصيل إضافية" rows="3"></textarea>
                </div>
                <div class="action-buttons">
                    <button class="btn btn-primary" onclick="submitAlert()">
                        <i class="fas fa-paper-plane"></i> إرسال التنبيه
                    </button>
                    <button class="btn btn-warning" onclick="cancelAlertForm()">
                        <i class="fas fa-times"></i> إلغاء
                    </button>
                </div>
            </div>
        </div>

        <!-- قصص ملهمة -->
        <div class="section" id="stories">
            <h2 class="section-title">قصص ملهمة</h2>
            <div style="background: white; padding: 25px; border-radius: 12px;">
                <div class="form-group">
                    <label>رفع صورة للقصة</label>
                    <input type="file" class="form-control" accept="image/*">
                </div>
                <div class="form-group">
                    <label>رفع تسجيل صوتي</label>
                    <input type="file" class="form-control" accept="audio/*">
                </div>
                <div class="form-group">
                    <label>نص القصة</label>
                    <textarea class="form-control" rows="6" placeholder="اكتب القصة الملهمة هنا..."></textarea>
                </div>
                <button class="btn btn-primary" style="padding: 12px 30px;">
                    <i class="fas fa-upload"></i> نشر القصة
                </button>
            </div>
        </div>
    </div>
</div>

<footer style="display: none;">
    متوسطة الأولى بتيماء – كل يوم قدوة 🌟
</footer>

<script>
// ===== البيانات والمتغيرات =====
let isAdmin = false;
let currentStaffId = null;
let classActive = false;

// بيانات القاعات
const rooms = [
    { id: 1, name: "قاعة أول متوسط (١)", status: "empty" },
    { id: 2, name: "قاعة أول متوسط (٢)", status: "occupied" },
    { id: 3, name: "قاعة ثاني متوسط (١)", status: "empty" },
    { id: 4, name: "قاعة ثاني متوسط (٢)", status: "closed" },
    { id: 5, name: "قاعة ثالث متوسط (١)", status: "empty" },
    { id: 6, name: "قاعة ثالث متوسط (٢)", status: "occupied" },
    { id: 7, name: "معمل الحاسب الآلي", status: "occupied" },
    { id: 8, name: "معمل العلوم", status: "empty" },
    { id: 9, name: "معمل الاجتماعيات", status: "closed" },
    { id: 10, name: "مصادر التعلم", status: "occupied" },
    { id: 11, name: "الصالة الرياضية", status: "empty" }
];

// بيانات الموظفات (محاكاة)
let staffData = [
    { id: 1, name: "سارة أحمد", specialty: "معلمة لغة عربية", phone: "0512345678", email: "sara@school.edu.sa", password: "123456", notes: "متميزة في التدريس" },
    { id: 2, name: "فاطمة محمد", specialty: "معلمة رياضيات", phone: "0587654321", email: "fatima@school.edu.sa", password: "654321", notes: "إبداعية في شرح الدروس" },
    { id: 3, name: "نورة عبدالله", specialty: "معلمة علوم", phone: "0555555555", email: "nora@school.edu.sa", password: "nora123", notes: "تهتم بالتجارب العملية" }
];

// بيانات البطاقات الأسبوعية
let weeklyCards = [
    { id: 1, name: "سارة أحمد", reason: "تميز في تفاعل الطالبات", date: "الأسبوع الأول" },
    { id: 2, name: "فاطمة محمد", reason: "إبداع في تصميم الأنشطة", date: "الأسبوع الثاني" }
];

// بيانات رسائل الشكر
let thankMessages = {
    student: [
        { id: 1, studentName: "أميرة خالد", teacherName: "سارة أحمد", message: "شكرًا لكِ على صبرك وشرحك الواضح" },
        { id: 2, studentName: "لما عبدالرحمن", teacherName: "فاطمة محمد", message: "أحب طريقة شرحك للرياضيات" }
    ],
    parent: [
        { id: 1, parentName: "أحمد محمد", teacherName: "نورة عبدالله", message: "شكرًا لاهتمامك بابنتي وتحسين مستواها" }
    ]
};

// ===== نظام تسجيل الدخول =====
function loginAdmin() {
    const username = document.getElementById('adminUsername').value;
    const password = document.getElementById('adminPassword').value;
    
    // تحقق بسيط (في الواقع يجب أن يكون من قاعدة بيانات)
    if (username === "admin" && password === "admin123") {
        isAdmin = true;
        document.getElementById('loginOverlay').style.display = 'none';
        document.getElementById('welcomeOverlay').style.display = 'flex';
        showAdminControls();
    } else {
        alert("اسم المستخدم أو كلمة المرور غير صحيحة");
    }
}

function showAdminControls() {
    if (isAdmin) {
        document.getElementById('adminControls').style.display = 'flex';
        document.querySelectorAll('#staffActions, #thanksActions, #weeklyActions, #alertActions').forEach(el => {
            el.style.display = 'flex';
        });
        
        // عرض نموذج إنشاء الشهادات
        document.getElementById('certForm').style.display = 'block';
        
        // تحميل بيانات الموظفات في القوائم المنسدلة
        loadTeachersForSelect();
    }
}

function logout() {
    isAdmin = false;
    document.getElementById('loginOverlay').style.display = 'flex';
    document.getElementById('welcomeOverlay').style.display = 'none';
    document.querySelector('header').style.display = 'none';
    document.querySelector('.main').style.display = 'none';
    document.querySelector('footer').style.display = 'none';
    hideAdminControls();
}

function hideAdminControls() {
    document.getElementById('adminControls').style.display = 'none';
    document.querySelectorAll('#staffActions, #thanksActions, #weeklyActions, #alertActions').forEach(el => {
        el.style.display = 'none';
    });
    document.getElementById('certForm').style.display = 'none';
}

// ===== الترحيب =====
function closeWelcome() {
    document.getElementById('welcomeOverlay').style.display = 'none';
    document.querySelector('header').style.display = 'flex';
    document.querySelector('.main').style.display = 'flex';
    document.querySelector('footer').style.display = 'block';
    
    // تحميل البيانات الأولية
    loadRooms();
    loadStaff();
    loadThankMessages();
    loadWeeklyCards();
    loadWeeklyCardsHome();
    loadCertificates();
    loadAlerts();
}

// ===== التنقل بين الأقسام =====
function showSection(sectionId) {
    document.querySelectorAll('.section').forEach(section => {
        section.classList.remove('active');
    });
    document.getElementById(sectionId).classList.add('active');
    
    // تحديث الأزرار في القائمة الجانبية
    document.querySelectorAll('.sidebar button').forEach(btn => {
        btn.classList.remove('home');
    });
    event.currentTarget.classList.add('home');
}

// ===== إدارة القاعات =====
function loadRooms() {
    const roomsList = document.getElementById('roomsList');
    roomsList.innerHTML = '';
    
    rooms.forEach(room => {
        let statusClass = "";
        let statusText = "";
        
        if (room.status === "empty") {
            statusClass = "empty";
            statusText = "فارغة";
        } else if (room.status === "occupied") {
            statusClass = "occupied";
            statusText = "مشغولة";
        } else {
            statusClass = "closed";
            statusText = "مقفلة";
        }
        
        roomsList.innerHTML += `
            <div class="room-card">
                <div class="room-name">${room.name}</div>
                <div class="status ${statusClass}">${statusText}</div>
                ${isAdmin ? `
                <div style="margin-top: 15px; display: flex; gap: 5px; justify-content: center;">
                    <button class="btn btn-primary" onclick="changeRoomStatus(${room.id}, 'occupied')" style="padding: 5px 8px; font-size: 12px;">إشغال</button>
                    <button class="btn btn-danger" onclick="changeRoomStatus(${room.id}, 'empty')" style="padding: 5px 8px; font-size: 12px;">تفريغ</button>
                    <button class="btn btn-warning" onclick="changeRoomStatus(${room.id}, 'closed')" style="padding: 5px 8px; font-size: 12px;">إقفال</button>
                </div>` : ''}
            </div>
        `;
    });
}

function changeRoomStatus(id, newStatus) {
    const room = rooms.find(r => r.id === id);
    if (room) {
        room.status = newStatus;
        loadRooms();
    }
}

// ===== إدارة الموظفات =====
function loadStaff() {
    const staffList = document.getElementById('staffList');
    staffList.innerHTML = '';
    
    staffData.forEach(staff => {
        staffList.innerHTML += `
            <div class="staff-card">
                ${isAdmin ? `
                <div class="staff-actions">
                    <button class="btn btn-warning" onclick="editStaff(${staff.id})" style="padding: 5px 10px; font-size: 12px;">
                        <i class="fas fa-edit"></i>
                    </button>
                    <button class="btn btn-danger" onclick="deleteStaff(${staff.id})" style="padding: 5px 10px; font-size: 12px;">
                        <i class="fas fa-trash"></i>
                    </button>
                </div>` : ''}
                <div class="staff-name">${staff.name}</div>
                <div class="staff-info"><strong>التخصص:</strong> ${staff.specialty}</div>
                <div class="staff-info"><strong>الجوال:</strong> ${staff.phone}</div>
                <div class="staff-info"><strong>البريد:</strong> ${staff.email}</div>
                ${isAdmin ? `
                <div class="password-field">
                    <strong>كلمة المرور:</strong>
                    <span>${staff.password}</span>
                </div>
                <div class="staff-info" style="margin-top: 10px;"><strong>ملاحظات:</strong> ${staff.notes}</div>
                ` : ''}
            </div>
        `;
    });
    
    // تحديث القوائم المنسدلة التي تعتمد على الموظفات
    loadTeachersForSelect();
}

function showStaffForm() {
    currentStaffId = null;
    document.getElementById('staffFormTitle').textContent = "إضافة موظفة جديدة";
    document.getElementById('staffName').value = '';
    document.getElementById('staffSpecialty').value = '';
    document.getElementById('staffPhone').value = '';
    document.getElementById('staffEmail').value = '';
    document.getElementById('staffPassword').value = '';
    document.getElementById('staffNotes').value = '';
    document.getElementById('staffForm').style.display = 'block';
    document.getElementById('staffList').style.display = 'none';
}

function hideStaffForm() {
    document.getElementById('staffForm').style.display = 'none';
    document.getElementById('staffList').style.display = 'grid';
}

function saveStaff() {
    const name = document.getElementById('staffName').value;
    const specialty = document.getElementById('staffSpecialty').value;
    const phone = document.getElementById('staffPhone').value;
    const email = document.getElementById('staffEmail').value;
    const password = document.getElementById('staffPassword').value;
    const notes = document.getElementById('staffNotes').value;
    
    if (!name || !specialty) {
        alert("الرجاء إدخال الاسم والتخصص على الأقل");
        return;
    }
    
    if (currentStaffId) {
        // تعديل
        const index = staffData.findIndex(s => s.id === currentStaffId);
        staffData[index] = { id: currentStaffId, name, specialty, phone, email, password, notes };
    } else {
        // إضافة جديد
        const newId = staffData.length > 0 ? Math.max(...staffData.map(s => s.id)) + 1 : 1;
        staffData.push({ id: newId, name, specialty, phone, email, password, notes });
    }
    
    loadStaff();
    hideStaffForm();
}

function editStaff(id) {
    const staff = staffData.find(s => s.id === id);
    if (staff) {
        currentStaffId = id;
        document.getElementById('staffFormTitle').textContent = "تعديل بيانات الموظفة";
        document.getElementById('staffName').value = staff.name;
        document.getElementById('staffSpecialty').value = staff.specialty;
        document.getElementById('staffPhone').value = staff.phone;
        document.getElementById('staffEmail').value = staff.email;
        document.getElementById('staffPassword').value = staff.password;
        document.getElementById('staffNotes').value = staff.notes;
        document.getElementById('staffForm').style.display = 'block';
        document.getElementById('staffList').style.display = 'none';
    }
}

function deleteStaff(id) {
    if (confirm('هل أنت متأكد من حذف هذه الموظفة؟')) {
        staffData = staffData.filter(s => s.id !== id);
        loadStaff();
    }
}

// ===== رسائل الشكر =====
function loadTeachersForSelect() {
    const teacherSelect = document.getElementById('teacherSelect');
    const alertTeacher = document.getElementById('alertTeacher');
    
    if (teacherSelect) {
        teacherSelect.innerHTML = '<option value="">اختر المعلمة / الموظفة</option>';
        staffData.forEach(staff => {
            teacherSelect.innerHTML += `<option value="${staff.id}">${staff.name}</option>`;
        });
    }
    
    if (alertTeacher) {
        alertTeacher.innerHTML = '<option value="">اختر المعلمة</option>';
        staffData.forEach(staff => {
            alertTeacher.innerHTML += `<option value="${staff.id}">${staff.name}</option>`;
        });
    }
}

function showThankForm() {
    document.getElementById('thankForm').style.display = 'block';
    loadTeachersForSelect();
}

function toggleSenderFields() {
    const type = document.getElementById('senderType').value;
    if (type === 'student') {
        document.getElementById('studentField').style.display = 'block';
        document.getElementById('parentField').style.display = 'none';
    } else {
        document.getElementById('studentField').style.display = 'none';
        document.getElementById('parentField').style.display = 'block';
    }
}

function submitThank() {
    const type = document.getElementById('senderType').value;
    const teacherId = document.getElementById('teacherSelect').value;
    const message = document.getElementById('thankMessage').value;
    
    if (!teacherId || !message) {
        alert('الرجاء اختيار المعلمة وكتابة الرسالة');
        return;
    }
    
    const teacher = staffData.find(s => s.id == teacherId);
    const newId = Date.now();
    
    if (type === 'student') {
        const name = document.getElementById('studentName').value || "طالبة";
        thankMessages.student.push({ id: newId, studentName: name, teacherName: teacher.name, message });
    } else {
        const name = document.getElementById('parentName').value || "ولي أمر";
        thankMessages.parent.push({ id: newId, parentName: name, teacherName: teacher.name, message });
    }
    
    cancelThankForm();
    loadThankMessages();
    
    // توجيه الرسالة للمعلمة (محاكاة)
    alert(`تم إرسال رسالة الشكر إلى ${teacher.name}`);
}

function cancelThankForm() {
    document.getElementById('thankForm').style.display = 'none';
    document.getElementById('studentName').value = '';
    document.getElementById('parentName').value = '';
    document.getElementById('teacherSelect').value = '';
    document.getElementById('thankMessage').value = '';
}

function loadThankMessages() {
    const studentThanks = document.getElementById('studentThanks');
    const parentThanks = document.getElementById('parentThanks');
    
    studentThanks.innerHTML = '';
    parentThanks.innerHTML = '';
    
    thankMessages.student.forEach(msg => {
        studentThanks.innerHTML += `
            <div style="background: white; padding: 15px; border-radius: 8px; margin-bottom: 10px;">
                <strong>من الطالبة: ${msg.studentName}</strong><br>
                <strong>إلى المعلمة: ${msg.teacherName}</strong><br>
                <p style="margin-top: 8px;">${msg.message}</p>
                ${isAdmin ? `<button class="btn btn-danger" onclick="deleteThankMessage('student', ${msg.id})" style="padding: 5px 10px; font-size: 12px;">
                    حذف
                </button>` : ''}
            </div>
        `;
    });
    
    thankMessages.parent.forEach(msg => {
        parentThanks.innerHTML += `
            <div style="background: white; padding: 15px; border-radius: 8px; margin-bottom: 10px;">
                <strong>من ولي الأمر: ${msg.parentName}</strong><br>
                <strong>إلى المعلمة: ${msg.teacherName}</strong><br>
                <p style="margin-top: 8px;">${msg.message}</p>
                ${isAdmin ? `<button class="btn btn-danger" onclick="deleteThankMessage('parent', ${msg.id})" style="padding: 5px 10px; font-size: 12px;">
                    حذف
                </button>` : ''}
            </div>
        `;
    });
}

function deleteThankMessage(type, id) {
    if (confirm('هل أنت متأكد من حذف هذه الرسالة؟')) {
        thankMessages[type] = thankMessages[type].filter(msg => msg.id !== id);
        loadThankMessages();
    }
}

// ===== البطاقات الأسبوعية =====
function loadWeeklyCards() {
    const weeklyCardsContainer = document.getElementById('weeklyCards');
    weeklyCardsContainer.innerHTML = '';
    
    weeklyCards.forEach(card => {
        weeklyCardsContainer.innerHTML += `
            <div class="weekly-card">
                <h3>بطاقة تكريم أسبوعية</h3>
                <p><strong>المكرمة:</strong> ${card.name}</p>
                <p><strong>سبب التكريم:</strong> ${card.reason}</p>
                <p><strong>الفترة:</strong> ${card.date}</p>
                ${isAdmin ? `
                <div style="margin-top: 15px;">
                    <button class="btn btn-warning" onclick="editWeeklyCard(${card.id})" style="margin-right: 10px;">
                        <i class="fas fa-edit"></i> تعديل
                    </button>
                    <button class="btn btn-danger" onclick="deleteWeeklyCard(${card.id})">
                        <i class="fas fa-trash"></i> حذف
                    </button>
                </div>` : ''}
            </div>
        `;
    });
}

function loadWeeklyCardsHome() {
    const weeklyCardsHome = document.getElementById('weeklyCardsHome');
    weeklyCardsHome.innerHTML = '';
    
    // عرض آخر 3 بطاقات فقط
    const recentCards = weeklyCards.slice(-3);
    
    recentCards.forEach(card => {
        weeklyCardsHome.innerHTML += `
            <div class="weekly-card-home">
                <h4>🎖️ ${card.name}</h4>
                <p>${card.reason}</p>
                <small>${card.date}</small>
            </div>
        `;
    });
}

function addWeeklyCard() {
    const name = prompt('اسم الموظفة / الموظف:');
    const reason = prompt('سبب التكريم:');
    const date = prompt('الفترة (مثال: الأسبوع الثالث):');
    
    if (name && reason && date) {
        const newId = weeklyCards.length > 0 ? Math.max(...weeklyCards.map(c => c.id)) + 1 : 1;
        weeklyCards.push({ id: newId, name, reason, date });
        loadWeeklyCards();
        loadWeeklyCardsHome();
    }
}

function editWeeklyCard(id) {
    const card = weeklyCards.find(c => c.id === id);
    if (card) {
        const name = prompt('اسم الموظفة / الموظف:', card.name);
        const reason = prompt('سبب التكريم:', card.reason);
        const date = prompt('الفترة:', card.date);
        
        if (name && reason && date) {
            card.name = name;
            card.reason = reason;
            card.date = date;
            loadWeeklyCards();
            loadWeeklyCardsHome();
        }
    }
}

function deleteWeeklyCard(id) {
    if (confirm('هل أنت متأكد من حذف هذه البطاقة؟')) {
        weeklyCards = weeklyCards.filter(c => c.id !== id);
        loadWeeklyCards();
        loadWeeklyCardsHome();
    }
}

// ===== شهادات الشكر =====
function loadCertificates() {
    const certificatesList = document.getElementById('certificatesList');
    certificatesList.innerHTML = '';
    
    // شهادات افتراضية
    const certificates = [
        { type: "teacher", name: "سارة أحمد", reason: "لتميزها في تدريس اللغة العربية وتفاعل الطالبات" },
        { type: "staff", name: "وفاء السلامة", reason: "لجهودها المتميزة في إدارة المبادرة وتنظيم الفعاليات" },
        { type: "student", name: "أميرة خالد", reason: "لتفوقها الدراسي وتمثيلها المدرسة في المسابقات" }
    ];
    
    certificates.forEach((cert, index) => {
        let title = "";
        if (cert.type === "teacher") title = "شهادة شكر معلمة";
        else if (cert.type === "staff") title = "شهادة شكر موظفة";
        else title = "شهادة شكر طالبة";
        
        certificatesList.innerHTML += `
            <div class="certificate" style="margin-bottom: 30px;">
                ${isAdmin ? `
                <div class="cert-actions">
                    <button class="btn btn-warning" onclick="editCertificate(${index})">
                        <i class="fas fa-edit"></i>
                    </button>
                    <button class="btn btn-danger" onclick="deleteCertificate(${index})">
                        <i class="fas fa-trash"></i>
                    </button>
                </div>` : ''}
                <h3>${title}</h3>
                <p>
                    تُمنح هذه الشهادة التقديرية للأستاذة الفاضلة<br>
                    <strong>${cert.name}</strong><br><br>
                    ${cert.reason}<br><br>
                    وذلك تقديرًا لجهودها المتميزة وعطائها المستمر.<br>
                    <br>
                    <em>مديرة المدرسة</em>
                </p>
            </div>
        `;
    });
}

function createCertificate() {
    const type = document.getElementById('certType').value;
    const name = document.getElementById('certName').value;
    const reason = document.getElementById('certReason').value;
    
    if (!name || !reason) {
        alert('الرجاء ملء جميع الحقول');
        return;
    }
    
    alert(`تم إنشاء شهادة شكر لـ ${name}`);
    
    // إعادة تعيين النموذج
    document.getElementById('certName').value = '';
    document.getElementById('certReason').value = '';
    
    // إعادة تحميل الشهادات
    loadCertificates();
}

function cancelCertForm() {
    document.getElementById('certName').value = '';
    document.getElementById('certReason').value = '';
}

function editCertificate(index) {
    const newReason = prompt('عدل سبب التكريم:', 'سبب التكريم الحالي');
    if (newReason) {
        // في التطبيق الحقيقي، هنا يتم تحديث قاعدة البيانات
        alert('تم التعديل (محاكاة)');
        loadCertificates();
    }
}

function deleteCertificate(index) {
    if (confirm('هل أنت متأكد من حذف هذه الشهادة؟')) {
        // في التطبيق الحقيقي، هنا يتم الحذف من قاعدة البيانات
        alert('تم الحذف (محاكاة)');
        loadCertificates();
    }
}

// ===== نظام الباركود =====
// رسم باركود بسيط
const canvas = document.getElementById('barcodeCanvas');
const ctx = canvas.getContext('2d');

// تنظيف Canvas
ctx.fillStyle = 'white';
ctx.fillRect(0, 0, canvas.width, canvas.height);

// رسم خطوط الباركود
ctx.fillStyle = 'black';
for (let i = 0; i < 20; i++) {
    const height = 30 + Math.random() * 50;
    const width = 10;
    const x = 20 + i * 12;
    ctx.fillRect(x, 20, width, height);
}

// كتابة نص تحت الباركود
ctx.fillStyle = '#333';
ctx.font = '14px Arial';
ctx.textAlign = 'center';
ctx.fillText('باركود الحصة الدراسية - مسح للبدء', canvas.width / 2, 90);

function scanBarcode() {
    const statusIndicator = document.getElementById('classStatus');
    const statusText = document.getElementById('statusText');
    
    if (classActive) {
        // إنهاء الحصة
        classActive = false;
        statusIndicator.className = 'status-indicator status-red';
        statusText.textContent = 'الحصة انتهت';
        statusText.style.color = '#c62828';
        
        // تغيير لون القاعة في النظام
        const currentRoom = rooms.find(r => r.status === 'occupied');
        if (currentRoom) {
            currentRoom.status = 'empty';
            loadRooms();
        }
        
        alert('تم إنهاء الحصة وتغيير حالة القاعة إلى فارغة');
    } else {
        // بدء الحصة
        classActive = true;
        statusIndicator.className = 'status-indicator status-green';
        statusText.textContent = 'الحصة نشطة الآن';
        statusText.style.color = '#2e7d32';
        
        // تغيير لون أول قاعة فارغة
        const emptyRoom = rooms.find(r => r.status === 'empty');
        if (emptyRoom) {
            emptyRoom.status = 'occupied';
            loadRooms();
        }
        
        alert('تم بدء الحصة وتغيير حالة القاعة إلى مشغولة');
    }
}

// ===== تنبيهات التأخير =====
function loadAlerts() {
    const alertsList = document.getElementById('alertsList');
    alertsList.innerHTML = '';
    
    // تنبيهات افتراضية
    const alerts = [
        { teacher: "سارة أحمد", reason: "اجتماع", details: "اجتماع طارئ مع الإدارة", time: "8:15 ص" },
        { teacher: "فاطمة محمد", reason: "مواصلات", details: "تأخر بسبب ازدحام المرور", time: "9:00 ص" }
    ];
    
    if (alerts.length === 0) {
        alertsList.innerHTML = '<p style="text-align: center; color: #666;">لا توجد تنبيهات تأخير حالية</p>';
        return;
    }
    
    alerts.forEach((alert, index) => {
        alertsList.innerHTML += `
            <div class="alert-box">
                <div>
                    <strong>المعلمة: ${alert.teacher}</strong><br>
                    <span>السبب: ${alert.reason}</span><br>
                    <small>${alert.details} - الساعة: ${alert.time}</small>
                </div>
                ${isAdmin ? `
                <div>
                    <button class="btn btn-warning" onclick="resolveAlert(${index})" style="margin-left: 10px;">
                        <i class="fas fa-check"></i> معالجة
                    </button>
                    <button class="btn btn-danger" onclick="deleteAlert(${index})">
                        <i class="fas fa-times"></i> حذف
                    </button>
                </div>` : ''}
            </div>
        `;
    });
}

function sendDelayAlert() {
    document.getElementById('alertForm').style.display = 'block';
}

function submitAlert() {
    const teacherId = document.getElementById('alertTeacher').value;
    const reason = document.getElementById('delayReason').value;
    const details = document.getElementById('alertDetails').value;
    
    if (!teacherId) {
        alert('الرجاء اختيار المعلمة');
        return;
    }
    
    const teacher = staffData.find(s => s.id == teacherId);
    if (!teacher) {
        alert('المعلمة غير موجودة');
        return;
    }
    
    const now = new Date();
    const time = now.getHours() + ':' + (now.getMinutes() < 10 ? '0' : '') + now.getMinutes();
    
    // في التطبيق الحقيقي، هنا يتم حفظ التنبيه في قاعدة البيانات
    // وإرسال إشعار للمعلمة
    
    alert(`تم إرسال تنبيه تأخير إلى ${teacher.name}`);
    
    // توجيه التنبيه للمعلمة (محاكاة)
    console.log(`تنبيه تأخير لـ ${teacher.name}: ${reason} - ${details}`);
    
    cancelAlertForm();
    loadAlerts();
}

function cancelAlertForm() {
    document.getElementById('alertForm').style.display = 'none';
    document.getElementById('alertTeacher').value = '';
    document.getElementById('delayReason').value = 'اجتماع';
    document.getElementById('alertDetails').value = '';
}

function resolveAlert(index) {
    if (confirm('تمت معالجة تنبيه التأخير؟')) {
        // في التطبيق الحقيقي، هنا يتم تحديث قاعدة البيانات
        alert('تمت المعالجة (محاكاة)');
        loadAlerts();
    }
}

function deleteAlert(index) {
    if (confirm('حذف تنبيه التأخير؟')) {
        // في التطبيق الحقيقي، هنا يتم الحذف من قاعدة البيانات
        alert('تم الحذف (محاكاة)');
        loadAlerts();
    }
}

// ===== تهيئة أولية =====
// عند تحميل الصفحة، تعطى الأولوية لنظام تسجيل الدخول
window.onload = function() {
    // إنشاء باركود
    scanBarcode(); // تعيين الحالة الأولية
    
    // تعيين اسم الأسبوع الحالي في البطاقات الأسبوعية
    const weeks = ['الأول', 'الثاني', 'الثالث', 'الرابع', 'الخامس'];
    const currentWeek = weeks[new Date().getDate() % 5];
    weeklyCards.forEach(card => {
        if (card.date.includes('الأسبوع')) {
            card.date = `الأسبوع ${currentWeek}`;
        }
    });
};
</script>
</body>
</html>
