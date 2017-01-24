---
title: "unordered_map (Clase) | Microsoft Docs"
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
  - "std::tr1::unordered_map"
  - "std.tr1.unordered_map"
  - "tr1.unordered_map"
  - "tr1::unordered_map"
  - "unordered_map"
  - "unordered_map/std::tr1::unordered_map"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unordered_map (clase)"
  - "unordered_map (clase) [TR1]"
ms.assetid: 7cf7cfa1-16e7-461c-a9b2-3b8d8ec24e0d
caps.latest.revision: 20
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# unordered_map (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un objeto que controla una secuencia de longitud variable de elementos de tipo `std::pair<const Key, Ty>`.  La secuencia está ordenada débilmente por una función hash, que divide la secuencia en un conjunto ordenado subsecuencias denominadas depósitos.  Dentro de cada depósito una función de comparación determina si algún par de elementos tiene una ordenación equivalente.  Cada elemento almacena dos objetos, una clave de ordenación y un valor.  La secuencia se representan de tal forma que permite la búsqueda, inserción y eliminación de un elemento arbitrario con una serie de operaciones que pueden ser independientes del número de elementos de la secuencia \(tiempo constante\), al menos cuando todos los depósitos tienen una longitud aproximadamente igual.  En el peor de los casos, cuando todos los elementos están en un depósito, el número de operaciones es proporcional al número de elementos de la secuencia \(tiempo lineal\).  Además, la inserción de un elemento no invalida ningún iterador y al quitar un elemento solo se invalidan los iteradores que apuntan al elemento quitado.  
  
## Sintaxis  
  
```  
template<class Key,  
    class Ty,  
    class Hash = std::hash<Key>,  
    class Pred = std::equal_to<Key>,  
    class Alloc = std::allocator<std::pair<const Key, Ty> > >  
    class unordered_map;  
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
|[unordered\_map::allocator\_type](../Topic/unordered_map::allocator_type.md)|El tipo de un asignador para administrar el almacenamiento.|  
|[unordered\_map::const\_iterator](../Topic/unordered_map::const_iterator.md)|El tipo de un iterador constante para la secuencia controlada.|  
|[unordered\_map::const\_local\_iterator](../Topic/unordered_map::const_local_iterator.md)|El tipo de un iterador de depósito constante para la secuencia controlada.|  
|[unordered\_map::const\_pointer](../Topic/unordered_map::const_pointer.md)|El tipo de un puntero constante a un elemento.|  
|[unordered\_map::const\_reference](../Topic/unordered_map::const_reference.md)|El tipo de una referencia constante a un elemento.|  
|[unordered\_map::difference\_type](../Topic/unordered_map::difference_type.md)|El tipo de una distancia con signo entre dos elementos.|  
|[unordered\_map::hasher](../Topic/unordered_map::hasher.md)|El tipo de la función hash.|  
|[unordered\_map::iterator](../Topic/unordered_map::iterator.md)|El tipo de un iterador para la secuencia controlada.|  
|[unordered\_map::key\_equal](../Topic/unordered_map::key_equal.md)|El tipo de la función de comparación.|  
|[unordered\_map::key\_type](../Topic/unordered_map::key_type.md)|El tipo de una clave de ordenación.|  
|[unordered\_map::local\_iterator](../Topic/unordered_map::local_iterator.md)|El tipo de un iterador de depósito para la secuencia controlada.|  
|[unordered\_map::mapped\_type](../Topic/unordered_map::mapped_type.md)|El tipo de un valor asignado asociado a cada clave.|  
|[unordered\_map::pointer](../Topic/unordered_map::pointer.md)|El tipo de un puntero a un elemento.|  
|[unordered\_map::reference](../Topic/unordered_map::reference.md)|El tipo de una referencia a un elemento.|  
|[unordered\_map::size\_type](../Topic/unordered_map::size_type.md)|El tipo de una distancia sin signo entre dos elementos.|  
|[unordered\_map::value\_type](../Topic/unordered_map::value_type.md)|El tipo de un elemento.|  
  
|||  
|-|-|  
|Función miembro|Descripción|  
|[unordered\_map::at](../Topic/unordered_map::at.md)|Busca un elemento con la clave especificada.|  
|[unordered\_map::begin](../Topic/unordered_map::begin.md)|Designa el principio de la secuencia controlada.|  
|[unordered\_map::bucket](../Topic/unordered_map::bucket.md)|Obtiene el número de depósito para un valor de clave.|  
|[unordered\_map::bucket\_count](../Topic/unordered_map::bucket_count.md)|Obtiene el número de depósitos.|  
|[unordered\_map::bucket\_size](../Topic/unordered_map::bucket_size.md)|Obtiene el tamaño de un depósito.|  
|[unordered\_map::cbegin](../Topic/unordered_map::cbegin.md)|Designa el principio de la secuencia controlada.|  
|[unordered\_map::cend](../Topic/unordered_map::cend.md)|Designa el final de la secuencia controlada.|  
|[unordered\_map::clear](../Topic/unordered_map::clear.md)|Quita todos los elementos.|  
|[unordered\_map::count](../Topic/unordered_map::count.md)|Busca el número de elementos que coinciden con una clave especificada.|  
|[unordered\_map::emplace](../Topic/unordered_map::emplace.md)|Agrega un elemento construido en contexto.|  
|[unordered\_map::emplace\_hint](../Topic/unordered_map::emplace_hint.md)|Agrega un elemento construido en contexto, con sugerencia.|  
|[unordered\_map::empty](../Topic/unordered_map::empty.md)|Comprueba si no hay ningún elemento presente.|  
|[unordered\_map::end](../Topic/unordered_map::end.md)|Designa el final de la secuencia controlada.|  
|[unordered\_map::equal\_range](../Topic/unordered_map::equal_range.md)|Busca el intervalo que coincide con una clave especificada.|  
|[unordered\_map::erase](../Topic/unordered_map::erase.md)|Quita los elementos de las posiciones especificadas.|  
|[unordered\_map::find](../Topic/unordered_map::find.md)|Busca un elemento que coincide con una clave especificada.|  
|[unordered\_map::get\_allocator](../Topic/unordered_map::get_allocator.md)|Obtiene el objeto de asignador almacenado.|  
|[unordered\_map::hash\_function](../Topic/unordered_map::hash_function.md)|Obtiene el objeto de función hash almacenado.|  
|[unordered\_map::insert](../Topic/unordered_map::insert.md)|Agrega elementos.|  
|[unordered\_map::key\_eq](../Topic/unordered_map::key_eq.md)|Obtiene el objeto de función de comparación almacenado.|  
|[unordered\_map::load\_factor](../Topic/unordered_map::load_factor.md)|Cuenta los elementos promedio por depósito.|  
|[unordered\_map::max\_bucket\_count](../Topic/unordered_map::max_bucket_count.md)|Obtiene el número máximo de depósitos.|  
|[unordered\_map::max\_load\_factor](../Topic/unordered_map::max_load_factor.md)|Obtiene o establece los elementos máximos por depósito.|  
|[unordered\_map::max\_size](../Topic/unordered_map::max_size.md)|Obtiene el tamaño máximo de la secuencia controlada.|  
|[unordered\_map::rehash](../Topic/unordered_map::rehash.md)|Recompila la tabla hash.|  
|[unordered\_map::size](../Topic/unordered_map::size.md)|Cuenta el número de elementos.|  
|[unordered\_map::swap](../Topic/unordered_map::swap.md)|Intercambia el contenido de dos contenedores.|  
|[unordered\_map::unordered\_map](../Topic/unordered_map::unordered_map.md)|Construye un objeto contenedor.|  
  
|||  
|-|-|  
|Operador|Descripción|  
|[unordered\_map::operator](../Topic/unordered_map::operator.md)|Busca o inserta un elemento con la clave especificada.|  
|[unordered\_map::operator\=](../Topic/unordered_map::operator=.md)|Copia una tabla hash.|  
  
## Comentarios  
 El objeto ordena la secuencia que controla llamando a dos objetos almacenados, un objeto de función de comparación de tipo [unordered\_map::key\_equal](../Topic/unordered_map::key_equal.md) y un objeto de función hash de tipo [unordered\_map::hasher](../Topic/unordered_map::hasher.md).  Se tiene acceso al primer objeto almacenado llamando a la función miembro [unordered\_map::key\_eq](../Topic/unordered_map::key_eq.md)`()`; y se tiene acceso al segundo objeto almacenado llamando a la función miembro [unordered\_map::hash\_function](../Topic/unordered_map::hash_function.md)`()`.  Concretamente, para todos los valores `X` e `Y` de tipo `Key`, la llamada a `key_eq()(X, Y)` solo devuelve true si los dos valores de argumento tienen una ordenación equivalente; la llamada a `hash_function()(keyval)` produce una distribución de valores de tipo `size_t`.  A diferencia de la clase de plantilla [unordered\_multimap \(Clase\)](../standard-library/unordered-multimap-class.md), un objeto de clase de plantilla `unordered_map` garantiza que `key_eq()(X, Y)` es siempre falso para cualquiera de los dos elementos de la secuencia controlada. \(Las claves son únicas\).  
  
 El objeto también almacena un factor de carga máxima, que especifica el número promedio deseado máximo de elementos por depósito.  Si la inserción de un elemento hace que [unordered\_map::load\_factor](../Topic/unordered_map::load_factor.md)`()` supere el factor de carga máxima, el contenedor aumenta el número de depósitos y recompila la tabla hash según sea necesario.  
  
 El orden real de los elementos de la secuencia controlada depende de la función hash, la función de comparación, el orden de inserción, el factor de carga máxima y el número actual de depósitos.  En general no se puede predecir el orden de los elementos de la secuencia controlada.  Sin embargo, siempre se puede asegurar que cualquier subconjunto de elementos que tengan una ordenación equivalente son adyacentes en la secuencia controlada.  
  
 El objeto asigna y libera almacenamiento para la secuencia que controla a través de un objeto asignador almacenado de tipo [unordered\_map::allocator\_type](../Topic/unordered_map::allocator_type.md).  Ese objeto de asignador debe tener la misma interfaz externa que un objeto de clase de plantilla `allocator`.  Tenga en cuenta que el objeto de asignador almacenado no se copia cuando se asigna el objeto contenedor.  
  
## Requisitos  
 **Encabezado:** \<unordered\_map\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<unordered\_map\>](../standard-library/unordered-map.md)   
 [Contenedores](../cpp/containers-modern-cpp.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)