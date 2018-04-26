---
title: div, ldiv, lldiv | Documentos de Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- div function
- quotients, computing
- quotients
- dividing integers
- remainder computing
ms.assetid: 8ae80d97-54fd-499e-b14c-e30993b58119
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b3a0e28030b62f68d478cb976b1f89d91904655a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
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

**div** llama mediante argumentos de tipo **int** devuelve una estructura de tipo **div_t**, formada por el cociente y el resto. El valor devuelto con argumentos de tipo **largo** es **ldiv_t**y el valor devuelto con argumentos de tipo **largo** **largo** es **lldiv_t**. **div_t**, **ldiv_t**, y **lldiv_t** se definen en \<stdlib.h >.

## <a name="remarks"></a>Comentarios

El **div** función divide *número* por *denom* y, por tanto, calcula el cociente y el resto. El [div_t](../../c-runtime-library/standard-types.md) estructura contiene el cociente, **quot**y el resto, **rem**. El signo del cociente es el mismo que el del cociente matemático. Su valor absoluto es el entero más grande que es menor que el valor absoluto del cociente matemático. Si el denominador es 0, el programa se cierra con un mensaje de error.

Las sobrecargas de **div** que toman argumentos de tipo **largo** o **largo** **largo** solo están disponibles para el código de C++. Los tipos de valor devueltos [ldiv_t](../../c-runtime-library/standard-types.md) y [lldiv_t](../../c-runtime-library/standard-types.md) contiene miembros **quot** y **rem**, que tienen los mismos significados que los miembros de **div_t**.

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
