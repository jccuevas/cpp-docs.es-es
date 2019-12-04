---
title: Error del compilador C2027
ms.date: 11/04/2016
f1_keywords:
- C2027
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
ms.openlocfilehash: 62cf208d9d0025afba06d32a15b9a1e50777c473
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751006"
---
# <a name="compiler-error-c2027"></a>Error del compilador C2027

uso del tipo no definido ' tipo '

No se puede usar un tipo hasta que se haya definido. Para resolver el error, asegúrese de que el tipo está totalmente definido antes de hacer referencia a él.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2027.

```cpp
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

Es posible declarar un puntero a un tipo declarado pero no definido. Pero C++ no permite una referencia a un tipo sin definir.

En el ejemplo siguiente se genera C2027.

```cpp
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
