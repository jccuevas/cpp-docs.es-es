---
title: _calloc_dbg
ms.date: 11/04/2016
apiname:
- _calloc_dbg
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
- _calloc_dbg
- calloc_dbg
helpviewer_keywords:
- _calloc_dbg function
- calloc_dbg function
ms.assetid: 7f62c42b-eb9f-4de5-87d0-df57036c87de
ms.openlocfilehash: c525aa2f19b39ba3cb8304c59c96196707ad859c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454397"
---
# <a name="callocdbg"></a>_calloc_dbg

Asigna varios bloques de memoria del montón con espacio adicional para un encabezado de depuración y búferes sobrescritos (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
void *_calloc_dbg(
   size_t num,
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parámetros

*Número*<br/>
Número de bloques de memoria solicitado.

*size*<br/>
Tamaño de cada bloque de memoria solicitado (bytes).

*blockType*<br/>
Tipo de bloque de memoria solicitado: **_CLIENT_BLOCK** o **_NORMAL_BLOCK**.

Para obtener información sobre la asignación de tipos de bloque y cómo se usan, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details).

*filename*<br/>
Puntero al nombre del archivo de código fuente que solicitó la operación de asignación o **NULL**.

*linenumber*<br/>
Número de línea en el archivo de origen que se solicitó la operación de asignación o **NULL**.

El *filename* y *linenumber* parámetros solo están disponibles cuando **_calloc_dbg** se ha llamado explícitamente o [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)se ha definido la constante de preprocesador.

## <a name="return-value"></a>Valor devuelto

Se completa correctamente, esta función devuelve un puntero a la parte del usuario del último bloque de memoria asignado, llama a la nueva función de controlador o devuelve **NULL**. Para obtener una descripción completa del comportamiento de retorno, vea la sección de comentarios. Para obtener más información sobre cómo se usa la nueva función de controlador, consulte la función [calloc](calloc.md).

## <a name="remarks"></a>Comentarios

**_calloc_dbg** es una versión de depuración de la [calloc](calloc.md) función. Cuando [_DEBUG](../../c-runtime-library/debug.md) no está definido, cada llamada a **_calloc_dbg** se reduce a una llamada a **calloc**. Ambos **calloc** y **_calloc_dbg** asignar *número* bloques de memoria del montón base, pero **_calloc_dbg** ofrece varios depuración características:

- Búferes situados a cada lado de la parte del usuario del bloque para comprobar si hay pérdidas.

- Un parámetro de tipo de bloque para realizar el seguimiento de tipos de asignación específicos.

- *nombre de archivo*/*linenumber* información para determinar el origen de las solicitudes de asignación.

**_calloc_dbg** asigna cada bloque de memoria con un poco más de espacio solicitado *tamaño*. El administrador del montón de depuración usa el espacio adicional para vincular los bloques de memoria de depuración, y para proporcionar a la aplicación información de encabezado de depuración y sobrescribir los búferes. Cuando se asigna el bloque, la parte del usuario de bloque se rellena con el valor 0xCD y cada uno de los búferes sobrescritos se rellena con 0xFD.

**_calloc_dbg** establece **errno** a **ENOMEM** si se produce un error en una asignación de memoria; **EINVAL** se devuelve si se supera la cantidad de memoria necesaria (incluida la sobrecarga ya mencionada) **_HEAP_MAXREQ**. Para obtener información sobre este y otros códigos de error, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre las diferencias entre llamar a una función estándar del montón y llamar a su versión de depuración en una compilación de depuración de una aplicación, consulte [Versiones de depuración de las funciones de asignación del montón](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_calloc_dbg**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_callocd.c
// This program uses _calloc_dbg to allocate space for
// 40 long integers. It initializes each element to zero.

#include <stdio.h>
#include <malloc.h>
#include <crtdbg.h>

int main( void )
{
    long *bufferN, *bufferC;

    // Call _calloc_dbg to include the filename and line number
    // of our allocation request in the header and also so we can
    // allocate CLIENT type blocks specifically
    bufferN = (long *)_calloc_dbg( 40, sizeof(long), _NORMAL_BLOCK, __FILE__, __LINE__ );
    bufferC = (long *)_calloc_dbg( 40, sizeof(long), _CLIENT_BLOCK, __FILE__, __LINE__ );
    if( bufferN != NULL && bufferC != NULL )
        printf( "Allocated memory successfully\n" );
    else
        printf( "Problem allocating memory\n" );

    / _free_dbg must be called to free CLIENT type blocks
    free( bufferN );
    _free_dbg( bufferC, _CLIENT_BLOCK );
}
```

```Output
Allocated memory successfully
```

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
[calloc](calloc.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
