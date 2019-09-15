---
title: _set_SSE2_enable
ms.date: 04/05/2018
api_name:
- _set_SSE2_enable
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
- _set_SSE2_enable
- set_SSE2_enable
helpviewer_keywords:
- _set_SSE2_enable function
- Streaming SIMD Extensions 2 instructions
- set_SSE2_enable function
ms.assetid: 55db895d-fc1e-475a-9110-b781a9bb51c5
ms.openlocfilehash: 8838282db851c6811a3f24c75a03b31c5870e6d3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948352"
---
# <a name="_set_sse2_enable"></a>_set_SSE2_enable

Habilita o deshabilita el uso de las instrucciones de extensiones SIMD de streaming 2 (SSE2) en las rutinas matemáticas de CRT. (esta función no está disponible en las arquitecturas x64 porque SSE2 está habilitada de forma predeterminada).

## <a name="syntax"></a>Sintaxis

```C
int _set_SSE2_enable(
   int flag
);
```

### <a name="parameters"></a>Parámetros

*flag*<br/>
1 para habilitar la implementación de SSE2 y 0 para deshabilitarla. De forma predeterminada, la implementación de SSE2 está habilitada en los procesadores compatibles.

## <a name="return-value"></a>Valor devuelto

Valor distinto de cero si la implementación de SSE2 está habilitada; cero si está deshabilitada.

## <a name="remarks"></a>Comentarios

Las siguientes funciones tienen implementaciones SSE2 que se pueden habilitar mediante **_set_SSE2_enable**:

- [atan](atan-atanf-atanl-atan2-atan2f-atan2l.md)

- [ceil](ceil-ceilf-ceill.md)

- [exp](exp-expf.md)

- [floor](floor-floorf-floorl.md)

- [log](log-logf-log10-log10f.md)

- [log10](log-logf-log10-log10f.md)

- [modf](modf-modff-modfl.md)

- [pow](pow-powf-powl.md)

Las implementaciones de SSE2 de estas funciones pueden proporcionar respuestas algo diferentes que las implementaciones predeterminadas, porque los valores intermedios de SSE2 son cantidades de punto flotante de 64 bits, mientras que los valores intermedios de implementación predeterminados son cantidades de punto flotante de 80 bits.

> [!NOTE]
> Si usa la opción del compilador [/OI (generar funciones intrínsecas)](../../build/reference/oi-generate-intrinsic-functions.md) para compilar el proyecto, puede parecer que **_set_SSE2_enable** no tiene ningún efecto. La opción del compilador **/OI** proporciona al compilador la autoridad para utilizar intrínsecos para reemplazar las llamadas de CRT; Este comportamiento invalida el efecto de **_set_SSE2_enable**. Si quiere garantizar que **/OI** no invalide **_set_SSE2_enable**, use **/OI-** para compilar el proyecto. Esto también podría ser recomendable cuando se usan otros modificadores de compilador que implican **/OI**.

La implementación de SSE2 solo se usa si se enmascaran todas las excepciones. Use [_control87, _controlfp](control87-controlfp-control87-2.md) para enmascarar las excepciones.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_set_SSE2_enable**|\<math.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_set_SSE2_enable.c
// processor: x86
#include <math.h>
#include <stdio.h>

int main()
{
   int i = _set_SSE2_enable(1);

   if (i)
      printf("SSE2 enabled.\n");
   else
      printf("SSE2 not enabled; processor does not support SSE2.\n");
}
```

```Output
SSE2 enabled.
```

## <a name="see-also"></a>Vea también

[Características de la biblioteca CRT](../../c-runtime-library/crt-library-features.md)<br/>
