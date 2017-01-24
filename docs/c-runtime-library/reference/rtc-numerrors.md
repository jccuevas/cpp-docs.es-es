---
title: "_RTC_NumErrors | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_RTC_NumErrors"
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
  - "_RTC_NumErrors"
  - "RTC_NumErrors"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "errores en tiempo de ejecución"
  - "_RTC_NumErrors (función)"
  - "RTC_NumErrors (función)"
ms.assetid: 7e82adae-38e2-4f8b-bc0b-37bda8109fd1
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _RTC_NumErrors
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve el número total de errores que se pueden detectar mediante las comprobaciones de errores en tiempo de ejecución \(RTC\). Puede utilizar este número como el control de un bucle **for**, donde cada valor del bucle se pasa a [\_RTC\_GetErrDesc](../../c-runtime-library/reference/rtc-geterrdesc.md).  
  
## Sintaxis  
  
```  
  
int _RTC_NumErrors( void );  
  
```  
  
## Valor devuelto  
 Un entero cuyo valor representa el número total de errores que se pueden detectar mediante las comprobaciones de errores en tiempo de ejecución de Visual C\+\+.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_RTC_NumErrors`|\<rtcapi.h\>|  
  
 Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [\_RTC\_GetErrDesc](../../c-runtime-library/reference/rtc-geterrdesc.md)   
 [Comprobar errores en tiempo de ejecución](../../c-runtime-library/run-time-error-checking.md)