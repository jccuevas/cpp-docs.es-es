---
title: Error del compilador C2352
ms.date: 11/04/2016
f1_keywords:
- C2352
helpviewer_keywords:
- C2352
ms.assetid: 0efad8cb-659f-4b3e-8f6f-9f8ec44d345c
ms.openlocfilehash: 387738faa5b55e60cbb9df2185efcb94098011d7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528757"
---
# <a name="compiler-error-c2352"></a>Error del compilador C2352

'class::function': llamada no válida de función miembro no estática

Una función miembro `static` llamó a una función miembro no estática. O bien, se llamó a una función miembro no estática desde fuera de la clase como una función estática.

El ejemplo siguiente genera el error C2352 y muestra cómo corregirlo:

```
// C2352.cpp
// compile with: /c
class CMyClass {
public:
   static void func1();
   void func2();
   static void func3() {
      func2();   // C2352 calls nonstatic func2
      func1();   // OK calls static func1
   }
};
```

El ejemplo siguiente genera el error C2352 y muestra cómo corregirlo:

```
// C2352b.cpp
class MyClass {
public:
   void MyFunc() {}
   static void MyFunc2() {}
};

int main() {
   MyClass::MyFunc();   // C2352
   MyClass::MyFunc2();   // OK
}
```