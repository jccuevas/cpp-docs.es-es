---
title: "set (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::set"
  - "set"
  - "set/std::set"
  - "std.set"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "set (clase)"
ms.assetid: 8991f9aa-5509-4440-adc1-371512d32018
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# set (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El conjunto de clases contenedoras STL se usa para el almacenamiento y la recuperación de datos de una colección en la que los valores de los elementos contenidos son únicos y sirven como valores de clave según los cuales se ordenan automáticamente los datos.  El valor de un elemento de un conjunto no se puede cambiar directamente.  Lo que se debe hacer es eliminar los valores antiguos e insertar elementos con nuevos valores.  
  
## Sintaxis  
  
```  
template <  
    class Key,   
    class Traits=less<Key>,   
    class Allocator=allocator<Key>   
>  
class set  
```  
  
#### Parámetros  
 `Key`  
 Tipo de datos de los elementos que se va a almacenar en el conjunto.  
  
 `Traits`  
 Tipo que proporciona un objeto de función que puede comparar dos valores de elementos como criterios de ordenación para determinar su orden relativo en el conjunto.  Este argumento es opcional y el predicado binario **less***\<Key\>* es el valor predeterminado.  
  
 En C\+\+14 puede habilitar la búsqueda heterogénea especificando el predicado `std::less<>` o `std::greater<>`, que no tienen ningún parámetro de tipo.  Para obtener más información, vea el tema sobre [Búsqueda heterogénea en contenedores asociativos](../standard-library/stl-containers.md#sequence_containers)  
  
 `Allocator`  
 Tipo que representa el objeto asignador almacenado que encapsula los detalles acerca de la asignación y desasignación de memoria del conjunto.  Este argumento es opcional y el valor predeterminado es **allocator***\<Key\>.*  
  
## Comentarios  
 Un conjunto STL es:  
  
-   Un contenedor asociativo de tamaño variable que admite la recuperación eficaz de valores de elemento según un valor de clave asociado.  Es más, es un contenedor asociativo simple porque los valores de elemento son sus valores de clave.  
  
-   Reversible, porque proporciona un iterador bidireccional para tener acceso a sus elementos.  
  
-   Ordenada, porque sus elementos se ordenan según los valores de clave dentro del contenedor de acuerdo con una función de comparación especificada.  
  
-   Único en el sentido de que cada uno de sus elementos debe tener una clave única.  Puesto que el conjunto es también un contenedor asociativo simple, sus elementos también son únicos.  
  
 Un conjunto también se describe como una clase de plantilla, porque la funcionalidad que proporciona es genérica e independiente del tipo específico de datos contenidos como elementos.  En su lugar, el tipo de datos que se usará se especifica como un parámetro en la plantilla de clase junto con la función de comparación y el asignador.  
  
 En general, la elección del tipo de contenedor se debe tomar según el tipo de búsqueda y de inserción que necesite la aplicación.  Los contenedores asociativos están optimizados para las operaciones de búsqueda, inserción y eliminación.  Las funciones miembro que admiten estas operaciones explícitamente las realizan de forma eficiente en un tiempo que es proporcional en promedio al logaritmo del número de elementos del contenedor.  La inserción de elementos no invalida ningún iterador y al quitar elementos solo se invalidan los iteradores que habían apuntado específicamente a los elementos quitados.  
  
 El conjunto debe ser el contenedor asociativo elegido cuando la aplicación satisfaga las condiciones que asocian los valores a sus claves.  Los elementos de un conjunto son únicos y actúan como sus propios criterios de ordenación.  Un modelo para este tipo de estructura es una lista ordenada, por ejemplo, de palabras en las que las palabras pueden aparecer solo una vez.  Si se permitieran varias repeticiones de las palabras, la estructura de contenedor adecuada sería multiset.  Si los valores necesitan estar asociados a una lista de palabras clave únicas, un mapa sería una estructura adecuada para contener estos datos.  Si, por el contrario, las claves no son únicas, un multimap sería el contenedor preferido.  
  
 El conjunto ordena la secuencia que controla llamando a un objeto de función almacenado de tipo [key\_compare](../Topic/set::key_compare.md).  Este objeto almacenado es una función de comparación a la que se puede tener acceso llamando a la función miembro [key\_comp](../Topic/set::key_comp.md).  En general, los elementos deben ser meramente menos que comparables para establecer este orden de forma que, dados dos elementos cualesquiera, se pueda determinar que son equivalentes \(en el sentido de que ninguno es menor que el otro\) o que uno es menor que el otro.  Esto produce una ordenación entre los elementos no equivalentes.  En un sentido más técnico, la función de comparación es un predicado binario que induce una ordenación débil estricta en el sentido matemático estándar.  Un predicado binario *f*\(*x,y*\) es un objeto de función que tiene dos objetos de argumento *x* e *y*, y un valor devuelto de **true** o **false**.  Una ordenación impuesta en un conjunto es una ordenación débil estricta si el predicado binario es irreflexivo, antisimétrico y transitivo, y si la equivalencia es transitiva, donde dos objetos *x* e *y* se definen como equivalentes cuando tanto *f*\(*x,y*\) como *f*\(*y,x*\) son false.  Si la condición más fuerte de igualdad entre las claves reemplaza la de equivalencia, la ordenación se convierte en total \(en el sentido de que todos los elementos se ordenan entre sí\) y las claves coincidentes serán indiscernibles unas de otras.  
  
 En C\+\+14 puede habilitar la búsqueda heterogénea especificando el predicado `std::less<>` o `std::greater<>`, que no tienen ningún parámetro de tipo.  Para obtener más información, vea el tema sobre [Búsqueda heterogénea en contenedores asociativos](../standard-library/stl-containers.md#sequence_containers)  
  
 El iterador proporcionado por la clase del conjunto es un iterador bidireccional, pero las funciones miembro de la clase [insert](../Topic/set::insert.md) y [conjunto](../Topic/set::set.md) tienen versiones que toman como parámetros de plantilla un iterador de entrada más débil, cuyos requisitos de funcionalidad son más mínimos que los garantizados por la clase de iteradores bidireccionales.  Los distintos conceptos de iterador forman una familia relacionada por los refinamientos de su funcionalidad.  Cada concepto de iterador tiene su propio conjunto de requisitos, y los algoritmos que funcionan con ellos deben limitar sus suposiciones a los requisitos proporcionados por ese tipo de iterador.  Se puede suponer que se puede desreferenciar un iterador de entrada para hacer referencia a un objeto y que se puede incrementar hasta el iterador siguiente de la secuencia.  Se trata de un conjunto mínimo de funcionalidad, pero es suficiente para poder comunicarse sobre un intervalo de iteradores \[`First`, `Last`\) en el contexto de las funciones miembro de clase.  
  
### Constructores  
  
|||  
|-|-|  
|[establecer](../Topic/set::set.md)|Construye un conjunto que está vacío o que es una copia de todo o de parte de otro conjunto.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[allocator\_type](../Topic/set::allocator_type.md)|Tipo que representa la clase `allocator` para el conjunto.|  
|[const\_iterator](../Topic/set::const_iterator.md)|Tipo que proporciona un iterador bidireccional que puede leer un elemento `const` en el conjunto.|  
|[const\_pointer](../Topic/set::const_pointer.md)|Tipo que proporciona un puntero a un elemento `const` en un conjunto.|  
|[const\_reference](../Topic/set::const_reference.md)|Tipo que proporciona una referencia a un elemento `const` almacenado en un conjunto para leer y realizar operaciones `const`.|  
|[const\_reverse\_iterator](../Topic/set::const_reverse_iterator.md)|Tipo que proporciona un iterador bidireccional que puede leer cualquier elemento `const` del conjunto.|  
|[difference\_type](../Topic/set::difference_type.md)|Tipo entero con signo que se puede usar para representar el número de elementos de un conjunto en un intervalo entre elementos a los que apuntan los iteradores.|  
|[iterator](../Topic/set::iterator.md)|Tipo que proporciona un iterador bidireccional que puede leer o modificar cualquier elemento de un conjunto.|  
|[key\_compare](../Topic/set::key_compare.md)|Tipo que proporciona un objeto de función que puede comparar dos criterios de ordenación para determinar el orden relativo de dos elementos en el conjunto.|  
|[key\_type](../Topic/set::key_type.md)|El tipo describe un objeto almacenado como un elemento de un conjunto en su capacidad como criterio de ordenación.|  
|[puntero](../Topic/set::pointer.md)|Tipo que proporciona un puntero a un elemento de un conjunto.|  
|[referencia](../Topic/set::reference.md)|Tipo que proporciona una referencia a un elemento almacenado en un conjunto.|  
|[reverse\_iterator](../Topic/set::reverse_iterator.md)|Tipo que proporciona un iterador bidireccional que puede leer o modificar un elemento en un conjunto invertido.|  
|[size\_type](../Topic/set::size_type.md)|Tipo entero sin signo que puede representar el número de elementos de un conjunto.|  
|[value\_compare](../Topic/set::value_compare.md)|Tipo que proporciona un objeto de función que puede comparar dos elementos como criterios de ordenación para determinar su orden relativo en el conjunto.|  
|[value\_type](../Topic/set::value_type.md)|El tipo describe un objeto almacenado como un elemento de un conjunto en su capacidad como valor.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[begin](../Topic/set::begin.md)|Devuelve un iterador que direcciona el primer elemento del conjunto.|  
|[cbegin](../Topic/set::cbegin.md)|Devuelve un iterador const que direcciona el primer elemento del conjunto.|  
|[cend](../Topic/set::cend.md)|Devuelve un iterador constante que direcciona la ubicación que sigue al último elemento de un conjunto.|  
|[desactivada](../Topic/set::clear.md)|Borra todos los elementos de un conjunto.|  
|[count](../Topic/set::count.md)|Devuelve el número de elementos de un conjunto cuya clave coincide con una clave especificada por un parámetro.|  
|[crbegin](../Topic/set::rbegin.md)|Devuelve un iterador const que direcciona el primer elemento de un set invertido.|  
|[crend](../Topic/set::rend.md)|Devuelve un iterador const que direcciona la ubicación que sigue al último elemento de un set invertido.|  
|[emplace](../Topic/set::emplace.md)|Inserta un elemento construido en contexto dentro de un conjunto.|  
|[emplace\_hint](../Topic/set::emplace_hint.md)|Inserta un elemento construido en contexto dentro de un conjunto, con una sugerencia de colocación.|  
|[vacío](../Topic/set::empty.md)|Comprueba si un conjunto está vacío.|  
|[end](../Topic/set::end.md)|Devuelve un iterador que direcciona la ubicación que sigue al último elemento de un conjunto.|  
|[equal\_range](../Topic/set::equal_range.md)|Devuelve un par de iteradores, respectivamente, al primer elemento de un conjunto cuya clave mayor es que una clave especificada y al primer elemento del conjunto cuya clave es igual o mayor que la clave especificada.|  
|[erase](../Topic/set::erase.md)|Quita un elemento o un intervalo de elementos de un conjunto de las posiciones especificadas o quita los elementos que coinciden con una clave especificada.|  
|[find](../Topic/set::find.md)|Devuelve un iterador que direcciona la ubicación de un elemento en un conjunto que tiene una clave equivalente a una clave especificada.|  
|[get\_allocator](../Topic/set::get_allocator.md)|Devuelve una copia del objeto `allocator` utilizado para construir el conjunto.|  
|[insertar](../Topic/set::insert.md)|Inserta un elemento o un intervalo de elementos en un conjunto.|  
|[key\_comp](../Topic/set::key_comp.md)|Recupera una copia del objeto de comparación utilizado para ordenar claves de un conjunto.|  
|[lower\_bound](../Topic/set::lower_bound.md)|Devuelve un iterador al primer elemento de un conjunto cuyo valor de clave es igual o mayor que el de una clave especificada.|  
|[max\_size](../Topic/set::max_size.md)|Devuelve la longitud máxima del conjunto.|  
|[rbegin](../Topic/set::rbegin.md)|Devuelve un iterador que direcciona el primer elemento en un conjunto invertido.|  
|[rend](../Topic/set::rend.md)|Devuelve un iterador que direcciona la ubicación que sigue al último elemento en un conjunto invertido.|  
|[size](../Topic/set::size.md)|Devuelve el número de elementos del conjunto.|  
|[swap](../Topic/set::swap.md)|Intercambia los elementos de dos conjuntos.|  
|[upper\_bound](../Topic/set::upper_bound.md)|Devuelve un iterador al primer elemento de conjunto con un valor de clave que es mayor que una clave especificada.|  
|[value\_comp](../Topic/set::value_comp.md)|Recupera una copia del objeto de comparación utilizado para ordenar valores de elemento de un conjunto.|  
  
### Operadores  
  
|||  
|-|-|  
|[operador \=](../Topic/set::operator=.md)|Reemplaza los elementos de un conjunto con una copia de otro conjunto.|  
  
## Requisitos  
 **Encabezado:** \<set\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<set\>](../standard-library/set.md)   
 [Contenedores](../cpp/containers-modern-cpp.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)