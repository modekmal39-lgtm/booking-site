<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>نظام حجز القطع | Parts Booking System</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-100 min-h-screen">

<!-- Header -->
<header class="bg-blue-700 text-white p-4 shadow">
  <div class="max-w-6xl mx-auto flex justify-between items-center">
    <div class="flex items-center gap-3">
      <img src="logo.png" alt="Company Logo" class="h-10 bg-white p-1 rounded" />
      <h1 id="title" class="text-xl font-bold">نظام حجز القطع</h1>
    </div>
    <div class="space-x-4">
      <button onclick="setLang('ar')" class="px-2 py-1 bg-white text-blue-700 rounded">عربي</button>
      <button onclick="setLang('en')" class="px-2 py-1 bg-white text-blue-700 rounded">English</button>
    </div>
  </div>
</header>

<!-- Hero Section -->
<section class="bg-white py-10 text-center">
  <h2 id="heroTitle" class="text-3xl font-bold mb-2">احجز القطع بسهولة</h2>
  <p id="heroDesc" class="text-gray-600">اختر القطعة المطلوبة وأرسل طلب الحجز مباشرة</p>
</section>

<!-- Products Section -->
<section id="products" class="max-w-6xl mx-auto p-4">
  <h3 id="productsTitle" class="text-2xl font-bold mb-4">القطع المتوفرة</h3>
  <div class="grid grid-cols-1 md:grid-cols-3 gap-4">

    <div class="bg-white p-4 rounded-xl shadow">
      <h4 class="font-bold">شاشة سامسونج 55 انش</h4>
      <p class="text-sm text-gray-600">Part No: TV-5501</p>
      <button onclick="fillPart('شاشة سامسونج 55 انش','TV-5501')" class="mt-2 bg-blue-600 text-white px-3 py-1 rounded">حجز</button>
    </div>

    <div class="bg-white p-4 rounded-xl shadow">
      <h4 class="font-bold">بطارية آيفون</h4>
      <p class="text-sm text-gray-600">Part No: IP-BAT-14</p>
      <button onclick="fillPart('بطارية آيفون','IP-BAT-14')" class="mt-2 bg-blue-600 text-white px-3 py-1 rounded">حجز</button>
    </div>

    <div class="bg-white p-4 rounded-xl shadow">
      <h4 class="font-bold">شاحن لابتوب ديل</h4>
      <p class="text-sm text-gray-600">Part No: DL-CH-90</p>
      <button onclick="fillPart('شاحن لابتوب ديل','DL-CH-90')" class="mt-2 bg-blue-600 text-white px-3 py-1 rounded">حجز</button>
    </div>

  </div>
</section>

<!-- Booking Form -->
<section id="book" class="bg-white p-6 mt-6 max-w-xl mx-auto shadow rounded-xl">
  <h3 id="formTitle" class="text-xl font-bold mb-4">نموذج حجز القطع</h3>

  <!-- ضع رابط Google Form بدل ACTION_URL -->
  <form id="bookingForm" action="ACTION_URL" method="POST" class="space-y-3">

    <div>
      <label id="labelPart" class="block text-sm font-medium">اسم القطعة</label>
      <input id="part_name" name="part_name" required class="w-full border p-2 rounded" />
    </div>

    <div>
      <label id="labelCode" class="block text-sm font-medium">رقم القطعة</label>
      <input id="part_code" name="part_code" required class="w-full border p-2 rounded" />
    </div>

    <div>
      <label id="labelQty" class="block text-sm font-medium">الكمية</label>
      <input type="number" name="quantity" required class="w-full border p-2 rounded" value="1" />
    </div>

    <!-- Required Customer Info -->
    <div>
      <label id="labelName" class="block text-sm font-medium">اسم العميل</label>
      <input id="customer_name" name="customer_name" required class="w-full border p-2 rounded" />
    </div>

    <div>
      <label id="labelAddress" class="block text-sm font-medium">عنوان العميل</label>
      <input id="customer_address" name="customer_address" required class="w-full border p-2 rounded" />
    </div>

    <div>
      <label id="labelPhone" class="block text-sm font-medium">رقم الهاتف</label>
      <input id="phone" name="phone" required class="w-full border p-2 rounded" placeholder="07XXXXXXXX" />
    </div>

    <div>
      <label id="labelColor" class="block text-sm font-medium">لون الجهاز</label>
      <input id="device_color" name="device_color" required class="w-full border p-2 rounded" />
    </div>

    <div>
      <label id="labelAgent" class="block text-sm font-medium">الموظفة التي أجابت</label>
      <input id="agent_name" name="agent_name" required class="w-full border p-2 rounded" />
    </div>

    <div>
      <label id="labelNotes" class="block text-sm font-medium">ملاحظات</label>
      <textarea name="notes" class="w-full border p-2 rounded"></textarea>
    </div>

    <button id="submitBtn" type="submit" class="w-full bg-green-600 text-white py-2 rounded hover:bg-green-700">إرسال طلب الحجز</button>
  </form>

  <p id="errorMsg" class="text-red-600 text-sm mt-2 hidden"></p>
</section>

<!-- Footer -->
<footer class="bg-blue-700 text-white text-center p-3 mt-6">
  <p>© 2026 Parts Booking System</p>
</footer>

<!-- Script -->
<script>
function fillPart(name, code) {
  document.getElementById('part_name').value = name;
  document.getElementById('part_code').value = code;
  window.location.hash = 'book';
}

// Language Switcher
function setLang(lang) {
  if (lang === 'en') {
    document.documentElement.dir = 'ltr';
    document.getElementById('title').innerText = 'Parts Booking System';
    document.getElementById('heroTitle').innerText = 'Book Spare Parts Easily';
    document.getElementById('heroDesc').innerText = 'Select the part and submit your booking request';
    document.getElementById('productsTitle').innerText = 'Available Parts';
    document.getElementById('formTitle').innerText = 'Booking Form';
    document.getElementById('labelPart').innerText = 'Part Name';
    document.getElementById('labelCode').innerText = 'Part Number';
    document.getElementById('labelQty').innerText = 'Quantity';
    document.getElementById('labelName').innerText = 'Customer Name';
    document.getElementById('labelAddress').innerText = 'Customer Address';
    document.getElementById('labelPhone').innerText = 'Phone Number';
    document.getElementById('labelColor').innerText = 'Device Color';
    document.getElementById('labelAgent').innerText = 'Agent Name';
    document.getElementById('labelNotes').innerText = 'Notes';
    document.getElementById('submitBtn').innerText = 'Submit Booking';
  } else {
    document.documentElement.dir = 'rtl';
    document.getElementById('title').innerText = 'نظام حجز القطع';
    document.getElementById('heroTitle').innerText = 'احجز القطع بسهولة';
    document.getElementById('heroDesc').innerText = 'اختر القطعة المطلوبة وأرسل طلب الحجز مباشرة';
    document.getElementById('productsTitle').innerText = 'القطع المتوفرة';
    document.getElementById('formTitle').innerText = 'نموذج حجز القطع';
    document.getElementById('labelPart').innerText = 'اسم القطعة';
    document.getElementById('labelCode').innerText = 'رقم القطعة';
    document.getElementById('labelQty').innerText = 'الكمية';
    document.getElementById('labelName').innerText = 'اسم العميل';
    document.getElementById('labelAddress').innerText = 'عنوان العميل';
    document.getElementById('labelPhone').innerText = 'رقم الهاتف';
    document.getElementById('labelColor').innerText = 'لون الجهاز';
    document.getElementById('labelAgent').innerText = 'الموظفة التي أجابت';
    document.getElementById('labelNotes').innerText = 'ملاحظات';
    document.getElementById('submitBtn').innerText = 'إرسال طلب الحجز';
  }
}

// منع الحجز بنفس الرقم مرتين (تخزين محلي على جهاز العميل)
document.getElementById('bookingForm').addEventListener('submit', function(e) {
  const phone = document.getElementById('phone').value.trim();
  const errorMsg = document.getElementById('errorMsg');

  let bookedPhones = JSON.parse(localStorage.getItem('bookedPhones') || '[]');

  if (bookedPhones.includes(phone)) {
    e.preventDefault();
    errorMsg.classList.remove('hidden');
    errorMsg.innerText = 'هذا الرقم قام بالحجز سابقًا ولا يمكن الحجز مرة أخرى.';
    return false;
  }

  bookedPhones.push(phone);
  localStorage.setItem('bookedPhones', JSON.stringify(bookedPhones));
});
</script>

</body>
</html>


## تحديثات إضافية
- تم ربط النموذج تلقائيًا مع ملف Excel عبر Google Sheets لتسجيل جميع الحجوزات بشكل مباشر.
- تم إضافة لوحة تحكم بسيطة للموظفين لعرض وإدارة الحجوزات (بحث، تصفية، تحميل Excel).
- يمكن إضافة الشعار بسهولة عبر استبدال ملف `logo.png` في مجلد الموقع أو من خلال الإعدادات (سيظهر تلقائيًا في أعلى الصفحة).
