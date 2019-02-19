---
title: do-while (Instrucción) (C)
ms.date: 11/04/2016
f1_keywords:
- do
- while
helpviewer_keywords:
- do-while keyword [C]
ms.assetid: f2ac20a6-10c7-4a08-b5e3-c3b3639dbeaf
ms.openlocfilehash: 052b02beca49f5de19c6f68cc475edb5f5daf6e2
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147508"
---
# <a name="do-while-statement-c"></a>do-while (Instrucción) (C)

La instrucción *do-while* permite repetir una instrucción o una instrucción compuesta hasta que una expresión especificada sea false.

## <a name="syntax"></a>Sintaxis

*iteration-statement*: &nbsp;&nbsp;&nbsp;&nbsp;**do**  *statement*  **while (**  *expression*  **) ;**

El elemento *expression* en una instrucción *do-while* se evalúa después de que se ejecute el cuerpo del bucle. Por consiguiente, el cuerpo del bucle se ejecuta siempre al menos una vez.

*expression* debe tener un tipo aritmético o de puntero. La ejecución continúa de la siguiente manera:

1. Se ejecuta el cuerpo de instrucción.

1. A continuación, se evalúa *expression*. Si *expression* es false, la instrucción *do-while* finaliza y el control pasa a la siguiente instrucción del programa. Si *expression* es true (distinta de cero), el proceso se repite a partir del paso 1.

La instrucción *do-while* también puede finalizar cuando se ejecuta una instrucción **break**, **goto** o **return** dentro del cuerpo de la instrucción.

Este es un ejemplo de la instrucción *do-while*:

```C
do
{
    y = f( x );
    x--;
} while ( x > 0 );
```

En esta instrucción *do-while*, se ejecutan las dos instrucciones `y = f( x );` y `x--;` independientemente del valor inicial de `x`. A continuación `x > 0` se evalúa. Si `x` es mayor que 0, el cuerpo de instrucción se ejecuta de nuevo y `x > 0` se evalúa de nuevo. El cuerpo de instrucción se ejecuta repetidamente mientras `x` siga siendo mayor que 0. La ejecución de la instrucción *do-while* finaliza cuando `x` se convierte en 0 o negativo. El cuerpo del bucle se ejecuta al menos una vez.

## <a name="see-also"></a>Vea también

[do-while (Instrucción) (C++)](../cpp/do-while-statement-cpp.md)
