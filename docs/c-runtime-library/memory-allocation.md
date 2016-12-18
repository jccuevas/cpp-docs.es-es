---
title: "Asignaci&#243;n de memoria | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.memory"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "asignación de memoria, rutinas"
  - "memoria, asignación"
  - "memoria, administrar"
ms.assetid: b4470556-a128-4782-9943-2ccf7a7d9979
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Asignaci&#243;n de memoria
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Use estas rutinas para asignar, liberar y reasignar memoria.  
  
### Rutinas de asignación de memoria  
  
|Rutina|Uso|Equivalente de .NET Framework|  
|------------|---------|-----------------------------------|  
|[\_alloca](../c-runtime-library/reference/alloca.md), [\_malloca](../c-runtime-library/reference/malloca.md)|Asignar memoria de una pila|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[calloc](../c-runtime-library/reference/calloc.md)|Asignar almacenamiento para la matriz, inicializando a 0 cada byte en el bloque asignado|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_calloc\_dbg](../c-runtime-library/reference/calloc-dbg.md)|Depurar la versión de `calloc`; disponible únicamente en las versiones de depuración de las bibliotecas en tiempo de ejecución|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[operator delete](../c-runtime-library/operator-delete-crt.md)|Liberar un bloque asignado|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[operator delete&#91;&#93;](../c-runtime-library/delete-operator-crt.md)|Liberar un bloque asignado|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_expand](../c-runtime-library/reference/expand.md)|Expandir o reducir un bloque de memoria sin moverlo|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_expand\_dbg](../c-runtime-library/reference/expand-dbg.md)|Depurar la versión de `_expand`; disponible únicamente en las versiones de depuración de las bibliotecas en tiempo de ejecución|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[free](../c-runtime-library/reference/free.md)|Liberar un bloque asignado|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_free\_dbg](../c-runtime-library/reference/free-dbg.md)|Depurar la versión de `free`; disponible únicamente en las versiones de depuración de las bibliotecas en tiempo de ejecución|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_freea](../c-runtime-library/reference/freea.md)|Liberar un bloque asignado de la pila|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_get\_heap\_handle](../c-runtime-library/reference/get-heap-handle.md)|Obtener identificador de Win32 en el montón de CRT.|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_heapadd](../c-runtime-library/heapadd.md)|Agregar memoria al montón|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_heapchk](../c-runtime-library/reference/heapchk.md)|Comprobar la coherencia del montón|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_heapmin](../c-runtime-library/reference/heapmin.md)|Liberar la memoria sin usar del montón|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_heapset](../c-runtime-library/heapset.md)|Rellenar las entradas de montón libres con el valor especificado|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_heapwalk](../c-runtime-library/reference/heapwalk.md)|Devolver información sobre cada entrada en el montón|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[malloc](../c-runtime-library/reference/malloc.md)|Asignar un bloque de memoria del montón|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_malloc\_dbg](../c-runtime-library/reference/malloc-dbg.md)|Depurar la versión de `malloc`; disponible únicamente en las versiones de depuración de las bibliotecas en tiempo de ejecución|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_msize](../c-runtime-library/reference/msize.md)|Devolver el tamaño del bloque asignado|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_msize\_dbg](../c-runtime-library/reference/msize-dbg.md)|Depurar la versión de `_msize`; disponible únicamente en las versiones de depuración de las bibliotecas en tiempo de ejecución|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[new](../c-runtime-library/operator-new-crt.md)|Asignar un bloque de memoria del montón|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[new&#91;&#93;](../c-runtime-library/new-operator-crt.md)|Asignar un bloque de memoria del montón|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_query\_new\_handler](../c-runtime-library/reference/query-new-handler.md)|Devolver la dirección de la nueva rutina de controlador actual, según lo establecido por `_set_new_handler`|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_query\_new\_mode](../c-runtime-library/reference/query-new-mode.md)|Devolver un entero que indique el nuevo modo de controlador establecido por `_set_new_mode`  para `malloc`|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[realloc](../c-runtime-library/reference/realloc.md)|Reasignar un nuevo tamaño al bloque|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_realloc\_dbg](../c-runtime-library/reference/realloc-dbg.md)|Depurar la versión de `realloc`; disponible únicamente en las versiones de depuración de las bibliotecas en tiempo de ejecución|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_set\_new\_handler](../c-runtime-library/reference/set-new-handler.md)|Habilitar el mecanismo de tratamiento de errores cuando el operador `new` no pueda asignar memoria y habilitar la compilación de bibliotecas de plantillas estándar \(STL\)|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_set\_new\_mode](../c-runtime-library/reference/set-new-mode.md)|Definir el nuevo modo de controlador para `malloc`|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
  
## Vea también  
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)