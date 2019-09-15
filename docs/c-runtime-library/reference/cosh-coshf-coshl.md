---
title: cosh, coshf, coshl
ms.date: 04/11/2018
api_name:
- cosh
- coshf
- coshl
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
- cosh
- coshf
- coshl
helpviewer_keywords:
- cosh function
- coshf function
- coshl function
- trigonometric functions
- hyperbolic functions
ms.openlocfilehash: 446988e67ca6e3b4a3839a9336f1ea4e2755c124
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938995"
---
# <a name="cosh-coshf-coshl"></a>cosh, coshf, coshl

Calcula el coseno hiperbólico.

## <a name="syntax"></a>Sintaxis

```C
double cosh( double x );
float coshf( float x );
long double coshl( long double x );
```

```cpp
float cosh( float x );  // C++ only
long double cosh( long double x );  // C++ only
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Ángulo en radianes.

## <a name="return-value"></a>Valor devuelto

Coseno hiperbólico de *x*.

De forma predeterminada, si el resultado es demasiado grande en una llamada **cosh**, **coshf (** o **Coshl** , la función devuelve **HUGE_VAL** y establece **errno** en **ERANGE**.

|Entrada|Excepción SEH|Excepción de Matherr|
|-----------|-------------------|-----------------------|
|± **QNAN**, **IND**|ninguna|**_DOMAIN**|
|*x* ≥ 7.104760e+002|**DESBORDAMIENTO INEXACTO**+|**OVERFLOW**|

## <a name="remarks"></a>Comentarios

Dado C++ que permite las sobrecargas, puede llamar a las sobrecargas de **cosh** que toman y devuelven valores de tipo **float** o **Long** **Double** . En un programa de C, **cosh** siempre toma y devuelve un **valor Double**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario (C)|Encabezado necesario (C++)|
|-------------|---------------------|-|
|**coshf**, **cosl**, **coshl**|\<math.h>|\<cmath> o \<math.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [SENOH, sinhf, sinhl](sinh-sinhf-sinhl.md).

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[acosh, acoshf, acoshl](acosh-acoshf-acoshl.md)<br/>
[asinh, asinhf, asinhl](asinh-asinhf-asinhl.md)<br/>
[atanh, atanhf, atanhl](atanh-atanhf-atanhl.md)<br/>
[_matherr](matherr.md)<br/>
[sinh, sinhf, sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh, tanhf, tanhl](tanh-tanhf-tanhl.md)<br/>
