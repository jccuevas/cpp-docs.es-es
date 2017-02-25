---
title: "realloc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "realloc"
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
  - "_brealloc"
  - "_nrealloc"
  - "realloc"
  - "_frealloc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_brealloc (función)"
  - "realloc (función)"
  - "nrealloc (función)"
  - "frealloc (función)"
  - "_nrealloc (función)"
  - "bloques de memoria, reasignar"
  - "memoria, reasignar"
  - "_frealloc (función)"
  - "reasignar bloques de memoria"
ms.assetid: 2b2239de-810b-4b11-9438-32ab0a244185
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# realloc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Reasigne bloques de memoria.  
  
## Sintaxis  
  
```  
void *realloc(  
   void *memblock,  
   size_t size   
);  
```  
  
#### Parámetros  
 `memblock`  
 Puntero al bloque de memoria previamente asignado.  
  
 `size`  
 Nuevo tamaño en bytes.  
  
## Valor devuelto  
 `realloc` devuelve un puntero de `void` \(y posiblemente desplazado\) al bloque de memoria reasignado.  
  
 Si no hay suficiente memoria disponible para expandir el bloque al tamaño especificado, el bloque original permanece sin cambios, y se devuelve `NULL` .  
  
 Si `size` es cero, el bloque indicada por `memblock` se libera; el valor devuelto es `NULL`, y `memblock` se permite informar sobre un bloque liberado.  
  
 Los puntos del valor devuelto a un espacio de almacenamiento que se garantiza alinearse convenientemente para el almacenamiento de cualquier tipo de objeto.  Para obtener un puntero a un tipo distinto de `void`, utilice una conversión de tipo del valor devuelto.  
  
## Comentarios  
 Los cambios de función de `realloc` el tamaño de un bloque de memoria asignado.  Los puntos del argumento de `memblock` al principio del bloque de memoria.  Si `memblock` es `NULL`, `realloc` se comporta de la misma manera que `malloc` y asigna un nuevo bloque de bytes de `size` .  Si `memblock` no es `NULL`, debe ser un puntero devuelto por una llamada anterior a `calloc`, a `malloc`, o a `realloc`.  
  
 El argumento de `size` da el nuevo tamaño de bloque, en bytes.  El contenido del bloque son sin cambios hasta el menor de los nuevo y antiguo tamaños, aunque el nuevo bloque puede estar en una ubicación diferente.  Dado que el nuevo bloque puede estar en una nueva ubicación de memoria, no garantiza que el puntero devuelto por `realloc` para ser el puntero pasado a través del argumento de `memblock` .  `realloc` no pone a cero memoria recién asignada en el caso de crecimiento del búfer.  
  
 `realloc` establece `errno` a `ENOMEM` si se produce un error en la asignación de memoria o si la cantidad de memoria solicitada supera `_HEAP_MAXREQ`.  Para obtener información sobre estos y otros códigos de error, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 llamadas`malloc`de`realloc`para usar la función de C\+\+ [\_set\_new\_mode](../../c-runtime-library/reference/set-new-mode.md) para establecer el nuevo modo de controlador.  El nuevo modo de controlador indica si, en caso de error, `malloc` debe llamar a la nueva rutina de controlador como se establece por [\_set\_new\_handler](../../c-runtime-library/reference/set-new-handler.md).  De forma predeterminada, `malloc` no llama a la nueva rutina del controlador si no se puede asignar memoria.  Puede invalidar este comportamiento predeterminado para que, cuando `realloc` no puede asignar memoria, `malloc` llama a la nueva rutina de controlador de la misma manera que hace el operador `new` cuando produce errores por la misma razón.  Para reemplazar el valor predeterminado, llame  
  
```  
_set_new_mode(1)  
```  
  
 temprano en unos programa, o vínculo con NEWMODE.OBJ \(vea [Opciones de vínculo](../../c-runtime-library/link-options.md)\).  
  
 Cuando la aplicación se vincula con una versión de depuración de las bibliotecas en tiempo de ejecución de C, `realloc` resuelve a [\_realloc\_dbg](../../c-runtime-library/reference/realloc-dbg.md).  Para obtener más información sobre cómo la pila se administra durante el proceso de depuración, vea [El montón de depuración de CRT](../Topic/CRT%20Debug%20Heap%20Details.md).  
  
 `realloc` es `__declspec(noalias)` marcado y `__declspec(restrict)`, lo que significa que la función está garantizada para no modificar variables globales, y que el puntero devuelto no es con alias.  Para obtener más información, vea [noalias](../../cpp/noalias.md) y [limitado](../../cpp/restrict.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`realloc`|\<stdlib.h\> y \<malloc.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_realloc.c  
// This program allocates a block of memory for  
// buffer and then uses _msize to display the size of that  
// block. Next, it uses realloc to expand the amount of  
// memory used by buffer and then calls _msize again to  
// display the new amount of memory allocated to buffer.  
  
#include <stdio.h>  
#include <malloc.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   long *buffer, *oldbuffer;  
   size_t size;  
  
   if( (buffer = (long *)malloc( 1000 * sizeof( long ) )) == NULL )  
      exit( 1 );  
  
   size = _msize( buffer );  
   printf_s( "Size of block after malloc of 1000 longs: %u\n", size );  
  
   // Reallocate and show new size:  
   oldbuffer = buffer;     // save pointer in case realloc fails  
   if( (buffer = realloc( buffer, size + (1000 * sizeof( long )) ))   
        ==  NULL )  
   {  
      free( oldbuffer );  // free original block  
      exit( 1 );  
   }  
   size = _msize( buffer );  
   printf_s( "Size of block after realloc of 1000 more longs: %u\n",   
            size );  
  
   free( buffer );  
   exit( 0 );  
}  
```  
  
  **El tamaño de bloque después de malloc de 1000 desee: 4000**  
**El tamaño de bloque después realloc de 1000 desea más: 8000**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)