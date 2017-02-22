---
title: "_RTC_SetErrorFuncW | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_RTC_SetErrorFuncW"
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
  - "_RTC_SetErrorFuncW"
  - "RTC_SetErrorFuncW"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "errores en tiempo de ejecución"
  - "RTC_SetErrorFuncW (función)"
  - "_RTC_error_fnW (typedef)"
  - "_RTC_SetErrorFuncW (función)"
  - "RTC_error_fnW (typedef)"
ms.assetid: b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _RTC_SetErrorFuncW
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Designa una función como el controlador de la notificación de comprobaciones de errores en tiempo de ejecución \(RTC\).  
  
## Sintaxis  
  
```  
  
_RTC_error_fnW _RTC_SetErrorFuncW(  
   _RTC_error_fnW  
 function   
);  
  
```  
  
#### Parámetros  
 `function`  
 La dirección de la función que controlará las comprobaciones de errores en tiempo de ejecución.  
  
## Valor devuelto  
 La función de error definida previamente o `NULL` si no hay ninguna función definida con anterioridad.  
  
## Comentarios  
 En el nuevo código, utilice solo `_RTC_SetErrorFuncW`.`_RTC_SetErrorFunc` solo se incluye en la biblioteca para una compatibilidad con versiones anteriores.  
  
 La devolución de llamada `_RTC_SetErrorFuncW` se aplica solo al componente en el que estaba vinculado, pero no de forma global.  
  
 Asegúrese de que la dirección que pasa a `_RTC_SetErrorFuncW` es la de una función de control de errores válida.  
  
 Si se asignó un tipo de –1 a un error mediante [\_RTC\_SetErrorType](../../c-runtime-library/reference/rtc-seterrortype.md), no se llama a la función de control de errores.  
  
 Antes de poder llamar a esta función, primero debe llamar a una de las funciones de inicialización de la comprobación de errores en tiempo de ejecución. Para obtener más información, consulta [Utilizar comprobaciones en tiempo de ejecución sin la biblioteca en tiempo de ejecución de C](../Topic/Using%20Run-Time%20Checks%20Without%20the%20C%20Run-Time%20Library.md).  
  
 **\_RTC\_error\_fnW** se define como se indica a continuación:  
  
 **typedef int \(\_\_cdecl \*\_RTC\_error\_fnW\)\(int**  `errorType` **, const wchar\_t \*** *filename* **, int**  *linenumber* **, const wchar\_t \*** `moduleName` **, const wchar\_t \*** *format* **, ...\);**  
  
 donde:  
  
 `errorType`  
 El tipo de error que especifica [\_RTC\_SetErrorType](../../c-runtime-library/reference/rtc-seterrortype.md).  
  
 *filename*  
 El archivo de origen donde se produjo el error, o null si no hay información de depuración.  
  
 *linenumber*  
 La línea de *filename* donde se produjo el error, o 0 si no hay información de depuración disponible.  
  
 `moduleName`  
 El nombre del archivo DLL o del ejecutable en el que se produjo el error.  
  
 *format*  
 cadena de estilo printf para mostrar un mensaje de error, usando los parámetros restantes. El primer argumento de VA\_ARGLIST es el número de errores de RTC que se produjeron.  
  
 Para ver un ejemplo en el que se muestra cómo usar **\_RTC\_error\_fnW**, consulte [Personalización de las comprobaciones nativas en tiempo de ejecución](../Topic/Native%20Run-Time%20Checks%20Customization.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_RTC_SetErrorFuncW`|\<rtcapi.h\>|  
  
 Para obtener más información, consulta [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [\_CrtDbgReport, \_CrtDbgReportW](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)   
 [Comprobar errores en tiempo de ejecución](../../c-runtime-library/run-time-error-checking.md)