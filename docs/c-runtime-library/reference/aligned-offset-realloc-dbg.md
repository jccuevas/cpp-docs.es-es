---
title: _aligned_offset_realloc_dbg | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _aligned_offset_realloc_dbg
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
- aligned_offset_realloc_dbg
- _aligned_offset_realloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- aligned_offset_realloc_dbg function
- _aligned_offset_realloc_dbg function
ms.assetid: 64e30a12-887e-453b-aea8-aed793fca9d8
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 139046ad9114971b2085be02391b8fd2362a4749
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="alignedoffsetreallocdbg"></a>_aligned_offset_realloc_dbg
Cambia el tamaño de un bloque de memoria que se ha asignado con [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) o [_aligned_offset_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) (solo versión de depuración).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void * _aligned_offset_realloc_dbg(  
   void *memblock,   
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
  
 [in] `size`  
 Tamaño de la asignación de memoria.  
  
 [in] `alignment`  
 Valor de la alineación, que debe ser un entero potencia de 2.  
  
 [in] `offset`  
 Desplazamiento en la asignación de memoria para imponer la alineación.  
  
 [in] `filename`  
 Puntero al nombre del archivo de código fuente que solicitó la operación `aligned_offset_realloc` o valor NULL.  
  
 [in] `linenumber`  
 Número de línea del archivo de código fuente en la que se solicitó la operación `aligned_offset_realloc` o valor NULL.  
  
## <a name="return-value"></a>Valor devuelto  
 `_aligned_offset_realloc_dbg` devuelve un puntero void al bloque de memoria reasignado (y, probablemente, trasladado). El valor devuelto es `NULL` si el tamaño es cero y el argumento de búfer no es `NULL`, o si no hay memoria suficiente para expandir el bloque al tamaño en cuestión. En el primer caso, se libera el bloque original. En el segundo, el bloque original permanece inalterado. El valor devuelto apunta a un espacio de almacenamiento confirmado como correctamente alineado para almacenar cualquier tipo de objeto. Para obtener un puntero a un tipo distinto a void, use una conversión de tipo en el valor devuelto.  
  
## <a name="remarks"></a>Comentarios  
 La función `_aligned_offset_realloc_dbg` es una versión de depuración de la función [_aligned_offset_realloc](../../c-runtime-library/reference/aligned-offset-realloc.md). Si no se define [_DEBUG](../../c-runtime-library/debug.md), cada llamada a `_aligned_offset_realloc_dbg` se reduce a una llamada a `_aligned_offset_realloc`. `_aligned_offset_realloc` y `_aligned_offset_realloc_dbg` reasignan un bloque de memoria del montón base, pero `_aligned_offset_realloc_dbg` admite varias características de depuración: búferes situados a cada lado de la parte del usuario del bloque en el que se va a comprobar si hay pérdidas, un parámetro de tipo de bloque para realizar el seguimiento de tipos de asignación concretos, e información sobre `filename`/`linenumber` para determinar el origen de las solicitudes de asignación.  
  
 Al igual que [_aligned_offset_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md), `_aligned_offset_realloc_dbg` permite alinear una estructura en un desplazamiento dentro de la estructura.  
  
 `_realloc_dbg` reasigna el bloque de memoria especificado con un poco más de espacio que el `newSize` solicitado. `newSize` podría ser mayor o menor que el tamaño del bloque de memoria asignado originalmente. El administrador del montón de depuración usa el espacio adicional para vincular los bloques de memoria de depuración, y para proporcionar a la aplicación información de encabezado de depuración y sobrescribir los búferes. La reasignación podría hacer que el bloque de memoria original se ponga en una ubicación distinta del montón y cambiar el tamaño del bloque de memoria. Si se mueve el bloque de memoria, el contenido del bloque original se sobrescribe.  
  
 Esta función establece `errno` en `ENOMEM` si se produce un error en la asignación de memoria o si el tamaño solicitado es mayor que `_HEAP_MAXREQ`. Para obtener más información sobre `errno`, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Además, `_aligned_offset_realloc_dbg` valida sus parámetros. Si `alignment` no es una potencia de 2, o `offset` es mayor o igual que `size` y distinto de cero, esta función invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve `NULL` y establece `errno` en `EINVAL`.  
  
 Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre la asignación de tipos de bloque y cómo se usan, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, consulte [Versiones de depuración de las funciones de asignación del montón](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_aligned_offset_realloc_dbg`|\<crtdbg.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)
