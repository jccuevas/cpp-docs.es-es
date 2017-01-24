---
title: "_CrtGetDumpClient | Microsoft Docs"
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
  - "_CrtGetDumpClient"
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
  - "CrtGetDumpClient"
  - "_CrtGetDumpClient"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_CrtGetDumpClient (función)"
  - "CrtGetDumpClient (función)"
ms.assetid: 9051867f-341b-493b-b53d-45d2b454a3ad
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CrtGetDumpClient
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera la función actual definida por la aplicación para volcar los bloques de memoria de tipo `_CLIENT_BLOCK` \(solo versión de depuración\).  
  
## Sintaxis  
  
```  
_CRT_DUMP_CLIENT _CrtGetDumpClient( void );  
```  
  
## Valor devuelto  
 Devuelve la rutina de volcado actual.  
  
## Comentarios  
 La función `_CrtGetDumpClient` recupera la función actual de enlace para volcar los objetos almacenados en los bloques de memoria `_CLIENT_BLOCK` para el proceso de volcado de memoria de depuración en tiempo de ejecución de C.  
  
 Para obtener más información sobre cómo usar otras funciones con capacidad de enlace en tiempo de ejecución y cómo escribir funciones de enlace definidas por el cliente, vea [Creación de funciones de enlace de depuración](../Topic/Debug%20Hook%20Function%20Writing.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_CrtGetDumpClient`|\<crtdbg.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Solo las versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [\_CrtReportBlockType](../../c-runtime-library/reference/crtreportblocktype.md)   
 [\_CrtSetDumpClient](../../c-runtime-library/reference/crtsetdumpclient.md)