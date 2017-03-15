---
title: "list (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::list"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/list> (encabezado) [STL/CLR]"
  - "<list> (encabezado) [STL/CLR]"
  - "list (clase) [STL/CLR]"
ms.assetid: a70c45c8-a257-4f6b-8434-b27ff6685bac
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# list (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un objeto que controla una secuencia de la variar\- longitud de elementos con acceso bidireccional.  Utiliza el contenedor `list` para administrar una secuencia de elementos como una lista vinculada bidireccional de nodos, cada un elemento que almacena.  
  
 En la descripción siguiente, `GValue` es igual que `Value` a menos que este último es un tipo de referencia, en este caso es `Value^`.  
  
## Sintaxis  
  
```  
template<typename Value>  
    ref class list  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        Microsoft::VisualC::StlClr::IList<GValue>  
    { ..... };  
```  
  
#### Parámetros  
 Valor  
 Tipo de un elemento de la secuencia controlada.  
  
## Miembros  
  
|Definición de tipo|Descripción|  
|------------------------|-----------------|  
|[list::const\_iterator](../dotnet/list-const-iterator-stl-clr.md)|El tipo de un iterador constante para la secuencia controlada.|  
|[list::const\_reference](../dotnet/list-const-reference-stl-clr.md)|El tipo de una referencia constante a un elemento.|  
|[list::const\_reverse\_iterator](../dotnet/list-const-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso constante para la secuencia controlada.|  
|[list::difference\_type](../dotnet/list-difference-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[list::generic\_container](../dotnet/list-generic-container-stl-clr.md)|El tipo de interfaz genérica para el contenedor.|  
|[list::generic\_iterator](../dotnet/list-generic-iterator-stl-clr.md)|El tipo de un iterador para la interfaz genérica para el contenedor.|  
|[list::generic\_reverse\_iterator](../dotnet/list-generic-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso para la interfaz genérica para el contenedor.|  
|[list::generic\_value](../dotnet/list-generic-value-stl-clr.md)|El tipo de un elemento de la interfaz genérica para el contenedor.|  
|[list::iterator](../dotnet/list-iterator-stl-clr.md)|El tipo de un iterador para la secuencia controlada.|  
|[list::reference](../dotnet/list-reference-stl-clr.md)|El tipo de una referencia a un elemento.|  
|[list::reverse\_iterator](../dotnet/list-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso para la secuencia controlada.|  
|[list::size\_type](../dotnet/list-size-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[list::value\_type](../dotnet/list-value-type-stl-clr.md)|El tipo de un elemento.|  
  
|Función de miembro|Descripción|  
|------------------------|-----------------|  
|[list::assign](../dotnet/list-assign-stl-clr.md)|Reemplaza todos los elementos.|  
|[list::back](../dotnet/list-back-stl-clr.md)|Tiene acceso al último elemento.|  
|[list::begin](../dotnet/list-begin-stl-clr.md)|Designa el principio de la secuencia controlada.|  
|[list::clear](../dotnet/list-clear-stl-clr.md)|Quita todos los elementos.|  
|[list::empty](../dotnet/list-empty-stl-clr.md)|Comprueba si no hay elementos presentes.|  
|[list::end](../dotnet/list-end-stl-clr.md)|Designa el final de la secuencia controlada.|  
|[list::erase](../dotnet/list-erase-stl-clr.md)|Quita los elementos en las posiciones especificadas.|  
|[list::front](../dotnet/list-front-stl-clr.md)|Tiene acceso al primer elemento.|  
|[list::insert](../dotnet/list-insert-stl-clr.md)|Agrega elementos en una posición especificada.|  
|[list::list](../dotnet/list-list-stl-clr.md)|Construye un objeto contenedor.|  
|[list::merge](../dotnet/list-merge-stl-clr.md)|Combina dos secuencias controladas ordenadas.|  
|[list::pop\_back](../dotnet/list-pop-back-stl-clr.md)|Quita el último elemento.|  
|[list::pop\_front](../dotnet/list-pop-front-stl-clr.md)|Quita el primer elemento.|  
|[list::push\_back](../dotnet/list-push-back-stl-clr.md)|Agrega un nuevo elemento pasado.|  
|[list::push\_front](../dotnet/list-push-front-stl-clr.md)|Agrega un nuevo primero.|  
|[list::rbegin](../dotnet/list-rbegin-stl-clr.md)|Designa el principio de la secuencia controlada inversa.|  
|[list::remove](../dotnet/list-remove-stl-clr.md)|Quita un elemento con un valor especificado.|  
|[list::remove\_if](../dotnet/list-remove-if-stl-clr.md)|Quita los elementos que pasan una prueba especificada.|  
|[list::rend](../dotnet/list-rend-stl-clr.md)|Designa el final de la secuencia controlada inversa.|  
|[list::resize](../dotnet/list-resize-stl-clr.md)|Cambia el número de elementos.|  
|[list::reverse](../dotnet/list-reverse-stl-clr.md)|Invierte la secuencia controlada.|  
|[list::size](../dotnet/list-size-stl-clr.md)|Cuenta el número de elementos.|  
|[list::sort](../dotnet/list-sort-stl-clr.md)|Ordena la secuencia controlada.|  
|[list::splice](../dotnet/list-splice-stl-clr.md)|Vuelve a unir vínculos entre nodos.|  
|[list::swap](../dotnet/list-swap-stl-clr.md)|Intercambia el contenido de dos contenedores.|  
|[list::to\_array](../dotnet/list-to-array-stl-clr.md)|Copia la secuencia controlada a una nueva matriz.|  
|[list::unique](../dotnet/list-unique-stl-clr.md)|Quita los elementos adyacentes que superan una prueba especificada.|  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|[list::back\_item](../dotnet/list-back-item-stl-clr.md)|Tiene acceso al último elemento.|  
|[list::front\_item](../dotnet/list-front-item-stl-clr.md)|Tiene acceso al primer elemento.|  
  
|operador ??|Descripción|  
|-----------------|-----------------|  
|[list::operator\=](../dotnet/list-operator-assign-stl-clr.md)|Reemplaza la secuencia controlada.|  
|[operator\!\= \(list\)](../dotnet/operator-inequality-list-stl-clr.md)|Determina si un objeto de `list` no es igual a otro objeto de `list` .|  
|[operator\< \(list\)](../dotnet/operator-less-than-list-stl-clr.md)|Determina si un objeto de `list` es menor que otro objeto de `list` .|  
|[operator\<\= \(list\)](../dotnet/operator-less-or-equal-list-stl-clr.md)|Determina si un objeto de `list` menor o igual que otro objeto de `list` .|  
|[operator\=\= \(list\)](../dotnet/operator-equality-list-stl-clr.md)|Determina si un objeto de `list` es igual a otro objeto de `list` .|  
|[operator\> \(list\)](../dotnet/operator-greater-than-list-stl-clr.md)|Determina si un objeto de `list` es mayor que otro objeto de `list` .|  
|[operator\>\= \(list\)](../dotnet/operator-greater-or-equal-list-stl-clr.md)|Determina si un objeto de `list` mayor o igual que otro objeto de `list` .|  
  
## Interfaces  
  
|Interfaz|Descripción|  
|--------------|-----------------|  
|<xref:System.ICloneable>|Dupliquen un objeto.|  
|<xref:System.Collections.IEnumerable>|Secuencia a través de los elementos.|  
|<xref:System.Collections.ICollection>|Mantenga el grupo de elementos.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Secuencia mediante elementos escritos.|  
|<xref:System.Collections.Generic.ICollection%601>|Mantenga el grupo de elementos escritos.|  
|IListValue\<\>|Mantenga el contenedor genérico.|  
  
## Comentarios  
 El objeto asigna y libera el almacenamiento de la secuencia que controla mientras los nodos individuales en una lista bidireccional de vínculo.  Reorganiza elementos modificando los vínculos entre los nodos, nunca copiando el contenido de un nodo a otro.  Eso significa que puede insertar y quitar elementos libremente sin elementos restantes que modifican.  Así, una lista es una buena candidata al contenedor subyacente para la clase de plantilla [queue](../dotnet/queue-stl-clr.md) o clase de plantilla [pila](../dotnet/stack-stl-clr.md).  
  
 Un objeto de `list` admite iteradores bidireccionales, que significa que se puede pasar a los elementos adyacentes dado un iterador que señale un elemento de la secuencia controlada.  Un nodo principal especial corresponde al iterador devuelto por [list::end](../dotnet/list-end-stl-clr.md)`()`.  Puede reducir este iterador para lograr el último elemento de la secuencia controlada, si existe.  Puede incrementar un iterador de la lista para lograr el nodo principal, y a continuación comparará el igual a `end()`.  Pero no puede desreferenciar el iterador devuelto por `end()`.  
  
 Observe que no puede hacer referencia a un elemento de la lista determinado directamente su posición numérica \-\- esto requiere un iterador de acceso aleatorio.  Una lista es tan `not` utilizable como el contenedor subyacente para la clase de plantilla [priority\_queue](../dotnet/priority-queue-stl-clr.md).  
  
 Un iterador de la lista almacena un identificador al nodo asociado de la lista, que a su vez almacena un identificador para el contenedor asociado.  Puede usar iteradores únicamente con los objetos contenedores asociados.  Un iterador de la lista sigue siendo válido siempre y cuando el nodo asociado de la lista se asocia a alguna lista.  Por otra parte, un iterador válido es dereferencable \-\- puede utilizarlo para obtener acceso o modificar el valor del elemento que señala \-\- siempre y cuando no es igual a `end()`.  
  
 Borrar o quitar un elemento denomina destructor por el valor almacenado.  Destruyendo el contenedor borra todos los elementos.  Así, un contenedor cuyo tipo de elemento es una clase de referencia se asegura que ningún elemento sobrevivan al contenedor.  La nota, sin embargo, que un contenedor de identificadores hace `not` destruye sus elementos.  
  
## Requisitos  
 cliext \<de**Encabezado:** \/enumerado\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [deque](../dotnet/deque-stl-clr.md)   
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [queue](../dotnet/queue-stl-clr.md)   
 [pila](../dotnet/stack-stl-clr.md)   
 [vector](../dotnet/vector-stl-clr.md)   
 [Biblioteca STL\/CLR](../dotnet/stl-clr-library-reference.md)