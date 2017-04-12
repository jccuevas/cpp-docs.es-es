---
title: Compilador advertencia (nivel 1) C4750 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4750
dev_langs:
- C++
helpviewer_keywords:
- C4750
ms.assetid: b0b2c938-7d2a-4c36-8270-7daee15ffee3
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 84f0628de933344eb23dc6325679abdcd3699c3a
ms.openlocfilehash: 6e22ef89b92a5b584979abbd370f82b482cf74e0
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4750"></a>Advertencia del compilador (nivel 1) C4750
'identificador': función con _alloca() insertada en un bucle  
  
 La función 'identificador' fuerza la expansión en línea de la [_alloca](../../c-runtime-library/reference/alloca.md) función dentro de un bucle, lo que podría producir un desbordamiento de pila cuando se ejecuta el bucle.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Asegúrese de que la función 'identificador' no se modifica con el [__forceinline](../../cpp/inline-functions-cpp.md) especificador.  
  
2.  Asegúrese de que la función 'identificador' no contiene una [_alloca](../../c-runtime-library/reference/alloca.md) función que se encuentra en un bucle.  
  
3.  No se especifica la [/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md), [/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md), [/Ox](../../build/reference/ox-full-optimization.md), o [/Og](../../build/reference/og-global-optimizations.md) modificador de compilación.  
  
4.  Colocar el [_alloca](../../c-runtime-library/reference/alloca.md) funcionan en un [intente-excepto la instrucción](../../cpp/try-except-statement.md) que detectará un desbordamiento de pila.  
  
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
