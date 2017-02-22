---
title: "_CrtMemCheckpoint | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtMemCheckpoint"
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
  - "CrtMemCheckpoint"
  - "_CrtMemCheckpoint"
  - "crtdbg/_CrtMemCheckpoint"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CrtMemCheckpoint (función)"
  - "_CrtMemCheckpoint (función)"
ms.assetid: f1bacbaa-5a0c-498a-ac7a-b6131d83dfbc
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# _CrtMemCheckpoint
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene el estado actual del montón de depuración y lo almacena en una estructura de `_CrtMemState` proporcionada por la aplicación \(solo versión de depuración\).  
  
## Sintaxis  
  
```  
void _CrtMemCheckpoint(  
   _CrtMemState *state   
);  
```  
  
#### Parámetros  
 `state`  
 Puntero a la estructura de `_CrtMemState` que se va a rellenar con el punto de control de memoria.  
  
## Comentarios  
 La función `_CrtMemCheckpoint` crea una instantánea del estado actual del montón de depuración en cualquier momento determinado. Esta instantánea la pueden usar otras funciones de estado del montón, como [\_CrtMemDifference](../../c-runtime-library/reference/crtmemdifference.md), para ayudar a detectar pérdidas de memoria y otros problemas. Si no se define [\_DEBUG](../../c-runtime-library/debug.md), las llamadas a `_CrtMemState` se quitan durante el preprocesamiento.  
  
 La aplicación debe pasar un puntero a una instancia de la estructura de `_CrtMemState` previamente asignada, definida en Crtdbg.h, en el parámetro `state`. Si `_CrtMemCheckpoint` encuentra un error durante la creación del punto de control, la función genera un informe de depuración de `_CRT_WARN` en el que se describe el problema.  
  
 Para más información sobre las funciones de estado del montón y la estructura `_CrtMemState`, vea [Funciones que indican el estado del montón](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Heap_State_Reporting_Functions). Para más información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [Detalles del montón de depuración de CRT](../Topic/CRT%20Debug%20Heap%20Details.md).  
  
 Si `state` es `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) se establece en `EINVAL` y la función finaliza.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_CrtMemCheckpoint`|\<crtdbg.h\>, \<errno.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
 **Bibliotecas:** solo versiones de depuración de la UCRT.  
  
## Equivalente en .NET Framework  
 No disponible. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [\_CrtMemDifference](../../c-runtime-library/reference/crtmemdifference.md)