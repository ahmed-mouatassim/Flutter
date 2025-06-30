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
