---
title: "hacer-while (instrucción (C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
caps.latest.revision: 9
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
ms.openlocfilehash: 8c81bbeea9f841a834d59186017b2932f83de862
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

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
