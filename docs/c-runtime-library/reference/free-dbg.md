---
title: _free_dbg | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _free_dbg
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
dev_langs: C++
helpviewer_keywords:
- memory blocks, deallocating
- freeing memory
- _free_dbg function
- free_dbg function
ms.assetid: fc5e8299-616d-48a0-b979-e037117278c6
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fccae4629bc4c1c9b6af71f254c28311210ec0e9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="freedbg"></a>_free_dbg
Libera un bloque de memoria del montón (solo versión de depuración).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void _free_dbg(   
   void *userData,  
   int blockType   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `userData`  
 Puntero al bloque de memoria asignado que se va a liberar.  
  
 `blockType`  
 Tipo de bloque de memoria asignado que se va a liberar: `_CLIENT_BLOCK`, `_NORMAL_BLOCK` o `_IGNORE_BLOCK`.  
  
## <a name="remarks"></a>Comentarios  
 La función `_free_dbg` es una versión de depuración de la función [free](../../c-runtime-library/reference/free.md). Si no se define [_DEBUG](../../c-runtime-library/debug.md), cada llamada a `_free_dbg` se reduce a una llamada a `free`. `free` y `_free_dbg` liberan un bloque de memoria del montón base, pero `_free_dbg` incluye dos características de depuración: la posibilidad de mantener los bloques liberados en la lista vinculada del montón para simular condiciones de memoria insuficiente y un parámetro de tipo de bloque para liberar tipos de asignación específicos.  
  
 `_free_dbg` realiza una comprobación de validez en todos los archivos especificados y las ubicaciones de bloques antes de realizar la operación de liberación. No se espera que la aplicación proporcione esta información. Cuando se libera un bloque de memoria, el administrador del montón de depuración comprueba automáticamente la integridad de los búferes situados a cada lado de la parte del usuario y emite un informe de error en caso de sobrescritura. Si se establece el campo de bits `_CRTDBG_DELAY_FREE_MEM_DF` de la marca [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md), el bloque liberado se rellena con el valor 0xDD, se asigna el tipo de bloque `_FREE_BLOCK` y se mantiene en la lista vinculada de bloques de memoria del montón.  
  
 Si se produce un error al liberar memoria, en `errno` se muestra información sobre la naturaleza del error proporcionada por el sistema operativo. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre la asignación de tipos de bloque y cómo se usan, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, consulte [Versiones de depuración de las funciones de asignación del montón](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_free_dbg`|\<crtdbg.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
 Para obtener un ejemplo de cómo usar `_free_dbg`, consulte [crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167).  
  
## <a name="see-also"></a>Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md)