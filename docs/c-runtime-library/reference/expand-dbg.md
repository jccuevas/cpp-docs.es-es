---
title: "_expand_dbg | Microsoft Docs"
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
  - "_expand_dbg"
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
  - "expand_dbg"
  - "_expand_dbg"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "bloques de memoria, cambiar tamaño"
  - "expand_dbg (función)"
  - "_expand_dbg (función)"
ms.assetid: dc58c91f-72a8-48c6-b643-fe130fb6c1fd
caps.latest.revision: 18
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _expand_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cambia el tamaño de un bloque de memoria especificado en el montón, ya sea expandiendo o contrayendo el bloque \(solo versión de depuración\).  
  
## Sintaxis  
  
```  
void *_expand_dbg(   
   void *userData,  
   size_t newSize,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### Parámetros  
 `userData`  
 Puntero al bloque de memoria asignado previamente.  
  
 `newSize`  
 Nuevo tamaño solicitado para el bloque \(en bytes\).  
  
 `blockType`  
 Tipo solicitado para el bloque cuyo tamaño ha cambiado: `_CLIENT_BLOCK`  o `_NORMAL_BLOCK`.  
  
 `filename`  
 Puntero al nombre del archivo de código fuente que solicitó la operación de expansión, o `NULL`.  
  
 `linenumber`  
 Número de línea del archivo de código fuente en la que se solicitó la operación de expansión, o `NULL`.  
  
 Los parámetros `filename` y `linenumber` solo están disponibles cuando se ha llamado a `_expand_dbg` explícitamente o se ha definido la constante de preprocesador [\_CRTDBG\_MAP\_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md).  
  
## Valor devuelto  
 Cuando se ejecuta correctamente, `_expand_dbg` devuelve un puntero al bloque de memoria cuyo tamaño ha cambiado.  Dado que la memoria no se mueve, la dirección es la misma que la de userData.  Si se produce un error o el bloque no se puede expandir al tamaño solicitado, devuelve `NULL`.  Si se produce un error, se devuelve `errno` con información del sistema operativo sobre la naturaleza del error.  Para obtener más información sobre `errno`, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función `_expand_dbg` es una versión de depuración de la función \_[expand](../../c-runtime-library/reference/expand.md).  Si no se define [\_DEBUG](../../c-runtime-library/debug.md), cada llamada a `_expand_dbg` se reduce a una llamada a `_expand`.  `_expand`  y `_expand_dbg`  cambian el tamaño de un bloque de memoria del montón base, pero `_expand_dbg` admite varias características de depuración: búferes situados a cada lado de la parte del usuario del bloque en el que se va a comprobar si hay pérdidas, un parámetro de tipo de bloque para realizar el seguimiento de tipos de asignación concretos, e información sobre `filename` o `linenumber` para determinar el origen de las solicitudes de asignación.  
  
 `_expand_dbg` cambia el tamaño del bloque de memoria especificado con un poco más de espacio que el `newSize` solicitado.  `newSize` podría ser mayor o menor que el tamaño del bloque de memoria asignado originalmente.  El administrador del montón de depuración usa el espacio adicional para vincular los bloques de memoria de depuración, y para proporcionar a la aplicación información de encabezado de depuración y sobrescribir los búferes.  El cambio de tamaño es realiza expandiendo o contrayendo el bloque de memoria original.  `_expand_dbg` no mueve el bloque de memoria, algo que si hace la función [\_realloc\_dbg](../../c-runtime-library/reference/realloc-dbg.md).  
  
 Si `newSize` es mayor que el tamaño del bloque original, el bloque de memoria se expande.  Durante una extensión, si el bloque de memoria no se puede expandir para adaptarse al tamaño solicitado, se devuelve `NULL`.  Si `newSize` es menor que el tamaño del bloque original, el bloque de memoria se contrae hasta que tiene el nuevo tamaño.  
  
 Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [Detalles del montón de depuración de CRT](../Topic/CRT%20Debug%20Heap%20Details.md).  Para obtener información sobre la asignación de tipos de bloque y cómo se usan, vea [Tipos de bloques en el montón de depuración](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap).  Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, vea [Versiones de depuración de las funciones de asignación del montón](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md).  
  
 Esta función valida sus parámetros.  Si `memblock` es un puntero nulo, o si el tamaño es mayor que `_HEAP_MAXREQ`, esta función invoca un controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve `NULL`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_expand_dbg`|\<crtdbg.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Solo las versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_expand_dbg.c  
//  
// This program allocates a block of memory using _malloc_dbg  
// and then calls _msize_dbg to display the size of that block.  
// Next, it uses _expand_dbg to expand the amount of  
// memory used by the buffer and then calls _msize_dbg again to  
// display the new amount of memory allocated to the buffer.  
//  
  
#include <stdio.h>  
#include <malloc.h>  
#include <stdlib.h>  
#include <crtdbg.h>  
  
int main( void )  
{  
   long *buffer;  
   size_t size;  
  
   // Call _malloc_dbg to include the filename and line number  
   // of our allocation request in the header  
   buffer = (long *)_malloc_dbg( 40 * sizeof(long),  
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );  
   if( buffer == NULL )  
      exit( 1 );  
  
   // Get the size of the buffer by calling _msize_dbg  
   size = _msize_dbg( buffer, _NORMAL_BLOCK );  
   printf( "Size of block after _malloc_dbg of 40 longs: %u\n", size );  
  
   // Expand the buffer using _expand_dbg and show the new size  
   buffer = (long *)_expand_dbg( buffer, size + sizeof(long),  
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );  
  
   if( buffer == NULL )  
      exit( 1 );  
   size = _msize_dbg( buffer, _NORMAL_BLOCK );  
   printf( "Size of block after _expand_dbg of 1 more long: %u\n",  
           size );  
  
   free( buffer );  
   exit( 0 );  
}  
```  
  
  **Size of block after \_malloc\_dbg of 40 longs: 160**  
**Size of block after \_expand\_dbg of 1 more long: 164**   
## Comment  
 El resultado de este programa depende de la capacidad del equipo de expandir todas las secciones.  Si se expanden todas las secciones, el resultado se refleja en la sección de salida.  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md)