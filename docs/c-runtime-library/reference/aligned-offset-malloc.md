---
title: "_aligned_offset_malloc | Microsoft Docs"
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
  - "_aligned_offset_malloc"
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
  - "_aligned_offset_malloc"
  - "aligned_offset_malloc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_aligned_offset_malloc (función)"
  - "aligned_offset_malloc (función)"
ms.assetid: 447681a3-7c95-4655-86ba-fa3a4ca4c521
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _aligned_offset_malloc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Asigna memoria en un límite de alineación especificado.  
  
## Sintaxis  
  
```  
void * _aligned_offset_malloc(  
   size_t size,   
   size_t alignment,   
   size_t offset  
);  
```  
  
#### Parámetros  
 \[in\] `size`  
 Tamaño de la asignación de memoria solicitada.  
  
 \[in\] `alignment`  
 Valor de la alineación, que debe ser un entero potencia de 2.  
  
 \[in\] `offset`  
 Desplazamiento en la asignación de memoria para imponer la alineación.  
  
## Valor devuelto  
 Puntero al bloque de memoria que se asignó o `NULL`  si se produjo un error en la operación.  
  
## Comentarios  
 `_aligned_offset_malloc` es útil en situaciones en las que la alineación se necesita en un elemento anidado, por ejemplo si se necesitara la alineación en una clase anidada.  
  
 `_aligned_offset_malloc` se basa en `malloc`. Para obtener más información, vea [malloc](../../c-runtime-library/reference/malloc.md).  
  
 `_aligned_offset_malloc` es `__declspec(noalias)` marcado y `__declspec(restrict)`, lo que significa que la función está garantizada para no modificar variables globales y que el puntero devuelto no es con alias.  Para obtener más información, vea [noalias](../../cpp/noalias.md) y [limitado](../../cpp/restrict.md).  
  
 Esta función establece `errno` en `ENOMEM` si se produce un error en la asignación de memoria o si el tamaño solicitado es mayor que `_HEAP_MAXREQ`.  Para obtener más información sobre `errno`, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  Además, `_aligned_offset_malloc` valida sus parámetros.  Si `alignment` no es una potencia de 2, o `offset` es mayor o igual que `size` y distinto de cero, esta función invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función devuelve `NULL` y establece `errno` en `EINVAL`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_aligned_offset_malloc`|\<malloc.h\>|  
  
## Ejemplo  
 Para obtener más información, vea [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md).  
  
## Vea también  
 [Alineación de datos](../../c-runtime-library/data-alignment.md)