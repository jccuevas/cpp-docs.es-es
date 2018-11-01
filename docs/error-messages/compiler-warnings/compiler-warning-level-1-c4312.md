---
title: Advertencia del compilador (nivel 1) C4312
ms.date: 11/04/2016
f1_keywords:
- C4312
helpviewer_keywords:
- C4312
ms.assetid: 541906ed-4f62-4bcb-947f-cf9ae7411bcb
ms.openlocfilehash: 666df7904a7aac88983af40d31a67271beaa0b1f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440240"
---
# <a name="compiler-warning-level-1-c4312"></a>Advertencia del compilador (nivel 1) C4312

'operación' : conversión de 'tipo1' a 'tipo2' de mayor tamaño

Esta advertencia detecta un intento de asignar un valor de 32 bits a un tipo de puntero de 64 bits, por ejemplo, la conversión de un valor `int` o `long` de 32 bits a un puntero de 64 bits.

Puede tratarse de una conversión no segura, incluso para los valores de puntero que se ajusten a 32 bits cuando se produce la extensión de signo. Si un entero negativo de 32 bits se asigna a un tipo de puntero de 64 bits, la extensión de signo provoca que el valor del puntero haga referencia a una dirección de memoria distinta a la del valor del entero.

Esta advertencia solo se genera para destinos de compilación de 64 bits. Para obtener más información, consulte [reglas para usar punteros](/windows/desktop/WinProg64/rules-for-using-pointers).

El ejemplo de código siguiente genera el error C4312 cuando se compila para destinos de 64 bits:

```
// C4312.cpp
// compile by using: cl /W1 /LD C4312.cpp
void* f(int i) {
   return (void*)i;   // C4312 for 64-bit targets
}

void* f2(__int64 i) {
   return (void*)i;   // OK
}
```