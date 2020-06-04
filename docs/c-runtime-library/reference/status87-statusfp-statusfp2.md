---
title: _status87, _statusfp, _statusfp2
ms.date: 04/05/2018
api_name:
- _statusfp2
- _statusfp
- _status87
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _statusfp2
- _statusfp
- statusfp2
- _status87
- status87
- statusfp
helpviewer_keywords:
- floating-point functions, getting status word
- floating-point numbers, status word
- status87 function
- status word, getting floating point
- statusfp function
- _statusfp function
- _statusfp2 function
- statusfp2 function
- _status87 function
- floating-point functions
- status word
ms.assetid: 7ef963fa-b1fb-429d-94d6-fbf282ab7432
ms.openlocfilehash: 54faf70296ef41f2682f88a8edaa82ee0d2071d4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958091"
---
# <a name="_status87-_statusfp-_statusfp2"></a>_status87, _statusfp, _statusfp2

Obtiene la palabra de estado de punto flotante.

## <a name="syntax"></a>Sintaxis

```C
unsigned int _status87( void );
unsigned int _statusfp( void );
void _statusfp2(unsigned int *px86, unsigned int *pSSE2)
```

### <a name="parameters"></a>Parámetros

*px86*<br/>
Esta dirección se rellena con la palabra de estado para la unidad de punto flotante x87.

*pSSE2*<br/>
Esta dirección se rellena con la palabra de estado para la unidad de punto flotante SSE2.

## <a name="return-value"></a>Valor devuelto

Para **_status87** y **_statusfp**, los bits del valor devuelto indican el estado de punto flotante. Vea el valor FLOAT. Archivo de inclusión H para una definición de los bits devueltos por **_statusfp**. Muchas funciones de la biblioteca matemática modifican la palabra de estado de punto flotante, con resultados imprevisibles. La optimización puede reordenar, combinar y eliminar operaciones de punto flotante en torno a llamadas a **_status87**, **_statusfp**y funciones relacionadas. Use la opción del compilador [/Od (Deshabilitar (Depurar))](../../build/reference/od-disable-debug.md) o la directiva pragma [fenv_access](../../preprocessor/fenv-access.md) para evitar optimizaciones que reordenen las operaciones de punto flotante. Los valores devueltos de **_clearfp** y **_statusfp**, así como los parámetros devueltos de **_statusfp2**, son más confiables si se realizan menos operaciones de punto flotante entre Estados conocidos de la palabra de estado de punto flotante.

## <a name="remarks"></a>Comentarios

La función **_statusfp** obtiene la palabra de estado de punto flotante. La palabra de estado es una combinación del estado de procesador de punto flotante y otras condiciones detectadas por el controlador de excepciones de punto flotante, por ejemplo, desbordamiento y subdesbordamiento de la pila de punto flotante. Las excepciones sin máscara se comprueban antes de que se devuelva el contenido de la palabra de estado. De esta forma, el llamador recibe información sobre las excepciones pendientes. En las plataformas x86, **_statusfp** devuelve una combinación del estado de punto flotante X87 y SSE2. En las plataformas x64, el estado que se devuelve se basa en el estado de MXCSR de SSE. En las plataformas ARM, **_statusfp** devuelve el estado del registro FPSCR.

**_statusfp** es una versión portátil e independiente de la plataforma de **_status87**. Es idéntico a **_status87** en plataformas Intel (x86) y también es compatible con las plataformas x64 y ARM. Para asegurarse de que el código de punto flotante es portable a todas las arquitecturas, use **_statusfp**. Si solo tiene como destino plataformas x86, puede usar **_status87** o **_statusfp**.

Se recomienda **_statusfp2** para chips (como Pentium IV) que tengan un procesador de punto flotante de x87 y de SSE2. En el caso de **_statusfp2**, las direcciones se rellenan usando la palabra de estado de punto flotante para el procesador de punto flotante X87 o SSE2. Para un chip que admite procesadores de punto flotante de x87 y SSE2, EM_AMBIGUOUS se establece en 1 si se usa **_statusfp** o _ **controlfp** y la acción era ambigua porque podía hacer referencia a la palabra de estado de punto flotante de x87 o SSE2. La función **_statusfp2** solo se admite en plataformas x86.

Estas funciones no son útiles para [/CLR (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) porque el Common Language Runtime (CLR) solo admite la precisión de punto flotante predeterminada.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_status87**, **_statusfp**, **_statusfp2**|\<float.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_statusfp.c
// Build by using: cl /W4 /Ox /nologo crt_statusfp.c
// This program creates various floating-point errors and
// then uses _statusfp to display messages that indicate these problems.

#include <stdio.h>
#include <float.h>
#pragma fenv_access(on)

double test( void )
{
   double a = 1e-40;
   float b;
   double c;

   printf("Status = 0x%.8x - clear\n", _statusfp());

   // Assignment into b is inexact & underflows:
   b = (float)(a + 1e-40);
   printf("Status = 0x%.8x - inexact, underflow\n", _statusfp());

   // c is denormal:
   c = b / 2.0;
   printf("Status = 0x%.8x - inexact, underflow, denormal\n",
            _statusfp());

   // Clear floating point status:
   _clearfp();
   return c;
}

int main(void)
{
   return (int)test();
}
```

```Output
Status = 0x00000000 - clear
Status = 0x00000003 - inexact, underflow
Status = 0x00080003 - inexact, underflow, denormal
```

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87, _clearfp](clear87-clearfp.md)<br/>
[_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md)<br/>
