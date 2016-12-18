---
title: "list (Clase) | Microsoft Docs"
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
  - "std.list"
  - "list"
  - "std::list"
  - "list/std::list"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "list (clase)"
ms.assetid: d3707f4a-10fd-444f-b856-f9ca2077c1cd
caps.latest.revision: 20
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# list (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de lista STL es una clase de plantilla de contenedores de secuencias que mantienen sus elementos en disposición lineal y permiten realizar inserciones y eliminaciones de manera eficiente en cualquier ubicación de la secuencia.  La secuencia se almacena como una lista de elementos vinculada de forma bidireccional, cada uno de los cuales contiene un miembro de algún tipo *Type*.  
  
## Sintaxis  
  
```cpp  
  
template <    class Type,     class Allocator=allocator<Type>  > class list  
```  
  
#### Parámetros  
 *Tipo*  
 El tipo de datos de elementos que se almacenará en la lista.  
  
 `Allocator`  
 El tipo que representa el objeto asignador almacenado que encapsula los detalles sobre la asignación y la desasignación de memoria de la lista.  Este argumento es opcional y el valor predeterminado es **allocator**\<*Type*\>*.*  
  
## Comentarios  
 En general, la elección del tipo de contenedor se debe tomar según el tipo de búsqueda y de inserción que necesite la aplicación.  Los vectores deben ser el contenedor preferido para administrar una secuencia cuando escasee el acceso aleatorio a algún elemento y solo sea necesario realizar inserciones o eliminaciones de elementos al final de una secuencia.  El rendimiento del contenedor deque de la clase es superior cuando el acceso aleatorio es necesario y escasean las inserciones y eliminaciones al principio y al final de una secuencia.  
  
 Las funciones miembro de lista [merge](../Topic/list::merge.md), [reverse](../Topic/list::reverse.md), [unique](../Topic/list::unique.md), [remove](../Topic/list::remove.md) y [remove\_if](../Topic/list::remove_if.md) se optimizaron para funcionar en objetos de lista y ofrecer una alternativa de alto rendimiento a sus equivalentes genéricos.  
  
 La reasignación de lista se realiza cuando una función miembro debe insertar o borrar elementos de la lista.  En todos esos casos, solo los iteradores o las referencias que apuntan a partes borradas de la secuencia controlada dejan de ser válidas.  
  
 Incluya el encabezado estándar STL \<list\> para definir la lista de clases de plantilla [container](../standard-library/stl-containers.md) y varias plantillas auxiliares.  
  
### Constructores  
  
|||  
|-|-|  
|[lista](../Topic/list::list.md)|Construye una lista de un tamaño específico, con elementos de un valor específico, con un `allocator` específico o como copia de alguna otra lista.|  
  
### Typedefs  
  
|||  
|-|-|  
|[allocator\_type](../Topic/list::allocator_type.md)|Tipo que representa la clase `allocator` para un objeto de lista.|  
|[const\_iterator](../Topic/list::const_iterator.md)|Tipo que proporciona un iterador bidireccional que puede leer un elemento `const` de una lista.|  
|[const\_pointer](../Topic/list::const_pointer.md)|Tipo que proporciona un puntero a un elemento `const` en una lista.|  
|[const\_reference](../Topic/list::const_reference.md)|Tipo que proporciona una referencia a un elemento `const` almacenado en una lista para leer y realizar operaciones `const`.|  
|[const\_reverse\_iterator](../Topic/list::const_reverse_iterator.md)|Tipo que proporciona un iterador bidireccional que puede leer cualquier elemento `const` de una lista.|  
|[difference\_type](../Topic/list::difference_type.md)|Tipo que proporciona la diferencia entre dos iteradores que hacen referencia a elementos de la misma lista.|  
|[iterator](../Topic/list::iterator.md)|Tipo que proporciona un iterador bidireccional que puede leer o modificar cualquier elemento de una lista.|  
|[puntero](../Topic/list::pointer.md)|Tipo que proporciona un puntero a un elemento de una lista.|  
|[reference](../Topic/list::reference.md)|Tipo que proporciona una referencia a un elemento `const` almacenado en una lista para leer y realizar operaciones `const`.|  
|[reverse\_iterator](../Topic/list::reverse_iterator.md)|Tipo que proporciona un iterador bidireccional que puede leer o modificar un elemento de una lista invertida.|  
|[size\_type](../Topic/list::size_type.md)|Tipo que cuenta el número de elementos de una lista.|  
|[value\_type](../Topic/list::value_type.md)|Tipo que representa el tipo de datos almacenados en una lista.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[assign](../Topic/list::assign.md)|Borra elementos de una lista y copia un nuevo conjunto de elementos a la lista de destino.|  
|[back](../Topic/list::back.md)|Devuelve una referencia al último elemento de una lista.|  
|[begin](../Topic/list::begin.md)|Devuelve un iterador que dirige al primer elemento de una lista.|  
|[list::cbegin](../Topic/list::cbegin.md)|Devuelve un iterador constante que dirige al primer elemento de una lista.|  
|[list::cend](../Topic/list::cend.md)|Devuelve un iterador constante que dirige a la ubicación siguiente al último elemento de una lista.|  
|[list::clear](../Topic/list::clear.md)|Borra todos los elementos de una lista.|  
|[list::crbegin](../Topic/list::crbegin.md)|Devuelve un iterador constante que dirige al primer elemento de una lista invertida.|  
|[list::crend](../Topic/list::crend.md)|Devuelve un iterador constante que dirige a la ubicación siguiente al último elemento de una lista invertida.|  
|[list::emplace](../Topic/list::emplace.md)|Inserta en una posición especificada de una lista un elemento construido en contexto.|  
|[list::emplace\_back](../Topic/list::emplace_back.md)|Agrega un elemento construido en contexto al final de una lista.|  
|[list::emplace\_front](../Topic/list::emplace_front.md)|Agrega un elemento construido en contexto al principio de una lista.|  
|[empty](../Topic/list::empty.md)|Comprueba si una lista está vacía.|  
|[end](../Topic/list::end.md)|Devuelve un iterador que dirige a la ubicación que sigue al último elemento de una lista.|  
|[erase](../Topic/list::erase.md)|Quita un elemento o un intervalo de elementos de una lista de las posiciones especificadas.|  
|[front](../Topic/list::front.md)|Devuelve una referencia al primer elemento de una lista.|  
|[get\_allocator](../Topic/list::get_allocator.md)|Devuelve una copia del objeto `allocator` utilizado para construir una lista.|  
|[insert](../Topic/list::insert.md)|Inserta un elemento, varios elementos o un intervalo de elementos en una lista en una posición especificada.|  
|[max\_size](../Topic/list::max_size.md)|Devuelve la longitud máxima de una lista.|  
|[merge](../Topic/list::merge.md)|Quita los elementos de la lista de argumentos, los inserta en la lista de objetivo y ordena el nuevo conjunto combinado de elementos en orden ascendente o en otro orden especificado.|  
|[pop\_back](../Topic/list::pop_back.md)|Elimina el elemento situado al final de una lista.|  
|[pop\_front](../Topic/list::pop_front.md)|Elimina el elemento situado al principio de una lista.|  
|[push\_back](../Topic/list::push_back.md)|Agrega un elemento al final de una lista.|  
|[push\_front](../Topic/list::push_front.md)|Agrega un elemento al principio de una lista.|  
|[rbegin](../Topic/list::rbegin.md)|Devuelve un iterador que dirige al primer elemento de una lista invertida.|  
|[remove](../Topic/list::remove.md)|Borra los elementos de una lista que coinciden con un valor especificado.|  
|[remove\_if](../Topic/list::remove_if.md)|Borra elementos de la lista para la que se cumple un predicado especificado.|  
|[rend](../Topic/list::rend.md)|Devuelve un iterador que dirige a la ubicación siguiente al último elemento de una lista invertida.|  
|[resize](../Topic/list::resize.md)|Especifica un nuevo tamaño de una lista.|  
|[reverse](../Topic/list::reverse.md)|Invierte el orden en que aparecen los elementos en una lista.|  
|[size](../Topic/list::size.md)|Devuelve el número de elementos de una lista.|  
|[sort](../Topic/list::sort.md)|Organiza los elementos de una lista en orden ascendente o con respecto a otra relación de ordenación.|  
|[splice](../Topic/list::splice.md)|Quita los elementos de la lista de argumentos y los inserta en la lista de destino.|  
|[swap](../Topic/list::swap.md)|Intercambia los elementos de dos listas.|  
|[unique](../Topic/list::unique.md)|Quita de la lista los elementos duplicados adyacentes o los elementos adyacentes que cumplan algún otro predicado binario.|  
  
### Operadores  
  
|||  
|-|-|  
|[list::operator\=](../Topic/list::operator=.md)|Reemplaza los elementos de la lista por una copia de otra lista.|  
  
## Requisitos  
 **Encabezado:** \<list\>  
  
## Vea también  
 [\<list\>](../standard-library/list.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)