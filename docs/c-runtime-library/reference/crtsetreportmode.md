---
title: "_CrtSetReportMode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtSetReportMode"
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
  - "_CrtSetReportMode"
  - "CrtSetReportMode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CrtSetReportMode (función)"
  - "CrtSetReportMode (función)"
ms.assetid: 3ecc6a12-afdd-4242-b046-8187ff6d4b36
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _CrtSetReportMode
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica el destino de un tipo de informe específico generado por `_CrtDbgReport` y cualquier macro que llame a [\_CrtDbgReport, \_CrtDbgReportW](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md), por ejemplo [\_ASSERT, \_ASSERTE, \_ASSERT\_EXPR \(macros\)](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md), [\_ASSERT, \_ASSERTE, \_ASSERT\_EXPR \(macros\)](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md), [\_RPT, \_RPTF, \_RPTW, \_RPTFW \(Macros\)](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) y [\_RPT, \_RPTF, \_RPTW, \_RPTFW \(Macros\)](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) \(solo versión de depuración\).  
  
## Sintaxis  
  
```  
int _CrtSetReportMode(   
   int reportType,  
   int reportMode   
);  
```  
  
#### Parámetros  
 `reportType`  
 Tipo de informe: `_CRT_WARN`, `_CRT_ERROR` y `_CRT_ASSERT`.  
  
 `reportMode`  
 Nuevo modo de informe para `reportType`.  
  
## Valor devuelto  
 Cuando se finaliza correctamente, `_CrtSetReportMode` devuelve el modo de informe anterior para el tipo de informe especificado en `reportType`.  Si se pasa un valor no válido como `reportType` o se especifica un modo no válido para `reportMode`, `_CrtSetReportMode` invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, esta función establece `errno` en `EINVAL` y devuelve \-1.  Para obtener más información, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 `_CrtSetReportMode` especifica el destino de salida para `_CrtDbgReport`.  Dado que las macros `_ASSERT`, `_ASSERTE`, `_RPT` y `_CrtDbgReport` llaman a `_CrtSetReportMode`, `_RPTF` especifica el destino de salida de texto especificado con las macros.  
  
 Cuando [\_DEBUG](../../c-runtime-library/debug.md) no se define, las llamadas a `_CrtSetReportMode` se quitan durante el preprocesamiento.  
  
 Si no llama a `_CrtSetReportMode` para definir el destino de salida de los mensajes, los valores predeterminados siguientes son los activos:  
  
-   Los errores de aserción y los demás errores se dirigen a una ventana de mensajes de depuración.  
  
-   Las advertencias de las aplicaciones se Windows se envían a la ventana de salida del depurador.  
  
-   Las advertencias de las aplicaciones de consola no se muestran.  
  
 En la tabla siguiente se enumeran los tipos de informe definidos en Crtdbg.h.  
  
|Tipo de informe|Descripción|  
|---------------------|-----------------|  
|`_CRT_WARN`|Advertencias, mensajes e información que no requieren atención inmediata.|  
|`_CRT_ERROR`|Errores, problemas irrecuperables y problemas que requieren atención inmediata.|  
|`_CRT_ASSERT`|Errores de aserción \(expresiones declaradas que se evalúan como `FALSE`\).|  
  
 La función `_CrtSetReportMode` asigna el nuevo modo de informe especificado en `reportMode` al tipo de informe especificado en `reportType` y devuelve el modo de informe previamente definido para `reportType`.  En la tabla siguiente se enumeran las opciones disponibles para `reportMode` y el comportamiento resultante de `_CrtDbgReport`.  Estas opciones se definen como marcas de bits en Crtdbg.h.  
  
|Modo de informe|Comportamiento de \_CrtDbgReport|  
|---------------------|--------------------------------------|  
|`_CRTDBG_MODE_DEBUG`|Escribe el mensaje en la ventana de salida del depurador.|  
|`_CRTDBG_MODE_FILE`|Escribe el mensaje en un identificador de archivos proporcionado por el usuario.  Es necesario llamar a [\_CrtSetReportFile](../../c-runtime-library/reference/crtsetreportfile.md) para definir el archivo o flujo concreto que se debe usar como destino.|  
|`_CRTDBG_MODE_WNDW`|Crea un cuadro de mensaje para mostrar el mensaje junto con los botones `Abort`, `Retry` e `Ignore`.|  
|`_CRTDBG_REPORT_MODE`|Devuelve `reportMode` correspondiente al objeto `reportType` especificado:<br /><br /> 1   `_CRTDBG_MODE_FILE`<br /><br /> 2   `_CRTDBG_MODE_DEBUG`<br /><br /> 4   `_CRTDBG_MODE_WNDW`|  
  
 Cada tipo de informe se puede designar mediante uno, dos o tres modos, o sin ningún modo.  Por consiguiente, es posible tener más de un destino definido para un único tipo de informe.  Por ejemplo, el fragmento de código siguiente hace que se envíen errores de aserción a una ventana de mensajes de depuración y a `stderr`:  
  
```  
_CrtSetReportMode( _CRT_ASSERT, _CRTDBG_MODE_FILE | _CRTDBG_MODE_WNDW );  
_CrtSetReportFile( _CRT_ASSERT, _CRTDBG_FILE_STDERR );  
```  
  
 Además, el modo o los modos de informe de cada tipo de informe se pueden controlar por separado.  Por ejemplo, se puede especificar que el `reportType` de `_CRT_WARN` se envíe a una cadena de depuración de salida, y que `_CRT_ASSERT` se muestre en una ventana de mensajes de depuración y se envíe a `stderr`, como ya se ha mostrado.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_CrtSetReportMode`|\<crtdbg.h\>|\<errno.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
 **Bibliotecas:** solo versiones de depuración de [Características de la biblioteca CRT](../../c-runtime-library/crt-library-features.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)