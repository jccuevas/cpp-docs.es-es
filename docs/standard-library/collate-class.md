---
title: "collate (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::collate"
  - "locale/std::collate"
  - "std.collate"
  - "collate"
  - "Collate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "collate (clase)"
ms.assetid: 92168798-9628-4a2e-be6e-fa62dcd4d6a6
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# collate (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una clase de plantilla que describe un objeto que puede actuar como faceta de configuración regional para controlar la ordenación y agrupación de los caracteres de una cadena, las comparaciones entre ellos y el hash de las cadenas.  
  
## Sintaxis  
  
```  
template <class CharType >  
   class collate : public locale::facet;  
```  
  
#### Parámetros  
 `CharType`  
 Tipo usado dentro de un programa para codificar caracteres.  
  
## Comentarios  
 Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero.  El primer intento de acceso a su valor almacenado almacena un valor positivo único en **id.** En algunos lenguajes, los caracteres se agrupan y se tratan como un carácter individual y, en otros, los caracteres individuales se tratan como si fueran dos caracteres.  Los servicios de intercalación que proporciona la clase collate ofrecen una manera de ordenar estos casos.  
  
### Constructores  
  
|||  
|-|-|  
|[collate](../Topic/collate::collate.md)|El constructor para los objetos de la clase `collate` que actúa como una faceta de configuración regional para controlar las convenciones de ordenación de cadenas.|  
  
### Typedefs  
  
|||  
|-|-|  
|[char\_type](../Topic/collate::char_type.md)|Un tipo que describe un carácter de tipo `CharType`.|  
|[string\_type](../Topic/collate::string_type.md)|Un tipo que describe una cadena de tipo `basic_string` que contiene caracteres de tipo `CharType`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[compare](../Topic/collate::compare.md)|Compara la igualdad o la desigualdad de dos secuencias de caracteres según las reglas específicas de su faceta.|  
|[do\_compare](../Topic/collate::do_compare.md)|Función virtual a la que se llama para comparar la igualdad o la desigualdad de dos secuencias de caracteres según las reglas específicas de su faceta.|  
|[do\_hash](../Topic/collate::do_hash.md)|Función virtual a la que se llama para determinar el valor hash de las secuencias según las reglas específicas de su faceta.|  
|[do\_transform](../Topic/collate::do_transform.md)|Función virtual a la que se llama para convertir una secuencia de caracteres de una configuración regional en una cadena que se puede usar en comparaciones lexicográficas con otras secuencias de caracteres convertidas de igual forma a partir de la misma configuración regional.|  
|[hash](../Topic/collate::hash.md)|Determina el valor hash de la secuencia según las reglas específicas de su faceta.|  
|[transformación](../Topic/collate::transform.md)|Convierte una secuencia de caracteres de una configuración regional en una cadena que se puede usar en comparaciones lexicográficas con otras secuencias de caracteres convertidas de forma similar a partir de la misma configuración regional.|  
  
## Requisitos  
 **Encabezado:** \<locale\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<locale\>](../standard-library/locale.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)