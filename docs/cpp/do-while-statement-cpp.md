---
title: "hacer-while (instrucción (C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: do_cpp
dev_langs: C++
helpviewer_keywords:
- do keyword [C++], do-while
- do-while keyword [C++]
- do keyword [C++]
- while keyword [C++], do-while
ms.assetid: e01e6f7c-7da1-4591-87f9-c26ff848e7b0
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b9ef52e04bd855824e709c66693cb989a18b1283
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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
 La prueba de la condición de finalización se realiza después de cada ejecución del bucle; por consiguiente, un bucle `do-while` se ejecuta una o más veces, dependiendo del valor de la expresión de finalización. El `do-while` instrucción también puede finalizar cuando un [salto](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md), o [devolver](../cpp/return-statement-cpp.md) instrucción se ejecuta dentro del cuerpo de instrucción.  
  
 *expression* debe tener un tipo aritmético o de puntero. La ejecución continúa de la siguiente manera:  
  
1.  Se ejecuta el cuerpo de instrucción.  
  
2.  A continuación, se evalúa *expression*. Si *expression* es false, la instrucción `do-while` finaliza y el control pasa a la siguiente instrucción del programa. Si *expression* es true (distinta de cero), el proceso se repite a partir del paso 1.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra la instrucción `do-while`:  
  
```  
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