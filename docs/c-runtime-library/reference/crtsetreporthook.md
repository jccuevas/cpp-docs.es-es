---
title: "_CrtSetReportHook | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtSetReportHook"
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
  - "_CrtSetReportHook"
  - "CrtSetReportHook"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CrtSetReportHook (función)"
  - "_CrtSetReportHook (función)"
ms.assetid: 1ae7c64f-8c84-4797-9574-b59f00f7a509
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# _CrtSetReportHook
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Instala una función de generación de informes definida por el cliente enlazándola al proceso de creación de informes de depuración en tiempo de ejecución de C \(solo versión de depuración\).  
  
## Sintaxis  
  
```  
_CRT_REPORT_HOOK _CrtSetReportHook(   
   _CRT_REPORT_HOOK reportHook   
);  
```  
  
#### Parámetros  
 `reportHook`  
 Nueva función de creación de informes definida por el cliente que se va a enlazar al proceso de creación de informes de depuración en tiempo de ejecución de C.  
  
## Valor devuelto  
 Devuelve la función de creación de informes definida por el cliente anterior.  
  
## Comentarios  
 `_CrtSetReportHook` permite que una aplicación use su propia función de creación de informes en el proceso de creación de informes de la biblioteca de depuración en tiempo de ejecución de C.  Por tanto, siempre que se llama a [\_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) para generar un informe de depuración, primero se llama a la función de creación de informes de la aplicación.  Esta funcionalidad permite que una aplicación realice operaciones como el filtrado de informes de depuración, de modo que se pueda centrar en determinados tipos de asignación o enviar un informe a destinos no disponibles mediante `_CrtDbgReport`.  Cuando no se define [\_DEBUG](../../c-runtime-library/debug.md), las llamadas a `_CrtSetReportHook` se quitan durante el preprocesamiento.  
  
 Para obtener una versión más sólida de `_CrtSetReportHook`, vea [\_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md).  
  
 La función `_CrtSetReportHook` instala la nueva función de creación de informes definida por el cliente especificada en `reportHook` y devuelve el enlace definido por el cliente anterior.  En el ejemplo siguiente se muestra cómo se deben crear prototipos de un enlace de informe definido por el cliente:  
  
```  
int YourReportHook( int reportType, char *message, int *returnValue );  
```  
  
 donde `reportType` es el tipo de informe de depuración \(`_CRT_WARN`, `_CRT_ERROR` o `_CRT_ASSERT`\), `message` es el mensaje totalmente ensamblado de usuario de depuración que se debe incluir en el informe, y `returnValue` es el valor especificado por la función de creación de informes definida por el cliente que `_CrtDbgReport` debe devolver.  Para obtener una descripción completa de los tipos de informe disponibles, vea la función [\_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md).  
  
 Si la función de creación de informes definida por el cliente controla completamente el mensaje de depuración para que no sea necesario ningún otro informe, la función debe devolver `TRUE`.  Cuando la función devuelve `FALSE`, se llama a `_CrtDbgReport` para generar el informe de depuración mediante la configuración actual de tipo, modo y archivo de informe.  Además, si se especifica el valor devuelto por `_CrtDbgReport` en `returnValue`, la aplicación también puede controlar si se produce una interrupción de depuración.  Para obtener una descripción completa de cómo se configura y genera el informe de depuración, vea `_CrtSetReportMode`, [\_CrtSetReportFile](../../c-runtime-library/reference/crtsetreportfile.md) y `_CrtDbgReport`.  
  
 Para obtener más información sobre cómo usar otras funciones con capacidad de enlace en tiempo de ejecución y cómo escribir funciones de enlace definidas por el cliente, vea [Creación de funciones de enlace de depuración](../Topic/Debug%20Hook%20Function%20Writing.md).  
  
> [!NOTE]
>  Si la aplicación se compila con `/clr` y se llama a la función de creación de informes una vez que la aplicación se ha cerrado, CLR inicia una excepción si la función de creación de informes llama a cualquier función de CRT.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_CrtSetReportHook`|\<crtdbg.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Solo las versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [\_CrtGetReportHook](../../c-runtime-library/reference/crtgetreporthook.md)