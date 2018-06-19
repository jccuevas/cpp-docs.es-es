---
title: Compilador advertencia (nivel 1) C4750 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4750
dev_langs:
- C++
helpviewer_keywords:
- C4750
ms.assetid: b0b2c938-7d2a-4c36-8270-7daee15ffee3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ffe378f8d2466e702c90127e44f3b48831abf50
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282449"
---
# <a name="compiler-warning-level-1-c4750"></a>Advertencia del compilador (nivel 1) C4750
'identificador': función con _alloca() insertada en un bucle  
  
 La función 'identificador' fuerza la expansión inline de la función [_alloca](../../c-runtime-library/reference/alloca.md) dentro de un bucle, lo que podría producir un desbordamiento de pila cuando se ejecuta el bucle.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Asegúrese de que la función 'identificador' no se modifica con el especificador [__forceinline](../../cpp/inline-functions-cpp.md) .  
  
2.  Asegúrese de que la función 'identificador' no contiene una función [_alloca](../../c-runtime-library/reference/alloca.md) que se está contenida en un bucle.  
  
3.  No especifique el modificador de compilación [/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md), [/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md), [/Ox](../../build/reference/ox-full-optimization.md)u [/Og](../../build/reference/og-global-optimizations.md) .  
  
4.  Coloque la función [_alloca](../../c-runtime-library/reference/alloca.md) en una [instrucción try-except](../../cpp/try-except-statement.md) que detectará un desbordamiento de pila.  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo de código llama a `MyFunction` en un bucle y `MyFunction` llama a la función `_alloca` . El modificador `__forceinline` hace que la expansión inline de la función `_alloca` .  
  
```  
// c4750.cpp  
// compile with: /O2 /W1 /c  
#include <intrin.h>  
  
char * volatile newstr;  
  
__forceinline void myFunction(void) // C4750 warning  
{  
// The _alloca function does not require a __try/__except   
// block because the example uses compiler option /c.  
    newstr = (char * volatile) _alloca(1000);  
}  
  
int main(void)  
{  
    for (int i=0; i<50000; i++)  
       myFunction();  
    return 0;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [_alloca](../../c-runtime-library/reference/alloca.md)