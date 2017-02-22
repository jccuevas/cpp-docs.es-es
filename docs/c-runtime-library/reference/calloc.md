---
title: "calloc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "calloc"
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
  - "calloc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "asignación de memoria, matrices"
  - "calloc (función)"
ms.assetid: 17bb79a1-98cf-4096-90cb-1f9365cd6829
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# calloc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Asigna una matriz en memoria con elementos inicializado a 0.  
  
## Sintaxis  
  
```  
void *calloc(   
   size_t num,  
   size_t size   
);  
```  
  
#### Parámetros  
 `num`  
 Número de elementos.  
  
 `size`  
 Longitud en bytes de cada elemento.  
  
## Valor devuelto  
 `calloc` devuelve un puntero al espacio asignado.  El espacio de almacenamiento designado por el valor devuelto se garantiza alinearse convenientemente para el almacenamiento de cualquier tipo de objeto.  Para obtener un puntero a un tipo distinto de `void`, utilice una conversión de tipo del valor devuelto.  
  
## Comentarios  
 La función de `calloc` asigna espacio de almacenamiento para una matriz de elementos de `num` , cada uno de los bytes de `size` de longitud.  Cada elemento se inicializa en 0.  
  
 `calloc` establece `errno` en `ENOMEM` si se produce un error al asignar una memoria o si la cantidad de memoria solicitada supera `_HEAP_MAXREQ`.  Para obtener información sobre estos y otros códigos de error, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 llamadas `malloc` de`calloc` para usar la función de C\+\+ [\_set\_new\_mode](../../c-runtime-library/reference/set-new-mode.md) para establecer el nuevo modo de controlador.  El nuevo modo de controlador indica si, en caso de error, `malloc` debe llamar a la nueva rutina de controlador como se establece por [\_set\_new\_handler](../../c-runtime-library/reference/set-new-handler.md).  De forma predeterminada, `malloc` no llama a la nueva rutina del controlador si no se puede asignar memoria.  Puede invalidar este comportamiento predeterminado para que, cuando `calloc` no puede asignar memoria, `malloc` llama a la nueva rutina de controlador de la misma manera que hace el operador `new` cuando produce errores por la misma razón.  Para reemplazar el valor predeterminado, llame  
  
```  
_set_new_mode(1)  
```  
  
 al principio del programa, o vincularlo con NEWMODE.OBJ \(vea [Opciones de vínculo](../../c-runtime-library/link-options.md)\).  
  
 Cuando la aplicación se vincula con una versión de depuración de las bibliotecas en tiempo de ejecución de C, `calloc` resuelve a [\_calloc\_dbg](../../c-runtime-library/reference/calloc-dbg.md).  Para obtener más información sobre cómo la pila se administra durante el proceso de depuración, vea [El montón de depuración de CRT](../Topic/CRT%20Debug%20Heap%20Details.md).  
  
 `calloc` es `__declspec(noalias)` marcado y `__declspec(restrict)`, lo que significa que la función está garantizada para no modificar variables globales, y que el puntero devuelto no es con alias.  Para obtener más información, vea [noalias](../../cpp/noalias.md) y [limitado](../../cpp/restrict.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`calloc`|\<stdlib.h\> y \<malloc.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_calloc.c  
// This program uses calloc to allocate space for  
// 40 long integers. It initializes each element to zero.  
  
#include <stdio.h>  
#include <malloc.h>  
  
int main( void )  
{  
   long *buffer;  
  
   buffer = (long *)calloc( 40, sizeof( long ) );  
   if( buffer != NULL )  
      printf( "Allocated 40 long integers\n" );  
   else  
      printf( "Can't allocate memory\n" );  
   free( buffer );  
}  
```  
  
  **Asignado 40 enteros largos**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)