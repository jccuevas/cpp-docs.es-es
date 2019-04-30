---
title: Error del compilador C2027
ms.date: 11/04/2016
f1_keywords:
- C2027
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
ms.openlocfilehash: 3f3fac9d5410595fe5653e257d97d2fd7c858545
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303494"
---
# <a name="compiler-error-c2027"></a>Error del compilador C2027

el uso de un tipo no definido 'type'

No se puede usar un tipo hasta que se define. Para resolver el error, asegúrese de que el tipo se define completamente antes de hacer referencia a ella.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2027.

```
// C2027.cpp
class C;
class D {
public:
   void func() {
   }
};

int main() {
   C *pC;
   pC->func();   // C2027

   D *pD;
   pD->func();
}
```

## <a name="example"></a>Ejemplo

Es posible declarar un puntero a un tipo declarado pero no definido.  Pero Visual C++ no permite una referencia a un tipo no definido.

El ejemplo siguiente genera C2027.

```
// C2027_b.cpp
class A;
A& CreateA();

class B;
B* CreateB();

int main() {
   CreateA();   // C2027
   CreateB();   // OK
}
```