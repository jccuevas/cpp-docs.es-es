---
title: do-while (instrucción de C++)
ms.date: 11/04/2016
f1_keywords:
- do_cpp
helpviewer_keywords:
- do keyword [C++], do-while
- do-while keyword [C++]
- do keyword [C++]
- while keyword [C++], do-while
ms.assetid: e01e6f7c-7da1-4591-87f9-c26ff848e7b0
ms.openlocfilehash: f52c065210a8861dc065508248a506770b039b1d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189278"
---
# <a name="do-while-statement-c"></a>do-while (instrucción de C++)

Ejecuta una *instrucción* varias veces hasta que la condición de finalización especificada (la *expresión*) se evalúa como cero.

## <a name="syntax"></a>Sintaxis

```
do
   statement
while ( expression ) ;
```

## <a name="remarks"></a>Observaciones

La prueba de la condición de finalización se realiza después de cada ejecución del bucle. por lo tanto, un bucle **do-while** se ejecuta una o más veces, dependiendo del valor de la expresión de finalización. La instrucción **do-while** también puede finalizar cuando se ejecuta una instrucción [break](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md) o [return](../cpp/return-statement-cpp.md) dentro del cuerpo de la instrucción.

*expression* debe tener un tipo aritmético o de puntero. La ejecución continúa de la siguiente manera:

1. Se ejecuta el cuerpo de instrucción.

1. A continuación, se evalúa *expression*. Si *expression* es false, la instrucción **do-while** finaliza y el control pasa a la siguiente instrucción del programa. Si *expression* es true (distinta de cero), el proceso se repite a partir del paso 1.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra la instrucción **do-while** :

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

## <a name="see-also"></a>Consulte también

[Instrucciones de iteración](../cpp/iteration-statements-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[while (Instrucción) (C++)](../cpp/while-statement-cpp.md)<br/>
[for (Instrucción) (C++)](../cpp/for-statement-cpp.md)<br/>
[Instrucción for basada en intervalo (C++)](../cpp/range-based-for-statement-cpp.md)
