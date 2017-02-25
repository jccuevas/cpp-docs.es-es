---
title: "map (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::map"
  - "map/std::map"
  - "map"
  - "std.map"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "map (clase)"
ms.assetid: 7876f4c9-ebb4-4878-af1e-09364c43af0a
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# map (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se utiliza para el almacenamiento y la recuperación de datos de una colección en la que cada elemento es un par que tiene un valor de datos y una clave de ordenación.  El valor de la clave es único y se utiliza para ordenar los datos automáticamente.  
  
 El valor de un elemento de una asignación se puede cambiar directamente.  El valor de clave es una constante y no se puede cambiar.  En su lugar, se deben eliminar los valores de clave asociados a los antiguos elementos y se deben insertar nuevos valores de clave para los elementos nuevos.  
  
## Sintaxis  
  
```  
template <  
   class Key,   
   class Type,   
   class Traits = less<Key>,   
   class Allocator=allocator<pair <const Key, Type> >   
> class map;  
```  
  
#### Parámetros  
 `Key`  
 Tipo de datos de clave que se almacenará en la asignación.  
  
 `Type`  
 Tipo de datos de elementos que se va a almacenar en la asignación.  
  
 `Traits`  
 Tipo que proporciona un objeto de función que puede comparar dos valores de elementos como claves de ordenación para determinar su orden relativo en la asignación.  Este argumento es opcional y el predicado binario `less<``Key``>` es el valor predeterminado.  
  
 En C\+\+14 puede habilitar la búsqueda heterogénea especificando el predicado std::less\<\> que no tiene ningún parámetro de tipo.  Para más información, vea [Búsqueda heterogénea en los contenedores asociativos](../standard-library/stl-containers.md#sequence_containers)  
  
 `Allocator`  
 Tipo que representa el objeto de asignador almacenado que encapsula los detalles acerca de la asignación y desasignación de memoria de la asignación.  Este argumento es opcional y el valor predeterminado es `allocator<pair` `<const``Key`*,* `Type``> >`.  
  
## Comentarios  
 La clase map de la Biblioteca de plantillas estándar \(STL\) es:  
  
-   Un contenedor de tamaño variable que recupera eficazmente valores de elementos según los valores de clave asociados.  
  
-   Reversible, porque proporciona iteradores bidireccionales para tener acceso a sus elementos.  
  
-   Ordenada, porque sus elementos se ordenan por valores de clave según una función de comparación especificada.  
  
-   Única,  ya que cada uno de sus elementos debe tener una clave única.  
  
-   Un contenedor asociativo de pares, ya que los valores de datos de sus elementos son distintos de sus valores de clave.  
  
-   Una clase de plantilla, porque la funcionalidad que proporciona es genérica e independiente del tipo de elemento o de clave.  Los tipos de datos usados para los elementos y las claves se especifican como parámetros en la plantilla de clase junto con la función de comparación y el asignador.  
  
 El iterador proporcionado por la clase map es un iterador bidireccional, pero las funciones miembro de clase [insert](../Topic/map::insert.md) y [map](../Topic/map::map.md) tienen versiones que toman como parámetros de plantilla un iterador de entrada más débil, cuyos requisitos de funcionalidad son menores que los garantizados por la clase de iteradores bidireccionales.  Los distintos conceptos de iterador están relacionados por los refinamientos de su funcionalidad.  Cada concepto de iterador tiene su propio conjunto de requisitos y los algoritmos que funcionan con él deben estar limitados por esos requisitos.  Un iterador de entrada se puede desreferenciar para hacer referencia a algún objeto e incrementar al iterador siguiente de la secuencia.  
  
 Se recomienda elegir el tipo de contenedor según la clase de búsqueda e inserción que necesite la aplicación.  Los contenedores asociativos están optimizados para las operaciones de búsqueda, inserción y eliminación.  Las funciones miembro que admiten estas operaciones explícitamente las realizan en una tiempo de caso peor que es proporcional al logaritmo del número de elementos del contenedor.  La inserción de elementos no invalida ningún iterador y al quitar elementos solo se invalidan los iteradores que habían apuntado específicamente a los elementos quitados.  
  
 Se recomienda que el mapa sea el contenedor asociativo preferido si la aplicación satisface las condiciones que asocian valores a claves.  Un modelo para este tipo de estructura es una lista ordenada de palabras clave que aparecen de forma única y que tienen asociados valores de cadena que proporcionan definiciones.  Si una palabra tiene más de una definición correcta, de modo que la clave no es única, el contenedor más adecuado sería un multimap.  Si solo se va a almacenar la lista de palabras, el contenedor adecuado sería un conjunto.  Si se permiten varias apariciones de las palabras, lo mejor sería usar un multiset.  
  
 El mapa ordena los elementos que controla llamando a un objeto de función almacenado de tipo [key\_compare](../Topic/map::key_compare.md).  Este objeto almacenado es una función de comparación a la que se tiene acceso llamando al método [key\_comp](../Topic/map::key_comp.md).  En general, se comparan dos elementos especificados para determinar si uno es menor que otro o si son equivalentes.  Cuando se comparan todos los elementos, se crea una secuencia ordenada de elementos no equivalentes.  
  
> [!NOTE]
>  La función de comparación es un predicado binario que induce una ordenación parcial estricta en el sentido matemático estándar.  Un predicado binario f\(x,y\) es un objeto de función que tiene dos objetos de argumento x e y, y un valor devuelto de `true` o `false`.  Una ordenación impuesta en un conjunto es una ordenación débil estricta si el predicado binario es irreflexivo, antisimétrico y transitivo, y si la equivalencia es transitiva, donde dos objetos x e y se definen como equivalentes cuandof\(x,y\) ``  y f\(y,x\) son `false`.  Si la condición más fuerte de igualdad entre las claves reemplaza la de equivalencia, la ordenación se convierte en total \(en el sentido de que todos los elementos se ordenan entre sí\) y las claves coincidentes serán indiscernibles unas de otras.  
>   
>  En C\+\+14 puede habilitar la búsqueda heterogénea especificando el predicado `std::less<>` o `std::greater<>`, que no tienen ningún parámetro de tipo.  Para más información, vea [Búsqueda heterogénea en los contenedores asociativos](../standard-library/stl-containers.md#sequence_containers)  
  
## Miembros  
  
### Constructores  
  
|||  
|-|-|  
|[map](../Topic/map::map.md)|Crea una lista de un tamaño concreto o con elementos de un valor concreto o con un `allocator` específico o como copia de algún otro mapa.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[allocator\_type](../Topic/map::allocator_type.md)|Definición de tipos para la clase `allocator` del objeto map.|  
|[const\_iterator](../Topic/map::const_iterator.md)|Definición de tipos para un iterador bidireccional que puede leer un elemento `const` del mapa.|  
|[const\_pointer](../Topic/map::const_pointer.md)|Definición de tipos para un puntero a un elemento `const` de un mapa.|  
|[const\_reference](../Topic/map::const_reference.md)|Definición de tipos para una referencia a un elemento `const` almacenado en un mapa para leer y realizar operaciones `const`.|  
|[const\_reverse\_iterator](../Topic/map::const_reverse_iterator.md)|Tipo que proporciona un iterador bidireccional que puede leer cualquier elemento `const` del mapa.|  
|[difference\_type](../Topic/map::difference_type.md)|Definición de tipos enteros con signo para el número de elementos de un mapa en un intervalo entre los elementos a los que apuntan los iteradores.|  
|[iterator](../Topic/map::iterator.md)|Definición de tipos para un iterador bidireccional que puede leer o modificar cualquier elemento de un mapa.|  
|[key\_compare](../Topic/map::key_compare.md)|Definición de tipos para un objeto de función que puede comparar dos claves de ordenación para determinar el orden relativo de dos elementos del mapa.|  
|[key\_type](../Topic/map::key_type.md)|Definición de tipos para la clave de ordenación almacenada en cada elemento del mapa.|  
|[mapped\_type](../Topic/map::mapped_type.md)|Definición de tipos para los datos almacenados en cada elemento de un mapa.|  
|[puntero](../Topic/map::pointer.md)|Definición de tipos para un puntero a un elemento `const` de un mapa.|  
|[referencia](../Topic/map::reference.md)|Definición de tipos para una referencia a un elemento almacenado en un mapa.|  
|[reverse\_iterator](../Topic/map::reverse_iterator.md)|Definición de tipos para un iterador bidireccional que puede leer o modificar un elemento de un mapa invertido.|  
|[size\_type](../Topic/map::size_type.md)|Definición de tipos enteros sin signo para el número de elementos de un mapa|  
|[value\_type](../Topic/map::value_type.md)|Definición de tipos para el tipo de objeto almacenado como elemento en un mapa.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[en](../Topic/map::at.md)|Busca un elemento con un valor de clave especificado.|  
|[begin](../Topic/map::begin.md)|Devuelve un iterador que apunta al primer elemento del mapa.|  
|[cbegin](../Topic/map::cbegin.md)|Devuelve un iterador constante que apunta al primer elemento del mapa.|  
|[cend](../Topic/map::cend.md)|Devuelve un iterador constante más allá del final.|  
|[desactivada](../Topic/map::clear.md)|Borra todos los elementos de un mapa.|  
|[count](../Topic/map::count.md)|Devuelve el número de elementos de un mapa cuya clave coincide con la clave especificada en un parámetro.|  
|[crbegin](../Topic/map::crbegin.md)|Devuelve un iterador constante que apunta al primer elemento de un mapa invertido.|  
|[crend](../Topic/map::crend.md)|Devuelve un iterador constante que apunta a la ubicación posterior al último elemento de un mapa invertido.|  
|[emplace](../Topic/map::emplace.md)|Inserta en el mapa un elemento construido en contexto.|  
|[emplace\_hint](../Topic/map::emplace_hint.md)|Inserta en el mapa un elemento construido en contexto, con una sugerencia de colocación.|  
|[vacío](../Topic/map::empty.md)|Devuelve `true` si un mapa está vacío.|  
|[end](../Topic/map::end.md)|Devuelve el iterador más allá del final.|  
|[equal\_range](../Topic/map::equal_range.md)|Devuelve un par de iteradores.  El primer iterador del par apunta al primer elemento de un `map` cuya clave es mayor que una clave especificada.  El segundo iterador del par apunta al primer elemento del `map` cuya clave es igual o mayor que la clave especificada.|  
|[erase](../Topic/map::erase.md)|Quita un elemento o un intervalo de elementos de un mapa de las posiciones especificadas.|  
|[find](../Topic/map::find.md)|Devuelve un iterador que apunta a la ubicación de un elemento en un mapa que tiene una clave igual que una clave especificada.|  
|[get\_allocator](../Topic/map::get_allocator.md)|Devuelve una copia del objeto `allocator` utilizado para construir el mapa.|  
|[insertar](../Topic/map::insert.md)|Inserta un elemento o un intervalo de elementos en el mapa en una posición especificada.|  
|[key\_comp](../Topic/map::key_comp.md)|Devuelve una copia del objeto de comparación utilizado para ordenar las claves en un mapa.|  
|[lower\_bound](../Topic/map::lower_bound.md)|Devuelve un iterador al primer elemento de un mapa cuyo valor de clave es igual o mayor que el de una clave especificada.|  
|[max\_size](../Topic/map::max_size.md)|Devuelve la longitud máxima del mapa.|  
|[rbegin](../Topic/map::rbegin.md)|Devuelve un iterador que apunta al primer elemento de un mapa invertido.|  
|[rend](../Topic/map::rend.md)|Devuelve un iterador que apunta a la ubicación posterior al último elemento de un mapa invertido.|  
|[size](../Topic/map::size.md)|Devuelve el número de elementos del mapa.|  
|[swap](../Topic/map::swap.md)|Intercambia los elementos de dos mapas.|  
|[upper\_bound](../Topic/map::upper_bound.md)|Devuelve un iterador al primer elemento de un mapa cuyo valor de clave es mayor que el de una clave especificada.|  
|[value\_comp](../Topic/map::value_comp.md)|Recupera una copia del objeto de comparación que se utiliza para ordenar valores de elementos de un mapa.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator&#91;&#93;](../Topic/map::operator[].md)|Inserta un elemento en un mapa con un valor de clave especificado.|  
|[operador \=](../Topic/map::operator=.md)|Reemplaza los elementos de un mapa con una copia de otro mapa.|  
  
## Requisitos  
 **Encabezado:** \<map\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [miembros de \<Asignar\>](http://msdn.microsoft.com/es-es/7e8f0bc2-6034-40f6-9d14-76d4cef86308)   
 [Contenedores](../cpp/containers-modern-cpp.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)