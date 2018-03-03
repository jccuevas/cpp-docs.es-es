---
title: "Símbolos (tokens) (C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- tokens [C++]
- parsing, C++ tokens
- translation units
- white space, in C++ tokens
ms.assetid: aa812fd0-6d47-4f3f-aee0-db002ee4d8b9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 852165a345b36c2ea07d18334b050d5fcb8f7bc7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="tokens-c"></a>Símbolos (tokens) (C++)
Un token es el elemento mínimo de un programa de C++ que es significativo para el compilador. El analizador de C++ reconoce estas clases de tokens: identificadores, palabras clave, literales, operadores, signos de puntuación y otros separadores. Una secuencia de estos tokens constituye una unidad de traducción.  
  
 Los tokens suelen estar separados por *espacios en blanco*. El espacio en blanco puede ser uno o varios de los elementos siguientes:  
  
-   Espacios en blanco  
  
-   Tabulaciones horizontales o verticales  
  
-   Nuevas líneas  
  
-   Avances de página  
  
-   Comentarios  
  
 El analizador reconoce las palabras clave, los identificadores, los literales, los operadores y los signos de puntuación. Para obtener información sobre los tipos de token específicos, consulte [Palabras clave](../cpp/keywords-cpp.md), [Identificadores](../cpp/identifiers-cpp.md), [Literales numéricos, booleanos y de puntero](../cpp/numeric-boolean-and-pointer-literals-cpp.md), [Literales de cadena y carácter](../cpp/string-and-character-literals-cpp.md), [Literales definidos por el usuario](../cpp/user-defined-literals-cpp.md), [Operadores integrados de C++, prioridad y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)y [Signos de puntuación](../cpp/punctuators-cpp.md). El espacio en blanco se omite, salvo si es necesario para separar los tokens.  
  
 Los tokens de preprocesamiento se usan en las fases de preprocesamiento para generar el flujo de tokens que se pasa al compilador. Las categorías de token de preprocesamiento son: nombres de encabezado, identificadores, números de preprocesamiento, literales de carácter, literales de cadena, operadores de preprocesamiento y signos de puntuación, y caracteres únicos que no son espacios en blanco y que no coinciden con una de las otras categorías. Los literales de carácter y cadena pueden ser literales definidos por el usuario. Los tokens de preprocesamiento pueden estar separados por espacios en blanco o comentarios.  
  
 El analizador separa los tokens del flujo de entrada creando el token más largo posible usando los caracteres de entrada en un examen de izquierda a derecha. Considere este fragmento de código:  
  
```  
a = i+++j;  
```  
  
 El programador que escribió el código puede haber pensado cualquiera de estas dos instrucciones:  
  
```  
a = i + (++j)  
  
a = (i++) + j  
```  
  
 Como el analizador crea el token más largo posible a partir del flujo de entrada, elige la segunda interpretación, creando los tokens `i++`, `+`y `j`.  
  
## <a name="see-also"></a>Vea también  
 [Convenciones léxicas](../cpp/lexical-conventions.md)