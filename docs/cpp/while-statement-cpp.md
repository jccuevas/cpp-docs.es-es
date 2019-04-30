---
title: while (Instrucción) (C++)
ms.date: 11/04/2016
f1_keywords:
- while_cpp
helpviewer_keywords:
- while keyword [C++]
- while keyword [C++], syntax
ms.assetid: 358dbe76-5e5e-4af5-b575-c2293c636899
ms.openlocfilehash: 669618e9807109be18117968b1f5b6f49ec15e07
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325421"
---
# <a name="while-statement-c"></a>while (Instrucción) (C++)

Ejecuta *instrucción* repetidamente hasta que *expresión* se evalúa como cero.

## <a name="syntax"></a>Sintaxis

```
while ( expression )
   statement
```

## <a name="remarks"></a>Comentarios

La prueba de *expresión* tiene lugar antes de cada ejecución del bucle; por lo tanto, un **mientras** bucle ejecuta cero o más veces. *expresión* debe ser de un tipo entero, un tipo de puntero, o un tipo de clase con una conversión no ambigua a un entero o un tipo de puntero.

Un **mientras** bucle también puede finalizar cuando un [salto](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md), o [devolver](../cpp/return-statement-cpp.md) dentro de la instrucción se ejecuta el cuerpo. Use [continuar](../cpp/continue-statement-cpp.md) para finalizar la iteración actual sin salir del **mientras** bucle. **continuar** pasa el control a la siguiente iteración de la **mientras** bucle.

El siguiente código utiliza un **mientras** caracteres de subrayado de bucle para recortar los finales de una cadena:

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

## <a name="see-also"></a>Vea también

[Instrucciones de iteración](../cpp/iteration-statements-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[do-while (Instrucción) (C++)](../cpp/do-while-statement-cpp.md)<br/>
[for (Instrucción) (C++)](../cpp/for-statement-cpp.md)<br/>
[Instrucción for basada en intervalo (C++)](../cpp/range-based-for-statement-cpp.md)