---
title: Error del compilador C2272
ms.date: 11/04/2016
f1_keywords:
- C2272
helpviewer_keywords:
- C2272
ms.assetid: 1517706a-9c27-452e-9b10-3424b3d232bc
ms.openlocfilehash: fd6fdecd3a491ce5f068f4d51d413e6767aabe2f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758702"
---
# <a name="compiler-error-c2272"></a>Error del compilador C2272

' función ': modificadores no permitidos en funciones miembro estáticas

Un `static` función miembro se declara con un especificador de modelo de memoria, como [const](../../cpp/const-cpp.md) o [volatile](../../cpp/volatile-cpp.md), y tales modificadores no se permiten en `static` funciones miembro.

En el ejemplo siguiente se genera C2272:

```cpp
// C2272.cpp
// compile with: /c
class CMyClass {
public:
   static void func1() const volatile;   // C2272  func1 is static
   void func2() const volatile;   // OK
};
```
