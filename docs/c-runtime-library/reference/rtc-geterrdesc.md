---
title: "_RTC_GetErrDesc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_RTC_GetErrDesc"
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
  - "RTC_GetErrDesc"
  - "_RTC_GetErrDesc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "errores en tiempo de ejecución"
  - "_RTC_GetErrDesc (función)"
  - "RTC_GetErrDesc (función)"
ms.assetid: 7994ec2b-5488-4fd4-806d-a166c9a9f927
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _RTC_GetErrDesc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve una breve descripción de un tipo de comprobación de error en tiempo de ejecución \(RTC\).  
  
## Sintaxis  
  
```  
  
const char * _RTC_GetErrDesc(  
   _RTC_ErrorNumber   
errnum  
);  
  
```  
  
#### Parámetros  
 *errnum*  
 Un número entre cero y el valor devuelto por `_RTC_NumErrors` menos uno.  
  
## Valor devuelto  
 Una cadena de caracteres que contiene una descripción breve de uno de los tipos de error que detectó el sistema de comprobación de errores en tiempo de ejecución. Si el error es menor que cero o mayor o igual que el valor devuelto por [\_RTC\_NumErrors](../../c-runtime-library/reference/rtc-numerrors.md), `_RTC_GetErrDesc` devuelve NULL.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_RTC_GetErrDesc`|\<rtcapi.h\>|  
  
 Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [\_RTC\_NumErrors](../../c-runtime-library/reference/rtc-numerrors.md)   
 [Comprobar errores en tiempo de ejecución](../../c-runtime-library/run-time-error-checking.md)