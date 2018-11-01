---
title: _status87, _statusfp, _statusfp2
ms.date: 04/05/2018
apiname:
- _statusfp2
- _statusfp
- _status87
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
ms.openlocfilehash: 271c28dd4e267e5b3b702858cc398689e3e35d6f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597535"
---
# <a name="status87-statusfp-statusfp2"></a>_status87, _statusfp, _statusfp2

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

Para **_status87** y **_statusfp**, los bits en el valor devuelto indican el estado de punto flotante. Vea el tipo FLOAT. H incluir archivo para una definición de los bits devueltos por **_statusfp**. Muchas funciones de la biblioteca matemática modifican la palabra de estado de punto flotante, con resultados imprevisibles. La optimización puede reordenar, combinar y eliminar operaciones de punto flotante en torno a llamadas a **_status87**, **_statusfp**y funciones relacionadas. Use la opción del compilador [/Od (Deshabilitar (Depurar))](../../build/reference/od-disable-debug.md) o la directiva pragma [fenv_access](../../preprocessor/fenv-access.md) para evitar optimizaciones que reordenen las operaciones de punto flotante. Los valores devueltos de **_clearfp** y **_statusfp**y también los parámetros devueltos de **_statusfp2**, son más confiables si se realizan menos operaciones de punto flotante entre Estados conocidos de la palabra de estado de punto flotante.

## <a name="remarks"></a>Comentarios

El **_statusfp** función obtiene la palabra de estado de punto flotante. La palabra de estado es una combinación del estado de procesador de punto flotante y otras condiciones detectadas por el controlador de excepciones de punto flotante, por ejemplo, desbordamiento y subdesbordamiento de la pila de punto flotante. Las excepciones sin máscara se comprueban antes de que se devuelva el contenido de la palabra de estado. De esta forma, el llamador recibe información sobre las excepciones pendientes. En x86 plataformas, **_statusfp** devuelve una combinación de x87 y estado de punto flotante SSE2. En las plataformas x64, el estado que se devuelve se basa en el estado de MXCSR de SSE. En plataformas ARM, **_statusfp** devuelve el estado desde el registro fpscr.

**_statusfp** es una versión independiente de la plataforma y portable de **_status87**. Es idéntico a **_status87** en plataformas Intel (x86) y también es compatible con la x64 y las plataformas ARM. Para asegurarse de que el código de punto flotante es portable a todas las arquitecturas, use **_statusfp**. Si solo va a usar x86 plataformas, se puede usar **_status87** o **_statusfp**.

Se recomienda **_statusfp2** para los chips (como Pentium IV) que tienen un x87 y un procesador de punto flotante SSE2. Para **_statusfp2**, las direcciones se rellenan mediante la palabra de estado de punto flotante para x87 o el procesador de punto flotante SSE2. Chips que admite x87 y procesadores de punto flotante SSE2, EM_AMBIGUOUS se establece en 1 si **_statusfp** o **_controlfp** se usa y la acción es ambigua porque podría referirse a x87 o SSE2 palabra de estado de punto flotante. El **_statusfp2** función solo se admite en x86 plataformas.

Estas funciones no son útiles para [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) porque common language runtime (CLR) solo admite la precisión de punto flotante predeterminada.

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
