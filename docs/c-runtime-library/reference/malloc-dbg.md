---
title: _malloc_dbg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _malloc_dbg
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
- malloc_dbg
- _malloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- malloc_dbg function
- memory allocation
- _malloc_dbg function
ms.assetid: c97eca51-140b-4461-8bd2-28965b49ecdb
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 080bd3813fe14187df7f6b6184a0cfe21e9c5243
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="mallocdbg"></a>_malloc_dbg

Asigna un bloque de memoria del montón con espacio adicional para un encabezado de depuración y búferes sobrescritos (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
void *_malloc_dbg(
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parámetros

*size*<br/>
Tamaño solicitado del bloque de memoria (en bytes).

*blockType*<br/>
Tipo del bloque de memoria solicitado: **_CLIENT_BLOCK** o **_NORMAL_BLOCK**.

*filename*<br/>
Puntero al nombre del archivo de código fuente que solicitó la operación de asignación o valor NULL.

*linenumber*<br/>
Número de línea del archivo de código fuente en la que se solicitó la operación de asignación o valor NULL.

El *filename* y *linenumber* parámetros solo están disponibles cuando **_malloc_dbg** se ha llamado explícitamente o [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)se ha definido la constante de preprocesador.

## <a name="return-value"></a>Valor devuelto

Cuando se lleva a cabo correctamente, esta función devuelve un puntero a la parte del usuario del último bloque de memoria asignado, llama a la nueva función de controlador o devuelve NULL. Para obtener una descripción completa del comportamiento de retorno, vea la sección de comentarios más abajo. Para obtener más información sobre cómo se usa la nueva función de controlador, vea la función [malloc](malloc.md).

## <a name="remarks"></a>Comentarios

**_malloc_dbg** es una versión de depuración de la [malloc](malloc.md) función. Cuando [_DEBUG](../../c-runtime-library/debug.md) no está definido, cada llamada a **_malloc_dbg** se reduce a una llamada a **malloc**. Ambos **malloc** y **_malloc_dbg** asignar un bloque de memoria del montón base, pero **_malloc_dbg** ofrece varias características de depuración: búferes situados a cada lado del usuario parte del bloque para comprobar si hay pérdidas, un parámetro de tipo de bloque para realizar el seguimiento de tipos de asignación concretos, y *filename*/*linenumber* información para determinar el origen de solicitudes de asignación.

**_malloc_dbg** asigna el bloque de memoria con un poco más de espacio que solicitado *tamaño*. El administrador del montón de depuración usa el espacio adicional para vincular los bloques de memoria de depuración, y para proporcionar a la aplicación información de encabezado de depuración y sobrescribir los búferes. Cuando se asigna el bloque, la parte del usuario de bloque se rellena con el valor 0xCD y cada uno de los búferes sobrescritos se rellena con 0xFD.

**_malloc_dbg** establece **errno** a **ENOMEM** si se produce un error en una asignación de memoria o si la cantidad de memoria necesaria (incluida la sobrecarga ya mencionada) es mayor **_HEAP_ MAXREQ**. Para obtener información sobre este y otros códigos de error, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre la asignación de tipos de bloque y cómo se usan, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, consulte [Versiones de depuración de las funciones de asignación del montón](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_malloc_dbg**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

Para obtener un ejemplo de cómo usar **_malloc_dbg**, consulte [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1).

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
[malloc](malloc.md)<br/>
[_calloc_dbg](calloc-dbg.md)<br/>
[_calloc_dbg](calloc-dbg.md)<br/>
