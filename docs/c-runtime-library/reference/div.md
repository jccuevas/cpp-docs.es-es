---
title: div, ldiv, lldiv
ms.date: 04/05/2018
apiname:
- div
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- div
helpviewer_keywords:
- div function
- quotients, computing
- quotients
- dividing integers
- remainder computing
ms.assetid: 8ae80d97-54fd-499e-b14c-e30993b58119
ms.openlocfilehash: 0ee1b3b6a5d7b15470ffe1e667b4077d1f9581e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653432"
---
# <a name="div-ldiv-lldiv"></a>div, ldiv, lldiv

Calcula el cociente y el resto de dos valores enteros.

## <a name="syntax"></a>Sintaxis

```C
div_t div(
   int numer,
   int denom
);
ldiv_t ldiv(
   long numer,
   long denom
);
lldiv_t lldiv(
   long long numer,
   long long denom
);
```

```cpp
ldiv_t div(
   long numer,
   long denom
); /* C++ only */
lldiv_t div(
   long long numer,
   long long denom
); /* C++ only */
```

### <a name="parameters"></a>Parámetros

*número*<br/>
Numerador.

*denom*<br/>
Denominador.

## <a name="return-value"></a>Valor devuelto

**div** llamado con argumentos de tipo **int** devuelve una estructura de tipo **div_t**, que compone el cociente y el resto. El valor devuelto con argumentos de tipo **largo** es **ldiv_t**y el valor devuelto con argumentos de tipo **largo** **largo** es **lldiv_t**. **div_t**, **ldiv_t**, y **lldiv_t** se definen en \<stdlib.h >.

## <a name="remarks"></a>Comentarios

El **div** función divide *número* por *denom* y, por tanto, se calcula el cociente y el resto. El [div_t](../../c-runtime-library/standard-types.md) estructura contiene el cociente, **quot**y el resto, **rem**. El signo del cociente es el mismo que el del cociente matemático. Su valor absoluto es el entero más grande que es menor que el valor absoluto del cociente matemático. Si el denominador es 0, el programa se cierra con un mensaje de error.

Las sobrecargas de **div** que aceptan argumentos de tipo **largo** o **largo** **largo** solo están disponibles para el código de C++. Los tipos devueltos [ldiv_t](../../c-runtime-library/standard-types.md) y [lldiv_t](../../c-runtime-library/standard-types.md) contiene miembros **quot** y **rem**, que tienen los mismos significados que los miembros de **div_t**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**div**, **ldiv**, **lldiv**|\<stdlib.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_div.c
// arguments: 876 13

// This example takes two integers as command-line
// arguments and displays the results of the integer
// division. This program accepts two arguments on the
// command line following the program name, then calls
// div to divide the first argument by the second.
// Finally, it prints the structure members quot and rem.
//

#include <stdlib.h>
#include <stdio.h>
#include <math.h>

int main( int argc, char *argv[] )
{
   int x,y;
   div_t div_result;

   x = atoi( argv[1] );
   y = atoi( argv[2] );

   printf( "x is %d, y is %d\n", x, y );
   div_result = div( x, y );
   printf( "The quotient is %d, and the remainder is %d\n",
           div_result.quot, div_result.rem );
}
```

```Output
x is 876, y is 13
The quotient is 67, and the remainder is 5
```

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
