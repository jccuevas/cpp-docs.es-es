---
title: Error del compilador C2774
ms.date: 11/04/2016
f1_keywords:
- C2774
helpviewer_keywords:
- C2774
ms.assetid: 10f428c6-7f49-489a-92ba-6ef978b7caaf
ms.openlocfilehash: 2630dba6a74bf6b31a5df7af57e42fd7c8fd4e09
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740109"
---
# <a name="compiler-error-c2774"></a>Error del compilador C2774

' Identifier ': no hay ningún método ' Put ' asociado a esta propiedad

Un miembro de datos declarado con la [propiedad](../../cpp/property-cpp.md) no tiene `put` función, pero una expresión intenta establecer su valor.

En el ejemplo siguiente se genera C2774:

```cpp
// C2774.cpp
struct A {
   __declspec(property(get=GetProp)) int prop;
   int GetProp(void);

   __declspec(property(get=GetProp2, put=PutProp2)) int prop2;
   int GetProp2(void);
   void PutProp2(int);
};

int main() {
   A* pa = new A;
   int val = 0;
   pa->prop = val;   // C2774
   pa->prop++;   // C2774
}
```
