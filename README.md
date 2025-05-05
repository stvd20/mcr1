# 🏥 Medical Referral System Dashboard (MCR1)

نظام متكامل لإدارة الإحالات الطبية بين المنشآت، يتكوّن من 6 صفحات رئيسية:

## 🧾 الصفحات:

1. **الرئيسية (index.html)** – عرض جميع الإحالات + رسم بياني DashBoard
2. **إنشاء إحالة (create.html)** – تسجيل بيانات مريض + نوع الإحالة + الطبيب
3. **الإحالات الواردة (incoming.html)** – إحالات وصلت من مستشفيات أخرى
4. **الرد على الإحالة (reply.html)** – يتم بواسطة الطبيب المعالج مع مرفق ورد
5. **التقارير (reports.html)** – تقارير الإحالات المنقولة والمقبولة
6. **الإعدادات (settings.html)** – تغيير كلمة مرور، حجب الشاشات حسب الصلاحيات

## 💡 مميزات النظام:
- واجهة RTL عربية بسيطة وفعالة
- تقنيات: HTML + CSS + JS (مع دعم مستقبلي لـ Firebase)
- يدعم صلاحيات المستخدمين: طبيب – موظف – مدير

## 🛠️ التطوير المستقبلي:
- دعم قاعدة بيانات حية
- تسجيل دخول وتسجيل خروج
- رفع ملفات ومرفقات لكل إحالة
<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <title>إنشاء إحالة</title>
  <link rel="stylesheet" href="style.css">
  <style>
    body {
      font-family: 'Tajawal', sans-serif;
      direction: rtl;
      background: #f9f9f9;
      padding: 20px;
    }
    h2 {
      color: #333;
    }
    .row {
      display: flex;
      justify-content: space-between;
      gap: 20px;
      margin-top: 20px;
    }
    .section {
      background: #fff;
      padding: 15px;
      border-radius: 10px;
      flex: 1;
      box-shadow: 0 0 10px rgba(0,0,0,0.05);
    }
    input, select {
      width: 100%;
      padding: 10px;
      margin-bottom: 15px;
      border-radius: 5px;
      border: 1px solid #ccc;
    }
    label {
      font-weight: bold;
      display: block;
      margin-bottom: 5px;
    }
    .badge {
      padding: 8px 10px;
      color: #fff;
      border-radius: 5px;
      margin: 5px 0;
      display: inline-block;
    }
    .red { background-color: #e74c3c; }
    .yellow { background-color: #f1c40f; }
    .green { background-color: #2ecc71; }
    .blue { background-color: #3498db; }
  </style>
</head>
<body>

  <h2>📝 إنشاء إحالة جديدة</h2>

  <label>🔍 البحث برقم الإحالة:</label>
  <input type="text" placeholder="أدخل رقم الإحالة للبحث">

  <div class="row">
    <!-- سعودي -->
    <div class="section">
      <h3>👤 سعودي</h3>
      <label>رقم الملف</label>
      <input type="text">
      <label>اسم المريض</label>
      <input type="text">
      <label>نوع المريض</label>
      <select>
        <option>ذكر</option>
        <option>أنثى</option>
      </select>
      <label>الجنسية</label>
      <input type="text" value="سعودي" disabled>
    </div>

    <!-- مقيم -->
    <div class="section">
      <h3>👤 مقيم</h3>
      <label>رقم الإحالة</label>
      <input type="text">
      <label>نوع الإحالة</label>
      <div>
        <span class="badge red">إنقاذ حياة</span>
        <span class="badge yellow">طارئ</span>
        <span class="badge green">تنويم</span>
        <span class="badge blue">عيادات</span>
      </div>
      <label>اسم المستشفى المستقبل</label>
      <input type="text">
      <label>التخصص المطلوب</label>
      <input type="text" placeholder="اكتب التخصص هنا">
    </div>

    <!-- زائر/مجهول -->
    <div class="section">
      <h3>👤 زائر / مجهول</h3>
      <label>اسم الطبيب</label>
      <input type="text">
      <label>رقم الجوال</label>
      <input type="text">
      <label>اسم الموظف المنشئ</label>
      <input type="text">
    </div>
  </div>

</body>
</html>
