---
title: "&lt; stdexcept &gt; | Microsoft Docs"
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
  - "std.<stdexcept>"
  - "std::<stdexcept>"
  - "<stdexcept>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "stdexcept (encabezado)"
ms.assetid: 495c10b1-1e60-4514-9f8f-7fda11a2f522
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt; stdexcept &gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define varias clases estándar usadas para notificar excepciones. Las clases forman una jerarquía de derivación todas ellas derivada de la clase [excepción](../standard-library/exception-class1.md) e incluyen dos tipos generales de excepciones: errores lógicos y errores en tiempo de ejecución. Los errores lógicos son errores producidos por el programador. Se derivan de la clase base logic_error e incluyen:  
  
-   `domain_error`  
  
-   `invalid_argument`  
  
-   `length_error`  
  
-   `out_of_range`  
  
 Los errores de tiempo de ejecución se producen debido a errores en las funciones de biblioteca o en el sistema de tiempo de ejecución. Se derivan de la clase base runtime_error e incluyen:  
  
-   `overflow_error`  
  
-   `range_error`  
  
-   `underflow_error`  
  
### <a name="classes"></a>Clases  
  
|||  
|-|-|  
|[domain_error (clase)](../standard-library/domain-error-class.md)|Clase que actúa como la clase base para todas las excepciones iniciadas para notificar un error de dominio.|  
|[invalid_argument (clase)](../standard-library/invalid-argument-class.md)|Clase que actúa como la clase base para todas las excepciones iniciadas para notificar un argumento inválido.|  
|[length_error (clase)](../standard-library/length-error-class.md)|Clase que actúa como la clase base para todas las excepciones iniciadas para informar de un intento de generar un objeto demasiado largo como para poder especificarlo.|  
|[logic_error (clase)](../standard-library/logic-error-class.md)|Clase que actúa como la clase base para todas las excepciones iniciadas para informar de errores supuestamente detectables antes de que se ejecute el programa, como las infracciones de las condiciones lógicas previas.|  
|[out_of_range (clase)](../standard-library/out-of-range-class.md)|Clase que actúa como la clase base para todas las excepciones iniciadas para informar sobre un argumento que está fuera de su rango válido.|  
|[overflow_error (clase)](../standard-library/overflow-error-class.md)|Clase que actúa como la clase base para todas las excepciones iniciadas para notificar un desbordamiento aritmético.|  
|[range_error (clase)](../standard-library/range-error-class.md)|Clase que actúa como la clase base para todas las excepciones iniciadas para notificar un error de rango.|  
|[runtime_error (clase)](../standard-library/runtime-error-class.md)|Clase que actúa como la clase base para todas las excepciones iniciadas para informar de errores supuestamente detectables únicamente cuando se ejecute el programa.|  
|[underflow_error (clase)](../standard-library/underflow-error-class.md)|Clase que actúa como la clase base para todas las excepciones iniciadas para notificar un subdesbordamiento aritmético.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

