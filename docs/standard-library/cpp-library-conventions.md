---
title: "Convenciones de la biblioteca de C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases [C++]"
  - "convenciones de código, Biblioteca estándar de C++"
  - "convenciones [C++], Biblioteca estándar de C++"
  - "nombres de funciones [C++]"
  - "funciones [C++], convenciones de nomenclatura de la biblioteca"
  - "convenciones de nomenclatura [C++], biblioteca de C++"
  - "convenciones de nomenclatura [C++], Biblioteca estándar de C++"
  - "Biblioteca estándar de C++, convenciones"
ms.assetid: bf41b79a-2d53-4f46-8d05-779358335146
caps.latest.revision: 9
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Convenciones de la biblioteca de C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La biblioteca de C\+\+ obedece mucho a las mismas convenciones que la biblioteca de c estándar, más algunos descritos aquí.  
  
 Una implementación tiene alguna latitud en cómo declara tipos y funciones de la biblioteca de C\+\+:  
  
-   Los nombres de funciones de la biblioteca de c estándar pueden tener extern \# " C\+\+” o vinculación extern “c”.  Incluya el encabezado de C estándar de adecuada en lugar de una entidad de la biblioteca en línea.  
  
-   Un nombre de función miembro en una clase de biblioteca puede tener firmas adicionales de la función a los mostrados en este documento.  Puede asegurarse de que una llamada de función descrita aquí se comporta, pero no puede tomar confiable a la dirección de una función miembro de biblioteca. \(El tipo se puede no ser la esperada.\)  
  
-   Una clase de biblioteca puede tener clases base \(no virtual\) indocumentadas.  Una clase documentada como derivado de otra se puede, de hecho, derivar de esa clase a través de otras clases indocumentadas.  
  
-   Un tipo definido como sinónimo de algún tipo entero puede ser igual que distintos tipos enteros.  
  
-   Un tipo de máscara de bits se puede implementar como un tipo entero o una enumeración.  En cualquier caso, puede realizar operaciones bit a bit \(como `AND` y `OR`\) en valores del mismo tipo de máscara de bits.  Los elementos `A` y `B` de un tipo de máscara de bits son valores distintos de cero de modo que `A` &`B` es cero.  
  
-   Una función de biblioteca que no tiene una especificación de excepciones puede producir una excepción arbitraria, a menos que su definición limite claramente por tanto.  
  
 Por otra parte, hay algunas restricciones:  
  
-   La biblioteca de c estándar de no utiliza ninguna macro de enmascarado.  Sólo se reservan las firmas de la función específica, no los nombres de las funciones propios.  
  
-   Un nombre de función de biblioteca fuera de una clase no tendrá adicional, indocumentado, las firmas de la función.  Puede tomar confiable a su dirección.  
  
-   Las clases base y virtuales descrita las funciones miembro tan son de confianza virtuales, mientras que las descritas como no virtual son de confianza no virtual.  
  
-   Dos tipos definidos por la biblioteca de C\+\+ siempre son diferentes a menos que este documento explícitamente sugiera de otra manera.  
  
-   Las funciones proporcionadas por la biblioteca, incluidas las versiones predeterminadas de funciones reemplazables, pueden producir *como máximo* esas excepciones mostradas en cualquier especificación de excepciones.  Cualquier destructores proporcionados por la biblioteca producen excepciones.  Las funciones de la biblioteca de c estándar pueden propagar una excepción, como cuando `qsort` llama a una función de comparación que inicia una excepción, pero no producen de otra manera excepciones.  
  
## Vea también  
 [Información general de STL](../standard-library/cpp-standard-library-overview.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)