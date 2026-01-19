# 📱 دليل شامل: Flutter UI Components & Data Persistence

> دليل كامل يشرح **Layouts / Widgets / Navigation / Lifecycle** وطرق **حفظ البيانات** في تطبيقات Flutter (بنفس فكرة دليل Android اللي عندك)

---

## 📁 هيكل مشروع Flutter (مختصر مهم)

أهم ملفات/مجلدات رح تتعامل معها:

```
lib/
  main.dart
  screens/
  widgets/
  models/
  services/
assets/
  images/
pubspec.yaml
```

* `pubspec.yaml`: dependencies + assets
* `lib/main.dart`: نقطة الدخول للتطبيق
* `screens/`: الشاشات (Pages)
* `widgets/`: ويدجتس قابلة لإعادة الاستخدام
* `models/`: Data models (User, Product, …)
* `services/`: API / storage / helpers

---

## 1️⃣ pubspec.yaml (Dependencies + Assets)

### Dependencies شائعة

```yaml
dependencies:
  flutter:
    sdk: flutter

  # Networking
  http: ^1.2.2

  # JSON (اختياري — الأفضل مع code generation)
  json_annotation: ^4.9.0

  # Persistence
  shared_preferences: ^2.3.2
  hive: ^2.2.3
  hive_flutter: ^1.1.0

  # Local DB (اختياري)
  sqflite: ^2.3.3
  path_provider: ^2.1.4

  # Secure storage (للأشياء الحساسة)
  flutter_secure_storage: ^9.2.2
```

### Assets (صور/ملفات)

```yaml
flutter:
  assets:
    - assets/images/
```

---

## 2️⃣ main.dart (نقطة الدخول + MaterialApp + Theme)

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Guide App',
      debugShowCheckedModeBanner: false,

      // Theme (بديل styles.xml + colors.xml)
      theme: ThemeData(
        colorScheme: ColorScheme.fromSeed(seedColor: Colors.indigo),
        useMaterial3: true,
        textTheme: const TextTheme(
          titleLarge: TextStyle(fontSize: 22, fontWeight: FontWeight.bold),
          bodyMedium: TextStyle(fontSize: 16),
        ),
      ),

      home: const HomeScreen(),
    );
  }
}

class HomeScreen extends StatelessWidget {
  const HomeScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return const Scaffold(
      appBar: AppBar(title: Text('Home')),
      body: Center(child: Text('Hello Flutter')),
    );
  }
}
```

---

# 📐 Layouts في Flutter (بدائل Linear/Relative/Constraint…)

## ✅ 1) Column / Row (بديل LinearLayout)

* `Column`: عمودي
* `Row`: أفقي
* أهم شي: توزيع المساحة باستخدام `Expanded` / `Flexible` (بديل weight)

```dart
Column(
  crossAxisAlignment: CrossAxisAlignment.stretch,
  children: [
    const Text('Item 1'),
    Expanded(
      child: Container(
        alignment: Alignment.center,
        child: const Text('Takes remaining space'),
      ),
    ),
    ElevatedButton(
      onPressed: () {},
      child: const Text('Button'),
    ),
  ],
);
```

### بديل `layout_weight`

* `Expanded(flex: 1)` مثل weight=1
* `Expanded(flex: 2)` مثل weight=2

```dart
Row(
  children: [
    Expanded(flex: 1, child: Container(height: 60)),
    Expanded(flex: 2, child: Container(height: 60)),
  ],
);
```

---

## ✅ 2) Margin vs Padding (نفس المفهوم)

في Flutter:

* `Padding(...)` = padding
* `Container(margin: ...)` = margin

```dart
Container(
  margin: const EdgeInsets.all(16),        // Margin
  padding: const EdgeInsets.symmetric(
    horizontal: 20, vertical: 10),         // Padding
  child: const Text('Box'),
);
```

**EdgeInsets الأكثر استخداماً**

```dart
EdgeInsets.all(16)
EdgeInsets.only(top: 10, bottom: 10)
EdgeInsets.symmetric(horizontal: 12, vertical: 8)
```

---

## ✅ 3) Stack (بديل FrameLayout)

```dart
Stack(
  children: [
    Image.asset('assets/images/bg.jpg', fit: BoxFit.cover, width: double.infinity),
    const Positioned(
      left: 16,
      bottom: 16,
      child: Text('Text over image', style: TextStyle(color: Colors.white, fontSize: 22)),
    ),
    Positioned(
      right: 16,
      bottom: 16,
      child: ElevatedButton(
        onPressed: () {},
        child: const Text('Click'),
      ),
    ),
  ],
);
```

---

## ✅ 4) SingleChildScrollView (بديل ScrollView)

> ملاحظة: مثل Android، الأفضل ما تحط `ListView` جوّا `SingleChildScrollView` إلا بحذر.

```dart
SingleChildScrollView(
  padding: const EdgeInsets.all(16),
  child: Column(
    children: const [
      Text('Long content...'),
      SizedBox(height: 20),
      Text('More content...'),
    ],
  ),
);
```

---

## ✅ 5) Table (بديل TableLayout)

```dart
Table(
  border: TableBorder.all(),
  columnWidths: const {
    0: FlexColumnWidth(1),
    1: FlexColumnWidth(2),
  },
  children: const [
    TableRow(children: [
      Padding(padding: EdgeInsets.all(8), child: Text('Name')),
      Padding(padding: EdgeInsets.all(8), child: Text('Email')),
    ]),
    TableRow(children: [
      Padding(padding: EdgeInsets.all(8), child: Text('Ahmad')),
      Padding(padding: EdgeInsets.all(8), child: Text('a@x.com')),
    ]),
  ],
);
```

---

## ✅ 6) “ConstraintLayout” في Flutter؟

Flutter ما عنده ConstraintLayout بنفس الفكرة، لأن **كل شيء مبني على Constraints** أساساً. البدائل العملية:

* `Row/Column + Expanded/Flexible`
* `Stack + Positioned`
* `Align`
* `LayoutBuilder` (لو بدك سلوك حسب الحجم)

مثال LayoutBuilder:

```dart
LayoutBuilder(
  builder: (context, constraints) {
    if (constraints.maxWidth > 600) {
      return Row(children: const [Expanded(child: Text('Tablet Layout'))]);
    }
    return const Text('Phone Layout');
  },
);
```

---

# 🧩 UI Components (Widgets)

## Scaffold (هيكل الشاشة)

```dart
Scaffold(
  appBar: AppBar(title: const Text('Title')),
  body: const Center(child: Text('Body')),
  floatingActionButton: FloatingActionButton(
    onPressed: () {},
    child: const Icon(Icons.add),
  ),
);
```

## Text (بديل TextView)

```dart
Text(
  'Hello',
  maxLines: 2,
  overflow: TextOverflow.ellipsis,
  style: const TextStyle(
    fontSize: 16,
    fontWeight: FontWeight.bold,
    color: Colors.black,
  ),
);
```

## TextField (بديل EditText)

```dart
final controller = TextEditingController();

TextField(
  controller: controller,
  keyboardType: TextInputType.emailAddress,
  obscureText: false,
  decoration: const InputDecoration(
    labelText: 'Email',
    hintText: 'Enter email',
    prefixIcon: Icon(Icons.email),
    border: OutlineInputBorder(),
  ),
);
```

## Buttons

```dart
ElevatedButton(onPressed: () {}, child: const Text('Elevated'));
TextButton(onPressed: () {}, child: const Text('Text'));
OutlinedButton(onPressed: () {}, child: const Text('Outlined'));
IconButton(onPressed: () {}, icon: const Icon(Icons.delete));
```

## Image

```dart
Image.asset('assets/images/logo.png', width: 120);
Image.network('https://...', fit: BoxFit.cover);
```

## Card

```dart
Card(
  elevation: 4,
  child: Padding(
    padding: const EdgeInsets.all(16),
    child: Column(
      crossAxisAlignment: CrossAxisAlignment.start,
      children: const [
        Text('Card title', style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold)),
        SizedBox(height: 6),
        Text('Card content...'),
      ],
    ),
  ),
);
```

## ListView (بديل RecyclerView)

الأفضل للأداء: `ListView.builder`

```dart
ListView.builder(
  itemCount: 100,
  itemBuilder: (context, index) {
    return ListTile(
      title: Text('Item $index'),
      onTap: () {},
    );
  },
);
```

---

# 🧭 Navigation (بديل Intents)

## 1) فتح شاشة جديدة (push)

```dart
Navigator.push(
  context,
  MaterialPageRoute(builder: (_) => const DetailsScreen(id: 7)),
);
```

## 2) رجوع (pop)

```dart
Navigator.pop(context);
```

## 3) تمرير بيانات للشاشة الثانية

```dart
class DetailsScreen extends StatelessWidget {
  final int id;
  const DetailsScreen({super.key, required this.id});

  @override
  Widget build(BuildContext context) => Scaffold(
    appBar: AppBar(title: Text('Details $id')),
    body: Center(child: Text('Item id = $id')),
  );
}
```

## 4) إرجاع نتيجة (مثل startActivityForResult)

```dart
final result = await Navigator.push<String>(
  context,
  MaterialPageRoute(builder: (_) => const PickScreen()),
);

if (result != null) {
  debugPrint('Picked: $result');
}
```

---

# ♻️ Lifecycle في Flutter (بديل Activity Lifecycle)

## StatefulWidget Lifecycle

* `initState()` مثل “تهيئة أول مرة”
* `build()` رسم الواجهة
* `dispose()` تنظيف الموارد

```dart
class Demo extends StatefulWidget {
  const Demo({super.key});

  @override
  State<Demo> createState() => _DemoState();
}

class _DemoState extends State<Demo> {
  @override
  void initState() {
    super.initState();
    debugPrint('initState');
  }

  @override
  void dispose() {
    debugPrint('dispose');
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    debugPrint('build');
    return const SizedBox();
  }
}
```

## App Lifecycle (Background/Foreground)

```dart
class AppLifeObserver extends StatefulWidget {
  const AppLifeObserver({super.key});

  @override
  State<AppLifeObserver> createState() => _AppLifeObserverState();
}

class _AppLifeObserverState extends State<AppLifeObserver>
    with WidgetsBindingObserver {

  @override
  void initState() {
    super.initState();
    WidgetsBinding.instance.addObserver(this);
  }

  @override
  void didChangeAppLifecycleState(AppLifecycleState state) {
    debugPrint('App state: $state'); // resumed, paused, inactive...
  }

  @override
  void dispose() {
    WidgetsBinding.instance.removeObserver(this);
    super.dispose();
  }

  @override
  Widget build(BuildContext context) => const SizedBox();
}
```

---

# 💾 Data Persistence في Flutter (نفس فكرة SharedPrefs / SQLite / Files)

## ✅ جدول سريع (مثل جدول Android)

| الطريقة                  | الاستخدام               | حجم البيانات |
| ------------------------ | ----------------------- | ------------ |
| `shared_preferences`     | إعدادات بسيطة key-value | صغير         |
| `flutter_secure_storage` | Tokens/Secrets          | صغير + حساس  |
| `hive`                   | كاش + Objects بسرعة     | متوسط        |
| `sqflite`                | بيانات منظمة (جداول)    | متوسط-كبير   |
| `path_provider + files`  | ملفات محلية (نص/JSON)   | متنوع        |

---

## 🔑 1) SharedPreferences (بديل SharedPreferences Android)

### حفظ/قراءة/حذف

```dart
import 'package:shared_preferences/shared_preferences.dart';

class Prefs {
  static const _keyUsername = 'username';
  static const _keyLoggedIn = 'isLoggedIn';

  static Future<void> saveLogin(String username) async {
    final prefs = await SharedPreferences.getInstance();
    await prefs.setString(_keyUsername, username);
    await prefs.setBool(_keyLoggedIn, true);
  }

  static Future<String> getUsername() async {
    final prefs = await SharedPreferences.getInstance();
    return prefs.getString(_keyUsername) ?? 'Guest';
  }

  static Future<void> logout() async {
    final prefs = await SharedPreferences.getInstance();
    await prefs.remove(_keyUsername);
    await prefs.setBool(_keyLoggedIn, false);
  }
}
```

> مثل Android: ما تخزن أشياء حساسة (token) هنا، استخدم Secure Storage.

---

## 🔒 2) Secure Storage (للـ Tokens)

```dart
import 'package:flutter_secure_storage/flutter_secure_storage.dart';

class Secure {
  static const _storage = FlutterSecureStorage();

  static Future<void> saveToken(String token) =>
      _storage.write(key: 'token', value: token);

  static Future<String?> readToken() =>
      _storage.read(key: 'token');

  static Future<void> clear() => _storage.deleteAll();
}
```

---

## 📦 3) Hive (Local NoSQL سريع)

### Setup سريع

```dart
import 'package:hive_flutter/hive_flutter.dart';

Future<void> initHive() async {
  await Hive.initFlutter();
  await Hive.openBox('appBox');
}

class LocalCache {
  static Box get box => Hive.box('appBox');

  static void saveUserJson(String json) => box.put('user', json);
  static String? loadUserJson() => box.get('user');
}
```

---

## 🗃️ 4) SQLite (sqflite) للفورمات المنظمة

> مناسب لو عندك جداول وعلاقات واستعلامات.

```dart
import 'package:sqflite/sqflite.dart';
import 'package:path/path.dart';

class DB {
  static Database? _db;

  static Future<Database> instance() async {
    if (_db != null) return _db!;
    final path = join(await getDatabasesPath(), 'app.db');
    _db = await openDatabase(
      path,
      version: 1,
      onCreate: (db, v) async {
        await db.execute('''
          CREATE TABLE users(
            id INTEGER PRIMARY KEY,
            name TEXT,
            email TEXT
          )
        ''');
      },
    );
    return _db!;
  }

  static Future<void> insertUser(int id, String name, String email) async {
    final db = await instance();
    await db.insert('users', {'id': id, 'name': name, 'email': email});
  }
}
```

---

# 🌐 Networking + JSON (بديل Volley + Gson)

## 1) HTTP GET

```dart
import 'dart:convert';
import 'package:http/http.dart' as http;

Future<Map<String, dynamic>> fetchUser() async {
  final res = await http.get(Uri.parse('https://api.example.com/user'));
  if (res.statusCode != 200) throw Exception('Failed');
  return jsonDecode(res.body) as Map<String, dynamic>;
}
```

## 2) Model بسيط + fromJson/toJson

```dart
class User {
  final String name;
  final int age;

  User({required this.name, required this.age});

  factory User.fromJson(Map<String, dynamic> json) =>
      User(name: json['name'], age: json['age']);

  Map<String, dynamic> toJson() => {'name': name, 'age': age};
}
```

---

# 📐 Orientation & Responsive (بديل layout-land + sw600dp)

## 1) OrientationBuilder

```dart
OrientationBuilder(
  builder: (context, orientation) {
    if (orientation == Orientation.landscape) {
      return const Center(child: Text('Landscape UI'));
    }
    return const Center(child: Text('Portrait UI'));
  },
);
```

## 2) MediaQuery (أبعاد الشاشة)

```dart
final w = MediaQuery.of(context).size.width;
final isTablet = w >= 600;
```

## 3) قفل الاتجاه (مثل Manifest)

```dart
import 'package:flutter/services.dart';

await SystemChrome.setPreferredOrientations([
  DeviceOrientation.portraitUp,
]);
```

---

# 📏 الوحدات (Units) في Flutter

* Flutter يستخدم **logical pixels** (مثل dp conceptually)
* النص يتأثر بـ **Text Scale Factor** (مثل sp conceptually)
* الأفضل تستخدم `TextTheme` بدل ما تثبّت أحجام كثيرة يدويًا.

---

# ✅ Best Practices (UI + Storage + Performance)

## UI

1. استخدم `const` قد ما تقدر لتقليل rebuilds
2. استخدم `ListView.builder` بدل list ثابتة لعناصر كثيرة
3. افصل `widgets/` reusable
4. لا تكبّر `build()` بكود كثير — قسّم

## State

* البسيط: `setState`
* متوسط: `ValueNotifier` / `ChangeNotifier`
* مشاريع كبيرة: `Provider / Riverpod / Bloc` (اختار واحد)

## Persistence

1. `shared_preferences` للإعدادات فقط
2. tokens: `flutter_secure_storage`
3. بيانات كبيرة: `Hive` أو `SQLite`

## Performance

1. تجنب عمليات ثقيلة داخل `build()`
2. استخدم `FutureBuilder` / `StreamBuilder` بشكل صحيح
3. للصور: prefer caching (مثل `cached_network_image` لو احتجت)

---

# 🎯 ملخص سريع (مقارنة ذهنية مع Android)

| Android             | Flutter البديل                       |
| ------------------- | ------------------------------------ |
| Activity / Fragment | Screen = Widget (Stateless/Stateful) |
| XML Layout          | Widgets tree                         |
| LinearLayout        | Row / Column                         |
| FrameLayout         | Stack                                |
| ScrollView          | SingleChildScrollView                |
| RecyclerView        | ListView.builder                     |
| Intent Navigation   | Navigator.push/pop                   |
| SharedPreferences   | shared_preferences                   |
| Volley + Gson       | http + jsonDecode / Models           |

