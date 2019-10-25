---
title: ilogb, ilogbf, ilogbl2
ms.date: 04/05/2018
api_name:
- ilogb
- ilogbf
- ilogbl
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
- ilogb
- ilogbf
- ilogbl
- math/ilogb
- math/ilogbf
- math/ilogbl
helpviewer_keywords:
- ilogb function
- ilogbf function
- ilogbl function
ms.assetid: 9ef19d57-1caa-41d5-8233-2faad3562fcb
ms.openlocfilehash: fdafba039537358c9b6a1de21dc176ceea38b4fa
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954767"
---
# <a name="ilogb-ilogbf-ilogbl"></a>ilogb, ilogbf, ilogbl

Recupera un entero que representa el exponente imparcial de base 2 del valor especificado.

## <a name="syntax"></a>Sintaxis

```C
int ilogb(
   double x
);

int ilogb(
   float x
); //C++ only

int ilogb(
   long double x
); //C++ only

int ilogbf(
   float x
);

int ilogbl(
   long double x
);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Valor especificado.

## <a name="return-value"></a>Valor devuelto

Si es correcto, devuelve el exponente de base 2 de *x* como valor **int** con signo.

De lo contrario, devuelve uno de los valores siguientes, definidos en \<math.h>:

|Entrada|Resultado|
|-----------|------------|
|±0|FP_ILOGB0|
|± inf, ± Nan, indefinido|FP_ILOGBNAN|

Los errores se notifican tal como se especifica en [_matherr](matherr.md).

## <a name="remarks"></a>Comentarios

Dado C++ que permite las sobrecargas, puede llamar a las sobrecargas de **ilogb (** que toman y devuelven los tipos **float** y **Long** **Double** . En un programa de C, **ilogb (** siempre toma y devuelve un **valor Double**.

Llamar a esta función es similar a llamar a la función **logb** equivalente y, después, convertir el valor devuelto a **int**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado C|Encabezado C++|
|-------------|--------------|------------------|
|**ilogb**, **ilogbf**, **ilogbl**|\<math.h>|\<cmath>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[frexp](frexp.md)<br/>
[logb, logbf, logbl, _logb, _logbf](logb-logbf-logbl-logb-logbf.md)<br/>
