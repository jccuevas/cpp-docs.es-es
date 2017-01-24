---
title: "concurrent_unordered_map (Clase) | Microsoft Docs"
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
  - "concurrent_unordered_map/concurrency::concurrent_unordered_map"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "concurrent_unordered_map (clase)"
ms.assetid: b2d879dd-87ef-4af9-a266-a5443fd538b8
caps.latest.revision: 13
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# concurrent_unordered_map (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La clase `concurrent_unordered_map` es un contenedor seguro para simultaneidad que controla una secuencia de variación de longitud de elementos del tipo `std::pair<const _Key_type, _Element_type>`.  La secuencia se representa de una manera que habilita la anexión segura para simultaneidad, el acceso a elementos, el acceso a iterador y las operaciones de recorrido de iterador.  
  
## Sintaxis  
  
```  
template <  
   typename _Key_type,  
   typename _Element_type,  
   typename _Hasher = std::tr1::hash<_Key_type>,  
   typename _Key_equality = std::equal_to<_Key_type>,  
   typename _Allocator_type = std::allocator<std::pair<const _Key_type,  
   _Element_type> >  
>  
, typename _Key_equality = std::equal_to<_Key_type>, typename _Allocator_type = std::allocator<std::pair<const _Key_type, _Element_type> > > class concurrent_unordered_map : public details::_Concurrent_hash< details::_Concurrent_unordered_map_traits<_Key_type, _Element_type, details::_Hash_compare<_Key_type, _Hasher, _Key_equality>, _Allocator_type, false> >;  
```  
  
#### Parámetros  
 `_Key_type`  
 El tipo de clave.  
  
 `_Element_type`  
 El tipo asignado.  
  
 `_Hasher`  
 El tipo de objeto de la función hash.  Este argumento es opcional y el valor predeterminado es `std::tr1::hash<``_Key_type``>`.  
  
 `_Key_equality`  
 El tipo de objeto de función de comparación de igualdad.  Este argumento es opcional y el valor predeterminado es `std::equal_to<``_Key_type``>`.  
  
 `_Allocator_type`  
 El tipo que representa el objeto de asignador almacenado que encapsula los detalles acerca de la asignación y desasignación de memoria para el mapa no ordenado simultáneo.  Este argumento es opcional y el valor predeterminado es `std::allocator<std::pair<``_Key_type`, `_Element_type``>>`.  
  
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
|`mapped_type`|El tipo de un valor asignado asociado a cada clave.|  
|`pointer`|El tipo de un puntero a un elemento.|  
|`reference`|El tipo de una referencia a un elemento.|  
|`size_type`|El tipo de una distancia sin signo entre dos elementos.|  
|`value_type`|El tipo de un elemento.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[concurrent\_unordered\_map::concurrent\_unordered\_map \(Constructor\)](../Topic/concurrent_unordered_map::concurrent_unordered_map%20Constructor.md)|Sobrecargado.  Construye un mapa no ordenado simultáneo.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[concurrent\_unordered\_map::at \(Método\)](../Topic/concurrent_unordered_map::at%20Method.md)|Sobrecargado.  Busca un elemento en `concurrent_unordered_map` con un valor de clave especificado.  Este método es seguro para simultaneidad.|  
|[concurrent\_unordered\_map::hash\_function \(Método\)](../Topic/concurrent_unordered_map::hash_function%20Method.md)|Obtiene el objeto almacenado de la función hash.|  
|[concurrent\_unordered\_map::insert \(Método\)](../Topic/concurrent_unordered_map::insert%20Method.md)|Sobrecargado.  Agrega elementos al objeto `concurrent_unordered_map`.|  
|[concurrent\_unordered\_map::key\_eq \(Método\)](../Topic/concurrent_unordered_map::key_eq%20Method.md)|Obtiene el objeto de función de comparación de igualdad almacenado.|  
|[concurrent\_unordered\_map::swap \(Método\)](../Topic/concurrent_unordered_map::swap%20Method.md)|Intercambia el contenido de dos objetos `concurrent_unordered_map`.  Este método no es seguro para la simultaneidad.|  
|[concurrent\_unordered\_map::unsafe\_erase \(Método\)](../Topic/concurrent_unordered_map::unsafe_erase%20Method.md)|Sobrecargado.  Quita los elementos de `concurrent_unordered_map` en las posiciones especificadas.  Este método no es seguro para la simultaneidad.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[concurrent\_unordered\_map::operatorOperator](../Topic/concurrent_unordered_map::operatorOperator.md)|Sobrecargado.  Busca o inserta un elemento con la clave especificada.  Este método es seguro para simultaneidad.|  
|[concurrent\_unordered\_map::operator\= \(Operador\)](../Topic/concurrent_unordered_map::operator=%20Operator.md)|Sobrecargado.  Asigna el contenido de otro objeto `concurrent_unordered_map` a este.  Este método no es seguro para la simultaneidad.|  
  
## Comentarios  
 Para obtener información detallada sobre la clase `concurrent_unordered_map`, vea [Contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## Jerarquía de herencia  
 `_Traits`  
  
 `_Concurrent_hash`  
  
 `concurrent_unordered_map`  
  
## Requisitos  
 **Encabezado:** concurrent\_unordered\_map.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md)