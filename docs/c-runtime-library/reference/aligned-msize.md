---
title: _aligned_msize
ms.date: 4/2/2020
api_name:
- _aligned_msize
- _o__aligned_msize
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _aligned_msize
- aligned_msize
helpviewer_keywords:
- aligned_msize function
- _aligned_msize function
ms.assetid: 10995edc-2110-4212-9ca9-5e0220a464f4
ms.openlocfilehash: 21ae07c90bbf9a729a212a97b7de3e0916f8e2c6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350602"
---
# <a name="_aligned_msize"></a>_aligned_msize

Devuelve el tamaño de un bloque de memoria asignado en el montón.

## <a name="syntax"></a>Sintaxis

```C
size_t _msize(
   void *memblock,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>Parámetros

*memblock*<br/>
Puntero al bloque de memoria.

*Alineación*<br/>
Valor de la alineación, que debe ser un entero potencia de 2.

*offset*<br/>
Desplazamiento en la asignación de memoria para imponer la alineación.

## <a name="return-value"></a>Valor devuelto

Devuelve el tamaño (en bytes) de un entero sin signo.

## <a name="remarks"></a>Observaciones

La función **_aligned_msize** devuelve el tamaño, en bytes, del bloque de memoria asignado por una llamada a [_aligned_malloc](aligned-malloc.md) o [_aligned_realloc](aligned-realloc.md). Los valores de *alineación* y *desfase* deben ser los mismos que los valores pasados a la función que asignó el bloque.

Cuando la aplicación está vinculada con una versión de depuración de las bibliotecas en tiempo de ejecución de C, **_aligned_msize** se resuelve en [_aligned_msize_dbg](aligned-msize-dbg.md). Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).

Esta función valida su parámetro. Si *memblock* es un puntero nulo o *la alineación* no es una potencia de 2, **_msize** invoca un controlador de parámetros no válido, como se describe en [validación](../../c-runtime-library/parameter-validation.md)de parámetros . Si se controla el error, la función establece **errno en** **EINVAL** y devuelve -1.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_msize**|\<malloc.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Consulte también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
