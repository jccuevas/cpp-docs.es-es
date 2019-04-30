---
title: Error del compilador C2272
ms.date: 11/04/2016
f1_keywords:
- C2272
helpviewer_keywords:
- C2272
ms.assetid: 1517706a-9c27-452e-9b10-3424b3d232bc
ms.openlocfilehash: 1a5a1e47a721cb6edd795012cc45943e63708936
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388896"
---
# <a name="compiler-error-c2272"></a>Error del compilador C2272

'function': modificadores no permitidos en funciones miembro static

Un `static` función miembro se declara con un especificador de modelo de memoria, como [const](../../cpp/const-cpp.md) o [volátil](../../cpp/volatile-cpp.md), y no se permiten estos modificadores en `static` funciones miembro.

El ejemplo siguiente genera C2272:

```
// C2272.cpp
// compile with: /c
class CMyClass {
public:
   static void func1() const volatile;   // C2272  func1 is static
   void func2() const volatile;   // OK
};
```