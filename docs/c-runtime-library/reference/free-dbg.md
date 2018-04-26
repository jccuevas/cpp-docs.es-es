---
title: _free_dbg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _free_dbg
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
- _free_dbg
- free_dbg
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, deallocating
- freeing memory
- _free_dbg function
- free_dbg function
ms.assetid: fc5e8299-616d-48a0-b979-e037117278c6
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 01dfb441886b46a32a9b6605742b4cd14611b458
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="freedbg"></a>_free_dbg

Libera un bloque de memoria del montón (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
void _free_dbg(
   void *userData,
   int blockType
);
```

### <a name="parameters"></a>Parámetros

*userData* puntero al bloque de memoria asignado que se libere.

*Existen* tipo de bloque de memoria asignado que se libere: **_CLIENT_BLOCK**, **_NORMAL_BLOCK**, o **_IGNORE_BLOCK**.

## <a name="remarks"></a>Comentarios

El **_free_dbg** función es una versión de depuración de la [libre](free.md) función. Cuando [_DEBUG](../../c-runtime-library/debug.md) no está definido, cada llamada a **_free_dbg** se reduce a una llamada a **libre**. Ambos **libre** y **_free_dbg** liberar un bloque de memoria del montón base, pero **_free_dbg** incluye dos características de depuración: la posibilidad de mantener liberados bloques en el montón lista vinculada para simular condiciones de memoria insuficiente y un parámetro de tipo de bloque para liberar a tipos de asignación concretos.

**_free_dbg** realiza una comprobación de validez en todos los archivos especificados y ubicaciones de bloques antes de realizar la operación de liberación. No se espera que la aplicación proporcione esta información. Cuando se libera un bloque de memoria, el administrador del montón de depuración comprueba automáticamente la integridad de los búferes situados a cada lado de la parte del usuario y emite un informe de error en caso de sobrescritura. Si el **_CRTDBG_DELAY_FREE_MEM_DF** campo de bits de la [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) marca está establecida, el bloque liberado se rellena con el valor 0xDD, recibe el **_FREE_BLOCK** tipo, de bloque y se mantiene en la lista del montón vinculada de bloques de memoria.

Si se produce un error al liberar memoria, **errno** se configura con información del sistema operativo de la naturaleza del error. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre la asignación de tipos de bloque y cómo se usan, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, consulte [Versiones de depuración de las funciones de asignación del montón](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_free_dbg**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Para obtener un ejemplo de cómo usar **_free_dbg**, consulte [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
