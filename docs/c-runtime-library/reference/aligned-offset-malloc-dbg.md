---
title: "_aligned_offset_malloc_dbg | Microsoft Docs"
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
  - "_aligned_offset_malloc_dbg"
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
  - "_aligned_offset_malloc_dbg"
  - "aligned_offset_malloc_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_aligned_offset_malloc_dbg (función)"
  - "aligned_offset_malloc_dbg (función)"
ms.assetid: 6c242307-c59e-4d63-aae5-d8cbec8e021c
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _aligned_offset_malloc_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Asigna memoria en un límite de alineación especificado \(solo versión de depuración\).  
  
## Sintaxis  
  
```  
void * _aligned_offset_malloc_dbg(  
   size_t size,   
   size_t alignment,   
   size_t offset,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### Parámetros  
 \[in\] `size`  
 Tamaño de la asignación de memoria solicitada.  
  
 \[in\] `alignment`  
 Valor de la alineación, que debe ser un entero potencia de 2.  
  
 \[in\] `offset`  
 Desplazamiento en la asignación de memoria para imponer la alineación.  
  
 \[in\] `filename`  
 Puntero al nombre del archivo de código fuente que solicitó la operación de asignación o valor NULL.  
  
 \[in\] `linenumber`  
 Número de línea del archivo de código fuente en la que se solicitó la operación de asignación o valor NULL.  
  
## Valor devuelto  
 Puntero al bloque de memoria que se asignó o `NULL`  si se produjo un error en la operación.  
  
## Comentarios  
 `_aligned_offset_malloc_dbg` es una versión de depuración de la función [\_aligned\_offset\_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md).  Si no se define [\_DEBUG](../../c-runtime-library/debug.md), cada llamada a `_aligned_offset_malloc_dbg` se reduce a una llamada a `_aligned_offset_malloc`.  `_aligned_offset_malloc` y `_aligned_offset_malloc_dbg` asignan un bloque de memoria del montón base, pero `_aligned_offset_malloc_dbg` proporciona varias características de depuración: búferes situados a cada lado de la parte del usuario del bloque en el que se va a comprobar si hay pérdidas, un parámetro de tipo de bloque para realizar el seguimiento de tipos de asignación concretos, e información sobre `filename` o `linenumber` para determinar el origen de las solicitudes de asignación.  
  
 `_aligned_offset_malloc_dbg` asigna el bloque de memoria con un poco más de espacio que el `size` solicitado.  El administrador del montón de depuración usa el espacio adicional para vincular los bloques de memoria de depuración, y para proporcionar a la aplicación información de encabezado de depuración y sobrescribir los búferes.  Cuando se asigna el bloque, la parte del usuario de bloque se rellena con el valor 0xCD y cada uno de los búferes sobrescritos se rellena con 0xFD.  
  
 `_aligned_offset_malloc_dbg` es útil en situaciones en las que la alineación se necesita en un elemento anidado, por ejemplo si se necesitara la alineación en una clase anidada.  
  
 `_aligned_offset_malloc_dbg` se basa en `malloc`. Para obtener más información, vea [malloc](../../c-runtime-library/reference/malloc.md).  
  
 Esta función establece `errno` en `ENOMEM` si se produce un error en la asignación de memoria o si el tamaño solicitado es mayor que `_HEAP_MAXREQ`.  Para obtener más información sobre `errno`, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  Además, `_aligned_offset_malloc` valida sus parámetros.  Si `alignment` no es una potencia de 2, o `offset` es mayor o igual que `size` y distinto de cero, esta función invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función devuelve `NULL` y establece `errno` en `EINVAL`.  
  
 Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [Detalles del montón de depuración de CRT](../Topic/CRT%20Debug%20Heap%20Details.md).  
  
 Para obtener información sobre la asignación de tipos de bloque y cómo se usan, vea [Tipos de bloques en el montón de depuración](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_aligned_offset_malloc_dbg`|\<crtdbg.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Solo las versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)