---
title: goto (instrucción (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- goto_cpp
dev_langs:
- C++
helpviewer_keywords:
- goto keyword [C++]
ms.assetid: 724c5deb-2de1-42d8-8ef1-23589d9bf5ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 52e3bbd026a00306fb2d8e69df94fd9c0c913039
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="goto-statement-c"></a>goto (Instrucción) (C++)
La instrucción `goto` transfiere incondicionalmente el control a la instrucción etiquetada por el identificador especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
goto identifier;  
```  
  
## <a name="remarks"></a>Comentarios  
 La instrucción con etiqueta designada por `identifier` debe estar en la función actual. Todos los nombres de `identifier` son miembros de un espacio de nombres interno y, por tanto, no interfieren con otros identificadores.  
  
 Una etiqueta de instrucción solo es significativa para una instrucción `goto`; de lo contrario, se omiten las etiquetas de instrucciones. Las etiquetas no se pueden volver a declarar.  
  
 Un buen estilo de programación consiste en utilizar las instrucciones `break`, `continue` y `return` en lugar de la instrucción `goto` siempre que sea posible. Sin embargo, puesto que la instrucción `break` sale de un solo nivel de un bucle, puede que tenga que utilizar una instrucción `goto` para salir de un bucle anidado profundamente.  
  
 Para obtener más información sobre las etiquetas y la `goto` instrucción, consulte [instrucciones con etiquetas](../cpp/labeled-statements.md) y [usar etiquetas con la instrucción goto](http://msdn.microsoft.com/en-us/6cd7c31a-9822-4241-8566-f79f51be48fe).  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, una instrucción `goto` transfiere el control al punto con la etiqueta `stop` cuando `i` es igual a 3.  
  
```  
// goto_statement.cpp  
#include <stdio.h>  
int main()  
{  
    int i, j;  
  
    for ( i = 0; i < 10; i++ )  
    {  
        printf_s( "Outer loop executing. i = %d\n", i );  
        for ( j = 0; j < 2; j++ )  
        {  
            printf_s( " Inner loop executing. j = %d\n", j );  
            if ( i == 3 )  
                goto stop;  
        }  
    }  
  
    // This message does not print:   
    printf_s( "Loop exited. i = %d\n", i );  
  
    stop:   
    printf_s( "Jumped to stop. i = %d\n", i );  
}  
```  
  
```Output  
Outer loop executing. i = 0  
 Inner loop executing. j = 0  
 Inner loop executing. j = 1  
Outer loop executing. i = 1  
 Inner loop executing. j = 0  
 Inner loop executing. j = 1  
Outer loop executing. i = 2  
 Inner loop executing. j = 0  
 Inner loop executing. j = 1  
Outer loop executing. i = 3  
 Inner loop executing. j = 0  
Jumped to stop. i = 3  
```  
  
## <a name="see-also"></a>Vea también  
 [Jump Statements](../cpp/jump-statements-cpp.md)  (Instrucciones de salto)  
 [Palabras clave](../cpp/keywords-cpp.md)