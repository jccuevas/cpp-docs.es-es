---
title: "continuar la instrucción) (C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- continue
- continue_cpp
dev_langs:
- C++
helpviewer_keywords:
- continue keyword [C++]
ms.assetid: 3c94ee57-f732-4c1d-8537-d0ce5382bfd4
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 502254adc8b01966182f911af5a0dce8af36c1f3
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="continue-statement-c"></a>continue (Instrucción) (C++)
Fuerza la transferencia del control a la expresión de control de los más pequeño [hacer](../cpp/do-while-statement-cpp.md), [para](../cpp/for-statement-cpp.md), o [mientras](../cpp/while-statement-cpp.md) bucle.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
continue;  
```  
  
## <a name="remarks"></a>Comentarios  
 No se ejecuta ninguna de las instrucciones restantes de la iteración actual. La siguiente iteración del bucle se determina del modo siguiente:  
  
-   En un bucle `do` o `while`, la siguiente iteración se inicia reevaluando la expresión de control de la instrucción `do` o `while`.  
  
-   En un bucle `for` (que use la sintaxis `for`(`init-expr`; `cond-expr`; `loop-expr`)), se ejecuta la cláusula `loop-expr`. A continuación, se evalúa de nuevo la cláusula `cond-expr` y, en función del resultado, el bucle finaliza o se produce otra iteración.  
  
 En el ejemplo siguiente se muestra cómo se puede usar la instrucción `continue` para omitir secciones de código e iniciar la siguiente iteración de un bucle.  
  
## <a name="example"></a>Ejemplo  
  
```  
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
