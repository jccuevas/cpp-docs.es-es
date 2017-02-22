---
title: "_aligned_msize | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_aligned_msize"
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
  - "_aligned_msize"
  - "aligned_msize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_aligned_msize (función)"
  - "aligned_msize (función)"
ms.assetid: 10995edc-2110-4212-9ca9-5e0220a464f4
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# _aligned_msize
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve el tamaño de un bloque de memoria asignado en el montón.  
  
## Sintaxis  
  
```  
size_t _msize(  
   void *memblock,  
   size_t alignment,  
   size_t offset  
);  
```  
  
#### Parámetros  
 \[in\] `memblock`  
 Puntero al bloque de memoria.  
  
 \[in\] `alignment`  
 Valor de la alineación, que debe ser un entero potencia de 2.  
  
 \[in\] `offset`  
 Desplazamiento en la asignación de memoria para imponer la alineación.  
  
## Valor devuelto  
 Devuelve el tamaño \(en bytes\) de un entero sin signo.  
  
## Comentarios  
 La función de `_aligned_msize` devuelve el tamaño, en bytes, del bloque de memoria asignado por una llamada a [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md) o a [\_aligned\_realloc](../../c-runtime-library/reference/aligned-realloc.md).  Los valores de `alignment` y `offset` deben ser iguales que los valores que se pasan a la función que asignó el bloque.  
  
 Cuando la aplicación se vincula con una versión de depuración de las bibliotecas en tiempo de ejecución de C, `_aligned_msize` resuelve a [\_aligned\_msize\_dbg](../../c-runtime-library/reference/aligned-msize-dbg.md).  Para obtener más información sobre cómo la pila se administra durante el proceso de depuración, vea [El montón de depuración de CRT](../Topic/CRT%20Debug%20Heap%20Details.md).  
  
 Esta función valida su parámetro.  Si `memblock` es un puntero nulo o `alignment` no es una potencia de 2, `_msize` invoca un controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si se controla el error, la función establece `errno` en `EINVAL` y devuelve \-1.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_msize`|\<malloc.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)