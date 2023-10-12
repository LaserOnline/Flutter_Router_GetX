
## Router GetX Code Example

main.dart

```bash
import 'package:flutter/material.dart';
import 'package:get/get.dart';
import 'module/router/router.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return GetMaterialApp(
      debugShowCheckedModeBanner: false,
      initialRoute: 'myapp',
      getPages: AppRoutes.routes,
    );
  }
}
```
router.dart
```bash
import 'package:get/get.dart';

class AppRoutes {
  static final routes = [
    GetPage(
      name: '/myapp',
      page: () => Myapp(),
    ),
  ];
}
```

การกำหนด route แบบพื้นฐาน
```bash
GetPage(
  name: '/home',
  page: () => HomePage(),
)
```

การกำหนด route พร้อม binding
```bash
GetPage(
  name: '/profile',
  page: () => ProfilePage(),
  binding: ProfileBinding(),
)
```

การกำหนด route ปิดการใช้งาน popGesture
```bash
GetPage(
  name: '/noPopGesture',
  page: () => NoPopGesturePage(),
  popGesture: false,
)
```

การกำหนด route พร้อม transition
```bash
GetPage(
  name: '/details',
  page: () => DetailsPage(),
  transition: Transition.fade,
)
```

การกำหนด route ให้เป็น fullscreenDialog
```bash
GetPage(
  name: '/fullscreenDialog',
  page: () => FullscreenDialogPage(),
  fullscreenDialog: true,
)
```

การกำหนด route พร้อม middlewares
```bash
GetPage(
  name: '/withMiddleware',
  page: () => WithMiddlewarePage(),
  middlewares: [
    AuthMiddleware(),
  ],
)
```

การกำหนด route พร้อม parameters
```bash
GetPage(
  name: '/product/:id',
  page: () => ProductPage(),
)
```

รับข้อมูล
```bash
class ProductPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    final String? productId = Get.parameters['id'];

    return Scaffold(
      appBar: AppBar(title: Text("Product Details")),
      body: Center(
        child: Text('Product ID: $productId'),
      ),
    );
  }
}

```

การเปลี่ยนไปยังหน้าถัดไป
```bash
Get.to(YourPage());
```

การเปลี่ยนไปยังหน้าถัดไปด้วยชื่อ route
```bash
Get.toNamed('/yourRouteName');
```

การกลับมายังหน้าก่อนหน้า
```bash
Get.back();
```

การเปลี่ยนไปยังหน้าและไม่ต้องการย้อนกลับ (เป็นการปิดหน้าปัจจุบันและเปิดหน้าใหม่)
```bash
Get.off(YourPage());
```

การเปลี่ยนไปยังหน้าด้วยชื่อ route และไม่ต้องการย้อนกลับ
```bash
Get.offNamed('/yourRouteName');
```

การเปลี่ยนไปยังหน้าแรก (เป็นการปิดหน้าทั้งหมดและเปิดหน้าใหม่เป็นหน้าแรก)
```bash
Get.offAll(YourHomePage());
```

การเปลี่ยนไปยังหน้าแรกด้วยชื่อ route
```bash
Get.offAllNamed('/homeRouteName');
```

การส่งข้อมูลระหว่างหน้า
```bash
Get.to(YourPage(), arguments: yourData);
```

และใน YourPage สามารถรับข้อมูลได้โดยใช้
```bash
var data = Get.arguments;
```

การใช้ binding
```bash
Get.to(YourPage(), binding: YourBinding());
```

การเปลี่ยนไปยังหน้าถัดไปโดยมี transition
```bash
Get.to(YourPage(), transition: Transition.zoom);
```
