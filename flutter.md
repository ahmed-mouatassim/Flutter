# 1. Shared Preferences:


## 🪄 الكود 1 :

```dart
Future<void> saveToken(String token) async {
  final prefs = await SharedPreferences.getInstance();
  await prefs.setString('token', token);
}
```


## 🧠 الشرح سطر بسطر:

### 🟦 `Future<void> saveToken(String token) async {`

* هادي دالة سميتها `saveToken`
* كتاخذ **token** كـ **String**، مثلا: `"abc12345"`
* `async`: حيت فيها `await`، خصنا نقولو ليها أنها دالة غير متزامنة
* `Future<void>`: كتعني أن هاد الدالة **غادي تكمل فالمستقبل** وماغادي ترجع والو (`void`)

---

### 🟦 `final prefs = await SharedPreferences.getInstance();`

* هنا كنديرو `await` باش **نجيب الإعدادات (SharedPreferences)** من الهاتف
* `SharedPreferences.getInstance()` كتخدم بحال `open()` ديال ملف، يعني كتفتح الاتصال مع التخزين
* `prefs` دابا هو **الكائن** اللي غادي نقدر نستعملو باش نخزن القيم (Strings, ints, booleans...)

---

### 🟦 `await prefs.setString('token', token);`

* هنا كنقولو ليه: **خزن القيمة `token` تحت المفتاح `'token'`**
* بحال لا قلنا ليه: `prefs['token'] = token;`
* ولكن حيت العملية تقدر تاخذ شوية وقت، استعملنا `await` باش **نسنا حتى تسالي التخزين**



## 🔐 علاش كنستعمل `SharedPreferences`؟

باش نخزنو بيانات صغيرة بشكل دائم، بحال:

* **token** ديال تسجيل الدخول
* الوضع الليلي (`darkMode`)
* لغة التطبيق
* user ID...

---

## 🧪 ملخص سريع:

| الكود                             | المعنى بالدارجة                   |
| --------------------------------- | --------------------------------- |
| `Future<void>`                    | دالة كتخدم مع الوقت وماراجعة والو |
| `async`                           | دالة غادي نستعمل فيها `await`     |
| `await`                           | سنا حتى تسالي العملية             |
| `SharedPreferences.getInstance()` | جيب access لتخزين الهاتف          |
| `prefs.setString(...)`            | خزن String فالهاتف تحت مفتاح معين |

---

إذا بغيتي ندير ليك مثال تطبيقي بـ **زر كيخزن وكيعرض token** قولها ليا، ونوريك كيفاش تستعمله في Flutter بطريقة عملية 💡📱

---
 
## 🪄 الكود 2 :

```dart
Future<void> removeToken() async {
  final prefs = await SharedPreferences.getInstance();
  await prefs.remove('token');
}

```

## 🧠 الشرح سطر بسطر:



### 🟦 `Future<String?> getToken() async {`

* هادي دالة سميتها `getToken`
* `async`: حيت فيها `await`، يعني كتخدم بشكل غير متزامن
* `Future<String?>`: هاد الدالة **غادي ترجع String فالمستقبل، ولكن تقدر تكون null**

⛔ علاش `String?`؟
لأن ممكن ميكونش شي token مخزن، فترجع `null`.

---

### 🟦 `final prefs = await SharedPreferences.getInstance();`

* هنا كنديرو `await` باش **نجيب الكائن ديال SharedPreferences** من تخزين الهاتف.
* `prefs` ولى فيه access لقراءة وكتابة البيانات فالتخزين.

---

### 🟦 `return prefs.getString('token');`

* كنرجعو القيمة اللي مخزنة تحت المفتاح `'token'`
* إذا كان مخزن، غادي ترجع `"abc123"`
* إذا ماكانش مخزن، غادي ترجع `null`

---

## 🎯 مثال عملي:

```dart
void checkToken() async {
  String? token = await getToken();

  if (token != null) {
    print('Token: $token');
  } else {
    print('Token ma kaynach!');
  }
}
```

---

## 📦 ملخص:

| الكود                        | المعنى بالدارجة                           |
| ---------------------------- | ----------------------------------------- |
| `Future<String?>`            | الدالة غادي ترجع String أو null فالمستقبل |
| `await SharedPreferences...` | سنا حتى نفتح التخزين                      |
| `prefs.getString('token')`   | رجع القيمة المخزنة تحت `'token'`          |

---

## 🪄 الكود 3 :



## ✅ الكود:

```dart
Future<void> removeToken() async {
  final prefs = await SharedPreferences.getInstance();
  await prefs.remove('token');
}
```
الدالة `removeToken()` كتقوم بـ **مسح (حذف) `token`** من التخزين (SharedPreferences).



## 🧠 الشرح:

### 🟦 `Future<void> removeToken() async {`

* هادي دالة سميتها `removeToken`
* `async`: حيت فيها `await`
* `Future<void>`: كتخدم مع الوقت ولكن **ماكتْرجع والو**

---

### 🟦 `final prefs = await SharedPreferences.getInstance();`

* كنجيب `prefs` اللي فيه الصلاحية باش نقرا ونكتب فـ SharedPreferences
* لازم نستعمل `await` حيت العملية تقدر تاخذ وقت

---

### 🟦 `await prefs.remove('token');`

* كنقولو ليه: **مسح المفتاح `'token'` من التخزين**
* يعني من بعد، `getToken()` غادي ترجع `null` لأن ما بقى والو مخزن

---

## 📦 ملخص سريع:

| الكود                     | المعنى بالدارجة                           |
| ------------------------- | ----------------------------------------- |
| `Future<void>`            | دالة كتخدم فالمستقبل وماكتْرجع والو       |
| `await prefs.remove(...)` | سنا حتى تمسح المفتاح `'token'` من التخزين |

---

## 🎯 مثال كامل فيه كلشي:

```dart
Future<void> saveToken(String token) async {
  final prefs = await SharedPreferences.getInstance();
  await prefs.setString('token', token);
}

Future<String?> getToken() async {
  final prefs = await SharedPreferences.getInstance();
  return prefs.getString('token');
}

Future<void> removeToken() async {
  final prefs = await SharedPreferences.getInstance();
  await prefs.remove('token');
}
```

# 2. Provider:

وعليكم السلام أحمد،
مرحبا بيك 🌟! بما أنك كتتعلم **Flutter** و**Dart** ومعاهم **PHP وMySQL**، فراك غادي مزيان بزاف، وهادشي لي كتسول عليه (Shared Preferences وProvider) مهمين بزاف فـ Flutter سواء فـ front-end أو حتى فـ التعامل مع الـ backend.

غادي نشرح ليك بجوج:

---

## ✅ 1. **Shared Preferences**

### 🟢 شنو هي؟

`SharedPreferences` هي وسيلة باش تخزن معلومات بسيطة (مثل token ديال الauth، اسم المستخدم، boolean واش دار login ...) مباشرة فـ الهاتف (local storage).

### 🟠 واش مناسبة لأي حاجة؟

لا. مناسبة فقط للحاجات **البسيطة**، بحال:

* Token
* UserId
* Theme (dark / light)
* لغة التطبيق
* واش دار login ولا لا...

### 🛠️ كيفاش نخدم بيها؟

#### أول حاجة: التثبيت

ضف هاد الباكيج فـ `pubspec.yaml`:

```yaml
dependencies:
  shared_preferences: ^2.2.2
```

#### ثاني حاجة: كيفاش نستعملها

```dart
import 'package:shared_preferences/shared_preferences.dart';

// لتخزين قيمة
Future<void> saveToken(String token) async {
  final prefs = await SharedPreferences.getInstance();
  await prefs.setString('token', token);
}

// لقراءة القيمة
Future<String?> getToken() async {
  final prefs = await SharedPreferences.getInstance();
  return prefs.getString('token');
}

// لحذف القيمة
Future<void> removeToken() async {
  final prefs = await SharedPreferences.getInstance();
  await prefs.remove('token');
}
```

---

## ✅ 2. **Provider**

### 🟢 شنو هو؟

`Provider` هو **State Management** system.
يعني كيساعدك تتحكم فـ الحالة ديال الواجهة (state) بطريقة منظمة وعصرية، مثلا:

* واش المستخدم داخل؟
* لائحة البيانات من API؟
* واش كاين loading؟
* عدد العناصر فـ cart؟
  وكتقدر توصل للمعلومة من أي بلاصة فالتطبيق بلا ما تدوزها بزز (prop drilling).

### 🟠 علاش نستعملوه؟

حيت Flutter عندو UI reactive، خاصك واحد الmethod باش تنظم المعلومة وتخلي الواجهات تعرف وقتاش تحدث رأسها.

