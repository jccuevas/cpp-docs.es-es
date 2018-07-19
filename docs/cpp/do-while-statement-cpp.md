---
title: hacer-while (instrucción (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- do_cpp
dev_langs:
- C++
helpviewer_keywords:
- do keyword [C++], do-while
- do-while keyword [C++]
- do keyword [C++]
- while keyword [C++], do-while
ms.assetid: e01e6f7c-7da1-4591-87f9-c26ff848e7b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d2de180d58c31f4bd6c8b15eb69076b99f8b57b0
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37944613"
---
# <a name="do-while-statement-c"></a>do-while (instrucción de C++)
Ejecuta un *instrucción* repetidamente hasta que la condición de finalización (el *expresión*) se evalúa como cero.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
do  
   statement  
while ( expression ) ;  
```  
  
## <a name="remarks"></a>Comentarios  
 La prueba de la condición de finalización se realiza después de cada ejecución del bucle; por lo tanto, un **hacer-mientras** bucle ejecuta una o varias veces, dependiendo del valor de la expresión de finalización. El **hacer-mientras** instrucción también puede finalizar cuando un [salto](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md), o [devolver](../cpp/return-statement-cpp.md) instrucción se ejecuta dentro del cuerpo de instrucción.  
  
 *expression* debe tener un tipo aritmético o de puntero. La ejecución continúa de la siguiente manera:  
  
1.  Se ejecuta el cuerpo de instrucción.  
  
2.  A continuación, se evalúa *expression*. Si *expresión* es false, el **hacer-mientras** instrucción termina y el control pasa a la siguiente instrucción en el programa. Si *expression* es true (distinta de cero), el proceso se repite a partir del paso 1.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente se muestra el **hacer-mientras** instrucción:  
  
```cpp 
// do_while_statement.cpp  
#include <stdio.h>  
int main()  
{  
    int i = 0;  
    do  
    {  
        printf_s("\n%d",i++);  
    } while (i < 3);  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Iteration Statements](../cpp/iteration-statements-cpp.md)  (Instrucciones de iteración)  
 [Palabras clave](../cpp/keywords-cpp.md)   
 [while (Instrucción) (C++)](../cpp/while-statement-cpp.md)   
 [for (Instrucción) (C++)](../cpp/for-statement-cpp.md)   
 [Instrucción for basada en intervalo (C++)](../cpp/range-based-for-statement-cpp.md)