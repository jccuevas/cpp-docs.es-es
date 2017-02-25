---
title: "_aligned_malloc_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_aligned_malloc_dbg"
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
  - "_aligned_malloc_dbg"
  - "aligned_malloc_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_aligned_malloc_dbg (función)"
  - "aligned_malloc_dbg (función)"
ms.assetid: fb0429c3-685d-4826-9075-2515c5bdc5c6
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# _aligned_malloc_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Asigna memoria en un límite de alineación especificado con espacio adicional para un encabezado de depuración y búferes sobrescritos \(solo versión de depuración\).  
  
## Sintaxis  
  
```  
void * _aligned_malloc_dbg(     size_t size,      size_t alignment,    const char *filename,    int linenumber  );  
```  
  
#### Parámetros  
 \[in\] `size`  
 Tamaño de la asignación de memoria solicitada.  
  
 \[in\] `alignment`  
 Valor de la alineación, que debe ser un entero potencia de 2.  
  
 \[in\] `filename`  
 Puntero al nombre del archivo de código fuente que solicitó la operación de asignación o valor NULL.  
  
 \[in\] `linenumber`  
 Número de línea del archivo de código fuente en la que se solicitó la operación de asignación o valor NULL.  
  
## Valor devuelto  
 Puntero al bloque de memoria que se asignó o `NULL` si se produjo un error en la operación.  
  
## Comentarios  
 `_aligned_malloc_dbg` es una versión de depuración de la función [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md).  Si no se define [\_DEBUG](../../c-runtime-library/debug.md), cada llamada a `_aligned_malloc_dbg` se reduce a una llamada a `_aligned_malloc`.  `_aligned_malloc` y `_aligned_malloc_dbg` asignan un bloque de memoria del montón base, pero `_aligned_malloc_dbg` ofrece varias características de depuración: búferes situados a cada lado de la parte del usuario del bloque en el que se va a comprobar si hay pérdidas e información sobre `filename`\/`linenumber` para conocer el origen de las solicitudes de asignación.  
  
 `_aligned_malloc_dbg` asigna el bloque de memoria con un poco más de espacio que el `size` solicitado.  El administrador del montón de depuración usa el espacio adicional para vincular los bloques de memoria de depuración, y para proporcionar a la aplicación información de encabezado de depuración y sobrescribir los búferes.  Cuando se asigna el bloque, la parte del usuario de bloque se rellena con el valor 0xCD y cada uno de los búferes sobrescritos se rellena con 0xFD.  
  
 `_aligned_malloc_dbg` establece `errno` en `ENOMEM` si se produce un error de asignación de memoria o si la cantidad de memoria necesaria \(incluida la sobrecarga ya mencionada\) es mayor que `_HEAP_MAXREQ`.  Para obtener más información sobre este y otros códigos de error, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  Además, `_aligned_malloc_dbg` valida sus parámetros.  Si `alignment` no es una potencia de 2 o `size`, esta función invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función devuelve `NULL` y establece `errno` en `EINVAL`.  
  
 Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [Detalles del montón de depuración de CRT](../Topic/CRT%20Debug%20Heap%20Details.md).  Para más información sobre los tipos de bloques de asignación y su uso, vea [Tipos de bloques en el montón de depuración](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap).  Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, vea [Versiones de depuración de las funciones de asignación del montón](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_aligned_malloc_dbg`|\<crtdbg.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Solo las versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)