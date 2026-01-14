FROM openjdk:17-jdk-slim
WORKDIR /app
# هذا الأمر ينسخ كل شيء لضمان عدم ضياع الملفات
COPY . . 
# ابحث عن أي ملف ينتهي بـ .jar وقم بتشغيله
CMD ["sh", "-c", "java -jar $(find . -name '*.jar' | head -n 1)"]