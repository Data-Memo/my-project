# ملاحظات تقنية (Technical Notes)

## معلومات البيئة
- **اللغة:** Java 17
- **الإطار الرسومي:** JavaFX
- **أداة البناء:** Maven

## استخدام دوكر (Docker)
- تم استخدام **Multi-stage build** لتقليل حجم الصورة النهائية.
- المرحلة الأولى (Build): تستخدم `maven:3.8.4-openjdk-17` لبناء ملف الـ JAR.
- المرحلة الثانية (Runtime): تستخدم `openjdk:17-jdk-slim` لتشغيل التطبيق.

## تعليمات التشغيل
1. بناء الصورة: `docker build -t javafx-app .`
2. تشغيل الحاوية: `docker run -it javafx-app`