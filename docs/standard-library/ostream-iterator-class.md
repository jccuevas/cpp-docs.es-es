---
title: "ostream_iterator (Clase) | Microsoft Docs"
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
  - "ostream_iterator"
  - "std.ostream_iterator"
  - "std::ostream_iterator"
  - "iterator/std::ostream_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ostream_iterator (clase)"
ms.assetid: 24d842d3-9f45-4bf6-a697-62f5968f5a03
caps.latest.revision: 17
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ostream_iterator (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla ostream\_iterator describe un objeto iterador de salida que escribe elementos sucesivos en el flujo de salida con la extracción **operator \<\<**.  
  
## Sintaxis  
  
```  
  
      template <  
   class Type   
   class CharType = char  
   class Traits = char_traits<CharType>  
>  
class ostream_iterator  
```  
  
#### Parámetros  
 *Tipo*  
 Tipo de objeto que se va a insertar en el flujo de salida.  
  
 `CharType`  
 Tipo que representa el tipo de caracteres para `ostream_iterator`.  Este argumento es opcional y el valor predeterminado es `char`*.*  
  
 `Traits`  
 Tipo que representa el tipo de caracteres para `ostream_iterator`.  Este argumento es opcional y el valor predeterminado es `char_traits`\<*CharType\>.*  
  
 La clase ostream\_iterator debe satisfacer los requisitos de un iterador de salida.  Los algoritmos se pueden escribir directamente en el flujo de salida mediante `ostream_iterator`.  
  
### Constructores  
  
|||  
|-|-|  
|[ostream\_iterator](../Topic/ostream_iterator::ostream_iterator.md)|Construye una clase `ostream_iterator` que se inicializa y delimita para escribir caracteres en el flujo de salida.|  
  
### Typedefs  
  
|||  
|-|-|  
|[char\_type](../Topic/ostream_iterator::char_type.md)|Tipo que proporciona el tipo de los caracteres de `ostream_iterator`.|  
|[ostream\_type](../Topic/ostream_iterator::ostream_type.md)|Tipo que proporciona el tipo de flujo de `ostream_iterator`.|  
|[traits\_type](../Topic/ostream_iterator::traits_type.md)|Tipo que proporciona el tipo de rasgos de los caracteres de `ostream_iterator`.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator\*](../Topic/ostream_iterator::operator*.md)|Desreferencia el operador usado para implementar la expresión de iterador de salida \*`i` \= `x`.|  
|[operator\+\+](../Topic/ostream_iterator::operator++.md)|Operador de incremento no funcional que devuelve un objeto `ostream_iterator` al mismo objeto que señalaba antes de que se llamara a la operación.|  
|[operator\=](../Topic/ostream_iterator::operator=.md)|Operador de asignación que se usa para implementar la expresión de iterador de salida \*`i` \= `x` para escribir en un flujo de salida.|  
  
## Requisitos  
 **Encabezado:** \<iterator\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<iterator\>](../standard-library/iterator.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)