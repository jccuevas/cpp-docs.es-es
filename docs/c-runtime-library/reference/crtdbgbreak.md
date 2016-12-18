---
title: "_CrtDbgBreak | Microsoft Docs"
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
  - "_CrtDbgBreak"
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
  - "_CrtDbgBreak"
  - "CrtDbgBreak"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_CrtDbgBreak (función)"
  - "CrtDbgBreak (función)"
ms.assetid: 01f8b4a2-a2c7-4e1f-9f39-e573b4a7871f
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CrtDbgBreak
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece un punto de interrupción en una línea de código determinada. \(Utilizado en modo de depuración sólo.\)  
  
## Sintaxis  
  
```  
void _CrtDbgBreak( void );  
```  
  
## Valor devuelto  
 No hay ningún valor devuelto.  
  
## Comentarios  
 La función de `_CrtDbgBreak` establece un punto de interrupción de depuración en la línea de código determinada donde se encuentra la función.  Esta función se utiliza en modo de depuración solamente y depende de `_DEBUG` que se definió anteriormente.  
  
 Para obtener más información sobre cómo usar otras funciones enlace\- capaces de runtime y escritura para formar funciones cliente\- definido de enlace, vea [Escritura de las propias funciones de enlace de depuración](../Topic/Debug%20Hook%20Function%20Writing.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_CrtDbgBreak`|\<CRTDBG.h\>|  
  
## Bibliotecas  
 Solo las versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [\_\_debugbreak](../../intrinsics/debugbreak.md)