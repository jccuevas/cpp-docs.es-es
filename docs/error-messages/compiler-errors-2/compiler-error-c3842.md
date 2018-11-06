---
title: Error del compilador C3842
ms.date: 11/04/2016
f1_keywords:
- C3842
helpviewer_keywords:
- C3842
ms.assetid: 41a1a44a-c618-40a2-8d26-7da27d14095d
ms.openlocfilehash: a61a69aca53f7f8996d0261a57b749930ecc01cc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638352"
---
# <a name="compiler-error-c3842"></a>Error del compilador C3842

'function': no se admiten calificadores 'const' y 'volatile' en funciones miembro de WinRT o tipos administrados

[Const](../../cpp/const-cpp.md) y [volátil](../../cpp/volatile-cpp.md) no se admiten en las funciones miembro de Windows en tiempo de ejecución o tipos administrados.

El siguiente ejemplo genera el error C3842:

```
// C3842a.cpp
// compile with: /clr /c
public ref struct A {
   void f() const {}   // C3842
   void f() volatile {}   // C3842

   void f() {}
};
```