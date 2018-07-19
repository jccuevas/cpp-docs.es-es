---
title: Instrucción goto (C++) | Microsoft Docs
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
ms.openlocfilehash: 7676f38e52734fa2f0ce8ecbc9b268be1939f6dc
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953400"
---
# <a name="goto-statement-c"></a>goto (Instrucción) (C++)
El **goto** instrucción transfiere incondicionalmente el control a la instrucción etiquetada por el identificador especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
goto identifier;  
```  
  
## <a name="remarks"></a>Comentarios  
 La instrucción con etiqueta designada por `identifier` debe estar en la función actual. Todos los nombres de `identifier` son miembros de un espacio de nombres interno y, por tanto, no interfieren con otros identificadores.  
  
 Una etiqueta de instrucción solo es significativa para un **goto** instrucción; de lo contrario, se omiten las etiquetas de instrucción. Las etiquetas no se pueden volver a declarar.  
  
 Es una buena programación de estilo que se usará el **salto**, **continuar**, y **devolver** instrucciones en lugar de la **goto** instrucción cada vez que es posible. Sin embargo, dado que el **salto** instrucción sale de un solo nivel de un bucle, es posible que deba usar un **goto** instrucción para salir de un bucle profundamente anidado.  
  
 Para obtener más información acerca de las etiquetas y la **goto** instrucción, consulte [instrucciones con etiquetas](../cpp/labeled-statements.md).  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, un **goto** instrucción transfiere el control al punto con la etiqueta `stop` cuando `i` es igual a 3.  
  
```cpp  
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