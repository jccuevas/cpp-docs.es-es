---
title: isnan, _isnan, _isnanf
ms.date: 01/31/2019
api_name:
- _isnan
- _isnanf
- isnan
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
- _isnan
- isnan
- math/isnan
- math/_isnan
- math/_isnanf
- _isnanf
helpviewer_keywords:
- NAN (not a number)
- _isnan function
- IEEE floating-point representation
- Not a Number (NANs)
- isnan function
ms.assetid: 391fbc5b-89a4-4fba-997e-68f1131caf82
ms.openlocfilehash: a0cc60fb80f8d5b78ec2947a87fde82a536b413c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953765"
---
# <a name="isnan-_isnan-_isnanf"></a>isnan, _isnan, _isnanf

Comprueba si un determinado valor de punto flotante es un valor NaN (Not a Number).

## <a name="syntax"></a>Sintaxis

```C
int isnan(
   /* floating-point */ x
); /* C-only macro */

int _isnan(
   double x
);

int _isnanf(
   float x
); /* x64 only */

template <class T>
bool isnan(
   T x
) throw(); /* C++ only */
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Valor de punto flotante que se va a probar.

## <a name="return-value"></a>Valor devuelto

En C, la macro **isNaN** y las funciones **_isnan** y **isnanf** devuelven un valor distinto de cero si el argumento *x* es un Nan; en caso contrario, devuelven 0.

En C++, la función de plantilla **isNaN** devuelve **true** si el argumento *x* es un Nan; en caso contrario, devuelve **false**.

## <a name="remarks"></a>Comentarios

Dado que un valor NaN no se compara como igual que cualquier otro valor NaN, debe usar una de estas funciones o macros para detectar uno. Se genera un NaN cuando el resultado de una operación de punto flotante no se puede representar en el formato de punto flotante IEEE-754 para el tipo especificado. Para obtener información sobre cómo se representa un NaN para la salida, vea [printf](printf-printf-l-wprintf-wprintf-l.md).

Cuando se compila C++como, la macro **isNaN** no está definida y en su lugar se define una función de plantilla **isNaN** . Se comporta de la misma forma que la macro, pero devuelve un valor de tipo **bool** en lugar de un entero.

Las funciones **_isnan** y **isnanf** son específicas de Microsoft. La función **isnanf** solo está disponible cuando se compila para x64.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario (C)|Encabezado necesario (C++)|
|-------------|---------------------------|-------------------------------|
|**isNaN**, **isnanf**|\<math.h>|\<math.h> o \<cmath>|
|**_isnan**|\<float.h>|\<float.h> o \<cfloat>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnormal](isnormal.md)<br/>
