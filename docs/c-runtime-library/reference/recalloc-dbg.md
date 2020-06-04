---
title: _recalloc_dbg
ms.date: 11/04/2016
api_name:
- _recalloc_dbg
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
- recalloc_dbg
- _recalloc_dbg
helpviewer_keywords:
- _recalloc_dbg function
- recalloc_dbg function
ms.assetid: 43c3e9b2-be6d-4508-9b0f-3220c8a47ca3
ms.openlocfilehash: 6274e749b2c4e6f64c7c7f82f8764dcf5ba642fe
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949470"
---
# <a name="_recalloc_dbg"></a>_recalloc_dbg

Reasigna una matriz e inicializa sus elementos a 0 (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
void *_recalloc_dbg(
   void *userData,
   size_t num,
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parámetros

*userData*<br/>
Puntero al bloque de memoria asignado previamente.

*number*<br/>
Número de bloques de memoria solicitado.

*size*<br/>
Tamaño de cada bloque de memoria solicitado (bytes).

*blockType*<br/>
Tipo de bloque de memoria solicitado: _ **client_block** o **_NORMAL_BLOCK**.

Para obtener información sobre la asignación de tipos de bloque y cómo se usan, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details).

*filename*<br/>
Puntero al nombre del archivo de código fuente que solicitó la operación de asignación o **null**.

*linenumber*<br/>
Número de línea del archivo de código fuente donde se solicitó la operación de asignación o **null**.

Los parámetros *filename* y *lineNumber* solo están disponibles cuando se ha llamado a **_recalloc_dbg** explícitamente o se ha definido la constante de preprocesador _ [crtdbg_map_alloc](../../c-runtime-library/crtdbg-map-alloc.md) .

## <a name="return-value"></a>Valor devuelto

Si se completa correctamente, esta función devuelve un puntero a la parte del usuario del bloque de memoria reasignado, llama a la nueva función de controlador o devuelve **null**. Para obtener una descripción completa del comportamiento de retorno, vea la sección de comentarios más abajo. Para obtener más información sobre cómo se usa la nueva función de controlador, vea la función [_recalloc](recalloc.md).

## <a name="remarks"></a>Comentarios

**_recalloc_dbg** es una versión de depuración de la función [_recalloc](recalloc.md) . Cuando no se define [_ Debug](../../c-runtime-library/debug.md) , cada llamada a **_recalloc_dbg** se reduce a una llamada a **_recalloc**. Tanto **_recalloc** como **_recalloc_dbg** reasignan un bloque de memoria en el montón base, pero **_recalloc_dbg** admite varias características de depuración: búferes situados a cada lado de la parte del usuario del bloque para comprobar si hay pérdidas, un parámetro de tipo de bloque para realizar el seguimiento de tipos de asignación específicos y la información de *nombre de archivo*/*lineNumber* para determinar el origen de las solicitudes de asignación.

**_recalloc_dbg** reasigna el bloque de memoria especificado con un poco más de espacio que el tamaño solicitado (*tamaño* *número* * ), que puede ser mayor o menor que el tamaño del bloque de memoria asignado originalmente. El administrador del montón de depuración usa el espacio adicional para vincular los bloques de memoria de depuración, y para proporcionar a la aplicación información de encabezado de depuración y sobrescribir los búferes. La reasignación podría hacer que el bloque de memoria original se ponga en una ubicación distinta del montón y cambiar el tamaño del bloque de memoria. La parte del usuario de bloque se rellena con el valor 0xCD y cada uno de los búferes sobrescritos se rellena con 0xFD.

**_recalloc_dbg** establece **errno** en **ENOMEM** si se produce un error de asignación de memoria. Se devuelve **EINVAL** si la cantidad de memoria necesaria (incluida la sobrecarga mencionada anteriormente) supera el valor de **_HEAP_MAXREQ**. Para obtener información sobre este y otros códigos de error, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, vea [Versiones de depuración de las funciones de asignación del montón](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_recalloc_dbg**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
