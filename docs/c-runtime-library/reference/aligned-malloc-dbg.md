---
title: _aligned_malloc_dbg
ms.date: 11/04/2016
apiname:
- _aligned_malloc_dbg
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
- _aligned_malloc_dbg
- aligned_malloc_dbg
helpviewer_keywords:
- aligned_malloc_dbg function
- _aligned_malloc_dbg function
ms.assetid: fb0429c3-685d-4826-9075-2515c5bdc5c6
ms.openlocfilehash: eb58313c892ffe13e9f8e34e98b7940022899d14
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62341644"
---
# <a name="alignedmallocdbg"></a>_aligned_malloc_dbg

Asigna memoria en un límite de alineación especificado con espacio adicional para un encabezado de depuración y búferes sobrescritos (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
void * _aligned_malloc_dbg(
    size_t size,
    size_t alignment,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parámetros

*size*<br/>
Tamaño de la asignación de memoria solicitada.

*alignment*<br/>
Valor de la alineación, que debe ser un entero potencia de 2.

*filename*<br/>
Puntero al nombre del archivo de código fuente que solicitó la operación de asignación o valor NULL.

*linenumber*<br/>
Número de línea del archivo de código fuente en la que se solicitó la operación de asignación o valor NULL.

## <a name="return-value"></a>Valor devuelto

Un puntero al bloque de memoria que se ha asignado o NULL si la operación produjo un error.

## <a name="remarks"></a>Comentarios

**_aligned_malloc_dbg** es una versión de depuración de la [_aligned_malloc](aligned-malloc.md) función. Cuando [_DEBUG](../../c-runtime-library/debug.md) no está definido, cada llamada a **_aligned_malloc_dbg** se reduce a una llamada a `_aligned_malloc`. Ambos `_aligned_malloc` y **_aligned_malloc_dbg** asignan un bloque de memoria del montón base, pero **_aligned_malloc_dbg** ofrece varias características de depuración: búferes situados a cada lado de la parte del usuario en el bloque para comprobar si hay pérdidas, y *filename*/*linenumber* información para determinar el origen de las solicitudes de asignación. Seguimiento de los tipos de asignación concretos con un parámetro de tipo de bloque no es una característica de depuración compatibles para las asignaciones de alineado. Las asignaciones de alineado aparecerá como un tipo de bloque _NORMAL_BLOCK.

**_aligned_malloc_dbg** asigna el bloque de memoria con un poco más de espacio solicitado *tamaño*. El administrador del montón de depuración usa el espacio adicional para vincular los bloques de memoria de depuración, y para proporcionar a la aplicación información de encabezado de depuración y sobrescribir los búferes. Cuando se asigna el bloque, la parte del usuario de bloque se rellena con el valor 0xCD y cada uno de los búferes sobrescritos se rellena con 0xFD.

**_aligned_malloc_dbg** establece `errno` a `ENOMEM` si se produce un error en una asignación de memoria o si se supera la cantidad de memoria necesaria (incluida la sobrecarga ya mencionada) `_HEAP_MAXREQ`. Para obtener información sobre este y otros códigos de error, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Además, **_aligned_malloc_dbg** valida sus parámetros. Si *alineación* no es una potencia de 2 o *tamaño* es cero, esta función invoca al controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve NULL y establece `errno` a `EINVAL`.

Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre la asignación de tipos de bloque y cómo se usan, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, consulte [Versiones de depuración de las funciones de asignación del montón](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_aligned_malloc_dbg**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)