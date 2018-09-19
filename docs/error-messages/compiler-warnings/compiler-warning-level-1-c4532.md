---
title: Compilador advertencia (nivel 1) C4532 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4532
dev_langs:
- C++
helpviewer_keywords:
- C4532
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 717af9626866fb20e92342fe90f4dde2b5030774
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025482"
---
# <a name="compiler-warning-level-1-c4532"></a>Advertencia del compilador (nivel 1) C4532

'continue': salto fuera del bloque __finally/finally tiene un comportamiento indefinido durante el control de finalización

El compilador encontró una de las siguientes palabras clave:

- [continue](../../cpp/continue-statement-cpp.md)

- [break](../../cpp/break-statement-cpp.md)

- [goto](../../cpp/goto-statement-cpp.md)

causando un salto fuera de un [__finally](../../cpp/try-finally-statement.md) o [finalmente](../../dotnet/finally.md) bloque durante la terminación anormal.

Si se produce una excepción, y mientras se está desenredando la pila durante la ejecución de los controladores de finalización (el `__finally` o bloques finally), y el código salta fuera de un `__finally` bloquear antes de la `__finally` bloque finaliza, el comportamiento es indefinido. Control no puede volver al código de desenredado, por lo que es posible que no se controla correctamente la excepción.

Si debe saltar fuera de un **__finally** bloquear, busque en primer lugar una finalización anómala.

El ejemplo siguiente genera la advertencia C4532; simplemente marque como comentario las instrucciones de salto para resolver las advertencias.

```
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