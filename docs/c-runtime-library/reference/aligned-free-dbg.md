---
title: _aligned_free_dbg
ms.date: 11/04/2016
api_name:
- _aligned_free_dbg
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _aligned_free_dbg
- aligned_free_dbg
helpviewer_keywords:
- _aligned_free_dbg function
- aligned_free_dbg function
ms.assetid: eb0cb3c8-0992-4db8-bac3-65f1b8311ca6
ms.openlocfilehash: 18c1a23d666070afaf1eff687c7d33b0240f0ac3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171286"
---
# <a name="_aligned_free_dbg"></a>_aligned_free_dbg

Libera un bloque de memoria que se ha asignado con [_aligned_malloc](aligned-malloc.md) o [_aligned_offset_malloc](aligned-offset-malloc.md) (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
void _aligned_free_dbg(
   void *memblock
);
```

### <a name="parameters"></a>Parámetros

*memblock*<br/>
Puntero al bloque de memoria que se devolvió a la función [_aligned_malloc](aligned-malloc.md) o [_aligned_offset_malloc](aligned-offset-malloc.md) .

## <a name="remarks"></a>Observaciones

La función **_aligned_free_dbg** es una versión de depuración de la función [_aligned_free](aligned-free.md) . Cuando no se define [_DEBUG](../../c-runtime-library/debug.md) , cada llamada a **_aligned_free_dbg** se reduce a una llamada a `_aligned_free`. Tanto `_aligned_free` como **_aligned_free_dbg** liberar un bloque de memoria en el montón base, pero **_aligned_free_dbg** admite una característica de depuración: la capacidad de mantener los bloques liberados en la lista vinculada del montón para simular condiciones de memoria insuficiente.

**_aligned_free_dbg** realiza una comprobación de validez en todos los archivos especificados y las ubicaciones de bloques antes de realizar la operación de liberación. No se espera que la aplicación proporcione esta información. Cuando se libera un bloque de memoria, el administrador del montón de depuración comprueba automáticamente la integridad de los búferes situados a cada lado de la parte del usuario y emite un informe de error en caso de sobrescritura. Si se establece el campo de bits _CRTDBG_DELAY_FREE_MEM_DF del indicador de [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) , el bloque liberado se rellena con el valor 0xDD, se le asigna el tipo de bloque _FREE_BLOCK y se mantiene en la lista vinculada de bloques de memoria del montón.

Si se produce un error al liberar memoria, en `errno` se muestra información sobre la naturaleza del error proporcionada por el sistema operativo. Para obtener más información, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre la asignación de tipos de bloque y cómo se usan, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, vea [Versiones de depuración de las funciones de asignación del montón](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_aligned_free_dbg**|\<crtdbg.h>|

Para más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)
