---
title: ADVERTENCIA del compilador (nivel 1) C4313
ms.date: 11/04/2016
f1_keywords:
- C4313
helpviewer_keywords:
- C4313
ms.assetid: bcf64191-e2cf-452e-97b4-423fcec2d07c
ms.openlocfilehash: 4000ba2254c868bf9959a6f0fb6f8e76255f7590
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966078"
---
# <a name="compiler-warning-level-1-c4313"></a>ADVERTENCIA del compilador (nivel 1) C4313

'function': 'format specifier' en cadena de formato entra en conflicto con el número de argumento de tipo 'type'

Hay un conflicto entre el formato especificado y el valor que está pasando. Por ejemplo, ha pasado un parámetro de 64 bits a un especificador de formato %d sin calificar, que espera un parámetro de entero de 32 bits. Esta advertencia solo tiene efecto cuando el código se compila para destinos de 64 bits.

## <a name="example"></a>Ejemplo

El ejemplo de código siguiente genera el error C4313 cuando se compila para un destino de 64 bits.

```cpp
// C4313.cpp
// Compile by using: cl /W1 C4313.cpp
#include <stdio.h>
int main() {
   int * pI = 0;
   printf("%d", pI);   // C4313 on 64-bit platform code
   // Try one of the following lines instead:
   // printf("%p\n", pI);
   // printf("%Id\n", pI);   // %I64d expects 64-bits of information
}
```