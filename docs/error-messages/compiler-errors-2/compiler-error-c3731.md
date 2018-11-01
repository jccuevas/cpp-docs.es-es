---
title: Error del compilador C3731
ms.date: 11/04/2016
f1_keywords:
- C3731
helpviewer_keywords:
- C3731
ms.assetid: 45f89fcd-464c-4bc8-8a42-edcb5416d26c
ms.openlocfilehash: 5acc33869648f83cd44bc557128c685f521ddf88
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496062"
---
# <a name="compiler-error-c3731"></a>Error del compilador C3731

evento incompatible 'función1' y el controlador 'function2'; origen del evento y controlador de eventos deben ser del mismo tipo

El origen del evento y el receptor de eventos deben tener el mismo tipo (por ejemplo `native` frente a `com` tipos). Para corregir este error, asegúrese de los tipos de origen del evento y la coincidencia de controlador de eventos.

El ejemplo siguiente genera C3731:

```
// C3731.cpp
// compile with: /clr
#using <mscorlib.dll>
[event_source(native)]
struct A {
   __event void MyEvent();
};

[event_receiver(managed)]
// try the following line instead
// [event_receiver(native)]
struct B {
   void func();
   B(A a) {
      __hook(&A::MyEvent, &a, &B::func);   // C3731
   }
};

int main() {
}
```