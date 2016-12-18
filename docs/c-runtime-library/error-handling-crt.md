---
title: "Control de errores (CRT) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.errors"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "control de errores, rutinas de C para"
  - "control de errores, rutinas de biblioteca"
  - "errores lógicos"
  - "pruebas, para errores de programa"
ms.assetid: 125ac697-9eb0-4152-a440-b7842f23d97f
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Control de errores (CRT)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Utilice estas rutinas para controlar los errores de programa.  
  
### Rutinas de control de errores  
  
|Rutina|Utilice|Equivalente de .NET Framework|  
|------------|-------------|-----------------------------------|  
|macro de[validar](../c-runtime-library/reference/assert-macro-assert-wassert.md)|Prueba para errores lógicos programados; disponible en las versiones de lanzamiento y depuración de la biblioteca en tiempo de ejecución|[\<caps:sentence id\="tgt8" sentenceid\="14fd9bf776829d73028df00162f7533f" class\="tgtSentence"\>System::Diagnostics::Debug::Assert\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|macros de[\_ASSERT; \_ASSERTE](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)|Similar a `assert`, pero sólo está disponible en las versiones de depuración de la biblioteca en tiempo de ejecución|[\<caps:sentence id\="tgt11" sentenceid\="14fd9bf776829d73028df00162f7533f" class\="tgtSentence"\>System::Diagnostics::Debug::Assert\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|[clearerr](../c-runtime-library/reference/clearerr.md)|Mensaje de error de reinicio.  La llamada `rewind` o al cerrar una secuencia también restaura el indicador de error.|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_eof](../c-runtime-library/reference/eof.md)|Comprobación de final de archivo en E\/S de bajo nivel|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[feof](../c-runtime-library/reference/feof.md)|Prueba para el final del archivo.  Final del archivo también se indica cuándo `_read` devuelve 0.|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[ferror](../c-runtime-library/reference/ferror.md)|Prueba para los errores de E\/S de secuencia|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|macros de[\_RPT, \_RPTF](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)|Generar un informe similar a `printf`, pero sólo está disponible en las versiones de depuración de la biblioteca en tiempo de ejecución|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_set\_error\_mode](../c-runtime-library/reference/set-error-mode.md)|Modifica `__error_mode` para determinar la ubicación de no predeterminado donde el tiempo de ejecución de C escribe un mensaje de error para un error finalizar posiblemente el programa.||  
|[\_set\_purecall\_handler](../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md)|Establece el controlador para una llamada de función virtual pura.||  
  
## Vea también  
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)