---
title: div, LDIV, lldiv
ms.date: 04/05/2018
api_name:
- div
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- div
helpviewer_keywords:
- div function
- quotients, computing
- quotients
- dividing integers
- remainder computing
ms.assetid: 8ae80d97-54fd-499e-b14c-e30993b58119
ms.openlocfilehash: 5b40fa0c4cc9cdf0c0de0f6af21da04b0c70369f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70937698"
---
# <a name="div-ldiv-lldiv"></a>div, LDIV, lldiv

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

*numer*<br/>
Numerador.

*denom*<br/>
Denominador.

## <a name="return-value"></a>Valor devuelto

el **div** al que se llama mediante argumentos de tipo **int** devuelve una estructura de tipo **div_t**, que comprende el cociente y el resto. El valor devuelto con argumentos de tipo **Long** es **ldiv_t**y el valor devuelto con argumentos de **tipo Long** **Long** es **lldiv_t**. **div_t**, **ldiv_t**y **lldiv_t** se definen en \<stdlib. h >.

## <a name="remarks"></a>Comentarios

La función **div** divide el *número* por *denom* y, por tanto, calcula el cociente y el resto. La estructura [div_t](../../c-runtime-library/standard-types.md) contiene el cociente, **quot**y el resto, **REM**. El signo del cociente es el mismo que el del cociente matemático. Su valor absoluto es el entero más grande que es menor que el valor absoluto del cociente matemático. Si el denominador es 0, el programa se cierra con un mensaje de error.

Las sobrecargas de **div** que toman argumentos de tipo **Long** o **Long** **Long** solo están disponibles para C++ el código. Los tipos de valor devuelto [ldiv_t](../../c-runtime-library/standard-types.md) y [lldiv_t](../../c-runtime-library/standard-types.md) contienen los miembros **quot** y **REM**, que tienen los mismos significados que los miembros de **div_t**.

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
