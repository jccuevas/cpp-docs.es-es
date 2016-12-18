---
title: "_CrtMemDifference | Microsoft Docs"
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
  - "_CrtMemDifference"
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
  - "_CrtMemDifference"
  - "CrtMemDifference"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "CrtMemDifference (función)"
  - "_CrtMemDifference (función)"
ms.assetid: 0f327278-b551-482f-958b-76941f796ba4
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CrtMemDifference
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Compara dos estados de memoria y devuelve sus diferencias \(solo versión de depuración\).  
  
## Sintaxis  
  
```  
int _CrtMemDifference(   
   _CrtMemState *stateDiff,  
   const _CrtMemState *oldState,  
   const _CrtMemState *newState   
);  
```  
  
#### Parámetros  
 `stateDiff`  
 Puntero a una estructura de `_CrtMemState` que se usa para almacenar las diferencias entre los dos estados de memoria \(devueltas\).  
  
 `oldState`  
 Puntero a un estado de memoria anterior \(estructura de `_CrtMemState`\).  
  
 `newState`  
 Puntero a un estado de memoria posterior \(estructura de `_CrtMemState`\).  
  
## Valor devuelto  
 Si los estados de memoria son significativamente distintos, `_CrtMemDifference` devuelve TRUE. De lo contrario, la función devuelve el FALSE.  
  
## Comentarios  
 La función `_CrtMemDifference` compara `oldState` y `newState`, y almacena sus diferencias en `stateDiff`, que la aplicación puede usar para detectar pérdidas y otros problemas de memoria. Cuando [\_DEBUG](../../c-runtime-library/debug.md) no se define, las llamadas a `_CrtMemDifference` se quitan durante el preprocesamiento.  
  
 Tanto `newState` como `oldState` deben ser punteros válidos a una estructura de `_CrtMemState`, definida en Crtdbg.h, que [\_CrtMemCheckpoint](../../c-runtime-library/reference/crtmemcheckpoint.md) ha llenado antes de llamar a `_CrtMemDifference`.`stateDiff` debe ser un puntero a una instancia asignada previamente de la estructura de `_CrtMemState`. Si `stateDiff`, `newState` o `oldState` es `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) se establece en `EINVAL` y la función devuelve FALSE.  
  
 `_CrtMemDifference` compara los valores de campo de `_CrtMemState` de los bloques de `oldState` con los de `newState`, y almacena el resultado en `stateDiff`. Cuando el número de tipos de bloque asignados o el número total de bloques asignados para cada tipo no es igual en los dos estados de memoria, los estados se consideran significativamente diferentes. La diferencia entre la mayor cantidad que se haya asignado en algún momento simultáneamente a los dos estados y la diferencia entre las asignaciones totales a los dos estados también se almacenan en `stateDiff`.  
  
 De forma predeterminada, los bloques internos en tiempo de ejecución de C \(`_CRT_BLOCK`\) no se incluyen en las operaciones de estado de la memoria. La función [\_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md) se puede usar para activar el bit `_CRTDBG_CHECK_CRT_DF` de `_crtDbgFlag` y así incluir estos bloques en la detección de pérdidas y otras operaciones de estado de la memoria. Los bloques de memoria liberados \(`_FREE_BLOCK`\) no hacen que `_CrtMemDifference` devuelva TRUE.  
  
 Para más información sobre las funciones de estado del montón y la estructura `_CrtMemState`, vea [Heap State Reporting Functions](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Heap_State_Reporting_Functions). Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [Detalles del montón de depuración de CRT](../Topic/CRT%20Debug%20Heap%20Details.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_CrtMemDifference`|\<crtdbg.h\>|\<errno.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
 **Bibliotecas:** solo versiones de depuración de [Características de la biblioteca CRT](../../c-runtime-library/crt-library-features.md).  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [\_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)