---
title: _aligned_offset_malloc_dbg
ms.date: 11/04/2016
apiname:
- _aligned_offset_malloc_dbg
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
apitype: DLLExport
f1_keywords:
- _aligned_offset_malloc_dbg
- aligned_offset_malloc_dbg
helpviewer_keywords:
- _aligned_offset_malloc_dbg function
- aligned_offset_malloc_dbg function
ms.assetid: 6c242307-c59e-4d63-aae5-d8cbec8e021c
ms.openlocfilehash: 96fe9e7fda0d0cdfdbfa5462e4f601e3649e2233
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348879"
---
# <a name="alignedoffsetmallocdbg"></a>_aligned_offset_malloc_dbg

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
Puntero al nombre del archivo de código fuente que solicitó la operación de asignación o **NULL**.

*linenumber*<br/>
Número de línea en el archivo de origen que se solicitó la operación de asignación o **NULL**.

## <a name="return-value"></a>Valor devuelto

Un puntero al bloque de memoria que se ha asignado o **NULL** si la operación produjo un error.

## <a name="remarks"></a>Comentarios

**_aligned_offset_malloc_dbg** es una versión de depuración de la [_aligned_offset_malloc](aligned-offset-malloc.md) función. Cuando [_DEBUG](../../c-runtime-library/debug.md) no está definido, cada llamada a **_aligned_offset_malloc_dbg** se reduce a una llamada a **_aligned_offset_malloc**. Ambos **_aligned_offset_malloc** y **_aligned_offset_malloc_dbg** asignan un bloque de memoria del montón base, pero **_aligned_offset_malloc_dbg** ofrece varios las características de depuración: búferes situados a cada lado de la parte del usuario del bloque para comprobar si hay pérdidas, y *filename*/*linenumber* información para determinar el origen de solicitudes de asignación. Seguimiento de los tipos de asignación concretos con un parámetro de tipo de bloque no es una característica de depuración compatibles para las asignaciones de alineado. Las asignaciones de alineado aparecerá como un tipo de bloque _NORMAL_BLOCK.

**_aligned_offset_malloc_dbg** asigna el bloque de memoria con un poco más de espacio solicitado *tamaño*. El administrador del montón de depuración usa el espacio adicional para vincular los bloques de memoria de depuración, y para proporcionar a la aplicación información de encabezado de depuración y sobrescribir los búferes. Cuando se asigna el bloque, la parte del usuario de bloque se rellena con el valor 0xCD y cada uno de los búferes sobrescritos se rellena con 0xFD.

**_aligned_offset_malloc_dbg** resulta útil en situaciones donde la alineación se necesita en un elemento anidado; por ejemplo, si se necesitara la alineación en una clase anidada.

**_aligned_offset_malloc_dbg** se basa en **malloc**; para obtener más información, consulte [malloc](malloc.md).

Esta función establece **errno** a **ENOMEM** si produjo un error en la asignación de memoria o si el tamaño solicitado es mayor que **_HEAP_MAXREQ**. Para obtener más información acerca de **errno**, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Además, **_aligned_offset_malloc** valida sus parámetros. Si *alineación* no es una potencia de 2 o si *desplazamiento* es mayor o igual a *tamaño* y distinto de cero, esta función invoca al controlador de parámetros no válidos, tal y como se describe en [ Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve **NULL** y establece **errno** a **EINVAL**.

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
