---
title: goto e instrucciones con etiquetas (C)
ms.date: 11/04/2016
f1_keywords:
- goto
helpviewer_keywords:
- labeled statement
- statements, labeled
- goto keyword [C]
ms.assetid: 3d0473dc-4b18-4fcc-9616-31a38499d7d7
ms.openlocfilehash: b23e7e6310ba4ed968e2eac8e6d07d81ee4e79ba
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151954"
---
# <a name="goto-and-labeled-statements-c"></a>goto e instrucciones con etiquetas (C)

La instrucción `goto` transfiere el control a una etiqueta. La etiqueta especificada debe estar en la misma función y puede aparecer delante de una sola instrucción en la misma función.

## <a name="syntax"></a>Sintaxis

*statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*labeled-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*jump-statement*

*jump-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**goto**  *identifier*  **;**

*labeled-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*  **:**  *statement*

Una etiqueta de instrucción solo tiene sentido en una instrucción `goto`; en cualquier otro contexto, una instrucción con etiqueta se ejecuta sin tener en cuenta la etiqueta.

Un elemento *jump-statement* debe estar en la misma función y puede aparecer delante de una sola instrucción en la misma función. El conjunto de nombres de *identifier* que siguen a `goto` tiene su propio espacio de nombres, por lo que los nombres no interfieren con otros identificadores. Las etiquetas no se pueden volver a declarar. Para más información, vea [Espacios de nombres](../c-language/name-spaces.md).

Una práctica de programación recomendada es usar la instrucción **break**, **continue** y `return` en lugar de `goto` siempre que sea posible. Como la instrucción **break** solo sale de un nivel del bucle, puede ser necesario usar `goto` para salir de un bucle profundamente anidado.

En este ejemplo se muestra la instrucción `goto`:

```
// goto.c
#include <stdio.h>

int main()
{
    int i, j;

    for ( i = 0; i < 10; i++ )
    {
        printf_s( "Outer loop executing. i = %d\n", i );
        for ( j = 0; j < 3; j++ )
        {
            printf_s( " Inner loop executing. j = %d\n", j );
            if ( i == 5 )
                goto stop;
        }
    }

    /* This message does not print: */
    printf_s( "Loop exited. i = %d\n", i );

    stop: printf_s( "Jumped to stop. i = %d\n", i );
}
```

En este ejemplo, una instrucción `goto` transfiere el control al punto con la etiqueta `stop` cuando `i` es igual a 5.

## <a name="see-also"></a>Vea también

[Instrucciones](../c-language/statements-c.md)
