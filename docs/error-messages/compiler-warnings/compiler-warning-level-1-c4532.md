---
title: ADVERTENCIA del compilador (nivel 1) C4532
ms.date: 11/04/2016
f1_keywords:
- C4532
helpviewer_keywords:
- C4532
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
ms.openlocfilehash: b47eb192bc01e6fe2c6c9423ed2c672f16c6818f
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966248"
---
# <a name="compiler-warning-level-1-c4532"></a>ADVERTENCIA del compilador (nivel 1) C4532

' Continue ': saltar fuera de __finally bloque/Finally tiene un comportamiento indefinido durante el control de finalización

El compilador encontró una de las palabras clave siguientes:

- [continue](../../cpp/continue-statement-cpp.md)

- [break](../../cpp/break-statement-cpp.md)

- [goto](../../cpp/goto-statement-cpp.md)

producir un salto fuera de un bloque [__finally](../../cpp/try-finally-statement.md) o [Finally](../../dotnet/finally.md) durante una terminación anómala.

Si se produce una excepción y mientras se está desenredando la pila durante la ejecución de los controladores de finalización (los bloques `__finally` o Finally) y el código salta fuera de un bloque de `__finally` antes de que finalice el bloque de `__finally`, el comportamiento es indefinido. Es posible que el control no vuelva al código de desenredado, por lo que es posible que la excepción no se administre correctamente.

Si debe saltar fuera de un bloque **__finally** , compruebe primero la terminación anómala.

En el ejemplo siguiente se genera C4532; simplemente comente las instrucciones de salto para resolver las advertencias.

```cpp
// C4532.cpp
// compile with: /W1
// C4532 expected
int main() {
   int i;
   for (i = 0; i < 10; i++) {
      __try {
      } __finally {
         // Delete the following line to resolve.
         continue;
      }

      __try {
      } __finally {
         // Delete the following line to resolve.
         break;
      }
   }
}
```