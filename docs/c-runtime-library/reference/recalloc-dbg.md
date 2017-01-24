---
title: "_recalloc_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_recalloc_dbg"
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
  - "recalloc_dbg"
  - "_recalloc_dbg"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_recalloc_dbg (función)"
  - "recalloc_dbg (función)"
ms.assetid: 43c3e9b2-be6d-4508-9b0f-3220c8a47ca3
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _recalloc_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Reasigna una matriz e inicializa sus elementos a 0 \(solo versión de depuración\).  
  
## Sintaxis  
  
```  
void *_recalloc_dbg(     void *userData,    size_t num,    size_t size,    int blockType,    const char *filename,    int linenumber  );  
```  
  
#### Parámetros  
 `userData`  
 Puntero al bloque de memoria asignado previamente.  
  
 `num`  
 Número de bloques de memoria solicitado.  
  
 `size`  
 Tamaño de cada bloque de memoria solicitado \(bytes\).  
  
 `blockType`  
 Tipo de bloque de memoria solicitado: `_CLIENT_BLOCK` o `_NORMAL_BLOCK`.  
  
 Para más información sobre los tipos de bloques de asignación y su uso, vea [Tipos de bloques en el montón de depuración](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap).  
  
 `filename`  
 Puntero al nombre del archivo de código fuente que solicitó la operación de asignación o `NULL`.  
  
 `linenumber`  
 Número de línea del archivo de código fuente en la que se solicitó la operación de asignación o `NULL`.  
  
 Los parámetros `filename` y `linenumber` solo están disponibles cuando se ha llamado a `_recalloc_dbg` explícitamente o se ha definido la constante de preprocesador [\_CRTDBG\_MAP\_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md).  
  
## Valor devuelto  
 Cuando se lleva a cabo correctamente, esta función devuelve un puntero a la parte del usuario del bloque de memoria reasignado, llama a la nueva función de controlador o devuelve NULL.  Para obtener una descripción completa del comportamiento de retorno, vea la sección de comentarios más abajo.  Para más información sobre cómo usar la nueva función de controlador, vea la función [\_recalloc](../../c-runtime-library/reference/recalloc.md).  
  
## Comentarios  
 `_recalloc_dbg` es una versión de depuración de la función [\_recalloc](../../c-runtime-library/reference/recalloc.md).  Si no se define [\_DEBUG](../../c-runtime-library/debug.md), cada llamada a `_recalloc_dbg` se reduce a una llamada a `_recalloc`.  `_recalloc` y `_recalloc_dbg` reasignan los bloques de memoria del montón base, pero `_recalloc_dbg` ofrece varias características de depuración: búferes situados a cada lado de la parte del usuario del bloque en el que se va a comprobar si hay pérdidas, un parámetro de tipo de bloque para realizar el seguimiento de tipos de asignación concretos e información sobre `filename`\/`linenumber` para conocer el origen de las solicitudes de asignación.  
  
 `_recalloc_dbg` reasigna el bloque de memoria especificado con un poco más de espacio del solicitado \(`num` \* `size`\), que podría ser mayor o menor que el tamaño del bloque de memoria asignado originalmente.  El administrador del montón de depuración usa el espacio adicional para vincular los bloques de memoria de depuración, y para proporcionar a la aplicación información de encabezado de depuración y sobrescribir los búferes.  La reasignación podría hacer que el bloque de memoria original se ponga en una ubicación distinta del montón y cambiar el tamaño del bloque de memoria.  La parte del usuario de bloque se rellena con el valor 0xCD y cada uno de los búferes sobrescritos se rellena con 0xFD.  
  
 `_recalloc_dbg` establece `errno` en `ENOMEM` si se produce un error de asignación de memoria. Se devuelve `EINVAL` si la cantidad de memoria necesaria \(incluida la sobrecarga ya mencionada\) es mayor que `_HEAP_MAXREQ`.  Para obtener más información sobre este y otros códigos de error, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [Detalles del montón de depuración de CRT](../Topic/CRT%20Debug%20Heap%20Details.md).  Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, vea [Versiones de depuración de las funciones de asignación del montón](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_recalloc_dbg`|\<crtdbg.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Solo las versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)