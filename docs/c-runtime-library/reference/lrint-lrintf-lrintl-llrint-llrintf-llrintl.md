---
title: lrint, lrintf, lrintl, llrint, llrintf, llrintl
ms.date: 04/05/2018
apiname:
- lrint
- lrintl
- lrintf
- llrint
- llrintf
- llrintl
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
ms.openlocfilehash: 01680a62e654112475a55bd8eac0cc14d254e2a2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62285777"
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

|Problema|Volver|
|-----------|------------|
|*x* está fuera del intervalo del tipo de valor devuelto<br /><br /> *x* = ±∞<br /><br /> *x* = NaN|Genera **FE_INVALID** y devuelve cero (0).|

## <a name="remarks"></a>Comentarios

Dado que C++ admite sobrecargas, puede llamar a sobrecargas de **lrint** y **llrint** que toman **float** y **largo**  **Double** tipos. En un programa C, **lrint** y **llrint** siempre tienen un **doble**.

Si *x* no representa el equivalente de punto flotante de un valor entero, estas funciones generan **FE_INEXACT**.

**Específico de Microsoft**: Cuando el resultado está fuera del intervalo del tipo de valor devuelto, o cuando el parámetro es un NaN o infinito, el valor devuelto es implementación definida. El compilador de Microsoft devuelve un valor cero (0).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**lrint**, **lrintf**, **lrintl**, **llrint**, **llrintf**, **llrintl**|\<math.h>|\<cmath>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
