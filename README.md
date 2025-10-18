# JODN Dashboard - لوحة تحكم جودن

## 🎯 مشروع مستقل تماماً

هذا المشروع **مستقل بالكامل** ويمكن نقله لأي مكان آخر والعمل بدون مشاكل.

## 📦 المتطلبات

- Node.js 16+
- npm أو yarn

## 🚀 التشغيل

### 1. تثبيت الاعتماديات
```bash
npm install
```

### 2. تشغيل البيئة التطويرية
```bash
npm run dev
```

### 3. بناء المشروع للإنتاج
```bash
npm run build
```

## 📁 البنية

```
dashboard/
├── src/
│   ├── components/     # المكونات
│   ├── pages/         # الصفحات
│   ├── stores/        # Pinia stores
│   ├── composables/   # Vue composables
│   ├── router/        # Vue Router
│   └── assets/        # الأصول (CSS, images)
├── public/            # الملفات الثابتة
├── package.json       # الاعتماديات
├── vite.config.js     # إعدادات Vite
└── tailwind.config.js # إعدادات Tailwind
```

## ⚙️ إعدادات النقل لمشروع آخر

### إذا أردت نقل المشروع:

1. **انسخ المجلد كاملاً**
2. **عدّل `vite.config.js`:**
   ```javascript
   base: command === 'build' ? '/اسم-مشروعك-الجديد/' : '/'
   ```
   أو اجعلها `/` فقط إذا كان في الـ root

3. **عدّل `package.json`:**
   - غيّر `name`
   - غيّر `description`

4. **نفّذ:**
   ```bash
   npm install
   npm run dev
   ```

## ✅ الاستقلالية الكاملة

- ✅ جميع الـ dependencies منفصلة
- ✅ لا يوجد imports من خارج المجلد
- ✅ جميع الـ assets داخلية
- ✅ Configuration مستقل بالكامل
- ✅ يعمل standalone بدون أي ملفات خارجية

## 🌐 المميزات

- 🌙 Dark Mode
- 🌍 متعدد اللغات (عربي/إنجليزي)
- 📱 Responsive Design
- 🎨 Tailwind CSS
- 📊 Charts.js للرسوم البيانية
- 🔄 Vue Router
- 💾 Pinia State Management

## 📝 ملاحظات

- المشروع يستخدم Vue 3 + Vite
- التصميم RTL/LTR متوافق
- جميع المسارات نسبية باستخدام `@/` alias
