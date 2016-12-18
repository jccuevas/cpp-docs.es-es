---
title: "char_traits (Struct) | Microsoft Docs"
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
  - "std::char_traits"
  - "std.char_traits"
  - "iosfwd/std::char_traits"
  - "char_traits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "char_traits (clase)"
  - "char_traits (struct)"
ms.assetid: 568e59f0-4521-4207-9223-9dcf6a16d620
caps.latest.revision: 20
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# char_traits (Struct)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La estructura char\_traits describe los atributos asociados a un carácter.  
  
## Sintaxis  
  
```  
template <  
   class CharType  
> struct char_traits;  
```  
  
#### Parámetros  
 `CharType`  
 Tipo de datos del elemento.  
  
## Comentarios  
 La estructura de plantilla describe varios rasgos de caracteres del tipo **CharType**.  La clase de plantilla [basic\_string](../standard-library/basic-string-class.md) y varias clases de plantilla de iostream, incluyendo [basic\_ios](../standard-library/basic-ios-class.md), usan esta información para manipular elementos de tipo **CharType**.  Un tipo de elemento de este tipo no debe requerir ni una construcción ni una destrucción explícita.  Debe proporcionar un constructor predeterminado, un constructor de copias y un operador de asignación, con la semántica esperada.  Una copia bit a bit debe tener el mismo efecto que una asignación.  Ninguna de las funciones miembro de la estructura char\_traits puede iniciar excepciones.  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[char\_type](../Topic/char_traits::char_type.md)|Un tipo de carácter.|  
|[int\_type](../Topic/char_traits::int_type.md)|Tipo entero que puede representar un carácter de tipo `char_type` o un carácter de final de archivo \(EOF\).|  
|[off\_type](../Topic/char_traits::off_type.md)|Tipo entero que puede representar desplazamientos entre posiciones de una secuencia.|  
|[pos\_type](../Topic/char_traits::pos_type.md)|Tipo entero que puede representar posiciones de una secuencia.|  
|[state\_type](../Topic/char_traits::state_type.md)|Tipo que representa el estado de conversión de caracteres multibyte de una secuencia.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[assign](../Topic/char_traits::assign.md)|Asigna un valor de carácter a otro.|  
|[compare](../Topic/char_traits::compare.md)|Compara un número especificado de caracteres de dos cadenas.|  
|[copy](../Topic/char_traits::copy.md)|Copia un número especificado de caracteres de una cadena a otra.  Desusado.  En su lugar, use [char\_traits::\_Copy\_s](../Topic/char_traits::_Copy_s.md).|  
|[\_Copy\_s](../Topic/char_traits::_Copy_s.md)|Copia un número especificado de caracteres de una cadena a otra.|  
|[eof](../Topic/char_traits::eof.md)|Devuelve el carácter de final de archivo \(EOF\).|  
|[eq](../Topic/char_traits::eq.md)|Comprueba si dos caracteres `char_type` son iguales.|  
|[eq\_int\_type](../Topic/char_traits::eq_int_type.md)|Comprueba si dos caracteres que se representan como `int_type` son iguales.|  
|[find](../Topic/char_traits::find.md)|Busca la primera aparición de un carácter especificado en un intervalo de caracteres.|  
|[length](../Topic/char_traits::length.md)|Devuelve la longitud de una cadena.|  
|[lt](../Topic/char_traits::lt.md)|Comprueba si un carácter es menor que otro.|  
|[move](../Topic/char_traits::move.md)|Copia un número especificado de caracteres de una secuencia en otra secuencia que puede que esté superpuesta.  Desusado.  En su lugar, use [char\_traits::\_Move\_s](../Topic/char_traits::_Move_s.md).|  
|[\_Move\_s](../Topic/char_traits::_Move_s.md)|Copia un número especificado de caracteres de una secuencia en otra secuencia que puede que esté superpuesta.|  
|[not\_eof](../Topic/char_traits::not_eof.md)|Comprueba si un carácter es el carácter de final de archivo \(EOF\).|  
|[to\_char\_type](../Topic/char_traits::to_char_type.md)|Convierte un carácter `int_type` en el carácter `char_type` correspondiente y devuelve el resultado.|  
|[to\_int\_type](../Topic/char_traits::to_int_type.md)|Convierte un carácter `char_type` en el carácter `int_type` correspondiente y devuelve el resultado.|  
  
## Requisitos  
 **Encabezado:** \<string\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)