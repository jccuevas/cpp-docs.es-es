---
title: cbrt, cbrtf, cbrtl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- cbrt
- cbrtf
- cbrtl
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
- cbrtl
- cbrt
- cbrtf
dev_langs:
- C++
helpviewer_keywords:
- cbrtl function
- cbrtf function
- cbrt function
ms.assetid: ab51d916-3db2-4beb-b46a-28b4062cd33f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29dee00f35c2b4d75e838e5abe2ee24de9753013
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32393620"
---
# <a name="cbrt-cbrtf-cbrtl"></a>cbrt, cbrtf, cbrtl

Calcula la raíz cúbica.

## <a name="syntax"></a>Sintaxis

```C
double cbrt(
   double x
);
float cbrt(
   float x
);  // C++ only
long double cbrt(
   long double x
);  // C++ only
float cbrtf(
   float x
);
long double cbrtl(
   long double x
);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Valor de punto flotante

## <a name="return-value"></a>Valor devuelto

El **cbrt** funciones devuelven la raíz cúbica de *x*.

|Entrada|Excepción SEH|**_matherr** (excepción)|
|-----------|-------------------|--------------------------|
|± ∞, QNAN, IND|ninguna|ninguna|

## <a name="remarks"></a>Comentarios

Como C++ permite las sobrecargas, puede llamar a sobrecargas de **cbrt** que toman **float** o **largo** **doble** tipos. En un programa C, **cbrt** siempre toma y devuelve **doble**.

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**cbrt**, **cbrtf**, **cbrtl**|\<math.h>|\<cmath>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_cbrt.c
// Compile using: cl /W4 crt_cbrt.c
// This program calculates a cube root.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double question = -64.64;
   double answer;

   answer = cbrt(question);
   printf("The cube root of %.2f is %.6f\n", question, answer);
}
```

```Output
The cube root of -64.64 is -4.013289
```

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[exp, expf, expl](exp-expf.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
[pow, powf, powl](pow-powf-powl.md)<br/>
