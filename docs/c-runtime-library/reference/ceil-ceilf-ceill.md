---
title: ceil, ceilf, ceill | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- ceilf
- ceil
- ceill
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
- ntdll.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- ceil
- ceilf
- ceill
dev_langs:
- C++
helpviewer_keywords:
- calculating value ceilings
- ceill function
- ceil function
- ceilf function
ms.assetid: f4e5acab-5c8f-4b10-9ae2-9561e6453718
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa68ff857db09d1426fbed6ea497624e13cc362a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394270"
---
# <a name="ceil-ceilf-ceill"></a>ceil, ceilf, ceill

Calcula el límite superior de un valor.

## <a name="syntax"></a>Sintaxis

```C
double ceil(
   double x
);
float ceil(
   float x
);  // C++ only
long double ceil(
   long double x
);  // C++ only
float ceilf(
   float x
);
long double ceill(
   long double x
);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Valor de punto flotante.

## <a name="return-value"></a>Valor devuelto

El **ceil** funciones devuelven un valor de punto flotante que representa el entero más pequeño que es mayor o igual que *x*. No se devuelve ningún error.

|Entrada|Excepción SEH|Excepción de Matherr|
|-----------|-------------------|-----------------------|
|± **QNAN**, **IND**|ninguna|**_DOMAIN**|

**ceil** tiene una implementación que usa Extensiones SIMD de transmisión por secuencias 2 (SSE2). Para obtener información y conocer las restricciones sobre el uso de la implementación de SSE2, consulte [_set_SSE2_enable](set-sse2-enable.md).

## <a name="remarks"></a>Comentarios

Como C++ permite las sobrecargas, puede llamar a sobrecargas de **ceil** que toman **float** o **largo** **doble** tipos. En un programa C, **ceil** siempre toma y devuelve un **doble**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**ceil**, **ceilf**, **ceill**|\<math.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [floor](floor-floorf-floorl.md).

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[round, roundf, roundl](round-roundf-roundl.md)<br/>
