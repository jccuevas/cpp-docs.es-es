---
title: "_aligned_offset_realloc | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_aligned_offset_realloc"
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
  - "aligned_offset_realloc"
  - "_aligned_offset_realloc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "aligned_offset_realloc (función)"
  - "_aligned_offset_realloc (función)"
ms.assetid: e0263533-991e-41b0-acc9-1b8a51ab9ecd
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _aligned_offset_realloc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cambia el tamaño de un bloque de memoria que fue asignado con [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md) o [\_aligned\_offset\_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md).  
  
## Sintaxis  
  
```  
void * _aligned_offset_realloc(  
   void *memblock,   
   size_t size,   
   size_t alignment,  
   size_t offset  
);  
```  
  
#### Parámetros  
 `memblock`  
 El puntero actual del bloque de memoria.  
  
 `size`  
 El tamaño de asignación de memoria.  
  
 `alignment`  
 Valor de la alineación, que debe ser un entero potencia de 2.  
  
 `offset`  
 Desplazamiento en la asignación de memoria para imponer la alineación.  
  
## Valor devuelto  
 `_aligned_offset_realloc` devuelve un puntero void \(y posiblemente desplazado\) al bloque de memoria reasignado.  El valor devuelto es `NULL` si el tamaño es cero y el argumento del búfer no es `NULL`, o si no hay suficiente memoria disponible para expandir el bloque al tamaño especificado.  En el primer caso, se libera el bloque original.  En el segundo caso, el bloque de original no varía.  Los puntos del valor devuelto a un espacio de almacenamiento que se garantiza alinearse convenientemente para el almacenamiento de cualquier tipo de objeto.  Para obtener un puntero a un tipo distinto de vacío, utilice una conversión de tipo del valor devuelto.  
  
 `_aligned_offset_realloc` es `__declspec(noalias)` marcado y `__declspec(restrict)`, lo que significa que la función está garantizada para no modificar variables globales y que el puntero devuelto no es con alias.  Para obtener más información, vea [noalias](../../cpp/noalias.md) y [limitado](../../cpp/restrict.md).  
  
## Comentarios  
 Como [\_aligned\_offset\_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md), `_aligned_offset_realloc` permite que una estructura está alineada en un desplazamiento dentro de la estructura.  
  
 `_aligned_offset_realloc` se basa en `malloc`.  Para obtener más información sobre cómo utilizar `_aligned_offset_malloc`, vea [malloc](../../c-runtime-library/reference/malloc.md).  Si `memblock` es `NULL`, la función `_aligned_offset_malloc` internamente.  
  
 Esta función establece `errno` en `ENOMEM` si se produce un error en la asignación de memoria o si el tamaño solicitado es mayor que `_HEAP_MAXREQ`.  Para obtener más información sobre `errno`, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  Además, `_aligned_offset_realloc` valida sus parámetros.  Si `alignment` no es una potencia de 2, o `offset` es mayor o igual que `size` y distinto de cero, esta función invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función devuelve `NULL` y establece `errno` en `EINVAL`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_aligned_offset_realloc`|\<malloc.h\>|  
  
## Ejemplo  
 Para obtener más información, vea [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md).  
  
## Vea también  
 [Alineación de datos](../../c-runtime-library/data-alignment.md)