---
title: _realloc_dbg
ms.date: 11/04/2016
api_name:
- _realloc_dbg
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
- _realloc_dbg
- realloc_dbg
helpviewer_keywords:
- reallocating memory blocks
- realloc_dbg function
- memory blocks, reallocating
- memory, reallocating
- _realloc_dbg function
ms.assetid: 7c3cb780-51ed-4d9c-9929-cdde606d846a
ms.openlocfilehash: 58d12ed6f4b013996f3f59cba1b146b823adbee6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949514"
---
# <a name="_realloc_dbg"></a>_realloc_dbg

Reasigna un bloque de memoria especificado en el montón moviendo o cambiando el tamaño del bloque (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
void *_realloc_dbg(
   void *userData,
   size_t newSize,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parámetros

*userData*<br/>
Puntero al bloque de memoria asignado previamente.

*newSize*<br/>
Tamaño solicitado para el bloque reasignado (bytes).

*blockType*<br/>
Tipo solicitado para el bloque reasignado: _ **client_block** o **_NORMAL_BLOCK**.

*filename*<br/>
Puntero al nombre del archivo de código fuente que solicitó la operación **realloc** o **null**.

*linenumber*<br/>
Número de línea del archivo de código fuente donde se solicitó la operación **realloc** o **null**.

Los parámetros *filename* y *lineNumber* solo están disponibles cuando se ha llamado a **_realloc_dbg** explícitamente o se ha definido la constante de preprocesador _ [crtdbg_map_alloc](../../c-runtime-library/crtdbg-map-alloc.md) .

## <a name="return-value"></a>Valor devuelto

Si se completa correctamente, esta función devuelve un puntero a la parte del usuario del bloque de memoria reasignado, llama a la nueva función de controlador o devuelve **null**. Para obtener una descripción completa del comportamiento de retorno, vea la sección de comentarios más abajo. Para obtener más información sobre cómo se usa la nueva función de controlador, vea la función [realloc](realloc.md).

## <a name="remarks"></a>Comentarios

**_realloc_dbg** es una versión de depuración de la función [realloc](realloc.md) . Cuando no se define [_ Debug](../../c-runtime-library/debug.md) , cada llamada a **_realloc_dbg** se reduce a una llamada a **realloc**. **Realloc** y **_realloc_dbg** reasignan un bloque de memoria en el montón base, pero **_realloc_dbg** admite varias características de depuración: búferes situados a cada lado de la parte del usuario del bloque para comprobar si hay pérdidas, un parámetro de tipo de bloque en Realice un seguimiento de los tipos de asignación específicos y la información de *nombre de archivo*/*lineNumber* para determinar el origen de las solicitudes de asignación.

**_realloc_dbg** reasigna el bloque de memoria especificado con un poco más de espacio que el de la *NewSize*solicitada. *NewSize* puede ser mayor o menor que el tamaño del bloque de memoria asignado originalmente. El administrador del montón de depuración usa el espacio adicional para vincular los bloques de memoria de depuración, y para proporcionar a la aplicación información de encabezado de depuración y sobrescribir los búferes. La reasignación podría hacer que el bloque de memoria original se ponga en una ubicación distinta del montón y cambiar el tamaño del bloque de memoria. Si se mueve el bloque de memoria, el contenido del bloque original se sobrescribe.

**_realloc_dbg** establece **errno** en **ENOMEM** si se produce un error de asignación de memoria o si la cantidad de memoria necesaria (incluida la sobrecarga mencionada anteriormente) supera **_HEAP_MAXREQ**. Para obtener información sobre este y otros códigos de error, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre la asignación de tipos de bloque y cómo se usan, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, consulte [Versiones de depuración de las funciones de asignación del montón](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_realloc_dbg**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo del tema [_msize_dbg](msize-dbg.md).

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
