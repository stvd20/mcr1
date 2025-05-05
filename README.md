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
<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <title>الإحالات الواردة</title>
  <link rel="stylesheet" href="style.css">
  <style>
    body {
      font-family: 'Tajawal', sans-serif;
      direction: rtl;
      background: #f1f1f1;
      padding: 20px;
    }
    h2 {
      color: #2c3e50;
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

  <h2>📩 الإحالات الواردة</h2>

  <label>🔍 البحث برقم الإحالة:</label>
  <input type="text" placeholder="أدخل رقم الإحالة للبحث">

  <div class="row">
    <!-- معلومات المريض -->
    <div class="section">
      <h3>🧍‍♂️ معلومات المريض</h3>
      <label>رقم الإحالة</label>
      <input type="text">
      <label>اسم المريض</label>
      <input type="text">
      <label>نوع المريض</label>
      <select>
        <option>سعودي</option>
        <option>مقيم</option>
        <option>زائر</option>
      </select>
      <label>جنسية المريض</label>
      <input type="text">
    </div>

    <!-- تفاصيل الإحالة -->
    <div class="section">
      <h3>📄 تفاصيل الإحالة</h3>
      <label>رقم الإحالة</label>
      <input type="text">
      <label>نوع الإحالة</label>
      <div>
        <span class="badge red">إنقاذ حياة</span>
        <span class="badge yellow">طارئ</span>
        <span class="badge green">تنويم</span>
        <span class="badge blue">عيادات</span>
      </div>
    </div>

    <!-- المستشفى والتخصص -->
    <div class="section">
      <h3>🏥 بيانات المستشفى</h3>
      <label>اسم المستشفى المرسل</label>
      <input type="text">
      <label>التخصص المطلوب</label>
      <input type="text">
    </div>
  </div>

</body>
</html>
/* 📦 ملف التنسيق العام للمشروع */

body {
  font-family: 'Tajawal', sans-serif;
  direction: rtl;
  background-color: #f5f5f5;
  margin: 0;
  padding: 20px;
}

h1, h2, h3 {
  color: #2c3e50;
}

input, select, textarea {
  width: 100%;
  padding: 10px;
  margin-bottom: 15px;
  border: 1px solid #ccc;
  border-radius: 5px;
  font-family: inherit;
}

label {
  font-weight: bold;
  margin-bottom: 5px;
  display: block;
}

.section {
  background-color: #fff;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 0 8px rgba(0,0,0,0.05);
  margin-bottom: 20px;
}

.row {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.badge {
  padding: 8px 12px;
  color: #fff;
  border-radius: 5px;
  display: inline-block;
  margin: 5px 5px 10px 0;
  font-size: 14px;
}

.red { background-color: #e74c3c; }
.yellow { background-color: #f1c40f; color: #000; }
.green { background-color: #2ecc71; }
.blue { background-color: #3498db; }

button {
  padding: 10px 20px;
  background-color: #3498db;
  border: none;
  color: #fff;
  font-size: 16px;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #2980b9;
}
<!-- داخل قسم الإحالة -->
<button onclick="goToReply()">رد على الإحالة</button>

<script>
  function goToReply() {
    const referralNumber = document.querySelector('input[placeholder="أدخل رقم الإحالة"]').value;
    const patientName = document.querySelector('input[placeholder="اسم المريض"]').value;
    const specialty = document.querySelector('input[placeholder="مثال: جراحة قلب"]').value;

    // خزّن البيانات
    localStorage.setItem('referralNumber', referralNumber);
    localStorage.setItem('patientName', patientName);
    localStorage.setItem('specialty', specialty);

    // روح لصفحة الرد
    window.location.href = 'reply.html';
  }
</script>
<script>
  window.onload = () => {
    document.querySelector('input[placeholder="أدخل رقم الإحالة"]').value = localStorage.getItem('referralNumber') || '';
    document.querySelector('input[placeholder="اسم المريض"]').value = localStorage.getItem('patientName') || '';
    document.querySelector('input[placeholder="مثال: جراحة قلب"]').value = localStorage.getItem('specialty') || '';
  };
</script>
<button onclick="goToReply()">رد على الإحالة</button>

<script>
  function goToReply() {
    const referralNumber = document.querySelector('input[placeholder="أدخل رقم الإحالة"]').value;
    const patientName = document.querySelector('input[placeholder="اسم المريض"]').value;
    const specialty = document.querySelector('input[placeholder="مثال: جراحة قلب"]').value;

    // تخزين البيانات مؤقتًا في المتصفح
    localStorage.setItem('referralNumber', referralNumber);
    localStorage.setItem('patientName', patientName);
    localStorage.setItem('specialty', specialty);

    // التوجه لصفحة الرد
    window.location.href = 'reply.html';
  }
</script>
<script>
  window.onload = () => {
    document.querySelector('input[placeholder="أدخل رقم الإحالة"]').value = localStorage.getItem('referralNumber') || '';
    document.querySelector('input[placeholder="اسم المريض"]').value = localStorage.getItem('patientName') || '';
    document.querySelector('input[placeholder="مثال: جراحة قلب"]').value = localStorage.getItem('specialty') || '';
  };
</script>
<div class="section">
  <h3>🔍 قائمة الإحالات</h3>
  <div class="referral" onclick="goToReply('12345', 'أحمد محمد', 'أنف وأذن')">
    <p>رقم الإحالة: 12345</p>
    <p>اسم المريض: أحمد محمد</p>
    <p>التخصص: أنف وأذن</p>
    <button>رد على الإحالة</button>
  </div>

  <div class="referral" onclick="goToReply('98765', 'سارة خالد', 'قلب')">
    <p>رقم الإحالة: 98765</p>
    <p>اسم المريض: سارة خالد</p>
    <p>التخصص: قلب</p>
    <button>رد على الإحالة</button>
  </div>
</div>

<script>
  function goToReply(referralNumber, patientName, specialty) {
    localStorage.setItem('referralNumber', referralNumber);
    localStorage.setItem('patientName', patientName);
    localStorage.setItem('specialty', specialty);
    window.location.href = 'reply.html';
  }
</script>
<script>
  window.onload = () => {
    document.querySelector('input[placeholder="أدخل رقم الإحالة"]').value = localStorage.getItem('referralNumber') || '';
    document.querySelector('input[placeholder="اسم المريض"]').value = localStorage.getItem('patientName') || '';
    document.querySelector('input[placeholder="مثال: جراحة قلب"]').value = localStorage.getItem('specialty') || '';
  };
</script>
function clearLocalStorage() {
  localStorage.removeItem('referralNumber');
  localStorage.removeItem('patientName');
  localStorage.removeItem('specialty');
}
<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <title>تقارير الإحالات</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <h2>📰 التقارير</h2>

  <div class="section">
    <h3>📦 الإحالات المنقولة</h3>
    <table border="1" width="100%" cellpadding="10">
      <tr>
        <th>رقم الإحالة</th>
        <th>اسم المريض</th>
        <th>التخصص</th>
        <th>المستشفى المستقبل</th>
        <th>ملاحظة</th>
      </tr>
      <tr>
        <td>12345</td>
        <td>أحمد محمد</td>
        <td>جراحة</td>
        <td>مستشفى الملك فهد</td>
        <td>تم نقل الإحالة إلى مستشفى الملك فهد</td>
      </tr>
    </table>
  </div>

  <div class="section">
    <h3>✅ الإحالات المقبولة</h3>
    <table border="1" width="100%" cellpadding="10">
      <tr>
        <th>رقم الإحالة</th>
        <th>اسم المريض</th>
        <th>نوع الإحالة</th>
        <th>الحالة</th>
      </tr>
      <tr>
        <td>98765</td>
        <td>سارة خالد</td>
        <td>تنويم</td>
        <td><span class="badge green">تم القبول</span></td>
      </tr>
    </table>
  </div>

</body>
</html>
<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <title>إعدادات النظام</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <h2>⚙️ إعدادات النظام</h2>

  <div class="section">
    <h3>🔐 قفل الشاشة</h3>
    <button onclick="lockScreen()">قفل الآن</button>
  </div>

  <div class="section">
    <h3>🔁 استعادة الحساب</h3>
    <input type="text" placeholder="البريد الإلكتروني أو اسم المستخدم">
    <button>🔎 استعادة الحساب</button>
  </div>

  <div class="section">
    <h3>🔒 تغيير كلمة المرور</h3>
    <input type="password" placeholder="كلمة المرور الحالية">
    <input type="password" placeholder="كلمة المرور الجديدة">
    <input type="password" placeholder="تأكيد كلمة المرور">
    <button>✅ تغيير</button>
  </div>

  <div class="section">
    <h3>👥 صلاحيات المستخدمين</h3>
    <select id="userSelect">
      <option>مستخدم 1</option>
      <option>مستخدم 10</option>
    </select>
    <p>💡 مستخدم 1 يشوف فقط صفحة الرد – البقية يشوفوا الكل ماعدا الرئيسية</p>
    <button>💾 حفظ الصلاحيات</button>
  </div>

  <script>
    function lockScreen() {
      alert("تم قفل الشاشة مؤقتًا 🔒");
      // هنا تقدر تحط كود تحويل لصفحة قفل وهمية
    }
  </script>

</body>
</html>
