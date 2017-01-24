---
title: "_aligned_recalloc | Microsoft Docs"
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
  - "_aligned_recalloc"
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
  - "aligned_recalloc"
  - "_aligned_recalloc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "aligned_recalloc (función)"
  - "_aligned_recalloc (función)"
ms.assetid: d3da3dcc-79ef-4273-8af5-ac7469420142
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _aligned_recalloc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cambia el tamaño de un bloque de memoria que fue asignado con [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md) o [\_aligned\_offset\_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) e inicializa memoria a 0.  
  
## Sintaxis  
  
```  
void * _aligned_recalloc(  
   void *memblock,   
   size_t num,  
   size_t size,   
   size_t alignment  
);  
```  
  
#### Parámetros  
 \[in\] `memblock`  
 El puntero actual del bloque de memoria.  
  
 \[in\] `num`  
 El número de elementos.  
  
 \[in\] `size`  
 Tamaño en bytes de cada elemento.  
  
 \[in\] `alignment`  
 Valor de la alineación, que debe ser un entero potencia de 2.  
  
## Valor devuelto  
 `_aligned_recalloc` devuelve un puntero void \(y posiblemente desplazado\) al bloque de memoria reasignado.  El valor devuelto es `NULL` si el tamaño es cero y el argumento del búfer no es `NULL`, o si no hay suficiente memoria disponible para expandir el bloque al tamaño especificado.  En el primer caso, se libera el bloque original.  En el segundo caso, el bloque de original no varía.  Los puntos del valor devuelto a un espacio de almacenamiento que se garantiza alinearse convenientemente para el almacenamiento de cualquier tipo de objeto.  Para obtener un puntero a un tipo distinto de vacío, utilice una conversión de tipo del valor devuelto.  
  
 Es un error para reasignar la memoria y para cambiar la alineación de un bloque.  
  
## Comentarios  
 `_aligned_recalloc` se basa en `malloc`.  Para obtener más información sobre cómo utilizar `_aligned_offset_malloc`, vea [malloc](../../c-runtime-library/reference/malloc.md).  
  
 Esta función establece `errno` en `ENOMEM` si se produce un error en la asignación de memoria o si el tamaño solicitado es mayor que `_HEAP_MAXREQ`.  Para obtener más información sobre `errno`, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  Además, `_aligned_recalloc` valida sus parámetros.  Si `alignment` no es una potencia de 2, esta función invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función devuelve `NULL` y establece `errno` en `EINVAL`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_aligned_recalloc`|\<malloc.h\>|  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Alineación de datos](../../c-runtime-library/data-alignment.md)   
 [\_recalloc](../../c-runtime-library/reference/recalloc.md)   
 [\_aligned\_offset\_recalloc](../../c-runtime-library/reference/aligned-offset-recalloc.md)