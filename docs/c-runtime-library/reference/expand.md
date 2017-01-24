---
title: "_expand | Microsoft Docs"
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
  - "_expand"
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
  - "_bexpand"
  - "fexpand"
  - "expand"
  - "nexpand"
  - "_fexpand"
  - "_nexpand"
  - "bexpand"
  - "_expand"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_expand (función)"
  - "expand (función)"
  - "bloques de memoria, cambiar el tamaño"
ms.assetid: 4ac55410-39c8-45c7-bccd-3f1042ae2ed3
caps.latest.revision: 22
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _expand
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cambia el tamaño de un bloque de memoria.  
  
## Sintaxis  
  
```  
void *_expand(   
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
 `_expand` devuelve un puntero vacío al bloque de memoria reasignado.  `_expand`, a diferencia de `realloc`, no puede mover un bloque para cambiar su tamaño.  Así, si hay suficiente memoria disponible expandir el bloque sin moverlo, el parámetro de `memblock` a `_expand` es igual que el valor devuelto.  
  
 `_expand` devuelve `NULL` cuando se detecta un error durante la operación.  Por ejemplo, si `_expand` se utiliza para reducir un bloque de memoria, puede detectar daños en el montón o un puntero y un retorno no válidos `NULL`de bloques de bloque.  
  
 Si la memoria disponible no es suficiente expandir el bloque al tamaño especificado sin moverlo, la función devuelve `NULL`.  `_expand` nunca devuelve un bloque expandido a un tamaño menor que solicitado.  Si se produce un error, `errno` indica la naturaleza del error.  Para obtener más información sobre `errno`, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Los puntos del valor devuelto a un espacio de almacenamiento que se garantiza alinearse convenientemente para el almacenamiento de cualquier tipo de objeto.  Para comprobar el nuevo tamaño del elemento, utilice `_msize`.  Para obtener un puntero a un tipo distinto de `void`, utilice una conversión de tipo del valor devuelto.  
  
## Comentarios  
 Los cambios de función de `_expand` el tamaño de un bloque de memoria previamente asignado por intentar para expandir o el contrato el bloque sin mover su ubicación en la pila.  Los puntos del parámetro de `memblock` al principio del bloque.  El parámetro de `size` da el nuevo tamaño de bloque, en bytes.  El contenido del bloque son sin cambios hasta el menor de los nuevo y antiguo tamaños.  `memblock` no debe ser un bloque se ha liberado que.  
  
> [!NOTE]
>  En plataformas de 64 bits, `_expand` podría no contrato el bloque si el nuevo tamaño sea menor que el tamaño actual; en concreto, si el bloque es menos que 16K de tamaño y por consiguiente asignado en el montón Low Fragmentation, `_expand` sale del bloque sin cambios y devuelve `memblock`.  
  
 Cuando la aplicación se vincula con una versión de depuración de las bibliotecas en tiempo de ejecución de C, `_expand` resuelve a [\_expand\_dbg](../../c-runtime-library/reference/expand-dbg.md).  Para obtener más información sobre cómo la pila se administra durante el proceso de depuración, vea [El montón de depuración de CRT](../Topic/CRT%20Debug%20Heap%20Details.md).  
  
 Esta función valida sus parámetros.  Si `memblock` es un puntero NULL, esta función invoca un controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve `NULL`.  Si `size` es mayor que `_HEAP_MAXREQ`, `errno` se establece en `ENOMEM` y la función devuelve `NULL`.  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`_expand`|\<malloc.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_expand.c  
  
#include <stdio.h>  
#include <malloc.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   char *bufchar;  
   printf( "Allocate a 512 element buffer\n" );  
   if( (bufchar = (char *)calloc( 512, sizeof( char ) )) == NULL )  
      exit( 1 );  
   printf( "Allocated %d bytes at %Fp\n",   
         _msize( bufchar ), (void *)bufchar );  
   if( (bufchar = (char *)_expand( bufchar, 1024 )) == NULL )  
      printf( "Can't expand" );  
   else  
      printf( "Expanded block to %d bytes at %Fp\n",   
            _msize( bufchar ), (void *)bufchar );  
   // Free memory   
   free( bufchar );  
   exit( 0 );  
}  
```  
  
  **Asigna un búfer de 512 elementos**  
**Asignado 512 bytes en 002 C12 C.**  
**Bloque expandido a 1024 bytes en 002 C12 C.**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [\_msize](../../c-runtime-library/reference/msize.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)