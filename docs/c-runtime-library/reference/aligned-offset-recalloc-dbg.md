---
title: _aligned_offset_recalloc_dbg
ms.date: 11/04/2016
api_name:
- _aligned_offset_recalloc_dbg
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
- aligned_offset_recalloc_dbg
- _aligned_offset_recalloc_dbg
helpviewer_keywords:
- aligned_offset_recalloc_dbg function
- _aligned_offset_recalloc_dbg function
ms.assetid: 7ab719c3-77e0-4d2e-934f-01529d062fbf
ms.openlocfilehash: e363a1cb104db9973f5f9e9c67a5d40693d405ee
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939746"
---
# <a name="_aligned_offset_recalloc_dbg"></a>_aligned_offset_recalloc_dbg

Cambia el tamaño de un bloque de memoria que se ha asignado con [_aligned_malloc](aligned-malloc.md) o [_aligned_offset_malloc](aligned-offset-malloc.md) e inicializa la memoria a 0 (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
void * _aligned_offset_recalloc_dbg(
   void *memblock,
   size_t num,
   size_t size,
   size_t alignment,
   size_t offset,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parámetros

*memblock*<br/>
Puntero de bloque de memoria actual.

*number*<br/>
Número de elementos.

*size*<br/>
Longitud en bytes de cada elemento.

*alignment*<br/>
Valor de la alineación, que debe ser un entero potencia de 2.

*offset*<br/>
Desplazamiento en la asignación de memoria para imponer la alineación.

*filename*<br/>
Puntero al nombre del archivo de código fuente que solicitó la operación realloc o **null**.

*linenumber*<br/>
Número de línea del archivo de código fuente donde se solicitó la operación realloc o **null**.

## <a name="return-value"></a>Valor devuelto

**_aligned_offset_recalloc_dbg** devuelve un puntero void al bloque de memoria reasignado (y que posiblemente se ha cambiado). El valor devuelto es **null** si el tamaño es cero y el argumento de búfer no es **null**, o si no hay suficiente memoria disponible para expandir el bloque al tamaño especificado. En el primer caso, se libera el bloque original. En el segundo, el bloque original permanece inalterado. El valor devuelto apunta a un espacio de almacenamiento confirmado como correctamente alineado para almacenar cualquier tipo de objeto. Para obtener un puntero a un tipo distinto a void, use una conversión de tipo en el valor devuelto.

## <a name="remarks"></a>Comentarios

**_aligned_offset_realloc_dbg** es una versión de depuración de la función [_aligned_offset_recalloc](aligned-offset-recalloc.md) . Cuando no se define [_ Debug](../../c-runtime-library/debug.md) , cada llamada a **_aligned_offset_recalloc_dbg** se reduce a una llamada a **_aligned_offset_recalloc**. Tanto **_aligned_offset_recalloc** como **_aligned_offset_recalloc_dbg** reasignan un bloque de memoria en el montón base, pero **_aligned_offset_recalloc_dbg** admite varias características de depuración: búferes situados a cada lado de la parte del usuario del bloque en el que se van a comprobar las fugas y la información de *nombre de archivo*/*lineNumber* para determinar el origen de las solicitudes de asignación. El seguimiento de tipos de asignación específicos con un parámetro de tipo de bloque no es una característica de depuración admitida para asignaciones alineadas. Las asignaciones alineadas aparecerán como un tipo de bloque _NORMAL_BLOCK.

**_aligned_offset_realloc_dbg** reasigna el bloque de memoria especificado con un poco más de espacio que el de la *NewSize*solicitada. *NewSize* puede ser mayor o menor que el tamaño del bloque de memoria asignado originalmente. El administrador del montón de depuración usa el espacio adicional para vincular los bloques de memoria de depuración, y para proporcionar a la aplicación información de encabezado de depuración y sobrescribir los búferes. La reasignación podría hacer que el bloque de memoria original se ponga en una ubicación distinta del montón y cambiar el tamaño del bloque de memoria. Si se mueve el bloque de memoria, el contenido del bloque original se sobrescribe.

Esta función establece **errno** en **ENOMEM** si se produce un error en la asignación de memoria o si el tamaño solicitado (*tamaño*de*número* * ) era mayor que **_HEAP_MAXREQ**. Para obtener más información acerca de **errno**, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Además, **_aligned_offset_recalloc_dbg** valida sus parámetros. Si la *alineación* no es una potencia de 2 o si el *desplazamiento* es mayor o igual que el tamaño solicitado y distinto de cero, esta función invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve **null** y establece **errno** en **EINVAL**.

Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre la asignación de tipos de bloque y cómo se usan, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, consulte [Versiones de depuración de las funciones de asignación del montón](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_aligned_offset_recalloc_dbg**|\<malloc.h>|

## <a name="see-also"></a>Vea también

[Alineación de datos](../../c-runtime-library/data-alignment.md)<br/>
