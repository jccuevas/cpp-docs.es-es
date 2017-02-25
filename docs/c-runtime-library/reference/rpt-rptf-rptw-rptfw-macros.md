---
title: "_RPT, _RPTF, _RPTW, _RPTFW (Macros) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
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
  - "RPT3"
  - "RPTF4"
  - "_RPT4"
  - "RPT1"
  - "_RPTF0"
  - "RPTF3"
  - "_RPTF4"
  - "RPTF1"
  - "RPT4"
  - "_RPT1"
  - "_RPT0"
  - "RPT0"
  - "_RPTF2"
  - "RPTF0"
  - "_RPT3"
  - "_RPT2"
  - "_RPTF3"
  - "RPT2"
  - "_RPTF1"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "depurar [CRT], usar macros"
  - "_RPTW3 (macro)"
  - "_RPT0 (macro)"
  - "RPTW4 (macro)"
  - "_RPTF3 (macro)"
  - "_RPTW4 (macro)"
  - "RPTF4 (macro)"
  - "RPTFW2 (macro)"
  - "RPTW (macros)"
  - "RPT1 (macro)"
  - "_RPTF (macros)"
  - "RPTFW3 (macro)"
  - "_RPTW0 (macro)"
  - "_RPTF0 (macro)"
  - "macros, depurar con"
  - "_RPTW2 (macro)"
  - "RPTF3 (macro)"
  - "RPT3 (macro)"
  - "RPT0 (macro)"
  - "_RPT (macros)"
  - "RPTW3 (macro)"
  - "_RPTFW (macros)"
  - "macros de informes de depuración"
  - "RPTF (macros)"
  - "RPT (macros)"
  - "_RPTW (macros)"
  - "RPTF2 (macro)"
  - "_RPTF1 (macro)"
  - "_RPT1 (macro)"
  - "_RPT4 (macro)"
  - "_RPTFW2 (macro)"
  - "_RPTFW1 (macro)"
  - "RPTF0 (macro)"
  - "_RPT2 (macro)"
  - "RPTFW (macros)"
  - "_RPTW1 (macro)"
  - "_RPTFW0 (macro)"
  - "RPT4 (macro)"
  - "_RPT3 (macro)"
  - "_RPTFW3 (macro)"
  - "_RPTF4 (macro)"
  - "_RPTFW4 (macro)"
  - "_RPTF2 (macro)"
  - "RPTW0 (macro)"
  - "RPTFW4 (macro)"
  - "RPTFW0 (macro)"
  - "RPTW2 (macro)"
  - "RPTF1 (macro)"
  - "RPT2 (macro)"
  - "RPTFW1 (macro)"
  - "RPTW1 (macro)"
ms.assetid: a5bf8b30-57f7-4971-8030-e773b7a1ae13
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# _RPT, _RPTF, _RPTW, _RPTFW (Macros)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Realiza el seguimiento del progreso de una aplicación genera un informe de depuración \(versión de depuración solo\).  Observe que *n* especifica el número de argumentos en `args` y puede ser 0, 1, 2, 3, 4, 5.  
  
## Sintaxis  
  
```  
  
      _RPT  
      n  
      (  
   reportType,  
   format,  
...[args]  
);  
_RPTFn(  
   reportType,  
   format,  
   [args]  
);  
_RPTWn(  
   reportType,  
   format   
   [args]  
);  
_RPTFWn(  
   reportType,  
   format   
   [args]  
);  
```  
  
#### Parámetros  
 `reportType`  
 Informe tipo: `_CRT_WARN`, `_CRT_ERROR`, o `_CRT_ASSERT`.  
  
 `format`  
 Cadena de la Formato\- CONTROL utilizada para crear el mensaje de usuario.  
  
 `args`  
 Argumentos de sustitución utilizados por `format`.  
  
## Comentarios  
 Todas estas macros toman los parámetrosde `reportType`yde `format`.  Además, también aceptan hasta cuatro argumentos adicionales, significados por el número anexado al nombre de la macro.  Por ejemplo, `_RPT0` y `_RPTF0` no toman ningún argumento adicional, `_RPT1` y `_RPTF1` toma `arg1`, `_RPT2` y `_RPTF2` toma `arg1` y `arg2`, etc.  
  
 Las macros de `_RPT` y de `_RPTF` son similares a la función de [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) , porque se pueden utilizar para seguir el progreso de una aplicación durante el proceso de depuración.  Sin embargo, estas macros son más flexibles que `printf` porque no es necesario encerrar en las instrucciones de `#ifdef` para evitar que se muestran en una compilación comercial de una aplicación.  Esta flexibilidad se logra mediante la macro de [\_DEBUG](../../c-runtime-library/debug.md) ; las macros de `_RPT` y de `_RPTF` sólo están disponibles cuando se define la marca de `_DEBUG` .  Cuando `_DEBUG` no está definido, las llamadas a estas macros se quitan durante el preprocesamiento.  
  
 Las macros de `_RPTW` y de `_RPTFW` son versiones de caracteres anchos de estas macros.  Son los `wprintf` y tome las cadenas de caracteres como argumentos.  
  
 Las macros de `_RPT` llaman a la función de [\_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) para generar un informe de depuración con un mensaje de usuario.  Las macros de `_RPTW` llaman a la función de `_CrtDbgReportW` para generar el mismo informe con los caracteres anchos.  Las macros de `_RPTF` y de `_RPTFW` crean un informe de depuración con el archivo de código fuente y el número de línea donde la macro de informe se llamó, además del mensaje de usuario.  El mensaje de usuario crea sustituyendo los argumentos de `arg`\[*n*\] en la cadena de `format` , utilizando las mismas reglas definidas por la función de [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) .  
  
 `_CrtDbgReport` o `_CrtDbgReportW` genera el informe de depuración y determina los destinos basándose en los modos de informe y el archivo actuales definidos para `reportType`.  Las funciones de [\_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) y de [\_CrtSetReportFile](../../c-runtime-library/reference/crtsetreportfile.md) se utilizan para definir los destinos para cada tipo de informe.  
  
 Si se llama a una macro de `_RPT` y no se ha llamado a `_CrtSetReportMode` ni `_CrtSetReportFile` , los mensajes se muestran como sigue.  
  
|Tipo de informe|Destino de salida|  
|---------------------|-----------------------|  
|`_CRT_WARN`|El texto de advertencia no se muestra.|  
|`_CRT_ERROR`|Una ventana emergente.  Igual que si `_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_WNDW);` se hubiera especificado.|  
|`_CRT_ASSERT`|Igual que `_CRT_ERROR`.|  
  
 Cuando el destino es una ventana de mensajes de depuración y el usuario elija el botón de **Reintentar** , `_CrtDbgReport` o `_CrtDbgReportW` devuelve 1, haciendo que estas macros enciendan el depurador, siempre que está habilitada la depuración just\-in\-time de \(JIT\).  Para obtener más información sobre cómo utilizar estas macros como mecanismo de control de errores de la depuración, vea [Utilizando las macros para comprobación e informes](../Topic/Macros%20for%20Reporting.md).  
  
 Otras dos macros existen que generan un informe de depuración.  La macro de [\_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) genera un informe, pero únicamente cuando el argumento de la expresión se evalúa como FALSE.  [\_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) es exactamente igual `_ASSERT`, pero incluye la expresión incorrectos en el informe generado.  
  
## Requisitos  
  
|Macro|Encabezado necesario|  
|-----------|--------------------------|  
|macros de`_RPT`|\<crtdbg.h\>|  
|macros de`_RPTF`|\<crtdbg.h\>|  
|macros de`_RPTW`|\<crtdbg.h\>|  
|macros de`_RPTFW`|\<crtdbg.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Solo las versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
 Aunque se trata de macros y son obtenidas incluye Crtdbg.h, la aplicación debe vincularse a una de las bibliotecas de depuración porque estas macros llaman a otras funciones en tiempo de ejecución.  
  
## Ejemplo  
 Vea el ejemplo del tema de [\_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) .  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)