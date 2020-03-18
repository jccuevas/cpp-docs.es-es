---
title: _cabs
ms.date: 11/04/2016
api_name:
- _cabs
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
- _cabs
helpviewer_keywords:
- cabs function
- absolute values
- _cabs function
- calculating absolute values
ms.assetid: fea292ee-1a39-4a0a-b416-4a189346ff26
ms.openlocfilehash: ba24b10fb267c9b54ec4944704de988128b4b419
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443053"
---
# <a name="_cabs"></a>_cabs

Calcula el valor absoluto de un número complejo.

## <a name="syntax"></a>Sintaxis

```C
double _cabs(
   struct _complex z
);
```

### <a name="parameters"></a>Parámetros

*z*<br/>
Número complejo.

## <a name="return-value"></a>Valor devuelto

**_cabs** devuelve el valor absoluto de su argumento si se realiza correctamente. En el desbordamiento, **_cabs** devuelve **HUGE_VAL** y establece **errno** en **ERANGE**. Puede cambiar el control de errores con [_matherr](matherr.md).

## <a name="remarks"></a>Observaciones

La función **_cabs** calcula el valor absoluto de un número complejo, que debe ser una estructura de tipo [_complex](../../c-runtime-library/standard-types.md). La estructura *z* se compone de un componente real *x* y un componente imaginario *y*. Una llamada a **_cabs** genera un valor equivalente al del `sqrt( z.x * z.x + z.y * z.y )`de expresión.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_cabs**|\<math.h>|

Para más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_cabs.c
// Using _cabs, this program calculates
// the absolute value of a complex number.

#include <math.h>
#include <stdio.h>

int main( void )
{
   struct _complex number = { 3.0, 4.0 };
   double d;

   d = _cabs( number );
   printf( "The absolute value of %f + %fi is %f\n",
           number.x, number.y, d );
}
```

```Output
The absolute value of 3.000000 + 4.000000i is 5.000000
```

## <a name="see-also"></a>Consulte también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)