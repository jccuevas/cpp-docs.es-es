---
title: "runtime_checks | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.runtime_checks"
  - "runtime_checks_CPP"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "runtime_checks (pragma)"
  - "pragmas, runtime_checks"
ms.assetid: ae50b43f-f88d-47ad-a2db-3389e9e7df5b
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# runtime_checks
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Deshabilita o restaura la configuración de [\/RTC](../build/reference/rtc-run-time-error-checks.md).  
  
## Sintaxis  
  
```  
  
#pragma runtime_checks(  
"[runtime_checks]", {restore | off} )  
```  
  
## Comentarios  
 No se puede habilitar una comprobación en tiempo de ejecución que no se haya habilitado con una opción del compilador. Por ejemplo, si no se especifica \/RTC, especificar `#pragma runtime_checks( "s", restore)` no habilitará la comprobación del marco de pila.  
  
 La directiva pragma **runtime\_checks** debe aparecer fuera de una función y tiene efecto en la primera función definida después de que se vea la directiva pragma. Los argumentos **restore** y **off** activan o desactivan las opciones especificadas en *runtime\_checks*.  
  
 Los parámetros *runtime\_checks* pueden ser varios o ninguno de los mostrados en la tabla siguiente.  
  
### Parámetros de la directiva pragma runtime\_checks  
  
|Parámetros|Tipo de comprobación en tiempo de ejecución|  
|----------------|-------------------------------------------------|  
|**s**|Habilita la comprobación de pila \(marco\).|  
|**c**|Comunica los casos en que se asigna un valor a un tipo de datos más pequeño y se provoca una pérdida de datos.|  
|**u**|Comunica cuando se usa una variable antes de definirla.|  
  
 Son las mismas letras usadas con la opción del compilador \/RTC. Por ejemplo:  
  
```  
#pragma runtime_checks( "sc", restore )  
```  
  
 El uso de la directiva pragma **runtime\_checks** con la cadena vacía \(**""**\) es una forma especial de la directiva:  
  
-   Cuando se usa el parámetro **off**, desactiva las comprobaciones de errores en tiempo de ejecución, que se enumeran en la tabla anterior.  
  
-   Cuando se usa el parámetro **restore**, restablece las comprobaciones de errores en tiempo de ejecución a las especificadas con la opción del compilador \/RTC.  
  
```  
#pragma runtime_checks( "", off )  
.  
.  
.  
#pragma runtime_checks( "", restore )   
```  
  
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [RTC sample](http://msdn.microsoft.com/es-es/b3415b09-f6fd-43dc-8c02-9a910bc2574e)