---
title: establecer (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set
- cliext::operator!=
- cliext::operator<
- cliext::operator<=
- cliext::operator==
- cliext::operator>
- cliext::operator>=
- cliext::set::begin
- cliext::set::clear
- cliext::set::const_iterator
- cliext::set::const_reference
- cliext::set::const_reverse_iterator
- cliext::set::count
- cliext::set::difference_type
- cliext::set::empty
- cliext::set::end
- cliext::set::equal_range
- cliext::set::erase
- cliext::set::find
- cliext::set::generic_container
- cliext::set::generic_iterator
- cliext::set::generic_reverse_iterator
- cliext::set::generic_value
- cliext::set::insert
- cliext::set::iterator
- cliext::set::key_comp
- cliext::set::key_compare
- cliext::set::key_type
- cliext::set::lower_bound
- cliext::set::make_value
- cliext::set::operator=
- cliext::set::rbegin
- cliext::set::reference
- cliext::set::rend
- cliext::set::reverse_iterator
- cliext::set::set
- cliext::set::size
- cliext::set::size_type
- cliext::set::swap
- cliext::set::to_array
- cliext::set::upper_bound
- cliext::set::value_comp
- cliext::set::value_compare
- cliext::set::value_type
dev_langs:
- C++
helpviewer_keywords:
- <cliext/set> header [STL/CLR]
- <set> header [STL/CLR]
- set class [STL/CLR]
- operator!= (set) member [STL/CLR]
- operator< (set) member [STL/CLR]
- operator<= (set) member [STL/CLR]
- operator== (set) member [STL/CLR]
- operator> (set) member [STL/CLR]
- operator>= (set) member [STL/CLR]
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
- operator= member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- reverse_iterator member [STL/CLR]
- set member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- upper_bound member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 27d3628c-741a-43a7-bef1-5085536f679e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 99ea41a77a8ed01cb78df3513ccb79b6b2a8b3f1
ms.sourcegitcommit: 301bb19056e5bae84ff50f7d1df1e546efe225ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/21/2018
ms.locfileid: "36305896"
---
# <a name="set-stlclr"></a>set (STL/CLR)
La clase de plantilla describe un objeto que controla una secuencia de longitud variable de elementos que tiene acceso bidireccional. Utilice el contenedor de `set` para administrar una secuencia de elementos como un árbol equilibrado (casi) ordenada de nodos, cada uno de ellos almacenar un elemento.  
  
 En la descripción siguiente, `GValue` es el mismo que `GKey`, que a su vez es igual a `Key` a menos que el segundo es un tipo de referencia, en cuyo caso es `Key^`.  
  
### <a name="syntax"></a>Sintaxis  
  
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
  
## <a name="declarations"></a>Declaraciones  
  
|Definición de tipo|Descripción|  
|---------------------|-----------------|  
|[set::const_iterator (STL/CLR)](#const_iterator)|El tipo de un iterador constante para la secuencia controlada.|  
|[set::const_reference (STL/CLR)](#const_reference)|El tipo de una referencia constante a un elemento.|  
|[set::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|El tipo de un iterador invertido constante para la secuencia controlada.|  
|[set::difference_type (STL/CLR)](#difference_type)|El tipo de una distancia (posiblemente con signo) entre dos elementos.|  
|[set::generic_container (STL/CLR)](#generic_container)|El tipo de la interfaz genérica para el contenedor.|  
|[set::generic_iterator (STL/CLR)](#generic_iterator)|El tipo de un iterador para la interfaz genérica para el contenedor.|  
|[set::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|El tipo de un iterador inverso para la interfaz genérica para el contenedor.|  
|[set::generic_value (STL/CLR)](#generic_value)|El tipo de un elemento de la interfaz genérica para el contenedor.|  
|[set::iterator (STL/CLR)](#iterator)|El tipo de un iterador para la secuencia controlada.|  
|[set::key_compare (STL/CLR)](#key_compare)|El delegado para dos claves de ordenación.|  
|[set::key_type (STL/CLR)](#key_type)|El tipo de una clave de ordenación.|  
|[set::reference (STL/CLR)](#reference)|El tipo de una referencia a un elemento.|  
|[set::reverse_iterator (STL/CLR)](#reverse_iterator)|El tipo de un iterador invertido para la secuencia controlada.|  
|[set::size_type (STL/CLR)](#size_type)|El tipo de una distancia (positivo) entre dos elementos.|  
|[set::value_compare (STL/CLR)](#value_compare)|El delegado de ordenación para los dos valores de elemento.|  
|[set::value_type (STL/CLR)](#value_type)|El tipo de un elemento.|  
  
|Función miembro|Descripción|  
|---------------------|-----------------|  
|[set::begin (STL/CLR)](#begin)|Designa el principio de la secuencia controlada.|  
|[set::clear (STL/CLR)](#clear)|Quita todos los elementos.|  
|[set::count (STL/CLR)](#count)|Recuentos de elementos que coinciden con una clave especificada.|  
|[set::empty (STL/CLR)](#empty)|Comprueba si no hay ningún elemento presente.|  
|[set::end (STL/CLR)](#end)|Designa el final de la secuencia controlada.|  
|[set::equal_range (STL/CLR)](#equal_range)|Busca el intervalo que coincide con una clave especificada.|  
|[set::erase (STL/CLR)](#erase)|Quita los elementos de las posiciones especificadas.|  
|[set::find (STL/CLR)](#find)|Busca un elemento que coincide con una clave especificada.|  
|[set::insert (STL/CLR)](#insert)|Agrega elementos.|  
|[set::key_comp (STL/CLR)](#key_comp)|Copia al delegado para dos claves de ordenación.|  
|[set::lower_bound (STL/CLR)](#lower_bound)|Busca el comienzo del intervalo que coincide con una clave especificada.|  
|[set::make_value (STL/CLR)](#make_value)|Construye un objeto de valor.|  
|[set::rbegin (STL/CLR)](#rbegin)|Designa el principio de la secuencia controlada inversa.|  
|[set::rend (STL/CLR)](#rend)|Designa el final de la secuencia controlada inversa.|  
|[set::set (STL/CLR)](#set)|Construye un objeto contenedor.|  
|[set::size (STL/CLR)](#size)|Cuenta el número de elementos.|  
|[set::swap (STL/CLR)](#swap)|Intercambia el contenido de dos contenedores.|  
|[set::to_array (STL/CLR)](#to_array)|Copia la secuencia controlada en una nueva matriz.|  
|[set::upper_bound (STL/CLR)](#upper_bound)|Busca el final del intervalo que coincide con una clave especificada.|  
|[set::value_comp (STL/CLR)](#value_comp)|Copia al delegado de ordenación para los dos valores de elemento.|  
  
|Operador|Descripción|  
|--------------|-----------------|  
|[set::operator= (STL/CLR)](#op_as)|Reemplaza la secuencia controlada.|  
|[operator!= (set) (STL/CLR)](#op_neq)|Determina si un `set` no es igual a otro objeto `set` objeto.|  
|[operator< (set) (STL/CLR)](#op_lt)|Determina si un `set` objeto es menor que otro `set` objeto.|  
|[operator<= (set) (STL/CLR)](#op_lteq)|Determina si un `set` objeto es menor o igual que otro `set` objeto.|  
|[operator== (set) (STL/CLR)](#op_eq)|Determina si un `set` es igual a otro objeto `set` objeto.|  
|[operator> (set) (STL/CLR)](#op_gt)|Determina si un `set` es mayor que otro objeto `set` objeto.|  
|[operator>= (set) (STL/CLR)](#op_gteq)|Determina si un `set` objeto es mayor o igual que otro `set` objeto.|  
  
## <a name="interfaces"></a>Interfaces  
  
|Interfaz|Descripción|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplicar un objeto.|  
|<xref:System.Collections.IEnumerable>|Secuencia a través de los elementos.|  
|<xref:System.Collections.ICollection>|Mantener el grupo de elementos.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Secuencia a través de los elementos con tipo.|  
|<xref:System.Collections.Generic.ICollection%601>|Mantener el grupo de elementos con tipo.|  
|ITree\<clave, valor >|Mantener contenedor genérico.|  
  
### <a name="remarks"></a>Comentarios  
 El objeto asigna y libera almacenamiento para la secuencia que controla como nodos individuales. Inserta elementos en un árbol equilibrado (casi) que mantiene ordenada por la modificación de los vínculos entre los nodos, nunca copiando el contenido de un nodo a otro. Esto significa que puede insertar y quitar elementos libremente sin alterar los elementos restantes.  
  
 El objeto ordena la secuencia controla mediante una llamada a un objeto de delegado almacenado de tipo [Set:: key_compare (STL/CLR)](../dotnet/set-key-compare-stl-clr.md). Puede especificar el objeto de delegado almacenado cuando se construye el conjunto; Si no se especifica ningún objeto de delegado, el valor predeterminado es la comparación `operator<(key_type, key_type)`. Tener acceso a este objeto almacenado llamando a la función miembro [key_comp (STL/CLR)](../dotnet/set-key-comp-stl-clr.md)`()`.  
  
 Este tipo de objeto de delegado debe imponer una ordenación débil estricta en claves de tipo [Set:: KEY_TYPE (STL/CLR)](../dotnet/set-key-type-stl-clr.md). Es decir, para las dos claves `X` y `Y`:  
  
 `key_comp()(X, Y)` Devuelve el valor booleano mismo resultado en cada llamada.  
  
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
 
## <a name="members"></a>Miembros

## <a name="begin"></a>Set:: begin (STL/CLR)
Designa el principio de la secuencia controlada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
iterator begin();  
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve un iterador bidireccional que designa el primer elemento de la secuencia controlada o más allá del final de una secuencia vacía. Utilícelo para obtener un iterador que designa el `current` a partir de la secuencia controlada, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_begin.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Myset::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = {0}", *it);   
    System::Console::WriteLine("*++begin() = {0}", *++it);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*begin() = a  
*++begin() = b  
```  

## <a name="clear"></a>Set:: Clear (STL/CLR)
Quita todos los elementos.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void clear();  
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro llama eficazmente a [Set:: Erase (STL/CLR)](../dotnet/set-erase-stl-clr.md) `(` [Set:: begin (STL/CLR)](../dotnet/set-begin-stl-clr.md) `(),` [Set:: end (STL/CLR)](../dotnet/set-end-stl-clr.md) `())`. Utilizarlo para asegurarse de que la secuencia controlada está vacía.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_clear.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// add elements and clear again   
    c1.insert(L'a');   
    c1.insert(L'b');   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size() = 0  
 a b  
size() = 0  
```  

## <a name="const_iterator"></a>Set:: const_iterator (STL/CLR)
El tipo de un iterador constante para la secuencia controlada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef T2 const_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un objeto de tipo no especificado `T2` que puede actuar como un iterador constante bidireccional para la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_const_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    Myset::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" {0}", *cit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="const_reference"></a>Set:: const_reference (STL/CLR)
El tipo de una referencia constante a un elemento.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef value_type% const_reference;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una referencia constante a un elemento.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_const_reference.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    Myset::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        {   // get a const reference to an element   
        Myset::const_reference cref = *cit;   
        System::Console::Write(" {0}", cref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="const_reverse_iterator"></a>Set:: const_reverse_iterator (STL/CLR)
El tipo de un iterador inverso constante para la secuencia controlada...  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef T4 const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un objeto de tipo no especificado `T4` que puede actuar como un iterador inverso constante para la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" reversed   
    Myset::const_reverse_iterator crit = c1.rbegin();   
    for (; crit != c1.rend(); ++crit)   
        System::Console::Write(" {0}", *crit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  

## <a name="count"></a>Set:: Count (STL/CLR)
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
// cliext_set_count.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));   
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));   
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
count(L'A') = 0  
count(L'b') = 1  
count(L'C') = 0  
```  

## <a name="difference_type"></a>Set:: difference_type (STL/CLR)
Los tipos de una distancia con signo entre dos elementos.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un recuento de elemento posiblemente negativo.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_difference_type.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Myset::difference_type diff = 0;   
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
  
// compute negative difference   
    diff = 0;   
    for (Myset::iterator it = c1.end(); it != c1.begin(); --it)   
        --diff;   
    System::Console::WriteLine("begin()-end() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
end()-begin() = 3  
begin()-end() = -3  
```  

## <a name="empty"></a>Empty (STL/CLR)
Comprueba si no hay ningún elemento presente.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
bool empty();  
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve true para una secuencia controlada vacía. Es equivalente a [Set:: Size (STL/CLR)](../dotnet/set-size-stl-clr.md)`() == 0`. Se usa para comprobar si el conjunto está vacío.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_empty.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
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
 a b c  
size() = 3  
empty() = False  
size() = 0  
empty() = True  
```  

## <a name="end"></a>Set:: end (STL/CLR)
Designa el final de la secuencia controlada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
iterator end();  
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve un iterador bidireccional que apunta justo después del final de la secuencia controlada. Utilícelo para obtener un iterador que designa el final de la secuencia controlada; su no de estado de cambio si cambia la longitud de la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_end.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last two items   
    Myset::iterator it = c1.end();   
    --it;   
    System::Console::WriteLine("*-- --end() = {0}", *--it);   
    System::Console::WriteLine("*--end() = {0}", *++it);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*-- --end() = b  
*--end() = c  
```  

## <a name="equal_range"></a>Set:: equal_range (STL/CLR)
Busca el intervalo que coincide con una clave especificada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
cliext::pair<iterator, iterator> equal_range(key_type key);  
```  
  
#### <a name="parameters"></a>Parámetros  
 key  
 Valor de clave que se va a buscar.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve un par de iteradores `cliext::pair<iterator, iterator>(` [Set:: lower_bound (STL/CLR)](../dotnet/set-lower-bound-stl-clr.md) `(key),` [Set:: upper_bound (STL/CLR)](../dotnet/set-upper-bound-stl-clr.md)`(key))`. Usa para determinar el intervalo de elementos actualmente en la secuencia controlada que coinciden con una clave especificada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_equal_range.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
typedef Myset::pair_iter_iter Pairii;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display results of failed search   
    Pairii pair1 = c1.equal_range(L'x');   
    System::Console::WriteLine("equal_range(L'x') empty = {0}",   
        pair1.first == pair1.second);   
  
// display results of successful search   
    pair1 = c1.equal_range(L'b');   
    for (; pair1.first != pair1.second; ++pair1.first)   
        System::Console::Write(" {0}", *pair1.first);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
equal_range(L'x') empty = True  
 b  
``` 

## <a name="erase"></a>Set:: Erase (STL/CLR)
Quita los elementos de las posiciones especificadas.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
size_type erase(key_type key)  
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
 La primera función miembro quita el elemento de la secuencia controlada señalada por `where`y devuelve un iterador que designa el primer elemento que permanece más allá del elemento eliminado, o [Set:: end (STL/CLR)](../dotnet/set-end-stl-clr.md) `()` si no existe ese elemento. Usa para quitar un único elemento.  
  
 La segunda función miembro quita los elementos de la secuencia controlada en el intervalo [`first`, `last`) y devuelve un iterador que designa el primer elemento que permanece más allá de los elementos quitados, o `end()` si ningún elemento existe... Usa para quitar cero o más elementos contiguos.  
  
 La tercera función miembro quita cualquier elemento de la secuencia controlada cuyo criterio de ordenación es equivalente a `key`y devuelve un recuento del número de elementos quitados. Se usa para quitar y recuento de todos los elementos que coinciden con una clave especificada.  
  
 La eliminación de cada elemento lleva tiempo proporcional al logaritmo del número de elementos de la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_erase.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.insert(L'd');   
    c1.insert(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    Myset::iterator it = c1.end();   
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",   
        *c1.erase(c1.begin(), --it));   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
erase(begin()) = b  
 b c d e  
erase(begin(), end()-1) = e  
size() = 1  
```   

## <a name="find"></a>Set:: Find (STL/CLR)
Busca un elemento que coincide con una clave especificada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
iterator find(key_type key);  
```  
  
#### <a name="parameters"></a>Parámetros  
 key  
 Valor de clave que se va a buscar.  
  
### <a name="remarks"></a>Comentarios  
 Si al menos un elemento de la secuencia controlada tiene una ordenación equivalente con `key`, la función miembro devuelve un iterador que designa uno de esos elementos; de lo contrario, devuelve [Set:: end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`. Usa para buscar un elemento actualmente en la secuencia controlada que coincida con una clave especificada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_find.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("find {0} = {1}",   
        L'A', c1.find(L'A') != c1.end());   
    System::Console::WriteLine("find {0} = {1}",   
        L'b', *c1.find(L'b'));   
    System::Console::WriteLine("find {0} = {1}",   
        L'C', c1.find(L'C') != c1.end());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
find A = False  
find b = b  
find C = False  
```  

## <a name="generic_container"></a>Set::generic_container (STL/CLR)
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
// cliext_set_generic_container.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    gc1->insert(L'd');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify original and display generic   
    c1.insert(L'e');   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a b c d  
a b c d e  
```  
  
## <a name="generic_iterator"></a> Set::generic_iterator (STL/CLR)
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
// cliext_set_generic_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myset::generic_iterator gcit = gc1->begin();   
    Myset::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a  
```  
  
## <a name="generic_reverse_iterator"></a> Set::generic_reverse_iterator (STL/CLR)
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
// cliext_set_generic_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myset::generic_reverse_iterator gcit = gc1->rbegin();   
    Myset::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
c  
```  

## <a name="generic_value"></a> Set::generic_value (STL/CLR)
El tipo de un elemento para su uso con la interfaz genérica para el contenedor.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un objeto de tipo `GValue` que describe el valor del elemento almacenado para su uso con la interfaz genérica para esta clase de contenedor de plantilla.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_generic_value.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myset::generic_iterator gcit = gc1->begin();   
    Myset::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a  
```  
  
## <a name="insert"></a> Set:: Insert (STL/CLR)
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
// cliext_set_insert.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
typedef Myset::pair_iter_bool Pairib;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value, unique and duplicate   
    Pairib pair1 = c1.insert(L'x');   
    System::Console::WriteLine("insert(L'x') = [{0} {1}]",   
        *pair1.first, pair1.second);   
  
    pair1 = c1.insert(L'b');   
    System::Console::WriteLine("insert(L'b') = [{0} {1}]",   
        *pair1.first, pair1.second);   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value with hint   
    System::Console::WriteLine("insert(begin(), L'y') = {0}",   
        *c1.insert(c1.begin(), L'y'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    Myset c2;   
    Myset::iterator it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Myset c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
insert(L'x') = [x True]  
insert(L'b') = [b False]  
 a b c x  
insert(begin(), L'y') = y  
 a b c x y  
 a b c x  
 a b c x y  
```  

## <a name="iterator"></a> Set:: Iterator (STL/CLR)
El tipo de un iterador para la secuencia controlada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef T1 iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un objeto de tipo no especificado `T1` que puede actuar como un iterador bidireccional para la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    Myset::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="key_comp"></a> key_comp (STL/CLR)
Copia al delegado para dos claves de ordenación.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
key_compare^key_comp();  
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve al delegado de ordenación utilizado para ordenar la secuencia controlada. Usa para comparar dos claves.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_key_comp.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    Myset::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Myset c2 = cliext::greater<wchar_t>();   
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

## <a name="key_compare"></a> Set:: key_compare (STL/CLR)
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
// cliext_set_key_compare.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    Myset::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Myset c2 = cliext::greater<wchar_t>();   
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

## <a name="key_type"></a> Set:: KEY_TYPE (STL/CLR)
El tipo de una clave de ordenación.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla `Key`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_key_type.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" using key_type   
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in key_type object   
        Myset::key_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="lower_bound"></a> Set:: lower_bound (STL/CLR)
Busca el comienzo del intervalo que coincide con una clave especificada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
iterator lower_bound(key_type key);  
```  
  
#### <a name="parameters"></a>Parámetros  
 key  
 Valor de clave que se va a buscar.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro determina el primer elemento `X` en la secuencia controlada que tiene una ordenación equivalente a `key`. Si no existe ese elemento, devuelve [Set:: end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`; en caso contrario, devuelve un iterador que designa `X`. Usa para buscar el principio de una secuencia de elementos actualmente en la secuencia controlada que coinciden con una clave especificada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_lower_bound.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",   
        c1.lower_bound(L'x') == c1.end());   
  
    System::Console::WriteLine("*lower_bound(L'a') = {0}",   
        *c1.lower_bound(L'a'));   
    System::Console::WriteLine("*lower_bound(L'b') = {0}",   
        *c1.lower_bound(L'b'));   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
lower_bound(L'x')==end() = True  
*lower_bound(L'a') = a  
*lower_bound(L'b') = b  
```  

## <a name="make_value"></a> Set::make_value (STL/CLR)
Construye un objeto de valor.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
static value_type make_value(key_type key);  
```  
  
#### <a name="parameters"></a>Parámetros  
 key  
 Valor de clave a utilizar.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve un `value_type` objeto cuya clave es `key`. Usarlo para crear un objeto adecuado para su uso con muchas otras funciones de miembro.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_make_value.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(Myset::make_value(L'a'));   
    c1.insert(Myset::make_value(L'b'));   
    c1.insert(Myset::make_value(L'c'));   
  
// display contents " a b c"   
    for each (Myset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="op_as"></a> Set::operator = (STL/CLR)
Reemplaza la secuencia controlada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
set<Key>% operator=(set<Key>% right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 right  
 Contenedor que se va a copiar.  
  
### <a name="remarks"></a>Comentarios  
 Las copias de operador de miembro `right` en el objeto, a continuación, devuelve `*this`. Se usa para reemplazar la secuencia controlada por una copia de la secuencia controlada de `right`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_operator_as.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (Myset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2 = c1;   
// display contents " a b c"   
    for each (Myset::value_type elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
```  

## <a name="rbegin"></a> rbegin (STL/CLR)
Designa el principio de la secuencia controlada inversa.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
reverse_iterator rbegin();  
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve un iterador inverso que designa el último elemento de la secuencia controlada o inmediatamente después del principio de una secuencia vacía. Por tanto, designa el `beginning` de la secuencia inversa. Utilícelo para obtener un iterador que designa el `current` a partir de la secuencia controlada mostrada en orden inverso, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_rbegin.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    Myset::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = {0}", *rit);   
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*rbegin() = c  
*++rbegin() = b  
```  

## <a name="reference"></a> Set:: Reference (STL/CLR)
El tipo de una referencia a un elemento.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una referencia a un elemento.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_reference.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    Myset::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        Myset::reference ref = *it;   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```

## <a name="rend"></a> Set:: rend (STL/CLR)
Designa el final de la secuencia controlada inversa.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
reverse_iterator rend();  
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve un iterador inverso que apunta inmediatamente después del principio de la secuencia controlada. Por tanto, designa el `end` de la secuencia inversa. Utilícelo para obtener un iterador que designa el `current` final de la secuencia controlada mostrada en orden inverso, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_rend.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Myset::reverse_iterator rit = c1.rend();   
    --rit;   
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);   
    System::Console::WriteLine("*--rend() = {0}", *++rit);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*-- --rend() = b  
*--rend() = a  
```    

## <a name="reverse_iterator"></a> Set:: reverse_iterator (STL/CLR)
El tipo de un iterador invertido para la secuencia controlada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef T3 reverse_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un objeto de tipo no especificado `T3` que puede actuar como un iterador inverso de la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" reversed   
    Myset::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  
  
## <a name="set"></a> Set:: Set (STL/CLR)
Construye un objeto contenedor.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
set();  
explicit set(key_compare^ pred);  
set(set<Key>% right);  
set(set<Key>^ right);  
template<typename InIter>  
    setset(InIter first, InIter last);  
template<typename InIter>  
    set(InIter first, InIter last,  
        key_compare^ pred);  
set(System::Collections::Generic::IEnumerable<GValue>^ right);  
set(System::Collections::Generic::IEnumerable<GValue>^ right,  
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
  
 `set();`  
  
 Inicializa la secuencia controlada con ningún elemento con el predicado del orden predeterminado `key_compare()`. Se usa para especificar una secuencia controlada inicial vacía, con el predicado del orden predeterminado.  
  
 El constructor:  
  
 `explicit set(key_compare^ pred);`  
  
 Inicializa la secuencia controlada con ningún elemento con el predicado ordenación `pred`. Se usa para especificar una secuencia controlada inicial vacía, con el predicado de ordenación especificado.  
  
 El constructor:  
  
 `set(set<Key>% right);`  
  
 Inicializa la secuencia controlada a la secuencia [`right.begin()`, `right.end()`), con el predicado del orden predeterminado. Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de conjunto `right`, con el predicado del orden predeterminado.  
  
 El constructor:  
  
 `set(set<Key>^ right);`  
  
 Inicializa la secuencia controlada a la secuencia [`right->begin()`, `right->end()`), con el predicado del orden predeterminado. Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de conjunto `right`, con el predicado del orden predeterminado.  
  
 El constructor:  
  
 `template<typename InIter> set(InIter first, InIter last);`  
  
 Inicializa la secuencia controlada a la secuencia [`first`, `last`), con el predicado del orden predeterminado. Usa para hacer una copia de otra secuencia de la secuencia controlada con el predicado del orden predeterminado.  
  
 El constructor:  
  
 `template<typename InIter> set(InIter first, InIter last, key_compare^ pred);`  
  
 Inicializa la secuencia controlada a la secuencia [`first`, `last`), con el predicado ordenación `pred`. Usa para realizar una copia de otra secuencia, con el predicado especificado de ordenación de la secuencia controlada.  
  
 El constructor:  
  
 `set(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 Inicializa la secuencia controlada con la secuencia designada por el enumerador `right`, con el predicado del orden predeterminado. Usa para realizar una copia de otra secuencia descrita por un enumerador con el predicado del orden predeterminado de la secuencia controlada.  
  
 El constructor:  
  
 `set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 Inicializa la secuencia controlada con la secuencia designada por el enumerador `right`, con el predicado ordenación `pred`. Usa para realizar una copia de otra secuencia descrita por un enumerador con el predicado especificado de ordenación de la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_construct.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
// construct an empty container   
    Myset c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myset c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myset c3(c1.begin(), c1.end());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myset c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myset c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myset c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c6)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Myset c7(c4);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myset c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 a b c  
size() = 0  
 c b a  
 a b c  
 c b a  
 a b c  
 c b a  
 c b a  
 a b c  
```  

## <a name="size"></a> Set:: Size (STL/CLR)
Cuenta el número de elementos.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
size_type size();  
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve la longitud de la secuencia controlada. Usa para determinar el número de elementos actualmente en la secuencia controlada. Si todo lo que le interesa es si la secuencia tiene tamaño distinto de cero, vea [Empty (STL/CLR)](../dotnet/set-empty-stl-clr.md)`()`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_size.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.insert(L'a');   
    c1.insert(L'b');   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size() = 3 starting with 3  
size() = 0 after clearing  
size() = 2 after adding 2  
```  

## <a name="size_type"></a> Set:: size_type (STL/CLR)
El tipo de una distancia con signo entre dos elementos.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef int size_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un recuento de elemento no negativo.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_size_type.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Myset::size_type diff = 0;   
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
end()-begin() = 3  
```  

## <a name="swap"></a> Set:: swap (STL/CLR)
Intercambia el contenido de dos contenedores.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void swap(set<Key>% right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 right  
 Contenedor con el que se va a intercambiar el contenido.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro intercambia las secuencias controladas entre `this` y `right`. Lo hace en tiempo constante y no inicia ninguna excepción. Utiliza como una forma rápida para intercambiar el contenido de dos contenedores.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_swap.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    Myset c2;   
    c2.insert(L'd');   
    c2.insert(L'e');   
    c2.insert(L'f');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
d e f  
d e f  
a b c  
```  
  
## <a name="to_array"></a> Set::to_array (STL/CLR)
Copia la secuencia controlada en una nueva matriz.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
cli::array<value_type>^ to_array();  
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve una matriz que contiene la secuencia controlada. Se usa para obtener una copia de la secuencia controlada en forma de matriz.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_to_array.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// copy the container and modify it   
    cli::array<wchar_t>^ a1 = c1.to_array();   
  
    c1.insert(L'd');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display the earlier array copy   
    for each (wchar_t elem in a1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c d  
a b c  
```  

## <a name="upper_bound"></a> Set:: upper_bound (STL/CLR)
Busca el final del intervalo que coincide con una clave especificada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
iterator upper_bound(key_type key);  
```  
  
#### <a name="parameters"></a>Parámetros  
 key  
 Valor de clave que se va a buscar.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro determina el último elemento `X` en la secuencia controlada que tiene una ordenación equivalente a `key`. Si no existe ese elemento, o si `X` es el último elemento de la secuencia controlada, devuelve [Set:: end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`; en caso contrario, devuelve un iterador que designa el primer elemento más allá de `X`. Usa para buscar el final de una secuencia de elementos actualmente en la secuencia controlada que coinciden con una clave especificada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_upper_bound.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",   
        c1.upper_bound(L'x') == c1.end());   
  
    System::Console::WriteLine("*upper_bound(L'a') = {0}",   
        *c1.upper_bound(L'a'));   
    System::Console::WriteLine("*upper_bound(L'b') = {0}",   
        *c1.upper_bound(L'b'));   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
upper_bound(L'x')==end() = True  
*upper_bound(L'a') = b  
*upper_bound(L'b') = c  
```  

## <a name="value_comp"></a> Set:: value_comp (STL/CLR)
Copia al delegado de ordenación para los dos valores de elemento.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
value_compare^ value_comp();  
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve al delegado de ordenación utilizado para ordenar la secuencia controlada. Usa para comparar dos valores de elemento.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_value_comp.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    Myset::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
compare(L'a', L'a') = False  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
```  

## <a name="value_compare"></a> Set:: value_compare (STL/CLR)
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
// cliext_set_value_compare.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    Myset::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
compare(L'a', L'a') = False  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
```  

## <a name="value_type"></a> Set:: value_type (STL/CLR)
El tipo de un elemento.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
  
typedef generic_value value_type;  
  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de `generic_value`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_value_type.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" using value_type   
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in value_type object   
        Myset::value_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="op_neq"></a> operador! = (set) (STL/CLR)
Lista de comparación no es igual.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
template<typename Key>  
    bool operator!=(set<Key>% left,  
        set<Key>% right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 izquierda  
 Contenedor izquierdo que se va a comparar.  
  
 right  
 Contenedor derecho que se va a comparar.  
  
### <a name="remarks"></a>Comentarios  
 Devuelve la función de operador `!(left == right)`. Se usa para comprobar si `left` no está ordenado el mismo que `right` cuando los dos conjuntos son comparado elemento por elemento.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_operator_ne.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] != [a b c] is {0}",   
        c1 != c1);   
    System::Console::WriteLine("[a b c] != [a b d] is {0}",   
        c1 != c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] != [a b c] is False  
[a b c] != [a b d] is True  
```  

## <a name="op_lt"></a> operador&lt; (set) (STL/CLR)
Lista inferior comparación.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
template<typename Key>  
    bool operator<(set<Key>% left,  
        set<Key>% right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 izquierda  
 Contenedor izquierdo que se va a comparar.  
  
 right  
 Contenedor derecho que se va a comparar.  
  
### <a name="remarks"></a>Comentarios  
 El operador función devuelve true si, para la posición más baja `i` que `!(right[i] < left[i])` es también true que `left[i] < right[i]`. De lo contrario, devuelve `left->size() < right->size()` se usa para comprobar si `left` está ordenado antes `right` cuando los dos conjuntos son comparado elemento por elemento.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_operator_lt.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] < [a b c] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[a b c] < [a b d] is {0}",   
        c1 < c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] < [a b c] is False  
[a b c] < [a b d] is True  
```  

## <a name="op_lteq"></a> operador&lt;= (set) (STL/CLR)
Menor o igual lista comparación.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
template<typename Key>  
    bool operator<=(set<Key>% left,  
        set<Key>% right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 izquierda  
 Contenedor izquierdo que se va a comparar.  
  
 right  
 Contenedor derecho que se va a comparar.  
  
### <a name="remarks"></a>Comentarios  
 Devuelve la función de operador `!(right < left)`. Se usa para comprobar si `left` no está ordenado después `right` cuando los dos conjuntos son comparado elemento por elemento.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_operator_le.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] <= [a b c] is {0}",   
        c1 <= c1);   
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",   
        c2 <= c1);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] <= [a b c] is True  
[a b d] <= [a b c] is False  
```  
  
## <a name="op_eq"></a> operador == (set) (STL/CLR)
Lista comparación igual.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
template<typename Key>  
    bool operator==(set<Key>% left,  
        set<Key>% right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 izquierda  
 Contenedor izquierdo que se va a comparar.  
  
 right  
 Contenedor derecho que se va a comparar.  
  
### <a name="remarks"></a>Comentarios  
 La función de operador devuelve true solo si controlan las secuencias de `left` y `right` tienen la misma longitud y, para cada posición `i`, `left[i] ==` `right[i]`. Se usa para comprobar si `left` se ordenan igual `right` cuando los dos conjuntos son comparado elemento por elemento.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_operator_eq.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] == [a b c] is {0}",   
        c1 == c1);   
    System::Console::WriteLine("[a b c] == [a b d] is {0}",   
        c1 == c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] == [a b c] is True  
[a b c] == [a b d] is False  
```  

## <a name="op_gt"></a> operador&gt; (set) (STL/CLR)
Lista es mayor que la comparación.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
template<typename Key>  
    bool operator>(set<Key>% left,  
        set<Key>% right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 izquierda  
 Contenedor izquierdo que se va a comparar.  
  
 right  
 Contenedor derecho que se va a comparar.  
  
### <a name="remarks"></a>Comentarios  
 Devuelve la función de operador `right` `<` `left`. Se usa para comprobar si `left` se ordena después `right` cuando los dos conjuntos son comparado elemento por elemento.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_operator_gt.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] > [a b c] is {0}",   
        c1 > c1);   
    System::Console::WriteLine("[a b d] > [a b c] is {0}",   
        c2 > c1);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] > [a b c] is False  
[a b d] > [a b c] is True  
```  

## <a name="op_gteq"></a> operador&gt;= (set) (STL/CLR)
Comparación igual o mayor de la lista.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
template<typename Key>  
    bool operator>=(set<Key>% left,  
        set<Key>% right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 izquierda  
 Contenedor izquierdo que se va a comparar.  
  
 right  
 Contenedor derecho que se va a comparar.  
  
### <a name="remarks"></a>Comentarios  
 Devuelve la función de operador `!(left < right)`. Se usa para comprobar si `left` no está ordenado antes `right` cuando los dos conjuntos son comparado elemento por elemento.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_operator_ge.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] >= [a b c] is {0}",   
        c1 >= c1);   
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",   
        c1 >= c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] >= [a b c] is True  
[a b c] >= [a b d] is False  
```  