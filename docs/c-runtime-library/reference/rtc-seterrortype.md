---
title: "_RTC_SetErrorType | Microsoft Docs"
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
  - "_RTC_SetErrorType"
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
  - "RTC_SetErrorType"
  - "_RTC_SetErrorType"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "errores en tiempo de ejecución"
  - "RTC_SetErrorType (función)"
  - "_RTC_SetErrorType (función)"
ms.assetid: f5f99be7-d357-4b11-b8f5-ddd3428f2b06
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _RTC_SetErrorType
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Asocia un error que se detecta mediante comprobaciones de errores en tiempo de ejecución \(RTC\) con un tipo. El controlador de errores procesa cómo mostrar los errores del tipo especificado.  
  
## Sintaxis  
  
```  
  
int _RTC_SetErrorType(  
   _RTC_ErrorNumber  
errnum  
,  
   int  
ErrType   
);  
  
```  
  
#### Parámetros  
 *errnum*  
 Un número entre cero y el valor devuelto por [\_RTC\_NumErrors](../../c-runtime-library/reference/rtc-numerrors.md) menos uno.  
  
 *ErrType*  
 Valor que se va a asignar a este elemento *errnum*. Por ejemplo, se podría usar **\_CRT\_ERROR**. Si está utilizando `_CrtDbgReport` como el controlador de errores *ErrType*  solo puede tener uno de los símbolos definidos en [\_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md). Si tiene su propio controlador de errores \([\_RTC\_SetErrorFunc](../../c-runtime-library/reference/rtc-seterrorfunc.md)\), puede disponer de tantos elementos *ErrType* como elementos *errnum* haya.  
  
 Un valor de *ErrType* de \_RTC\_ERRTYPE\_IGNORE tiene un significado especial para `_CrtSetReportMode`; se omite el error.  
  
## Valor devuelto  
 El valor anterior del tipo de error `type`.  
  
## Comentarios  
 De forma predeterminada, todos los errores se establecen en *ErrType* \= 1, que corresponde a **\_CRT\_ERROR**. Para más información sobre los tipos de errores predeterminados de tipos, como **\_CRT\_ERROR**, consulte [\_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).  
  
 Antes de poder llamar a esta función, primero debe llamar a una de las funciones de inicialización de comprobación de errores en tiempo de ejecución; vea [Uso de comprobaciones en tiempo de ejecución sin la biblioteca en tiempo de ejecución de C](../Topic/Using%20Run-Time%20Checks%20Without%20the%20C%20Run-Time%20Library.md)  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_RTC_SetErrorType`|\<rtcapi.h\>|  
  
 Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [\_RTC\_GetErrDesc](../../c-runtime-library/reference/rtc-geterrdesc.md)   
 [Comprobar errores en tiempo de ejecución](../../c-runtime-library/run-time-error-checking.md)