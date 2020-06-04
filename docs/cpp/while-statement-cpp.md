---
title: while (Instrucción) (C++)
ms.date: 11/04/2016
f1_keywords:
- while_cpp
helpviewer_keywords:
- while keyword [C++]
- while keyword [C++], syntax
ms.assetid: 358dbe76-5e5e-4af5-b575-c2293c636899
ms.openlocfilehash: 0dfbbb2865c9cf0a23b04ce213a0e739e29c27da
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187328"
---
# <a name="while-statement-c"></a>while (Instrucción) (C++)

Ejecuta la *instrucción* repetidamente hasta que la *expresión* se evalúa como cero.

## <a name="syntax"></a>Sintaxis

```
while ( expression )
   statement
```

## <a name="remarks"></a>Observaciones

La prueba de *Expression* tiene lugar antes de cada ejecución del bucle; por lo tanto, un bucle **While** se ejecuta cero o más veces. la *expresión* debe ser de un tipo entero, un tipo de puntero o un tipo de clase con una conversión no ambigua a un tipo entero o de puntero.

Un bucle **While** también puede finalizar cuando se ejecuta [break](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md)o [Return](../cpp/return-statement-cpp.md) dentro del cuerpo de la instrucción. Use [continuar](../cpp/continue-statement-cpp.md) para finalizar la iteración actual sin salir del bucle **While** . **continue** pasa el control a la siguiente iteración del bucle **While** .

En el código siguiente se usa un bucle **While** para recortar los guiones bajos finales de una cadena:

```cpp
// while_statement.cpp

#include <string.h>
#include <stdio.h>
char *trim( char *szSource )
{
    char *pszEOS = 0;

    //  Set pointer to character before terminating NULL
    pszEOS = szSource + strlen( szSource ) - 1;

    //  iterate backwards until non '_' is found
    while( (pszEOS >= szSource) && (*pszEOS == '_') )
        *pszEOS-- = '\0';

    return szSource;
}
int main()
{
    char szbuf[] = "12345_____";

    printf_s("\nBefore trim: %s", szbuf);
    printf_s("\nAfter trim: %s\n", trim(szbuf));
}
```

La condición de finalización se evalúa al principio del bucle. Si no hay ningún carácter de subrayado final, el bucle nunca se ejecuta.

## <a name="see-also"></a>Consulte también

[Instrucciones de iteración](../cpp/iteration-statements-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[do-while (Instrucción) (C++)](../cpp/do-while-statement-cpp.md)<br/>
[for (Instrucción) (C++)](../cpp/for-statement-cpp.md)<br/>
[Instrucción for basada en intervalo (C++)](../cpp/range-based-for-statement-cpp.md)
