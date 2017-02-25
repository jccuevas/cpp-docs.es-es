---
title: "multiset (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::multiset"
  - "set/std::multiset"
  - "std.multiset"
  - "multiset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "multiset (clase)"
ms.assetid: 630e8c10-0ce9-4ad9-8d79-9e91a600713f
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# multiset (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase multiset de la Biblioteca de plantillas estándar se emplea para el almacenamiento y la recuperación de datos de una colección en la que los valores de los elementos contenidos no tienen por qué ser únicos y en la que actúan como valores de clave según los cuales los datos se ordenan automáticamente.  El valor de clave de un elemento de un multiset no se puede cambiar directamente.  En su lugar, se deben eliminar los valores anteriores e insertar elementos con valores nuevos.  
  
## Sintaxis  
  
```  
  
        template <  
   class Key,   
   class Compare=less<Key>,   
   class Allocator=allocator<Key>   
>  
class multiset  
```  
  
#### Parámetros  
 *Key*  
 Tipo de datos de elemento que se va a almacenar en la clase multiset.  
  
 *Comparar*  
 Tipo que proporciona un objeto de función que puede comparar dos valores de elementos como claves de ordenación para determinar su orden relativo en la clase multiset.  El predicado binario **less**\<Key\> es el valor predeterminado.  
  
 En C\+\+14 puede habilitar la búsqueda heterogénea especificando el predicado `std::less<>` o `std::greater<>`, que no tienen ningún parámetro de tipo.  Para obtener más información, vea el tema sobre [búsqueda heterogénea en contenedores asociativos](../standard-library/stl-containers.md#sequence_containers).  
  
 `Allocator`  
 Tipo que representa el objeto de asignador almacenado que encapsula los detalles acerca de la asignación y desasignación de memoria de la clase multiset.  El valor predeterminado es **allocator***\<Key\>.*  
  
## Comentarios  
 La clase multiset de STL es:  
  
-   Un contenedor asociativo de tamaño variable que admite la recuperación eficaz de valores de elemento según un valor de clave asociado.  
  
-   Reversible, porque proporciona iteradores bidireccionales para tener acceso a sus elementos.  
  
-   Ordenada, porque sus elementos se ordenan según los valores de clave dentro del contenedor de acuerdo con una función de comparación especificada.  
  
-   Múltiple en el sentido de que sus elementos no necesitan tener claves únicas, de modo que un valor de clave puede tener asociados varios valores de elemento.  
  
-   Un contenedor asociativo simple porque sus valores de elemento son sus valores de clave.  
  
-   Una clase de plantilla, porque la funcionalidad que proporciona es genérica y por tanto independiente del tipo específico de datos contenido como elementos.  En su lugar, el tipo de datos que se usará se especifica como un parámetro en la plantilla de clase junto con la función de comparación y el asignador.  
  
 El iterador proporcionado por la clase multiset es un iterador bidireccional, pero las funciones miembro de clase [insert](../Topic/multiset::insert.md) y [multiset](../Topic/multiset::multiset.md) tienen versiones que toman como parámetros de plantilla un iterador de entrada más débil, cuyos requisitos de funcionalidad son más mínimos que los garantizados por la clase de iteradores bidireccionales.  Los distintos conceptos de iterador forman una familia relacionada por los refinamientos de su funcionalidad.  Cada concepto de iterador tiene su propio conjunto de requisitos y los algoritmos que funcionan con ellos deben limitar sus suposiciones a los requisitos proporcionados por ese tipo de iterador.  Se puede suponer que se puede desreferenciar un iterador de entrada para hacer referencia a un objeto y que se puede incrementar hasta el iterador siguiente de la secuencia.  Se trata de un conjunto mínimo de funcionalidad, pero es suficiente para poder comunicarse sobre un intervalo de iteradores \[`First`, `Last`\) en el contexto de las funciones miembro de clase.  
  
 En general, la elección del tipo de contenedor se debe tomar según el tipo de búsqueda y de inserción que necesite la aplicación.  Los contenedores asociativos están optimizados para las operaciones de búsqueda, inserción y eliminación.  Las funciones miembro que admiten estas operaciones explícitamente las realizan de forma eficiente en un tiempo que es proporcional en promedio al logaritmo del número de elementos del contenedor.  La inserción de elementos no invalida ningún iterador y al quitar elementos solo se invalidan los iteradores que habían apuntado específicamente a los elementos quitados.  
  
 La clase multiset debe ser el contenedor asociativo preferido cuando la aplicación satisfaga las condiciones que asocian los valores a sus claves.  Los elementos de una clase multiset pueden ser varios y actuar como sus propias claves de ordenación, por lo que las claves no son únicas.  Un modelo para este tipo de estructura es una lista ordenada, por ejemplo, de palabras en las que las palabras pueden aparecer más de una vez.  Si no se permitieran varias repeticiones de las palabras, la estructura de contenedor adecuada sería un set.  Si se asociaron definiciones únicas como valores a la lista de palabras clave únicas, la estructura adecuada para contener estos datos sería una clase map.  Si por el contrario las definiciones no son únicas, un multimap sería el contenedor preferido.  
  
 La clase multiset ordena la secuencia que controla llamando a un objeto de función almacenado de tipo `Compare`.  Este objeto almacenado es una función de comparación a la que se puede tener acceso llamando a la función miembro [key\_comp](../Topic/multiset::key_comp.md).  En general, se debe poder comparar si los elementos son menores que otros para poder establecer este orden; de este modo, dados dos elementos cualesquiera, se puede determinar que son equivalentes \(en el sentido de que ninguno es menor que el otro\) o que uno es menor que el otro.  Esto produce una ordenación entre los elementos no equivalentes.  En un sentido más técnico, la función de comparación es un predicado binario que induce una ordenación débil estricta en el sentido matemático estándar.  Un predicado binario *f*\(*x*,*y*\) es un objeto de función que tiene dos objetos de argumento *x* e *y*, y un valor devuelto de **true** o **false**.  Una ordenación impuesta en un conjunto es una ordenación débil estricta si el predicado binario es irreflexivo, antisimétrico y transitivo, y si la equivalencia es transitiva, donde dos objetos x e y se definen como equivalentes cuando tanto *f*\(*x,y*\) como *f*\(*y,x*\) son false.  Si la condición más fuerte de igualdad entre las claves reemplaza la de equivalencia, la ordenación se convierte en total \(en el sentido de que todos los elementos se ordenan entre sí\) y las claves coincidentes serán indiscernibles unas de otras.  
  
 En C\+\+14 puede habilitar la búsqueda heterogénea especificando el predicado `std::less<>` o `std::greater<>`, que no tienen ningún parámetro de tipo.  Para obtener más información, vea el tema sobre [búsqueda heterogénea en contenedores asociativos](../standard-library/stl-containers.md#sequence_containers).  
  
### Constructores  
  
|||  
|-|-|  
|[multiset](../Topic/multiset::multiset.md)|Construye un `multiset` que está vacío o que es una copia de todo o de parte de un `multiset` especificado.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[allocator\_type](../Topic/multiset::allocator_type.md)|Definición de tipos para la clase `allocator` del objeto `multiset`.|  
|[const\_iterator](../Topic/multiset::const_iterator.md)|Definición de tipos para un iterador bidireccional que puede leer un elemento `const` del `multiset`.|  
|[const\_pointer](../Topic/multiset::const_pointer.md)|Definición de tipos para un puntero a un elemento `const` de un `multiset`.|  
|[const\_reference](../Topic/multiset::const_reference.md)|Definición de tipos para una referencia a un elemento `const` almacenado en un `multiset` para leer y realizar operaciones `const`.|  
|[const\_reverse\_iterator](../Topic/multiset::const_reverse_iterator.md)|Definición de tipos para un iterador bidireccional que puede leer cualquier elemento `const` del `multiset`.|  
|[difference\_type](../Topic/multiset::difference_type.md)|Definición de tipos enteros con signo para el número de elementos de un `multiset` en un intervalo entre los elementos a los que apuntan los iteradores.|  
|[iterator](../Topic/multiset::iterator.md)|Definición de tipos para un iterador bidireccional que puede leer o modificar cualquier elemento de un `multiset`.|  
|[key\_compare](../Topic/multiset::key_compare.md)|Definición de tipos para un objeto de función que puede comparar dos claves para determinar el orden relativo de dos elementos del `multiset`.|  
|[key\_type](../Topic/multiset::key_type.md)|Definición de tipos para un objeto de función que puede comparar dos claves de ordenación para determinar el orden relativo de dos elementos del `multiset`.|  
|[puntero](../Topic/multiset::pointer.md)|Definición de tipos para un puntero a un elemento de un `multiset`.|  
|[referencia](../Topic/multiset::reference.md)|Definición de tipos para una referencia a un elemento almacenado en un `multiset`.|  
|[reverse\_iterator](../Topic/multiset::reverse_iterator.md)|Definición de tipos para un iterador bidireccional que puede leer o modificar un elemento de un `multiset` invertido.|  
|[size\_type](../Topic/multiset::size_type.md)|Tipo entero sin signo que puede representar el número de elementos de un `multiset`.|  
|[value\_compare](../Topic/multiset::value_compare.md)|Definición de tipos para un objeto de función que puede comparar dos elementos como claves de ordenación para determinar su orden relativo en el `multiset`.|  
|[value\_type](../Topic/multiset::value_type.md)|Definición de tipos que describe un objeto almacenado como un elemento como un `multiset` en su capacidad como valor.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[begin](../Topic/multiset::begin.md)|Devuelve un iterador que apunta al primer elemento del `multiset`.|  
|[cbegin](../Topic/multiset::cbegin.md)|Devuelve un iterador const que direcciona el primer elemento del `multiset`.|  
|[cend](../Topic/multiset::cend.md)|Devuelve un iterador constante que direcciona la ubicación que sigue al último elemento de `multiset`.|  
|[desactivada](../Topic/multiset::clear.md)|Borra todos los elementos de un `multiset`.|  
|[count](../Topic/multiset::count.md)|Devuelve el número de elementos de un `multiset` cuya clave coincide con la clave especificada como parámetro.|  
|[crbegin](../Topic/multiset::crbegin.md)|Devuelve un iterador const que direcciona el primer elemento de un set invertido.|  
|[crend](../Topic/multiset::crend.md)|Devuelve un iterador const que direcciona la ubicación que sigue al último elemento de un set invertido.|  
|[emplace](../Topic/multiset::emplace.md)|Inserta en un `multiset` un elemento construido en contexto.|  
|[emplace\_hint](../Topic/multiset::emplace_hint.md)|Inserta en un `multiset` un elemento construido en contexto, con una sugerencia de colocación.|  
|[vacío](../Topic/multiset::empty.md)|Comprueba si un `multiset` está vacío.|  
|[end](../Topic/multiset::end.md)|Devuelve un iterador que apunta a la ubicación posterior al último elemento de un `multiset` invertido.|  
|[equal\_range](../Topic/multiset::equal_range.md)|Devuelve un par de iteradores.  El primer iterador del par apunta al primer elemento de un `multiset` cuya clave es mayor que una clave especificada.  El segundo iterador del par apunta al primer elemento del `multiset` cuya clave es igual o mayor que la clave especificada.|  
|[erase](../Topic/multiset::erase.md)|Quita un elemento o un intervalo de elementos de una clase `multiset` de las posiciones especificadas o quita los elementos que coinciden con una clave especificada.|  
|[find](../Topic/multiset::find.md)|Devuelve un iterador que apunta a la primera ubicación de un elemento en un `multiset` que tiene una clave igual que una clave especificada.|  
|[get\_allocator](../Topic/multiset::get_allocator.md)|Devuelve una copia del objeto `allocator` utilizado para construir el `multiset`.|  
|[insertar](../Topic/multiset::insert.md)|Inserta un elemento o un intervalo de elementos en un `multiset`.|  
|[key\_comp](../Topic/multiset::key_comp.md)|Proporciona un objeto de función que puede comparar dos claves de ordenación para determinar el orden relativo de dos elementos en el `multiset`.|  
|[lower\_bound](../Topic/multiset::lower_bound.md)|Devuelve un iterador al primer elemento de un `multiset` cuya clave es igual o mayor que una clave especificada.|  
|[max\_size](../Topic/multiset::max_size.md)|Devuelve la longitud máxima del `multiset`.|  
|[rbegin](../Topic/multiset::rbegin.md)|Devuelve un iterador que apunta al primer elemento de un `multiset` invertido.|  
|[rend](../Topic/multiset::rend.md)|Devuelve un iterador que apunta a la ubicación posterior al último elemento de un `multiset` invertido.|  
|[size](../Topic/multiset::size.md)|Devuelve el número de elementos de un `multiset`.|  
|[swap](../Topic/multiset::swap.md)|Intercambia los elementos de dos `multiset`.|  
|[upper\_bound](../Topic/multiset::upper_bound.md)|Devuelve un iterador al primer elemento de un `multiset` con una clave que es mayor que una clave especificada.|  
|[value\_comp](../Topic/multiset::value_comp.md)|Recupera una copia del objeto de comparación que se emplea para ordenar los valores de elementos de un `multiset`.|  
  
### Operadores  
  
|||  
|-|-|  
|[operador \=](../Topic/multiset::operator=.md)|Reemplaza los elementos de un `multiset` con una copia de otro `multiset`.|  
  
## Requisitos  
 **Encabezado:** \<set\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [miembros de \<conjunto\>](http://msdn.microsoft.com/es-es/0c2d57c0-173f-4204-b579-c5f06aad8b95)   
 [Contenedores](../cpp/containers-modern-cpp.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)