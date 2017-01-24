---
title: "multimap (Clase) | Microsoft Docs"
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
  - "multimap"
  - "std.multimap"
  - "map/std::multimap"
  - "std::multimap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "multimap (clase)"
ms.assetid: 8796ae05-37c4-475a-9e61-75fde9d4a463
caps.latest.revision: 23
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# multimap (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase multimap de la Biblioteca de plantillas estándar se utiliza para el almacenamiento y la recuperación de datos de una colección en la que cada elemento es un par que tiene un valor de datos y un criterio de ordenación.  El valor de la clave no necesita ser único y se utiliza para ordenar los datos automáticamente.  El valor de un elemento de una clase multimap se puede cambiar directamente, pero no su valor de clave asociado.  En su lugar, se deben eliminar los valores de clave asociados a los antiguos elementos e insertar los nuevos valores de clave asociados a los elementos nuevos.  
  
## Sintaxis  
  
```  
template <  
   class Key,   
   class Type,   
   class Traits=less<Key>,   
   class Allocator=allocator<pair <const Key, Type> >   
> class multimap;  
```  
  
#### Parámetros  
 `Key`  
 Tipo de datos de clave que se almacenará en la clase multimap.  
  
 `Type`  
 Tipo de datos de elemento que se almacenará en la clase multimap.  
  
 `Traits`  
 Tipo que proporciona un objeto de función que puede comparar dos valores de elementos como claves de ordenación para determinar su orden relativo en la clase multimap.  El predicado binario `less<Key>` es el valor predeterminado.  
  
 En C\+\+14 puede habilitar la búsqueda heterogénea especificando el predicado `std::less<>` o `std::greater<>`, que no tienen ningún parámetro de tipo.  Para obtener más información, vea el tema sobre [Búsqueda heterogénea en contenedores asociativos](../standard-library/stl-containers.md#sequence_containers)  
  
 `Allocator`  
 Tipo que representa el objeto de asignador almacenado que encapsula los detalles acerca de la asignación y desasignación de memoria de la asignación.  Este argumento es opcional y el valor predeterminado es `allocator<pair <const Key, Type> >`.  
  
## Comentarios  
 La clase STL multimap es  
  
-   Un contenedor asociativo de tamaño variable que admite la recuperación eficaz de valores de elemento según un valor de clave asociado.  
  
-   Reversible, porque proporciona iteradores bidireccionales para tener acceso a sus elementos.  
  
-   Ordenada, porque sus elementos se ordenan según los valores de clave dentro del contenedor de acuerdo con una función de comparación especificada.  
  
-   Múltiple, porque sus elementos no necesitan tener claves únicas, de modo que un valor de clave puede tener asociados varios valores de datos de elemento.  
  
-   Un contenedor asociativo de pares, ya que los valores de datos de sus elementos son distintos de sus valores de clave.  
  
-   Una clase de plantilla, porque la funcionalidad que proporciona es genérica y por tanto independiente del tipo específico de datos contenido como elementos o claves.  Los tipos de datos que se usarán para los elementos y las claves se especifican como parámetros en la plantilla de clase junto con la función de comparación y el asignador.  
  
 El iterador proporcionado por la clase map es un iterador bidireccional, pero las funciones miembro [insert](../Topic/multimap::insert.md) y [multimap](../Topic/multimap::multimap.md) de la clase tienen versiones que toman como parámetros de plantilla un iterador de entrada más débil, cuyos requisitos de funcionalidad son más mínimos que los garantizados por la clase de iteradores bidireccionales.  Los distintos conceptos de iterador forman una familia relacionada por los refinamientos de su funcionalidad.  Cada concepto de iterador tiene su propio conjunto de requisitos y los algoritmos que funcionan con ellos deben limitar sus suposiciones a los requisitos proporcionados por ese tipo de iterador.  Se puede suponer que se puede desreferenciar un iterador de entrada para hacer referencia a un objeto y que se puede incrementar hasta el iterador siguiente de la secuencia.  Se trata de un conjunto mínimo de funcionalidad, pero es suficiente para poder comunicarse sobre un intervalo de iteradores `[First, Last)` en el contexto de las funciones miembro de la clase.  
  
 En general, la elección del tipo de contenedor se debe tomar según el tipo de búsqueda y de inserción que necesite la aplicación.  Los contenedores asociativos están optimizados para las operaciones de búsqueda, inserción y eliminación.  Las funciones miembro que admiten estas operaciones explícitamente las realizan de forma eficiente en un tiempo que es proporcional en promedio al logaritmo del número de elementos del contenedor.  La inserción de elementos no invalida ningún iterador y al quitar elementos solo se invalidan los iteradores que habían apuntado específicamente a los elementos quitados.  
  
 La clase multimap debe ser el contenedor asociativo preferido cuando la aplicación satisfaga las condiciones que asocian los valores a sus claves.  Un modelo para este tipo de estructura es una lista ordenada de palabras clave con valores de cadena asociados que proporcionan por ejemplo definiciones, donde las palabras no siempre están definidas de forma única.  Si, por el contrario, las palabras clave se definieran de forma única para que fueran únicas, el contenedor más adecuado sería map.  Por otra parte, si solo se almacenara la lista de palabras, el contenedor correcto sería set.  Si se permitieran varias repeticiones de las palabras, la estructura de contenedor adecuada sería multiset.  
  
 La clase multimap ordena la secuencia que controla llamando a un objeto de función almacenado de tipo [key\_compare](../Topic/multimap::key_compare.md).  Este objeto almacenado es una función de comparación a la que se puede tener acceso llamando a la función miembro [key\_comp](../Topic/multimap::key_comp.md).  En general, se debe poder comparar si los elementos son menores que otros para poder establecer este orden; de este modo, dados dos elementos cualesquiera, se puede determinar que son equivalentes \(en el sentido de que ninguno es menor que el otro\) o que uno es menor que el otro.  Esto produce una ordenación entre los elementos no equivalentes.  En un sentido más técnico, la función de comparación es un predicado binario que induce una ordenación débil estricta en el sentido matemático estándar.  Un predicado binario `f(x,y)` es un objeto de función que tiene dos objetos de argumento `x` e `y` y un valor devuelto de true o false.  Una ordenación impuesta en un conjunto es una ordenación débil estricta si el predicado binario es irreflexivo, antisimétrico y transitivo, y si la equivalencia es transitiva, donde dos objetos `x` e `y` se definen como equivalentes cuando `f(x,y)` y `f(y,x)` son falsos.  Si la condición más fuerte de igualdad entre las claves reemplaza la de equivalencia, la ordenación se convierte en total \(en el sentido de que todos los elementos se ordenan entre sí\) y las claves coincidentes serán indiscernibles unas de otras.  
  
 En C\+\+14 puede habilitar la búsqueda heterogénea especificando el predicado `std::less<>` o `std::greater<>`, que no tienen ningún parámetro de tipo.  Para obtener más información, vea el tema sobre [Búsqueda heterogénea en contenedores asociativos](../standard-library/stl-containers.md#sequence_containers)  
  
## Miembros  
  
### Constructores  
  
|||  
|-|-|  
|[multimap](../Topic/multimap::multimap.md)|Construye un `multimap` que está vacío o que es una copia de todo o de parte de otro `multimap`.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[allocator\_type](../Topic/multimap::allocator_type.md)|Tipo que representa la clase `allocator` para el objeto `multimap`.|  
|[const\_iterator](../Topic/multimap::const_iterator.md)|Tipo que proporciona un iterador bidireccional que puede leer un elemento `const` en `multimap`.|  
|[const\_pointer](../Topic/multimap::const_pointer.md)|Tipo que proporciona un puntero a un elemento `const` en un `multimap`.|  
|[const\_reference](../Topic/multimap::const_reference.md)|Tipo que proporciona una referencia a un elemento `const` almacenado en un `multimap` para leer y realizar operaciones `const`.|  
|[const\_reverse\_iterator](../Topic/multimap::const_reverse_iterator.md)|Tipo que proporciona un iterador bidireccional que puede leer cualquier elemento `const` en `multimap`.|  
|[difference\_type](../Topic/multimap::difference_type.md)|Tipo entero con signo que se puede usar para representar el número de elementos de un `multimap` en un intervalo entre elementos a los que apuntan los iteradores.|  
|[iterator](../Topic/multimap::iterator.md)|Tipo que proporciona la diferencia entre dos iteradores que hacen referencia a elementos de la misma clase `multimap`.|  
|[key\_compare](../Topic/multimap::key_compare.md)|Tipo que proporciona un objeto de función que puede comparar dos claves de ordenación para determinar el orden relativo de dos elementos en el `multimap`.|  
|[key\_type](../Topic/multimap::key_type.md)|Tipo que describe el objeto de clave de ordenación que constituye cada elemento de `multimap`.|  
|[mapped\_type](../Topic/multimap::mapped_type.md)|Tipo que representa el tipo de datos almacenados en un `multimap`.|  
|[puntero](../Topic/multimap::pointer.md)|Tipo que proporciona un puntero a un elemento `const` en un `multimap`.|  
|[referencia](../Topic/multimap::reference.md)|Tipo que proporciona una referencia a un elemento almacenado en un `multimap`.|  
|[reverse\_iterator](../Topic/multimap::reverse_iterator.md)|Tipo que proporciona un iterador bidireccional que puede leer o modificar un elemento de `multimap` invertido.|  
|[size\_type](../Topic/multimap::size_type.md)|Un tipo entero sin signo que proporciona un puntero a un elemento `const` de una clase `multimap`.|  
|[value\_type](../Topic/multimap::value_type.md)|Tipo que proporciona un objeto de función que puede comparar dos elementos como claves de ordenación para determinar su orden relativo en el `multimap`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[begin](../Topic/multimap::begin.md)|Devuelve un iterador que direcciona el primer elemento del `multimap`.|  
|[cbegin](../Topic/multimap::cbegin.md)|Devuelve un iterador constante que direcciona el primer elemento del `multimap`.|  
|[cend](../Topic/multimap::cend.md)|Devuelve un iterador constante que direcciona la ubicación que sigue al último elemento de `multimap`.|  
|[desactivada](../Topic/multimap::clear.md)|Borra todos los elementos de un `multimap`.|  
|[count](../Topic/multimap::count.md)|Devuelve el número de elementos de un `multimap` cuya clave coincide con una clave especificada por un parámetro.|  
|[crbegin](../Topic/multimap::crbegin.md)|Devuelve un iterador constante que direcciona el primer elemento de `multimap` invertido.|  
|[crend](../Topic/multimap::crend.md)|Devuelve un iterador constante que direcciona la ubicación que sigue al último elemento de `multimap` invertido.|  
|[emplace](../Topic/multimap::emplace.md)|Inserta en un `multimap` un elemento construido en contexto.|  
|[emplace\_hint](../Topic/multimap::emplace_hint.md)|Inserta un elemento construido en contexto en `multimap`, con una sugerencia de colocación.|  
|[vacío](../Topic/multimap::empty.md)|Comprueba si un `multimap` está vacío.|  
|[end](../Topic/multimap::end.md)|Devuelve un iterador que direcciona la ubicación que sigue al último elemento de `multimap`.|  
|[equal\_range](../Topic/multimap::equal_range.md)|Encuentra el intervalo de elementos donde la clave del elemento coincide con un valor especificado.|  
|[erase](../Topic/multimap::erase.md)|Quita un elemento o un intervalo de elementos de una clase `multimap` de las posiciones especificadas o quita los elementos que coinciden con una clave especificada.|  
|[find](../Topic/multimap::find.md)|Devuelve un iterador que direcciona la primera ubicación de un elemento de `multimap` que tiene una clave equivalente a una clave especificada.|  
|[get\_allocator](../Topic/multimap::get_allocator.md)|Devuelve una copia del objeto `allocator` utilizado para construir el `multimap`.|  
|[insertar](../Topic/multimap::insert.md)|Inserta un elemento o un intervalo de elementos en un `multimap`.|  
|[key\_comp](../Topic/multimap::key_comp.md)|Recupera una copia del objeto de comparación utilizado para ordenar claves de un `multimap`.|  
|[lower\_bound](../Topic/multimap::lower_bound.md)|Devuelve un iterador al primer elemento de `multimap` cuyo valor de clave es igual o mayor que el de una clave especificada.|  
|[max\_size](../Topic/multimap::max_size.md)|Devuelve la longitud máxima del `multimap`.|  
|[rbegin](../Topic/multimap::rbegin.md)|Devuelve un iterador que direcciona el primer elemento de `multimap` invertido.|  
|[rend](../Topic/multimap::rend.md)|Devuelve un iterador que direcciona la ubicación que sigue al último elemento de `multimap` invertido.|  
|[size](../Topic/multimap::size.md)|Devuelve el número de elementos de `multimap`.|  
|[swap](../Topic/multimap::swap.md)|Intercambia los elementos de dos `multimap`.|  
|[upper\_bound](../Topic/multimap::upper_bound.md)|Devuelve un iterador al primer elemento de `multimap` con un valor de clave que es mayor que una clave especificada.|  
|[value\_comp](../Topic/multimap::value_comp.md)|La función miembro devuelve un objeto de función que determina el orden de los elementos de `multimap` mediante la comparación de sus valores de clave.|  
  
### Operadores  
  
|||  
|-|-|  
|[operador \=](../Topic/multimap::operator=.md)|Reemplaza los elementos de un `multimap` con una copia de otro `multimap`.|  
  
## Requisitos  
 **Encabezado:** \<map\>  
  
 **Espacio de nombres:** std  
  
 Los pares \(**clave**, **value**\) se almacenan en multimap como objetos de tipo `pair`.  La clase pair requiere el encabezado \<utility\>, que es automáticamente incluido por \<map\>.  
  
## Vea también  
 [miembros de \<Asignar\>](http://msdn.microsoft.com/es-es/7e8f0bc2-6034-40f6-9d14-76d4cef86308)   
 [Contenedores](../cpp/containers-modern-cpp.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)