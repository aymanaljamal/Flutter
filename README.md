# 🌟 Flutter & Dart – COMPLETE STUDY GUIDE

### 🚀 From ZERO to REAL Applications

> 📌 **دليل شامل ومفصّل للدراسة والمراجعة والاحتراف**

---

## 📑 جدول المحتويات (Table of Contents)

| القسم | الموضوع | الصفحة |
|------|---------|
| 1 | Dart - الأساسيات |
| 2 | Collections - البيانات |
| 3 | OOP - البرمجة الكائنية |
| 4 | Flutter - البداية |
| 5 | Layout - بناء الواجهة |
| 6 | Lists - القوائم |
| 7 | Buttons - الأزرار |
| 8 | Navigation - التنقل |
| 9 | Colors & Themes |
| 10 | Async + API |
| 11 | Images - الصور |
| 12 | Storage - التخزين |
| 13 | State Management |
| 14 | Advanced Widgets |
| 15 | Best Practices |

---

## 🧠 الفكرة العامة (اقرأها أولًا)

Flutter = بناء تطبيق كامل من **Widgets صغيرة** مركبة فوق بعض وكل شيء يتحكم فيه **Dart**

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

### 📊 جدول أنواع البيانات:

| النوع | الاستخدام | مثال |
|------|----------|------|
| `int` | أرقام صحيحة | `25` |
| `double` | أرقام عشرية | `3.14` |
| `String` | نصوص | `"Hello"` |
| `bool` | صح/خطأ | `true` |
| `dynamic` | أي نوع | `var x` |

---

## 4️⃣ var / final / const

```dart
var x = 10;        // Dart يحدد النوع
final y = 20;      // ثابت وقت التشغيل
const z = 30;      // ثابت وقت الترجمة
```

### الفرق بين final و const:

| | final | const |
|---|-------|-------|
| متى يتحدد | Runtime | Compile Time |
| مثال | `final now = DateTime.now()` | `const pi = 3.14` |

---

## 5️⃣ Null Safety (مهم جدًا)

```dart
String? title;        // ممكن null
String name = "Ali";  // لا يقبل null

// أمثلة عملية:
String? username;
print(username ?? "Guest");  // إذا null اطبع Guest

String? data = getData();
print(data!.length);  // تأكيد أن data ليست null
```

### أدوات التعامل مع null:

| الأداة | الاستخدام | مثال |
|-------|----------|------|
| `??` | قيمة بديلة | `name ?? "Unknown"` |
| `!` | تأكيد ليس null | `name!` |
| `?.` | استدعاء آمن | `user?.name` |

---

## 6️⃣ Operators

```dart
int sum = 5 + 3;      // 8
int div = 10 ~/ 3;    // 3 (قسمة صحيحة)
int mod = 10 % 3;     // 1 (الباقي)

// مقارنة
bool isEqual = (5 == 5);     // true
bool isGreater = (10 > 5);   // true

// منطقية
bool result = true && false;  // false
bool result2 = true || false; // true
```

---

## 7️⃣ الشروط (Conditions)

```dart
// If-Else
if (age >= 18) {
  print("Adult");
} else if (age >= 13) {
  print("Teenager");
} else {
  print("Child");
}

// Ternary
String status = age >= 18 ? "Adult" : "Minor";

// Switch
switch (grade) {
  case 'A':
    print("Excellent");
    break;
  case 'B':
    print("Good");
    break;
  default:
    print("Keep trying");
}
```

---

## 8️⃣ Loops

```dart
// For Loop
for (int i = 0; i < 5; i++) {
  print(i);  // 0 1 2 3 4
}

// For-in Loop
List<String> names = ["Ali", "Sara", "Omar"];
for (var name in names) {
  print(name);
}

// While
int count = 0;
while (count < 3) {
  print(count);
  count++;
}

// Do-While
int x = 0;
do {
  print(x);
  x++;
} while (x < 3);
```

---

## 9️⃣ Functions

```dart

int add(int a, int b) {
  return a + b;
}

// Arrow function
int multiply(int a, int b) => a * b;

// دالة بدون return
void greet(String name) {
  print("Hello $name");
}

// مثال عملي
String getFullName(String first, String last) {
  return "$first $last";
}

void main() {
  print(add(5, 3));           // 8
  print(multiply(4, 2));      // 8
  greet("Ahmed");             // Hello Ahmed
  print(getFullName("Ali", "Mohammed")); // Ali Mohammed
}
```

---

## 🔟 Parameters

```dart
// 1. Positional (Required)
void sendMessage(String to, String message) {
  print("To: $to, Message: $message");
}
sendMessage("Ahmed", "Hello!");

// 2. Optional Positional
void greet(String name, [String greeting = "Hello"]) {
  print("$greeting $name");
}
greet("Sara");              // Hello Sara
greet("Sara", "Hi");        // Hi Sara

// 3. Named Parameters
void createUser({
  required String name,
  required int age,
  String? city,
}) {
  print("Name: $name, Age: $age, City: $city");
}
createUser(name: "Omar", age: 25, city: "Ramallah");

// 4. Mixed
void register(String email, {required String password, bool rememberMe = false}) {
  print("Email: $email, Remember: $rememberMe");
}
register("test@test.com", password: "123456");
```

---

# 🟥 2) Collections – البيانات

## 1️⃣1️⃣ List

```dart
List<int> numbers = [1, 2, 3, 4, 5];
List<String> fruits = ["Apple", "Banana", "Orange"];

// العمليات الأساسية
numbers.add(6);              // إضافة
numbers.remove(3);           // حذف
numbers[0] = 10;            // تعديل
print(numbers.length);      // الطول
print(numbers.first);       // أول عنصر
print(numbers.last);        // آخر عنصر

// أمثلة عملية
List<String> students = ["Ali", "Sara", "Omar"];
students.insert(1, "Layla");  // إضافة في موقع محدد
students.removeAt(0);         // حذف من موقع
print(students.contains("Sara")); // true
```

---

## 1️⃣2️⃣ Set (بدون تكرار)

```dart
Set<int> uniqueNumbers = {1, 2, 2, 3}; 
print(uniqueNumbers); // {1, 2, 3}

// أمثلة عملية
Set<String> tags = {"flutter", "dart", "mobile"};
tags.add("flutter");  // لن يضاف (موجود)
tags.add("android");  // سيضاف
print(tags.length);   // 4
```

---

## 1️⃣3️⃣ Map (Key / Value)

```dart
Map<String, int> scores = {
  "Ali": 90,
  "Sara": 85,
  "Omar": 78,
};

// العمليات
scores["Ahmed"] = 95;           // إضافة
scores["Ali"] = 92;             // تعديل
scores.remove("Omar");          // حذف
print(scores["Sara"]);          // 85
print(scores.containsKey("Ali")); // true

// مثال عملي: بيانات مستخدم
Map<String, dynamic> user = {
  "name": "Ahmed",
  "age": 25,
  "isStudent": true,
  "gpa": 3.8,
};
print(user["name"]); // Ahmed
```

---

## 1️⃣4️⃣ List Methods (مهمة جدًا)

```dart
List<int> numbers = [1, 2, 3, 4, 5];

// map - تحويل كل عنصر
List<int> doubled = numbers.map((n) => n * 2).toList();
print(doubled); // [2, 4, 6, 8, 10]

// where - فلترة
List<int> evens = numbers.where((n) => n.isEven).toList();
print(evens); // [2, 4]

// reduce - دمج في قيمة واحدة
int sum = numbers.reduce((a, b) => a + b);
print(sum); // 15

// forEach - تنفيذ على كل عنصر
numbers.forEach((n) => print(n));

// any / every
bool hasEven = numbers.any((n) => n.isEven);      // true
bool allPositive = numbers.every((n) => n > 0);   // true

// مثال عملي كامل
List<Map<String, dynamic>> products = [
  {"name": "Phone", "price": 500},
  {"name": "Laptop", "price": 1000},
  {"name": "Tablet", "price": 300},
];

// المنتجات الأغلى من 400
var expensive = products.where((p) => p["price"] > 400).toList();
print(expensive); // Phone, Laptop
```

---

# 🟥 3) OOP – البرمجة الكائنية

## 1️⃣5️⃣ Class

```dart
class Student {
  String name;
  int age;
  
  // Constructor
  Student(this.name, this.age);
  
  // Method
  void study() {
    print("$name is studying");
  }
}

// استخدام
Student s1 = Student("Ali", 20);
s1.study(); // Ali is studying

// Named Constructor
class User {
  String username;
  String email;
  
  User(this.username, this.email);
  
  // Named constructor
  User.guest() : username = "Guest", email = "";
}

User guest = User.guest();

// مثال عملي: Product
class Product {
  final String name;
  final double price;
  final String? description;
  
  Product({
    required this.name,
    required this.price,
    this.description,
  });
  
  void showInfo() {
    print("Product: $name - \$$price");
  }
}

Product p = Product(name: "Phone", price: 599.99);
p.showInfo();
```

---

## 1️⃣6️⃣ Inheritance (الوراثة)

```dart
// Parent Class
class Person {
  String name;
  int age;
  
  Person(this.name, this.age);
  
  void introduce() {
    print("I'm $name, $age years old");
  }
}

// Child Class
class Student extends Person {
  String university;
  
  Student(String name, int age, this.university) : super(name, age);
  
  @override
  void introduce() {
    super.introduce();
    print("I study at $university");
  }
}

// استخدام
Student s = Student("Omar", 22, "Birzeit University");
s.introduce();
// I'm Omar, 22 years old
// I study at Birzeit University
```

---

## 1️⃣7️⃣ Abstract Class & Interface

```dart
// Abstract Class
abstract class Animal {
  void makeSound(); // يجب تطبيقها
  
  void sleep() {    // اختيارية
    print("Sleeping...");
  }
}

class Cat extends Animal {
  @override
  void makeSound() {
    print("Meow!");
  }
}

Cat c = Cat();
c.makeSound(); // Meow!
c.sleep();     // Sleeping...
```

---

# 🟥 4) Flutter – البداية الحقيقية

## 1️⃣8️⃣ تشغيل التطبيق

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'My First App',
      home: HomeScreen(),
    );
  }
}
```

---

## 1️⃣9️⃣ MaterialApp

```dart
MaterialApp(
  title: 'Flutter App',
  theme: ThemeData(
    primarySwatch: Colors.blue,
    brightness: Brightness.light,
  ),
  darkTheme: ThemeData.dark(),
  home: HomeScreen(),
  debugShowCheckedModeBanner: false,
);
```

### خصائص MaterialApp المهمة:

| الخاصية | الوصف |
|---------|-------|
| `home` | الشاشة الرئيسية |
| `theme` | الألوان والستايل |
| `routes` | مسارات التنقل |
| `initialRoute` | المسار الابتدائي |
| `locale` | اللغة |

---

## 2️⃣0️⃣ Stateless vs Stateful

### 📊 جدول المقارنة:

| | StatelessWidget | StatefulWidget |
|---|----------------|----------------|
| **التغيير** | ثابت، لا يتغير | متغير، يتغير |
| **إعادة البناء** | مرة واحدة | عند كل setState |
| **الاستخدام** | UI ثابت | UI ديناميكي |
| **مثال** | نص، أيقونة | عداد، فورم |

### StatelessWidget (ثابت):

```dart
class WelcomeScreen extends StatelessWidget {
  final String title;
  
  WelcomeScreen({required this.title});
  
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text(title)),
      body: Center(
        child: Text("Welcome!"),
      ),
    );
  }
}
```

### StatefulWidget (متغير):

```dart
class CounterScreen extends StatefulWidget {
  @override
  _CounterScreenState createState() => _CounterScreenState();
}

class _CounterScreenState extends State<CounterScreen> {
  int counter = 0;
  
  void increment() {
    setState(() {
      counter++;
    });
  }
  
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Counter")),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Text("Count: $counter", style: TextStyle(fontSize: 30)),
            SizedBox(height: 20),
            ElevatedButton(
              onPressed: increment,
              child: Text("Add +1"),
            ),
          ],
        ),
      ),
    );
  }
}
```

---

## 2️⃣1️⃣ setState() - مهم جدًا

```dart
void increment() {// ❌ خطأ - التغيير بدون setState
  counter++; // لن يعمل
}

// ✅ صح - استخدام setState
void increment() {
  setState(() {
    counter++; // سيعمل ويعيد رسم الشاشة
  });
}

// مثال عملي: تبديل الألوان
Color bgColor = Colors.white;

void changeColor() {
  setState(() {
    bgColor = bgColor == Colors.white ? Colors.blue : Colors.white;
  });
}
```

### 📌 قواعد setState:

1. يستخدم فقط داخل StatefulWidget
2. يعيد تشغيل build()
3. ضع فقط الكود المتغير داخله
4. ❌ لا تستخدم async داخل setState

---

## 2️⃣2️⃣ build() Method

```dart
@override
Widget build(BuildContext context) {
  // هذه الدالة تُستدعى كثيرًا
  // ❌ لا تضع async هنا
  // ❌ لا تضع عمليات ثقيلة
  
  return Scaffold(
    body: Center(
      child: Text("Hello"),
    ),
  );
}
```

### متى يتم استدعاء build():

* عند أول إنشاء للـ Widget
* عند كل setState()
* عند تغيير الـ Theme
* عند تدوير الشاشة

---

## 2️⃣3️⃣ BuildContext

```dart
void showMessage(BuildContext context) {// استخدامات BuildContext

  // 1. الحصول على Theme
  var theme = Theme.of(context);
  
  // 2. الحصول على حجم الشاشة
  var size = MediaQuery.of(context).size;
  
  // 3. التنقل
  Navigator.push(context, ...);
  
  // 4. إظهار SnackBar
  ScaffoldMessenger.of(context).showSnackBar(
    SnackBar(content: Text("Hello")),
  );
}
```

---

# 🟥 5) Layout – بناء الواجهة

## 2️⃣4️⃣ Scaffold - الهيكل الأساسي

```dart
Scaffold(
  appBar: AppBar(
    title: Text("My App"),
    actions: [
      IconButton(icon: Icon(Icons.search), onPressed: () {}),
      IconButton(icon: Icon(Icons.settings), onPressed: () {}),
    ],
  ),
  body: Center(child: Text("Main Content")),
  floatingActionButton: FloatingActionButton(
    onPressed: () {},
    child: Icon(Icons.add),
  ),
  drawer: Drawer(
    child: ListView(
      children: [
        DrawerHeader(child: Text("Menu")),
        ListTile(title: Text("Home")),
        ListTile(title: Text("Profile")),
      ],
    ),
  ),
  bottomNavigationBar: BottomNavigationBar(
    items: [
      BottomNavigationBarItem(icon: Icon(Icons.home), label: "Home"),
      BottomNavigationBarItem(icon: Icon(Icons.person), label: "Profile"),
    ],
  ),
);
```

### 📊 أجزاء Scaffold:

| الجزء | الوصف |
|-------|-------|
| `appBar` | الشريط العلوي |
| `body` | المحتوى الرئيسي |
| `floatingActionButton` | زر دائري عائم |
| `drawer` | قائمة جانبية |
| `bottomNavigationBar` | شريط سفلي |

---

## 2️⃣5️⃣ Container - الحاوية

```dart
Container(
  width: 200,
  height: 100,
  padding: EdgeInsets.all(16),
  margin: EdgeInsets.symmetric(vertical: 10),
  decoration: BoxDecoration(
    color: Colors.blue,
    borderRadius: BorderRadius.circular(12),
    boxShadow: [
      BoxShadow(
        color: Colors.grey,
        blurRadius: 5,
        offset: Offset(2, 2),
      ),
    ],
  ),
  child: Text("Hello", style: TextStyle(color: Colors.white)),
);
```

### Container Properties:

| الخاصية | الوصف | مثال |
|---------|-------|------|
| `width` | العرض | `200` |
| `height` | الارتفاع | `100` |
| `color` | اللون | `Colors.blue` |
| `padding` | مسافة داخلية | `EdgeInsets.all(16)` |
| `margin` | مسافة خارجية | `EdgeInsets.all(10)` |
| `decoration` | تنسيق متقدم | `BoxDecoration(...)` |

---

## 2️⃣6️⃣ SizedBox - مسافة فارغة

```dart
Column(
  children: [
    Text("First"),
    SizedBox(height: 20),  // مسافة عمودية
    Text("Second"),
    SizedBox(height: 10),
    Text("Third"),
  ],
);

Row(
  children: [
    Text("Left"),
    SizedBox(width: 30),   // مسافة أفقية
    Text("Right"),
  ],
);

// مربع فارغ بحجم معين
SizedBox(
  width: 100,
  height: 100,
  child: Container(color: Colors.red),
);
```

---

## 2️⃣7️⃣ Column & Row

### 📊 جدول Main/Cross Axis:

| Widget | Main Axis | Cross Axis |
|--------|-----------|------------|
| `Column` | عمودي ⬇️ | أفقي ➡️ |
| `Row` | أفقي ➡️ | عمودي ⬇️ |

### Column (عمودي):

```dart
Column(
  mainAxisAlignment: MainAxisAlignment.center,     // عمودي
  crossAxisAlignment: CrossAxisAlignment.start,    // أفقي
  children: [
    Text("Item 1"),
    Text("Item 2"),
    Text("Item 3"),
  ],
);
```

### Row (أفقي):

```dart
Row(
  mainAxisAlignment: MainAxisAlignment.spaceBetween,
  crossAxisAlignment: CrossAxisAlignment.center,
  children: [
    Icon(Icons.star),
    Text("Rating"),
    Text("4.5"),
  ],
);
```

### MainAxisAlignment Options:

| القيمة | الوصف |
|--------|-------|
| `start` | في البداية |
| `end` | في النهاية |
| `center` | في المنتصف |
| `spaceBetween` | مسافات بين العناصر |
| `spaceAround` | مسافات حول العناصر |
| `spaceEvenly` | مسافات متساوية |

---

## 2️⃣8️⃣ Expanded & Flexible

```dart
// Expanded - يأخذ كل المساحة المتاحة
Row(
  children: [
    Container(width: 50, color: Colors.red),
    Expanded(
      child: Container(color: Colors.blue), // يملأ الباقي
    ),
    Container(width: 50, color: Colors.green),
  ],
);

// Expanded مع flex - تقسيم نسبي
Row(
  children: [
    Expanded(flex: 1, child: Container(color: Colors.red)),
    Expanded(flex: 2, child: Container(color: Colors.blue)),  // ضعف الأول
    Expanded(flex: 1, child: Container(color: Colors.green)),
  ],
);

// Flexible - يأخذ حسب الحاجة
Row(
  children: [
    Flexible(
      child: Container(
        width: 1000,  // سيتقلص ليناسب
        color: Colors.orange,
      ),
    ),
  ],
);
```

### Expanded vs Flexible:

| | Expanded | Flexible |
|---|----------|----------|
| المساحة | يأخذ كل المتاح | يأخذ حسب الحاجة |
| الاستخدام | ملء المساحة | تقليص إذا لزم |

---

## 2️⃣9️⃣ Stack - تراكب الويدجت

```dart
Stack(
  children: [
    // الخلفية
    Container(
      width: 300,
      height: 200,
      color: Colors.blue,
    ),
    // فوقها
    Positioned(
      top: 20,
      right: 20,
      child: Icon(Icons.star, color: Colors.yellow, size: 50),
    ),
    // في المنتصف
    Center(
      child: Text("Hello", style: TextStyle(fontSize: 30, color: Colors.white)),
    ),
  ],
);

// مثال عملي: صورة مع نص فوقها
Stack(
  children: [
    Image.network("https://picsum.photos/400/200"),
    Positioned(
      bottom: 10,
      left: 10,
      child: Container(
        padding: EdgeInsets.all(8),
        color: Colors.black54,
        child: Text("Beautiful View", style: TextStyle(color: Colors.white)),
      ),
    ),
  ],
);
```

---

# 🟥 6) القوائم (Lists UI)

## 3️⃣0️⃣ ListView

```dart
// ListView عادي
ListView(
  children: [
    ListTile(title: Text("Item 1")),
    ListTile(title: Text("Item 2")),
    ListTile(title: Text("Item 3")),
  ],
);

// ListView مع Divider
ListView(
  children: [
    ListTile(title: Text("Item 1")),
    Divider(),
    ListTile(title: Text("Item 2")),
    Divider(),
    ListTile(title: Text("Item 3")),
  ],
);
```

---

## 3️⃣1️⃣ ListView.builder - مهم جدًا

```dart
List<String> items = ["Apple", "Banana", "Orange", "Mango"];

ListView.builder(
  itemCount: items.length,
  itemBuilder: (context, index) {
    return ListTile(
      title: Text(items[index]),
      subtitle: Text("Item #$index"),
    );
  },
);

// مثال عملي: قائمة منتجات
class Product {
  final String name;
  final double price;
  Product(this.name, this.price);
}

List<Product> products = [
  Product("Phone", 500),
  Product("Laptop", 1000),
  Product("Tablet", 300),
];

ListView.builder(
  itemCount: products.length,
  itemBuilder: (context, index) {
    Product p = products[index];
    return Card(
      child: ListTile(
        leading: Icon(Icons.shopping_bag),
        title: Text(p.name),
        subtitle: Text("\$${p.price}"),
        trailing: Icon(Icons.arrow_forward),
        onTap: () {
          print("Clicked: ${p.name}");
        },
      ),
    );
  },
);
```

### 📌 فوائد ListView.builder:

* يبني العناصر عند الحاجة فقط (Lazy Loading)
* أداء أفضل للقوائم الطويلة
* يوفر الذاكرة

---

## 3️⃣2️⃣ ListTile - عنصر جاهز

```dart
ListTile(
  leading: CircleAvatar(
    backgroundImage: NetworkImage("https://picsum.photos/100"),
  ),
  title: Text("Ahmed Ali"),
  subtitle: Text("Flutter Developer"),
  trailing: Icon(Icons.arrow_forward_ios),
  onTap: () {
    print("Tapped!");
  },
  onLongPress: () {
    print("Long pressed!");
  },
);
```

### 📊 أجزاء ListTile:

| الجزء | الموقع | مثال |
|-------|--------|------|
| `leading` | البداية | صورة، أيقونة |
| `title` | العنوان | النص الرئيسي |
| `subtitle` | تحت العنوان | نص فرعي |
| `trailing` | النهاية | أيقونة، زر |

---

## 3️⃣3️⃣ Card - بطاقة

```dart
Card(
  elevation: 5,           // الظل
  shape: RoundedRectangleBorder(
    borderRadius: BorderRadius.circular(15),
  ),
  child: Padding(
    padding: EdgeInsets.all(16),
    child: Column(
      crossAxisAlignment: CrossAxisAlignment.start,
      children: [
        Text("Title", style: TextStyle(fontSize: 20, fontWeight: FontWeight.bold)),
        SizedBox(height: 8),
        Text("This is a card content"),
      ],
    ),
  ),
);

// مثال عملي: بطاقة منتج
Card(
  margin: EdgeInsets.all(10),
  child: Column(
    children: [
      Image.network("https://picsum.photos/300/150", fit: BoxFit.cover),
      ListTile(
        title: Text("Product Name"),
        subtitle: Text("\$99.99"),
        trailing: Icon(Icons.favorite_border),
      ),
    ],
  ),
);
```

---

## 3️⃣4️⃣ GridView - شبكة

```dart
GridView.builder(
  gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
    crossAxisCount: 2,      // عدد الأعمدة
    crossAxisSpacing: 10,   // المسافة الأفقية
    mainAxisSpacing: 10,    // المسافة العمودية
    childAspectRatio: 1,    // نسبة العرض/الارتفاع
  ),
  itemCount: 10,
  itemBuilder: (context, index) {
    return Card(
      color: Colors.primaries[index % Colors.primaries.length],
      child: Center(
        child: Text("Item $index", style: TextStyle(fontSize: 20)),
      ),
    );
  },
);
```

---

# 🟥 7) الأزرار & Callbacks

## 3️⃣5️⃣ أنواع الأزرار

### 📊 جدول المقارنة:

| النوع | الشكل | الاستخدام |
|-------|-------|-----------|
| `ElevatedButton` | مرفوع بظل | الأزرار الرئيسية |
| `TextButton` | نص فقط | الأزرار الثانوية |
| `OutlinedButton` | محدد بإطار | بدائل |
| `IconButton` | أيقونة فقط | أيقونات |
| `FloatingActionButton` | دائري عائم | الإجراء الرئيسي |

### أمثلة:

```dart
// ElevatedButton
ElevatedButton(
  onPressed: () {
    print("Clicked!");
  },
  style: ElevatedButton.styleFrom(
    backgroundColor: Colors.blue,
    padding: EdgeInsets.symmetric(horizontal: 30, vertical: 15),
    shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(10)),
  ),
  child: Text("Submit"),
);

// TextButton
TextButton(
  onPressed: () {},
  child: Text("Cancel"),
);

// OutlinedButton
OutlinedButton(
  onPressed: () {},
  child: Text("More Info"),
);

// IconButton
IconButton(
  icon: Icon(Icons.favorite),
  color: Colors.red,
  onPressed: () {},
);

// FloatingActionButton
FloatingActionButton(
  onPressed: () {},
  child: Icon(Icons.add),
  backgroundColor: Colors.blue,
);

// FloatingActionButton.extended
FloatingActionButton.extended(
  onPressed: () {},
  icon: Icon(Icons.add),
  label: Text("Add Item"),
);
```

---

## 3️⃣6️⃣ Callbacks - الدوال التفاعلية

```dart
void myFunction() {// ✅ الطريقة الصحيحة - تمرير اسم الدالة
  print("Button clicked!");
}

ElevatedButton(
  onPressed: myFunction,  // ✅ بدون ()
  child: Text("Click Me"),
);

ElevatedButton(
  onPressed: () {// أو دالة مباشرة

    print("Clicked!");
  },
  child: Text("Click"),
);

// ❌ خطأ شائع
ElevatedButton(
  onPressed: myFunction(),  // ❌ خطأ - سينفذ فورًا
  child: Text("Click"),
);

// تمرير معاملات
void showMessage(String msg) {
  print(msg);
}

ElevatedButton(
  onPressed: () => showMessage("Hello!"),  // ✅
  child: Text("Say Hello"),
);
```

---

# 🟥 8) Navigation (التنقل بين الشاشات)

## 3️⃣7️⃣ فتح شاشة جديدة

```dart
class HomeScreen extends StatelessWidget {// الشاشة الأولى

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Home")),
      body: Center(
        child: ElevatedButton(
          onPressed: () {
            Navigator.push(
              context,
              MaterialPageRoute(builder: (context) => SecondScreen()),
            );
          },
          child: Text("Go to Second Screen"),
        ),
      ),
    );
  }
}

// الشاشة الثانية
class SecondScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Second")),
      body: Center(
        child: ElevatedButton(
          onPressed: () {
            Navigator.pop(context);  // الرجوع
          },
          child: Text("Go Back"),
        ),
      ),
    );
  }
}
```

---

## 3️⃣8️⃣ تمرير البيانات بين الشاشات

```dart
Navigator.push(// إرسال بيانات

  context,
  MaterialPageRoute(
    builder: (context) => DetailScreen(
      title: "Product Name",
      price: 99.99,
    ),
  ),
);

// استقبال البيانات
class DetailScreen extends StatelessWidget {
  final String title;
  final double price;
  
  DetailScreen({required this.title, required this.price});
  
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text(title)),
      body: Center(
        child: Text("Price: \$$price"),
      ),
    );
  }
}
```

---

## 3️⃣9️⃣ استقبال بيانات عند الرجوع

```dart
void openSecondScreen() async {// الشاشة الأولى

  final result = await Navigator.push(
    context,
    MaterialPageRoute(builder: (context) => SecondScreen()),
  );
  
  print("Received: $result");
}

// الشاشة الثانية - إرجاع بيانات
Navigator.pop(context, "Some data");
```

---

# 🟥 9) الألوان والثيمات 🎨

## 4️⃣0️⃣ Material Colors

```dart
Colors.red
Colors.blue
Colors.green

// درجات الألوان
Colors.red.shade50    // فاتح جدًا
Colors.red.shade100
Colors.red.shade200
...
Colors.red.shade900   // غامق جدًا

// مثال عملي
Container(
  color: Colors.blue.shade700,
  child: Text("Hello"),
);
```

### 📊 جدول درجات الألوان:

| الدرجة | الوصف |
|--------|-------|
| 50-200 | فاتح |
| 300-500 | متوسط |
| 600-900 | غامق |

---

## 4️⃣1️⃣ Custom Colors

```dart
Color myColor = Color(0xFF42A5F5);// لون مخصص من Hex

// لون من ARGB
Color myColor2 = Color.fromARGB(255, 66, 165, 245);

// لون من RGB
Color myColor3 = Color.fromRGBO(66, 165, 245, 1.0);
```

---

## 4️⃣2️⃣ Theme - الثيم

```dart
MaterialApp(
  theme: ThemeData(
    primarySwatch: Colors.blue,
    brightness: Brightness.light,
    
    // الألوان
    primaryColor: Colors.blue,
    accentColor: Colors.orange,
    
    // النصوص
    textTheme: TextTheme(
      headline1: TextStyle(fontSize: 30, fontWeight: FontWeight.bold),
      bodyText1: TextStyle(fontSize: 16),
    ),
    
    // الأزرار
    elevatedButtonTheme: ElevatedButtonThemeData(
      style: ElevatedButton.styleFrom(
        backgroundColor: Colors.blue,
        padding: EdgeInsets.all(15),
      ),
    ),
  ),
  home: HomeScreen(),
);

// استخدام الثيم
Container(
  color: Theme.of(context).primaryColor,
);
```

---

# 🟥 🔟 Async + API - التعامل مع البيانات

## 4️⃣3️⃣ Future & async/await

```dart
Future<String> fetchData() async {// Future بسيط

  await Future.delayed(Duration(seconds: 2));
  return "Data loaded!";
}

// استخدام
void loadData() async {
  String data = await fetchData();
  print(data);
}

// مع معالجة الأخطاء
void loadDataSafe() async {
  try {
    String data = await fetchData();
    print(data);
  } catch (e) {
    print("Error: $e");
  }
}
```

---

## 4️⃣4️⃣ HTTP Package

أولًا، أضف في `pubspec.yaml`:

```yaml
dependencies:
  http: ^1.1.0
```

### GET Request:

```dart
import 'package:http/http.dart' as http;
import 'dart:convert';

Future<void> fetchUsers() async {
  final url = Uri.parse('https://jsonplaceholder.typicode.com/users');
  
  try {
    final response = await http.get(url);
    
    if (response.statusCode == 200) {
      List<dynamic> data = json.decode(response.body);
      print(data);
    } else {
      print("Error: ${response.statusCode}");
    }
  } catch (e) {
    print("Error: $e");
  }
}
```

### POST Request:

```dart
Future<void> createPost() async {
  final url = Uri.parse('https://jsonplaceholder.typicode.com/posts');
  
  final response = await http.post(
    url,
    headers: {"Content-Type": "application/json"},
    body: json.encode({
      "title": "My Post",
      "body": "This is the content",
      "userId": 1,
    }),
  );
  
  if (response.statusCode == 201) {
    print("Created successfully!");
    print(json.decode(response.body));
  }
}
```

---

## 4️⃣5️⃣ Model Class - نموذج البيانات

```dart
class User {
  final int id;
  final String name;
  final String email;
  final String phone;
  
  User({
    required this.id,
    required this.name,
    required this.email,
    required this.phone,
  });
  
  // من JSON إلى Object
  factory User.fromJson(Map<String, dynamic> json) {
    return User(
      id: json['id'],
      name: json['name'],
      email: json['email'],
      phone: json['phone'],
    );
  }
  
  // من Object إلى JSON
  Map<String, dynamic> toJson() {
    return {
      'id': id,
      'name': name,
      'email': email,
      'phone': phone,
    };
  }
}

// استخدام
Future<List<User>> fetchUsers() async {
  final url = Uri.parse('https://jsonplaceholder.typicode.com/users');
  final response = await http.get(url);
  
  if (response.statusCode == 200) {
    List<dynamic> jsonData = json.decode(response.body);
    return jsonData.map((json) => User.fromJson(json)).toList();
  } else {
    throw Exception("Failed to load users");
  }
}
```

---

## 4️⃣6️⃣ FutureBuilder - عرض البيانات

```dart
class UsersScreen extends StatelessWidget {
  Future<List<User>> fetchUsers() async {
    final url = Uri.parse('https://jsonplaceholder.typicode.com/users');
    final response = await http.get(url);
    
    if (response.statusCode == 200) {
      List<dynamic> jsonData = json.decode(response.body);
      return jsonData.map((json) => User.fromJson(json)).toList();
    } else {
      throw Exception("Failed");
    }
  }
  
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Users")),
      body: FutureBuilder<List<User>>(
        future: fetchUsers(),
        builder: (context, snapshot) {
          // Loading
          if (snapshot.connectionState == ConnectionState.waiting) {
            return Center(child: CircularProgressIndicator());
          }
          
          // Error
          if (snapshot.hasError) {
            return Center(child: Text("Error: ${snapshot.error}"));
          }
          
          // No Data
          if (!snapshot.hasData || snapshot.data!.isEmpty) {
            return Center(child: Text("No users found"));
          }
          
          // Success - عرض البيانات
          List<User> users = snapshot.data!;
          return ListView.builder(
            itemCount: users.length,
            itemBuilder: (context, index) {
              User user = users[index];
              return Card(
                child: ListTile(
                  leading: CircleAvatar(child: Text("${user.id}")),
                  title: Text(user.name),
                  subtitle: Text(user.email),
                  trailing: Icon(Icons.arrow_forward),
                ),
              );
            },
          );
        },
      ),
    );
  }
}
```

### 📊 حالات FutureBuilder:

| الحالة | متى | الإجراء |
|--------|-----|---------|
| `ConnectionState.waiting` | جاري التحميل | أظهر Loading |
| `snapshot.hasError` | حدث خطأ | أظهر رسالة خطأ |
| `!snapshot.hasData` | لا توجد بيانات | أظهر "لا توجد بيانات" |
| `snapshot.hasData` | نجح | اعرض البيانات |

---

## 4️⃣7️⃣ مثال API كامل - Posts App

```dart
// 1. Model
class Post {
  final int id;
  final String title;
  final String body;
  
  Post({required this.id, required this.title, required this.body});
  
  factory Post.fromJson(Map<String, dynamic> json) {
    return Post(
      id: json['id'],
      title: json['title'],
      body: json['body'],
    );
  }
}

// 2. API Service
class ApiService {
  static const String baseUrl = 'https://jsonplaceholder.typicode.com';
  
  static Future<List<Post>> getPosts() async {
    final response = await http.get(Uri.parse('$baseUrl/posts'));
    
    if (response.statusCode == 200) {
      List<dynamic> jsonData = json.decode(response.body);
      return jsonData.map((json) => Post.fromJson(json)).toList();
    } else {
      throw Exception('Failed to load posts');
    }
  }
}

// 3. UI Screen
class PostsScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Posts")),
      body: FutureBuilder<List<Post>>(
        future: ApiService.getPosts(),
        builder: (context, snapshot) {
          if (snapshot.connectionState == ConnectionState.waiting) {
            return Center(child: CircularProgressIndicator());
          }
          
          if (snapshot.hasError) {
            return Center(child: Text("Error: ${snapshot.error}"));
          }
          
          List<Post> posts = snapshot.data!;
          return ListView.builder(
            itemCount: posts.length,
            itemBuilder: (context, index) {
              Post post = posts[index];
              return Card(
                margin: EdgeInsets.all(8),
                child: ListTile(
                  leading: CircleAvatar(child: Text("${post.id}")),
                  title: Text(post.title),
                  subtitle: Text(
                    post.body,
                    maxLines: 2,
                    overflow: TextOverflow.ellipsis,
                  ),
                  onTap: () {
                    Navigator.push(
                      context,
                      MaterialPageRoute(
                        builder: (context) => PostDetailScreen(post: post),
                      ),
                    );
                  },
                ),
              );
            },
          );
        },
      ),
    );
  }
}

// 4. Detail Screen
class PostDetailScreen extends StatelessWidget {
  final Post post;
  
  PostDetailScreen({required this.post});
  
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Post #${post.id}")),
      body: Padding(
        padding: EdgeInsets.all(16),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            Text(
              post.title,
              style: TextStyle(fontSize: 24, fontWeight: FontWeight.bold),
            ),
            SizedBox(height: 16),
            Text(post.body, style: TextStyle(fontSize: 16)),
          ],
        ),
      ),
    );
  }
}
```

---

# 🟥 11) الصور 🖼️

## 4️⃣8️⃣ Image من الإنترنت

```dart
Image.network('https://picsum.photos/400/200');

// مع خصائص
Image.network(
  'https://picsum.photos/400/200',
  width: 400,
  height: 200,
  fit: BoxFit.cover,
  loadingBuilder: (context, child, loadingProgress) {
    if (loadingProgress == null) return child;
    return Center(child: CircularProgressIndicator());
  },
  errorBuilder: (context, error, stackTrace) {
    return Icon(Icons.error);
  },
);
```

### BoxFit Options:

| القيمة | الوصف |
|--------|-------|
| `cover` | يغطي كامل المساحة |
| `contain` | يناسب بدون قص |
| `fill` | يمدد لملء المساحة |
| `fitWidth` | ملء العرض |
| `fitHeight` | ملء الارتفاع |

---

## 4️⃣9️⃣ Image من Assets

1. أضف المجلد في `pubspec.yaml`:

```yaml
flutter:
  assets:
    - assets/images/
```

2. استخدم الصورة:

```dart
Image.asset('assets/images/logo.png');

// مع خصائص
Image.asset(
  'assets/images/logo.png',
  width: 200,
  height: 100,
);
```

---

## 5️⃣0️⃣ CircleAvatar - صورة دائرية

```dart
CircleAvatar(
  radius: 50,
  backgroundImage: NetworkImage('https://picsum.photos/200'),
);

// من Assets
CircleAvatar(
  radius: 50,
  backgroundImage: AssetImage('assets/images/profile.jpg'),
);

// مع نص
CircleAvatar(
  radius: 30,
  backgroundColor: Colors.blue,
  child: Text("A", style: TextStyle(fontSize: 30, color: Colors.white)),
);
```

---

# 🟥 12) التخزين المحلي (Local Storage)

## 5️⃣1️⃣ SharedPreferences

أولًا، أضف في `pubspec.yaml`:

```yaml
dependencies:
  shared_preferences: ^2.2.0
```

### حفظ واسترجاع البيانات:

```dart
import 'package:shared_preferences/shared_preferences.dart';

// حفظ
Future<void> saveData() async {
  final prefs = await SharedPreferences.getInstance();
  
  await prefs.setString('username', 'Ahmed');
  await prefs.setInt('age', 25);
  await prefs.setDouble('balance', 500.50);
  await prefs.setBool('isLoggedIn', true);
  await prefs.setStringList('tags', ['flutter', 'dart']);
}

// استرجاع
Future<void> loadData() async {
  final prefs = await SharedPreferences.getInstance();
  
  String? username = prefs.getString('username');
  int? age = prefs.getInt('age');
  double? balance = prefs.getDouble('balance');
  bool? isLoggedIn = prefs.getBool('isLoggedIn');
  List<String>? tags = prefs.getStringList('tags');
  
  print("Username: $username");
  print("Age: $age");
}

// حذف
Future<void> deleteData() async {
  final prefs = await SharedPreferences.getInstance();
  await prefs.remove('username');
}

// حذف كل شيء
Future<void> clearAll() async {
  final prefs = await SharedPreferences.getInstance();
  await prefs.clear();
}
```
---
## Dropdown
```dart
import 'package:flutter/material.dart';
import 'package:shared_preferences/shared_preferences.dart';

class DropdownFromPrefs extends StatefulWidget {
  const DropdownFromPrefs({super.key});

  @override
  State<DropdownFromPrefs> createState() => _DropdownFromPrefsState();
}

class _DropdownFromPrefsState extends State<DropdownFromPrefs> {
  List<String> options = [];
  String? selected;

  @override
  void initState() {
    super.initState();
    loadOptions();
  }

  // ✅ تحميل القائمة من SharedPreferences
  Future<void> loadOptions() async {
    final prefs = await SharedPreferences.getInstance();

    // إذا ما في بيانات مخزنة، استخدم default list
    final savedList = prefs.getStringList('fruits') ??
        ['Apple', 'Orange', 'Mango', 'Banana'];

    // ✅ (اختياري) خزّنها أول مرة عشان تصير موجودة في prefs
    await prefs.setStringList('fruits', savedList);

    setState(() {
      options = savedList;

      // ✅ لو ما كان في selected، خلي أول عنصر
      selected ??= options.isNotEmpty ? options[0] : null;
    });
  }

  // ✅ حفظ الاختيار الحالي
  Future<void> saveSelected(String value) async {
    final prefs = await SharedPreferences.getInstance();
    await prefs.setString('selectedFruit', value);
  }

  // ✅ تحميل الاختيار السابق (إذا بدك)
  Future<void> loadSelected() async {
    final prefs = await SharedPreferences.getInstance();
    final saved = prefs.getString('selectedFruit');
    if (saved != null) {
      setState(() => selected = saved);
    }
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text("Dropdown from SharedPreferences")),
      body: Padding(
        padding: const EdgeInsets.all(16),
        child: options.isEmpty
            ? const Center(child: CircularProgressIndicator())
            : Column(
                children: [
                  DropdownButton<String>(
                    isExpanded: true,
                    value: selected,
                    items: options.map((e) {
                      return DropdownMenuItem<String>(
                        value: e,
                        child: Text(e),
                      );
                    }).toList(),
                    onChanged: (value) {
                      if (value == null) return;
                      setState(() => selected = value);
                      saveSelected(value);
                    },
                  ),

                  const SizedBox(height: 20),

                  Text(
                    "Selected: $selected",
                    style: const TextStyle(fontSize: 18),
                  ),
                ],
              ),
      ),
    );
  }
}
```
---

## 5️⃣2️⃣ مثال عملي: Login System

```dart
class AuthService {
  static const String _keyToken = 'auth_token';
  static const String _keyUsername = 'username';
  
  // تسجيل دخول
  static Future<void> login(String username, String token) async {
    final prefs = await SharedPreferences.getInstance();
    await prefs.setString(_keyUsername, username);
    await prefs.setString(_keyToken, token);
  }
  
  // فحص تسجيل الدخول
  static Future<bool> isLoggedIn() async {
    final prefs = await SharedPreferences.getInstance();
    return prefs.containsKey(_keyToken);
  }
  
  // الحصول على اسم المستخدم
  static Future<String?> getUsername() async {
    final prefs = await SharedPreferences.getInstance();
    return prefs.getString(_keyUsername);
  }
  
  // تسجيل خروج
  static Future<void> logout() async {
    final prefs = await SharedPreferences.getInstance();
    await prefs.remove(_keyToken);
    await prefs.remove(_keyUsername);
  }
}

// استخدام
void main() async {
  await AuthService.login("ahmed", "token123");
  
  bool loggedIn = await AuthService.isLoggedIn();
  print("Logged in: $loggedIn");
  
  String? username = await AuthService.getUsername();
  print("Username: $username");
}
```

---

# 🟥 13) State Management - إدارة الحالة

## 5️⃣3️⃣ initState & dispose

```dart
class MyScreen extends StatefulWidget {
  @override
  _MyScreenState createState() => _MyScreenState();
}

class _MyScreenState extends State<MyScreen> {
  int counter = 0;
  
  @override
  void initState() {
    super.initState();
    // ينفذ مرة واحدة عند إنشاء الـ Widget
    print("Screen initialized");
    loadData();
  }
  
  @override
  void dispose() {
    // ينفذ عند إزالة الـ Widget
    print("Screen disposed");
    super.dispose();
  }
  
  void loadData() {
    // تحميل البيانات
  }
  
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Center(child: Text("$counter")),
    );
  }
}
```

### 📊 Lifecycle Methods:

| Method | متى ينفذ | الاستخدام |
|--------|---------|-----------|
| `initState` | مرة واحدة في البداية | تحميل بيانات، تهيئة |
| `build` | كل مرة يتغير UI | رسم الواجهة |
| `dispose` | عند الإغلاق | تنظيف الموارد |

---

## 5️⃣4️⃣ StatefulBuilder

```dart
StatefulBuilder(// تحديث جزء من الشاشة بدون StatefulWidget
  builder: (context, setState) {
    int count = 0;
    
    return Column(
      children: [
        Text("Count: $count"),
        ElevatedButton(
          onPressed: () {
            setState(() {
              count++;
            });
          },
          child: Text("Add"),
        ),
      ],
    );
  },
);
```

---

~~5️⃣5️⃣ ValueNotifier & ValueListenableBuilder~~

```dart
class CounterScreen extends StatelessWidget {
  final ValueNotifier<int> counter = ValueNotifier<int>(0);
  
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("ValueNotifier")),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            ValueListenableBuilder<int>(
              valueListenable: counter,
              builder: (context, value, child) {
                return Text("Count: $value", style: TextStyle(fontSize: 30));
              },
            ),
            SizedBox(height: 20),
            ElevatedButton(
              onPressed: () {
                counter.value++;
              },
              child: Text("Increment"),
            ),
          ],
        ),
      ),
    );
  }
}
```

---

~~# 🟥 14) Advanced Widgets~~

## ~~5️⃣6️⃣ BottomNavigationBar~~

```dart
class MainScreen extends StatefulWidget {
  @override
  _MainScreenState createState() => _MainScreenState();
}

class _MainScreenState extends State<MainScreen> {
  int _currentIndex = 0;
  
  final List<Widget> _screens = [
    HomeScreen(),
    SearchScreen(),
    ProfileScreen(),
  ];
  
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: _screens[_currentIndex],
      bottomNavigationBar: BottomNavigationBar(
        currentIndex: _currentIndex,
        onTap: (index) {
          setState(() {
            _currentIndex = index;
          });
        },
        items: [
          BottomNavigationBarItem(
            icon: Icon(Icons.home),
            label: "Home",
          ),
          BottomNavigationBarItem(
            icon: Icon(Icons.search),
            label: "Search",
          ),
          BottomNavigationBarItem(
            icon: Icon(Icons.person),
            label: "Profile",
          ),
        ],
      ),
    );
  }
}
```

---

## ~~5️⃣7️⃣ Drawer - القائمة الجانبية~~

```dart
Scaffold(
  appBar: AppBar(title: Text("My App")),
  drawer: Drawer(
    child: ListView(
      padding: EdgeInsets.zero,
      children: [
        DrawerHeader(
          decoration: BoxDecoration(color: Colors.blue),
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.start,
            children: [
              CircleAvatar(
                radius: 30,
                backgroundImage: NetworkImage("https://picsum.photos/100"),
              ),
              SizedBox(height: 10),
              Text("Ahmed Ali", style: TextStyle(color: Colors.white, fontSize: 20)),
              Text("ahmed@email.com", style: TextStyle(color: Colors.white70)),
            ],
          ),
        ),
        ListTile(
          leading: Icon(Icons.home),
          title: Text("Home"),
          onTap: () {
            Navigator.pop(context);
          },
        ),
        ListTile(
          leading: Icon(Icons.settings),
          title: Text("Settings"),
          onTap: () {},
        ),
        Divider(),
        ListTile(
          leading: Icon(Icons.logout),
          title: Text("Logout"),
          onTap: () {},
        ),
      ],
    ),
  ),
  body: Center(child: Text("Main Content")),
);
```

---

## ~~5️⃣8️⃣ DropdownButton - قائمة منسدلة~~

```dart
class DropdownExample extends StatefulWidget {
  @override
  _DropdownExampleState createState() => _DropdownExampleState();
}

class _DropdownExampleState extends State<DropdownExample> {
  String? selectedCity;
  
  List<String> cities = ["Ramallah", "Nablus", "Hebron", "Gaza"];
  
  @override
  Widget build(BuildContext context) {
    return DropdownButton<String>(
      value: selectedCity,
      hint: Text("Select City"),
      items: cities.map((String city) {
        return DropdownMenuItem<String>(
          value: city,
          child: Text(city),
        );
      }).toList(),
      onChanged: (String? newValue) {
        setState(() {
          selectedCity = newValue;
        });
      },
    );
  }
}
```

---

## ~~5️⃣9️⃣ TabBar - تبويبات~~

```dart
class TabBarExample extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return DefaultTabController(
      length: 3,
      child: Scaffold(
        appBar: AppBar(
          title: Text("Tabs"),
          bottom: TabBar(
            tabs: [
              Tab(icon: Icon(Icons.home), text: "Home"),
              Tab(icon: Icon(Icons.search), text: "Search"),
              Tab(icon: Icon(Icons.person), text: "Profile"),
            ],
          ),
        ),
        body: TabBarView(
          children: [
            Center(child: Text("Home Tab")),
            Center(child: Text("Search Tab")),
            Center(child: Text("Profile Tab")),
          ],
        ),
      ),
    );
  }
}
```

---

## 6️⃣0️⃣ Form & TextField

```dart
class LoginForm extends StatefulWidget {
  @override
  _LoginFormState createState() => _LoginFormState();
}

class _LoginFormState extends State<LoginForm> {
  final _formKey = GlobalKey<FormState>();
  final _emailController = TextEditingController();
  final _passwordController = TextEditingController();
  
  @override
  void dispose() {
    _emailController.dispose();
    _passwordController.dispose();
    super.dispose();
  }
  
  void _submit() {
    if (_formKey.currentState!.validate()) {
      String email = _emailController.text;
      String password = _passwordController.text;
      print("Email: $email, Password: $password");
    }
  }
  
  @override
  Widget build(BuildContext context) {
    return Form(
      key: _formKey,
      child: Column(
        children: [
          TextFormField(
            controller: _emailController,
            decoration: InputDecoration(
              labelText: "Email",
              prefixIcon: Icon(Icons.email),
              border: OutlineInputBorder(),
            ),
            validator: (value) {
              if (value == null || value.isEmpty) {
                return "Please enter email";
              }
              if (!value.contains("@")) {
                return "Invalid email";
              }
              return null;
            },
          ),
          SizedBox(height: 16),
          TextFormField(
            controller: _passwordController,
            obscureText: true,
            decoration: InputDecoration(
              labelText: "Password",
              prefixIcon: Icon(Icons.lock),
              border: OutlineInputBorder(),
            ),
            validator: (value) {
              if (value == null || value.isEmpty) {
                return "Please enter password";
              }
              if (value.length < 6) {
                return "Password must be at least 6 characters";
              }
              return null;
            },
          ),
          SizedBox(height: 24),
          ElevatedButton(
            onPressed: _submit,
            child: Text("Login"),
          ),
        ],
      ),
    );
  }
}
```

---

# 🟥 15) Best Practices & Common Errors

## ❌ أخطاء شائعة

### 1️⃣ async في build():

```dart
@override// ❌ خطأ
Widget build(BuildContext context) async {  // خطأ
  await loadData();
  return Scaffold(...);
}

// ✅ صح
@override
Widget build(BuildContext context) {
  return FutureBuilder(
    future: loadData(),
    builder: (context, snapshot) { ... },
  );
}
```

### 2️⃣ نسيان setState:

```dart
oid increment() {// ❌ خطأ
  counter++;  // لن يعمل
}

// ✅ صح
void increment() {
  setState(() {
    counter++;
  });
}
```

### 3️⃣ ListView داخل Column:

```dart
Column(// ❌ خطأ
  children: [
    ListView(...),  // Error!
  ],
)

// ✅ صح
Column(
  children: [
    Expanded(
      child: ListView(...),
    ),
  ],
)
```

### 4️⃣ null بدون ?:

```dart
String name;  // Error: must be initialized// ❌ خطأ

// ✅ صح
String? name;  // OK: can be null
String name = "";  // OK: initialized
```

---

## ✅ Best Practices

### 1️⃣ تنظيم الكود:

```
lib/
  ├── models/
  │   ├── user.dart
  │   └── post.dart
  ├── screens/
  │   ├── home_screen.dart
  │   └── profile_screen.dart
  ├── services/
  │   └── api_service.dart
  ├── widgets/
  │   └── custom_button.dart
  └── main.dart
```

### 2️⃣ استخدام const:

```dart
const Text("Hello");// ✅ أفضل للأداء
const SizedBox(height: 20);
const Icon(Icons.home);
```

### 3️⃣ تسمية واضحة:

```dart
final List<User> activeUsers = [];// ✅ جيد
void fetchUserData() {}

// ❌ سيء
final List<User> l = [];
void f() {}
```

---

## 📌 النتيجة النهائية

بعد هذا الدليل الشامل، أنت الآن قادر على:

✅ فهم Flutter & Dart من الصفر  
✅ بناء واجهات UI احترافية  
✅ التعامل مع APIs والبيانات  
✅ عرض الصور من الإنترنت و Assets  
✅ التخزين المحلي (SharedPreferences)  
✅ التنقل بين الشاشات  
✅ إدارة الحالة (State Management)  
✅ استخدام FutureBuilder & ListView.builder  
✅ كتابة كود نظيف ومنظم  

---

## 🎓 هذا الدليل مناسب لـ:

* 📚 الدراسة الذاتية
* 🧠 المراجعة السريعة
* 🧪 التدريب العملي
* 🧑‍💻 مرجع GitHub
* 🎓 الامتحانات والمقابلات

---

## 🚀 الخطوات التالية:

1. **مشاريع عملية** - ابدأ ببناء تطبيق كامل
2. **State Management متقدم** - Provider, Riverpod, BLoC
3. **Firebase Integration** - Authentication, Firestore, Storage
4. **Animations** - تعلم الحركات والانتقالات
5. **Publishing** - نشر التطبيق على المتاجر

---

**Good Luck! 🎉**
