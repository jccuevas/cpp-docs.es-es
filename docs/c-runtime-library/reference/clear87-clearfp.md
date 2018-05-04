---
title: _clear87, _clearfp | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _clearfp
- _clear87
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- clearfp
- _clearfp
- _clear87
- clear87
dev_langs:
- C++
helpviewer_keywords:
- clearing floating point status word
- clearfp function
- _clear87 function
- _clearfp function
- clear87 function
ms.assetid: 72d24a70-7688-4793-ae09-c96d33fcca52
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 195bd9f78ed9edfa47ec9ebbd2babbee676e5644
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="clear87-clearfp"></a>_clear87, _clearfp

Obtiene y borra la palabra de estado de punto flotante.

## <a name="syntax"></a>Sintaxis

```C
unsigned int _clear87( void );
unsigned int _clearfp( void );
```

## <a name="return-value"></a>Valor devuelto

Los bits de valor devuelto indican el estado de punto flotante antes de llamar a **_clear87** o **_clearfp**. Para ver una definición completa de los bits devueltos por **_clear87**, vea Float.h. Muchas de las funciones de la biblioteca matemática modifican la palabra de estado 8087/80287 con resultados imprevisibles. Valores devueltos de **_clear87** y **_status87** son más confiables se realizan menos operaciones de punto flotante entre Estados conocidos de la palabra de estado de punto flotante.

## <a name="remarks"></a>Comentarios

El **_clear87** función borra las marcas de excepción en la palabra de estado de punto flotante, el bit de actividad se establece en 0 y devuelve la palabra de estado. La palabra de estado de punto flotante es una combinación de la palabra de estado 8087/80287 y de otras condiciones detectadas por el controlador de excepciones 8087/80287 (por ejemplo, el desbordamiento y subdesbordamiento de la pila de punto flotante).

**_clearfp** es una versión independiente de la plataforma y portable de la **_clear87** rutina. Es idéntico a **_clear87** en plataformas Intel (x86) y también es compatible con la x64 y las plataformas ARM. Para asegurarse de que el código de punto flotante es portable a los x64 y ARM, use **_clearfp**. Si solo va a usar x86 plataformas, puede usar **_clear87** o **_clearfp**.

Estas funciones están en desuso cuando se compila con [/clr (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) porque common language runtime solo admite la precisión de punto flotante predeterminada.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_clear87**|\<float.h>|
|**_clearfp**|\<float.h>|

Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_clear87.c
// compile with: /Od

// This program creates various floating-point
// problems, then uses _clear87 to report on these problems.
// Compile this program with Optimizations disabled (/Od).
// Otherwise the optimizer will remove the code associated with
// the unused floating-point values.
//

#include <stdio.h>
#include <float.h>

int main( void )
{
   double a = 1e-40, b;
   float x, y;

   printf( "Status: %.4x - clear\n", _clear87()  );

   // Store into y is inexact and underflows:
   y = a;
   printf( "Status: %.4x - inexact, underflow\n", _clear87() );

   // y is denormal:
   b = y;
   printf( "Status: %.4x - denormal\n", _clear87() );
}
```

```Output
Status: 0000 - clear
Status: 0003 - inexact, underflow
Status: 80000 - denormal
```

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
