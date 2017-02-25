---
title: "concurrent_unordered_multiset (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concurrent_unordered_set/concurrency::concurrent_unordered_multiset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "concurrent_unordered_multiset (clase)"
ms.assetid: 219d7d67-1ff0-45f4-9400-e9cc272991a4
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# concurrent_unordered_multiset (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La clase `concurrent_unordered_multiset` es un contenedor seguro para simultaneidad que controla una secuencia de elementos de longitud variable del tipo \_Key\_type.  La secuencia se representa de una manera que habilita la anexión segura para simultaneidad, el acceso a elementos, el acceso a iterador y las operaciones de recorrido de iterador.  
  
## Sintaxis  
  
```  
template <  
   typename _Key_type,  
   typename _Hasher = std::tr1::hash<_Key_type>,  
   typename _Key_equality = std::equal_to<_Key_type>,  
   typename _Allocator_type = std::allocator<_Key_type>  
>  
, typename _Key_equality = std::equal_to<_Key_type>, typename _Allocator_type = std::allocator<_Key_type> > class concurrent_unordered_multiset : public details::_Concurrent_hash< details::_Concurrent_unordered_set_traits<_Key_type, details::_Hash_compare<_Key_type, _Hasher, _Key_equality>, _Allocator_type, true> >;  
```  
  
#### Parámetros  
 `_Key_type`  
 El tipo de clave.  
  
 `_Hasher`  
 El tipo de objeto de la función hash.  Este argumento es opcional y el valor predeterminado es `std::tr1::hash<``_Key_type``>`.  
  
 `_Key_equality`  
 El tipo de objeto de función de comparación de igualdad.  Este argumento es opcional y el valor predeterminado es `std::equal_to<``_Key_type``>`.  
  
 `_Allocator_type`  
 El tipo que representa el objeto de asignador almacenado que encapsula los detalles acerca de la asignación y desasignación de memoria para el vector simultáneo.  Este argumento es opcional y el valor predeterminado es `std::allocator<``_Key_type``>`.  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`allocator_type`|El tipo de un asignador para administrar el almacenamiento.|  
|`const_iterator`|El tipo de un iterador constante para la secuencia controlada.|  
|`const_local_iterator`|El tipo de un iterador de depósito constante para la secuencia controlada.|  
|`const_pointer`|El tipo de un puntero constante a un elemento.|  
|`const_reference`|El tipo de una referencia constante a un elemento.|  
|`difference_type`|El tipo de una distancia con signo entre dos elementos.|  
|`hasher`|El tipo de la función hash.|  
|`iterator`|El tipo de un iterador para la secuencia controlada.|  
|`key_equal`|El tipo de la función de comparación.|  
|`key_type`|El tipo de una clave de ordenación.|  
|`local_iterator`|El tipo de un iterador de depósito para la secuencia controlada.|  
|`pointer`|El tipo de un puntero a un elemento.|  
|`reference`|El tipo de una referencia a un elemento.|  
|`size_type`|El tipo de una distancia sin signo entre dos elementos.|  
|`value_type`|El tipo de un elemento.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[concurrent\_unordered\_multiset::concurrent\_unordered\_multiset \(Constructor\)](../Topic/concurrent_unordered_multiset::concurrent_unordered_multiset%20Constructor.md)|Sobrecargado.  Construye un conjunto múltiple desordenado simultáneo.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[concurrent\_unordered\_multiset::hash\_function \(Método\)](../Topic/concurrent_unordered_multiset::hash_function%20Method.md)|Devuelve el objeto almacenado de la función hash.|  
|[concurrent\_unordered\_multiset::insert \(Método\)](../Topic/concurrent_unordered_multiset::insert%20Method.md)|Sobrecargado.  Agrega elementos al objeto `concurrent_unordered_multiset`.|  
|[concurrent\_unordered\_multiset::key\_eq \(Método\)](../Topic/concurrent_unordered_multiset::key_eq%20Method.md)|El objeto de función de comparación de igualdad almacenado.|  
|[concurrent\_unordered\_multiset::swap \(Método\)](../Topic/concurrent_unordered_multiset::swap%20Method.md)|Intercambia el contenido de dos objetos `concurrent_unordered_multiset`.  Este método no es seguro para la simultaneidad.|  
|[concurrent\_unordered\_multiset::unsafe\_erase \(Método\)](../Topic/concurrent_unordered_multiset::unsafe_erase%20Method.md)|Sobrecargado.  Quita los elementos de `concurrent_unordered_multiset` en las posiciones especificadas.  Este método no es seguro para la simultaneidad.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[concurrent\_unordered\_multiset::operator\= \(Operador\)](../Topic/concurrent_unordered_multiset::operator=%20Operator.md)|Sobrecargado.  Asigna el contenido de otro objeto `concurrent_unordered_multiset` a este.  Este método no es seguro para la simultaneidad.|  
  
## Comentarios  
 Para obtener información detallada sobre la clase `concurrent_unordered_multiset`, vea [Contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## Jerarquía de herencia  
 `_Traits`  
  
 `_Concurrent_hash`  
  
 `concurrent_unordered_multiset`  
  
## Requisitos  
 **Encabezado:** concurrent\_unordered\_set.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md)