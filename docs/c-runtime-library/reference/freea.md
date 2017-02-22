---
title: "_freea | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_freea"
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
  - "freea"
  - "_freea"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_freea (función)"
  - "freea (función)"
  - "desasignación de memoria"
ms.assetid: dcd30584-dd9d-443b-8c4c-13237a1cecac
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# _freea
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Desasigna o libera un bloque de memoria.  
  
## Sintaxis  
  
```  
void _freea(   
   void *memblock   
);  
```  
  
#### Parámetros  
 `memblock`  
 Bloque de memoria previamente asignado se libere.  
  
## Valor devuelto  
 Ninguno.  
  
## Comentarios  
 La función de `_freea` desasigna un bloque de memoria \(`memblock`\) que fue asignado previamente por una llamada a [\_malloca](../../c-runtime-library/reference/malloca.md).  comprobaciones de`_freea` para ver si se asignó la memoria en la pila o el montón.  Si se asignó en la pila, `_freea` no hace nada.  Si se asignó en la pila, el número de bytes liberados es equivalente al número de bytes solicitados cuando el bloque fue asignado.  Si `memblock` es `NULL`, se omite el puntero y `_freea` inmediatamente devuelve.  Al intentar liberar un puntero no válido \(puntero a un bloque de memoria que no fue asignado por `_malloca`\) puede afectar a las solicitudes subsiguientes de asignación y producir errores.  
  
 \_`freea` llama `free` internamente si encuentra que memoria está asignada en el montón.  Si la memoria está en la pila o el montón está determinado por un marcador situado en memoria en la dirección inmediatamente antes de la memoria asignada.  
  
 Si se produce un error al liberar memoria, en `errno` se muestra información sobre la naturaleza del error proporcionada por el sistema operativo.  Para obtener más información, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Una vez liberado un bloque de memoria, [\_heapmin](../../c-runtime-library/reference/heapmin.md) minimiza la cantidad de memoria disponible en el montón uniéndose regiones no usadas y soltándola a éstos de nuevo al sistema operativo.  Memoria liberada que no se libera al sistema operativo se restaura el conjunto libre y está disponible para la asignación de nuevo.  
  
 Una llamada a `_freea` debe para todas las llamadas a `_malloca`.  También es un error para llamar a `_freea` dos veces en la misma.  Cuando la aplicación se vincula con una versión de depuración de las bibliotecas en tiempo de ejecución de C, especialmente con las características de [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md) habilitó definiendo `_CRTDBG_MAP_ALLOC`, resulta más fácil encontrar falta o llamadas duplicadas a `_freea`.  Para obtener más información sobre cómo la pila se administra durante el proceso de depuración, vea [El montón de depuración de CRT](../Topic/CRT%20Debug%20Heap%20Details.md).  
  
 `_freea` es `__declspec(noalias)`marcado, lo que significa que la función está garantizada para no modificar variables globales.  Para obtener más información, vea [noalias](../../cpp/noalias.md).  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`_freea`|\<stdlib.h\> y \<malloc.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Consulte el ejemplo de [\_malloca](../../c-runtime-library/reference/malloca.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)   
 [\_malloca](../../c-runtime-library/reference/malloca.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [\_free\_dbg](../../c-runtime-library/reference/free-dbg.md)   
 [\_heapmin](../../c-runtime-library/reference/heapmin.md)