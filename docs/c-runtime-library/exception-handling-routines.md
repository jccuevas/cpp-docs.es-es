---
title: "Rutinas para el control de excepciones | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.exceptions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "control de excepciones, rutinas"
ms.assetid: f60548c6-850a-4e1e-a79b-a2a6a541ab62
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Rutinas para el control de excepciones
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Utilice las funciones de control de excepciones de C\+\+ para recuperarse de eventos inesperados durante la ejecución del programa.  
  
### Funciones de control de excepciones  
  
|Función|Utilice|Equivalente de .NET Framework|  
|-------------|-------------|-----------------------------------|  
|[\_set\_se\_translator](../c-runtime-library/reference/set-se-translator.md)|Controlar las excepciones Win32 \(excepciones estructuradas C\) como C\+\+ escrito excepciones|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[set\_terminate](../c-runtime-library/reference/set-terminate-crt.md)|Instale poseen la rutina de finalización que se denomine por `terminate`|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[set\_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|Instale por la función de finalización que se denomine por `unexpected`|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[terminate](../c-runtime-library/reference/terminate-crt.md)|Se llama automáticamente en determinadas circunstancias después de la excepción que se produce.  Las llamadas de función `abort` de `terminate` o una función especificada mediante `set_terminate`|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[unexpected](../c-runtime-library/reference/unexpected-crt.md)|Llamadas `terminate` o una función especificada mediante `set_unexpected`.  La función de `unexpected` no se utiliza en la implementación actual del control de excepciones de Microsoft C\+\+|[\<caps:sentence id\="tgt30" sentenceid\="ec8332f3bf55c7bd183338eca87744ec" class\="tgtSentence"\>Clase de System::Exception\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.exception.aspx)|  
  
## Vea también  
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)