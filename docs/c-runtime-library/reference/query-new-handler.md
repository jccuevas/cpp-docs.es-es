---
title: "_query_new_handler | Microsoft Docs"
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
  - "_query_new_handler"
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
  - "_query_new_handler"
  - "query_new_handler"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_query_new_handler (función)"
  - "control de errores"
  - "rutinas de controlador"
  - "query_new_handler (función)"
ms.assetid: 9a84b5c3-fe33-4c01-83a0-be87dc3ec518
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _query_new_handler
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve la dirección de la nueva rutina del controlador actual.  
  
## Sintaxis  
  
```  
  
      _PNH _query_new_handler(  
   void   
);  
```  
  
## Valor devuelto  
 Devuelve la dirección de la nueva rutina del controlador actual como lo establece `_set_new_handler`.  
  
## Comentarios  
 La función de C\+\+ `_query_new_handler` devuelve la dirección del conjunto actual de la función de control de excepciones por la función de C\+\+ [\_set\_new\_handler](../../c-runtime-library/reference/set-new-handler.md) .  `_set_new_handler` se utiliza para especificar una función de control de excepciones que es el control de los si el operador de **new** no puede para asignar memoria.  Para obtener más información, vea las necesidades de [operador nuevo](../../misc/operator-new-function.md) y [operador delete](../../misc/operator-delete-function.md) funciona en *la referencia del lenguaje C\+\+*.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_query_new_handler`|\<new.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)   
 [free](../../c-runtime-library/reference/free.md)