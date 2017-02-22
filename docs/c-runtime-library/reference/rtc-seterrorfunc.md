---
title: "_RTC_SetErrorFunc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_RTC_SetErrorFunc"
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
  - "RTC_SetErrorFunc"
  - "_RTC_SetErrorFunc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RTC_SetErrorFunc (función)"
  - "_RTC_SetErrorFunc (función)"
ms.assetid: b2292722-0d83-4092-83df-3d5b19880666
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# _RTC_SetErrorFunc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Designa una función como el controlador para notificar comprobaciones de errores en tiempo de ejecución \(RTC\). Esta función está en desuso; use `_RTC_SetErrorFuncW` en su lugar.  
  
## Sintaxis  
  
```  
  
_RTC_error_fn _RTC_SetErrorFunc(  
   _RTC_error_fn  
 function   
);  
  
```  
  
#### Parámetros  
 *función*  
 La dirección de la función que controlará las comprobaciones de errores en tiempo de ejecución.  
  
## Valor devuelto  
 La función de error definida previamente. Si no hay ninguna función definida previamente, devuelve NULL.  
  
## Comentarios  
 No utilice esta función; en su lugar, utilice `_RTC_SetErrorFuncW`. Se conserva solo por motivos de compatibilidad con versiones anteriores.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_RTC_SetErrorFunc`|\<rtcapi.h\>|  
  
 Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [\_CrtDbgReport, \_CrtDbgReportW](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)   
 [Comprobar errores en tiempo de ejecución](../../c-runtime-library/run-time-error-checking.md)