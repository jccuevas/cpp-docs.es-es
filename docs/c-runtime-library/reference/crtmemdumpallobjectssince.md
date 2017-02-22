---
title: "_CrtMemDumpAllObjectsSince | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtMemDumpAllObjectsSince"
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
  - "CrtMemDumpAllObjectsSince"
  - "_CrtMemDumpAllObjectsSince"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CrtMemDumpAllObjectsSince (función)"
  - "CrtMemDumpAllObjectsSince (función)"
ms.assetid: c48a447a-e6bb-475c-9271-a3021182a0dc
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _CrtMemDumpAllObjectsSince
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Vuelca información sobre objetos en el montón desde el inicio de la ejecución del programa o desde un estado del montón especificado \(solo versión de depuración\).  
  
## Sintaxis  
  
```  
  
      void _CrtMemDumpAllObjectsSince(   
   const _CrtMemState *state   
);  
```  
  
#### Parámetros  
 `state`  
 Puntero al estado del montón desde el que se va a iniciar el volcado o **NULL**.  
  
## Comentarios  
 La función `_CrtMemDumpAllObjectsSince` vuelca, con un formato legible para el usuario, la información de encabezado de depuración de objetos asignados en el montón.  La aplicación puede usar la información del volcado para realizar el seguimiento de las asignaciones y detectar problemas de memoria.  Cuando no se define [\_DEBUG](../../c-runtime-library/debug.md), las llamadas a `_CrtMemDumpAllObjectsSince` se quitan durante el preprocesamiento.  
  
 `_CrtMemDumpAllObjectsSince` utiliza el valor del parámetro `state` para determinar dónde iniciar la operación de volcado.  Para iniciar el volcado desde un estado del montón especificado, el parámetro `state` debe ser un puntero a una estructura de **\_CrtMemState** que [\_CrtMemCheckpoint](../../c-runtime-library/reference/crtmemcheckpoint.md) ha rellenado antes de que se llamara a `_CrtMemDumpAllObjectsSince`.  Cuando `state` es **NULL**, la función empieza el volcado desde el inicio de la ejecución del programa.  
  
 Si la aplicación ha instalado una función de enlace de volcado llamando a [\_CrtSetDumpClient](../../c-runtime-library/reference/crtsetdumpclient.md), cada vez que `_CrtMemDumpAllObjectsSince` vuelca información sobre un tipo de bloque `_CLIENT_BLOCK`, llama también a la función de volcado proporcionada por la aplicación.  De forma predeterminada, los bloques internos en tiempo de ejecución de C \(`_CRT_BLOCK`\) no se incluyen en las operaciones de volcado de la memoria.  La función [\_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md) se puede usar para activar el bit `_CRTDBG_CHECK_CRT_DF` de **\_crtDbgFlag** de forma que incluya estos bloques.  Además, los bloques marcados como liberados u omitidos \(**\_FREE\_BLOCK**, **\_IGNORE\_BLOCK**\) no se incluyen en el volcado de memoria.  
  
 Para obtener más información sobre las funciones de estado del montón y la estructura de `_CrtMemState`, vea [Funciones que indican el estado del montón](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Heap_State_Reporting_Functions).  Para obtener más información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [Detalles del montón de depuración de CRT](../Topic/CRT%20Debug%20Heap%20Details.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|**\_CrtMemDumpAll\-ObjectsSince**|\<crtdbg.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Solo las versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
 Para obtener un ejemplo de cómo usar `_CrtMemDumpAllObjectsSince`, vea [crt\_dbg2](http://msdn.microsoft.com/es-es/21e1346a-6a17-4f57-b275-c76813089167).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [\_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)