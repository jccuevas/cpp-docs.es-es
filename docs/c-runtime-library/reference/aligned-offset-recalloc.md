---
title: "_aligned_offset_recalloc | Microsoft Docs"
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
  - "_aligned_offset_recalloc"
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
  - "aligned_offset_recalloc"
  - "_aligned_offset_recalloc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "aligned_offset_recalloc (función)"
  - "_aligned_offset_recalloc (función)"
ms.assetid: a258f54e-eeb4-4853-96fc-007d710f98e9
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _aligned_offset_recalloc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cambia el tamaño de un bloque de memoria que fue asignado con [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md) o [\_aligned\_offset\_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) e inicializa memoria a 0.  
  
## Sintaxis  
  
```  
void * _aligned_offset_recalloc(  
   void *memblock,   
   size_t num,   
   size_t size,   
   size_t alignment,  
   size_t offset  
);  
```  
  
#### Parámetros  
 `memblock`  
 El puntero actual del bloque de memoria.  
  
 `num`  
 Número de elementos.  
  
 `size`  
 Longitud en bytes de cada elemento.  
  
 `alignment`  
 Valor de la alineación, que debe ser un entero potencia de 2.  
  
 `offset`  
 Desplazamiento en la asignación de memoria para imponer la alineación.  
  
## Valor devuelto  
 `_aligned_offset_recalloc` devuelve un puntero void \(y posiblemente desplazado\) al bloque de memoria reasignado.  El valor devuelto es `NULL` si el tamaño es cero y el argumento del búfer no es `NULL`, o si no hay suficiente memoria disponible para expandir el bloque al tamaño especificado.  En el primer caso, se libera el bloque original.  En el segundo caso, el bloque de original no varía.  Los puntos del valor devuelto a un espacio de almacenamiento que se garantiza alinearse convenientemente para el almacenamiento de cualquier tipo de objeto.  Para obtener un puntero a un tipo distinto de vacío, utilice una conversión de tipo del valor devuelto.  
  
 `_aligned_offset_recalloc` es `__declspec(noalias)` marcado y `__declspec(restrict)`, lo que significa que la función está garantizada para no modificar variables globales y que el puntero devuelto no es con alias.  Para obtener más información, vea [noalias](../../cpp/noalias.md) y [limitado](../../cpp/restrict.md).  
  
## Comentarios  
 Como [\_aligned\_offset\_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md), `_aligned_offset_recalloc` permite que una estructura está alineada en un desplazamiento dentro de la estructura.  
  
 `_aligned_offset_recalloc` se basa en `malloc`.  Para obtener más información sobre cómo utilizar `_aligned_offset_malloc`, vea [malloc](../../c-runtime-library/reference/malloc.md).  Si `memblock` es `NULL`, la función `_aligned_offset_malloc` internamente.  
  
 Esta función establece `errno` a `ENOMEM` aunque falle la asignación de memoria o si el tamaño solicitado \(`num` \* `size`\) era mayor que `_HEAP_MAXREQ`.  Para obtener más información sobre `errno`, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  Además, `_aligned_offset_recalloc` valida sus parámetros.  Si `alignment` no es una potencia de 2 o si es `offset` mayor o igual que el tamaño solicitado y distinto de cero, esta función invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función devuelve `NULL` y establece `errno` en `EINVAL`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_aligned_offset_recalloc`|\<malloc.h\>|  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Alineación de datos](../../c-runtime-library/data-alignment.md)   
 [\_recalloc](../../c-runtime-library/reference/recalloc.md)   
 [\_aligned\_recalloc](../../c-runtime-library/reference/aligned-recalloc.md)