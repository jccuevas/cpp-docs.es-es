---
title: _free_dbg
ms.date: 11/04/2016
api_name:
- _free_dbg
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
- _free_dbg
- free_dbg
helpviewer_keywords:
- memory blocks, deallocating
- freeing memory
- _free_dbg function
- free_dbg function
ms.assetid: fc5e8299-616d-48a0-b979-e037117278c6
ms.openlocfilehash: 43591ce8710dd25ad33832a5f084ca6e84bba979
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956804"
---
# <a name="_free_dbg"></a>_free_dbg

Libera un bloque de memoria del montón (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
void _free_dbg(
   void *userData,
   int blockType
);
```

### <a name="parameters"></a>Parámetros

*userData*<br/>
Puntero al bloque de memoria asignado que se va a liberar.

*blockType*<br/>
Tipo de bloque de memoria asignado que se va a liberar: _ **client_block**, **_NORMAL_BLOCK**o **_IGNORE_BLOCK**.

## <a name="remarks"></a>Comentarios

La función **_free_dbg** es una versión de depuración de la función [Free](free.md) . Cuando no se define [_ Debug](../../c-runtime-library/debug.md) , cada llamada a **_free_dbg** se reduce a una llamada a **Free**. **Free** y **_free_dbg** liberan un bloque de memoria en el montón base, pero **_free_dbg** admite dos características de depuración: la posibilidad de mantener los bloques liberados en la lista vinculada del montón para simular condiciones de memoria insuficiente y un parámetro de tipo de bloque en tipos de asignación específicos gratuitos.

**_free_dbg** realiza una comprobación de validez en todos los archivos especificados y las ubicaciones de bloques antes de realizar la operación de liberación. No se espera que la aplicación proporcione esta información. Cuando se libera un bloque de memoria, el administrador del montón de depuración comprueba automáticamente la integridad de los búferes situados a cada lado de la parte del usuario y emite un informe de error en caso de sobrescritura. Si se establece el campo de bits **_CRTDBG_DELAY_FREE_MEM_DF** de la marca _ [crtdbgflag](../../c-runtime-library/crtdbgflag.md) , el bloque liberado se rellena con el valor 0xDD, se le asigna el tipo de bloque **_FREE_BLOCK** y se mantiene en la lista vinculada de bloques de memoria del montón.

Si se produce un error al liberar memoria, **errno** se establece con información del sistema operativo sobre la naturaleza del error. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre la asignación de tipos de bloque y cómo se usan, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, consulte [Versiones de depuración de las funciones de asignación del montón](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_free_dbg**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Para obtener un ejemplo de cómo usar **_free_dbg**, consulte [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
