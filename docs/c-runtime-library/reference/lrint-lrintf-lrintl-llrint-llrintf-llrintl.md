---
title: lrint, lrintf, lrintl, llrint, llrintf, llrintl
ms.date: 4/2/2020
api_name:
- lrint
- lrintl
- lrintf
- llrint
- llrintf
- llrintl
- _o_llrint
- _o_llrintf
- _o_llrintl
- _o_lrint
- _o_lrintf
- _o_lrintl
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
- lrint
- lrintf
- lrintl
- llrint
- llrintf
- llrintl
- math/lrint
- math/lrintf
- math/lrintl
- math/llrint
- math/llrintf
- math/llrintl
helpviewer_keywords:
- lrint function
- lrintf function
- lrintl function
- llrint function
- llrintf function
- llrintl function
ms.assetid: 28ccd5b3-5e6f-434f-997d-a21d51b8ce7f
ms.openlocfilehash: effb146cac201a21651f21e3e5c040fbb68819a6
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911370"
---
# <a name="lrint-lrintf-lrintl-llrint-llrintf-llrintl"></a>lrint, lrintf, lrintl, llrint, llrintf, llrintl

Redondea el valor de punto flotante especificado al valor entero más cercano usando el modo y la dirección de redondeo actual.

## <a name="syntax"></a>Sintaxis

```C
long int lrint(
   double x
);

long int lrint(
   float x
); //C++ only

long int lrint(
   long double x
); //C++ only

long int lrintf(
   float x
);

long int lrintl(
   long double x
);

long long int llrint(
   double x
);

long long int llrint(
   float x
); //C++ only

long long int llrint(
   long double x
); //C++ only

long long int llrintf(
   float x
);

long long int llrintl(
   long double x
);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
el valor que se va a redondear.

## <a name="return-value"></a>Valor devuelto

Si es correcto, devuelve el valor entero redondeado de *x*.

|Problema|Valor devuelto|
|-----------|------------|
|*x* está fuera del intervalo del tipo de valor devuelto<br /><br /> *x* = ± ∞<br /><br /> *x* = Nan|Genera **FE_INVALID** y devuelve cero (0).|

## <a name="remarks"></a>Observaciones

Dado que C++ permite las sobrecargas, puede llamar a las sobrecargas de **lrint** y **llrint** que toman tipos **float** y **Long** **Double** . En un programa de C, **lrint** y **llrint** siempre toman un **valor Double**.

Si *x* no representa el equivalente de punto flotante de un valor entero, estas funciones generan **FE_INEXACT**.

**Específico de Microsoft**: cuando el resultado está fuera del intervalo del tipo de valor devuelto, o cuando el parámetro es un Nan o infinito, el valor devuelto se define como implementación. El compilador de Microsoft devuelve un valor cero (0).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**lrint**, **lrintf**, **lrintl**, **llrint**, **llrintf**, **llrintl**|\<math.h>|\<cmath>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
