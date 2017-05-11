---
title: _aligned_offset_recalloc_dbg | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _aligned_offset_recalloc_dbg
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
- aligned_offset_recalloc_dbg
- _aligned_offset_recalloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- aligned_offset_recalloc_dbg function
- _aligned_offset_recalloc_dbg function
ms.assetid: 7ab719c3-77e0-4d2e-934f-01529d062fbf
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 7c65c73075c282f3a1b0dac83692c0adfe527c58
ms.contentlocale: es-es
ms.lasthandoff: 04/04/2017

---
# <a name="alignedoffsetrecallocdbg"></a>_aligned_offset_recalloc_dbg
Cambia el tamaño de un bloque de memoria que se ha asignado con [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) o [_aligned_offset_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) e inicializa la memoria a 0 (solo versión de depuración).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void * _aligned_offset_recalloc_dbg(  
   void *memblock,   
   size_t num,   
   size_t size,   
   size_t alignment,  
   size_t offset,  
   const char *filename,  
   int linenumber  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `memblock`  
 Puntero de bloque de memoria actual.  
  
 [in] `num`  
 Número de elementos.  
  
 [in] `size`  
 Longitud en bytes de cada elemento.  
  
 [in] `alignment`  
 Valor de la alineación, que debe ser un entero potencia de 2.  
  
 [in] `offset`  
 Desplazamiento en la asignación de memoria para imponer la alineación.  
  
 [in] `filename`  
 Puntero al nombre del archivo de código fuente que solicitó la operación `realloc` o valor NULL.  
  
 [in] `linenumber`  
 Número de línea del archivo de código fuente en la que se solicitó la operación `realloc` o valor NULL.  
  
## <a name="return-value"></a>Valor devuelto  
 `_aligned_offset_recalloc_dbg` devuelve un puntero void al bloque de memoria reasignado (y, probablemente, trasladado). El valor devuelto es `NULL` si el tamaño es cero y el argumento de búfer no es `NULL`, o si no hay memoria suficiente para expandir el bloque al tamaño en cuestión. En el primer caso, se libera el bloque original. En el segundo, el bloque original permanece inalterado. El valor devuelto apunta a un espacio de almacenamiento confirmado como correctamente alineado para almacenar cualquier tipo de objeto. Para obtener un puntero a un tipo distinto a void, use una conversión de tipo en el valor devuelto.  
  
## <a name="remarks"></a>Comentarios  
 La función `_aligned_offset_realloc_dbg` es una versión de depuración de la función [_aligned_offset_recalloc](../../c-runtime-library/reference/aligned-offset-recalloc.md). Si no se define [_DEBUG](../../c-runtime-library/debug.md), cada llamada a `_aligned_offset_recalloc_dbg` se reduce a una llamada a `_aligned_offset_recalloc`. `_aligned_offset_recalloc` y `_aligned_offset_recalloc_dbg` reasignan un bloque de memoria del montón base, pero `_aligned_offset_recalloc_dbg` admite varias características de depuración: búferes situados a cada lado de la parte del usuario del bloque en el que se va a comprobar si hay pérdidas, un parámetro de tipo de bloque para realizar el seguimiento de tipos de asignación concretos, e información sobre `filename`/`linenumber` para determinar el origen de las solicitudes de asignación.  
  
 `_aligned_offset_realloc_dbg` reasigna el bloque de memoria especificado con un poco más de espacio que el `newSize` solicitado. `newSize` podría ser mayor o menor que el tamaño del bloque de memoria asignado originalmente. El administrador del montón de depuración usa el espacio adicional para vincular los bloques de memoria de depuración, y para proporcionar a la aplicación información de encabezado de depuración y sobrescribir los búferes. La reasignación podría hacer que el bloque de memoria original se ponga en una ubicación distinta del montón y cambiar el tamaño del bloque de memoria. Si se mueve el bloque de memoria, el contenido del bloque original se sobrescribe.  
  
 Esta función establece `errno` en `ENOMEM` si se produce un error en la asignación de memoria o si el tamaño solicitado (`num` * `size`) es mayor que `_HEAP_MAXREQ`. Para obtener más información sobre `errno`, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Además, `_aligned_offset_recalloc_dbg` valida sus parámetros. Si `alignment` no es una potencia de 2 o `offset` es mayor o igual que el tamaño solicitado y distinto de cero, esta función invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve `NULL` y establece `errno` en `EINVAL`.  
  
 Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre la asignación de tipos de bloque y cómo se usan, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, consulte [Versiones de depuración de las funciones de asignación del montón](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_aligned_offset_recalloc_dbg`|\<malloc.h>|  
  
## <a name="see-also"></a>Vea también  
 [Alineación de datos](../../c-runtime-library/data-alignment.md)
