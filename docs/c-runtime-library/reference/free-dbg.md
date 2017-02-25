---
title: "_free_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_free_dbg"
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
  - "_free_dbg"
  - "free_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bloques de memoria, desasignar"
  - "freeing (función)"
  - "_free_dbg (función)"
  - "free_dbg (función)"
ms.assetid: fc5e8299-616d-48a0-b979-e037117278c6
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# _free_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Libera un bloque de memoria del montón \(solo versión de depuración\).  
  
## Sintaxis  
  
```  
void _free_dbg(   
   void *userData,  
   int blockType   
);  
```  
  
#### Parámetros  
 `userData`  
 Puntero al bloque de memoria asignado que se va a liberar.  
  
 `blockType`  
 Tipo de bloque de memoria asignado que se va a liberar: `_CLIENT_BLOCK`, `_NORMAL_BLOCK` o `_IGNORE_BLOCK`.  
  
## Comentarios  
 La función `_free_dbg` es una versión de depuración de la función [free](../../c-runtime-library/reference/free.md).  Si no se define [\_DEBUG](../../c-runtime-library/debug.md), cada llamada a `_free_dbg` se reduce a una llamada a `free`.  `free` y `_free_dbg` liberan un bloque de memoria del montón base, pero `_free_dbg`  incluye dos características de depuración: la posibilidad de mantener los bloques liberados en la lista vinculada del montón para simular condiciones de memoria insuficiente y un parámetro de tipo de bloque para liberar tipos de asignación específicos.  
  
 `_free_dbg` realiza una comprobación de validez en todos los archivos especificados y las ubicaciones de bloques antes de realizar la operación de liberación.  No se espera que la aplicación proporcione esta información.  Cuando se libera un bloque de memoria, el administrador del montón de depuración comprueba automáticamente la integridad de los búferes situados a cada lado de la parte del usuario y emite un informe de error en caso de sobrescritura.  Si se establece el campo de bits `_CRTDBG_DELAY_FREE_MEM_DF`  de la marca [\_crtDbgFlag](../../c-runtime-library/crtdbgflag.md), el bloque liberado se rellena con el valor 0xDD, recibe el tipo de bloque `_FREE_BLOCK` y se mantiene en la lista vinculada de bloques de memoria del montón.  
  
 Si se produce un error al liberar memoria, en `errno` se muestra información sobre la naturaleza del error proporcionada por el sistema operativo.  Para obtener más información, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [Detalles del montón de depuración de CRT](../Topic/CRT%20Debug%20Heap%20Details.md).  Para obtener información sobre la asignación de tipos de bloque y cómo se usan, vea [Tipos de bloques en el montón de depuración](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap).  Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, vea [Versiones de depuración de las funciones de asignación del montón](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_free_dbg`|\<crtdbg.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Para obtener un ejemplo de cómo usar `_free_dbg`, vea [crt\_dbg2](http://msdn.microsoft.com/es-es/21e1346a-6a17-4f57-b275-c76813089167).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md)