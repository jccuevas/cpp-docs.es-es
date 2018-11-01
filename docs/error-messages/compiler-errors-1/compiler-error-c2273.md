---
title: Error del compilador C2273
ms.date: 11/04/2016
f1_keywords:
- C2273
helpviewer_keywords:
- C2273
ms.assetid: 3c682c66-97bf-4a23-a22c-d9a26a92bf95
ms.openlocfilehash: f2ed5c49a9f8243fd5c9c302caf2876493c26bc3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526419"
---
# <a name="compiler-error-c2273"></a>Error del compilador C2273

'type': no es válido como lado derecho del operador '->'

Aparece un tipo como operando derecho de un `->` operador.

Este error puede deberse a intentar obtener acceso a una conversión de tipo definido por el usuario. Use la palabra clave `operator` entre -> y `type`.

El ejemplo siguiente genera C2273:

```
// C2273.cpp
struct MyClass {
   operator int() {
      return 0;
   }
};
int main() {
   MyClass * ClassPtr = new MyClass;
   int i = ClassPtr->int();   // C2273
   int j = ClassPtr-> operator int();   // OK
}
```