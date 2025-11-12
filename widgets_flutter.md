# ✅ **`AlertDialog`** 

## — نافذة تنبيه كاتطلع فوسط الشاشة

📌 كاتستعمل باش توري للمستخدم رسالة أو تأكيد.

### 📦 مثال:

```dart
showDialog(
  context: context,
  builder: (BuildContext context) {
    return AlertDialog(
      title: Text("تنبيه"),
      content: Text("واش متأكد بغيتي تخرج؟"),
      actions: [
        TextButton(
          child: Text("إلغاء"),
          onPressed: () {
            Navigator.of(context).pop(); // كتسد داك ال dialog
          },
        ),
        TextButton(
          child: Text("نعم"),
          onPressed: () {
            // دير هنا العملية لي بغيتي
          },
        ),
      ],
    );
  },
);
```

---
# ✅ **`SnackBar`**


```dart
  // 🔐 معالجة تسجيل الدخول (Login Handler)
  void _handleLogin() {
    // التحقق من صحة البيانات (Validation Logic)
    if (emailController.text.isEmpty || passwordController.text.isEmpty) {
      _showSnackBar('يرجى ملء جميع الحقول', Colors.red);
      return;
    }

    if (!emailController.text.contains('@ofppt-edu.ma')) {
      _showSnackBar('يجب استخدام إيميل OFPPT الرسمي', Colors.orange);
      return;
    }

    if (passwordController.text.length < 6) {
      _showSnackBar('كلمة المرور يجب أن تحتوي على 6 أحرف على الأقل', Colors.orange);
      return;
    }

    // إخفاء لوحة المفاتيح (Hide Keyboard)
    FocusScope.of(context).unfocus();

    // الانتقال للشاشة التالية (Navigate to Next Screen)
    Navigator.pushAndRemoveUntil(
      context,
      MaterialPageRoute(builder: (context) => const ChooseScreen()),
      (Route<dynamic> route) => false,
    );
  }

  // 📝 معالجة التسجيل (Sign Up Handler)
  void _handleSignUp() {
    _showSnackBar('ميزة التسجيل قيد التطوير', Colors.blue);
  }

  // 🔑 معالجة نسيان كلمة المرور (Forgot Password Handler)
  void _handleForgotPassword() {
    _showSnackBar('سيتم إرسال رابط إعادة تعيين كلمة المرور', Colors.green);
  }

  // 💬 عرض رسالة (Show Snackbar)
  void _showSnackBar(String message, Color color) {
    ScaffoldMessenger.of(context).showSnackBar(
      SnackBar(
        content: Text(message),
        backgroundColor: color,
        behavior: SnackBarBehavior.floating,
        shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(10)),
      ),
    );
  }
  ```

  ## ❔ ماذا يفعل هذا الكود  :

➖ **الكود يتعامل مع تسجيل الدخول بحيث اذا تركت الخانة فارغة يظهر لك رسالة خطأ وايضا يتحقق من صحة البريد الالكتروني.**

➖ **اذا كانت كلمة المرور اقل من 6 احرف او ارقام يعرض لك رسالة خطأ.**