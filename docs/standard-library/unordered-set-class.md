---
title: "unordered_set (Clase) | Microsoft Docs"
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
  - "std.tr1.unordered_set"
  - "std::tr1::unordered_set"
  - "unordered_set/std::tr1::unordered_set"
  - "tr1::unordered_set"
  - "unordered_set"
  - "tr1.unordered_set"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unordered_set (clase)"
  - "unordered_set (clase) [TR1]"
ms.assetid: ac08084e-05a7-48c0-9ae4-d40c529922dd
caps.latest.revision: 23
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# unordered_set (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un objeto que controla una secuencia de longitud variable de elementos de tipo `const Key`.  La secuencia está ordenada débilmente por una función hash, que divide la secuencia en un conjunto ordenado subsecuencias denominadas depósitos.  Dentro de cada depósito una función de comparación determina si algún par de elementos tiene una ordenación equivalente.  Cada elemento actúa como clave de ordenación y como valor.  La secuencia se representan de tal forma que permite la búsqueda, inserción y eliminación de un elemento arbitrario con una serie de operaciones que pueden ser independientes del número de elementos de la secuencia \(tiempo constante\), al menos cuando todos los depósitos tienen una longitud aproximadamente igual.  En el peor de los casos, cuando todos los elementos están en un depósito, el número de operaciones es proporcional al número de elementos de la secuencia \(tiempo lineal\).  Además, la inserción de un elemento no invalida ningún iterador y al quitar un elemento solo se invalidan los iteradores que apuntan al elemento quitado.  
  
## Sintaxis  
  
```  
template<class Key,  
    class Hash = std::hash<Key>,  
    class Pred = std::equal_to<Key>,  
    class Alloc = std::allocator<Key> >  
    class unordered_set;  
```  
  
#### Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`Key`|El tipo de clave.|  
|`Hash`|El tipo de objeto de la función hash.|  
|`Pred`|El tipo de objeto de función de comparación de igualdad.|  
|`Alloc`|Clase de asignador.|  
  
## Miembros  
  
|||  
|-|-|  
|Definición de tipo|Descripción|  
|[unordered\_set::allocator\_type](../Topic/unordered_set::allocator_type.md)|El tipo de un asignador para administrar el almacenamiento.|  
|[unordered\_set::const\_iterator](../Topic/unordered_set::const_iterator.md)|El tipo de un iterador constante para la secuencia controlada.|  
|[unordered\_set::const\_local\_iterator](../Topic/unordered_set::const_local_iterator.md)|El tipo de un iterador de depósito constante para la secuencia controlada.|  
|[unordered\_set::const\_pointer](../Topic/unordered_set::const_pointer.md)|El tipo de un puntero constante a un elemento.|  
|[unordered\_set::const\_reference](../Topic/unordered_set::const_reference.md)|El tipo de una referencia constante a un elemento.|  
|[unordered\_set::difference\_type](../Topic/unordered_set::difference_type.md)|El tipo de una distancia con signo entre dos elementos.|  
|[unordered\_set::hasher](../Topic/unordered_set::hasher.md)|El tipo de la función hash.|  
|[unordered\_set::iterator](../Topic/unordered_set::iterator.md)|El tipo de un iterador para la secuencia controlada.|  
|[unordered\_set::key\_equal](../Topic/unordered_set::key_equal.md)|El tipo de la función de comparación.|  
|[unordered\_set::key\_type](../Topic/unordered_set::key_type.md)|El tipo de una clave de ordenación.|  
|[unordered\_set::local\_iterator](../Topic/unordered_set::local_iterator.md)|El tipo de un iterador de depósito para la secuencia controlada.|  
|[unordered\_set::pointer](../Topic/unordered_set::pointer.md)|El tipo de un puntero a un elemento.|  
|[unordered\_set::reference](../Topic/unordered_set::reference.md)|El tipo de una referencia a un elemento.|  
|[unordered\_set::size\_type](../Topic/unordered_set::size_type.md)|El tipo de una distancia sin signo entre dos elementos.|  
|[unordered\_set::value\_type](../Topic/unordered_set::value_type.md)|El tipo de un elemento.|  
  
|||  
|-|-|  
|Función miembro|Descripción|  
|[unordered\_set::begin](../Topic/unordered_set::begin.md)|Designa el principio de la secuencia controlada.|  
|[unordered\_set::bucket](../Topic/unordered_set::bucket.md)|Obtiene el número de depósito para un valor de clave.|  
|[unordered\_set::bucket\_count](../Topic/unordered_set::bucket_count.md)|Obtiene el número de depósitos.|  
|[unordered\_set::bucket\_size](../Topic/unordered_set::bucket_size.md)|Obtiene el tamaño de un depósito.|  
|[unordered\_set::cbegin](../Topic/unordered_set::cbegin.md)|Designa el principio de la secuencia controlada.|  
|[unordered\_set::cend](../Topic/unordered_set::cend.md)|Designa el final de la secuencia controlada.|  
|[unordered\_set::clear](../Topic/unordered_set::clear.md)|Quita todos los elementos.|  
|[unordered\_set::count](../Topic/unordered_set::count.md)|Busca el número de elementos que coinciden con una clave especificada.|  
|[unordered\_set::emplace](../Topic/unordered_set::emplace.md)|Agrega un elemento construido en contexto.|  
|[unordered\_set::emplace\_hint](../Topic/unordered_set::emplace_hint.md)|Agrega un elemento construido en contexto, con sugerencia.|  
|[unordered\_set::empty](../Topic/unordered_set::empty.md)|Comprueba si no hay ningún elemento presente.|  
|[unordered\_set::end](../Topic/unordered_set::end.md)|Designa el final de la secuencia controlada.|  
|[unordered\_set::equal\_range](../Topic/unordered_set::equal_range.md)|Busca el intervalo que coincide con una clave especificada.|  
|[unordered\_set::erase](../Topic/unordered_set::erase.md)|Quita los elementos de las posiciones especificadas.|  
|[unordered\_set::find](../Topic/unordered_set::find.md)|Busca un elemento que coincide con una clave especificada.|  
|[unordered\_set::get\_allocator](../Topic/unordered_set::get_allocator.md)|Obtiene el objeto de asignador almacenado.|  
|[unordered\_set::hash\_function](../Topic/unordered_set::hash_function.md)|Obtiene el objeto de función hash almacenado.|  
|[unordered\_set::insert](../Topic/unordered_set::insert.md)|Agrega elementos.|  
|[unordered\_set::key\_eq](../Topic/unordered_set::key_eq.md)|Obtiene el objeto de función de comparación almacenado.|  
|[unordered\_set::load\_factor](../Topic/unordered_set::load_factor.md)|Cuenta los elementos promedio por depósito.|  
|[unordered\_set::max\_bucket\_count](../Topic/unordered_set::max_bucket_count.md)|Obtiene el número máximo de depósitos.|  
|[unordered\_set::max\_load\_factor](../Topic/unordered_set::max_load_factor.md)|Obtiene o establece los elementos máximos por depósito.|  
|[unordered\_set::max\_size](../Topic/unordered_set::max_size.md)|Obtiene el tamaño máximo de la secuencia controlada.|  
|[unordered\_set::rehash](../Topic/unordered_set::rehash.md)|Recompila la tabla hash.|  
|[unordered\_set::size](../Topic/unordered_set::size.md)|Cuenta el número de elementos.|  
|[unordered\_set::swap](../Topic/unordered_set::swap.md)|Intercambia el contenido de dos contenedores.|  
|[unordered\_set::unordered\_set](../Topic/unordered_set::unordered_set.md)|Construye un objeto contenedor.|  
  
|||  
|-|-|  
|Operadores|Descripción|  
|[unordered\_set::operator\=](../Topic/unordered_set::operator=.md)|Copia una tabla hash.|  
  
## Comentarios  
 El objeto ordena la secuencia que controla llamando a dos objetos almacenados, un objeto de función de comparación de tipo [unordered\_set::key\_equal](../Topic/unordered_set::key_equal.md) y un objeto de función hash de tipo [unordered\_set::hasher](../Topic/unordered_set::hasher.md).  Se tiene acceso al primer objeto almacenado llamando a la función miembro [unordered\_set::key\_eq](../Topic/unordered_set::key_eq.md)`()`; y se tiene acceso al segundo objeto almacenado llamando a la función miembro [unordered\_set::hash\_function](../Topic/unordered_set::hash_function.md)`()`.  Concretamente, para todos los valores `X` e `Y` de tipo `Key`, la llamada a `key_eq()(X, Y)` solo devuelve true si los dos valores de argumento tienen una ordenación equivalente; la llamada a `hash_function()(keyval)` produce una distribución de valores de tipo `size_t`.  A diferencia de la clase de plantilla [unordered\_multiset \(Clase\)](../standard-library/unordered-multiset-class.md), un objeto de clase de plantilla `unordered_set` garantiza que `key_eq()(X, Y)` es siempre falso para cualquiera de los dos elementos de la secuencia controlada. \(Las claves son únicas\).  
  
 El objeto también almacena un factor de carga máxima, que especifica el número promedio deseado máximo de elementos por depósito.  Si la inserción de un elemento hace que [unordered\_set::load\_factor](../Topic/unordered_set::load_factor.md)`()` supere el factor de carga máxima, el contenedor aumenta el número de depósitos y recompila la tabla hash según sea necesario.  
  
 El orden real de los elementos de la secuencia controlada depende de la función hash, la función de comparación, el orden de inserción, el factor de carga máxima y el número actual de depósitos.  En general no se puede predecir el orden de los elementos de la secuencia controlada.  Sin embargo, siempre se puede asegurar que cualquier subconjunto de elementos que tengan una ordenación equivalente son adyacentes en la secuencia controlada.  
  
 El objeto asigna y libera almacenamiento para la secuencia que controla a través de un objeto asignador almacenado de tipo [unordered\_set::allocator\_type](../Topic/unordered_set::allocator_type.md).  Ese objeto de asignador debe tener la misma interfaz externa que un objeto de clase de plantilla `allocator`.  Tenga en cuenta que el objeto de asignador almacenado no se copia cuando se asigna el objeto contenedor.  
  
## Requisitos  
 **Encabezado:** \<unordered\_set\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<unordered\_set\>](../standard-library/unordered-set.md)   
 [Contenedores](../cpp/containers-modern-cpp.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)