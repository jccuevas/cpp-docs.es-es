---
title: "forward_list (Clase) | Microsoft Docs"
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
  - "std::forward_list"
  - "forward_list"
  - "forward_list/std::forward_list"
  - "std.forward_list"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "forward_list (clase)"
ms.assetid: 89a3b805-ab60-4858-b772-5855130c11b1
caps.latest.revision: 25
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# forward_list (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un objeto que controla una secuencia de elementos de longitud variable.  La secuencia se almacena como una lista de nodos vinculada individualmente, cada uno de los cuales contiene un miembro de tipo `Type`.  
  
## Sintaxis  
  
```  
template<  
    class Type,   
    class Allocator = allocator<Type>   
>  
class forward_list   
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Type`|Tipo de datos de elemento que se almacenará en forward\_list.|  
|`Allocator`|Objeto de asignador almacenado que encapsula detalles sobre la asignación y desasignación de memoria de forward\_list.  Este parámetro es opcional.  El valor predeterminado es allocator\<`Type`\>.|  
  
## Comentarios  
 Un objeto `forward_list` asigna y libera el almacenamiento para la secuencia que controla mediante un objeto almacenado de clase `Allocator` que se basa en la [allocator \(Clase\)](../standard-library/allocator-class.md) \(conocida normalmente como `std::allocator)`.  Para obtener más información, consulte [Asignadores](../standard-library/allocators.md).  Un objeto de asignador debe tener la misma interfaz externa que un objeto de clase de plantilla `allocator`.  
  
> [!NOTE]
>  El objeto de asignador almacenado no se copia cuando se asigna el objeto contenedor.  
  
 Los iteradores, punteros y referencias pueden llegar a no ser válidos cuando los elementos de su secuencia controlada se borran mediante `forward_list`.  Las inserciones y uniones realizados en la secuencia controlada mediante `forward_list` no invalidan los iteradores.  
  
 Las adiciones a la secuencia controlada pueden realizarse mediante llamadas a [forward\_list::insert\_after](../Topic/forward_list::insert_after.md), que es la única función miembro que llama al constructor `Type(const _Type&)`.  `forward_list` también puede llamar a constructores de movimiento.  Si una expresión de ese tipo produce una excepción, el objeto contenedor no inserta ningún elemento nuevo y vuelve a producir la excepción.  Así, un objeto de clase de plantilla `forward_list` se queda en un estado conocido cuando se producen esas excepciones.  
  
### Constructores  
  
|||  
|-|-|  
|[forward\_list](../Topic/forward_list::forward_list.md)|Construye un objeto de tipo `forward_list`.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[allocator\_type](../Topic/forward_list::allocator_type.md)|Tipo que representa la clase de asignador de un objeto de lista de reenvíos.|  
|[const\_iterator](../Topic/forward_list::const_iterator.md)|Tipo que proporciona un iterador constante para la lista de reenvíos.|  
|[const\_pointer](../Topic/forward_list::const_pointer.md)|Tipo que proporciona un puntero a un elemento `const` de una lista de reenvíos.|  
|[const\_reference](../Topic/forward_list::const_reference.md)|Tipo que proporciona una referencia constante a un elemento de la lista de reenvíos.|  
|[difference\_type](../Topic/forward_list::difference_type.md)|Tipo entero con signo que se puede usar para representar el número de elementos de una lista de reenvíos en un intervalo entre elementos a los que apuntan los iteradores.|  
|[iterator](../Topic/forward_list::iterator.md)|Tipo que proporciona un iterador para la lista de reenvíos.|  
|[puntero](../Topic/forward_list::pointer.md)|Tipo que proporciona un puntero a un elemento de la lista de reenvíos.|  
|[referencia](../Topic/forward_list::reference.md)|Tipo que proporciona una referencia a un elemento de la lista de reenvíos.|  
|[size\_type](../Topic/forward_list::size_type.md)|Tipo que representa la distancia sin signo entre dos elementos.|  
|[value\_type](../Topic/forward_list::value_type.md)|Tipo que representa el tipo de elemento almacenado en una lista de reenvíos.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[assign](../Topic/forward_list::assign.md)|Borra elementos de una lista de reenvíos y copia un nuevo conjunto de elementos a una lista de reenvíos de destino.|  
|[before\_begin](../Topic/forward_list::before_begin.md)|Devuelve un iterador que direcciona la posición anterior al primer elemento de una lista de reenvíos.|  
|[begin](../Topic/forward_list::begin.md)|Devuelve un iterador que direcciona el primer elemento de una lista de reenvíos.|  
|[cbefore\_begin](../Topic/forward_list::cbefore_begin.md)|Devuelve un iterador const que direcciona la posición anterior al primer elemento de una lista de reenvíos.|  
|[cbegin](../Topic/forward_list::cbegin.md)|Devuelve un iterador const que direcciona el primer elemento de una lista de reenvíos.|  
|[cend](../Topic/forward_list::cend.md)|Devuelve un iterador constante que direcciona la ubicación que sigue al último elemento de una lista de reenvíos.|  
|[desactivada](../Topic/forward_list::clear.md)|Borra todos los elementos de una lista de reenvíos.|  
|[emplace\_after](../Topic/forward_list::emplace_after.md)|Construye con movimiento un nuevo elemento después de una posición especificada.|  
|[emplace\_front](../Topic/forward_list::emplace_front.md)|Agrega un elemento construido al principio de la lista.|  
|[vacío](../Topic/forward_list::empty.md)|Comprueba si una lista de reenvíos está vacía.|  
|[end](../Topic/forward_list::end.md)|Devuelve un iterador que direcciona la ubicación que sigue al último elemento de una lista de reenvíos.|  
|[erase\_after](../Topic/forward_list::erase_after.md)|Quita de la lista de reenvíos los elementos situados después de una posición especificada.|  
|[front](../Topic/forward_list::front.md)|Devuelve una referencia al primer elemento de una lista de reenvíos.|  
|[get\_allocator](../Topic/forward_list::get_allocator.md)|Devuelve una copia del objeto de asignador utilizado para construir una lista de reenvíos.|  
|[insert\_after](../Topic/forward_list::insert_after.md)|Agrega elementos a la lista de reenvíos después de una posición especificada.|  
|[max\_size](../Topic/forward_list::max_size.md)|Devuelve la longitud máxima de una lista de reenvíos.|  
|[combinar](../Topic/forward_list::merge.md)|Quita los elementos de la lista de argumentos, los inserta en la lista de reenvíos de destino y ordena el nuevo conjunto combinado de elementos en orden ascendente o en otro orden especificado.|  
|[pop\_front](../Topic/forward_list::pop_front.md)|Elimina el elemento situado al principio de una lista de reenvíos.|  
|[push\_front](../Topic/forward_list::push_front.md)|Agrega un elemento al principio de una lista de reenvíos.|  
|[quitar](../Topic/forward_list::remove.md)|Borra elementos de una lista de reenvíos que coincide con un valor especificado.|  
|[remove\_if](../Topic/forward_list::remove_if.md)|Borra elementos de una lista de reenvíos para la que se cumple el predicado especificado.|  
|[cambiar el tamaño](../Topic/forward_list::resize.md)|Especifica un nuevo tamaño de una lista de reenvíos.|  
|[reverse](../Topic/forward_list::reverse.md)|Invierte el orden en que aparecen los elementos en una lista de reenvíos.|  
|[sort](../Topic/forward_list::sort.md)|Organiza los elementos en orden ascendente o con un orden especificado por un predicado.|  
|[splice\_after](../Topic/forward_list::splice_after.md)|Vuelve a unir vínculos entre nodos.|  
|[swap](../Topic/forward_list::swap.md)|Intercambia los elementos de dos listas de reenvío.|  
|[unique](../Topic/forward_list::unique.md)|Quita los elementos adyacentes que superan una prueba especificada.|  
  
### Operadores  
  
|||  
|-|-|  
|[operador \=](../Topic/forward_list::operator=.md)|Reemplaza los elementos de la lista de reenvíos con una copia de otra lista de reenvíos.|  
  
## Requisitos  
 **Encabezado:** \<forward\_list\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<forward\_list\>](../standard-library/forward-list.md)