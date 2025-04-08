<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>تجربتي قبل أشتري - TryBeforeU</title>
  <style>
    body {
      font-family: 'Tahoma', sans-serif;
      background-color: #f4f4f4;
      margin: 0;
      padding: 0;
    }
    header {
      background-color: #4caf50;
      color: white;
      padding: 1rem;
      text-align: center;
    }
    .container {
      max-width: 800px;
      margin: 3rem auto;
      background: white;
      padding: 2rem;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    h2 {
      text-align: center;
    }
    input[type="text"], input[type="password"] {
      width: 100%;
      padding: 0.75rem;
      margin-bottom: 1rem;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    .btn {
      background-color: #4caf50;
      color: white;
      border: none;
      padding: 0.5rem 1rem;
      cursor: pointer;
      border-radius: 5px;
      margin-top: 0.5rem;
    }
    .btn:hover {
      background-color: #45a049;
    }
    .link {
      text-align: center;
      margin-top: 1rem;
    }
    .link a {
      color: #4caf50;
      text-decoration: none;
      cursor: pointer;
    }
    .hidden {
      display: none;
    }
    .product {
      border-bottom: 1px solid #ddd;
      padding: 1rem 0;
    }
    .product:last-child {
      border: none;
    }
    .testers {
      background: #f9f9f9;
      padding: 1rem;
      border-radius: 5px;
      margin-top: 1rem;
    }
    .back-btn {
      display: block;
      margin-top: 1rem;
      color: #4caf50;
      text-decoration: underline;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <header>
    <h1>تجربتي قبل أشتري - TryBeforeU</h1>
  </header>

  <div class="container" id="login-page">
    <h2>تسجيل الدخول</h2>
    <form onsubmit="login(event)">
      <input type="text" id="login-username" placeholder="اسم المستخدم" required />
      <input type="password" id="login-password" placeholder="كلمة المرور" required />
      <button type="submit" class="btn">دخول</button>
    </form>
    <div class="link">
      <p>ليس لديك حساب؟ <a onclick="showRegister()">سجل الآن</a></p>
    </div>
  </div>

  <div class="container hidden" id="register-page">
    <h2>تسجيل حساب جديد</h2>
    <form onsubmit="register(event)">
      <input type="text" id="reg-username" placeholder="اسم المستخدم" required />
      <input type="password" id="reg-password" placeholder="كلمة المرور" required />
      <button type="submit" class="btn">تسجيل</button>
    </form>
    <div class="link">
      <p>هل لديك حساب؟ <a onclick="showLogin()">سجّل الدخول</a></p>
    </div>
  </div>

  <div class="container hidden" id="products-page">
    <h2>المنتجات المتوفرة:</h2>
    <div class="product">
      <h3>ماكينة قهوة ديلونجي</h3>
      <p>ماكينة لتحضير القهوة الإيطالية.</p>
      <button class="btn" onclick="openDetails('coffee')">عرض التفاصيل</button>
    </div>
    <div class="product">
      <h3>جهاز بخار للوجه</h3>
      <p>مناسب للعناية بالبشرة.</p>
      <button class="btn" onclick="openDetails('steam')">عرض التفاصيل</button>
    </div>
  </div>

  <div class="container hidden" id="product-details">
    <div id="product-info"></div>
    <div class="testers">
      <h3>المجربون:</h3>
      <div id="testers-list"></div>
    </div>
    <span class="back-btn" onclick="showProducts()">⬅ رجوع إلى المنتجات</span>
  </div>

  <script>
    function showLogin() {
      document.getElementById('login-page').classList.remove('hidden');
      document.getElementById('register-page').classList.add('hidden');
    }

    function showRegister() {
      document.getElementById('login-page').classList.add('hidden');
      document.getElementById('register-page').classList.remove('hidden');
    }

    function login(event) {
      event.preventDefault();
      const username = document.getElementById('login-username').value;
      alert('مرحباً ' + username + '! تم تسجيل دخولك بنجاح.');
      showProducts();
    }

    function register(event) {
      event.preventDefault();
      const username = document.getElementById('reg-username').value;
      alert('مرحباً ' + username + '! تم إنشاء حسابك بنجاح.');
      showProducts();
    }

    function showProducts() {
      document.getElementById('login-page').classList.add('hidden');
      document.getElementById('register-page').classList.add('hidden');
      document.getElementById('products-page').classList.remove('hidden');
      document.getElementById('product-details').classList.add('hidden');
    }

    function openDetails(productId) {
      document.getElementById('products-page').classList.add('hidden');
      document.getElementById('product-details').classList.remove('hidden');

      let info = '';
      let testers = '';

      if (productId === 'coffee') {
        info = '<h2>ماكينة قهوة ديلونجي</h2><p>أفضل ماكينة منزلية لعشاق القهوة.</p>';
        testers = '<p><strong>أحمد - جدة</strong><br> "ماكينة ممتازة وتستاهل السعر."<br><button class="btn">راسل أحمد</button></p>';
      } else if (productId === 'steam') {
        info = '<h2>جهاز بخار للوجه</h2><p>جهاز للعناية ببشرة الوجه يعمل بالبخار.</p>';
        testers = '<p><strong>سارة - الرياض</strong><br> "ريحني كثير، حسيت ببشرتي ناعمة من أول استخدام."<br><button class="btn">راسل سارة</button></p>';
      }

      document.getElementById('product-info').innerHTML = info;
      document.getElementById('testers-list').innerHTML = testers;
    }
  </script>
</body>
</html>
