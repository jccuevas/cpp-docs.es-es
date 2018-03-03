---
title: establecer (STL/CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::set
dev_langs:
- C++
helpviewer_keywords:
- <cliext/set> header [STL/CLR]
- <set> header [STL/CLR]
- set class [STL/CLR]
ms.assetid: 27d3628c-741a-43a7-bef1-5085536f679e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9624f08c54629657e7f52c2c688d2083aa557a56
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="set-stlclr"></a>set (STL/CLR)
La clase de plantilla describe un objeto que controla una secuencia de longitud variable de elementos que tiene acceso bidireccional. Utilice el contenedor de `set` para administrar una secuencia de elementos como un árbol equilibrado (casi) ordenada de nodos, cada uno de ellos almacenar un elemento.  
  
 En la descripción siguiente, `GValue` es el mismo que `GKey`, que a su vez es igual a `Key` a menos que el segundo es un tipo de referencia, en cuyo caso es `Key^`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename Key>  
    ref class set  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::ITree<Gkey, GValue>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Parámetros  
 Key  
 El tipo del componente clave de un elemento de la secuencia controlada.  
  
## <a name="members"></a>Miembros  
  
|Definición de tipo|Descripción|  
|---------------------|-----------------|  
|[set::const_iterator (STL/CLR)](../dotnet/set-const-iterator-stl-clr.md)|El tipo de un iterador constante para la secuencia controlada.|  
|[set::const_reference (STL/CLR)](../dotnet/set-const-reference-stl-clr.md)|El tipo de una referencia constante a un elemento.|  
|[set::const_reverse_iterator (STL/CLR)](../dotnet/set-const-reverse-iterator-stl-clr.md)|El tipo de un iterador invertido constante para la secuencia controlada.|  
|[set::difference_type (STL/CLR)](../dotnet/set-difference-type-stl-clr.md)|El tipo de una distancia (posiblemente con signo) entre dos elementos.|  
|[set::generic_container (STL/CLR)](../dotnet/set-generic-container-stl-clr.md)|El tipo de la interfaz genérica para el contenedor.|  
|[set::generic_iterator (STL/CLR)](../dotnet/set-generic-iterator-stl-clr.md)|El tipo de un iterador para la interfaz genérica para el contenedor.|  
|[set::generic_reverse_iterator (STL/CLR)](../dotnet/set-generic-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso para la interfaz genérica para el contenedor.|  
|[set::generic_value (STL/CLR)](../dotnet/set-generic-value-stl-clr.md)|El tipo de un elemento de la interfaz genérica para el contenedor.|  
|[set::iterator (STL/CLR)](../dotnet/set-iterator-stl-clr.md)|El tipo de un iterador para la secuencia controlada.|  
|[set::key_compare (STL/CLR)](../dotnet/set-key-compare-stl-clr.md)|El delegado para dos claves de ordenación.|  
|[set::key_type (STL/CLR)](../dotnet/set-key-type-stl-clr.md)|El tipo de una clave de ordenación.|  
|[set::reference (STL/CLR)](../dotnet/set-reference-stl-clr.md)|El tipo de una referencia a un elemento.|  
|[set::reverse_iterator (STL/CLR)](../dotnet/set-reverse-iterator-stl-clr.md)|El tipo de un iterador invertido para la secuencia controlada.|  
|[set::size_type (STL/CLR)](../dotnet/set-size-type-stl-clr.md)|El tipo de una distancia (positivo) entre dos elementos.|  
|[set::value_compare (STL/CLR)](../dotnet/set-value-compare-stl-clr.md)|El delegado de ordenación para los dos valores de elemento.|  
|[set::value_type (STL/CLR)](../dotnet/set-value-type-stl-clr.md)|El tipo de un elemento.|  
  
|Función miembro|Descripción|  
|---------------------|-----------------|  
|[set::begin (STL/CLR)](../dotnet/set-begin-stl-clr.md)|Designa el principio de la secuencia controlada.|  
|[set::clear (STL/CLR)](../dotnet/set-clear-stl-clr.md)|Quita todos los elementos.|  
|[set::count (STL/CLR)](../dotnet/set-count-stl-clr.md)|Recuentos de elementos que coinciden con una clave especificada.|  
|[set::empty (STL/CLR)](../dotnet/set-empty-stl-clr.md)|Comprueba si no hay ningún elemento presente.|  
|[set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)|Designa el final de la secuencia controlada.|  
|[set::equal_range (STL/CLR)](../dotnet/set-equal-range-stl-clr.md)|Busca el intervalo que coincide con una clave especificada.|  
|[set::erase (STL/CLR)](../dotnet/set-erase-stl-clr.md)|Quita los elementos de las posiciones especificadas.|  
|[set::find (STL/CLR)](../dotnet/set-find-stl-clr.md)|Busca un elemento que coincide con una clave especificada.|  
|[set::insert (STL/CLR)](../dotnet/set-insert-stl-clr.md)|Agrega elementos.|  
|[set::key_comp (STL/CLR)](../dotnet/set-key-comp-stl-clr.md)|Copia al delegado para dos claves de ordenación.|  
|[set::lower_bound (STL/CLR)](../dotnet/set-lower-bound-stl-clr.md)|Busca el comienzo del intervalo que coincide con una clave especificada.|  
|[set::make_value (STL/CLR)](../dotnet/set-make-value-stl-clr.md)|Construye un objeto de valor.|  
|[set::rbegin (STL/CLR)](../dotnet/set-rbegin-stl-clr.md)|Designa el principio de la secuencia controlada inversa.|  
|[set::rend (STL/CLR)](../dotnet/set-rend-stl-clr.md)|Designa el final de la secuencia controlada inversa.|  
|[set::set (STL/CLR)](../dotnet/set-set-stl-clr.md)|Construye un objeto contenedor.|  
|[set::size (STL/CLR)](../dotnet/set-size-stl-clr.md)|Cuenta el número de elementos.|  
|[set::swap (STL/CLR)](../dotnet/set-swap-stl-clr.md)|Intercambia el contenido de dos contenedores.|  
|[set::to_array (STL/CLR)](../dotnet/set-to-array-stl-clr.md)|Copia la secuencia controlada en una nueva matriz.|  
|[set::upper_bound (STL/CLR)](../dotnet/set-upper-bound-stl-clr.md)|Busca el final del intervalo que coincide con una clave especificada.|  
|[set::value_comp (STL/CLR)](../dotnet/set-value-comp-stl-clr.md)|Copia al delegado de ordenación para los dos valores de elemento.|  
  
|Operador|Descripción|  
|--------------|-----------------|  
|[set::operator= (STL/CLR)](../dotnet/set-operator-assign-stl-clr.md)|Reemplaza la secuencia controlada.|  
|[operator!= (set) (STL/CLR)](../dotnet/operator-inequality-set-stl-clr.md)|Determina si un `set` no es igual a otro objeto `set` objeto.|  
|[operator< (set) (STL/CLR)](../dotnet/operator-less-than-set-stl-clr.md)|Determina si un `set` objeto es menor que otro `set` objeto.|  
|[operator<= (set) (STL/CLR)](../dotnet/operator-less-or-equal-set-stl-clr.md)|Determina si un `set` objeto es menor o igual que otro `set` objeto.|  
|[operator== (set) (STL/CLR)](../dotnet/operator-equality-set-stl-clr.md)|Determina si un `set` es igual a otro objeto `set` objeto.|  
|[operator> (set) (STL/CLR)](../dotnet/operator-greater-than-set-stl-clr.md)|Determina si un `set` es mayor que otro objeto `set` objeto.|  
|[operator>= (set) (STL/CLR)](../dotnet/operator-greater-or-equal-set-stl-clr.md)|Determina si un `set` objeto es mayor o igual que otro `set` objeto.|  
  
## <a name="interfaces"></a>Interfaces  
  
|Interfaz|Descripción|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplicar un objeto.|  
|<xref:System.Collections.IEnumerable>|Secuencia a través de los elementos.|  
|<xref:System.Collections.ICollection>|Mantener el grupo de elementos.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Secuencia a través de los elementos con tipo.|  
|<xref:System.Collections.Generic.ICollection%601>|Mantener el grupo de elementos con tipo.|  
|ITree\<clave, valor >|Mantener contenedor genérico.|  
  
## <a name="remarks"></a>Comentarios  
 El objeto asigna y libera almacenamiento para la secuencia que controla como nodos individuales. Inserta elementos en un árbol equilibrado (casi) que mantiene ordenada por la modificación de los vínculos entre los nodos, nunca copiando el contenido de un nodo a otro. Esto significa que puede insertar y quitar elementos libremente sin alterar los elementos restantes.  
  
 El objeto ordena la secuencia controla mediante una llamada a un objeto de delegado almacenado de tipo [Set:: key_compare (STL/CLR)](../dotnet/set-key-compare-stl-clr.md). Puede especificar el objeto de delegado almacenado cuando se construye el conjunto; Si no se especifica ningún objeto de delegado, el valor predeterminado es la comparación `operator<(key_type, key_type)`. Tener acceso a este objeto almacenado llamando a la función miembro [key_comp (STL/CLR)](../dotnet/set-key-comp-stl-clr.md)`()`.  
  
 Este tipo de objeto de delegado debe imponer una ordenación débil estricta en claves de tipo [Set:: KEY_TYPE (STL/CLR)](../dotnet/set-key-type-stl-clr.md). Es decir, para las dos claves `X` y `Y`:  
  
 `key_comp()(X, Y)`Devuelve el valor booleano mismo resultado en cada llamada.  
  
 Si `key_comp()(X, Y)` es true, a continuación, `key_comp()(Y, X)` debe ser false.  
  
 Si `key_comp()(X, Y)` es true, a continuación, `X` se dice que se ordenan antes que `Y`.  
  
 Si `!key_comp()(X, Y) && !key_comp()(Y, X)` es true, a continuación, `X` y `Y` se dice que tienen una ordenación equivalente.  
  
 Para cualquier elemento `X` que precede a `Y` en la secuencia controlada, `key_comp()(Y, X)` es false. (Para el objeto de delegado de forma predeterminada, las claves nunca disminuyen en valor.) A diferencia de la clase de plantilla [establecer](../dotnet/set-stl-clr.md), un objeto de clase de plantilla `set` no requiere que las claves para todos los elementos sean únicas. (Dos o más teclas pueden tener una ordenación equivalente).  
  
 Cada elemento actúa como un ey y un valor. La secuencia se representa de forma que permite la búsqueda, inserción y eliminación de un elemento arbitrario con una serie de operaciones proporcionales al logaritmo del número de elementos en la secuencia (tiempo logarítmico). Además, la inserción de un elemento no invalida ningún iterador y al quitar un elemento solo se invalidan los iteradores que apuntan al elemento quitado.  
  
 Un conjunto es compatible con los iteradores bidireccionales, lo que significa que puede ejecutar paso a paso para los elementos adyacentes que proporciona un iterador que designa un elemento de la secuencia controlada. Un nodo principal especial que se corresponde con el iterador devuelto por [Set:: end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`. Puede reducir este iterador para llegar al último elemento de la secuencia controlada, si está presente. Puede incrementar un iterador de conjunto para alcanzar el nodo principal y, a continuación, comparará igual a `end()`. Pero no se puede desreferenciar el iterador devuelto por `end()`.  
  
 Tenga en cuenta que no puede hacer referencia a un elemento de conjunto directamente dado su posición numérica, requiere un iterador de acceso aleatorio.  
  
 Un iterador de conjunto almacena un identificador a su nodo de conjunto asociado, que a su vez almacena un identificador a su contenedor asociado. Sólo puede usar iteradores con sus objetos de contenedor asociado. Un iterador de conjunto es válido siempre y cuando su nodo de conjunto asociado está asociado a un conjunto. Además, un iterador válido es dereferencable, se puede utilizar para tener acceso o modificar el valor del elemento designa--siempre y cuando no es igual a `end()`.  
  
 Borrar o quitar un elemento llama al destructor para definir el valor almacenado. Destruir el contenedor, borrará todos los elementos. Por lo tanto, un contenedor cuyo tipo de elemento es una clase ref garantiza que ningún elemento su duración mayor que el contenedor. Sin embargo, tenga en cuenta que un contenedor de identificadores no `not` destruir sus elementos.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [asignar (STL/CLR)](../dotnet/map-stl-clr.md)   
 [conjunto](../dotnet/set-stl-clr.md)   
 [conjunto](../dotnet/set-stl-clr.md)   
 [Referencia de la biblioteca STL/CLR](../dotnet/stl-clr-library-reference.md)