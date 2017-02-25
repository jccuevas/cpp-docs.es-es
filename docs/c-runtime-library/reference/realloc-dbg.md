---
title: "_realloc_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_realloc_dbg"
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
  - "_realloc_dbg"
  - "realloc_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reasignar bloques de memoria"
  - "realloc_dbg (función)"
  - "bloques de memoria, reasignar"
  - "memoria, reasignar"
  - "_realloc_dbg (función)"
ms.assetid: 7c3cb780-51ed-4d9c-9929-cdde606d846a
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _realloc_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Reasigna un bloque de memoria especificado en el montón moviendo o cambiando el tamaño del bloque \(solo versión de depuración\).  
  
## Sintaxis  
  
```  
void *_realloc_dbg(  
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
 Tamaño solicitado para el bloque reasignado \(bytes\).  
  
 `blockType`  
 Tipo solicitado para el bloque reasignado: `_CLIENT_BLOCK` o `_NORMAL_BLOCK`.  
  
 `filename`  
 Puntero al nombre del archivo de código fuente que solicitó la operación `realloc` o valor NULL.  
  
 `linenumber`  
 Número de línea del archivo de código fuente en la que se solicitó la operación `realloc` o valor NULL.  
  
 Los parámetros `filename` y `linenumber` solo están disponibles cuando se ha llamado a `_realloc_dbg` explícitamente o se ha definido la constante de preprocesador [\_CRTDBG\_MAP\_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md).  
  
## Valor devuelto  
 Cuando se lleva a cabo correctamente, esta función devuelve un puntero a la parte del usuario del bloque de memoria reasignado, llama a la nueva función de controlador o devuelve NULL.  Para obtener una descripción completa del comportamiento de retorno, vea la sección de comentarios más abajo.  Para obtener más información sobre cómo se usa la nueva función de controlador, vea la función [realloc](../../c-runtime-library/reference/realloc.md).  
  
## Comentarios  
 `_realloc_dbg` es una versión de depuración de la función [realloc](../../c-runtime-library/reference/realloc.md).  Si no se define [\_DEBUG](../../c-runtime-library/debug.md), cada llamada a `_realloc_dbg` se reduce a una llamada a `realloc`.  `realloc` y `_realloc_dbg` reasignan un bloque de memoria del montón base, pero `_realloc_dbg` admite varias características de depuración: búferes situados a cada lado de la parte del usuario del bloque en el que se va a comprobar si hay pérdidas, un parámetro de tipo de bloque para realizar el seguimiento de tipos de asignación concretos, e información sobre `filename` o `linenumber` para determinar el origen de las solicitudes de asignación.  
  
 `_realloc_dbg` reasigna el bloque de memoria especificado con un poco más de espacio que el `newSize` solicitado.  `newSize` podría ser mayor o menor que el tamaño del bloque de memoria asignado originalmente.  El administrador del montón de depuración usa el espacio adicional para vincular los bloques de memoria de depuración, y para proporcionar a la aplicación información de encabezado de depuración y sobrescribir los búferes.  La reasignación podría hacer que el bloque de memoria original se ponga en una ubicación distinta del montón y cambiar el tamaño del bloque de memoria.  Si se mueve el bloque de memoria, el contenido del bloque original se sobrescribe.  
  
 `_realloc_dbg` establece `errno` en `ENOMEM` si se produce un error de asignación de memoria o si la cantidad de memoria necesaria \(incluida la sobrecarga ya mencionada\) es mayor que `_HEAP_MAXREQ`.  Para obtener más información sobre este y otros códigos de error, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [Detalles del montón de depuración de CRT](../Topic/CRT%20Debug%20Heap%20Details.md).  Para obtener información sobre la asignación de tipos de bloque y cómo se usan, vea [Tipos de bloques en el montón de depuración](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap).  Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, vea [Versiones de depuración de las funciones de asignación del montón](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_realloc_dbg`|\<crtdbg.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Solo las versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
 Vea el ejemplo del tema sobre [\_msize\_dbg](../../c-runtime-library/reference/msize-dbg.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md)