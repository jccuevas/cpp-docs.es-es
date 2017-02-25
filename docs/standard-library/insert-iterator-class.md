---
title: "insert_iterator (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::insert_iterator"
  - "iterator/std::insert_iterator"
  - "std.insert_iterator"
  - "insert_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "insert_iterator (clase)"
  - "insert_iterator (clase), sintaxis"
ms.assetid: d5d86405-872e-4e3b-9e68-c69a2b7e8221
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# insert_iterator (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un adaptador de iterador que satisface los requisitos de un iterador de salida.  Inserta, en lugar de sobrescribir, elementos en una secuencia y proporciona así la semántica que es diferente de la semántica que sobrescribe proporcionada por los iteradores de la secuencia de C\+\+ y los contenedores asociativos.  La clase `insert_iterator` se hace plantilla en el tipo de contenedor que se adapta.  
  
## Sintaxis  
  
```  
template <class Container> class insert_iterator;  
```  
  
#### Parámetros  
 `Container`  
 Tipo de contenedor en el que un `insert_iterator` debe insertar los elementos.  
  
## Comentarios  
 El contenedor de tipo **Container** debe satisfacer los requisitos de un contenedor de tamaño variable y tener una función miembro insert de dos argumentos donde los parámetros son de tipo **Container::iterator** y **Container::value\_type** y devolver un tipo **Container::iterator**.  Los contenedores asociativos ordenados y de secuencia de la Biblioteca de plantillas estándar cumplen estos requisitos y pueden adaptarse para su uso con `insert_iterator`.  En los contenedores asociativos, el argumento de posición se trata como una sugerencia, algo que tiene potencial para mejorar o degradar el rendimiento, según la calidad de la sugerencia.  Un `insert_iterator` debe inicializarse siempre con su contenedor.  
  
### Constructores  
  
|||  
|-|-|  
|[insert\_iterator](../Topic/insert_iterator::insert_iterator.md)|Construye `insert_iterator` que inserta un elemento en una posición especificada de un contenedor.|  
  
### Typedefs  
  
|||  
|-|-|  
|[container\_type](../Topic/insert_iterator::container_type.md)|Tipo que representa el contenedor en el que se va a crear una inserción general.|  
|[reference](../Topic/insert_iterator::reference.md)|Tipo que proporciona una referencia a un elemento de una secuencia controlada por el contenedor asociado.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator\*](../Topic/insert_iterator::operator*.md)|Operador de desreferencia usado para implementar la expresión del iterador de salida \*`i` \= `x` para una inserción general.|  
|[operator\+\+](../Topic/insert_iterator::operator++.md)|Incrementa el `insert_iterator` a la siguiente ubicación en la que puede almacenarse un valor.|  
|[operator\=](../Topic/insert_iterator::operator=.md)|Operador de asignación usado para implementar la expresión del iterador de salida \*`i` \= `x` para una inserción general.|  
  
## Requisitos  
 **Encabezado**: \<iterator\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<iterator\>](../standard-library/iterator.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)