---
title: "_recalloc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_recalloc"
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
  - "_recalloc"
  - "recalloc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_recalloc (función)"
  - "recalloc (función)"
ms.assetid: 1db8305a-3f03-418c-8844-bf9149f63046
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# _recalloc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Combinación de `realloc` y `calloc`.  Reasigna una matriz en memoria y se inicializa sus elementos en 0.  
  
## Sintaxis  
  
```  
void *_recalloc(   
   void *memblock  
   size_t num,  
   size_t size   
);  
```  
  
#### Parámetros  
 `memblock`  
 Puntero al bloque de memoria previamente asignado.  
  
 `num`  
 Número de elementos.  
  
 `size`  
 Longitud en bytes de cada elemento.  
  
## Valor devuelto  
 `_recalloc` devuelve un puntero de `void` \(y posiblemente desplazado\) al bloque de memoria reasignado.  
  
 Si no hay suficiente memoria disponible para expandir el bloque al tamaño especificado, el bloque original permanece sin cambios, y se devuelve `NULL` .  
  
 Si el tamaño solicitado es cero, el bloque indicada por `memblock` se libera; el valor devuelto es `NULL`, y `memblock` se permite informar sobre un bloque liberado.  
  
 Los puntos del valor devuelto a un espacio de almacenamiento que se garantiza alinearse convenientemente para el almacenamiento de cualquier tipo de objeto.  Para obtener un puntero a un tipo distinto de `void`, utilice una conversión de tipo del valor devuelto.  
  
## Comentarios  
 Los cambios de función de`recalloc` de \_el tamaño de un bloque de memoria asignado.  Los puntos del argumento de `memblock` al principio del bloque de memoria.  Si `memblock` es `NULL`, \_`recalloc` se comporta de la misma manera que [calloc](../../c-runtime-library/reference/calloc.md) y asigna un nuevo bloque de `num` \* bytes de `size` .  Cada elemento se inicializa en 0.  Si `memblock` no es `NULL`, debe ser un puntero devuelto por una llamada anterior a `calloc`, a [malloc](../../c-runtime-library/reference/malloc.md), o a [realloc](../../c-runtime-library/reference/realloc.md).  
  
 Dado que el nuevo bloque puede estar en una nueva ubicación de memoria, no garantiza que el puntero devuelto por \_`recalloc` para ser el puntero pasado a través del argumento de `memblock` .  
  
 `_recalloc` establece `errno` a `ENOMEM` si se produce un error en la asignación de memoria o si la cantidad de memoria solicitada supera `_HEAP_MAXREQ`.  Para obtener información sobre estos y otros códigos de error, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 llamadas `realloc` de`recalloc` para usar la función de C\+\+ [\_set\_new\_mode](../../c-runtime-library/reference/set-new-mode.md) para establecer el nuevo modo de controlador.  El nuevo modo de controlador indica si, en caso de error, `realloc` debe llamar a la nueva rutina de controlador como se establece por [\_set\_new\_handler](../../c-runtime-library/reference/set-new-handler.md).  De forma predeterminada, `realloc` no llama a la nueva rutina del controlador si no se puede asignar memoria.  Puede invalidar este comportamiento predeterminado para que, cuando \_`recalloc` no puede para asignar memoria, `realloc` llame a la nueva rutina del controlador de la misma manera que el operador de `new` cuando falla por la misma razón.  Para reemplazar el valor predeterminado, llame  
  
```  
_set_new_mode(1)  
```  
  
 al principio del programa, o vínculo con NEWMODE.OBJ.  
  
 Cuando la aplicación se vincula con una versión de depuración de las bibliotecas en tiempo de ejecución de C, \_`recalloc` resuelve a [\_recalloc\_dbg](../../c-runtime-library/reference/recalloc-dbg.md).  Para obtener más información sobre cómo la pila se administra durante el proceso de depuración, vea [El montón de depuración de CRT](../Topic/CRT%20Debug%20Heap%20Details.md).  
  
 `_recalloc` es `__declspec(noalias)` marcado y `__declspec(restrict)`, lo que significa que la función está garantizada para no modificar variables globales, y que el puntero devuelto no es con alias.  Para obtener más información, vea [noalias](../../cpp/noalias.md) y [limitado](../../cpp/restrict.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_recalloc`|\<stdlib.h\> y \<malloc.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)   
 [\_recalloc\_dbg](../../c-runtime-library/reference/recalloc-dbg.md)   
 [\_aligned\_recalloc](../../c-runtime-library/reference/aligned-recalloc.md)   
 [\_aligned\_offset\_recalloc](../../c-runtime-library/reference/aligned-offset-recalloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [Opciones de vínculo](../../c-runtime-library/link-options.md)