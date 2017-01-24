---
title: "Control de excepciones de C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "control de excepciones de C++"
  - "Visual C++, control de excepciones"
ms.assetid: 65f80b44-9d0f-4d17-b910-07205a5c5c40
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Control de excepciones de C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El lenguaje C\+\+ proporciona compatibilidad integrada para producir y detectar excepciones.  Al programar en C\+\+, casi siempre se debe utilizar la compatibilidad con excepciones de C\+\+ integrada como se describe en esta sección.  
  
 Para habilitar el control de excepciones de C\+\+ en el código, utilice [\/EHsc](../build/reference/eh-exception-handling-model.md).  
  
## En esta sección  
 Esta descripción del control de excepciones de C\+\+ incluye lo siguiente:  
  
-   [Las instrucciones try, catch y throw](../cpp/try-throw-and-catch-statements-cpp.md)  
  
-   [Cómo se evalúan los bloques Catch](../cpp/how-catch-blocks-are-evaluated-cpp.md)  
  
-   [Excepciones y desenredo de la pila](../cpp/exceptions-and-stack-unwinding-in-cpp.md)  
  
-   [Especificaciones de excepciones](../cpp/exception-specifications-throw-cpp.md)  
  
-   [noexcept](../cpp/noexcept-cpp.md)  
  
-   [Excepciones de C\+\+ no controladas](../cpp/unhandled-cpp-exceptions.md)  
  
-   [Mezclar excepciones de C \(estructuradas\) y de C\+\+](../cpp/mixing-c-structured-and-cpp-exceptions.md)  
  
## Compatibilidad con excepciones MFC anteriores  
 A partir de la versión 4.0, MFC empezó a usar el mecanismo de control de excepciones de C\+\+.  Aunque se recomienda utilizar el control de excepciones de C\+\+ en el código nuevo, la versión 4.0 de MFC y las versiones posteriores conservan las macros de versiones anteriores de MFC, por lo que el código anterior no resultará dañado.  También se pueden combinar las macros y el nuevo mecanismo.  Para obtener información sobre cómo mezclar macros y el control de excepciones de C\+\+, y cómo convertir código anterior para utilizar el nuevo mecanismo, vea los artículos [Excepciones: utilizar macros de MFC y excepciones de C\+\+](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) y [Excepciones: convertir desde macros de excepciones de MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md).  Las macros de excepciones de MFC anteriores, si todavía las utiliza, se evalúan como palabras clave de excepciones de C\+\+.  Vea [Excepciones: cambios en las macros de excepciones en la versión 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md).  
  
## Vea también  
 [Control de excepciones](../cpp/exception-handling-in-visual-cpp.md)