<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>توجيه إلى التطبيق</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background: #f5f7ff;
            direction: rtl;
        }
        .container {
            text-align: center;
            padding: 20px;
            background: white;
            border-radius: 20px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
            max-width: 400px;
        }
        .logo {
            width: 80px;
            height: 80px;
            margin-bottom: 20px;
        }
        h2 {
            color: #1A6DFF;
            margin-bottom: 10px;
        }
        p {
            color: #555;
            margin-bottom: 20px;
        }
        .spinner {
            border: 4px solid #f3f3f3;
            border-top: 4px solid #1A6DFF;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            animation: spin 1s linear infinite;
            margin: 0 auto 20px;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        .button {
            background: #1A6DFF;
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 30px;
            font-size: 16px;
            cursor: pointer;
            text-decoration: none;
            display: inline-block;
        }
        .button:hover {
            background: #0047CC;
        }
    </style>
</head>
<body>
    <div class="container">
        <img src="https://your-domain.com/logo.png" alt="صنايعية" class="logo" onerror="this.style.display='none'">
        <h2>صنايعية</h2>
        <p>جاري فتح التطبيق...</p>
        <div class="spinner"></div>
        <p>إذا لم يتم فتح التطبيق تلقائياً، اضغط على الزر أدناه.</p>
        <a href="https://play.google.com/store/apps/details?id=com.sani3ia.app" class="button">تحميل التطبيق من المتجر</a>
    </div>

    <script>
        // استخراج نوع المحتوى (post أو product) والمعرف من الرابط
        const path = window.location.pathname; // مثلاً /post/123
        const segments = path.split('/').filter(s => s);
        const type = segments[0]; // "post" أو "product"
        const id = segments[1];   // المعرف

        // رابط التطبيق العميق
        const deepLink = `snae3ya://${type}/${id}`;

        // محاولة فتح التطبيق مباشرة (Intent على Android)
        // على Android 6+، هذه الطريقة تعمل إذا كان التطبيق مثبتاً
        window.location.href = deepLink;

        // إذا لم يفتح التطبيق خلال 2.5 ثانية، يتم توجيه المستخدم إلى المتجر
        setTimeout(function() {
            window.location.href = "https://play.google.com/store/apps/details?id=com.sani3ia.app";
        }, 2500);
    </script>
</body>
</html>
