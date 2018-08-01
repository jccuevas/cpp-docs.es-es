---
title: Continue (instrucción (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- continue_cpp
dev_langs:
- C++
helpviewer_keywords:
- continue keyword [C++]
ms.assetid: 3c94ee57-f732-4c1d-8537-d0ce5382bfd4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d0ab1e052b3e6d843813c33e5444fc3c08796d00
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402096"
---
# <a name="continue-statement-c"></a>continue (Instrucción) (C++)
Fuerza la transferencia del control a la expresión de control de los más pequeño incluye [hacer](../cpp/do-while-statement-cpp.md), [para](../cpp/for-statement-cpp.md), o [mientras](../cpp/while-statement-cpp.md) bucle.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
continue;  
```  
  
## <a name="remarks"></a>Comentarios  
 No se ejecuta ninguna de las instrucciones restantes de la iteración actual. La siguiente iteración del bucle se determina del modo siguiente:  
  
-   En un **hacer** o **mientras** bucle, la siguiente iteración empieza evaluando la expresión de control de la **hacer** o **mientras** instrucción.  
  
-   En un **para** bucle (mediante la sintaxis `for`(`init-expr`; `cond-expr`; `loop-expr`)), el `loop-expr` cláusula se ejecuta. A continuación, se evalúa de nuevo la cláusula `cond-expr` y, en función del resultado, el bucle finaliza o se produce otra iteración.  
  
 El ejemplo siguiente se muestra cómo el **continuar** instrucción puede utilizarse para omitir secciones de código y comenzar la siguiente iteración de un bucle.  
  
## <a name="example"></a>Ejemplo  
  
```cpp 
// continue_statement.cpp  
#include <stdio.h>  
int main()  
{  
    int i = 0;  
    do  
    {  
        i++;  
        printf_s("before the continue\n");  
        continue;  
        printf("after the continue, should never print\n");  
     } while (i < 3);  
  
     printf_s("after the do loop\n");  
}  
```  
  
```Output  
before the continue  
before the continue  
before the continue  
after the do loop  
```  
  
## <a name="see-also"></a>Vea también  
 [Jump Statements](../cpp/jump-statements-cpp.md)  (Instrucciones de salto)  
 [Palabras clave](../cpp/keywords-cpp.md)