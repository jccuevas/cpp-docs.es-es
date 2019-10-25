---
title: _malloc_dbg
ms.date: 11/04/2016
api_name:
- _malloc_dbg
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
- malloc_dbg
- _malloc_dbg
helpviewer_keywords:
- malloc_dbg function
- memory allocation
- _malloc_dbg function
ms.assetid: c97eca51-140b-4461-8bd2-28965b49ecdb
ms.openlocfilehash: cfaaaec17dc8546c937045f93027e9609981bd93
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952876"
---
# <a name="_malloc_dbg"></a>_malloc_dbg

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
Tipo solicitado del bloque de memoria: _ **client_block** o **_NORMAL_BLOCK**.

*filename*<br/>
Puntero al nombre del archivo de código fuente que solicitó la operación de asignación o **null**.

*linenumber*<br/>
Número de línea del archivo de código fuente donde se solicitó la operación de asignación o **null**.

Los parámetros *filename* y *lineNumber* solo están disponibles cuando se ha llamado a **_ malloc_dbg** explícitamente o se ha definido la constante de preprocesador _ [crtdbg_map_alloc](../../c-runtime-library/crtdbg-map-alloc.md) .

## <a name="return-value"></a>Valor devuelto

Cuando se completa correctamente, esta función devuelve un puntero a la parte del usuario del bloque de memoria asignado, llama a la nueva función de controlador o devuelve **null**. Para obtener una descripción completa del comportamiento de retorno, vea la sección de comentarios más abajo. Para obtener más información sobre cómo se usa la nueva función de controlador, vea la función [malloc](malloc.md).

## <a name="remarks"></a>Comentarios

**_ malloc_dbg** es una versión de depuración de la función [malloc](malloc.md) . Cuando no se define [_ Debug](../../c-runtime-library/debug.md) , cada llamada a **_ malloc_dbg** se reduce a una llamada a **malloc**. **Malloc** y **_ malloc_dbg** asignan un bloque de memoria en el montón base, pero **_ malloc_dbg** ofrece varias características de depuración: búferes situados a cada lado de la parte del usuario del bloque para comprobar si hay pérdidas, un parámetro de tipo de bloque para realizar el seguimiento. tipos de asignación específicos e información de *nombre de archivo*/*lineNumber* para determinar el origen de las solicitudes de asignación.

**_ malloc_dbg** asigna el bloque de memoria con un poco más de espacio que el *tamaño*solicitado. El administrador del montón de depuración usa el espacio adicional para vincular los bloques de memoria de depuración, y para proporcionar a la aplicación información de encabezado de depuración y sobrescribir los búferes. Cuando se asigna el bloque, la parte del usuario de bloque se rellena con el valor 0xCD y cada uno de los búferes sobrescritos se rellena con 0xFD.

**_ malloc_dbg** establece **errno** en **ENOMEM** si se produce un error de asignación de memoria o si la cantidad de memoria necesaria (incluida la sobrecarga mencionada anteriormente) supera el valor de **_HEAP_MAXREQ**. Para obtener información sobre este y otros códigos de error, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre la asignación de tipos de bloque y cómo se usan, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, consulte [Versiones de depuración de las funciones de asignación del montón](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_malloc_dbg**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

Para obtener un ejemplo de cómo usar **_ malloc_dbg**, vea [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1).

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
[malloc](malloc.md)<br/>
[_calloc_dbg](calloc-dbg.md)<br/>
