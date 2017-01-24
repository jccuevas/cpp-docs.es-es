---
title: "_aligned_offset_recalloc_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_aligned_offset_recalloc_dbg"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "aligned_offset_recalloc_dbg"
  - "_aligned_offset_recalloc_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_aligned_offset_recalloc_dbg (función)"
  - "aligned_offset_recalloc_dbg (función)"
ms.assetid: 7ab719c3-77e0-4d2e-934f-01529d062fbf
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _aligned_offset_recalloc_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cambia el tamaño de un bloque de memoria que se asignó con [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md) o [\_aligned\_offset\_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) e inicializa la memoria a 0 \(solo versión de depuración\).  
  
## Sintaxis  
  
```  
void * _aligned_offset_recalloc_dbg(    void *memblock,     size_t num,     size_t size,     size_t alignment,    size_t offset,    const char *filename,    int linenumber );  
```  
  
#### Parámetros  
 \[in\] `memblock`  
 Puntero de bloque de memoria actual.  
  
 \[in\] `num`  
 Número de elementos.  
  
 \[in\] `size`  
 Longitud en bytes de cada elemento.  
  
 \[in\] `alignment`  
 Valor de la alineación, que debe ser un entero potencia de 2.  
  
 \[in\] `offset`  
 Desplazamiento en la asignación de memoria para imponer la alineación.  
  
 \[in\] `filename`  
 Puntero al nombre del archivo de código fuente que solicitó la operación `realloc` o valor NULL.  
  
 \[in\] `linenumber`  
 Número de línea del archivo de código fuente en la que se solicitó la operación `realloc` o valor NULL.  
  
## Valor devuelto  
 `_aligned_offset_recalloc_dbg` devuelve un puntero void al bloque de memoria reasignado \(y, probablemente, trasladado\).  El valor devuelto es `NULL` si el tamaño es cero y el argumento de búfer no es `NULL`, o si no hay memoria suficiente para expandir el bloque al tamaño en cuestión.  En el primer caso, se libera el bloque original.  En el segundo, el bloque original permanece inalterado.  El valor devuelto apunta a un espacio de almacenamiento confirmado como correctamente alineado para almacenar cualquier tipo de objeto.  Para obtener un puntero a un tipo distinto a void, use una conversión de tipo en el valor devuelto.  
  
## Comentarios  
 `_aligned_offset_realloc_dbg` es una versión de depuración de la función [\_aligned\_offset\_recalloc](../../c-runtime-library/reference/aligned-offset-recalloc.md).  Si [\_DEBUG](../../c-runtime-library/debug.md) no se define, cada llamada a `_aligned_offset_recalloc_dbg` se reduce a una llamada a \_`aligned_offset_recalloc`.  \_`aligned_offset_recalloc` y `_aligned_offset_recalloc_dbg` reasignan los bloques de memoria del montón base, pero `_aligned_offset_recalloc_dbg` ofrece varias características de depuración: búferes situados a cada lado de la parte del usuario del bloque en el que se va a comprobar si hay pérdidas, un parámetro de tipo de bloque para realizar el seguimiento de tipos de asignación concretos e información sobre `filename`\/`linenumber` para conocer el origen de las solicitudes de asignación.  
  
 `_aligned_offset_realloc_dbg` reasigna el bloque de memoria especificado con un poco más de espacio que el `newSize` solicitado.  `newSize` podría ser mayor o menor que el tamaño del bloque de memoria asignado originalmente.  El administrador del montón de depuración usa el espacio adicional para vincular los bloques de memoria de depuración, y para proporcionar a la aplicación información de encabezado de depuración y sobrescribir los búferes.  La reasignación podría hacer que el bloque de memoria original se ponga en una ubicación distinta del montón y cambiar el tamaño del bloque de memoria.  Si se mueve el bloque de memoria, el contenido del bloque original se sobrescribe.  
  
 Esta función establece `errno` en `ENOMEM` si se produce un error en la asignación de memoria o si el tamaño solicitado \(`num` \* `size`\) es mayor que `_HEAP_MAXREQ`.  Para obtener más información sobre `errno`, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  Además, `_aligned_offset_recalloc_dbg` valida sus parámetros.  Si `alignment` no es una potencia de 2 o `offset` es mayor o igual que el tamaño solicitado y distinto de cero, esta función invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función devuelve `NULL` y establece `errno` en `EINVAL`.  
  
 Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [Detalles del montón de depuración de CRT](../Topic/CRT%20Debug%20Heap%20Details.md).  Para más información sobre los tipos de bloques de asignación y su uso, vea [Tipos de bloques en el montón de depuración](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap).  Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, vea [Versiones de depuración de las funciones de asignación del montón](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_aligned_offset_recalloc_dbg`|\<malloc.h\>|  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Alineación de datos](../../c-runtime-library/data-alignment.md)