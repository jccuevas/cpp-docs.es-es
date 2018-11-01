---
title: imaxdiv
ms.date: 04/05/2018
apiname:
- imaxdiv
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
- imaxdiv
helpviewer_keywords:
- imaxdiv function
ms.assetid: 7d90126f-fdc2-4986-9cdf-94e4c9123d26
ms.openlocfilehash: 23067b2028fc11193fae707e25165fb0ce754515
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434463"
---
# <a name="imaxdiv"></a>imaxdiv

Calcula el cociente y el resto de dos valores enteros de cualquier tamaño como una sola operación.

## <a name="syntax"></a>Sintaxis

```C
imaxdiv_t imaxdiv(
   intmax_t numer,
   intmax_t denom
);
```

### <a name="parameters"></a>Parámetros

*número*<br/>
Numerador.

*denom*<br/>
Denominador.

## <a name="return-value"></a>Valor devuelto

**imaxdiv** llamado con argumentos de tipo [intmax_t](../../c-runtime-library/standard-types.md) devuelve una estructura de tipo [imaxdiv_t](../../c-runtime-library/standard-types.md) que compone el cociente y el resto.

## <a name="remarks"></a>Comentarios

El **imaxdiv** función divide *número* por *denom* y, por tanto, se calcula el cociente y el resto. El **imaxdiv_t** estructura contiene el cociente, **intmax_t** **quot**y el resto, **intmax_t** **rem**. El signo del cociente es el mismo que el del cociente matemático. Su valor absoluto es el entero más grande que es menor que el valor absoluto del cociente matemático. Si el denominador es 0, el programa se cierra con un mensaje de error.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**imaxdiv**|\<inttypes.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_imaxdiv.c
// Build using: cl /W3 /Tc crt_imaxdiv.c
// This example takes two integers as command-line
// arguments and calls imaxdiv to divide the first
// argument by the second, then displays the results.

#include <stdio.h>
#include <stdlib.h>
#include <inttypes.h>

int main(int argc, char *argv[])
{
   intmax_t x,y;
   imaxdiv_t div_result;

   x = atoll(argv[1]);
   y = atoll(argv[2]);

   printf("The call to imaxdiv(%lld, %lld)\n", x, y);
   div_result = imaxdiv(x, y);
   printf("results in a quotient of %lld, and a remainder of %lld\n\n",
          div_result.quot, div_result.rem);
}
```

Si se compila y se llama con los parámetros de línea de comandos de `9460730470000000 8766`, el código genera esta salida:

```Output
The call to imaxdiv(9460730470000000, 8766)
results in a quotient of 1079252848505, and a remainder of 5170
```

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[div](div.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
