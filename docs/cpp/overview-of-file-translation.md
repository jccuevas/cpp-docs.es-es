---
title: Información general de traducción de archivos | Microsoft Docs
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
ms.openlocfilehash: 829afe53d5fde976b7877475cf577b6204be8aed
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051092"
---
# <a name="overview-of-file-translation"></a>Información general de traducción de archivos

Los programas de C++, como los programas de C, constan de uno o más archivos. Cada uno de estos archivos se traduce en el orden conceptual siguiente (el orden real sigue la regla “como si”: la traducción se debe realizar como si se hubieran seguido estos pasos):

1. Conversión de tokens léxicos. La asignación de caracteres y procesamiento de trígrafos, la delimitación de líneas y la conversión de tokens se realizan en esta fase de traducción.

2. Preprocesamiento. Esta fase de traducción introduce en los archivos de código fuente auxiliares que hace referencia `#include` directivas, controla "generación de cadenas" y las directivas de "conversión a" (caracteres"y realiza la expansión de macros y pegado de token (consulte [directivas de preprocesador](../preprocessor/preprocessor-directives.md) en el *referencia del preprocesador* para obtener más información). El resultado de la fase de preprocesamiento es una secuencia de tokens que, en conjunto, definen una “unidad de traducción”.

     Las directivas de preprocesador siempre empiezan por el signo de número (**#**) caracteres (es decir, el primer carácter de espacio en blanco en la línea debe ser un signo de número). Solo puede aparecer una directiva de preprocesador en cada línea. Por ejemplo:

    ```cpp
    #include <iostream>  // Include text of iostream in
                         //  translation unit.
    #define NDEBUG       // Define NDEBUG (NDEBUG contains empty
                         //  text string).
    ```

3. Generación de código. Esta fase de traducción utiliza los tokens generados en la fase de preprocesamiento para generar código de objetos.

     Durante esta fase, se realiza la comprobación sintáctica y semántica del código fuente.

Consulte [fases de traducción](../preprocessor/phases-of-translation.md) en el *referencia del preprocesador* para obtener más información.

El preprocesador de C++ es un superconjunto estricto del preprocesador C ANSI, pero en algunos casos es diferente. En la lista siguiente se describen algunas diferencias entre los preprocesadores de C ANSI y C++:

- Se admiten comentarios de una sola línea. Consulte [comentarios](../cpp/comments-cpp.md) para obtener más información.

- Una macro predefinida, `__cplusplus`, sólo se define para C++. Consulte [Predefined Macros](../preprocessor/predefined-macros.md) en el *referencia del preprocesador* para obtener más información.

- El preprocesador de C no reconoce los operadores de C++: **.** <strong>\*</strong>, **->** <strong>\*</strong>, y **::**. Consulte [operadores](../cpp/cpp-built-in-operators-precedence-and-associativity.md) y [expresiones](../cpp/expressions-cpp.md), para obtener más información acerca de los operadores.

## <a name="see-also"></a>Vea también

[Convenciones léxicas](../cpp/lexical-conventions.md)