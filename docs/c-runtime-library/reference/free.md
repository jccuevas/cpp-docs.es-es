---
title: "free | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "free"
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
  - "api-ms-win-crt-heap-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "free"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bloques de memoria, desasignar"
  - "free (función)"
ms.assetid: 74ded9cf-1863-432e-9306-327a42080bb8
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# free
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Desasigna o libera un bloque de memoria.  
  
## Sintaxis  
  
```  
void free(   
   void *memblock   
);  
```  
  
#### Parámetros  
 `memblock`  
 Bloque de memoria previamente asignado se libere.  
  
## Comentarios  
 La función de `free` desasigna un bloque de memoria \(`memblock`\) que fue asignado previamente por una llamada a `calloc`, a `malloc`, o a `realloc`.  El número de bytes liberados es equivalente al número de bytes solicitados cuando el bloque fue asignado \(o reasignado, en el caso de `realloc`\).  Si `memblock` es `NULL`, se omite el puntero y `free` inmediatamente devuelve.  Al intentar liberar un puntero no válido \(puntero a un bloque de memoria que no fue asignado por `calloc`, a `malloc`, o a `realloc`\) puede afectar a las solicitudes subsiguientes de asignación y producir errores.  
  
 Si se produce un error al liberar memoria, en `errno` se muestra información sobre la naturaleza del error proporcionada por el sistema operativo.  Para obtener más información, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Una vez liberado un bloque de memoria, [\_heapmin](../../c-runtime-library/reference/heapmin.md) minimiza la cantidad de memoria disponible en el montón uniéndose regiones no usadas y soltándola a éstos de nuevo al sistema operativo.  Memoria liberada que no se libera al sistema operativo se restaura el conjunto libre y está disponible para la asignación de nuevo.  
  
 Cuando la aplicación se vincula con una versión de depuración de las bibliotecas en tiempo de ejecución de C, `free` resuelve a [\_free\_dbg](../../c-runtime-library/reference/free-dbg.md).  Para obtener más información sobre cómo la pila se administra durante el proceso de depuración, vea [El montón de depuración de CRT](../Topic/CRT%20Debug%20Heap%20Details.md).  
  
 `free` es `__declspec(noalias)`marcado, lo que significa que la función está garantizada para no modificar variables globales.  Para obtener más información, vea [noalias](../../cpp/noalias.md).  
  
 Liberar memoria asignada con [\_malloca](../../c-runtime-library/reference/malloca.md), utilice [\_freea](../../c-runtime-library/reference/freea.md).  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`free`|\<stdlib.h\> y \<malloc.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Vea el ejemplo para [malloc](../../c-runtime-library/reference/malloc.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)   
 [\_alloca](../../c-runtime-library/reference/alloca.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [\_free\_dbg](../../c-runtime-library/reference/free-dbg.md)   
 [\_heapmin](../../c-runtime-library/reference/heapmin.md)   
 [\_freea](../../c-runtime-library/reference/freea.md)