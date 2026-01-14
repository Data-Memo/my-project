# المرحلة الأولى: بناء التطبيق (Build Stage)
# نستخدم صورة maven الرسمية لبناء المشروع
FROM maven:3.8.4-openjdk-17 AS build
WORKDIR /app

# 1. نسخ ملف الإعدادات أولاً لتحميل المكتبات (لجعل البناء أسرع في المرات القادمة)
COPY pom.xml .
RUN mvn dependency:go-offline

# 2. نسخ مجلد الكود المصدري بالكامل
COPY src ./src

# 3. بناء المشروع وتجهيز ملف الـ JAR (تجاهل الاختبارات لتسريع العملية)
RUN mvn clean package -DskipTests

# المرحلة الثانية: التشغيل (Runtime Stage)
# نستخدم نسخة أصغر من جافا فقط لتشغيل التطبيق وتقليل مساحة الحاوية
FROM openjdk:17-jdk-slim
WORKDIR /app

# 4. نسخ ملف الـ JAR الناتج من مرحلة البناء باستخدام "*" للتعميم
# وإعادة تسميته بـ app.jar ليكون الاسم ثابتاً وسهلاً
COPY --from=build /app/target/*.jar app.jar

# 5. تنبيه الحاوية لاستخدام المنفذ 8080 (أو المنفذ الذي يستخدمه تطبيقك)
EXPOSE 8080

# 6. أمر تشغيل التطبيق
CMD ["java", "-jar", "app.jar"]