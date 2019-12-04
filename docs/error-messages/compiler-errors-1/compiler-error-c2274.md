---
title: Error del compilador C2274
ms.date: 11/04/2016
f1_keywords:
- C2274
helpviewer_keywords:
- C2274
ms.assetid: 8e874903-f499-45ef-8291-f821eee4cc1c
ms.openlocfilehash: fd807dedb6c300860611d07212b8fc8952a90a65
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758676"
---
# <a name="compiler-error-c2274"></a>Error del compilador C2274

' type ': no es válido como lado derecho del operador '. '

Un tipo aparece como el operando derecho de un operador de acceso a miembros (.).

Este error puede deberse a un intento de obtener acceso a una conversión de tipo definido por el usuario. Use la palabra clave `operator` entre el punto y el `type`.

El ejemplo siguiente genera la advertencia C2286:

```cpp
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
