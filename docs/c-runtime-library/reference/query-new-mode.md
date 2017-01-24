---
title: "_query_new_mode | Microsoft Docs"
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
  - "_query_new_mode"
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
  - "query_new_mode"
  - "_query_new_mode"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_query_new_mode (función)"
  - "modos de controlador"
  - "query_new_mode (función)"
ms.assetid: e185c5f9-b73b-4257-8eff-b47648374768
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _query_new_mode
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve un entero que indica el nuevo modo de controlador establecido por `_set_new_mode` para `malloc`.  
  
## Sintaxis  
  
```  
  
      int _query_new_mode(  
   void   
);  
```  
  
## Valor devuelto  
 Devuelve el nuevo modo del controlador actual, que es 0 o 1, para `malloc`.  Devuelve un valor de 1 indica que, en el error asignar memoria, `malloc` llama a la nueva rutina de controlador; devuelve un valor de 0 indica que no almacena.  
  
## Comentarios  
 La función de C\+\+ `_query_new_mode` devuelve un entero que indica el nuevo modo de controlador que se establece por la función de C\+\+ [\_set\_new\_mode](../../c-runtime-library/reference/set-new-mode.md) para [malloc](../../c-runtime-library/reference/malloc.md).  El nuevo modo de controlador indica si, en el error asignar memoria, `malloc` es llamar a la nueva rutina de controlador como lo establece [\_set\_new\_handler](../../c-runtime-library/reference/set-new-handler.md).  De forma predeterminada, `malloc` no llama a la nueva rutina del controlador del error.  Puede utilizar `_set_new_mode` para reemplazar este comportamiento de modo que en el error `malloc` llame a la nueva rutina del controlador de la misma manera que el operador de **new** cuando no puede para asignar memoria.  Para obtener más información, vea [operador delete](../../misc/operator-delete-function.md) y [operador nuevo](../../misc/operator-new-function.md) funciona en *la referencia del lenguaje C\+\+*.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_query_new_mode`|\<new.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [\_query\_new\_handler](../../c-runtime-library/reference/query-new-handler.md)