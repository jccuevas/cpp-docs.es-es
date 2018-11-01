---
title: isnan, _isnan, _isnanf
ms.date: 04/05/2018
apiname:
- _isnan
- _isnanf
- isnan
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
ms.openlocfilehash: ce111569b7caee9d0c7b8f35352c395571ad08b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650871"
---
# <a name="isnan-isnan-isnanf"></a>isnan, _isnan, _isnanf

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

En C, el **isnan** macro y el **_isnan** y **_isnanf** funciones devuelven un valor distinto de cero si el argumento *x* es un NAN; de lo contrario, Devuelve 0.

En C++, el **isnan** funciones de plantilla devuelven **true** si el argumento *x* es un NAN; de lo contrario, devuelven **false**.

## <a name="remarks"></a>Comentarios

La C **isnan** macro y **_isnan** y **_isnanf** funciones prueban el valor de punto flotante *x*, devuelve un valor distinto de cero si *x* no es un valor de número (NAN). Los valores NaN se generan cuando el resultado de una operación de punto flotante no se puede representar con el formato de punto flotante de IEEE 754 para el tipo especificado. Para obtener información sobre cómo se representa un NaN en la salida, vea [printf](printf-printf-l-wprintf-wprintf-l.md).

Cuando se compila como C++, el **isnan** macro no está definida y un **isnan** función de plantilla se define en su lugar. Devuelve un valor de tipo **bool** en lugar de un entero.

El **_isnan** y **_isnanf** funciones son específicas de Microsoft. El **_isnanf** función sólo está disponible cuando se compila para x64.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario (C)|Encabezado necesario (C++)|
|-------------|---------------------------|-------------------------------|
|**isNaN**, **_isnanf**|\<math.h>|\<math.h> o \<cmath>|
|**_isnan**|\<float.h>|\<float.h> o \<cfloat>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[_finite, _finitef](finite-finitef.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
