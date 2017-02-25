---
title: "iterator (Struct) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "iterator"
  - "std::iterator"
  - "std.iterator"
  - "xutility/std::iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "iterator (clase)"
  - "iterator (struct)"
ms.assetid: c74c8000-8b18-4829-9b71-6103c4229b74
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# iterator (Struct)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Struct base vacío utilizado para asegurarse de que una clase definida por el usuario de iterador funciona correctamente con s para **iterator\_trait**.  
  
## Sintaxis  
  
```  
template<class Category, class Type, class Distance = ptrdiff_t  
    class Pointer = Type*, class Reference = Type&>  
    struct iterator {  
        typedef Category iterator_category;  
        typedef Type value_type;  
        typedef Distance difference_type;  
        typedef Distance distance_type;  
        typedef Pointer pointer;  
        typedef Reference reference;  
    };  
```  
  
## Comentarios  
 Struct de plantilla actúa como tipo base para todos los iteradores.  Define los tipos de miembro  
  
-   `iterator_category` \(un sinónimo para el parámetro `Category`de plantilla\).  
  
-   `value_type` \(un sinónimo para el parámetro **Tipo**de plantilla\).  
  
-   `difference_type` \(un sinónimo para el parámetro `Distance`de plantilla\).  
  
-   `distance_type` \(un sinónimo para el parámetro `Distance`de plantilla\)  
  
-   `pointer` \(un sinónimo para el parámetro `Pointer`de plantilla\).  
  
-   `reference` \(un sinónimo para el parámetro `Reference`de plantilla\).  
  
 Observe que `value_type` no debe ser un tipo constante incluso si los puntos de **puntero** en un objeto const **Tipo** y de referencia proporcionan un objeto const **Tipo**.  
  
## Ejemplo  
 Vea [iterator\_traits](../standard-library/iterator-traits-struct.md) para obtener un ejemplo de cómo declarar y usar los tipos de la clase base del iterador.  
  
## Requisitos  
 Iterador\<de**Header:** \>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<iterator\>](../standard-library/iterator.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)