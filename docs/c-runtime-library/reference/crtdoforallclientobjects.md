---
title: "_CrtDoForAllClientObjects | Microsoft Docs"
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
  - "_CrtDoForAllClientObjects"
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
  - "_CrtDoForAllClientObjects"
  - "CrtDoForAllClientObjects"
  - "crtdbg/_CrdDoForAllClientObjects"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_CrtDoForAllClientObjects (función)"
  - "CrtDoForAllClientObjects (función)"
ms.assetid: d0fdb835-3cdc-45f1-9a21-54208e8df248
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CrtDoForAllClientObjects
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Llama a una función proporcionada por la aplicación para todos los tipos `_CLIENT_BLOCK` del montón \(solo versión de depuración\).  
  
## Sintaxis  
  
```  
void _CrtDoForAllClientObjects(   
   void ( * pfn )( void *, void * ),  
   void *context  
);  
```  
  
#### Parámetros  
 `pfn`  
 Puntero a la función de devolución de llamada proporcionada por la aplicación. El primer parámetro de esta función señala a los datos. El segundo parámetro es el puntero de contexto que se pasa a la llamada a `_CrtDoForAllClientObjects`.  
  
 `context`  
 Puntero al contexto proporcionado por la aplicación que se va a pasar a la función proporcionada por la aplicación.  
  
## Comentarios  
 La función `_CrtDoForAllClientObjects` busca en la lista vinculada del montón bloques de memoria con el tipo `_CLIENT_BLOCK` y llama a la función proporcionada por la aplicación cuando se encuentra un bloque de este tipo. El bloque encontrado y el parámetro `context` se pasan como argumentos a la función proporcionada por la aplicación. Durante la depuración, una aplicación puede realizar el seguimiento de un grupo específico de asignaciones llamando explícitamente a las funciones del montón de depuración para asignar memoria y especificando que se asigne a los bloques el tipo de bloque `_CLIENT_BLOCK`. A continuación, se puede realizar el seguimiento y la notificación de estos bloques por separado durante la detección de pérdidas y la creación de informes sobre el estado de la memoria.  
  
 Si el campo de bits `_CRTDBG_ALLOC_MEM_DF` de la marca [\_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) no está activado, el resultado de `_CrtDoForAllClientObjects` se devuelve inmediatamente. Si no se define [\_DEBUG](../../c-runtime-library/debug.md), las llamadas a `_CrtDoForAllClientObjects` se quitan durante el preprocesamiento.  
  
 Para más información sobre el tipo `_CLIENT_BLOCK` y cómo lo pueden usar otras funciones de depuración, vea [Tipos de bloques en el montón de depuración](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap). Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [Detalles del montón de depuración de CRT](../Topic/CRT%20Debug%20Heap%20Details.md).  
  
 Si `pfn` es `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) se establece en `EINVAL` y la función finaliza.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_CrtDoForAllClientObjects`|\<crtdbg.h\>, \<errno.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
 **Bibliotecas:** solo versiones de depuración de las bibliotecas en tiempo de ejecución de C universales.  
  
## Equivalente en .NET Framework  
 No disponible. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [\_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md)   
 [Funciones que indican el estado del montón](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Heap_State_Reporting_Functions)   
 [\_CrtReportBlockType](../../c-runtime-library/reference/crtreportblocktype.md)