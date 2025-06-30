# ✔️ **Error in login method**

## ✅ الهدف:

* المستخدم يدخل الإيميل وكلمة السر.
* خاص:

  * الإيميل يكون فيه **@gmail.com**
  * كلمة السر تكون فيها **أكثر من 6 حروف**
* إلا ماكانوش هاد الشروط، يبان **error message**.

---

## 🎯 الخطوات العامة:

1. نحتاج `TextFormField` باش نستعمل الـ validation بسهولة.
2. نستعمل `Form` و `GlobalKey` باش نتحكم فالفورم كامل.
3. نستعمل الدالة `validator` باش ندير الشروط.

---

## ✅ الكود مبسط:

```dart
import 'package:flutter/material.dart';

class LoginPage extends StatelessWidget {
  final GlobalKey<FormState> _formKey = GlobalKey<FormState>();

  final TextEditingController emailController = TextEditingController();
  final TextEditingController passwordController = TextEditingController();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Login")),
      body: Padding(
        padding: EdgeInsets.all(16.0),
        child: Form(
          key: _formKey,
          child: Column(
            children: [
              // Email Field
              TextFormField(
                controller: emailController,
                decoration: InputDecoration(labelText: "Email"),
                validator: (value) {
                  if (value == null || value.isEmpty) {
                    return "دخل الإيميل";
                  } else if (!value.endsWith("@gmail.com")) {
                    return "خاص الإيميل يكون @gmail.com";
                  }
                  return null; // كلشي مزيان
                },
              ),

              // Password Field
              TextFormField(
                controller: passwordController,
                decoration: InputDecoration(labelText: "Password"),
                obscureText: true,
                validator: (value) {
                  if (value == null || value.isEmpty) {
                    return "دخل كلمة السر";
                  } else if (value.length < 6) {
                    return "كلمة السر خاصها تكون فيها أكثر من 6 حروف";
                  }
                  return null;
                },
              ),

              SizedBox(height: 20),

              // Button
              ElevatedButton(
                onPressed: () {
                  if (_formKey.currentState!.validate()) {
                    // إذا الشروط كلهم متوفرة
                    ScaffoldMessenger.of(context).showSnackBar(
                      SnackBar(content: Text("تم تسجيل الدخول ✅")),
                    );
                  }
                },
                child: Text("Login"),
              ),
            ],
          ),
        ),
      ),
    );
  }
}
```

---

## 📌 ملاحظات مهمة:

*  `validator`: كتسمح لينا نديرو شرط لكل حقل.

*  `Form`: كتجمع `TextFormField` وكتخلي `validate()` تخدم.

*  `ScaffoldMessenger`: باش نورّيو رسالة فالتطبيق.


