---
title: "Aserci&#243;n y mensajes proporcionados por el usuario (C++) | Microsoft Docs"
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
  - "#error%2C assert%2C static_assert [C++]"
  - "mensajes proporcionados por el usuario [C++], tiempo de compilación"
  - "mensajes proporcionados por el usuario [C++], tiempo de preprocesador"
  - "mensajes proporcionados por el usuario [C++], tiempo de ejecución"
ms.assetid: ebf7d885-61c8-4233-b0ae-1c9a38e0f385
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Aserci&#243;n y mensajes proporcionados por el usuario (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El lenguaje C\+\+ admite tres mecanismos de control de errores que ayudan a depurar la aplicación: la [directiva \#error](../preprocessor/hash-error-directive-c-cpp.md), la palabra clave [static\_assert](../cpp/static-assert.md) y la macro [assert \(macro\), \_assert, \_wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md).  Los tres mecanismos emiten mensajes de error y dos de ellos también prueban las aserciones de software.  Una aserción de software especifica una condición que se espera que sea cierta \(valor true\) en un determinado punto del programa.  Si se produce un error de aserción en tiempo de compilación, el compilador emite un mensaje de diagnóstico y un error de compilación.  Si se produce un error de aserción en tiempo de ejecución, el sistema operativo emite un mensaje de diagnóstico y cierra la aplicación.  
  
## Comentarios  
 La duración de la aplicación se compone de una fase de preprocesamiento, una de compilación y una de tiempo de ejecución.  Cada mecanismo de control de errores tiene acceso a la información de depuración disponible durante una de estas fases.  Para depurar eficazmente, seleccione el mecanismo que proporciona la información adecuada sobre esa fase:  
  
-   La [directiva \#error](../preprocessor/hash-error-directive-c-cpp.md) está vigente en tiempo de preprocesamiento.  Emite incondicionalmente un mensaje definido por el usuario y hace que se produzca un error de compilación.  El mensaje puede contener texto que se manipula mediante directivas de preprocesador, pero no se evalúa ninguna expresión resultante.  
  
-   La declaración [static\_assert](../cpp/static-assert.md) está vigente en tiempo de compilación.  Prueba una aserción de software que está representada por una expresión de tipo entero definida por el usuario que se puede convertir en un valor booleano.  Si la expresión se evalúa como cero \(false\), el compilador emite el mensaje definido por el usuario y se produce un error de compilación.  
  
     La declaración `static_assert` resulta especialmente útil para depurar plantillas, porque los argumentos de plantilla se pueden incluir en la expresión especificada por el usuario.  
  
-   La macro [assert \(macro\), \_assert, \_wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) está vigente en tiempo de ejecución.  Evalúa una expresión definida por el usuario y, si el resultado es cero, el sistema emite un mensaje de diagnóstico y cierra la aplicación.  Muchas otras macros, como[\_ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) y `_ASSERTE`, se parecen a esta macro pero emiten diferentes mensajes de diagnóstico definidos por el sistema o definidos por el usuario.  
  
## Vea también  
 [\#error \(Directiva\)](../preprocessor/hash-error-directive-c-cpp.md)   
 [assert \(macro\), \_assert, \_wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)   
 [\_ASSERT, \_ASSERTE, \_ASSERT\_EXPR \(macros\)](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)   
 [static\_assert](../cpp/static-assert.md)   
 [\_STATIC\_ASSERT \(Macro\)](../c-runtime-library/reference/static-assert-macro.md)   
 [Plantillas](../cpp/templates-cpp.md)