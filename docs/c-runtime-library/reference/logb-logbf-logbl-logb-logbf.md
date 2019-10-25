---
title: logb, logbf, logbl, _logb, _logbf
ms.date: 04/05/2018
api_name:
- logb
- _logb
- _logbl
- logbf
- logbl
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
- logb
- logbl
- _logb
- _logbf
- logbf
helpviewer_keywords:
- _logbf function
- mantissas, floating-point variables
- logbf function
- _logb function
- exponent, floating-point numbers
- logbl function
- logb function
- floating-point functions
- floating-point functions, mantissa and exponent
- exponents and mantissas
ms.assetid: 780c4daa-6fe6-4fbc-9412-4c1ba1a1766f
ms.openlocfilehash: c5fc59f786b00dcf4ab1056424d8442a03f3adbf
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953148"
---
# <a name="logb-logbf-logbl-_logb-_logbf"></a>logb, logbf, logbl, _logb, _logbf

Extrae el valor de exponente de un argumento de punto flotante.

## <a name="syntax"></a>Sintaxis

```C
double logb(
   double x
);
float logb(
   float x
); // C++ only
long double logb(
   long double x
); // C++ only
float logbf(
   float x
);
long double logbl(
   long double x
);
double _logb(
   double x
);
float _logbf(
   float x
);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Valor de punto flotante.

## <a name="return-value"></a>Valor devuelto

**logb** devuelve el valor de exponente no sesgado de *x* como un entero con signo representado como un valor de punto flotante.

## <a name="remarks"></a>Comentarios

Las funciones **logb** extraen el valor exponencial del argumento de punto flotante *x*, como si se representara *x* con intervalo infinito. Si el argumento *x* está desnormalizado, se trata como si estuviera normalizado.

Dado C++ que permite las sobrecargas, puede llamar a las sobrecargas de **logb** que toman y devuelven valores de tipo **float** o **Long** **Double** . En un programa de C, **logb** siempre toma y devuelve un **valor Double**.

|Entrada|Excepción SEH|Excepción de Matherr|
|-----------|-------------------|-----------------------|
|± QNAN,IND|None|_DOMAIN|
|± 0|ZERODIVIDE|_SING|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_logb**|\<float.h>|
|**logb**, **logbf**, **logbl**, **_logbf**|\<math.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
