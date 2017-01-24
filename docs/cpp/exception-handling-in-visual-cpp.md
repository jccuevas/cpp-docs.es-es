---
title: "Control de excepciones en Visual C++ | Microsoft Docs"
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
  - "try-catch (palabra clave) [C++], control de excepciones"
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Control de excepciones en Visual C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una excepción es una condición de error, posiblemente fuera del control del programa, que evita que el programa continúe a lo largo de su ruta normal de ejecución.  Determinadas operaciones, incluidas la creación de objetos, la entrada\/salida de archivo y las llamadas de función realizadas desde otros módulos, son posibles orígenes de excepciones aunque el programa se ejecute correctamente.  Un código robusto prevé y controla las excepciones.  
  
 Para detectar errores lógicos dentro de un programa o un módulo, se deben usar aserciones en lugar de excepciones \(vea [Uso de aserciones](../Topic/C-C++%20Assertions.md)\).  
  
 Visual C\+\+ admite tres tipos de control de excepciones:  
  
-   [Control de excepciones de C\+\+](../cpp/cpp-exception-handling.md)  
  
     Para la mayoría de los programas de C\+\+, se debe utilizar el control de excepciones de C\+\+, que tiene seguridad de tipos y garantiza que se llame a los destructores de objeto durante el desenredo de la pila.  
  
-   [Control estructurado de excepciones](../cpp/structured-exception-handling-c-cpp.md)  
  
     Windows suministra su propio mecanismo de excepción, denominado SEH.  No se recomienda para la programación con C\+\+ o con MFC.  SEH solo debe utilizarse en programas que no son de MFC C.  
  
-   [Excepciones de MFC](../mfc/exception-handling-in-mfc.md)  
  
     Desde la versión 3.0, MFC ha utilizado las excepciones de C\+\+ pero sigue admitiendo sus anteriores macros de control de excepciones, que son similares a las excepciones de C\+\+ en su forma.  Aunque estas macros no son recomendables para nueva programación, todavía se siguen admitiendo por razones de compatibilidad con versiones anteriores.  En los programas que ya utilizan las macros, también puede utilizar libremente las excepciones de C\+\+.  Durante el preprocesamiento, las macros evalúan las palabras clave de control de excepciones definidas en la implementación de Visual C\+\+ del lenguaje C\+\+ a partir de la versión 2.0 de Visual C\+\+.  Puede dejar las macros de excepciones existentes en su sitio mientras empieza a utilizar las excepciones de C\+\+.  
  
 Utilice la opción del compilador [\/EH](../build/reference/eh-exception-handling-model.md) para especificar el tipo de control de excepciones que se va a usar en un proyecto; el control de excepciones de C\+\+ es la opción predeterminada.  No combine los mecanismos de control de errores; por ejemplo, no use las excepciones de C\+\+ con control de excepciones estructurado.  Si usa el control de excepciones de C\+\+, el código será más portátil y podrá controlar todo tipo de excepciones.  Para obtener más información sobre los inconvenientes del control de excepciones estructurado, consulte [Control de excepciones estructurado](../cpp/structured-exception-handling-c-cpp.md).  Para obtener más información sobre la combinación de macros de MFC y excepciones de C\+\+, consulte [Excepciones: Uso de macros de MFC y excepciones de C\+\+](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).  
  
 Para obtener información sobre cómo se controlan las excepciones en las aplicaciones de CLR, vea [Control de excepciones](../windows/exception-handling-cpp-component-extensions.md).  
  
 Para obtener información sobre el control de excepciones en procesadores x64, vea [Control de excepciones \(x64\)](../build/exception-handling-x64.md).  
  
## Vea también  
 [Referencia de lenguaje C\+\+](../cpp/cpp-language-reference.md)