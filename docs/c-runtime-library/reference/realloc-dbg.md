---
title: _realloc_dbg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _realloc_dbg
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
- _realloc_dbg
- realloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- reallocating memory blocks
- realloc_dbg function
- memory blocks, reallocating
- memory, reallocating
- _realloc_dbg function
ms.assetid: 7c3cb780-51ed-4d9c-9929-cdde606d846a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c4bb3eab58807805ec3c4fbc35611d268bbeee9
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451646"
---
# <a name="reallocdbg"></a>_realloc_dbg

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

*UserData*<br/>
Puntero al bloque de memoria asignado previamente.

*newSize*<br/>
Tamaño solicitado para el bloque reasignado (bytes).

*blockType*<br/>
Tipo solicitado para el bloque reasignado: **_CLIENT_BLOCK** o **_NORMAL_BLOCK**.

*filename*<br/>
Puntero al nombre del archivo de origen que solicitó el **realloc** operación o **NULL**.

*linenumber*<br/>
Número de línea en el archivo de código fuente donde el **realloc** se solicitó la operación o **NULL**.

El *filename* y *linenumber* parámetros solo están disponibles cuando **_realloc_dbg** se ha llamado explícitamente o [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) se ha definido la constante de preprocesador.

## <a name="return-value"></a>Valor devuelto

Cuando se finaliza correctamente, esta función devuelve un puntero a la parte de usuario del bloque de memoria reasignado, llama a la nueva función de controlador o devuelve **NULL**. Para obtener una descripción completa del comportamiento de retorno, vea la sección de comentarios más abajo. Para obtener más información sobre cómo se usa la nueva función de controlador, vea la función [realloc](realloc.md).

## <a name="remarks"></a>Comentarios

**_realloc_dbg** es una versión de depuración de la [realloc](realloc.md) función. Cuando [_DEBUG](../../c-runtime-library/debug.md) no está definido, cada llamada a **_realloc_dbg** se reduce a una llamada a **realloc**. Ambos **realloc** y **_realloc_dbg** reasignan un bloque de memoria del montón base, pero **_realloc_dbg** admite varias características de depuración: búferes situados a cada lado de la parte de usuario del bloque para comprobar si hay pérdidas, un parámetro de tipo de bloque para realizar el seguimiento de tipos de asignación concretos, y *filename*/*linenumber* información para determinar el origen de solicitudes de asignación.

**_realloc_dbg** reasigna el bloque de memoria especificado con un poco más de espacio que solicitado *newSize*. *newSize* podría ser mayor o menor que el tamaño del bloque de memoria asignado originalmente. El administrador del montón de depuración usa el espacio adicional para vincular los bloques de memoria de depuración, y para proporcionar a la aplicación información de encabezado de depuración y sobrescribir los búferes. La reasignación podría hacer que el bloque de memoria original se ponga en una ubicación distinta del montón y cambiar el tamaño del bloque de memoria. Si se mueve el bloque de memoria, el contenido del bloque original se sobrescribe.

**_realloc_dbg** establece **errno** a **ENOMEM** si se produce un error en una asignación de memoria o si la cantidad de memoria necesaria (incluida la sobrecarga ya mencionada) es mayor **_HEAP_ MAXREQ**. Para obtener información sobre este y otros códigos de error, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

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
