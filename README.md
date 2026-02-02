
# 🌟 Flutter & Dart – COMPLETE STUDY GUIDE

### 🚀 From ZERO to REAL Applications

> 📌 **README.md تعليمي شامل – للدراسة والمراجعة والاحتراف**

---

## 🧠 الفكرة العامة (اقرأها أولًا)

Flutter = بناء تطبيق كامل
من **Widgets صغيرة**
مركبة فوق بعض
وكل شيء يتحكم فيه **Dart**

> ✨ **كل شيء في Flutter هو Widget**

---

# 🟥 1) Dart – الأساسيات (لغة البرمجة)

## 1️⃣ ما هي Dart؟

* لغة من Google
* Strongly Typed
* Null Safe
* سريعة
* أساس Flutter

---

## 2️⃣ أول برنامج Dart

```dart
void main() {
  print("Hello World");
}
```

* `main()` نقطة البداية
* `print` للطباعة

---

## 3️⃣ المتغيرات (Variables)

```dart
int age = 21;
double gpa = 3.5;
String name = "Tareq";
bool isStudent = true;
```

---

## 4️⃣ var / final / const

```dart
var x = 10;        // Dart يحدد النوع
final y = 20;      // ثابت وقت التشغيل
const z = 30;      // ثابت وقت الترجمة
```

---

## 5️⃣ Null Safety (مهم جدًا)

```dart
String? title;        // ممكن null
String name = "Ali";  // لا يقبل null
```

### أدوات التعامل مع null:

```dart
title ?? "Default";   // بديل
title!;               // تأكيد
```

---

## 6️⃣ Operators

* حسابية: `+ - * / ~/ %`
* مقارنة: `== != > <`
* منطقية: `&& || !`

---

## 7️⃣ الشروط (Conditions)

```dart
if (age >= 18) {
  print("Adult");
} else {
  print("Minor");
}
```

### Ternary

```dart
age >= 18 ? "Adult" : "Minor";
```

---

## 8️⃣ Loops

```dart
for (int i = 0; i < 5; i++) {}
while (x < 10) {}
```

---

## 9️⃣ Functions

```dart
int add(int a, int b) {
  return a + b;
}
```

### Arrow function

```dart
int add(int a, int b) => a + b;
```

---

## 🔟 Parameters

### Positional

```dart
void f(int a, int b) {}
```

### Optional

```dart
void f(int a, [int b = 0]) {}
```

### Named

```dart
void f({required String name, int age = 0}) {}
```

---

# 🟥 2) Collections – البيانات

## 1️⃣1️⃣ List

```dart
List<int> nums = [1, 2, 3];
```

---

## 1️⃣2️⃣ Set (بدون تكرار)

```dart
Set<int> s = {1, 2, 2}; // {1,2}
```

---

## 1️⃣3️⃣ Map (Key / Value)

```dart
Map<String, int> scores = {
  "Ali": 90,
};
```

---

## 1️⃣4️⃣ List Methods

```dart
nums.map((e) => e * 2);
nums.where((e) => e.isEven);
nums.reduce((a, b) => a + b);
```

---

# 🟥 3) OOP – البرمجة الكائنية

## 1️⃣5️⃣ Class

```dart
class Student {
  final String name;
  Student(this.name);
}
```

---

## 1️⃣6️⃣ Inheritance

```dart
class Person {}
class Student extends Person {}
```

---

## 1️⃣7️⃣ Override

```dart
@override
Widget build(BuildContext context) {}
```

---

# 🟥 4) Flutter – البداية الحقيقية

## 1️⃣8️⃣ تشغيل التطبيق

```dart
void main() {
  runApp(MyApp());
}
```

---

## 1️⃣9️⃣ MaterialApp

```dart
MaterialApp(
  home: HomeScreen(),
);
```

---

## 2️⃣0️⃣ Stateless vs Stateful

### StatelessWidget

* ثابت
* بدون تغيير

### StatefulWidget

* متغير
* فيه State + setState

---

## 2️⃣1️⃣ setState()

```dart
setState(() {
  counter++;
});
```

* يغير البيانات
* يعيد رسم الشاشة

---

## 2️⃣2️⃣ build()

* ترسم UI
* تُستدعى كثير
* ❌ لا async

---

## 2️⃣3️⃣ BuildContext

* موقعك في Widget Tree
* يستخدم مع:

  * Navigator
  * Theme
  * MediaQuery

---

# 🟥 5) Layout – بناء الواجهة

## 2️⃣4️⃣ Scaffold

```dart
Scaffold(
  appBar: AppBar(),
  body: ...
);
```

---

## 2️⃣5️⃣ Container

* لون
* حجم
* Padding
* Margin

```dart
Container(
  color: Colors.blue,
  padding: EdgeInsets.all(16),
);
```

---

## 2️⃣6️⃣ SizedBox

```dart
SizedBox(height: 20);
```

---

## 2️⃣7️⃣ Column & Row

* Column ⬇
* Row ➡

### Main / Cross Axis

| Widget | Main  | Cross |
| ------ | ----- | ----- |
| Column | عمودي | أفقي  |
| Row    | أفقي  | عمودي |

---

## 2️⃣8️⃣ Expanded / Flexible

* تقسيم المساحة
* يعمل على Main Axis

---

## 2️⃣9️⃣ Stack

* Widgets فوق بعض

---

# 🟥 6) القوائم (Lists UI)

## 3️⃣0️⃣ ListView

* Scroll
* عناصر كثيرة

---

## 3️⃣1️⃣ ListView.builder

```dart
itemBuilder: (context, index) {}
```

* `index` = رقم العنصر

---

## 3️⃣2️⃣ ListTile

* leading
* title
* subtitle
* trailing

---

## 3️⃣3️⃣ Card

* شكل جاهز
* ظل
* حواف

---

# 🟥 7) الأزرار & Callbacks

## 3️⃣4️⃣ Buttons

```dart
ElevatedButton(
  onPressed: myFunction,
);
```

📌 الويدجت **ينادي الدالة فقط**

---

# 🟥 8) Navigation (شاشتين)

## 3️⃣5️⃣ فتح شاشة

```dart
Navigator.push(...)
```

## 3️⃣6️⃣ رجوع

```dart
Navigator.pop(context);
```

---

# 🟥 9) الألوان 🎨

## 3️⃣7️⃣ Material Colors

```dart
Colors.red.shade700
```

* 50 فاتح
* 900 غامق

---

# 🟥 🔟 Async + API

## 3️⃣8️⃣ Future / async

```dart
Future<int> load() async {}
```

---

## 3️⃣9️⃣ HTTP Request

```dart
http.get(Uri.parse(url));
```

---

## 4️⃣0️⃣ JSON Decode

```dart
json.decode(response.body);
```

---

## 4️⃣1️⃣ Model Class

```dart
factory Post.fromJson(Map json) {}
```

---

## 4️⃣2️⃣ FutureBuilder

* Loading
* Error
* Data

---

## 🟥 11) الصور 🖼️

### API Image

```dart
Image.network(url);
```

### Asset Image

```dart
Image.asset("assets/images/logo.png");
```

---

## 🟥 12) التخزين المحلي

## 4️⃣3️⃣ SharedPreferences

```dart
prefs.setDouble("balance", 500);
```

---

## 🟥 13) بدون StatefulWidget

## 4️⃣4️⃣ بدائل

* StatefulBuilder
* ValueNotifier
* FutureBuilder
* StreamBuilder

---

## ❌ 14) أخطاء شائعة

* async داخل build
* نسيان setState
* ListView داخل Column بدون Expanded
* null بدون ?

---

## ✅ 15) النتيجة النهائية

بعد هذا الملف:

* تفهم Flutter من الصفر
* تبني UI كامل
* تتعامل مع API
* تعرض صور
* تخزن بيانات
* تعمل Navigation
* تكتب كود نظيف

---

## 📌 هذا الملف مناسب لـ:

* 📚 الدراسة
* 🧠 المراجعة
* 🧪 التدريب
* 🧑‍💻 GitHub README
* 🎓 الامتحانات

---

إذا بدك الخطوة التالية:

* 🔥 Roadmap احتراف Flutter
* 🔥 مشاريع تدريبية
* 🔥 تحويله PDF
* 🔥 تقسيمه Modules

احكيلي وأنا أكمل معك 👌
