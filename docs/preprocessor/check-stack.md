---
title: "check_stack | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.check_stack"
  - "check_stack_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "check_stack (pragma)"
  - "pragma (directivas), check_stack"
  - "pragma (directivas), check_stack (tabla de uso)"
ms.assetid: f18e20cc-9abb-48b7-ad62-8d384875b996
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# check_stack
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Indica al compilador que desactive las comprobaciones de la pila si se especifica **off** \(o **–**\), o que active las comprobaciones de la pila si se especifica **on** \(o **\+**\).  
  
## Sintaxis  
  
```  
  
      #pragma check_stack([ {on | off}] )  
#pragma check_stack{+ | –}  
```  
  
## Comentarios  
 Si no se especifica ningún argumento, las comprobaciones de la pila se tratan en la forma predeterminada.  Esta pragma surte efecto en la primera función que se define después de que aparezca la pragma.  Las comprobaciones de la pila no forman parte de las macros ni de las funciones insertadas que se generan.  
  
 Si no proporciona un argumento para la pragma **check\_stack**, la comprobación de pila revierte el comportamiento especificado en la línea de comandos.  Para obtener más información, vea [Referencia del compilador](../build/reference/compiler-options.md).  La interacción de **\#pragma check\_stack** y la opción [\/Gs](../build/reference/gs-control-stack-checking-calls.md) se resume en la tabla siguiente.  
  
### Utilización de la pragma check\_stack  
  
|Sintaxis|¿Se compila con<br /><br /> la opción \/Gs?|Acción|  
|--------------|-----------------------------------------|------------|  
|**\#pragma check\_stack\( \)** o<br /><br /> **\#pragma check\_stack**|Sí|Desactiva la comprobación de la pila para las funciones que la siguen|  
|**\#pragma check\_stack\( \)** o<br /><br /> **\#pragma check\_stack**|No|Activa la comprobación de la pila para las funciones que la siguen|  
|**\#pragma check\_stack\(on\)**<br /><br /> o **\#pragma check\_stack \+**|Sí o no|Activa la comprobación de la pila para las funciones que la siguen|  
|**\#pragma check\_stack\(off\)**<br /><br /> o **\#pragma check\_stack –**|Sí o no|Desactiva la comprobación de la pila para las funciones que la siguen|  
  
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)