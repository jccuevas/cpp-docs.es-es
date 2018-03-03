---
title: hash_multimap (STL/CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::hash_multimap
dev_langs:
- C++
helpviewer_keywords:
- hash_multimap class [STL/CLR]
- <cliext/hash_map> header [STL/CLR]
- <hash_map> header [STL/CLR]
ms.assetid: cd78687b-8a05-48e0-9d22-8b8194ae3b0b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b6927b25d627874f5a3d649099a4ed5e099bc6cb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="hashmultimap-stlclr"></a>hash_multimap (STL/CLR)
La clase de plantilla describe un objeto que controla una secuencia de longitud variable de elementos que tiene acceso bidireccional. Utilice el contenedor de `hash_multimap` para administrar una secuencia de elementos como una tabla hash, cada entrada de la tabla almacenar un bidireccional vinculado lista de nodos y cada nodo de almacenar un elemento. Un elemento consta de una clave, para ordenar la secuencia y un valor asignado, que va a lo largo de la transferencia.  
  
 En la descripción siguiente, `GValue` es igual que:  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 donde:  
  
 `GKey`es el mismo que `Key` a menos que el segundo es un tipo de referencia, en cuyo caso es`Key^`  
  
 `GMapped`es el mismo que `Mapped` a menos que el segundo es un tipo de referencia, en cuyo caso es`Mapped^`  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename Key,  
    typename Mapped>  
    ref class hash_multimap  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::IHash<Gkey, GValue>  
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
|[hash_multimap::const_iterator (STL/CLR)](../dotnet/hash-multimap-const-iterator-stl-clr.md)|El tipo de un iterador constante para la secuencia controlada.|  
|[hash_multimap::const_reference (STL/CLR)](../dotnet/hash-multimap-const-reference-stl-clr.md)|El tipo de una referencia constante a un elemento.|  
|[hash_multimap::const_reverse_iterator (STL/CLR)](../dotnet/hash-multimap-const-reverse-iterator-stl-clr.md)|El tipo de un iterador invertido constante para la secuencia controlada.|  
|[hash_multimap::difference_type (STL/CLR)](../dotnet/hash-multimap-difference-type-stl-clr.md)|El tipo de una distancia (posiblemente con signo) entre dos elementos.|  
|[hash_multimap::generic_container (STL/CLR)](../dotnet/hash-multimap-generic-container-stl-clr.md)|El tipo de la interfaz genérica para el contenedor.|  
|[hash_multimap::generic_iterator (STL/CLR)](../dotnet/hash-multimap-generic-iterator-stl-clr.md)|El tipo de un iterador para la interfaz genérica para el contenedor.|  
|[hash_multimap::generic_reverse_iterator (STL/CLR)](../dotnet/hash-multimap-generic-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso para la interfaz genérica para el contenedor.|  
|[hash_multimap::generic_value (STL/CLR)](../dotnet/hash-multimap-generic-value-stl-clr.md)|El tipo de un elemento de la interfaz genérica para el contenedor.|  
|[hash_multimap::hasher (STL/CLR)](../dotnet/hash-multimap-hasher-stl-clr.md)|El delegado de hash para una clave.|  
|[hash_multimap::iterator (STL/CLR)](../dotnet/hash-multimap-iterator-stl-clr.md)|El tipo de un iterador para la secuencia controlada.|  
|[hash_multimap::key_compare (STL/CLR)](../dotnet/hash-multimap-key-compare-stl-clr.md)|El delegado para dos claves de ordenación.|  
|[hash_multimap::key_type (STL/CLR)](../dotnet/hash-multimap-key-type-stl-clr.md)|El tipo de una clave de ordenación.|  
|[hash_multimap::mapped_type (STL/CLR)](../dotnet/hash-multimap-mapped-type-stl-clr.md)|El tipo del valor asignado asociado a cada clave.|  
|[hash_multimap::reference (STL/CLR)](../dotnet/hash-multimap-reference-stl-clr.md)|El tipo de una referencia a un elemento.|  
|[hash_multimap::reverse_iterator (STL/CLR)](../dotnet/hash-multimap-reverse-iterator-stl-clr.md)|El tipo de un iterador invertido para la secuencia controlada.|  
|[hash_multimap::size_type (STL/CLR)](../dotnet/hash-multimap-size-type-stl-clr.md)|El tipo de una distancia (positivo) entre dos elementos.|  
|[hash_multimap::value_compare (STL/CLR)](../dotnet/hash-multimap-value-compare-stl-clr.md)|El delegado de ordenación para los dos valores de elemento.|  
|[hash_multimap::value_type (STL/CLR)](../dotnet/hash-multimap-value-type-stl-clr.md)|El tipo de un elemento.|  
  
|Función miembro|Descripción|  
|---------------------|-----------------|  
|[hash_multimap::begin (STL/CLR)](../dotnet/hash-multimap-begin-stl-clr.md)|Designa el principio de la secuencia controlada.|  
|[hash_multimap::bucket_count (STL/CLR)](../dotnet/hash-multimap-bucket-count-stl-clr.md)|Cuenta el número de depósitos.|  
|[hash_multimap::clear (STL/CLR)](../dotnet/hash-multimap-clear-stl-clr.md)|Quita todos los elementos.|  
|[hash_multimap::count (STL/CLR)](../dotnet/hash-multimap-count-stl-clr.md)|Recuentos de elementos que coinciden con una clave especificada.|  
|[hash_multimap::empty (STL/CLR)](../dotnet/hash-multimap-empty-stl-clr.md)|Comprueba si no hay ningún elemento presente.|  
|[hash_multimap::end (STL/CLR)](../dotnet/hash-multimap-end-stl-clr.md)|Designa el final de la secuencia controlada.|  
|[hash_multimap::equal_range (STL/CLR)](../dotnet/hash-multimap-equal-range-stl-clr.md)|Busca el intervalo que coincide con una clave especificada.|  
|[hash_multimap::erase (STL/CLR)](../dotnet/hash-multimap-erase-stl-clr.md)|Quita los elementos de las posiciones especificadas.|  
|[hash_multimap::find (STL/CLR)](../dotnet/hash-multimap-find-stl-clr.md)|Busca un elemento que coincide con una clave especificada.|  
|[hash_multimap::hash_delegate (STL/CLR)](../dotnet/hash-multimap-hash-delegate-stl-clr.md)|Copia al delegado de hash para una clave.|  
|[hash_multimap::hash_multimap (STL/CLR)](../dotnet/hash-multimap-hash-multimap-stl-clr.md)|Construye un objeto contenedor.|  
|[hash_multimap::insert (STL/CLR)](../dotnet/hash-multimap-insert-stl-clr.md)|Agrega elementos.|  
|[hash_multimap::key_comp (STL/CLR)](../dotnet/hash-multimap-key-comp-stl-clr.md)|Copia al delegado para dos claves de ordenación.|  
|[hash_multimap::load_factor (STL/CLR)](../dotnet/hash-multimap-load-factor-stl-clr.md)|Cuenta los elementos promedio por depósito.|  
|[hash_multimap::lower_bound (STL/CLR)](../dotnet/hash-multimap-lower-bound-stl-clr.md)|Busca el comienzo del intervalo que coincide con una clave especificada.|  
|[hash_multimap::make_value (STL/CLR)](../dotnet/hash-multimap-make-value-stl-clr.md)|Construye un objeto de valor.|  
|[hash_multimap::max_load_factor (STL/CLR)](../dotnet/hash-multimap-max-load-factor-stl-clr.md)|Obtiene o establece los elementos máximos por depósito.|  
|[hash_multimap::rbegin (STL/CLR)](../dotnet/hash-multimap-rbegin-stl-clr.md)|Designa el principio de la secuencia controlada inversa.|  
|[hash_multimap::rehash (STL/CLR)](../dotnet/hash-multimap-rehash-stl-clr.md)|Recompila la tabla hash.|  
|[hash_multimap::rend (STL/CLR)](../dotnet/hash-multimap-rend-stl-clr.md)|Designa el final de la secuencia controlada inversa.|  
|[hash_multimap::size (STL/CLR)](../dotnet/hash-multimap-size-stl-clr.md)|Cuenta el número de elementos.|  
|[hash_multimap::swap (STL/CLR)](../dotnet/hash-multimap-swap-stl-clr.md)|Intercambia el contenido de dos contenedores.|  
|[hash_multimap::to_array (STL/CLR)](../dotnet/hash-multimap-to-array-stl-clr.md)|Copia la secuencia controlada en una nueva matriz.|  
|[hash_multimap::upper_bound (STL/CLR)](../dotnet/hash-multimap-upper-bound-stl-clr.md)|Busca el final del intervalo que coincide con una clave especificada.|  
|[hash_multimap::value_comp (STL/CLR)](../dotnet/hash-multimap-value-comp-stl-clr.md)|Copia al delegado de ordenación para los dos valores de elemento.|  
  
|Operador|Descripción|  
|--------------|-----------------|  
|[hash_multimap::operator= (STL/CLR)](../dotnet/hash-multimap-operator-assign-stl-clr.md)|Reemplaza la secuencia controlada.|  
  
## <a name="interfaces"></a>Interfaces  
  
|Interfaz|Descripción|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplicar un objeto.|  
|<xref:System.Collections.IEnumerable>|Secuencia a través de los elementos.|  
|<xref:System.Collections.ICollection>|Mantener el grupo de elementos.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Secuencia a través de los elementos con tipo.|  
|<xref:System.Collections.Generic.ICollection%601>|Mantener el grupo de elementos con tipo.|  
|IHash\<clave, valor >|Mantener contenedor genérico.|  
  
## <a name="remarks"></a>Comentarios  
 El objeto asigna y libera almacenamiento para la secuencia que controla como nodos individuales en una lista vinculada bidireccional. Para acelerar el acceso, el objeto también mantiene una matriz de longitud variable de punteros en la lista (la tabla hash), administrar de manera eficiente toda la lista como una secuencia de sublistas, o cubos. Inserta elementos en un depósito que mantiene ordenada por la modificación de los vínculos entre los nodos, nunca copiando el contenido de un nodo a otro. Esto significa que puede insertar y quitar elementos libremente sin alterar los elementos restantes.  
  
 El objeto ordena cada cubo controla mediante una llamada a un objeto de delegado almacenado de tipo [hash_set:: key_compare (STL/CLR)](../dotnet/hash-set-key-compare-stl-clr.md). Puede especificar el objeto de delegado almacenado cuando se construye el objeto hash_set; Si no se especifica ningún objeto de delegado, el valor predeterminado es la comparación `operator<=(key_type, key_type)`.  
  
 Se accede al objeto de delegado almacenado mediante una llamada a la función miembro [hash_set:: key_comp (STL/CLR)](../dotnet/hash-set-key-comp-stl-clr.md)`()`. Este tipo de objeto de delegado debe definir una ordenación equivalente entre las claves de tipo [hash_set:: KEY_TYPE (STL/CLR)](../dotnet/hash-set-key-type-stl-clr.md). Es decir, para las dos claves `X` y `Y`:  
  
 `key_comp()(X, Y)`Devuelve el valor booleano mismo resultado en cada llamada.  
  
 Si `key_comp()(X, Y) && key_comp()(Y, X)` es true, a continuación, `X` y `Y` se dice que tienen una ordenación equivalente.  
  
 Cualquier regla de ordenación que se comporta como `operator<=(key_type, key_type)`, `operator>=(key_type, key_type)` o `operator==(key_type, key_type)` define eqivalent orden.  
  
 Tenga en cuenta que el contenedor solo garantiza que los elementos cuyas claves tienen una ordenación equivalente (y qué hash en el mismo valor de entero) son adyacentes dentro de un depósito. A diferencia de la clase de plantilla [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md), un objeto de clase de plantilla `hash_multimap` no requiere que las claves para todos los elementos sean únicas. (Dos o más teclas pueden tener una ordenación equivalente).  
  
 El objeto determina qué cubo debe contener una clave de ordenación determinada mediante una llamada a un objeto de delegado almacenado de tipo [hash_set::hasher (STL/CLR)](../dotnet/hash-set-hasher-stl-clr.md). Tener acceso a este objeto almacenado llamando a la función miembro [hash_set::hash_delegate (STL/CLR)](../dotnet/hash-set-hash-delegate-stl-clr.md) `()` para obtener un valor entero que depende del valor de clave. Puede especificar el objeto de delegado almacenado cuando se construye el objeto hash_set; Si no se especifica ningún objeto de delegado, el valor predeterminado es la función `System::Object::hash_value(key_type)`. Es decir, para las claves `X` y `Y`:  
  
 `hash_delegate()(X)`Devuelve el mismo resultado entero en cada llamada.  
  
 Si `X` y `Y` tienen una ordenación equivalente, a continuación, `hash_delegate()(X)` debe devolver el mismo resultado entero que `hash_delegate()(Y)`.  
  
 Cada elemento contiene una clave independiente y un valor asignado. La secuencia se representa de forma que permite la búsqueda, inserción y eliminación de un elemento arbitrario con una serie de operaciones que es independiente del número de elementos de la secuencia (tiempo constante), al menos en lo mejor de los casos. Además, la inserción de un elemento no invalida ningún iterador y al quitar un elemento solo se invalidan los iteradores que apuntan al elemento quitado.  
  
 Si los valores hash no se distribuyen uniformemente, sin embargo, puede degeneradas una tabla hash. En el extremo: para una función hash que siempre devuelve el mismo valor--búsqueda, inserción y eliminación son proporcionales al número de elementos de la secuencia (tiempo lineal). El contenedor intenta elegir una función hash razonable, el tamaño de depósito promedio y tamaño de la tabla hash (número total de sectores de almacenamiento), pero puede invalidar cualquiera o la totalidad de estas opciones. Ver, por ejemplo, las funciones [hash_set::max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md) y [hash_set::rehash (STL/CLR)](../dotnet/hash-set-rehash-stl-clr.md).  
  
 Un hash_multimap es compatible con los iteradores bidireccionales, lo que significa que puede ejecutar paso a paso para los elementos adyacentes que proporciona un iterador que designa un elemento de la secuencia controlada. Un nodo principal especial que se corresponde con el iterador devuelto por [hash_multimap:: end (STL/CLR)](../dotnet/hash-multimap-end-stl-clr.md)`()`. Puede reducir este iterador para llegar al último elemento de la secuencia controlada, si está presente. Puede incrementar un iterador de hash_multimap hasta alcanzar el nodo principal y, a continuación, comparará igual a `end()`. Pero no se puede desreferenciar el iterador devuelto por `end()`.  
  
 Tenga en cuenta que no puede hacer referencia a un elemento de hash_multimap directamente dado su posición numérica, requiere un iterador de acceso aleatorio.  
  
 Un iterador de hash_multimap almacena un identificador a su nodo hash_multimap asociado, que a su vez almacena un identificador a su contenedor asociado. Sólo puede usar iteradores con sus objetos de contenedor asociado. Un iterador de hash_multimap es válido siempre y cuando su nodo hash_multimap asociado está asociado a algún hash_multimap. Además, un iterador válido es dereferencable, se puede utilizar para tener acceso o modificar el valor del elemento designa--siempre y cuando no es igual a `end()`.  
  
 Borrar o quitar un elemento llama al destructor para definir el valor almacenado. Destruir el contenedor, borrará todos los elementos. Por lo tanto, un contenedor cuyo tipo de elemento es una clase ref garantiza que ningún elemento su duración mayor que el contenedor. Sin embargo, tenga en cuenta que un contenedor de identificadores no `not` destruir sus elementos.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/hash_map >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [asignar (STL/CLR)](../dotnet/map-stl-clr.md)   
 [multimap (STL/CLR)](../dotnet/multimap-stl-clr.md)   
 [MULTISET (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [Set (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Referencia de la biblioteca STL/CLR](../dotnet/stl-clr-library-reference.md)