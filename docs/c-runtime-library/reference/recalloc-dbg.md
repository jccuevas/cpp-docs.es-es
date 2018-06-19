---
title: _recalloc_dbg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _recalloc_dbg
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
- recalloc_dbg
- _recalloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- _recalloc_dbg function
- recalloc_dbg function
ms.assetid: 43c3e9b2-be6d-4508-9b0f-3220c8a47ca3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3de6adddc4e7d95f3212c80666816d4855897388
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451054"
---
# <a name="recallocdbg"></a>_recalloc_dbg

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

*UserData*<br/>
Puntero al bloque de memoria asignado previamente.

*Número*<br/>
Número de bloques de memoria solicitado.

*size*<br/>
Tamaño de cada bloque de memoria solicitado (bytes).

*blockType*<br/>
Tipo de bloque de memoria solicitado: **_CLIENT_BLOCK** o **_NORMAL_BLOCK**.

Para obtener información sobre la asignación de tipos de bloque y cómo se usan, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details).

*filename*<br/>
Puntero al nombre del archivo de origen que solicitó la operación de asignación o **NULL**.

*linenumber*<br/>
Número de línea en el archivo de origen que se solicitó la operación de asignación o **NULL**.

El *filename* y *linenumber* parámetros solo están disponibles cuando **_recalloc_dbg** se ha llamado explícitamente o [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) se ha definido la constante de preprocesador.

## <a name="return-value"></a>Valor devuelto

Cuando se finaliza correctamente, esta función devuelve un puntero a la parte de usuario del bloque de memoria reasignado, llama a la nueva función de controlador o devuelve **NULL**. Para obtener una descripción completa del comportamiento de retorno, vea la sección de comentarios más abajo. Para obtener más información sobre cómo se usa la nueva función de controlador, vea la función [_recalloc](recalloc.md).

## <a name="remarks"></a>Comentarios

**_recalloc_dbg** es una versión de depuración de la [_recalloc](recalloc.md) (función). Cuando [_DEBUG](../../c-runtime-library/debug.md) no está definido, cada llamada a **_recalloc_dbg** se reduce a una llamada a **_recalloc**. Ambos **_recalloc** y **_recalloc_dbg** reasignan un bloque de memoria del montón base, pero **_recalloc_dbg** admite varias características de depuración: búferes situados a cada lado de la parte de usuario del bloque para comprobar si hay pérdidas, un bloque de tipo de parámetro para realizar el seguimiento de tipos de asignación concretos, y *filename*/*linenumber* información para determinar la origen de las solicitudes de asignación.

**_recalloc_dbg** reasigna el bloque de memoria especificado con un poco más espacio que el tamaño solicitado (*número* * *tamaño*) que podría ser mayor o menor que el tamaño de el bloque de memoria asignado originalmente. El administrador del montón de depuración usa el espacio adicional para vincular los bloques de memoria de depuración, y para proporcionar a la aplicación información de encabezado de depuración y sobrescribir los búferes. La reasignación podría hacer que el bloque de memoria original se ponga en una ubicación distinta del montón y cambiar el tamaño del bloque de memoria. La parte del usuario de bloque se rellena con el valor 0xCD y cada uno de los búferes sobrescritos se rellena con 0xFD.

**_recalloc_dbg** establece **errno** a **ENOMEM** si se produce un error en una asignación de memoria; **EINVAL** se devuelve si se supera la cantidad de memoria necesaria (incluida la sobrecarga ya mencionada) **_HEAP_MAXREQ**. Para obtener información sobre este y otros códigos de error, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

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
