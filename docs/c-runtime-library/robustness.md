---
title: "Solidez | Microsoft Docs"
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
  - "c.runtime"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "solidez [CRT]"
ms.assetid: 7f1a87f8-eff9-4b76-ae9b-d133d3de6adf
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Solidez
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Use las siguientes funciones de la biblioteca en tiempo de ejecución de C para mejorar la solidez del programa.  
  
### Funciones de solidez en tiempo de ejecución  
  
|Función|Uso|Equivalente de .NET Framework|  
|-------------|---------|-----------------------------------|  
|[\_set\_new\_handler](../c-runtime-library/reference/set-new-handler.md)|Transfiere el control al mecanismo de control de errores si el operador `new` no puede asignar memoria.|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_set\_se\_translator](../c-runtime-library/reference/set-se-translator.md)|Controla las excepciones Win32 \(excepciones estructuradas de C\) como con excepciones con tipo de C\+\+.|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[set\_terminate](../c-runtime-library/reference/set-terminate-crt.md)|Instala la función de finalización a la que debe llamar [terminate](../c-runtime-library/reference/terminate-crt.md).|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[set\_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|Instala la función de finalización a la que debe llamar [unexpected](../c-runtime-library/reference/unexpected-crt.md).|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
  
## Vea también  
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)   
 [SetUnhandledExceptionFilter](http://msdn.microsoft.com/library/windows/desktop/ms680634.aspx)