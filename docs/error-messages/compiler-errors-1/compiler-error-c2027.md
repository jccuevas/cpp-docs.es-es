---
title: Error del compilador C2027
ms.date: 11/04/2016
f1_keywords:
- C2027
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
ms.openlocfilehash: 901e9b791616c5684b352c1fda7687f67b895d9c
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447372"
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

Es posible declarar un puntero a un tipo declarado pero no definido. Pero C++ no permite una referencia a un tipo no definido.

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