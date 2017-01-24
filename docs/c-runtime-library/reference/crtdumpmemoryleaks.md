---
title: "_CrtDumpMemoryLeaks | Microsoft Docs"
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
  - "_CrtDumpMemoryLeaks"
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
  - "CRTDBG_LEAK_CHECK_DF"
  - "CRTDBG_CHECK_CRT_DF"
  - "_CRTDBG_LEAK_CHECK_DF"
  - "CrtDumpMemoryLeaks"
  - "_CrtDumpMemoryLeaks"
  - "_CRTDBG_CHECK_CRT_DF"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "CrtDumpMemoryLeaks (función)"
  - "CRTDBG_LEAK_CHECK_DF (macro)"
  - "_CRTDBG_LEAK_CHECK_DF (macro)"
  - "_CrtDumpMemoryLeaks (función)"
  - "CRTDBG_CHECK_CRT_DF (macro)"
  - "_CRTDBG_CHECK_CRT_DF (macro)"
ms.assetid: 71b2eab4-7f55-44e8-a55a-bfea4f32d34c
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CrtDumpMemoryLeaks
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Vuelca todos los bloques de memoria del montón de depuración cuando se ha producido una pérdida de memoria \(solo versión de depuración\).  
  
## Sintaxis  
  
```  
  
int _CrtDumpMemoryLeaks( void );  
```  
  
## Valor devuelto  
 `_CrtDumpMemoryLeaks` devuelve TRUE si se encuentra una pérdida de memoria.  De lo contrario, la función devuelve el FALSE.  
  
## Comentarios  
 La función `_CrtDumpMemoryLeaks` determina si se ha producido una pérdida de memoria desde que se inició la ejecución del programa.  Cuando se encuentra una pérdida, la información de encabezado de depuración de todos los objetos del montón se vuelca en un formato legible para usuario.  Cuando no se define [\_DEBUG](../../c-runtime-library/debug.md), las llamadas a `_CrtDumpMemoryLeaks` se quitan durante el preprocesamiento.  
  
 A menudo, se llama a `_CrtDumpMemoryLeaks` al final de la ejecución del programa para comprobar que se ha liberado toda la memoria asignada por la aplicación.  Se puede llamar a la función automáticamente cuando finaliza el programa activando el campo de bits `_CRTDBG_LEAK_CHECK_DF` de la marca [\_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) mediante la función [\_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md).  
  
 `_CrtDumpMemoryLeaks` llama a [\_CrtMemCheckpoint](../../c-runtime-library/reference/crtmemcheckpoint.md) para obtener el estado actual del montón y, a continuación, examina el estado para detectar bloques que no se han liberado.  Cuando se encuentra un bloque no liberado, `_CrtDumpMemoryLeaks` llama a [\_CrtMemDumpAllObjectsSince](../../c-runtime-library/reference/crtmemdumpallobjectssince.md) para volcar la información de todos los objetos asignados en el montón desde que se inició la ejecución del programa.  
  
 De forma predeterminada, los bloques internos en tiempo de ejecución de C \(`_CRT_BLOCK`\) no se incluyen en las operaciones de volcado de la memoria.  La función [\_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md) se puede usar para activar el bit `_CRTDBG_CHECK_CRT_DF` de `_crtDbgFlag` y así incluir estos bloques en el proceso de detección de pérdidas.  
  
 Para obtener más información sobre las funciones de estado del montón y la estructura de `_CrtMemState`, vea [Funciones que indican el estado del montón](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Heap_State_Reporting_Functions).  Para obtener más información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [Detalles del montón de depuración de CRT](../Topic/CRT%20Debug%20Heap%20Details.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_CrtDumpMemoryLeaks`|\<crtdbg.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Solo las versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
 Para obtener un ejemplo de cómo usar `_CrtDumpMemoryLeaks`, vea [crt\_dbg1](http://msdn.microsoft.com/es-es/17b4b20c-e849-48f5-8eb5-dca6509cbaf9).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)