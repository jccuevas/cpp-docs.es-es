---
title: Compilador advertencia (nivel 1) C4313 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4313
dev_langs:
- C++
helpviewer_keywords:
- C4313
ms.assetid: bcf64191-e2cf-452e-97b4-423fcec2d07c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: df3600483ee5c6fe2ec0f9a339ec7ce5b94569af
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090930"
---
# <a name="compiler-warning-level-1-c4313"></a>Advertencia del compilador (nivel 1) C4313

'function': 'format specifier' en cadena de formato entra en conflicto con el número de argumento de tipo 'type'

Hay un conflicto entre el formato especificado y el valor que está pasando. Por ejemplo, ha pasado un parámetro de 64 bits a un especificador de formato %d sin calificar, que espera un parámetro de entero de 32 bits. Esta advertencia solo tiene efecto cuando el código se compila para destinos de 64 bits.

## <a name="example"></a>Ejemplo

El ejemplo de código siguiente genera el error C4313 cuando se compila para un destino de 64 bits.

```
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