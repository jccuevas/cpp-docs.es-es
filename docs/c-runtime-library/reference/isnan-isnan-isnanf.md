---
title: isnan, _isnan, _isnanf
ms.date: 01/31/2019
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
ms.openlocfilehash: 8a907dd33803cebd7bc5d71789834d115333b6a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157355"
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

En C++, el **isnan** función de plantilla devuelve **true** si el argumento *x* es un NaN; de lo contrario devuelve **false**.

## <a name="remarks"></a>Comentarios

Dado que un valor NaN no se compara como igual a cualquier otro valor NaN, debe utilizar una de estas macros o funciones para detectar uno. Un NaN se genera cuando no se puede representar el resultado de una operación de punto flotante en formato de punto flotante de IEEE-754 para el tipo especificado. Para obtener información acerca de cómo se representa un NaN de salida, vea [printf](printf-printf-l-wprintf-wprintf-l.md).

Cuando se compila como C++, el **isnan** macro no está definida y un **isnan** función de plantilla se define en su lugar. Se comporta del mismo modo que la macro, pero devuelve un valor de tipo **bool** en lugar de un entero.

El **_isnan** y **_isnanf** funciones son específicas de Microsoft. El **_isnanf** función sólo está disponible cuando se compila para x64.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario (C)|Encabezado necesario (C++)|
|-------------|---------------------------|-------------------------------|
|**isnan**, **_isnanf**|\<math.h>|\<math.h> o \<cmath>|
|**_isnan**|\<float.h>|\<float.h> o \<cfloat>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnormal](isnormal.md)<br/>
