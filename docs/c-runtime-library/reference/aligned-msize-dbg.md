---
title: "_aligned_msize_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_aligned_msize_dbg"
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
  - "_aligned_msize_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_aligned_msize_dbg"
ms.assetid: f1c44af0-3f66-4033-81d1-d71d3afecba0
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# _aligned_msize_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve el tamaño de un bloque de memoria asignado en el montón \(solo versión de depuración\).  
  
## Sintaxis  
  
```  
size_t _aligned_msize_dbg(  
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
 Los valores de `alignment` y `offset` deben ser iguales que los valores que se pasan a la función que asignó el bloque.  
  
 `_aligned_msize_dbg` es una versión de depuración de la función [\_aligned\_msize](../../c-runtime-library/reference/aligned-msize.md).  Si no se define [\_DEBUG](../../c-runtime-library/debug.md), cada llamada a `_aligned_msize_dbg` se reduce a una llamada a `_aligned_msize`.  `_aligned_msize` y `_aligned_msize_dbg` calculan el tamaño de un bloque de memoria del montón base, pero `_aligned_msize_dbg` agrega una característica de depuración: incluye los búferes situados en cada extremo de la parte del usuario del bloque de memoria en el tamaño que devuelve.  
  
 Esta función valida su parámetro.  Si `memblock` es un puntero nulo o `alignment` no es una potencia de 2, `_msize` invoca un controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si se controla el error, la función establece `errno` en `EINVAL` y devuelve \-1.  
  
 Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [Detalles del montón de depuración de CRT](../Topic/CRT%20Debug%20Heap%20Details.md).  Para obtener información sobre la asignación de tipos de bloque y cómo se usan, vea [Tipos de bloques en el montón de depuración](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap).  Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, vea [Versiones de depuración de las funciones de asignación del montón](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_aligned_msize_dbg`|\<crtdbg.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Solo las versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)