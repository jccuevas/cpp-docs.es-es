---
title: "_malloc_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_malloc_dbg"
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
  - "malloc_dbg"
  - "_malloc_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_malloc_dbg (función)"
  - "malloc_dbg (función)"
  - "asignación de memoria"
ms.assetid: c97eca51-140b-4461-8bd2-28965b49ecdb
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# _malloc_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Asigna un bloque de memoria del montón con espacio adicional para un encabezado de depuración y búferes sobrescritos \(solo versión de depuración\).  
  
## Sintaxis  
  
```  
void *_malloc_dbg(    size_t size,    int blockType,    const char *filename,    int linenumber  );  
```  
  
#### Parámetros  
 `size`  
 Tamaño solicitado del bloque de memoria \(en bytes\).  
  
 `blockType`  
 Tipo de bloque de memoria solicitado: `_CLIENT_BLOCK` o `_NORMAL_BLOCK`.  
  
 `filename`  
 Puntero al nombre del archivo de código fuente que solicitó la operación de asignación o valor NULL.  
  
 `linenumber`  
 Número de línea del archivo de código fuente en la que se solicitó la operación de asignación o valor NULL.  
  
 Los parámetros `filename` y `linenumber` solo están disponibles cuando se ha llamado a `_malloc_dbg` explícitamente o se ha definido la constante de preprocesador [\_CRTDBG\_MAP\_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md).  
  
## Valor devuelto  
 Cuando se lleva a cabo correctamente, esta función devuelve un puntero a la parte del usuario del último bloque de memoria asignado, llama a la nueva función de controlador o devuelve NULL.  Para obtener una descripción completa del comportamiento de retorno, vea la sección de comentarios más abajo.  Para más información sobre cómo se usa la nueva función de controlador, vea la función [malloc](../../c-runtime-library/reference/malloc.md).  
  
## Comentarios  
 `_malloc_dbg` es una versión de depuración de la función [malloc](../../c-runtime-library/reference/malloc.md).  Si no se define [\_DEBUG](../../c-runtime-library/debug.md), cada llamada a `_malloc_dbg` se reduce a una llamada a `malloc`.  `malloc` y `_malloc_dbg` asignan un bloque de memoria del montón base, pero `_malloc_dbg` ofrece varias características de depuración: búferes situados a cada lado de la parte del usuario del bloque en el que se va a comprobar si hay pérdidas, un parámetro de tipo de bloque para realizar el seguimiento de tipos de asignación concretos e información sobre `filename`\/`linenumber` para conocer el origen de las solicitudes de asignación.  
  
 `_malloc_dbg` asigna el bloque de memoria con un poco más de espacio que el `size` solicitado.  El administrador del montón de depuración usa el espacio adicional para vincular los bloques de memoria de depuración, y para proporcionar a la aplicación información de encabezado de depuración y sobrescribir los búferes.  Cuando se asigna el bloque, la parte del usuario de bloque se rellena con el valor 0xCD y cada uno de los búferes sobrescritos se rellena con 0xFD.  
  
 `_malloc_dbg` establece `errno` en `ENOMEM` si se produce un error de asignación de memoria o si la cantidad de memoria necesaria \(incluida la sobrecarga ya mencionada\) es mayor que `_HEAP_MAXREQ`.  Para obtener más información sobre este y otros códigos de error, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [Detalles del montón de depuración de CRT](../Topic/CRT%20Debug%20Heap%20Details.md).  Para más información sobre los tipos de bloques de asignación y su uso, vea [Tipos de bloques en el montón de depuración](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap).  Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, vea [Versiones de depuración de las funciones de asignación del montón](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_malloc_dbg`|\<crtdbg.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Solo las versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
 Para obtener un ejemplo de cómo usar `_malloc_dbg`, vea [crt\_dbg1](http://msdn.microsoft.com/es-es/17b4b20c-e849-48f5-8eb5-dca6509cbaf9).  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [\_calloc\_dbg](../../c-runtime-library/reference/calloc-dbg.md)   
 [\_calloc\_dbg](../../c-runtime-library/reference/calloc-dbg.md)