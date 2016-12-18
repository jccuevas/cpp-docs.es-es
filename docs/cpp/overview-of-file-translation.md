---
title: "Informaci&#243;n general de traducci&#243;n de archivos | Microsoft Docs"
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
  - "traducción de archivos [C++], acerca de la traducción de archivos"
  - "archivos [C++], traslación"
  - "fase de preprocesamiento de traducción"
  - "programas [C++], convenciones léxicas de"
  - "traducción [C++]"
  - "fases de traducción"
ms.assetid: 5036c7b7-ccff-4e2c-b052-a9ea6c71af87
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Informaci&#243;n general de traducci&#243;n de archivos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los programas de C\+\+, como los programas de C, constan de uno o más archivos.  Cada uno de estos archivos se traduce en el orden conceptual siguiente \(el orden real sigue la regla “como si”: la traducción se debe realizar como si se hubieran seguido estos pasos\):  
  
1.  Conversión de tokens léxicos.  La asignación de caracteres y procesamiento de trígrafos, la delimitación de líneas y la conversión de tokens se realizan en esta fase de traducción.  
  
2.  Preprocesamiento.  Esta fase de traducción introduce los archivos de código fuente auxiliares a los que hacen referencia las directivas `#include`, controla las directivas de generación de cadenas y generación de caracteres, y realiza el pegado de tokens y la expansión de macros \(vea [Directivas de preprocesador](../preprocessor/preprocessor-directives.md) en la *Referencia del preprocesador* para obtener más información\).  El resultado de la fase de preprocesamiento es una secuencia de tokens que, en conjunto, definen una “unidad de traducción”.  
  
     Las directivas de preprocesador siempre empiezan con el carácter de signo de número \(**\#**\), es decir, el primer carácter distinto de un espacio en la línea debe ser un signo de número.  Solo puede aparecer una directiva de preprocesador en cada línea.  Por ejemplo:  
  
    ```  
    #include <iostream>  // Include text of iostream in   
                         //  translation unit.  
    #define NDEBUG       // Define NDEBUG (NDEBUG contains empty   
                         //  text string).  
    ```  
  
3.  Generación de código.  Esta fase de traducción utiliza los tokens generados en la fase de preprocesamiento para generar código de objetos.  
  
     Durante esta fase, se realiza la comprobación sintáctica y semántica del código fuente.  
  
 Vea [Fases de traducción](../preprocessor/phases-of-translation.md) en la *Referencia del preprocesador* para obtener más información.  
  
 El preprocesador de C\+\+ es un superconjunto estricto del preprocesador C ANSI, pero en algunos casos es diferente.  En la lista siguiente se describen algunas diferencias entre los preprocesadores de C ANSI y C\+\+:  
  
-   Se admiten comentarios de una sola línea.  Vea [Comentarios](../cpp/comments-cpp.md) para obtener más información.  
  
-   Solo se define una macro predefinida, **\_\_cplusplus**, para C\+\+.  Vea [Macros predefinidas](../preprocessor/predefined-macros.md) en la *Referencia del preprocesador* para obtener más información.  
  
-   El preprocesador de C no reconoce los operadores de C\+\+: **.\***, **–\>\*** y `::`.  Vea [Operadores](../cpp/cpp-built-in-operators-precedence-and-associativity.md) y [Expresiones](../cpp/expressions-cpp.md) para obtener más información sobre los operadores.  
  
## Vea también  
 [Convenciones léxicas](../cpp/lexical-conventions.md)