---
title: "_CrtGetReportHook | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtGetReportHook"
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
  - "CrtGetReportHook"
  - "_CrtGetReportHook"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CrtGetReportHook (función)"
  - "_CrtGetReportHook (función)"
ms.assetid: 922758ed-7edd-4359-9c92-0535192dc11a
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _CrtGetReportHook
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera la función de creación de informes definida por el usuario para enlazarla al tiempo de ejecución de C para el proceso de creación de informes de depuración \(solo versión de depuración\).  
  
## Sintaxis  
  
```  
_CRT_REPORT_HOOK _CrtGetReportHook( void );  
```  
  
## Valor devuelto  
 Devuelve la función actual de creación de informes definida por el cliente.  
  
## Comentarios  
 `_CrtGetReportHook` permite que una aplicación recupere la función actual de creación de informes para el proceso de creación de informes de la biblioteca de depuración en tiempo de ejecución de C.  
  
 Para obtener más información sobre cómo usar otras funciones con capacidad de enlace en tiempo de ejecución y cómo escribir funciones de enlace definidas por el cliente, vea [Creación de funciones de enlace de depuración](../Topic/Debug%20Hook%20Function%20Writing.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_CrtGetReportHook`|\<crtdbg.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Solo las versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
 Para obtener un ejemplo de cómo usar `_CrtSetReportHook`, vea [report](http://msdn.microsoft.com/es-es/f6e08c30-6bd9-459a-830a-56deec0d2051).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [\_CrtSetReportHook](../../c-runtime-library/reference/crtsetreporthook.md)