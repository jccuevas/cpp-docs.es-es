---
title: asignación (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::map
- cliext::map::begin
- cliext::map::clear
- cliext::map::const_iterator
- cliext::map::const_reference
- cliext::map::const_reverse_iterator
- cliext::map::count
- cliext::map::difference_type
- cliext::map::empty
- cliext::map::end
- cliext::map::equal_range
- cliext::map::erase
- cliext::map::find
- cliext::map::generic_container
- cliext::map::generic_iterator
- cliext::map::generic_reverse_iterator
- cliext::map::generic_value
- cliext::map::insert
- cliext::map::iterator
- cliext::map::key_comp
- cliext::map::key_compare
- cliext::map::key_type
- cliext::map::lower_bound
- cliext::map::make_value
- cliext::map::map
- cliext::map::mapped_type
- cliext::map::operator=
- cliext::map::operator
- cliext::map::rbegin
- cliext::map::reference
- cliext::map::rend
- cliext::map::reverse_iterator
- cliext::map::size
- cliext::map::size_type
- cliext::map::swap
- cliext::map::to_array
- cliext::map::upper_bound
- cliext::map::value_comp
- cliext::map::value_compare
- cliext::map::value_type
- cliext::operator!= (map)
- cliext::operator< (map)
- cliext::operator<= (map)
- cliext::operator== (map)
- cliext::operator> (map)
- cliext::operator>= (map)
dev_langs:
- C++
helpviewer_keywords:
- <map> header [STL/CLR]
- map class [STL/CLR]
- <cliext/map> header [STL/CLR]
- begin member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- count member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- equal_range member [STL/CLR]
- erase member [STL/CLR]
- find member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- key_comp member [STL/CLR]
- key_compare member [STL/CLR]
- key_type member [STL/CLR]
- lower_bound member [STL/CLR]
- make_value member [STL/CLR]
- map member [STL/CLR]
- mapped_type member [STL/CLR]
- operator= member [STL/CLR]
- operator member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- upper_bound member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
- operator!= (map) member [STL/CLR]
- operator< (map) member [STL/CLR]
- operator<= (map) member [STL/CLR]
- operator== (map) member [STL/CLR]
- operator> (map) member [STL/CLR]
- operator>= (map) member [STL/CLR]
ms.assetid: 8b0a7764-b5e4-4175-a802-82b72eb8662a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 51570171fbd8de9919bcba5dabb47c26d8e1c748
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079908"
---
# <a name="map-stlclr"></a>map (STL/CLR)
La clase de plantilla describe un objeto que controla una secuencia de longitud variable de elementos que tiene acceso bidireccional. Utilice el contenedor de `map` para administrar una secuencia de elementos como un árbol equilibrado (casi) ordenada de nodos, cada uno de ellos almacenar un elemento. Un elemento consta de una clave, para ordenar la secuencia y un valor asignado, que va a lo largo de la transferencia.  
  
 En la descripción siguiente, `GValue` es igual que:  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 donde:  
  
 `GKey` es el mismo que `Key` a menos que el segundo es un tipo de referencia, en cuyo caso es `Key^`  
  
 `GMapped` es el mismo que `Mapped` a menos que el segundo es un tipo de referencia, en cuyo caso es `Mapped^`  
  
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
  
### <a name="parameters"></a>Parámetros  
 Key  
 El tipo del componente clave de un elemento de la secuencia controlada.  
  
 Asignado  
 El tipo del componente adicional de un elemento de la secuencia controlada.  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/mapa >  
  
 **Namespace:** cliext  
  
## <a name="declarations"></a>Declaraciones
  
|Definición de tipo|Descripción|  
|---------------------|-----------------|  
|[map::const_iterator (STL/CLR)](#const_iterator)|El tipo de un iterador constante para la secuencia controlada.|  
|[map::const_reference (STL/CLR)](#const_reference)|El tipo de una referencia constante a un elemento.|  
|[map::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|El tipo de un iterador invertido constante para la secuencia controlada.|  
|[map::difference_type (STL/CLR)](#difference_type)|El tipo de una distancia (posiblemente con signo) entre dos elementos.|  
|[map::generic_container (STL/CLR)](#generic_container)|El tipo de la interfaz genérica para el contenedor.|  
|[map::generic_iterator (STL/CLR)](#generic_iterator)|El tipo de un iterador para la interfaz genérica para el contenedor.|  
|[map::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|El tipo de un iterador inverso para la interfaz genérica para el contenedor.|  
|[map::generic_value (STL/CLR)](#generic_value)|El tipo de un elemento de la interfaz genérica para el contenedor.|  
|[map::iterator (STL/CLR)](#iterator)|El tipo de un iterador para la secuencia controlada.|  
|[map::key_compare (STL/CLR)](#key_compare)|El delegado para dos claves de ordenación.|  
|[map::key_type (STL/CLR)](#key_type)|El tipo de una clave de ordenación.|  
|[map::mapped_type (STL/CLR)](#mapped_type)|El tipo del valor asignado asociado a cada clave.|  
|[map::reference (STL/CLR)](#reference)|El tipo de una referencia a un elemento.|  
|[map::reverse_iterator (STL/CLR)](#reverse_iterator)|El tipo de un iterador invertido para la secuencia controlada.|  
|[map::size_type (STL/CLR)](#size_type)|El tipo de una distancia (positivo) entre dos elementos.|  
|[map::value_compare (STL/CLR)](#value_compare)|El delegado de ordenación para los dos valores de elemento.|  
|[map::value_type (STL/CLR)](#value_type)|El tipo de un elemento.|  
  
|Función miembro|Descripción|  
|---------------------|-----------------|  
|[map::begin (STL/CLR)](#begin)|Designa el principio de la secuencia controlada.|  
|[map::clear (STL/CLR)](#clear)|Quita todos los elementos.|  
|[map::count (STL/CLR)](#count)|Recuentos de elementos que coinciden con una clave especificada.|  
|[map::empty (STL/CLR)](#empty)|Comprueba si no hay ningún elemento presente.|  
|[map::end (STL/CLR)](#end)|Designa el final de la secuencia controlada.|  
|[map::equal_range (STL/CLR)](#equal_range)|Busca el intervalo que coincide con una clave especificada.|  
|[map::erase (STL/CLR)](#erase)|Quita los elementos de las posiciones especificadas.|  
|[map::find (STL/CLR)](#find)|Busca un elemento que coincide con una clave especificada.|  
|[map::insert (STL/CLR)](#insert)|Agrega elementos.|  
|[map::key_comp (STL/CLR)](#key_comp)|Copia al delegado para dos claves de ordenación.|  
|[map::lower_bound (STL/CLR)](#lower_bound)|Busca el comienzo del intervalo que coincide con una clave especificada.|  
|[map::make_value (STL/CLR)](#make_value)|Construye un objeto de valor.|  
|[map::map (STL/CLR)](#map)|Construye un objeto contenedor.|  
|[map::rbegin (STL/CLR)](#rbegin)|Designa el principio de la secuencia controlada inversa.|  
|[map::rend (STL/CLR)](#rend)|Designa el final de la secuencia controlada inversa.|  
|[map::size (STL/CLR)](#size)|Cuenta el número de elementos.|  
|[map::swap (STL/CLR)](#swap)|Intercambia el contenido de dos contenedores.|  
|[map::to_array (STL/CLR)](#to_array)|Copia la secuencia controlada en una nueva matriz.|  
|[map::upper_bound (STL/CLR)](#upper_bound)|Busca el final del intervalo que coincide con una clave especificada.|  
|[map::value_comp (STL/CLR)](#value_comp)|Copia al delegado de ordenación para los dos valores de elemento.|  
  
|Operador|Descripción|  
|--------------|-----------------|  
|[map::operator= (STL/CLR)](#op_as)|Reemplaza la secuencia controlada.|  
|[map::operator(STL/CLR)](#op)|Asigna una clave a su valor asignado asociado.|  
|[operator!= (map) (STL/CLR)](#op_neq)|Determina si un `map` no es igual a otro objeto `map` objeto.|  
|[operator< (map) (STL/CLR)](#op_lt)|Determina si un `map` objeto es menor que otro `map` objeto.|  
|[operator<= (map) (STL/CLR)](#op_lteq)|Determina si un `map` objeto es menor o igual que otro `map` objeto.|  
|[operator== (map) (STL/CLR)](#op_eq)|Determina si un `map` es igual a otro objeto `map` objeto.|  
|[operator> (map) (STL/CLR)](#op_gt)|Determina si un `map` es mayor que otro objeto `map` objeto.|  
|[operator>= (map) (STL/CLR)](#op_gteq)|Determina si un `map` objeto es mayor o igual que otro `map` objeto.|  
  
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
  
 `key_comp()(X, Y)` Devuelve el valor booleano mismo resultado en cada llamada.  
  
 Si `key_comp()(X, Y)` es true, a continuación, `key_comp()(Y, X)` debe ser false.  
  
 Si `key_comp()(X, Y)` es true, a continuación, `X` se dice que se ordenan antes que `Y`.  
  
 Si `!key_comp()(X, Y) && !key_comp()(Y, X)` es true, a continuación, `X` y `Y` se dice que tienen una ordenación equivalente.  
  
 Para cualquier elemento `X` que precede a `Y` en la secuencia controlada, `key_comp()(Y, X)` es false. (Para el objeto de delegado de forma predeterminada, las claves nunca disminuyen en valor.) A diferencia de la clase de plantilla [mapa](../dotnet/map-stl-clr.md), un objeto de clase de plantilla `map` no requiere que las claves para todos los elementos sean únicas. (Dos o más teclas pueden tener una ordenación equivalente).  
  
 Cada elemento contiene una clave independiente y un valor asignado. La secuencia se representa de forma que permite la búsqueda, inserción y eliminación de un elemento arbitrario con una serie de operaciones proporcionales al logaritmo del número de elementos en la secuencia (tiempo logarítmico). Además, la inserción de un elemento no invalida ningún iterador y al quitar un elemento solo se invalidan los iteradores que apuntan al elemento quitado.  
  
 Una asignación es compatible con los iteradores bidireccionales, lo que significa que puede ejecutar paso a paso para los elementos adyacentes que proporciona un iterador que designa un elemento de la secuencia controlada. Un nodo principal especial que se corresponde con el iterador devuelto por [Map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`. Puede reducir este iterador para llegar al último elemento de la secuencia controlada, si está presente. Puede incrementar un iterador de mapa para alcanzar el nodo principal y, a continuación, comparará igual a `end()`. Pero no se puede desreferenciar el iterador devuelto por `end()`.  
  
 Tenga en cuenta que no puede hacer referencia a un elemento de mapa directamente dado su posición numérica, requiere un iterador de acceso aleatorio.  
  
 Un iterador de mapa almacena un identificador a su nodo de asignación asociada, que a su vez almacena un identificador a su contenedor asociado. Sólo puede usar iteradores con sus objetos de contenedor asociado. Un iterador de mapa es válido siempre y cuando su nodo de asignación asociada está asociado a algún mapa. Además, un iterador válido es dereferencable, se puede utilizar para tener acceso o modificar el valor del elemento designa--siempre y cuando no es igual a `end()`.  
  
 Borrar o quitar un elemento llama al destructor para definir el valor almacenado. Destruir el contenedor, borrará todos los elementos. Por lo tanto, un contenedor cuyo tipo de elemento es una clase ref garantiza que ningún elemento su duración mayor que el contenedor. Sin embargo, tenga en cuenta que un contenedor de identificadores no `not` destruir sus elementos.  
  
## <a name="members"></a>Miembros

## <a name="begin"></a> Map:: begin (STL/CLR)
Designa el principio de la secuencia controlada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
iterator begin();  
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve un iterador bidireccional que designa el primer elemento de la secuencia controlada o más allá del final de una secuencia vacía. Utilícelo para obtener un iterador que designa el `current` a partir de la secuencia controlada, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_begin.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Mymap::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = [{0} {1}]",   
        it->first, it->second);   
    ++it;   
    System::Console::WriteLine("*++begin() = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
*begin() = [a 1]  
*++begin() = [b 2]  
```  

## <a name="clear"></a> Map:: Clear (STL/CLR)
Quita todos los elementos.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void clear();  
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro llama eficazmente a [Map:: Erase (STL/CLR)](../dotnet/map-erase-stl-clr.md) `(` [Map:: begin (STL/CLR)](../dotnet/map-begin-stl-clr.md) `(),` [Map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md) `())`. Utilizarlo para asegurarse de que la secuencia controlada está vacía.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_clear.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
  
// display contents " [a 1] [b 2]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
size() = 0  
 [a 1] [b 2]  
size() = 0  
```  

## <a name="const_iterator"></a> Map:: const_iterator (STL/CLR)
El tipo de un iterador constante para la secuencia controlada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef T2 const_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un objeto de tipo no especificado `T2` que puede actuar como un iterador constante bidireccional para la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_const_iterator.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    Mymap::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" [{0} {1}]", cit->first, cit->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  

## <a name="const_reference"></a> Map:: const_reference (STL/CLR)
El tipo de una referencia constante a un elemento.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef value_type% const_reference;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una referencia constante a un elemento.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_const_reference.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    Mymap::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        {   // get a const reference to an element   
        Mymap::const_reference cref = *cit;   
        System::Console::Write(" [{0} {1}]", cref->first, cref->second);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  

## <a name="const_reverse_iterator"></a> Map:: const_reverse_iterator (STL/CLR)
El tipo de un iterador inverso constante para la secuencia controlada...  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef T4 const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un objeto de tipo no especificado `T4` que puede actuar como un iterador inverso constante para la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" reversed   
    Mymap::const_reverse_iterator crit = c1.rbegin();   
    for (; crit != c1.rend(); ++crit)   
        System::Console::Write(" [{0} {1}]", crit->first, crit->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[c 3] [b 2] [a 1]  
```  

## <a name="count"></a> Map:: Count (STL/CLR)
Busca el número de elementos que coinciden con una clave especificada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
size_type count(key_type key);  
```  
  
#### <a name="parameters"></a>Parámetros  
 key  
 Valor de clave que se va a buscar.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve el número de elementos de la secuencia controlada que tienen una ordenación equivalente con `key`. Usa para determinar el número de elementos actualmente en la secuencia controlada que coinciden con una clave especificada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_count.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));   
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));   
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
count(L'A') = 0  
count(L'b') = 1  
count(L'C') = 0  
```  

## <a name="difference_type"></a> Map:: difference_type (STL/CLR)
Los tipos de una distancia con signo entre dos elementos.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un recuento de elemento posiblemente negativo.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_difference_type.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Mymap::difference_type diff = 0;   
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
  
// compute negative difference   
    diff = 0;   
    for (Mymap::iterator it = c1.end(); it != c1.begin(); --it)   
        --diff;   
    System::Console::WriteLine("begin()-end() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
end()-begin() = 3  
begin()-end() = -3  
```  

## <a name="empty"></a> Map:: Empty (STL/CLR)
Comprueba si no hay ningún elemento presente.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
bool empty();  
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve true para una secuencia controlada vacía. Es equivalente a [Map:: Size (STL/CLR)](../dotnet/map-size-stl-clr.md)`() == 0`. Se usa para comprobar si el mapa está vacío.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_empty.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
size() = 3  
empty() = False  
size() = 0  
empty() = True  
```  

## <a name="end"></a> Map:: end (STL/CLR)
Designa el final de la secuencia controlada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
iterator end();  
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve un iterador bidireccional que apunta justo después del final de la secuencia controlada. Utilícelo para obtener un iterador que designa el final de la secuencia controlada; su no de estado de cambio si cambia la longitud de la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_end.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect last two items   
    Mymap::iterator it = c1.end();   
    --it;   
    --it;   
    System::Console::WriteLine("*-- --end() = [{0} {1}]",   
        it->first, it->second);   
    ++it;   
    System::Console::WriteLine("*--end() = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  

## <a name="equal_range"></a> Map:: equal_range (STL/CLR)
Busca el intervalo que coincide con una clave especificada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
cliext::pair<iterator, iterator> equal_range(key_type key);  
```  
  
#### <a name="parameters"></a>Parámetros  
 key  
 Valor de clave que se va a buscar.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve un par de iteradores `cliext::pair<iterator, iterator>(` [Map:: lower_bound (STL/CLR)](../dotnet/map-lower-bound-stl-clr.md) `(key),` [Map:: upper_bound (STL/CLR)](../dotnet/map-upper-bound-stl-clr.md)`(key))`. Usa para determinar el intervalo de elementos actualmente en la secuencia controlada que coinciden con una clave especificada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_equal_range.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
typedef Mymap::pair_iter_iter Pairii;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// display results of failed search   
    Pairii pair1 = c1.equal_range(L'x');   
    System::Console::WriteLine("equal_range(L'x') empty = {0}",   
        pair1.first == pair1.second);   
  
// display results of successful search   
    pair1 = c1.equal_range(L'b');   
    for (; pair1.first != pair1.second; ++pair1.first)   
        System::Console::Write(" [{0} {1}]",   
            pair1.first->first, pair1.first->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
equal_range(L'x') empty = True  
 [b 2]  
```  
  
## <a name="erase"></a> Map:: Erase (STL/CLR)
Quita los elementos de las posiciones especificadas.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
bool erase(key_type key)  
```  
  
#### <a name="parameters"></a>Parámetros  
 first  
 Comienzo del intervalo que se va a borrar.  
  
 key  
 Valor de clave para borrar.  
  
 last  
 Final del intervalo que se va a borrar.  
  
 donde  
 Elemento que se va a borrar.  
  
### <a name="remarks"></a>Comentarios  
 La primera función miembro quita el elemento de la secuencia controlada señalada por `where`y devuelve un iterador que designa el primer elemento que permanece más allá del elemento eliminado, o [Map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md) `()` si no existe ese elemento. Usa para quitar un único elemento.  
  
 La segunda función miembro quita los elementos de la secuencia controlada en el intervalo [`first`, `last`) y devuelve un iterador que designa el primer elemento que permanece más allá de los elementos quitados, o `end()` si ningún elemento existe... Usa para quitar cero o más elementos contiguos.  
  
 La tercera función miembro quita cualquier elemento de la secuencia controlada cuyo criterio de ordenación es equivalente a `key`y devuelve un recuento del número de elementos quitados. Se usa para quitar y recuento de todos los elementos que coinciden con una clave especificada.  
  
 La eliminación de cada elemento lleva tiempo proporcional al logaritmo del número de elementos de la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_erase.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    cliext::map<wchar_t, int> c1;   
    c1.insert(cliext::map<wchar_t, int>::make_value(L'a', 1));   
    c1.insert(cliext::map<wchar_t, int>::make_value(L'b', 2));   
    c1.insert(cliext::map<wchar_t, int>::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (cliext::map<wchar_t, int>::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    cliext::map<wchar_t, int>::iterator it =   
        c1.erase(c1.begin());   
    System::Console::WriteLine("erase(begin()) = [{0} {1}]",   
        it->first, it->second);   
  
// add elements and display " b c d e"   
    c1.insert(cliext::map<wchar_t, int>::make_value(L'd', 4));   
    c1.insert(cliext::map<wchar_t, int>::make_value(L'e', 5));   
    for each (cliext::map<wchar_t, int>::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// erase all but end   
    it = c1.end();   
    it = c1.erase(c1.begin(), --it);   
    System::Console::WriteLine("erase(begin(), end()-1) = [{0} {1}]",   
        it->first, it->second);   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// erase end   
    System::Console::WriteLine("erase(L'x') = {0}", c1.erase(L'x'));   
    System::Console::WriteLine("erase(L'e') = {0}", c1.erase(L'e'));   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
erase(begin()) = [b 2]  
 [b 2] [c 3] [d 4] [e 5]  
erase(begin(), end()-1) = [e 5]  
size() = 1  
erase(L'x') = 0  
erase(L'e') = 1  
```  
  
## <a name="find"></a> Map:: Find (STL/CLR)
Busca un elemento que coincide con una clave especificada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
iterator find(key_type key);  
```  
  
#### <a name="parameters"></a>Parámetros  
 key  
 Valor de clave que se va a buscar.  
  
### <a name="remarks"></a>Comentarios  
 Si al menos un elemento de la secuencia controlada tiene una ordenación equivalente con `key`, la función miembro devuelve un iterador que designa uno de esos elementos; de lo contrario, devuelve [Map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`. Usa para buscar un elemento actualmente en la secuencia controlada que coincida con una clave especificada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_find.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("find {0} = {1}",   
        L'A', c1.find(L'A') != c1.end());   
  
    Mymap::iterator it = c1.find(L'b');   
    System::Console::WriteLine("find {0} = [{1} {2}]",   
        L'b', it->first, it->second);   
  
    System::Console::WriteLine("find {0} = {1}",   
        L'C', c1.find(L'C') != c1.end());   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
find A = False  
find b = [b 2]  
find C = False  
```  

## <a name="generic_container"></a> Map::generic_container (STL/CLR)
El tipo de la interfaz genérica para el contenedor.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef Microsoft::VisualC::StlClr::  
    ITree<GKey, GValue>  
    generic_container;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe la interfaz genérica para esta clase de contenedor de plantilla.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_generic_container.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Mymap::generic_container^ gc1 = %c1;   
    for each (Mymap::value_type elem in gc1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    gc1->insert(Mymap::make_value(L'd', 4));   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// modify original and display generic   
    c1.insert(Mymap::make_value(L'e', 5));   
    for each (Mymap::value_type elem in gc1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[a 1] [b 2] [c 3]  
[a 1] [b 2] [c 3] [d 4]  
[a 1] [b 2] [c 3] [d 4] [e 5]  
```  

## <a name="generic_iterator"></a> Map::generic_iterator (STL/CLR)
El tipo de iterador para su uso con la interfaz genérica para el contenedor.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef Microsoft::VisualC::StlClr::Generic::  
    ContainerBidirectionalIterator<generic_value>  
    generic_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un iterador genérico que puede usarse con la interfaz genérica para esta clase de contenedor de plantilla.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_generic_iterator.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Mymap::generic_container^ gc1 = %c1;   
    for each (Mymap::value_type elem in gc1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Mymap::generic_iterator gcit = gc1->begin();   
    Mymap::generic_value gcval = *gcit;   
    System::Console::Write(" [{0} {1}]", gcval->first, gcval->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[a 1] [b 2] [c 3]  
[a 1]  
```  

## <a name="generic_reverse_iterator"></a> Map::generic_reverse_iterator (STL/CLR)
El tipo de un iterador inverso para su uso con la interfaz genérica para el contenedor.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef Microsoft::VisualC::StlClr::Generic::  
    ReverseRandomAccessIterator<generic_value>  
    generic_reverse_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un iterador inverso genérico que puede usarse con la interfaz genérica para esta clase de contenedor de plantilla.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_generic_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Mymap::generic_container^ gc1 = %c1;   
    for each (Mymap::value_type elem in gc1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Mymap::generic_reverse_iterator gcit = gc1->rbegin();   
    Mymap::generic_value gcval = *gcit;   
    System::Console::WriteLine(" [{0} {1}]", gcval->first, gcval->second);   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[a 1] [b 2] [c 3]  
[c 3]  
```  

## <a name="generic_value"></a> Map::generic_value (STL/CLR)
El tipo de un elemento para su uso con la interfaz genérica para el contenedor.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un objeto de tipo `GValue` que describe el valor del elemento almacenado para su uso con la interfaz genérica para esta clase de contenedor de plantilla.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_generic_value.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Mymap::generic_container^ gc1 = %c1;   
    for each (Mymap::value_type elem in gc1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Mymap::generic_iterator gcit = gc1->begin();   
    Mymap::generic_value gcval = *gcit;   
    System::Console::WriteLine(" [{0} {1}]", gcval->first, gcval->second);   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[a 1] [b 2] [c 3]  
[a 1]  
```  

## <a name="insert"></a> Map:: Insert (STL/CLR)
Agrega elementos.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
cliext::pair<iterator, bool> insert(value_type val);  
iterator insert(iterator where, value_type val);  
template<typename InIter>  
    void insert(InIter first, InIter last);  
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 first  
 Comienzo del intervalo que se va a insertar.  
  
 last  
 Final del intervalo que se va a insertar.  
  
 right  
 Enumeración para insertar.  
  
 Val  
 Valor de clave para insertar.  
  
 donde  
 WHERE en el contenedor para insertar (solo sugerencia).  
  
### <a name="remarks"></a>Comentarios  
 Cada una de las funciones miembro inserta una secuencia especificada por los operandos restantes.  
  
 La primera función miembro intenta insertar un elemento con el valor `val`y devuelve un par de valores `X`. Si `X.second` es true, `X.first` designa el elemento recién insertado; en caso contrario `X.first` designa un elemento con el equivalente de clasificación que ya existe y no se inserta ningún elemento nuevo. Se usar para insertar un elemento único.  
  
 La segunda función miembro inserta un elemento con el valor `val`con `where` como una sugerencia (para mejorar el rendimiento) y devuelve un iterador que designa el elemento recién insertado. Se usar para insertar un elemento único que podría estar adyacente a un elemento que se conoce.  
  
 La tercera función miembro inserta la secuencia [`first`, `last`). Usa para insertar cero o más de los elementos copiados desde otra secuencia.  
  
 La cuarta función miembro inserta la secuencia designada por el `right`. Usa para insertar una secuencia descrita por un enumerador.  
  
 Cada inserción elemento lleva tiempo proporcional al logaritmo del número de elementos de la secuencia controlada. Inserción se puede realizar en tiempo constante amortizado, sin embargo, dada una sugerencia que designa un elemento adyacente al punto de inserción.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_insert.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
typedef Mymap::pair_iter_bool Pairib;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert a single value, unique and duplicate   
// insert a single value, success and failure   
    Pairib pair1 = c1.insert(Mymap::make_value(L'x', 24));   
    System::Console::WriteLine("insert([L'x' 24]) = [[{0} {1}] {2}]",   
        pair1.first->first, pair1.first->second, pair1.second);   
  
    pair1 = c1.insert(Mymap::make_value(L'b', 2));   
    System::Console::WriteLine("insert([L'b' 2]) = [[{0} {1}] {2}]",   
        pair1.first->first, pair1.first->second, pair1.second);   
  
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert a single value with hint   
    Mymap::iterator it =   
        c1.insert(c1.begin(), Mymap::make_value(L'y', 25));   
    System::Console::WriteLine("insert(begin(), [L'y' 25]) = [{0} {1}]",   
        it->first, it->second);   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    Mymap c2;   
    it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Mymap c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::   
            IEnumerable<Mymap::value_type>^)%c1);   
    for each (Mymap::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
insert([L'x' 24]) = [[x 24] True]  
insert([L'b' 2]) = [[b 2] False]  
 [a 1] [b 2] [c 3] [x 24]  
insert(begin(), [L'y' 25]) = [y 25]  
 [a 1] [b 2] [c 3] [x 24] [y 25]  
 [a 1] [b 2] [c 3] [x 24]  
 [a 1] [b 2] [c 3] [x 24] [y 25]  
```  

## <a name="iterator"></a> Map:: Iterator (STL/CLR)
El tipo de un iterador para la secuencia controlada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef T1 iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un objeto de tipo no especificado `T1` que puede actuar como un iterador bidireccional para la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_iterator.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    Mymap::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" [{0} {1}]", it->first, it->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  
  

## <a name="key_comp"></a> Map:: key_comp (STL/CLR)
Copia al delegado para dos claves de ordenación.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
key_compare^key_comp();  
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve al delegado de ordenación utilizado para ordenar la secuencia controlada. Usa para comparar dos claves.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_key_comp.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    Mymap::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Mymap c2 = cliext::greater<wchar_t>();   
    kcomp = c2.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    return (0);   
    }  
  
```  
  
```Output  
compare(L'a', L'a') = False  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
  
compare(L'a', L'a') = False  
compare(L'a', L'b') = False  
compare(L'b', L'a') = True  
```  

## <a name="key_compare"></a> Map:: key_compare (STL/CLR)
El delegado para dos claves de ordenación.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>  
    key_compare;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo para el delegado que determina el orden de sus argumentos de la claves.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_key_compare.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    Mymap::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Mymap c2 = cliext::greater<wchar_t>();   
    kcomp = c2.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    return (0);   
    }  
  
```  
  
```Output  
compare(L'a', L'a') = False  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
  
compare(L'a', L'a') = False  
compare(L'a', L'b') = False  
compare(L'b', L'a') = True  
```

## <a name="key_type"></a> Map:: KEY_TYPE (STL/CLR)
El tipo de una clave de ordenación.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla `Key`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_key_type.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" using key_type   
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in key_type object   
        Mymap::key_type val = it->first;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="lower_bound"></a> Map:: lower_bound (STL/CLR)
Busca el comienzo del intervalo que coincide con una clave especificada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
iterator lower_bound(key_type key);  
```  
  
#### <a name="parameters"></a>Parámetros  
 key  
 Valor de clave que se va a buscar.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro determina el primer elemento `X` en la secuencia controlada que tiene una ordenación equivalente a `key`. Si no existe ese elemento, devuelve [Map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`; en caso contrario, devuelve un iterador que designa `X`. Usa para buscar el principio de una secuencia de elementos actualmente en la secuencia controlada que coinciden con una clave especificada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_lower_bound.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",   
        c1.lower_bound(L'x') == c1.end());   
  
    Mymap::iterator it = c1.lower_bound(L'a');   
    System::Console::WriteLine("*lower_bound(L'a') = [{0} {1}]",   
        it->first, it->second);   
    it = c1.lower_bound(L'b');   
    System::Console::WriteLine("*lower_bound(L'b') = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
lower_bound(L'x')==end() = True  
*lower_bound(L'a') = [a 1]  
*lower_bound(L'b') = [b 2]  
```  

## <a name="make_value"></a> Map::make_value (STL/CLR)
Construye un objeto de valor.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
static value_type make_value(key_type key, mapped_type mapped);  
```  
  
#### <a name="parameters"></a>Parámetros  
 key  
 Valor de clave a utilizar.  
  
 asignado  
 Valor asignado a buscar.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve un `value_type` objeto cuya clave es `key` y cuyo valor asignado es `mapped`. Usarlo para crear un objeto adecuado para su uso con muchas otras funciones de miembro.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_make_value.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  

## <a name="map"></a> Map (STL/CLR)
Construye un objeto contenedor.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
map();  
explicit map(key_compare^ pred);  
map(map<Key, Mapped>% right);  
map(map<Key, Mapped>^ right);  
template<typename InIter>  
    mapmap(InIter first, InIter last);  
template<typename InIter>  
    map(InIter first, InIter last,  
        key_compare^ pred);  
map(System::Collections::Generic::IEnumerable<GValue>^ right);  
map(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
```  
  
#### <a name="parameters"></a>Parámetros  
 first  
 Comienzo del intervalo que se va a insertar.  
  
 last  
 Final del intervalo que se va a insertar.  
  
 pred  
 Orden de predicado de la secuencia controlada.  
  
 right  
 Objeto o intervalo que se va a insertar.  
  
### <a name="remarks"></a>Comentarios  
 El constructor:  
  
 `map();`  
  
 Inicializa la secuencia controlada con ningún elemento con el predicado del orden predeterminado `key_compare()`. Se usa para especificar una secuencia controlada inicial vacía, con el predicado del orden predeterminado.  
  
 El constructor:  
  
 `explicit map(key_compare^ pred);`  
  
 Inicializa la secuencia controlada con ningún elemento con el predicado ordenación `pred`. Se usa para especificar una secuencia controlada inicial vacía, con el predicado de ordenación especificado.  
  
 El constructor:  
  
 `map(map<Key, Mapped>% right);`  
  
 Inicializa la secuencia controlada a la secuencia [`right.begin()`, `right.end()`), con el predicado del orden predeterminado. Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de mapa `right`, con el predicado del orden predeterminado.  
  
 El constructor:  
  
 `map(map<Key, Mapped>^ right);`  
  
 Inicializa la secuencia controlada a la secuencia [`right->begin()`, `right->end()`), con el predicado del orden predeterminado. Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de mapa `right`, con el predicado del orden predeterminado.  
  
 El constructor:  
  
 `template<typename InIter> map(InIter first, InIter last);`  
  
 Inicializa la secuencia controlada a la secuencia [`first`, `last`), con el predicado del orden predeterminado. Usa para hacer una copia de otra secuencia de la secuencia controlada con el predicado del orden predeterminado.  
  
 El constructor:  
  
 `template<typename InIter> map(InIter first, InIter last, key_compare^ pred);`  
  
 Inicializa la secuencia controlada a la secuencia [`first`, `last`), con el predicado ordenación `pred`. Usa para realizar una copia de otra secuencia, con el predicado especificado de ordenación de la secuencia controlada.  
  
 El constructor:  
  
 `map(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 Inicializa la secuencia controlada con la secuencia designada por el enumerador `right`, con el predicado del orden predeterminado. Usa para realizar una copia de otra secuencia descrita por un enumerador con el predicado del orden predeterminado de la secuencia controlada.  
  
 El constructor:  
  
 `map(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 Inicializa la secuencia controlada con la secuencia designada por el enumerador `right`, con el predicado ordenación `pred`. Usa para realizar una copia de otra secuencia descrita por un enumerador con el predicado especificado de ordenación de la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_construct.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
// construct an empty container   
    Mymap c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Mymap c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Mymap c3(c1.begin(), c1.end());   
    for each (Mymap::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Mymap c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (Mymap::value_type elem in c4)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Mymap c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Mymap::value_type>^)%c3);   
    for each (Mymap::value_type elem in c5)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Mymap c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Mymap::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>());   
    for each (Mymap::value_type elem in c6)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mymap c7(c4);   
    for each (Mymap::value_type elem in c7)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Mymap c8(%c3);   
    for each (Mymap::value_type elem in c8)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 [a 1] [b 2] [c 3]  
size() = 0  
 [c 3] [b 2] [a 1]  
 [a 1] [b 2] [c 3]  
 [c 3] [b 2] [a 1]  
 [a 1] [b 2] [c 3]  
 [c 3] [b 2] [a 1]  
 [c 3] [b 2] [a 1]  
 [a 1] [b 2] [c 3]  
```  

## <a name="mapped_type"></a> Map:: mapped_type (STL/CLR)
El tipo de un valor asignado asociado a cada clave.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef Mapped mapped_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla `Mapped`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_mapped_type.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" using mapped_type   
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in mapped_type object   
        Mymap::mapped_type val = it->second;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
1 2 3  
```  
  
## <a name="op_as"></a> Map:: operator = (STL/CLR)
Reemplaza la secuencia controlada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
map<Key, Mapped>% operator=(map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 right  
 Contenedor que se va a copiar.  
  
### <a name="remarks"></a>Comentarios  
 Las copias de operador de miembro `right` en el objeto, a continuación, devuelve `*this`. Se usa para reemplazar la secuencia controlada por una copia de la secuencia controlada de `right`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_operator_as.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymap c2;   
    c2 = c1;   
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[a 1] [b 2] [c 3]  
```  

## <a name="op"></a> Map::operator(STL/CLR)
Asigna una clave a su valor asignado asociado.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
mapped_type operator[](key_type key);  
```  
  
#### <a name="parameters"></a>Parámetros  
 key  
 Valor de clave que se va a buscar.  
  
### <a name="remarks"></a>Comentarios  
 Las funciones miembro esfuerzos en el ámbito para buscar un elemento con una ordenación equivalente a `key`. Si lo encuentra, devuelve el valor asignado asociado; de lo contrario, inserta `value_type(key, mapped_type())` y devuelve los asociados (valor predeterminado) asigna el valor. Usarlo para buscar un valor asignado según su clave asociada, o para asegurarse de que existe una entrada para la clave si no se encuentra ninguno.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_operator_sub.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("c1[{0}] = {1}",   
        L'A', c1[L'A']);   
    System::Console::WriteLine("c1[{0}] = {1}",   
        L'b', c1[L'b']);   
  
// redisplay altered contents   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// alter mapped values and redisplay   
    c1[L'A'] = 10;   
    c1[L'c'] = 13;   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
c1[A] = 0  
c1[b] = 2  
 [A 0] [a 1] [b 2] [c 3]  
 [A 10] [a 1] [b 2] [c 13]  
```  

## <a name="rbegin"></a> Map:: rbegin (STL/CLR)
Designa el principio de la secuencia controlada inversa.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
reverse_iterator rbegin();  
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve un iterador inverso que designa el último elemento de la secuencia controlada o inmediatamente después del principio de una secuencia vacía. Por tanto, designa el `beginning` de la secuencia inversa. Utilícelo para obtener un iterador que designa el `current` a partir de la secuencia controlada mostrada en orden inverso, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_rbegin.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    Mymap::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = [{0} {1}]",   
        rit->first, rit->second);   
    ++rit;   
    System::Console::WriteLine("*++rbegin() = [{0} {1}]",   
        rit->first, rit->second);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
*rbegin() = [c 3]  
*++rbegin() = [b 2]  
```  

## <a name="reference"></a> Map:: Reference (STL/CLR)
El tipo de una referencia a un elemento.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una referencia a un elemento.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_reference.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    Mymap::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        Mymap::reference ref = *it;   
        System::Console::Write(" [{0} {1}]", ref->first, ref->second);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
``` 

## <a name="rend"></a> Map:: rend (STL/CLR)
Designa el final de la secuencia controlada inversa.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
reverse_iterator rend();  
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve un iterador inverso que apunta inmediatamente después del principio de la secuencia controlada. Por tanto, designa el `end` de la secuencia inversa. Utilícelo para obtener un iterador que designa el `current` final de la secuencia controlada mostrada en orden inverso, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_rend.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    Mymap::reverse_iterator rit = c1.rend();   
    --rit;   
    --rit;   
    System::Console::WriteLine("*-- --rend() = [{0} {1}]",   
        rit->first, rit->second);   
    ++rit;   
    System::Console::WriteLine("*--rend() = [{0} {1}]",   
        rit->first, rit->second);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
*-- --rend() = [b 2]  
*--rend() = [a 1]  
```   

## <a name="reverse_iterator"></a> Map:: reverse_iterator (STL/CLR)
El tipo de un iterador invertido para la secuencia controlada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef T3 reverse_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un objeto de tipo no especificado `T3` que puede actuar como un iterador inverso de la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" reversed   
    Mymap::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" [{0} {1}]", rit->first, rit->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[c 3] [b 2] [a 1]  
```  

## <a name="size"></a> Map:: Size (STL/CLR)
Cuenta el número de elementos.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
size_type size();  
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve la longitud de la secuencia controlada. Usa para determinar el número de elementos actualmente en la secuencia controlada. Si todo lo que le interesa es si la secuencia tiene tamaño distinto de cero, vea [Map:: Empty (STL/CLR)](../dotnet/map-empty-stl-clr.md)`()`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_size.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.insert(Mymap::make_value(L'd', 4));   
    c1.insert(Mymap::make_value(L'e', 5));   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
size() = 0 after clearing  
size() = 2 after adding 2  
```  

## <a name="size_type"></a> Map:: size_type (STL/CLR)
El tipo de una distancia con signo entre dos elementos.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef int size_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un recuento de elemento no negativo.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_size_type.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Mymap::size_type diff = 0;   
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
end()-begin() = 3  
```  
  
## <a name="swap"></a> Map:: swap (STL/CLR)
Intercambia el contenido de dos contenedores.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void swap(map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 right  
 Contenedor con el que se va a intercambiar el contenido.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro intercambia las secuencias controladas entre `this` y `right`. Lo hace en tiempo constante y no inicia ninguna excepción. Utiliza como una forma rápida para intercambiar el contenido de dos contenedores.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_swap.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'd', 4));   
    c2.insert(Mymap::make_value(L'e', 5));   
    c2.insert(Mymap::make_value(L'f', 6));   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[d 4] [e 5] [f 6]  
[d 4] [e 5] [f 6]  
[a 1] [b 2] [c 3]  
```  

## <a name="to_array"></a> Map::to_array (STL/CLR)
Copia la secuencia controlada en una nueva matriz.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
cli::array<value_type>^ to_array();  
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve una matriz que contiene la secuencia controlada. Se usa para obtener una copia de la secuencia controlada en forma de matriz.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_to_array.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// copy the container and modify it   
    cli::array<Mymap::value_type>^ a1 = c1.to_array();   
  
    c1.insert(Mymap::make_value(L'd', 4));   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// display the earlier array copy   
    for each (Mymap::value_type elem in a1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3] [d 4]  
[a 1] [b 2] [c 3]  
```  

## <a name="upper_bound"></a> Map:: upper_bound (STL/CLR)
Busca el final del intervalo que coincide con una clave especificada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
iterator upper_bound(key_type key);  
```  
  
#### <a name="parameters"></a>Parámetros  
 key  
 Valor de clave que se va a buscar.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro determina el último elemento `X` en la secuencia controlada que tiene una ordenación equivalente a `key`. Si no existe ese elemento, o si `X` es el último elemento de la secuencia controlada, devuelve [Map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`; en caso contrario, devuelve un iterador que designa el primer elemento más allá de `X`. Usa para buscar el final de una secuencia de elementos actualmente en la secuencia controlada que coinciden con una clave especificada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_upper_bound.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",   
        c1.upper_bound(L'x') == c1.end());   
  
    Mymap::iterator it = c1.upper_bound(L'a');   
    System::Console::WriteLine("*upper_bound(L'a') = [{0} {1}]",   
        it->first, it->second);   
    it = c1.upper_bound(L'b');   
    System::Console::WriteLine("*upper_bound(L'b') = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
upper_bound(L'x')==end() = True  
*upper_bound(L'a') = [b 2]  
*upper_bound(L'b') = [c 3]  
```  

## <a name="value_comp"></a> Map:: value_comp (STL/CLR)
Copia al delegado de ordenación para los dos valores de elemento.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
value_compare^ value_comp();  
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve al delegado de ordenación utilizado para ordenar la secuencia controlada. Usa para comparar dos valores de elemento.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_value_comp.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    Mymap::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",   
        kcomp(Mymap::make_value(L'a', 1),   
            Mymap::make_value(L'a', 1)));   
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",   
        kcomp(Mymap::make_value(L'a', 1),   
            Mymap::make_value(L'b', 2)));   
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",   
        kcomp(Mymap::make_value(L'b', 2),   
            Mymap::make_value(L'a', 1)));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
compare([L'a', 1], [L'a', 1]) = False  
compare([L'a', 1], [L'b', 2]) = True  
compare([L'b', 2], [L'a', 1]) = False  
```  
  
## <a name="value_compare"></a> Map::value_compare (STL/CLR)
El delegado de ordenación para los dos valores de elemento.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>  
    value_compare;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo para el delegado que determina el orden de sus argumentos de valor.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_value_compare.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    Mymap::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",   
        kcomp(Mymap::make_value(L'a', 1),   
            Mymap::make_value(L'a', 1)));   
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",   
        kcomp(Mymap::make_value(L'a', 1),   
            Mymap::make_value(L'b', 2)));   
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",   
        kcomp(Mymap::make_value(L'b', 2),   
            Mymap::make_value(L'a', 1)));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
compare([L'a', 1], [L'a', 1]) = False  
compare([L'a', 1], [L'b', 2]) = True  
compare([L'b', 2], [L'a', 1]) = False  
```  

## <a name="value_type"></a> Map:: value_type (STL/CLR)
El tipo de un elemento.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef generic_value value_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de `generic_value`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_value_type.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" using value_type   
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in value_type object   
        Mymap::value_type val = *it;   
        System::Console::Write(" [{0} {1}]", val->first, val->second);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  

## <a name="op_neq"></a> operador! = (map) (STL/CLR)
Lista de comparación no es igual.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
template<typename Key,  
    typename Mapped>  
    bool operator!=(map<Key, Mapped>% left,  
        map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 izquierda  
 Contenedor izquierdo que se va a comparar.  
  
 right  
 Contenedor derecho que se va a comparar.  
  
### <a name="remarks"></a>Comentarios  
 Devuelve la función de operador `!(left == right)`. Se usa para comprobar si `left` no está ordenado el mismo que `right` cuando los dos mapas son comparado elemento por elemento.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_operator_ne.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'a', 1));   
    c2.insert(Mymap::make_value(L'b', 2));   
    c2.insert(Mymap::make_value(L'd', 4));   
  
// display contents " [a 1] [b 2] [d 4]"   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] != [a b c] is {0}",   
        c1 != c1);   
    System::Console::WriteLine("[a b c] != [a b d] is {0}",   
        c1 != c2);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [d 4]  
[a b c] != [a b c] is False  
[a b c] != [a b d] is True  
```  
  
## <a name="op_lt"></a> operador&lt; (map) (STL/CLR)
Lista inferior comparación.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
template<typename Key,  
    typename Mapped>  
    bool operator<(map<Key, Mapped>% left,  
        map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 izquierda  
 Contenedor izquierdo que se va a comparar.  
  
 right  
 Contenedor derecho que se va a comparar.  
  
### <a name="remarks"></a>Comentarios  
 El operador función devuelve true si, para la posición más baja `i` que `!(right[i] < left[i])` es también true que `left[i] < right[i]`. De lo contrario, devuelve `left->size() < right->size()` se usa para comprobar si `left` está ordenado antes `right` cuando los dos mapas son comparado elemento por elemento.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_operator_lt.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'a', 1));   
    c2.insert(Mymap::make_value(L'b', 2));   
    c2.insert(Mymap::make_value(L'd', 4));   
  
// display contents " [a 1] [b 2] [d 4]"   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] < [a b c] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[a b c] < [a b d] is {0}",   
        c1 < c2);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [d 4]  
[a b c] < [a b c] is False  
[a b c] < [a b d] is True  
```  

## <a name="op_lteq"></a> operador&lt;= (map) (STL/CLR)
Menor o igual lista comparación.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
template<typename Key,  
    typename Mapped>  
    bool operator<=(map<Key, Mapped>% left,  
        map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 izquierda  
 Contenedor izquierdo que se va a comparar.  
  
 right  
 Contenedor derecho que se va a comparar.  
  
### <a name="remarks"></a>Comentarios  
 Devuelve la función de operador `!(right < left)`. Se usa para comprobar si `left` no está ordenado después `right` cuando los dos mapas son comparado elemento por elemento.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_operator_le.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'a', 1));   
    c2.insert(Mymap::make_value(L'b', 2));   
    c2.insert(Mymap::make_value(L'd', 4));   
  
// display contents " [a 1] [b 2] [d 4]"   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] <= [a b c] is {0}",   
        c1 <= c1);   
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",   
        c2 <= c1);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [d 4]  
[a b c] <= [a b c] is True  
[a b d] <= [a b c] is False  
```  

## <a name="op_eq"></a> operador == (map) (STL/CLR)
Lista comparación igual.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
template<typename Key,  
    typename Mapped>  
    bool operator==(map<Key, Mapped>% left,  
        map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 izquierda  
 Contenedor izquierdo que se va a comparar.  
  
 right  
 Contenedor derecho que se va a comparar.  
  
### <a name="remarks"></a>Comentarios  
 La función de operador devuelve true solo si controlan las secuencias de `left` y `right` tienen la misma longitud y, para cada posición `i`, `left[i] ==` `right[i]`. Se usa para comprobar si `left` se ordenan igual `right` cuando los dos mapas son comparado elemento por elemento.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_operator_eq.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'a', 1));   
    c2.insert(Mymap::make_value(L'b', 2));   
    c2.insert(Mymap::make_value(L'd', 4));   
  
// display contents " [a 1] [b 2] [d 4]"   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] == [a b c] is {0}",   
        c1 == c1);   
    System::Console::WriteLine("[a b c] == [a b d] is {0}",   
        c1 == c2);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [d 4]  
[a b c] == [a b c] is True  
[a b c] == [a b d] is False  
```  

## <a name="op_gt"></a> operador&gt; (map) (STL/CLR)
Lista es mayor que la comparación.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
template<typename Key,  
    typename Mapped>  
    bool operator>(map<Key, Mapped>% left,  
        map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 izquierda  
 Contenedor izquierdo que se va a comparar.  
  
 right  
 Contenedor derecho que se va a comparar.  
  
### <a name="remarks"></a>Comentarios  
 Devuelve la función de operador `right` `<` `left`. Se usa para comprobar si `left` se ordena después `right` cuando los dos mapas son comparado elemento por elemento.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_operator_gt.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'a', 1));   
    c2.insert(Mymap::make_value(L'b', 2));   
    c2.insert(Mymap::make_value(L'd', 4));   
  
// display contents " [a 1] [b 2] [d 4]"   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] > [a b c] is {0}",   
        c1 > c1);   
    System::Console::WriteLine("[a b d] > [a b c] is {0}",   
        c2 > c1);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [d 4]  
[a b c] > [a b c] is False  
[a b d] > [a b c] is True  
```  

## <a name="op_gteq"></a> operador&gt;= (map) (STL/CLR)
Comparación igual o mayor de la lista.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
template<typename Key,  
    typename Mapped>  
    bool operator>=(map<Key, Mapped>% left,  
        map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 izquierda  
 Contenedor izquierdo que se va a comparar.  
  
 right  
 Contenedor derecho que se va a comparar.  
  
### <a name="remarks"></a>Comentarios  
 Devuelve la función de operador `!(left` `<` `right)`. Se usa para comprobar si `left` no está ordenado antes `right` cuando los dos mapas son comparado elemento por elemento.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_operator_ge.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'a', 1));   
    c2.insert(Mymap::make_value(L'b', 2));   
    c2.insert(Mymap::make_value(L'd', 4));   
  
// display contents " [a 1] [b 2] [d 4]"   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] >= [a b c] is {0}",   
        c1 >= c1);   
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",   
        c1 >= c2);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [d 4]  
[a b c] >= [a b c] is True  
[a b c] >= [a b d] is False  
``` 
