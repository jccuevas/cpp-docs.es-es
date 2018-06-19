---
title: remquo, remquof, remquol | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- remquof
- remquo
- remquol
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- remquof
- remquol
- remquo
dev_langs:
- C++
helpviewer_keywords:
- remquol function
- remquof function
- remquo function
ms.assetid: a1d3cb8b-8027-4cd3-8deb-04eb17f299fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d2bcb774d7ebe7e71c3877af326177bbf8d7160
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32407007"
---
# <a name="remquo-remquof-remquol"></a>remquo, remquof, remquol

Calcula el resto de dos valores enteros y almacena un valor entero con el signo y la magnitud aproximada del cociente en una ubicación que se especifica en un parámetro.

## <a name="syntax"></a>Sintaxis

```C
double remquo( double numer, double denom, int* quo );
float remquof( float numer, float denom, int* quo );
long double remquol( long double numer, long double denom, int* quo );
```

```cpp
float remquo( float numer, float denom, int* quo ); /* C++ only */
long double remquo( long double numer, long double denom, int* quo ); /* C++ only */
```

### <a name="parameters"></a>Parámetros

*número*<br/>
Numerador.

*denom*<br/>
Denominador.

*/quo*<br/>
Puntero a un entero para almacenar un valor que tiene el signo y la magnitud aproximada del cociente.

## <a name="return-value"></a>Valor devuelto

**remquo** devuelve el resto de punto flotante de *x* / *y*. Si el valor de *y* es 0,0, **remquo** devuelve un valor NaN reservado. Para obtener información acerca de la representación de un valor NaN reservado por la **printf** familia, vea [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Comentarios

El **remquo** función calcula el resto de punto flotante *f* de *x* / *y* que *x*   =  *i* * *y* + *f*, donde *i* es un entero , *f* tiene el mismo signo que *x*y el valor absoluto de *f* es menor que el valor absoluto de *y*.

C++ permite las sobrecargas, es posible llamar a las sobrecargas de **remquo** que toman y devuelven **float** o **largo** **doble** valores. En un programa C, **remquo** siempre toma dos **doble** argumentos y devuelve un **doble**.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario (C)|Encabezado necesario (C++)|
|--------------|---------------------|-|
|**remquo**, **remquof**, **remquol**|\<math.h>|\<cmath> o \<math.h>|

Para obtener información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_remquo.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;
   int quo = 0;

   z = remquo(w, x, &quo);
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);
   printf("Approximate signed quotient is %d\n", quo);
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
Approximate signed quotient is -3
```

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[remainder, remainderf, remainderl](remainder-remainderf-remainderl.md)<br/>
