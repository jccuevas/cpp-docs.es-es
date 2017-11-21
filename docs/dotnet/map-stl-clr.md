---
title: "asignación (STL/CLR) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::map
dev_langs: C++
helpviewer_keywords:
- <map> header [STL/CLR]
- map class [STL/CLR]
- <cliext/map> header [STL/CLR]
ms.assetid: 8b0a7764-b5e4-4175-a802-82b72eb8662a
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6b6e535dac08e473e281f45e45a084d856c931b7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="map-stlclr"></a>map (STL/CLR)
La clase de plantilla describe un objeto que controla una secuencia de longitud variable de elementos que tiene acceso bidireccional. Utilice el contenedor de `map` para administrar una secuencia de elementos como un árbol equilibrado (casi) ordenada de nodos, cada uno de ellos almacenar un elemento. Un elemento consta de una clave, para ordenar la secuencia y un valor asignado, que va a lo largo de la transferencia.  
  
 En la descripción siguiente, `GValue` es igual que:  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 donde:  
  
 `GKey`es el mismo que `Key` a menos que el segundo es un tipo de referencia, en cuyo caso es`Key^`  
  
 `GMapped`es el mismo que `Mapped` a menos que el segundo es un tipo de referencia, en cuyo caso es`Mapped^`  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename Key,  
    typename Mapped>  
    ref class map  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        System::Collections::Generic::IDictionary<Gkey, GMapped>,  
        Microsoft::VisualC::StlClr::ITree<Gkey, GValue>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Parámetros  
 Key  
 El tipo del componente clave de un elemento de la secuencia controlada.  
  
 asignado  
 El tipo del componente adicional de un elemento de la secuencia controlada.  
  
## <a name="members"></a>Miembros  
  
|Definición de tipo|Descripción|  
|---------------------|-----------------|  
|[map::const_iterator (STL/CLR)](../dotnet/map-const-iterator-stl-clr.md)|El tipo de un iterador constante para la secuencia controlada.|  
|[map::const_reference (STL/CLR)](../dotnet/map-const-reference-stl-clr.md)|El tipo de una referencia constante a un elemento.|  
|[map::const_reverse_iterator (STL/CLR)](../dotnet/map-const-reverse-iterator-stl-clr.md)|El tipo de un iterador invertido constante para la secuencia controlada.|  
|[map::difference_type (STL/CLR)](../dotnet/map-difference-type-stl-clr.md)|El tipo de una distancia (posiblemente con signo) entre dos elementos.|  
|[map::generic_container (STL/CLR)](../dotnet/map-generic-container-stl-clr.md)|El tipo de la interfaz genérica para el contenedor.|  
|[map::generic_iterator (STL/CLR)](../dotnet/map-generic-iterator-stl-clr.md)|El tipo de un iterador para la interfaz genérica para el contenedor.|  
|[map::generic_reverse_iterator (STL/CLR)](../dotnet/map-generic-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso para la interfaz genérica para el contenedor.|  
|[map::generic_value (STL/CLR)](../dotnet/map-generic-value-stl-clr.md)|El tipo de un elemento de la interfaz genérica para el contenedor.|  
|[map::iterator (STL/CLR)](../dotnet/map-iterator-stl-clr.md)|El tipo de un iterador para la secuencia controlada.|  
|[map::key_compare (STL/CLR)](../dotnet/map-key-compare-stl-clr.md)|El delegado para dos claves de ordenación.|  
|[map::key_type (STL/CLR)](../dotnet/map-key-type-stl-clr.md)|El tipo de una clave de ordenación.|  
|[map::mapped_type (STL/CLR)](../dotnet/map-mapped-type-stl-clr.md)|El tipo del valor asignado asociado a cada clave.|  
|[map::reference (STL/CLR)](../dotnet/map-reference-stl-clr.md)|El tipo de una referencia a un elemento.|  
|[map::reverse_iterator (STL/CLR)](../dotnet/map-reverse-iterator-stl-clr.md)|El tipo de un iterador invertido para la secuencia controlada.|  
|[map::size_type (STL/CLR)](../dotnet/map-size-type-stl-clr.md)|El tipo de una distancia (positivo) entre dos elementos.|  
|[map::value_compare (STL/CLR)](../dotnet/map-value-compare-stl-clr.md)|El delegado de ordenación para los dos valores de elemento.|  
|[map::value_type (STL/CLR)](../dotnet/map-value-type-stl-clr.md)|El tipo de un elemento.|  
  
|Función miembro|Descripción|  
|---------------------|-----------------|  
|[map::begin (STL/CLR)](../dotnet/map-begin-stl-clr.md)|Designa el principio de la secuencia controlada.|  
|[map::clear (STL/CLR)](../dotnet/map-clear-stl-clr.md)|Quita todos los elementos.|  
|[map::count (STL/CLR)](../dotnet/map-count-stl-clr.md)|Recuentos de elementos que coinciden con una clave especificada.|  
|[map::empty (STL/CLR)](../dotnet/map-empty-stl-clr.md)|Comprueba si no hay ningún elemento presente.|  
|[map::end (STL/CLR)](../dotnet/map-end-stl-clr.md)|Designa el final de la secuencia controlada.|  
|[map::equal_range (STL/CLR)](../dotnet/map-equal-range-stl-clr.md)|Busca el intervalo que coincide con una clave especificada.|  
|[map::erase (STL/CLR)](../dotnet/map-erase-stl-clr.md)|Quita los elementos de las posiciones especificadas.|  
|[map::find (STL/CLR)](../dotnet/map-find-stl-clr.md)|Busca un elemento que coincide con una clave especificada.|  
|[map::insert (STL/CLR)](../dotnet/map-insert-stl-clr.md)|Agrega elementos.|  
|[map::key_comp (STL/CLR)](../dotnet/map-key-comp-stl-clr.md)|Copia al delegado para dos claves de ordenación.|  
|[map::lower_bound (STL/CLR)](../dotnet/map-lower-bound-stl-clr.md)|Busca el comienzo del intervalo que coincide con una clave especificada.|  
|[map::make_value (STL/CLR)](../dotnet/map-make-value-stl-clr.md)|Construye un objeto de valor.|  
|[map::map (STL/CLR)](../dotnet/map-map-stl-clr.md)|Construye un objeto contenedor.|  
|[map::rbegin (STL/CLR)](../dotnet/map-rbegin-stl-clr.md)|Designa el principio de la secuencia controlada inversa.|  
|[map::rend (STL/CLR)](../dotnet/map-rend-stl-clr.md)|Designa el final de la secuencia controlada inversa.|  
|[map::size (STL/CLR)](../dotnet/map-size-stl-clr.md)|Cuenta el número de elementos.|  
|[map::swap (STL/CLR)](../dotnet/map-swap-stl-clr.md)|Intercambia el contenido de dos contenedores.|  
|[map::to_array (STL/CLR)](../dotnet/map-to-array-stl-clr.md)|Copia la secuencia controlada en una nueva matriz.|  
|[map::upper_bound (STL/CLR)](../dotnet/map-upper-bound-stl-clr.md)|Busca el final del intervalo que coincide con una clave especificada.|  
|[map::value_comp (STL/CLR)](../dotnet/map-value-comp-stl-clr.md)|Copia al delegado de ordenación para los dos valores de elemento.|  
  
|Operador|Descripción|  
|--------------|-----------------|  
|[map::operator= (STL/CLR)](../dotnet/map-operator-assign-stl-clr.md)|Reemplaza la secuencia controlada.|  
|[map::operator(STL/CLR)](../dotnet/map-operator-stl-clr.md)|Asigna una clave a su valor asignado asociado.|  
|[operator!= (map) (STL/CLR)](../dotnet/operator-inequality-map-stl-clr.md)|Determina si un `map` no es igual a otro objeto `map` objeto.|  
|[operator< (map) (STL/CLR)](../dotnet/operator-less-than-map-stl-clr.md)|Determina si un `map` objeto es menor que otro `map` objeto.|  
|[operator<= (map) (STL/CLR)](../dotnet/operator-less-or-equal-map-stl-clr.md)|Determina si un `map` objeto es menor o igual que otro `map` objeto.|  
|[operator== (map) (STL/CLR)](../dotnet/operator-equality-map-stl-clr.md)|Determina si un `map` es igual a otro objeto `map` objeto.|  
|[operator> (map) (STL/CLR)](../dotnet/operator-greater-than-map-stl-clr.md)|Determina si un `map` es mayor que otro objeto `map` objeto.|  
|[operator>= (map) (STL/CLR)](../dotnet/operator-greater-or-equal-map-stl-clr.md)|Determina si un `map` objeto es mayor o igual que otro `map` objeto.|  
  
## <a name="interfaces"></a>Interfaces  
  
|Interfaz|Descripción|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplicar un objeto.|  
|<xref:System.Collections.IEnumerable>|Secuencia a través de los elementos.|  
|<xref:System.Collections.ICollection>|Mantener el grupo de elementos.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Secuencia a través de los elementos con tipo.|  
|<xref:System.Collections.Generic.ICollection%601>|Mantener el grupo de elementos con tipo.|  
|<xref:System.Collections.Generic.IDictionary%602>|Mantener el grupo de {clave, valor} pares.|  
|ITree < clave, valor >|Mantener contenedor genérico.|  
  
## <a name="remarks"></a>Comentarios  
 El objeto asigna y libera almacenamiento para la secuencia que controla como nodos individuales. Inserta elementos en un árbol equilibrado (casi) que mantiene ordenada por la modificación de los vínculos entre los nodos, nunca copiando el contenido de un nodo a otro. Esto significa que puede insertar y quitar elementos libremente sin alterar los elementos restantes.  
  
 El objeto ordena la secuencia controla mediante una llamada a un objeto de delegado almacenado de tipo [Map:: key_compare (STL/CLR)](../dotnet/map-key-compare-stl-clr.md). Puede especificar el objeto de delegado almacenado cuando se crea la asignación; Si no se especifica ningún objeto de delegado, el valor predeterminado es la comparación `operator<(key_type, key_type)`. Tener acceso a este objeto almacenado llamando a la función miembro [Map:: key_comp (STL/CLR)](../dotnet/map-key-comp-stl-clr.md)`()`.  
  
 Este tipo de objeto de delegado debe imponer una ordenación débil estricta en claves de tipo [Map:: KEY_TYPE (STL/CLR)](../dotnet/map-key-type-stl-clr.md). Es decir, para las dos claves `X` y `Y`:  
  
 `key_comp()(X, Y)`Devuelve el valor booleano mismo resultado en cada llamada.  
  
 Si `key_comp()(X, Y)` es true, a continuación, `key_comp()(Y, X)` debe ser false.  
  
 Si `key_comp()(X, Y)` es true, a continuación, `X` se dice que se ordenan antes que `Y`.  
  
 Si `!key_comp()(X, Y) && !key_comp()(Y, X)` es true, a continuación, `X` y `Y` se dice que tienen una ordenación equivalente.  
  
 Para cualquier elemento `X` que precede a `Y` en la secuencia controlada, `key_comp()(Y, X)` es false. (Para el objeto de delegado de forma predeterminada, las claves nunca disminuyen en valor.) A diferencia de la clase de plantilla [mapa](../dotnet/map-stl-clr.md), un objeto de clase de plantilla `map` no requiere que las claves para todos los elementos sean únicas. (Dos o más teclas pueden tener una ordenación equivalente).  
  
 Cada elemento contiene una clave independiente y un valor asignado. La secuencia se representa de forma que permite la búsqueda, inserción y eliminación de un elemento arbitrario con una serie de operaciones proporcionales al logaritmo del número de elementos en la secuencia (tiempo logarítmico). Además, la inserción de un elemento no invalida ningún iterador y al quitar un elemento solo se invalidan los iteradores que apuntan al elemento quitado.  
  
 Una asignación es compatible con los iteradores bidireccionales, lo que significa que puede ejecutar paso a paso para los elementos adyacentes que proporciona un iterador que designa un elemento de la secuencia controlada. Un nodo principal especial que se corresponde con el iterador devuelto por [Map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`. Puede reducir este iterador para llegar al último elemento de la secuencia controlada, si está presente. Puede incrementar un iterador de mapa para alcanzar el nodo principal y, a continuación, comparará igual a `end()`. Pero no se puede desreferenciar el iterador devuelto por `end()`.  
  
 Tenga en cuenta que no puede hacer referencia a un elemento de mapa directamente dado su posición numérica, requiere un iterador de acceso aleatorio.  
  
 Un iterador de mapa almacena un identificador a su nodo de asignación asociada, que a su vez almacena un identificador a su contenedor asociado. Sólo puede usar iteradores con sus objetos de contenedor asociado. Un iterador de mapa es válido siempre y cuando su nodo de asignación asociada está asociado a algún mapa. Además, un iterador válido es dereferencable, se puede utilizar para tener acceso o modificar el valor del elemento designa--siempre y cuando no es igual a `end()`.  
  
 Borrar o quitar un elemento llama al destructor para definir el valor almacenado. Destruir el contenedor, borrará todos los elementos. Por lo tanto, un contenedor cuyo tipo de elemento es una clase ref garantiza que ningún elemento su duración mayor que el contenedor. Sin embargo, tenga en cuenta que un contenedor de identificadores no `not` destruir sus elementos.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/mapa >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [mapa](../dotnet/map-stl-clr.md)   
 [MULTISET (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [Set (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Referencia de la biblioteca STL/CLR](../dotnet/stl-clr-library-reference.md)