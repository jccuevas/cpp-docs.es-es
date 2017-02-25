---
title: "&lt;limits&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.<limits>"
  - "std::<limits>"
  - "limits/std::<limits>"
  - "<limits>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "limits (encabezado)"
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# &lt;limits&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define la clase de plantilla `numeric_limits` y dos enumeraciones relativas a las representaciones de punto flotante y el redondeo.  
  
## Sintaxis  
  
```  
  
#include <limits>  
  
```  
  
## Comentarios  
 Las especializaciones explícitas de la clase `numeric_limits` describen muchas propiedades de los tipos fundamentales, incluidos los tipos de carácter, entero y punto flotante y los `bool` que están definidos por la implementación en lugar de estar fijados por las reglas del lenguaje C\+\+.  Las propiedades que se describen en \<limits\> incluyen precisión, representaciones de tamaño mínimo y máximo, redondeo y errores de tipo de señalización.  
  
### Enumeraciones  
  
|||  
|-|-|  
|[float\_denorm\_style](../Topic/float_denorm_style.md)|La enumeración describe los diversos métodos que puede elegir una implementación para representar un valor de punto flotante no normalizado \(un valor demasiado pequeño para representarlo como un valor normalizado\):|  
|[float\_round\_style](../Topic/float_round_style.md)|La enumeración describe los diversos métodos que puede elegir una implementación para redondear un valor de punto flotante a un valor entero.|  
  
### Clases  
  
|||  
|-|-|  
|[numeric\_limits \(Clase\)](../standard-library/numeric-limits-class.md)|La clase de plantilla describe propiedades aritméticas de tipos numéricos integrados.|  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)