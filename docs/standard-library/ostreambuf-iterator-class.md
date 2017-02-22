---
title: "ostreambuf_iterator (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.ostreambuf_iterator"
  - "streambuf/std::ostreambuf_iterator"
  - "ostreambuf_iterator"
  - "std::ostreambuf_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ostreambuf_iterator (clase)"
ms.assetid: dad1e624-2f45-4e94-8887-a885e95f9071
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# ostreambuf_iterator (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla ostreambuf\_iterator describe un objeto iterador de salida que escribe elementos de caracteres sucesivos en el flujo de salida con la extracción **operator\>\>**.  Los objetos `ostreambuf_iterator`s se diferencian de los de la clase [ostream\_iterator](../standard-library/ostream-iterator-class.md) en que tienen caracteres en lugar de un tipo genérico en el tipo de objeto que se inserta en el flujo de salida.  
  
## Sintaxis  
  
```  
  
      template <   
   class CharType = char  
   class Traits = char_traits<CharType>  
>  
```  
  
#### Parámetros  
 `CharType`  
 Tipo que representa el tipo de caracteres para ostreambuf\_iterator.  Este argumento es opcional y el valor predeterminado es `char`*.*  
  
 `Traits`  
 Tipo que representa el tipo de caracteres para ostreambuf\_iterator.  Este argumento es opcional y el valor predeterminado es `char_traits`\<*CharType\>.*  
  
## Comentarios  
 La clase ostreambuf\_iterator debe satisfacer los requisitos de un iterador de salida.  Los algoritmos se pueden escribir directamente en el flujo de salida mediante `ostreambuf_iterator`.  La clase proporciona un iterador de flujo de bajo nivel que permite acceso al flujo raw \(sin formato\) de E\/S en forma de caracteres y la capacidad de omitir las traslaciones de caracteres y el almacenamiento en búfer asociados a los iteradores de flujo de alto nivel.  
  
### Constructores  
  
|||  
|-|-|  
|[ostreambuf\_iterator](../Topic/ostreambuf_iterator::ostreambuf_iterator.md)|Construye un objeto `ostreambuf_iterator` que se inicializa para escribir caracteres en el flujo de salida.|  
  
### Typedefs  
  
|||  
|-|-|  
|[char\_type](../Topic/ostreambuf_iterator::char_type.md)|Tipo que proporciona el tipo de los caracteres de `ostreambuf_iterator`.|  
|[ostream\_type](../Topic/ostreambuf_iterator::ostream_type.md)|Tipo que proporciona el tipo de flujo de `ostream_iterator`.|  
|[streambuf\_type](../Topic/ostreambuf_iterator::streambuf_type.md)|Tipo que proporciona el tipo de flujo de `ostreambuf_iterator`.|  
|[traits\_type](../Topic/ostreambuf_iterator::traits_type.md)|Tipo que proporciona el tipo de rasgos de los caracteres de `ostream_iterator`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[failed](../Topic/ostreambuf_iterator::failed.md)|Comprueba si hay errores en una inserción en el búfer del flujo de salida.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator\*](../Topic/ostreambuf_iterator::operator*.md)|Desreferencia el operador usado para implementar la expresión de iterador de salida \*`i` \= `x`.|  
|[operator\+\+](../Topic/ostreambuf_iterator::operator++.md)|Operador de incremento no funcional que devuelve un objeto `ostreambuf_iterator` al mismo objeto que señalaba antes de que se llamara a la operación.|  
|[operator\=](../Topic/ostreambuf_iterator::operator=.md)|El operador inserta un carácter en el búfer del flujo asociado.|  
  
## Requisitos  
 **Encabezado:** \<iterator\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<iterator\>](../standard-library/iterator.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)