---
title: _aligned_offset_malloc_dbg
ms.date: 11/04/2016
api_name:
- _aligned_offset_malloc_dbg
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
- _aligned_offset_malloc_dbg
- aligned_offset_malloc_dbg
helpviewer_keywords:
- _aligned_offset_malloc_dbg function
- aligned_offset_malloc_dbg function
ms.assetid: 6c242307-c59e-4d63-aae5-d8cbec8e021c
ms.openlocfilehash: 4fbacb170fd1ae1ce92de4a11ea85ff42b3942a0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939771"
---
# <a name="_aligned_offset_malloc_dbg"></a>_aligned_offset_malloc_dbg

Asigna memoria en un límite de alineación especificado (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
void * _aligned_offset_malloc_dbg(
   size_t size,
   size_t alignment,
   size_t offset,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parámetros

*size*<br/>
Tamaño de la asignación de memoria solicitada.

*alignment*<br/>
Valor de la alineación, que debe ser un entero potencia de 2.

*offset*<br/>
Desplazamiento en la asignación de memoria para imponer la alineación.

*filename*<br/>
Puntero al nombre del archivo de código fuente que solicitó la operación de asignación o **null**.

*linenumber*<br/>
Número de línea del archivo de código fuente donde se solicitó la operación de asignación o **null**.

## <a name="return-value"></a>Valor devuelto

Puntero al bloque de memoria que se asignó o **null** si se produjo un error en la operación.

## <a name="remarks"></a>Comentarios

**_aligned_offset_malloc_dbg** es una versión de depuración de la función [_aligned_offset_malloc](aligned-offset-malloc.md) . Cuando no se define [_ Debug](../../c-runtime-library/debug.md) , cada llamada a **_aligned_offset_malloc_dbg** se reduce a una llamada a **_aligned_offset_malloc**. Tanto **_aligned_offset_malloc** como **_aligned_offset_malloc_dbg** asignan un bloque de memoria en el montón base, pero **_aligned_offset_malloc_dbg** ofrece varias características de depuración: búferes situados a cada lado de la parte del usuario del bloque en Compruebe si hay pérdidas y la información de *nombre de archivo*/*lineNumber* para determinar el origen de las solicitudes de asignación. El seguimiento de tipos de asignación específicos con un parámetro de tipo de bloque no es una característica de depuración admitida para asignaciones alineadas. Las asignaciones alineadas aparecerán como un tipo de bloque _NORMAL_BLOCK.

**_aligned_offset_malloc_dbg** asigna el bloque de memoria con un poco más de espacio que el *tamaño*solicitado. El administrador del montón de depuración usa el espacio adicional para vincular los bloques de memoria de depuración, y para proporcionar a la aplicación información de encabezado de depuración y sobrescribir los búferes. Cuando se asigna el bloque, la parte del usuario de bloque se rellena con el valor 0xCD y cada uno de los búferes sobrescritos se rellena con 0xFD.

**_aligned_offset_malloc_dbg** es útil en situaciones en las que se necesita la alineación en un elemento anidado; por ejemplo, si se necesita la alineación en una clase anidada.

**_aligned_offset_malloc_dbg** se basa en **malloc**; para obtener más información, consulte [malloc](malloc.md).

Esta función establece **errno** en **ENOMEM** si se produce un error en la asignación de memoria o si el tamaño solicitado es mayor que **_HEAP_MAXREQ**. Para obtener más información acerca de **errno**, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Además, **_aligned_offset_malloc** valida sus parámetros. Si la *alineación* no es una potencia de 2 o si el *desplazamiento* es mayor o igual que *el tamaño* y distinto de cero, esta función invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve **null** y establece **errno** en **EINVAL**.

Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

Para obtener información sobre la asignación de tipos de bloque y cómo se usan, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_aligned_offset_malloc_dbg**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
