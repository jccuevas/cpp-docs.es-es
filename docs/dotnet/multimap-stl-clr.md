---
title: multimap (STL/CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::multimap
dev_langs: C++
helpviewer_keywords:
- <map> header [STL/CLR]
- <cliext/map> header [STL/CLR]
- multimap class [STL/CLR]
ms.assetid: 3dfe329d-a078-462a-b050-7999ce6110ad
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b944be379b851410a7c45af5aa05e72dbf63037c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="multimap-stlclr"></a>multimap (STL/CLR)
La clase de plantilla describe un objeto que controla una secuencia de longitud variable de elementos que tiene acceso bidireccional. Utilice el contenedor de `multimap` para administrar una secuencia de elementos como un árbol equilibrado (casi) ordenada de nodos, cada uno de ellos almacenar un elemento. Un elemento consta de una clave, para ordenar la secuencia y un valor asignado, que va a lo largo de la transferencia.  
  
 En la descripción siguiente, `GValue` es igual que:  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 donde:  
  
 `GKey`es el mismo que `Key` a menos que el segundo es un tipo de referencia, en cuyo caso es`Key^`  
  
 `GMapped`es el mismo que `Mapped` a menos que el segundo es un tipo de referencia, en cuyo caso es`Mapped^`  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename Key,  
    typename Mapped>  
    ref class multimap  
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
  
 asignado  
 El tipo del componente adicional de un elemento de la secuencia controlada.  
  
## <a name="members"></a>Miembros  
  
|Definición de tipo|Descripción|  
|---------------------|-----------------|  
|[multimap::const_iterator (STL/CLR)](../dotnet/multimap-const-iterator-stl-clr.md)|El tipo de un iterador constante para la secuencia controlada.|  
|[multimap::const_reference (STL/CLR)](../dotnet/multimap-const-reference-stl-clr.md)|El tipo de una referencia constante a un elemento.|  
|[multimap::const_reverse_iterator (STL/CLR)](../dotnet/multimap-const-reverse-iterator-stl-clr.md)|El tipo de un iterador invertido constante para la secuencia controlada.|  
|[multimap::difference_type (STL/CLR)](../dotnet/multimap-difference-type-stl-clr.md)|El tipo de una distancia (posiblemente con signo) entre dos elementos.|  
|[multimap::generic_container (STL/CLR)](../dotnet/multimap-generic-container-stl-clr.md)|El tipo de la interfaz genérica para el contenedor.|  
|[multimap::generic_iterator (STL/CLR)](../dotnet/multimap-generic-iterator-stl-clr.md)|El tipo de un iterador para la interfaz genérica para el contenedor.|  
|[multimap::generic_reverse_iterator (STL/CLR)](../dotnet/multimap-generic-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso para la interfaz genérica para el contenedor.|  
|[multimap::generic_value (STL/CLR)](../dotnet/multimap-generic-value-stl-clr.md)|El tipo de un elemento de la interfaz genérica para el contenedor.|  
|[multimap::iterator (STL/CLR)](../dotnet/multimap-iterator-stl-clr.md)|El tipo de un iterador para la secuencia controlada.|  
|[multimap::key_compare (STL/CLR)](../dotnet/multimap-key-compare-stl-clr.md)|El delegado para dos claves de ordenación.|  
|[multimap::key_type (STL/CLR)](../dotnet/multimap-key-type-stl-clr.md)|El tipo de una clave de ordenación.|  
|[multimap::mapped_type (STL/CLR)](../dotnet/multimap-mapped-type-stl-clr.md)|El tipo del valor asignado asociado a cada clave.|  
|[multimap::reference (STL/CLR)](../dotnet/multimap-reference-stl-clr.md)|El tipo de una referencia a un elemento.|  
|[multimap::reverse_iterator (STL/CLR)](../dotnet/multimap-reverse-iterator-stl-clr.md)|El tipo de un iterador invertido para la secuencia controlada.|  
|[multimap::size_type (STL/CLR)](../dotnet/multimap-size-type-stl-clr.md)|El tipo de una distancia (positivo) entre dos elementos.|  
|[multimap::value_compare (STL/CLR)](../dotnet/multimap-value-compare-stl-clr.md)|El delegado de ordenación para los dos valores de elemento.|  
|[multimap::value_type (STL/CLR)](../dotnet/multimap-value-type-stl-clr.md)|El tipo de un elemento.|  
  
|Función miembro|Descripción|  
|---------------------|-----------------|  
|[multimap::begin (STL/CLR)](../dotnet/multimap-begin-stl-clr.md)|Designa el principio de la secuencia controlada.|  
|[multimap::clear (STL/CLR)](../dotnet/multimap-clear-stl-clr.md)|Quita todos los elementos.|  
|[multimap::count (STL/CLR)](../dotnet/multimap-count-stl-clr.md)|Recuentos de elementos que coinciden con una clave especificada.|  
|[multimap::empty (STL/CLR)](../dotnet/multimap-empty-stl-clr.md)|Comprueba si no hay ningún elemento presente.|  
|[multimap::end (STL/CLR)](../dotnet/multimap-end-stl-clr.md)|Designa el final de la secuencia controlada.|  
|[multimap::equal_range (STL/CLR)](../dotnet/multimap-equal-range-stl-clr.md)|Busca el intervalo que coincide con una clave especificada.|  
|[multimap::erase (STL/CLR)](../dotnet/multimap-erase-stl-clr.md)|Quita los elementos de las posiciones especificadas.|  
|[multimap::find (STL/CLR)](../dotnet/multimap-find-stl-clr.md)|Busca un elemento que coincide con una clave especificada.|  
|[multimap::insert (STL/CLR)](../dotnet/multimap-insert-stl-clr.md)|Agrega elementos.|  
|[multimap::key_comp (STL/CLR)](../dotnet/multimap-key-comp-stl-clr.md)|Copia al delegado para dos claves de ordenación.|  
|[multimap::lower_bound (STL/CLR)](../dotnet/multimap-lower-bound-stl-clr.md)|Busca el comienzo del intervalo que coincide con una clave especificada.|  
|[multimap::make_value (STL/CLR)](../dotnet/multimap-make-value-stl-clr.md)|Construye un objeto de valor.|  
|[multimap::multimap (STL/CLR)](../dotnet/multimap-multimap-stl-clr.md)|Construye un objeto contenedor.|  
|[multimap::rbegin (STL/CLR)](../dotnet/multimap-rbegin-stl-clr.md)|Designa el principio de la secuencia controlada inversa.|  
|[multimap::rend (STL/CLR)](../dotnet/multimap-rend-stl-clr.md)|Designa el final de la secuencia controlada inversa.|  
|[multimap::size (STL/CLR)](../dotnet/multimap-size-stl-clr.md)|Cuenta el número de elementos.|  
|[multimap::swap (STL/CLR)](../dotnet/multimap-swap-stl-clr.md)|Intercambia el contenido de dos contenedores.|  
|[multimap::to_array (STL/CLR)](../dotnet/multimap-to-array-stl-clr.md)|Copia la secuencia controlada en una nueva matriz.|  
|[multimap::upper_bound (STL/CLR)](../dotnet/multimap-upper-bound-stl-clr.md)|Busca el final del intervalo que coincide con una clave especificada.|  
|[multimap::value_comp (STL/CLR)](../dotnet/multimap-value-comp-stl-clr.md)|Copia al delegado de ordenación para los dos valores de elemento.|  
  
|Operador|Descripción|  
|--------------|-----------------|  
|[multimap::operator= (STL/CLR)](../dotnet/multimap-operator-assign-stl-clr.md)|Reemplaza la secuencia controlada.|  
|[operator!= (multimap) (STL/CLR)](../dotnet/operator-inequality-multimap-stl-clr.md)|Determina si un `multimap` no es igual a otro objeto `multimap` objeto.|  
|[operator< (multimap) (STL/CLR)](../dotnet/operator-less-than-multimap-stl-clr.md)|Determina si un `multimap` objeto es menor que otro `multimap` objeto.|  
|[operator<= (multimap) (STL/CLR)](../dotnet/operator-less-or-equal-multimap-stl-clr.md)|Determina si un `multimap` objeto es menor o igual que otro `multimap` objeto.|  
|[operator== (multimap) (STL/CLR)](../dotnet/operator-equality-multimap-stl-clr.md)|Determina si un `multimap` es igual a otro objeto `multimap` objeto.|  
|[operator> (multimap) (STL/CLR)](../dotnet/operator-greater-than-multimap-stl-clr.md)|Determina si un `multimap` es mayor que otro objeto `multimap` objeto.|  
|[operator>= (multimap) (STL/CLR)](../dotnet/operator-greater-or-equal-multimap-stl-clr.md)|Determina si un `multimap` objeto es mayor o igual que otro `multimap` objeto.|  
  
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
  
 El objeto ordena la secuencia controla mediante una llamada a un objeto de delegado almacenado de tipo [multimap:: key_compare (STL/CLR)](../dotnet/multimap-key-compare-stl-clr.md). Puede especificar el objeto de delegado almacenado cuando se crea la asignación múltiple; Si no se especifica ningún objeto de delegado, el valor predeterminado es la comparación `operator<(key_type, key_type)`. Tener acceso a este objeto almacenado llamando a la función miembro [multimap:: key_comp (STL/CLR)](../dotnet/multimap-key-comp-stl-clr.md)`()`.  
  
 Este tipo de objeto de delegado debe imponer una ordenación débil estricta en claves de tipo [multimap:: KEY_TYPE (STL/CLR)](../dotnet/multimap-key-type-stl-clr.md). Es decir, para las dos claves `X` y `Y`:  
  
 `key_comp()(X, Y)`Devuelve el valor booleano mismo resultado en cada llamada.  
  
 Si `key_comp()(X, Y)` es true, a continuación, `key_comp()(Y, X)` debe ser false.  
  
 Si `key_comp()(X, Y)` es true, a continuación, `X` se dice que se ordenan antes que `Y`.  
  
 Si `!key_comp()(X, Y) && !key_comp()(Y, X)` es true, a continuación, `X` y `Y` se dice que tienen una ordenación equivalente.  
  
 Para cualquier elemento `X` que precede a `Y` en la secuencia controlada, `key_comp()(Y, X)` es false. (Para el objeto de delegado de forma predeterminada, las claves nunca disminuyen en valor.) A diferencia de la clase de plantilla [mapa (STL/CLR)](../dotnet/map-stl-clr.md), un objeto de clase de plantilla `multimap` no requiere que las claves para todos los elementos sean únicas. (Dos o más teclas pueden tener una ordenación equivalente).  
  
 Cada elemento contiene una clave independiente y un valor asignado. La secuencia se representa de forma que permite la búsqueda, inserción y eliminación de un elemento arbitrario con una serie de operaciones proporcionales al logaritmo del número de elementos en la secuencia (tiempo logarítmico). Además, la inserción de un elemento no invalida ningún iterador y al quitar un elemento solo se invalidan los iteradores que apuntan al elemento quitado.  
  
 Una asignación múltiple es compatible con los iteradores bidireccionales, lo que significa que puede ejecutar paso a paso para los elementos adyacentes que proporciona un iterador que designa un elemento de la secuencia controlada. Un nodo principal especial que se corresponde con el iterador devuelto por [multimap:: end (STL/CLR)](../dotnet/multimap-end-stl-clr.md)`()`. Puede reducir este iterador para llegar al último elemento de la secuencia controlada, si está presente. Puede incrementar un iterador multimap hasta alcanzar el nodo principal y, a continuación, comparará igual a `end()`. Pero no se puede desreferenciar el iterador devuelto por `end()`.  
  
 Tenga en cuenta que no puede hacer referencia a un elemento de asignación múltiple directamente dado su posición numérica, requiere un iterador de acceso aleatorio.  
  
 Un iterador multimap almacena un identificador a su nodo multimap asociado, que a su vez almacena un identificador de su contenedor asociado. Sólo puede usar iteradores con sus objetos de contenedor asociado. Un iterador multimap es válido siempre y cuando su nodo multimap asociado está asociado a algún multimap. Además, un iterador válido es dereferencable, se puede utilizar para tener acceso o modificar el valor del elemento designa--siempre y cuando no es igual a `end()`.  
  
 Borrar o quitar un elemento llama al destructor para definir el valor almacenado. Destruir el contenedor, borrará todos los elementos. Por lo tanto, un contenedor cuyo tipo de elemento es una clase ref garantiza que ningún elemento su duración mayor que el contenedor. Sin embargo, tenga en cuenta que un contenedor de identificadores no `not` destruir sus elementos.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/mapa >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)   
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [asignar (STL/CLR)](../dotnet/map-stl-clr.md)   
 [MULTISET (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [Set (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Referencia de la biblioteca STL/CLR](../dotnet/stl-clr-library-reference.md)