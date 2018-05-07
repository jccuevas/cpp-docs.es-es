---
title: lista (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list
dev_langs:
- C++
helpviewer_keywords:
- <cliext/list> header [STL/CLR]
- list class [STL/CLR]
- <list> header [STL/CLR]
ms.assetid: a70c45c8-a257-4f6b-8434-b27ff6685bac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4ff009da3ca29697e9b3affceb424bcd84b9b896
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="list-stlclr"></a>list (STL/CLR)
La clase de plantilla describe un objeto que controla una secuencia de longitud variable de elementos que tiene acceso bidireccional. Utilice el contenedor de `list` para administrar una secuencia de elementos como una lista vinculada bidireccional de nodos, cada uno de ellos almacenar un elemento.  
  
 En la descripción siguiente, `GValue` es el mismo que `Value` a menos que el segundo es un tipo de referencia, en cuyo caso es `Value^`.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
 Valor  
 Tipo de un elemento de la secuencia controlada.  
  
## <a name="members"></a>Miembros  
  
|Definición de tipo|Descripción|  
|---------------------|-----------------|  
|[list::const_iterator (STL/CLR)](../dotnet/list-const-iterator-stl-clr.md)|El tipo de un iterador constante para la secuencia controlada.|  
|[list::const_reference (STL/CLR)](../dotnet/list-const-reference-stl-clr.md)|El tipo de una referencia constante a un elemento.|  
|[list::const_reverse_iterator (STL/CLR)](../dotnet/list-const-reverse-iterator-stl-clr.md)|El tipo de un iterador invertido constante para la secuencia controlada.|  
|[list::difference_type (STL/CLR)](../dotnet/list-difference-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[list::generic_container (STL/CLR)](../dotnet/list-generic-container-stl-clr.md)|El tipo de la interfaz genérica para el contenedor.|  
|[list::generic_iterator (STL/CLR)](../dotnet/list-generic-iterator-stl-clr.md)|El tipo de un iterador para la interfaz genérica para el contenedor.|  
|[list::generic_reverse_iterator (STL/CLR)](../dotnet/list-generic-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso para la interfaz genérica para el contenedor.|  
|[list::generic_value (STL/CLR)](../dotnet/list-generic-value-stl-clr.md)|El tipo de un elemento de la interfaz genérica para el contenedor.|  
|[list::iterator (STL/CLR)](../dotnet/list-iterator-stl-clr.md)|El tipo de un iterador para la secuencia controlada.|  
|[list::reference (STL/CLR)](../dotnet/list-reference-stl-clr.md)|El tipo de una referencia a un elemento.|  
|[list::reverse_iterator (STL/CLR)](../dotnet/list-reverse-iterator-stl-clr.md)|El tipo de un iterador invertido para la secuencia controlada.|  
|[list::size_type (STL/CLR)](../dotnet/list-size-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[list::value_type (STL/CLR)](../dotnet/list-value-type-stl-clr.md)|El tipo de un elemento.|  
  
|Función miembro|Descripción|  
|---------------------|-----------------|  
|[list::assign (STL/CLR)](../dotnet/list-assign-stl-clr.md)|Reemplaza todos los elementos.|  
|[list::back (STL/CLR)](../dotnet/list-back-stl-clr.md)|Obtiene acceso al último elemento.|  
|[list::begin (STL/CLR)](../dotnet/list-begin-stl-clr.md)|Designa el principio de la secuencia controlada.|  
|[list::clear (STL/CLR)](../dotnet/list-clear-stl-clr.md)|Quita todos los elementos.|  
|[list::empty (STL/CLR)](../dotnet/list-empty-stl-clr.md)|Comprueba si no hay ningún elemento presente.|  
|[list::end (STL/CLR)](../dotnet/list-end-stl-clr.md)|Designa el final de la secuencia controlada.|  
|[list::erase (STL/CLR)](../dotnet/list-erase-stl-clr.md)|Quita los elementos de las posiciones especificadas.|  
|[list::front (STL/CLR)](../dotnet/list-front-stl-clr.md)|Obtiene acceso al primer elemento.|  
|[list::insert (STL/CLR)](../dotnet/list-insert-stl-clr.md)|Agrega un elemento en una posición especificada.|  
|[list::list (STL/CLR)](../dotnet/list-list-stl-clr.md)|Construye un objeto contenedor.|  
|[list::merge (STL/CLR)](../dotnet/list-merge-stl-clr.md)|Combina dos secuencias controladas ordenadas.|  
|[list::pop_back (STL/CLR)](../dotnet/list-pop-back-stl-clr.md)|Quita el último elemento.|  
|[list::pop_front (STL/CLR)](../dotnet/list-pop-front-stl-clr.md)|Quita el primer elemento.|  
|[list::push_back (STL/CLR)](../dotnet/list-push-back-stl-clr.md)|Agrega un nuevo elemento de la última.|  
|[list::push_front (STL/CLR)](../dotnet/list-push-front-stl-clr.md)|Agrega un nuevo primer elemento.|  
|[list::rbegin (STL/CLR)](../dotnet/list-rbegin-stl-clr.md)|Designa el principio de la secuencia controlada inversa.|  
|[list::remove (STL/CLR)](../dotnet/list-remove-stl-clr.md)|Quita un elemento con un valor especificado.|  
|[list::remove_if (STL/CLR)](../dotnet/list-remove-if-stl-clr.md)|Quita los elementos que superan una prueba especificada.|  
|[list::rend (STL/CLR)](../dotnet/list-rend-stl-clr.md)|Designa el final de la secuencia controlada inversa.|  
|[list::resize (STL/CLR)](../dotnet/list-resize-stl-clr.md)|Cambia el número de elementos.|  
|[list::reverse (STL/CLR)](../dotnet/list-reverse-stl-clr.md)|Invierte la secuencia controlada.|  
|[list::size (STL/CLR)](../dotnet/list-size-stl-clr.md)|Cuenta el número de elementos.|  
|[list::sort (STL/CLR)](../dotnet/list-sort-stl-clr.md)|Ordena la secuencia controlada.|  
|[list::splice (STL/CLR)](../dotnet/list-splice-stl-clr.md)|Vuelve a unir vínculos entre nodos.|  
|[list::swap (STL/CLR)](../dotnet/list-swap-stl-clr.md)|Intercambia el contenido de dos contenedores.|  
|[list::to_array (STL/CLR)](../dotnet/list-to-array-stl-clr.md)|Copia la secuencia controlada en una nueva matriz.|  
|[list::unique (STL/CLR)](../dotnet/list-unique-stl-clr.md)|Quita los elementos adyacentes que superan una prueba especificada.|  
  
|Property|Descripción|  
|--------------|-----------------|  
|[list::back_item (STL/CLR)](../dotnet/list-back-item-stl-clr.md)|Obtiene acceso al último elemento.|  
|[list::front_item (STL/CLR)](../dotnet/list-front-item-stl-clr.md)|Obtiene acceso al primer elemento.|  
  
|Operador|Descripción|  
|--------------|-----------------|  
|[list::operator= (STL/CLR)](../dotnet/list-operator-assign-stl-clr.md)|Reemplaza la secuencia controlada.|  
|[operator!= (list) (STL/CLR)](../dotnet/operator-inequality-list-stl-clr.md)|Determina si un `list` no es igual a otro objeto `list` objeto.|  
|[operator< (list) (STL/CLR)](../dotnet/operator-less-than-list-stl-clr.md)|Determina si un `list` objeto es menor que otro `list` objeto.|  
|[operator<= (list) (STL/CLR)](../dotnet/operator-less-or-equal-list-stl-clr.md)|Determina si un `list` objeto es menor o igual que otro `list` objeto.|  
|[operator== (list) (STL/CLR)](../dotnet/operator-equality-list-stl-clr.md)|Determina si un `list` es igual a otro objeto `list` objeto.|  
|[operator> (list) (STL/CLR)](../dotnet/operator-greater-than-list-stl-clr.md)|Determina si un `list` es mayor que otro objeto `list` objeto.|  
|[operator>= (list) (STL/CLR)](../dotnet/operator-greater-or-equal-list-stl-clr.md)|Determina si un `list` objeto es mayor o igual que otro `list` objeto.|  
  
## <a name="interfaces"></a>Interfaces  
  
|Interfaz|Descripción|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplicar un objeto.|  
|<xref:System.Collections.IEnumerable>|Secuencia a través de los elementos.|  
|<xref:System.Collections.ICollection>|Mantener el grupo de elementos.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Secuencia a través de los elementos con tipo.|  
|<xref:System.Collections.Generic.ICollection%601>|Mantener el grupo de elementos con tipo.|  
|IList\<valor >|Mantener contenedor genérico.|  
  
## <a name="remarks"></a>Comentarios  
 El objeto asigna y libera almacenamiento para la secuencia que controla como nodos individuales en una lista de vínculos bidireccional. Reorganiza los elementos por la modificación de los vínculos entre los nodos, nunca copiando el contenido de un nodo a otro. Esto significa que puede insertar y quitar elementos libremente sin alterar los elementos restantes. Por lo tanto, una lista es un buen candidato para el contenedor subyacente para la clase de plantilla [cola (STL/CLR)](../dotnet/queue-stl-clr.md) o clase de plantilla [(STL/CLR) de la pila](../dotnet/stack-stl-clr.md).  
  
 Un `list` objeto admite los iteradores bidireccionales, lo que significa que puede ejecutar paso a paso para los elementos adyacentes que proporciona un iterador que designa un elemento de la secuencia controlada. Un nodo principal especial que se corresponde con el iterador devuelto por [List:: end (STL/CLR)](../dotnet/list-end-stl-clr.md)`()`. Puede reducir este iterador para llegar al último elemento de la secuencia controlada, si está presente. Puede incrementar un iterador de lista para alcanzar el nodo principal y, a continuación, comparará igual a `end()`. Pero no se puede desreferenciar el iterador devuelto por `end()`.  
  
 Tenga en cuenta que no puede hacer referencia a un elemento de lista directamente dado su posición numérica, requiere un iterador de acceso aleatorio. Por lo que es una lista `not` puede usar como contenedor subyacente para la clase de plantilla [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md).  
  
 Un iterador de lista almacena un identificador a su nodo lista asociada, que a su vez almacena un identificador a su contenedor asociado. Sólo puede usar iteradores con sus objetos de contenedor asociado. Un iterador de lista es válido siempre y cuando su nodo de lista asociada está asociado a alguna lista. Además, un iterador válido es dereferencable, se puede utilizar para tener acceso o modificar el valor del elemento designa--siempre y cuando no es igual a `end()`.  
  
 Borrar o quitar un elemento llama al destructor para definir el valor almacenado. Destruir el contenedor, borrará todos los elementos. Por lo tanto, un contenedor cuyo tipo de elemento es una clase ref garantiza que ningún elemento su duración mayor que el contenedor. Sin embargo, tenga en cuenta que un contenedor de identificadores no `not` destruir sus elementos.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/list >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [cola (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [pila (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [vector (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Referencia de la biblioteca STL/CLR](../dotnet/stl-clr-library-reference.md)