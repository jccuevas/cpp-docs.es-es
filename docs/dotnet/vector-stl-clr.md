---
title: vector (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::vector
dev_langs:
- C++
helpviewer_keywords:
- vector class [STL/CLR]
- <cliext/vector> header [STL/CLR]
- <vector> header [STL/CLR]
ms.assetid: f90060d5-097a-4e9d-9a26-a634b5b9c6c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: de5d09d569933dc06666ed2008081703d59c1564
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172643"
---
# <a name="vector-stlclr"></a>vector (STL/CLR)
La clase de plantilla describe un objeto que controla una secuencia de longitud variable de elementos que tiene acceso aleatorio. Utilice el contenedor de `vector` para administrar una secuencia de elementos como un bloque contiguo de almacenamiento. El bloque se implementa como una matriz que aumenta de tamaño a petición.  
  
 En la descripción siguiente, `GValue` es el mismo que `Value` a menos que el segundo es un tipo de referencia, en cuyo caso es `Value^`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename Value>  
    ref class vector  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::IVector<GValue>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Parámetros  
 Valor  
 Tipo de un elemento de la secuencia controlada.  
  
## <a name="members"></a>Miembros  
  
|Definición de tipo|Descripción|  
|---------------------|-----------------|  
|[vector::const_iterator (STL/CLR)](../dotnet/vector-const-iterator-stl-clr.md)|El tipo de un iterador constante para la secuencia controlada.|  
|[vector::const_reference (STL/CLR)](../dotnet/vector-const-reference-stl-clr.md)|El tipo de una referencia constante a un elemento.|  
|[vector::const_reverse_iterator (STL/CLR)](../dotnet/vector-const-reverse-iterator-stl-clr.md)|El tipo de un iterador invertido constante para la secuencia controlada.|  
|[vector::difference_type (STL/CLR)](../dotnet/vector-difference-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[vector::generic_container (STL/CLR)](../dotnet/vector-generic-container-stl-clr.md)|El tipo de la interfaz genérica para el contenedor.|  
|[vector::generic_iterator (STL/CLR)](../dotnet/vector-generic-iterator-stl-clr.md)|El tipo de un iterador para la interfaz genérica para el contenedor.|  
|[vector::generic_reverse_iterator (STL/CLR)](../dotnet/vector-generic-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso para la interfaz genérica para el contenedor.|  
|[vector::generic_value (STL/CLR)](../dotnet/vector-generic-value-stl-clr.md)|El tipo de un elemento de la interfaz genérica para el contenedor.|  
|[vector::iterator (STL/CLR)](../dotnet/vector-iterator-stl-clr.md)|El tipo de un iterador para la secuencia controlada.|  
|[vector::reference (STL/CLR)](../dotnet/vector-reference-stl-clr.md)|El tipo de una referencia a un elemento.|  
|[vector::reverse_iterator (STL/CLR)](../dotnet/vector-reverse-iterator-stl-clr.md)|El tipo de un iterador invertido para la secuencia controlada.|  
|[vector::size_type (STL/CLR)](../dotnet/vector-size-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[vector::value_type (STL/CLR)](../dotnet/vector-value-type-stl-clr.md)|El tipo de un elemento.|  
  
|Función miembro|Descripción|  
|---------------------|-----------------|  
|[vector::assign (STL/CLR)](../dotnet/vector-assign-stl-clr.md)|Reemplaza todos los elementos.|  
|[vector::at (STL/CLR)](../dotnet/vector-at-stl-clr.md)|Obtiene acceso a un elemento en una posición especificada.|  
|[vector::back (STL/CLR)](../dotnet/vector-back-stl-clr.md)|Obtiene acceso al último elemento.|  
|[vector::begin (STL/CLR)](../dotnet/vector-begin-stl-clr.md)|Designa el principio de la secuencia controlada.|  
|[vector::capacity (STL/CLR)](../dotnet/vector-capacity-stl-clr.md)|Informa del tamaño de almacenamiento asignado para el contenedor.|  
|[vector::clear (STL/CLR)](../dotnet/vector-clear-stl-clr.md)|Quita todos los elementos.|  
|[vector::empty (STL/CLR)](../dotnet/vector-empty-stl-clr.md)|Comprueba si no hay ningún elemento presente.|  
|[vector::end (STL/CLR)](../dotnet/vector-end-stl-clr.md)|Designa el final de la secuencia controlada.|  
|[vector::erase (STL/CLR)](../dotnet/vector-erase-stl-clr.md)|Quita los elementos de las posiciones especificadas.|  
|[vector::front (STL/CLR)](../dotnet/vector-front-stl-clr.md)|Obtiene acceso al primer elemento.|  
|[vector::insert (STL/CLR)](../dotnet/vector-insert-stl-clr.md)|Agrega un elemento en una posición especificada.|  
|[vector::pop_back (STL/CLR)](../dotnet/vector-pop-back-stl-clr.md)|Quita el último elemento.|  
|[vector::push_back (STL/CLR)](../dotnet/vector-push-back-stl-clr.md)|Agrega un nuevo elemento de la última.|  
|[vector::rbegin (STL/CLR)](../dotnet/vector-rbegin-stl-clr.md)|Designa el principio de la secuencia controlada inversa.|  
|[vector::rend (STL/CLR)](../dotnet/vector-rend-stl-clr.md)|Designa el final de la secuencia controlada inversa.|  
|[vector::reserve (STL/CLR)](../dotnet/vector-reserve-stl-clr.md)|Garantiza una capacidad de crecimiento mínimo para el contenedor.|  
|[vector::resize (STL/CLR)](../dotnet/vector-resize-stl-clr.md)|Cambia el número de elementos.|  
|[vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md)|Cuenta el número de elementos.|  
|[vector::swap (STL/CLR)](../dotnet/vector-swap-stl-clr.md)|Intercambia el contenido de dos contenedores.|  
|[vector::to_array (STL/CLR)](../dotnet/vector-to-array-stl-clr.md)|Copia la secuencia controlada en una nueva matriz.|  
|[vector::vector (STL/CLR)](../dotnet/vector-vector-stl-clr.md)|Construye un objeto contenedor.|  
  
|Property|Descripción|  
|--------------|-----------------|  
|[vector::back_item (STL/CLR)](../dotnet/vector-back-item-stl-clr.md)|Obtiene acceso al último elemento.|  
|[vector::front_item (STL/CLR)](../dotnet/vector-front-item-stl-clr.md)|Obtiene acceso al primer elemento.|  
  
|Operador|Descripción|  
|--------------|-----------------|  
|[vector::operator= (STL/CLR)](../dotnet/vector-operator-assign-stl-clr.md)|Reemplaza la secuencia controlada.|  
|[vector::operator(STL/CLR)](../dotnet/vector-operator-stl-clr.md)|Obtiene acceso a un elemento en una posición especificada.|  
|[operator!= (vector) (STL/CLR)](../dotnet/operator-inequality-vector-stl-clr.md)|Determina si un `vector` no es igual a otro objeto `vector` objeto.|  
|[operator< (vector) (STL/CLR)](../dotnet/operator-less-than-vector-stl-clr.md)|Determina si un `vector` objeto es menor que otro `vector` objeto.|  
|[operator<= (vector) (STL/CLR)](../dotnet/operator-less-or-equal-vector-stl-clr.md)|Determina si un `vector` objeto es menor o igual que otro `vector` objeto.|  
|[operator== (vector) (STL/CLR)](../dotnet/operator-equality-vector-stl-clr.md)|Determina si un `vector` es igual a otro objeto `vector` objeto.|  
|[operator> (vector) (STL/CLR)](../dotnet/operator-greater-than-vector-stl-clr.md)|Determina si un `vector` es mayor que otro objeto `vector` objeto.|  
|[operator>= (vector) (STL/CLR)](../dotnet/operator-greater-or-equal-vector-stl-clr.md)|Determina si un `vector` objeto es mayor o igual que otro `vector` objeto.|  
  
## <a name="interfaces"></a>Interfaces  
  
|Interfaz|Descripción|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplicar un objeto.|  
|<xref:System.Collections.IEnumerable>|Secuencia a través de los elementos.|  
|<xref:System.Collections.ICollection>|Mantener el grupo de elementos.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Secuencia a través de los elementos con tipo.|  
|<xref:System.Collections.Generic.ICollection%601>|Mantener el grupo de elementos con tipo.|  
|<xref:System.Collections.Generic.IList%601>|Mantener un grupo ordenado de elementos con tipo.|  
|IVector < valor\>|Mantener contenedor genérico.|  
  
## <a name="remarks"></a>Comentarios  
 El objeto asigna y libera almacenamiento para la secuencia que controla a través de una matriz almacenada de `Value` elementos, lo que aumenta de tamaño a petición. El crecimiento tiene lugar de tal modo que el costo de anexar un nuevo elemento de tiempo constante amortizado. En otras palabras, el costo de agregar elementos al final no aumenta, en promedio, como la longitud de la mayor obtiene de la secuencia controlada. Por lo tanto, un vector es un buen candidato para el contenedor subyacente para la clase de plantilla [(STL/CLR) de la pila](../dotnet/stack-stl-clr.md).  
  
 A `vector` iteradores de acceso aleatorio admite, lo que significa que puede hacer referencia a un elemento directamente según su posición numérica, contando desde cero para el primer elemento (la parte delantera), a `size() - 1` para el último elemento (atrás). También significa que un vector es un buen candidato para el contenedor subyacente para la clase de plantilla [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md).  
  
 Un iterador de vector almacena un identificador a su objeto de vector asociado, junto con la diferencia del elemento que este designa. Sólo puede usar iteradores con sus objetos de contenedor asociado. La diferencia de un elemento de vector es igual a su posición.  
  
 Insertar o borrar elementos puede cambiar el valor del elemento almacenado en una posición determinada, por lo que también puede cambiar el valor designado por un iterador. (El contenedor puede tener que copiar los elementos de seguridad o hacia abajo para crear un "agujero" antes de una instrucción insert o para rellenar un "agujero" después de un borrado). Sin embargo, un iterador de vector sigue siendo válido siempre y cuando la diferencia está en el intervalo `[0, size()]`. Además, un iterador válido permanece dereferencable: se puede utilizar para tener acceso o modificar el valor del elemento designa--siempre y cuando su diferencia no es igual a `size()`.  
  
 Borrar o quitar un elemento llama al destructor para definir el valor almacenado. Destruir el contenedor, borrará todos los elementos. Por lo tanto, un contenedor cuyo tipo de elemento es una clase ref garantiza que ningún elemento su duración mayor que el contenedor. Sin embargo, tenga en cuenta que un contenedor de identificadores de destruir sus elementos.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/vector >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [lista (STL/CLR)](../dotnet/list-stl-clr.md)   
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [cola (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [pila (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md)  
 [Referencia de la biblioteca STL/CLR](../dotnet/stl-clr-library-reference.md)