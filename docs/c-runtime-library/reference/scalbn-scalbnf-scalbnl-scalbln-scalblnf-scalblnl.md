---
title: scalbn, scalbnf, scalbnl, scalbln, scalblnf, scalblnl
ms.date: 04/05/2018
api_name:
- scalblnl
- scalbnl
- scalbnf
- scalblnf
- scalbn
- scalbln
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- scalblnf
- scalbnl
- scalblnl
- scalbln
- scalbn
- scalbnf
helpviewer_keywords:
- scalbn function
- scalbln function
- scalblnl function
- scalbnl function
- scalbnf function
- scalblnf function
ms.assetid: df2f1543-8e39-4af4-a5cf-29307e64807d
ms.openlocfilehash: 794d0bdceb13aafb83de85fb29e47a4fa3125cd6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948918"
---
# <a name="scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl"></a>scalbn, scalbnf, scalbnl, scalbln, scalblnf, scalblnl

Multiplica un número de punto flotante por una potencia integral de FLT_RADIX.

## <a name="syntax"></a>Sintaxis

```C
double scalbn(
   double x,
   int exp
);
float scalbn(
   float x,
   int exp
);  // C++ only
long double scalbn(
   long double x,
   int exp
);  // C++ only
float scalbnf(
   float x,
   int exp
);
long double scalbnl(
   long double x,
   int exp
);
double scalbln(
   double x,
   long exp
);
float scalbln(
   float x,
   long exp
);  // C++ only
long double scalbln(
   long double x,
   long exp
);  // C++ only
float scalblnf(
   float x,
   long exp
);
long double scalblnl(
   long double x,
   long exp
);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Valor de punto flotante.

*exp*<br/>
Exponente de entero.

## <a name="return-value"></a>Valor devuelto

Las funciones **scalbn (** devuelven el valor de *x* \* **FLT_RADIX**<sup>exp</sup> cuando se realiza correctamente. En el desbordamiento (dependiendo del signo de *x*), **scalbn (** devuelve +/- **HUGE_VAL**; el valor **errno** se establece en **ERANGE**.

Para obtener más información sobre **errno** y los posibles valores devueltos de error, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

**FLT_RADIX** se define en \<float. h > como la base de punto flotante nativa; en los sistemas binarios, tiene un valor de 2 y **scalbn (** es equivalente a [ldexp](ldexp.md).

Dado C++ que permite las sobrecargas, puede llamar a las sobrecargas de **scalbn (** y **scalbln** que toman y devuelven los tipos **float** o **Long** **Double** . En un programa de C, **scalbn (** siempre toma un **valor Double** y un valor **int** y devuelve **Double**, y **scalbln** siempre toma **Double** y **Long** y devuelve un valor **Double**.

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**scalbn**, **scalbnf**, **scalbnl**, **scalbln**, **scalblnf**, **scalblnl**|\<math.h>|\<cmath>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_scalbn.c
// Compile using: cl /W4 crt_scalbn.c
#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 6.4, y;
   int p = 3;

   y = scalbn( x, p );
   printf( "%2.1f times FLT_RADIX to the power of %d is %2.1f\n", x, p, y );
}
```

### <a name="output"></a>Resultados

```Output
6.4 times FLT_RADIX to the power of 3 is 51.2
```

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[ldexp](ldexp.md)<br/>
[modf, modff, modfl](modf-modff-modfl.md)<br/>
