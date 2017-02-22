---
title: "unordered_multimap (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "unordered_map/std::tr1::unordered_multimap"
  - "tr1.unordered_multimap"
  - "unordered_multimap"
  - "std.tr1.unordered_multimap"
  - "tr1::unordered_multimap"
  - "std::tr1::unordered_multimap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unordered_multimap (clase)"
  - "unordered_multimap (clase) [TR1]"
ms.assetid: 4baead6c-5870-4b85-940f-a47d6b891c27
caps.latest.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 28
---
# unordered_multimap (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un objeto que controla una secuencia de longitud variable de elementos de tipo `std::pair<const Key, Ty>`.  La secuencia está ordenada débilmente por una función hash, que divide la secuencia en un conjunto ordenado subsecuencias denominadas depósitos.  Dentro de cada depósito una función de comparación determina si algún par de elementos tiene una ordenación equivalente.  Cada elemento almacena dos objetos, una clave de ordenación y un valor.  La secuencia se representan de tal forma que permite la búsqueda, inserción y eliminación de un elemento arbitrario con una serie de operaciones que pueden ser independientes del número de elementos de la secuencia \(tiempo constante\), al menos cuando todos los depósitos tienen una longitud aproximadamente igual.  En el peor de los casos, cuando todos los elementos están en un depósito, el número de operaciones es proporcional al número de elementos de la secuencia \(tiempo lineal\).  Además, la inserción de un elemento no invalida ningún iterador y al quitar un elemento solo se invalidan los iteradores que apuntan al elemento quitado.  
  
## Sintaxis  
  
```  
template<class Key,  
    class Ty,  
    class Hash = std::hash<Key>,  
    class Pred = std::equal_to<Key>,  
    class Alloc = std::allocator<Key> >  
    class unordered_multimap;  
```  
  
#### Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`Key`|El tipo de clave.|  
|`Ty`|El tipo asignado.|  
|`Hash`|El tipo de objeto de la función hash.|  
|`Pred`|El tipo de objeto de función de comparación de igualdad.|  
|`Alloc`|Clase de asignador.|  
  
## Miembros  
  
|||  
|-|-|  
|Definición de tipo|Descripción|  
|[unordered\_multimap::allocator\_type](../Topic/unordered_multimap::allocator_type.md)|El tipo de un asignador para administrar el almacenamiento.|  
|[unordered\_multimap::const\_iterator](../Topic/unordered_multimap::const_iterator.md)|El tipo de un iterador constante para la secuencia controlada.|  
|[unordered\_multimap::const\_local\_iterator](../Topic/unordered_multimap::const_local_iterator.md)|El tipo de un iterador de depósito constante para la secuencia controlada.|  
|[unordered\_multimap::const\_pointer](../Topic/unordered_multimap::const_pointer.md)|El tipo de un puntero constante a un elemento.|  
|[unordered\_multimap::const\_reference](../Topic/unordered_multimap::const_reference.md)|El tipo de una referencia constante a un elemento.|  
|[unordered\_multimap::difference\_type](../Topic/unordered_multimap::difference_type.md)|El tipo de una distancia con signo entre dos elementos.|  
|[unordered\_multimap::hasher](../Topic/unordered_multimap::hasher.md)|El tipo de la función hash.|  
|[unordered\_multimap::iterator](../Topic/unordered_multimap::iterator.md)|El tipo de un iterador para la secuencia controlada.|  
|[unordered\_multimap::key\_equal](../Topic/unordered_multimap::key_equal.md)|El tipo de la función de comparación.|  
|[unordered\_multimap::key\_type](../Topic/unordered_multimap::key_type.md)|El tipo de una clave de ordenación.|  
|[unordered\_multimap::local\_iterator](../Topic/unordered_multimap::local_iterator.md)|El tipo de un iterador de depósito para la secuencia controlada.|  
|[unordered\_multimap::mapped\_type](../Topic/unordered_multimap::mapped_type.md)|El tipo de un valor asignado asociado a cada clave.|  
|[unordered\_multimap::pointer](../Topic/unordered_multimap::pointer.md)|El tipo de un puntero a un elemento.|  
|[unordered\_multimap::reference](../Topic/unordered_multimap::reference.md)|El tipo de una referencia a un elemento.|  
|[unordered\_multimap::size\_type](../Topic/unordered_multimap::size_type.md)|El tipo de una distancia sin signo entre dos elementos.|  
|[unordered\_multimap::value\_type](../Topic/unordered_multimap::value_type.md)|El tipo de un elemento.|  
  
|||  
|-|-|  
|Función miembro|Descripción|  
|[unordered\_multimap::begin](../Topic/unordered_multimap::begin.md)|Designa el principio de la secuencia controlada.|  
|[unordered\_multimap::bucket](../Topic/unordered_multimap::bucket.md)|Obtiene el número de depósito para un valor de clave.|  
|[unordered\_multimap::bucket\_count](../Topic/unordered_multimap::bucket_count.md)|Obtiene el número de depósitos.|  
|[unordered\_multimap::bucket\_size](../Topic/unordered_multimap::bucket_size.md)|Obtiene el tamaño de un depósito.|  
|[unordered\_multimap::cbegin](../Topic/unordered_multimap::cbegin.md)|Designa el principio de la secuencia controlada.|  
|[unordered\_multimap::cend](../Topic/unordered_multimap::cend.md)|Designa el final de la secuencia controlada.|  
|[unordered\_multimap::clear](../Topic/unordered_multimap::clear.md)|Quita todos los elementos.|  
|[unordered\_multimap::count](../Topic/unordered_multimap::count.md)|Busca el número de elementos que coinciden con una clave especificada.|  
|[unordered\_multimap::emplace](../Topic/unordered_multimap::emplace.md)|Agrega un elemento construido en contexto.|  
|[unordered\_multimap::emplace\_hint](../Topic/unordered_multimap::emplace_hint.md)|Agrega un elemento construido en contexto, con sugerencia.|  
|[unordered\_multimap::empty](../Topic/unordered_multimap::empty.md)|Comprueba si no hay ningún elemento presente.|  
|[unordered\_multimap::end](../Topic/unordered_multimap::end.md)|Designa el final de la secuencia controlada.|  
|[unordered\_multimap::equal\_range](../Topic/unordered_multimap::equal_range.md)|Busca el intervalo que coincide con una clave especificada.|  
|[unordered\_multimap::erase](../Topic/unordered_multimap::erase.md)|Quita los elementos de las posiciones especificadas.|  
|[unordered\_multimap::find](../Topic/unordered_multimap::find.md)|Busca un elemento que coincide con una clave especificada.|  
|[unordered\_multimap::get\_allocator](../Topic/unordered_multimap::get_allocator.md)|Obtiene el objeto de asignador almacenado.|  
|[unordered\_multimap::hash\_function](../Topic/unordered_multimap::hash_function.md)|Obtiene el objeto de función hash almacenado.|  
|[unordered\_multimap::insert](../Topic/unordered_multimap::insert.md)|Agrega elementos.|  
|[unordered\_multimap::key\_eq](../Topic/unordered_multimap::key_eq.md)|Obtiene el objeto de función de comparación almacenado.|  
|[unordered\_multimap::load\_factor](../Topic/unordered_multimap::load_factor.md)|Cuenta los elementos promedio por depósito.|  
|[unordered\_multimap::max\_bucket\_count](../Topic/unordered_multimap::max_bucket_count.md)|Obtiene el número máximo de depósitos.|  
|[unordered\_multimap::max\_load\_factor](../Topic/unordered_multimap::max_load_factor.md)|Obtiene o establece los elementos máximos por depósito.|  
|[unordered\_multimap::max\_size](../Topic/unordered_multimap::max_size.md)|Obtiene el tamaño máximo de la secuencia controlada.|  
|[unordered\_multimap::rehash](../Topic/unordered_multimap::rehash.md)|Recompila la tabla hash.|  
|[unordered\_multimap::size](../Topic/unordered_multimap::size.md)|Cuenta el número de elementos.|  
|[unordered\_multimap::swap](../Topic/unordered_multimap::swap.md)|Intercambia el contenido de dos contenedores.|  
|[unordered\_multimap::unordered\_multimap](../Topic/unordered_multimap::unordered_multimap.md)|Construye un objeto contenedor.|  
  
|||  
|-|-|  
|Operador|Descripción|  
|[unordered\_multimap::operator\=](../Topic/unordered_multimap::operator=.md)|Copia una tabla hash.|  
  
## Comentarios  
 El objeto ordena la secuencia que controla llamando a dos objetos almacenados, un objeto de función de comparación de tipo [unordered\_multimap::key\_equal](../Topic/unordered_multimap::key_equal.md) y un objeto de función hash de tipo [unordered\_multimap::hasher](../Topic/unordered_multimap::hasher.md).  Se tiene acceso al primer objeto almacenado llamando a la función miembro [unordered\_multimap::key\_eq](../Topic/unordered_multimap::key_eq.md)`()`; y se tiene acceso al segundo objeto almacenado llamando a la función miembro [unordered\_multimap::hash\_function](../Topic/unordered_multimap::hash_function.md)`()`.  Concretamente, para todos los valores `X` e `Y` de tipo `Key`, la llamada a `key_eq()(X, Y)` solo devuelve true si los dos valores de argumento tienen una ordenación equivalente; la llamada a `hash_function()(keyval)` produce una distribución de valores de tipo `size_t`.  A diferencia de la clase de plantilla [unordered\_map \(Clase\)](../standard-library/unordered-map-class.md), un objeto de clase de plantilla `unordered_multimap` no garantiza que `key_eq()(X, Y)` es siempre false para dos elementos cualesquiera de la secuencia controlada. \(No es necesario que las claves sean únicas\).  
  
 El objeto también almacena un factor de carga máxima, que especifica el número promedio deseado máximo de elementos por depósito.  Si la inserción de un elemento hace que [unordered\_multimap::load\_factor](../Topic/unordered_multimap::load_factor.md)`()` supere el factor de carga máxima, el contenedor aumenta el número de depósitos y recompila la tabla hash según sea necesario.  
  
 El orden real de los elementos de la secuencia controlada depende de la función hash, la función de comparación, el orden de inserción, el factor de carga máxima y el número actual de depósitos.  En general no se puede predecir el orden de los elementos de la secuencia controlada.  Sin embargo, siempre se puede asegurar que cualquier subconjunto de elementos que tengan una ordenación equivalente son adyacentes en la secuencia controlada.  
  
 El objeto asigna y libera almacenamiento para la secuencia que controla a través de un objeto asignador almacenado de tipo [unordered\_multimap::allocator\_type](../Topic/unordered_multimap::allocator_type.md).  Ese objeto de asignador debe tener la misma interfaz externa que un objeto de clase de plantilla `allocator`.  Tenga en cuenta que el objeto de asignador almacenado no se copia cuando se asigna el objeto contenedor.  
  
## Requisitos  
 **Encabezado:** \<unordered\_map\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<unordered\_map\>](../standard-library/unordered-map.md)   
 [Contenedores](../cpp/containers-modern-cpp.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)