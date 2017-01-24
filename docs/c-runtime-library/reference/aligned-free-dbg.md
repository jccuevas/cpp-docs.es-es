---
title: "_aligned_free_dbg | Microsoft Docs"
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
  - "_aligned_free_dbg"
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
  - "_aligned_free_dbg"
  - "aligned_free_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_aligned_free_dbg (función)"
  - "aligned_free_dbg (función)"
ms.assetid: eb0cb3c8-0992-4db8-bac3-65f1b8311ca6
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _aligned_free_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Libera un bloque de memoria que se asignó con [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md) o [\_aligned\_offset\_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) \(solo versión de depuración\).  
  
## Sintaxis  
  
```  
void _aligned_free_dbg(    void *memblock );  
```  
  
#### Parámetros  
 `memblock`  
 Puntero al bloque de memoria que se devolvió a las funciones `_aligned_malloc` o `_aligned_offset_malloc`.  
  
## Comentarios  
 La función `_aligned_free_dbg`  es una versión de depuración de la función [\_aligned\_free](../../c-runtime-library/reference/aligned-free.md).  Si [\_DEBUG](../../c-runtime-library/debug.md) no se define, cada llamada a `_aligned_free_dbg` se reduce a una llamada a \_`aligned_free`.  \_`aligned_free` y `_aligned_free_dbg` liberan un bloque de memoria del montón base, pero `_aligned_free_dbg`  ofrece una característica de depuración: la posibilidad de mantener los bloques liberados en la lista vinculada del montón para simular situaciones de memoria baja.  
  
 `_aligned_free_dbg` realiza una comprobación de validez en todos los archivos especificados y las ubicaciones de bloques antes de realizar la operación de liberación.  No se espera que la aplicación proporcione esta información.  Cuando se libera un bloque de memoria, el administrador del montón de depuración comprueba automáticamente la integridad de los búferes situados a cada lado de la parte del usuario y emite un informe de error en caso de sobrescritura.  Si se establece el campo de bits `_CRTDBG_DELAY_FREE_MEM_DF`  de la marca [\_crtDbgFlag](../../c-runtime-library/crtdbgflag.md), el bloque liberado se rellena con el valor 0xDD, recibe el tipo de bloque `_FREE_BLOCK` y se mantiene en la lista vinculada de bloques de memoria del montón.  
  
 Si se produce un error al liberar memoria, en `errno` se muestra información sobre la naturaleza del error proporcionada por el sistema operativo.  Para obtener más información, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [Detalles del montón de depuración de CRT](../Topic/CRT%20Debug%20Heap%20Details.md).  Para más información sobre los tipos de bloques de asignación y su uso, vea [Tipos de bloques en el montón de depuración](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap).  Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, vea [Versiones de depuración de las funciones de asignación del montón](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_aligned_free_dbg`|\<crtdbg.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)