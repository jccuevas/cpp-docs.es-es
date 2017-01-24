---
title: "_CrtGetAllocHook | Microsoft Docs"
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
  - "_CrtGetAllocHook"
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
  - "CrtGetAllocHook"
  - "_CrtGetAllocHook"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_CrtGetAllocHook (función)"
  - "CrtGetAllocHook (función)"
ms.assetid: 036acf7c-547a-4b3f-a636-80451070d7ed
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CrtGetAllocHook
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera la función actual de asignación definida por el cliente para enlazar con el proceso de asignación de memoria de depuración en tiempo de ejecución de C \(solo versión de depuración\).  
  
## Sintaxis  
  
```  
_CRT_ALLOC_HOOK _CrtGetAllocHook( void );  
```  
  
## Valor devuelto  
 Devuelve la función definida actualmente de enlace de asignación.  
  
## Comentarios  
 `_CrtGetAllocHook` recupera la función actual de enlace de la aplicación definida por el cliente para el proceso de asignación de memoria de biblioteca de depuración en tiempo de ejecución de C.  
  
 Para obtener más información sobre cómo usar otras funciones con capacidad de enlace en tiempo de ejecución y cómo escribir funciones de enlace definidas por el cliente, vea [Creación de funciones de enlace de depuración](../Topic/Debug%20Hook%20Function%20Writing.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_CrtGetAllocHook`|\<crtdbg.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Solo las versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [\_CrtSetAllocHook](../../c-runtime-library/reference/crtsetallochook.md)