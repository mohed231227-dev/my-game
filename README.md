
# لعبة الكرة القافزة — حزمة المشروع

هذه الحزمة تحتوي على ملف `index.html` جاهز، وأصوات SFX صغيرة في `assets/sfx/`، وملف قواعد Firestore، ودليل تشغيل.

---

## محتويات الحزمة
- `index.html` — صفحة اللعبة (HTML + JS) مع دعم Firebase (إعدادات placeholder).
- `assets/sfx/*.wav` — أصوات قصيرة (coin/jump/buy/error/shield/revive).
- `firestore.rules` — قواعد مقترحة لقاعدة Firestore.
- هذا الملف README.

---

## خطوات سريعة لتشغيل المشروع محليًا (مختبر)
1. فكّ الضغط عن `game_project.zip` أو استخدم المجلد كما هو.
2. افتح تيرمنال في مجلد `game_project` ثم شغّل سيرفر HTTP بسيط:

   ```bash
   # Python 3
   python -m http.server 8000
   ```

3. افتح المتصفح واذهب إلى: `http://localhost:8000/index.html`

> ملاحظة: لتشغيل تسجيل الدخول عبر Firebase (Google/email)، من الأفضل رفع المشروع إلى موقع HTTPS (Netlify / GitHub Pages) لأن بعض ميزات OAuth تعمل أفضل على نطاقات مرخصة. لكن عادة `signInWithPopup` يعمل على `http://localhost` أثناء التطوير.

---

## كيفية إعداد Firebase (مرة واحدة)
1. ادخل إلى [Firebase Console](https://console.firebase.google.com). cite{firebase_auth}
2. أنشئ مشروع جديد.
3. فعّل Authentication:
   - اذهب إلى **Authentication → Sign-in method**.
   - فعّل **Email/Password** و**Google**. cite{firebase_email}
4. فعّل **Firestore** (Cloud Firestore) وأنشئ قاعدة بيانات في الوضع "المحمي" ثم استخدم قواعد التشغيل الموضوعة في `firestore.rules`. cite{firestore_rules}
5. احصل على إعدادات `firebaseConfig` من **Project settings → General → Your apps → Firebase SDK snippet**، وانسخ القيم إلى `index.html` مكان التعليقات `REPLACE_*`.

قواعد Firestore الموصى بها موجودة في `firestore.rules`. الصقها في قسم القواعد في Console ثم انشر.

---

## النشر على الإنترنت (اختياري — موصى به لتفعيل OAuth بثبات)
- **Netlify**: يمكنك رفع مجلد المشروع بالسحب والإفلات (Drag & Drop) في لوحة Netlify أو ربط مستودع GitHub. دليلك: مدونة Netlify. cite{netlify}
- **GitHub Pages**: أنشئ repo جديد، ادفع الملفات، ثم فعّل GitHub Pages من إعدادات المستودع. cite{gh_pages}

---

## ملاحظات عملية
- استبدل قيم `firebaseConfig` في `index.html`.
- الصوتيات المضمنة صغيرة ومبسطة؛ يمكنك استبدالها بملفات MP3/OGG أفضل في `assets/sfx/`.
- قواعد Firestore تمنع المستخدم من الوصول لبيانات غيره — ملفات `firestore.rules` جاهزة للاستخدام.
- إذا أردت، أجهز لك ZIP محسّن للنشر على Netlify مع ملف `netlify.toml` وإرشادات رفع جاهزة.

---

## مصادر رسمية للقراءة
- Firebase Auth (Email/Password) — https://firebase.google.com/docs/auth/web/password-auth. cite{firebase_email}
- Firebase Google Sign-In — https://firebase.google.com/docs/auth/web/google-signin. cite{firebase_google}
- Firestore Security Rules — https://firebase.google.com/docs/firestore/security/get-started. cite{firestore_rules}
- نشر على Netlify — https://www.netlify.com/blog/2016/10/27/a-step-by-step-guide-deploying-a-static-site-or-single-page-app/. cite{netlify}
- GitHub Pages — https://pages.github.com/. cite{gh_pages}

