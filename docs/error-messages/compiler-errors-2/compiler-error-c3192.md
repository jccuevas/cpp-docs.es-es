---
title: Error del compilador C3192
ms.date: 11/04/2016
f1_keywords:
- C3192
helpviewer_keywords:
- C3192
ms.assetid: 8b0083d4-706f-46f6-858a-e1d9af464cf8
ms.openlocfilehash: 685657857b2ed41c29c704633b07dc677fc32fc3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481112"
---
# <a name="compiler-error-c3192"></a>Error del compilador C3192

error de sintaxis: ' ^' no es un operador de prefijo (¿pretendía utilizar ' *'?)

No se puede usar un identificador como un operador de desreferenciación.

El ejemplo siguiente genera C3192:

```
// C3192.cpp
// compile with: /clr
using namespace System;

ref class MyClass {
public:
   MyClass () {}
   MyClass(MyClass%) {}
};

int main() {
   MyClass ^ s = gcnew MyClass;
   MyClass b = ^s;   // C3192

   // OK
   MyClass b2 = *s;
}
```