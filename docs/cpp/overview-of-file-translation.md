---
title: Información general de traducción de archivos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- file translation [C++], about file translation
- translation [C++]
- translation phases
- files [C++], translation
- programs [C++], lexical conventions of
- preprocessing translation phase
ms.assetid: 5036c7b7-ccff-4e2c-b052-a9ea6c71af87
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa38b2ea9ea05fb9391ab8a69e11821d4422e392
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="overview-of-file-translation"></a>Información general de traducción de archivos
Los programas de C++, como los programas de C, constan de uno o más archivos. Cada uno de estos archivos se traduce en el orden conceptual siguiente (el orden real sigue la regla “como si”: la traducción se debe realizar como si se hubieran seguido estos pasos):  
  
1.  Conversión de tokens léxicos. La asignación de caracteres y procesamiento de trígrafos, la delimitación de líneas y la conversión de tokens se realizan en esta fase de traducción.  
  
2.  Preprocesamiento. Esta fase de traducción introduce en archivos de código fuente auxiliares al que hace referencia `#include` directivas, controla "generación de cadenas" y "conversión a caracteres" directivas y realiza la expansión de macros y pegado de token (vea [directivas de preprocesador](../preprocessor/preprocessor-directives.md) en el *referencia del preprocesador* para obtener más información). El resultado de la fase de preprocesamiento es una secuencia de tokens que, en conjunto, definen una “unidad de traducción”.  
  
     Directivas de preprocesador siempre empiezan por el signo de número (**#**) carácter (es decir, el primer carácter de espacio en blanco en la línea debe ser un signo de número). Solo puede aparecer una directiva de preprocesador en cada línea. Por ejemplo:  
  
    ```  
    #include <iostream>  // Include text of iostream in   
                         //  translation unit.  
    #define NDEBUG       // Define NDEBUG (NDEBUG contains empty   
                         //  text string).  
    ```  
  
3.  Generación de código. Esta fase de traducción utiliza los tokens generados en la fase de preprocesamiento para generar código de objetos.  
  
     Durante esta fase, se realiza la comprobación sintáctica y semántica del código fuente.  
  
 Vea [fases de traducción](../preprocessor/phases-of-translation.md) en el *referencia del preprocesador* para obtener más información.  
  
 El preprocesador de C++ es un superconjunto estricto del preprocesador C ANSI, pero en algunos casos es diferente. En la lista siguiente se describen algunas diferencias entre los preprocesadores de C ANSI y C++:  
  
-   Se admiten comentarios de una sola línea. Vea [comentarios](../cpp/comments-cpp.md) para obtener más información.  
  
-   Una macro predefinida, **__cplusplus**, sólo se define para C++. Vea [Macros predefinidas](../preprocessor/predefined-macros.md) en el *referencia del preprocesador* para obtener más información.  
  
-   El preprocesador de C no reconoce los operadores de C++: **.\*** , **-> \***, y `::`. Vea [operadores](../cpp/cpp-built-in-operators-precedence-and-associativity.md) y [expresiones](../cpp/expressions-cpp.md), para obtener más información acerca de los operadores.  
  
## <a name="see-also"></a>Vea también  
 [Convenciones léxicas](../cpp/lexical-conventions.md)