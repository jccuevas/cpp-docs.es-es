---
title: remquo, remquof, remquol
ms.date: 4/2/2020
api_name:
- remquof
- remquo
- remquol
- _o_remquo
- _o_remquof
- _o_remquol
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
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- remquof
- remquol
- remquo
helpviewer_keywords:
- remquol function
- remquof function
- remquo function
ms.assetid: a1d3cb8b-8027-4cd3-8deb-04eb17f299fc
ms.openlocfilehash: 774a35f257b02c67b22618224a60ed501476a6f4
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917820"
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

*arábiga*<br/>
Numerador.

*denom*<br/>
Denominador.

*situación*<br/>
Puntero a un entero para almacenar un valor que tiene el signo y la magnitud aproximada del cociente.

## <a name="return-value"></a>Valor devuelto

**remquo (** devuelve el resto de punto flotante de *x* / *y*. Si el valor de *y* es 0,0, **Remquo (** devuelve un Nan silencioso. Para obtener información sobre la representación de un NaN silencioso por la familia **printf** , vea [printf, _printf_l, wprintf _wprintf_l](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Observaciones

La **función remquo (** calcula el resto de punto flotante *f* de *x* / *y* como *x* = x*i* \* *y* + *f*, donde *i* es un entero, *f* tiene el mismo signo que *x*y el valor absoluto de *f* es menor que el valor absoluto de *y*.

C++ permite las sobrecargas, por lo que puede llamar a las sobrecargas de **remquo (** que toman y devuelven valores de tipo **float** o **Long** **Double** . En un programa de C, **remquo (** siempre toma dos argumentos **Double** y devuelve un **valor Double**.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario (C)|Encabezado necesario (C++)|
|--------------|---------------------|-|
|**remquo (**, **remquof (**, **remquol**|\<math.h>|\<cmath> o \<math.h>|

Para obtener información sobre la compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Consulte también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[remainder, remainderf, remainderl](remainder-remainderf-remainderl.md)<br/>
