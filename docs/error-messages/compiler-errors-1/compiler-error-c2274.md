---
title: Error del compilador C2274
ms.date: 11/04/2016
f1_keywords:
- C2274
helpviewer_keywords:
- C2274
ms.assetid: 8e874903-f499-45ef-8291-f821eee4cc1c
ms.openlocfilehash: f2fcb75098f18ad113ba68959035b37d9cddd6e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667030"
---
# <a name="compiler-error-c2274"></a>Error del compilador C2274

'type': no es válido como lado derecho de '.' operador

Aparece un tipo como operando derecho de un operador de acceso a miembros (.).

Este error puede deberse a intentar obtener acceso a una conversión de tipo definido por el usuario. Use la palabra clave `operator` entre el período y `type`.

El ejemplo siguiente genera la advertencia C2286:

```
// C2274.cpp
struct MyClass {
   operator int() {
      return 0;
   }
};

int main() {
   MyClass ClassName;
   int i = ClassName.int();   // C2274
   int j = ClassName.operator int();   // OK
}
```