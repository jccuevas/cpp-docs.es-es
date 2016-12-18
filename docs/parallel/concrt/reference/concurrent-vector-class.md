---
title: "Clase concurrent_vector | Microsoft Docs"
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
  - "concurrent_vector/Concurrency::concurrent_vector"
  - "concurrent_vector/concurrency::concurrent_vector"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "concurrent_vector (clase)"
ms.assetid: a217b4ac-af2b-4d41-94eb-09a75ee28622
caps.latest.revision: 21
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clase concurrent_vector
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La clase `concurrent_vector` es una clase de contenedor de secuencia que permite el acceso aleatorio a cualquier elemento.  Habilita las operaciones de anexión segura para simultaneidad, acceso de elemento, acceso de iterador e iterador transversal.  
  
## Sintaxis  
  
```  
template<  
   typename _Ty,  
   class _Ax  
>  
class concurrent_vector: protected details::_Allocator_base<_Ty, _Ax>, private details::_Concurrent_vector_base_v4;  
```  
  
#### Parámetros  
 `_Ty`  
 Tipo de datos de los elementos que se van a almacenar en el vector.  
  
 `_Ax`  
 El tipo que representa el objeto de asignador almacenado que encapsula los detalles acerca de la asignación y desasignación de memoria para el vector simultáneo.  Este argumento es opcional y el valor predeterminado es `allocator<``_Ty``>`.  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`allocator_type`|Un tipo que representa la clase de asignador del vector simultáneo.|  
|`const_iterator`|Un tipo que proporciona un iterador de acceso aleatorio que puede leer un elemento `const` en un vector simultáneo.|  
|`const_pointer`|Un tipo que proporciona un puntero a un elemento `const` de un vector simultáneo.|  
|`const_reference`|Un tipo que proporciona una referencia a un elemento `const` almacenado en un vector simultáneo para leer y realizar operaciones `const`.|  
|`const_reverse_iterator`|Un tipo que proporciona un iterador de acceso aleatorio que puede leer cualquier elemento `const` en el vector simultáneo.|  
|`difference_type`|Un tipo que proporciona la distancia firmada entre dos elementos en un vector simultáneo.|  
|`iterator`|Un tipo que proporciona un iterador de acceso aleatorio que puede leer cualquier elemento en un vector simultáneo.  La modificación de un elemento usando el iterador no es segura para simultaneidad.|  
|`pointer`|Un tipo que proporciona un puntero a un elemento de un vector simultáneo.|  
|`reference`|Un tipo que proporciona una referencia a un elemento almacenado en un vector simultáneo.|  
|`reverse_iterator`|Un tipo que proporciona un iterador de acceso aleatorio que puede leer cualquier elemento en un vector simultáneo inverso.  La modificación de un elemento usando el iterador no es segura para simultaneidad.|  
|`size_type`|Un tipo que cuenta el número de elementos en un vector simultáneo.|  
|`value_type`|Un tipo que representa el tipo de datos almacenados en un vector simultáneo.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[concurrent\_vector::concurrent\_vector \(Constructor\)](../Topic/concurrent_vector::concurrent_vector%20Constructor.md)|Sobrecargado.  Construye un vector simultáneo.|  
|[concurrent\_vector::~concurrent\_vector \(Destructor\)](../Topic/concurrent_vector::~concurrent_vector%20Destructor.md)|Borra todos los elementos y destruye este vector simultáneo.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[concurrent\_vector::assign \(Método\)](../Topic/concurrent_vector::assign%20Method.md)|Sobrecargado.  Borra los elementos del vector simultáneo y le asigna todas las copias `_N` de `_Item` o los valores especificados por el intervalo de iterador \[`_Begin`, `_End`\).  Este método no es seguro para la simultaneidad.|  
|[concurrent\_vector::at \(Método\)](../Topic/concurrent_vector::at%20Method.md)|Sobrecargado.  Proporciona acceso al elemento en el índice especificado del vector simultáneo.  Este método es seguro para simultaneidad en las operaciones de lectura y también durante el aumento del vector, siempre que se haya asegurado de que el valor `_Index` es menor que el tamaño del vector simultáneo.|  
|[concurrent\_vector::back \(Método\)](../Topic/concurrent_vector::back%20Method.md)|Sobrecargado.  Devuelve una referencia o una referencia `const` al último elemento del vector simultáneo.  Si el vector simultáneo está vacío, el valor devuelto es undefined.  Este método es seguro para simultaneidad.|  
|[concurrent\_vector::begin \(Método\)](../Topic/concurrent_vector::begin%20Method.md)|Sobrecargado.  Devuelve un iterador de tipo `iterator` o `const_iterator` al principio del vector simultáneo.  Este método es seguro para simultaneidad.|  
|[concurrent\_vector::capacity \(Método\)](../Topic/concurrent_vector::capacity%20Method.md)|Devuelve el tamaño máximo que puede alcanzar el vector simultáneo sin tener que asignar más memoria.  Este método es seguro para simultaneidad.|  
|[concurrent\_vector::cbegin \(Método\)](../Topic/concurrent_vector::cbegin%20Method.md)|Devuelve un iterador de tipo `const_iterator` al principio del vector simultáneo.  Este método es seguro para simultaneidad.|  
|[concurrent\_vector::cend \(Método\)](../Topic/concurrent_vector::cend%20Method.md)|Devuelve un iterador de tipo `const_iterator` al final del vector simultáneo.  Este método es seguro para simultaneidad.|  
|[concurrent\_vector::clear \(Método\)](../Topic/concurrent_vector::clear%20Method.md)|Borra todos los elementos del vector simultáneo.  Este método no es seguro para la simultaneidad.|  
|[concurrent\_vector::crbegin \(Método\)](../Topic/concurrent_vector::crbegin%20Method.md)|Devuelve un iterador de tipo `const_reverse_iterator` al principio del vector simultáneo.  Este método es seguro para simultaneidad.|  
|[concurrent\_vector::crend \(Método\)](../Topic/concurrent_vector::crend%20Method.md)|Devuelve un iterador de tipo `const_reverse_iterator` al final del vector simultáneo.  Este método es seguro para simultaneidad.|  
|[concurrent\_vector::empty \(Método\)](../Topic/concurrent_vector::empty%20Method.md)|Comprueba si el vector simultáneo está vacío en el momento al que se llama a este método.  Este método es seguro para simultaneidad.|  
|[concurrent\_vector::end \(Método\)](../Topic/concurrent_vector::end%20Method.md)|Sobrecargado.  Devuelve un iterador de tipo `iterator` o `const_iterator` al final del vector simultáneo.  Este método es seguro para simultaneidad.|  
|[concurrent\_vector::front \(Método\)](../Topic/concurrent_vector::front%20Method.md)|Sobrecargado.  Devuelve una referencia o una referencia `const` al primer elemento del vector simultáneo.  Si el vector simultáneo está vacío, el valor devuelto es undefined.  Este método es seguro para simultaneidad.|  
|[concurrent\_vector::get\_allocator \(Método\)](../Topic/concurrent_vector::get_allocator%20Method.md)|Devuelve una copia del asignador usada para construir el vector simultáneo.  Este método es seguro para simultaneidad.|  
|[concurrent\_vector::grow\_by \(Método\)](../Topic/concurrent_vector::grow_by%20Method.md)|Sobrecargado.  Aumenta este vector simultáneo mediante elementos `_Delta`.  Este método es seguro para simultaneidad.|  
|[concurrent\_vector::grow\_to\_at\_least \(Método\)](../Topic/concurrent_vector::grow_to_at_least%20Method.md)|Aumenta este vector simultáneo hasta tener al menos elementos `_N`.  Este método es seguro para simultaneidad.|  
|[concurrent\_vector::max\_size \(Método\)](../Topic/concurrent_vector::max_size%20Method.md)|Devuelve el número máximo de elementos que el vector simultáneo puede contener.  Este método es seguro para simultaneidad.|  
|[concurrent\_vector::push\_back \(Método\)](../Topic/concurrent_vector::push_back%20Method.md)|Sobrecargado.  Anexa el elemento determinado al final del vector simultáneo.  Este método es seguro para simultaneidad.|  
|[concurrent\_vector::rbegin \(Método\)](../Topic/concurrent_vector::rbegin%20Method.md)|Sobrecargado.  Devuelve un iterador de tipo `reverse_iterator` o `const_reverse_iterator` al principio del vector simultáneo.  Este método es seguro para simultaneidad.|  
|[concurrent\_vector::rend \(Método\)](../Topic/concurrent_vector::rend%20Method.md)|Sobrecargado.  Devuelve un iterador de tipo `reverse_iterator` o `const_reverse_iterator` al final del vector simultáneo.  Este método es seguro para simultaneidad.|  
|[concurrent\_vector::reserve \(Método\)](../Topic/concurrent_vector::reserve%20Method.md)|Asigna espacio suficiente para que el vector simultáneo obtenga el tamaño necesario para dimensionar `_N` sin tener que asignar más memoria después.  Este método no es seguro para la simultaneidad.|  
|[concurrent\_vector::resize \(Método\)](../Topic/concurrent_vector::resize%20Method.md)|Sobrecargado.  Cambia el tamaño del vector simultáneo al tamaño solicitado, eliminando o agregando elementos según sea necesario.  Este método no es seguro para la simultaneidad.|  
|[concurrent\_vector::shrink\_to\_fit \(Método\)](../Topic/concurrent_vector::shrink_to_fit%20Method.md)|Compacta la representación interna del vector simultáneo para reducir la fragmentación y optimizar la utilización de memoria.  Este método no es seguro para la simultaneidad.|  
|[concurrent\_vector::size \(Método\)](../Topic/concurrent_vector::size%20Method.md)|Devuelve el número de elementos en un vector simultáneo.  Este método es seguro para simultaneidad.|  
|[concurrent\_vector::swap \(Método\)](../Topic/concurrent_vector::swap%20Method.md)|Intercambia el contenido de dos vectores simultáneos.  Este método no es seguro para la simultaneidad.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[concurrent\_vector::operatorOperator](../Topic/concurrent_vector::operatorOperator.md)|Sobrecargado.  Proporciona acceso al elemento en el índice especificado del vector simultáneo.  Este método es seguro para simultaneidad en las operaciones de lectura y también durante el aumento del vector, siempre que se haya asegurado de que el valor `_Index` es menor que el tamaño del vector simultáneo.|  
|[concurrent\_vector::operator\= \(Operador\)](../Topic/concurrent_vector::operator=%20Operator.md)|Sobrecargado.  Asigna el contenido de otro objeto `concurrent_vector` a este.  Este método no es seguro para la simultaneidad.|  
  
## Comentarios  
 Para obtener información detallada sobre la clase `concurrent_vector`, vea [Contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## Jerarquía de herencia  
 `_Concurrent_vector_base_v4`  
  
 `_Allocator_base`  
  
 `concurrent_vector`  
  
## Requisitos  
 **Encabezado:** concurrent\_vector.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md)