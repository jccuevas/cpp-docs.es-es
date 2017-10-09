---
title: _aligned_free_dbg | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _aligned_free_dbg
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
- _aligned_free_dbg
- aligned_free_dbg
dev_langs:
- C++
helpviewer_keywords:
- _aligned_free_dbg function
- aligned_free_dbg function
ms.assetid: eb0cb3c8-0992-4db8-bac3-65f1b8311ca6
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 724acaed1c99aa2507c33010e97f3f993e1b6de6
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="alignedfreedbg"></a>_aligned_free_dbg
Libera un bloque de memoria que se ha asignado con [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) o [_aligned_offset_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) (solo versión de depuración).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void _aligned_free_dbg(  
   void *memblock  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `memblock`  
 Puntero al bloque de memoria que se devolvió a las funciones `_aligned_malloc` o `_aligned_offset_malloc`.  
  
## <a name="remarks"></a>Comentarios  
 La función `_aligned_free_dbg` es una versión de depuración de la función [_aligned_free](../../c-runtime-library/reference/aligned-free.md). Si no se define [_DEBUG](../../c-runtime-library/debug.md), cada llamada a `_aligned_free_dbg` se reduce a una llamada a `_aligned_free`. Ambos `_aligned_free` y `_aligned_free_dbg` liberar un bloque de memoria del montón base, pero `_aligned_free_dbg` admite una característica de depuración: bloquea la posibilidad de mantener liberados en la lista del montón vinculada para simular condiciones de memoria insuficiente.  
  
 `_aligned_free_dbg` realiza una comprobación de validez en todos los archivos especificados y las ubicaciones de bloques antes de realizar la operación de liberación. No se espera que la aplicación proporcione esta información. Cuando se libera un bloque de memoria, el administrador del montón de depuración comprueba automáticamente la integridad de los búferes situados a cada lado de la parte del usuario y emite un informe de error en caso de sobrescritura. Si se establece el campo de bits `_CRTDBG_DELAY_FREE_MEM_DF` de la marca [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md), el bloque liberado se rellena con el valor 0xDD, se asigna el tipo de bloque `_FREE_BLOCK` y se mantiene en la lista vinculada de bloques de memoria del montón.  
  
 Si se produce un error al liberar memoria, en `errno` se muestra información sobre la naturaleza del error proporcionada por el sistema operativo. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre la asignación de tipos de bloque y cómo se usan, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, consulte [Versiones de depuración de las funciones de asignación del montón](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_aligned_free_dbg`|\<crtdbg.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="see-also"></a>Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)
