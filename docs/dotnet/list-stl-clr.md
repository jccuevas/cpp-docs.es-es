---
title: list (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::list
- cliext::list::assign
- cliext::list::back
- cliext::list::back_item
- cliext::list::begin
- cliext::list::clear
- cliext::list::const_iterator
- cliext::list::const_reference
- cliext::list::const_reverse_iterator
- cliext::list::difference_type
- cliext::list::empty
- cliext::list::end
- cliext::list::erase
- cliext::list::front
- cliext::list::front_item
- cliext::list::generic_container
- cliext::list::generic_iterator
- cliext::list::generic_reverse_iterator
- cliext::list::generic_value
- cliext::list::insert
- cliext::list::iterator
- cliext::list::list
- cliext::list::merge
- cliext::list::operator=
- cliext::list::pop_back
- cliext::list::pop_front
- cliext::list::push_back
- cliext::list::push_front
- cliext::list::rbegin
- cliext::list::reference
- cliext::list::remove
- cliext::list::remove_if
- cliext::list::rend
- cliext::list::resize
- cliext::list::reverse
- cliext::list::reverse_iterator
- cliext::list::size
- cliext::list::size_type
- cliext::list::sort
- cliext::list::splice
- cliext::list::swap
- cliext::list::to_array
- cliext::list::unique
- cliext::list::value_type
- cliext::operator!=(list)
- cliext::operator<(list)
- cliext::operator<=(list)
- cliext::operator==(list)
- cliext::operator>(list)
- cliext::operator>=(list)
helpviewer_keywords:
- <cliext/list> header [STL/CLR]
- list class [STL/CLR]
- <list> header [STL/CLR]
- assign member [STL/CLR]
- assign member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- erase member [STL/CLR]
- front member [STL/CLR]
- front_item member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- list member [STL/CLR]
- merge member [STL/CLR]
- operator= member [STL/CLR]
- pop_back member [STL/CLR]
- pop_front member [STL/CLR]
- push_back member [STL/CLR]
- push_front member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- remove member [STL/CLR]
- remove_if member [STL/CLR]
- rend member [STL/CLR]
- resize member [STL/CLR]
- reverse member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- sort member [STL/CLR]
- splice member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- unique member [STL/CLR]
- value_type member [STL/CLR]
- operator!=(list) member [STL/CLR]
- operator<(list) member [STL/CLR]
- operator<=(list) member [STL/CLR]
- operator==(list) member [STL/CLR]
- operator>(list) member [STL/CLR]
- operator>=(list) member [STL/CLR]
ms.assetid: a70c45c8-a257-4f6b-8434-b27ff6685bac
ms.openlocfilehash: 7a07f0cc66492c5e0c10c82a7a6971313e13d77b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208564"
---
# <a name="list-stlclr"></a>list (STL/CLR)

La clase de plantilla describe un objeto que controla una secuencia de elementos de longitud variable que tiene acceso bidireccional. La `list` de contenedor se utiliza para administrar una secuencia de elementos como una lista de nodos vinculada bidireccional, cada uno de los cuales almacena un elemento.

En la descripción siguiente, `GValue` es igual que el *valor* a menos que sea un tipo de referencia, en cuyo caso se `Value^`.

## <a name="syntax"></a>Sintaxis

```cpp
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

### <a name="parameters"></a>Parámetros

*Valor*<br/>
Tipo de un elemento de la secuencia controlada.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<cliext (/list >

**Espacio de nombres:** cliext (

## <a name="declarations"></a>Declaraciones

|Definición de tipo|Descripción|
|---------------------|-----------------|
|[list::const_iterator (STL/CLR)](#const_iterator)|El tipo de un iterador constante para la secuencia controlada.|
|[list::const_reference (STL/CLR)](#const_reference)|El tipo de una referencia constante a un elemento.|
|[list::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|El tipo de un iterador invertido constante para la secuencia controlada.|
|[list::difference_type (STL/CLR)](#difference_type)|El tipo de una distancia con signo entre dos elementos.|
|[list::generic_container (STL/CLR)](#generic_container)|Tipo de la interfaz genérica para el contenedor.|
|[list::generic_iterator (STL/CLR)](#generic_iterator)|El tipo de un iterador para la interfaz genérica del contenedor.|
|[list::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|El tipo de un iterador inverso para la interfaz genérica del contenedor.|
|[list::generic_value (STL/CLR)](#generic_value)|Tipo de un elemento de la interfaz genérica para el contenedor.|
|[list::iterator (STL/CLR)](#iterator)|El tipo de un iterador para la secuencia controlada.|
|[list::reference (STL/CLR)](#reference)|El tipo de una referencia a un elemento.|
|[list::reverse_iterator (STL/CLR)](#reverse_iterator)|El tipo de un iterador invertido para la secuencia controlada.|
|[list::size_type (STL/CLR)](#size_type)|El tipo de una distancia con signo entre dos elementos.|
|[list::value_type (STL/CLR)](#value_type)|El tipo de un elemento.|

|Función miembro|Descripción|
|---------------------|-----------------|
|[list::assign (STL/CLR)](#assign)|Reemplaza todos los elementos.|
|[list::back (STL/CLR)](#back)|Obtiene acceso al último elemento.|
|[list::begin (STL/CLR)](#begin)|Designa el principio de la secuencia controlada.|
|[list::clear (STL/CLR)](#clear)|Quita todos los elementos.|
|[list::empty (STL/CLR)](#empty)|Comprueba si no hay ningún elemento presente.|
|[list::end (STL/CLR)](#end)|Designa el final de la secuencia controlada.|
|[list::erase (STL/CLR)](#erase)|Quita los elementos de las posiciones especificadas.|
|[list::front (STL/CLR)](#front)|Obtiene acceso al primer elemento.|
|[list::insert (STL/CLR)](#insert)|Agrega elementos en una posición especificada.|
|[list::list (STL/CLR)](#list)|Construye un objeto contenedor.|
|[list::merge (STL/CLR)](#merge)|Combina dos secuencias controladas ordenadas.|
|[list::pop_back (STL/CLR)](#pop_back)|Quita el último elemento.|
|[list::pop_front (STL/CLR)](#pop_front)|Quita el primer elemento.|
|[list::push_back (STL/CLR)](#push_back)|Agrega un nuevo último elemento.|
|[list::push_front (STL/CLR)](#push_front)|Agrega un nuevo primer elemento.|
|[list::rbegin (STL/CLR)](#rbegin)|Designa el principio de la secuencia controlada inversa.|
|[list::remove (STL/CLR)](#remove)|Quita un elemento con un valor especificado.|
|[list::remove_if (STL/CLR)](#remove_if)|Quita los elementos que superan una prueba especificada.|
|[list::rend (STL/CLR)](#rend)|Designa el final de la secuencia controlada inversa.|
|[list::resize (STL/CLR)](#resize)|Cambia el número de elementos.|
|[list::reverse (STL/CLR)](#reverse)|Invierte la secuencia controlada.|
|[list::size (STL/CLR)](#size)|Cuenta el número de elementos.|
|[list::sort (STL/CLR)](#sort)|Ordena la secuencia controlada.|
|[list::splice (STL/CLR)](#splice)|Vuelve a unir vínculos entre nodos.|
|[list::swap (STL/CLR)](#swap)|Intercambia el contenido de dos contenedores.|
|[list::to_array (STL/CLR)](#to_array)|Copia la secuencia controlada en una nueva matriz.|
|[list::unique (STL/CLR)](#unique)|Quita los elementos adyacentes que superan una prueba especificada.|

|Propiedad|Descripción|
|--------------|-----------------|
|[list::back_item (STL/CLR)](#back_item)|Obtiene acceso al último elemento.|
|[list::front_item (STL/CLR)](#front_item)|Obtiene acceso al primer elemento.|

|Operator|Descripción|
|--------------|-----------------|
|[list::operator= (STL/CLR)](#op_as)|Reemplaza la secuencia controlada.|
|[operator!= (list) (STL/CLR)](#op_neq)|Determina si un objeto `list` no es igual a otro objeto `list`.|
|[operator< (list) (STL/CLR)](#op_lt)|Determina si un objeto `list` es menor que otro objeto `list`.|
|[operator<= (list) (STL/CLR)](#op_lteq)|Determina si un objeto `list` es menor o igual que otro objeto `list`.|
|[operator== (list) (STL/CLR)](#op_eq)|Determina si un objeto `list` es igual a otro objeto `list`.|
|[operator> (list) (STL/CLR)](#op_gt)|Determina si un objeto `list` es mayor que otro objeto `list`.|
|[operator>= (list) (STL/CLR)](#op_gteq)|Determina si un objeto `list` es mayor o igual que otro objeto `list`.|

## <a name="interfaces"></a>Interfaces

|Interfaz|Descripción|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplicar un objeto.|
|<xref:System.Collections.IEnumerable>|Secuencia a través de elementos.|
|<xref:System.Collections.ICollection>|Mantiene el grupo de elementos.|
|<xref:System.Collections.Generic.IEnumerable%601>|Secuencia a través de elementos con tipo.|
|<xref:System.Collections.Generic.ICollection%601>|Mantiene el grupo de elementos con tipo.|
|IList\<valor >|Mantenga el contenedor genérico.|

## <a name="remarks"></a>Observaciones

El objeto asigna y libera almacenamiento para la secuencia que controla como nodos individuales en una lista de vínculos bidireccionales. Reorganiza los elementos modificando los vínculos entre los nodos, nunca copiando el contenido de un nodo en otro. Esto significa que puede insertar y quitar elementos libremente sin molestar a los elementos restantes. Por lo tanto, una lista es una buena candidata para el contenedor subyacente de la cola de clase de plantilla [(STL/CLR)](../dotnet/queue-stl-clr.md) o la pila de clases de plantilla [(STL/CLR)](../dotnet/stack-stl-clr.md).

Un objeto `list` admite iteradores bidireccionales, lo que significa que puede ir a los elementos adyacentes dado un iterador que designa un elemento en la secuencia controlada. Un nodo principal especial corresponde al iterador devuelto por [List:: end (STL/CLR)](../dotnet/list-end-stl-clr.md)`()`. Puede reducir este iterador para llegar al último elemento de la secuencia controlada, si está presente. Puede incrementar un iterador de lista para llegar al nodo principal y, a continuación, se comparará igual que `end()`. Pero no se puede desreferenciar el iterador devuelto por `end()`.

Tenga en cuenta que no puede hacer referencia a un elemento de lista directamente a partir de su posición numérica, que requiere un iterador de acceso aleatorio. Por lo tanto, *no* se puede usar una lista como contenedor subyacente de la clase de plantilla [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md).

Un iterador de lista almacena un identificador en su nodo de lista asociado, que a su vez almacena un identificador en su contenedor asociado. Solo se pueden usar iteradores con sus objetos de contenedor asociados. Un iterador de lista sigue siendo válido, siempre y cuando su nodo de lista asociado esté asociado a alguna lista. Además, un iterador válido es dereferenceable--se puede usar para obtener acceso al valor del elemento que designa, y siempre que no sea igual que `end()`.

Al borrar o quitar un elemento, se llama al destructor para su valor almacenado. Al destruir el contenedor, se borran todos los elementos. Por lo tanto, un contenedor cuyo tipo de elemento es una clase Ref garantiza que ningún elemento durar más el contenedor. Sin embargo, tenga en cuenta que un contenedor de controladores *no destruye sus* elementos.

## <a name="members"></a>Members

## <a name="listassign-stlclr"></a><a name="assign"></a>List:: Assign (STL/CLR)

Reemplaza todos los elementos.

### <a name="syntax"></a>Sintaxis

```cpp
void assign(size_type count, value_type val);
template<typename InIt>
    void assign(InIt first, InIt last);
void assign(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>Parámetros

*count*<br/>
Número de elementos que se van a insertar.

*first*<br/>
Principio del intervalo que se va a insertar.

*last*<br/>
Final del intervalo que se va a insertar.

*right*<br/>
Enumeración que se va a insertar.

*val*<br/>
Valor del elemento que se va a insertar.

### <a name="remarks"></a>Observaciones

La primera función miembro reemplaza la secuencia controlada por una repetición de elementos de *recuento* de valor *Val*. Se usa para rellenar el contenedor con elementos que tienen el mismo valor.

Si `InIt` es un tipo entero, la segunda función miembro se comporta igual que `assign((size_type)first, (value_type)last)`. De lo contrario, reemplaza la secuencia controlada por la secuencia [`first`, `last`). Se usa para convertir la secuencia controlada en una copia otra secuencia.

La tercera función miembro reemplaza la secuencia controlada por la secuencia designada por el *derecho*del enumerador. Se usa para convertir la secuencia controlada en una copia de una secuencia descrita por un enumerador.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_assign.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // assign a repetition of values
    cliext::list<wchar_t> c2;
    c2.assign(6, L'x');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign an iterator range
    cliext::list<wchar_t>::iterator it = c1.end();
    c2.assign(c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign an enumeration
    c2.assign(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
x x x x x x
a b
a b c
```

## <a name="listback-stlclr"></a><a name="back"></a>List:: Back (STL/CLR)

Obtiene acceso al último elemento.

### <a name="syntax"></a>Sintaxis

```cpp
reference back();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve una referencia al último elemento de la secuencia controlada, que no debe estar vacía. Se usa para tener acceso al último elemento, cuando se sabe que existe.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_back.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last item
    System::Console::WriteLine("back() = {0}", c1.back());

    // alter last item and reinspect
    c1.back() = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
back() = c
a b x
```

## <a name="listback_item-stlclr"></a><a name="back_item"></a>List:: back_item (STL/CLR)

Obtiene acceso al último elemento.

### <a name="syntax"></a>Sintaxis

```cpp
property value_type back_item;
```

### <a name="remarks"></a>Observaciones

La propiedad tiene acceso al último elemento de la secuencia controlada, que no debe estar vacío. Se usa para leer o escribir el último elemento, cuando se sabe que existe.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_back_item.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last item
    System::Console::WriteLine("back_item = {0}", c1.back_item);

    // alter last item and reinspect
    c1.back_item = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
back_item = c
a b x
```

## <a name="listbegin-stlclr"></a><a name="begin"></a>List:: Begin (STL/CLR)

Designa el principio de la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
iterator begin();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve un iterador de acceso aleatorio que designa el primer elemento de la secuencia controlada o más allá del final de una secuencia vacía. Se usa para obtener un iterador que designe el principio de la secuencia controlada, indicado por `current`, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_begin.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    cliext::list<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = {0}", *it);
    System::Console::WriteLine("*++begin() = {0}", *++it);

    // alter first two items and reinspect
    *--it = L'x';
    *++it = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*begin() = a
*++begin() = b
x y c
```

## <a name="listclear-stlclr"></a><a name="clear"></a>List:: CLEAR (STL/CLR)

Quita todos los elementos.

### <a name="syntax"></a>Sintaxis

```cpp
void clear();
```

### <a name="remarks"></a>Observaciones

La función miembro llama eficazmente a [List:: Erase (STL/CLR)](../dotnet/list-erase-stl-clr.md)`(` [List:: Begin (STL/CLR)](../dotnet/list-begin-stl-clr.md)`(),` [List:: end (STL/CLR)](../dotnet/list-end-stl-clr.md)`())`. Se utiliza para asegurarse de que la secuencia controlada está vacía.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_clear.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

    // add elements and clear again
    c1.push_back(L'a');
    c1.push_back(L'b');

    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
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

## <a name="listconst_iterator-stlclr"></a><a name="const_iterator"></a>List:: const_iterator (STL/CLR)

El tipo de un iterador constante para la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto de tipo sin especificar `T2` que puede actuar como un iterador de acceso aleatorio constante para la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_const_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    cliext::list<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="listconst_reference-stlclr"></a><a name="const_reference"></a>List:: const_reference (STL/CLR)

El tipo de una referencia constante a un elemento.

### <a name="syntax"></a>Sintaxis

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Observaciones

El tipo describe una referencia constante a un elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_const_reference.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    cliext::list<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        cliext::list<wchar_t>::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="listconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>List:: const_reverse_iterator (STL/CLR)

Tipo de un iterador inverso constante para la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto de tipo sin especificar `T4` que puede actuar como un iterador inverso constante para la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" reversed
    cliext::list<wchar_t>::const_reverse_iterator crit = c1.rbegin();
    cliext::list<wchar_t>::const_reverse_iterator crend = c1.rend();
    for (; crit != crend; ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="listdifference_type-stlclr"></a><a name="difference_type"></a>List::d ifference_type (STL/CLR)

Tipos de una distancia con signo entre dos elementos.

### <a name="syntax"></a>Sintaxis

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Observaciones

El tipo describe un recuento de elementos firmados.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_difference_type.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    cliext::list<wchar_t>::difference_type diff = 0;
    for (cliext::list<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it) ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (cliext::list<wchar_t>::iterator it = c1.end();
        it != c1.begin(); --it) --diff;
    System::Console::WriteLine("begin()-end() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
begin()-end() = -3
```

## <a name="listempty-stlclr"></a><a name="empty"></a>List:: Empty (STL/CLR)

Comprueba si no hay ningún elemento presente.

### <a name="syntax"></a>Sintaxis

```cpp
bool empty();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve true para una secuencia controlada vacía. Es equivalente a [List:: Size (STL/CLR)](../dotnet/list-size-stl-clr.md)`() == 0`. Se usa para probar si la lista está vacía.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_empty.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
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

## <a name="listend-stlclr"></a><a name="end"></a>List:: end (STL/CLR)

Designa el final de la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
iterator end();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve un iterador de acceso aleatorio que apunta inmediatamente después del final de la secuencia controlada. Se usa para obtener un iterador que designe el final de la secuencia controlada. su estado no cambia si cambia la longitud de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_end.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last two items
    cliext::list<wchar_t>::iterator it = c1.end();
    --it;
    System::Console::WriteLine("*-- --end() = {0}", *--it);
    System::Console::WriteLine("*--end() = {0}", *++it);

    // alter first two items and reinspect
    *--it = L'x';
    *++it = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*-- --end() = b
*--end() = c
a x y
```

## <a name="listerase-stlclr"></a><a name="erase"></a>List:: Erase (STL/CLR)

Quita los elementos de las posiciones especificadas.

### <a name="syntax"></a>Sintaxis

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
```

#### <a name="parameters"></a>Parámetros

*first*<br/>
Principio del intervalo que se va a borrar.

*last*<br/>
Final del intervalo que se va a borrar.

*where*<br/>
Elemento que se va a borrar.

### <a name="remarks"></a>Observaciones

La primera función miembro quita el elemento de la secuencia controlada a la que apunta *Where*. Se utiliza para quitar un solo elemento.

La segunda función miembro quita los elementos de la secuencia controlada en el intervalo [`first`, `last`). Se usa para quitar cero o más elementos contiguos.

Ambas funciones miembro devuelven un iterador que designa el primer elemento que permanece más allá de los elementos quitados o [List:: end (STL/CLR)](../dotnet/list-end-stl-clr.md)`()` si no existe ese elemento.

Al borrar elementos, el número de copias de elementos es lineal en el número de elementos entre el final del borrado y el extremo más cercano de la secuencia. (Al borrar uno o varios elementos en cualquier extremo de la secuencia, no se produce ninguna copia del elemento).

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_erase.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // erase an element and reinspect
    System::Console::WriteLine("erase(begin()) = {0}",
        *c1.erase(c1.begin()));

    // add elements and display " b c d e"
    c1.push_back(L'd');
    c1.push_back(L'e');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // erase all but end
    cliext::list<wchar_t>::iterator it = c1.end();
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

## <a name="listfront-stlclr"></a><a name="front"></a>List:: Front (STL/CLR)

Obtiene acceso al primer elemento.

### <a name="syntax"></a>Sintaxis

```cpp
reference front();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve una referencia al primer elemento de la secuencia controlada, que no debe estar vacía. Se usa para leer o escribir el primer elemento, cuando se sabe que existe.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_front.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first item
    System::Console::WriteLine("front() = {0}", c1.front());

    // alter first item and reinspect
    c1.front() = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
front() = a
x b c
```

## <a name="listfront_item-stlclr"></a><a name="front_item"></a>List:: front_item (STL/CLR)

Obtiene acceso al primer elemento.

### <a name="syntax"></a>Sintaxis

```cpp
property value_type front_item;
```

### <a name="remarks"></a>Observaciones

La propiedad tiene acceso al primer elemento de la secuencia controlada, que no debe estar vacío. Se usa para leer o escribir el primer elemento, cuando se sabe que existe.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_front_item.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first item
    System::Console::WriteLine("front_item = {0}", c1.front_item);

    // alter first item and reinspect
    c1.front_item = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
front_item = a
x b c
```

## <a name="listgeneric_container-stlclr"></a><a name="generic_container"></a>List:: generic_container (STL/CLR)

Tipo de la interfaz genérica para el contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Microsoft::VisualC::StlClr::
    IList<generic_value>
    generic_container;
```

### <a name="remarks"></a>Observaciones

El tipo describe la interfaz genérica para esta clase de contenedor de plantillas.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_generic_container.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->insert(gc1->end(), L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify original and display generic
    c1.push_back(L'e');

    System::Collections::IEnumerator^ enum1 =
        gc1->GetEnumerator();
    while (enum1->MoveNext())
        System::Console::Write("{0} ", enum1->Current);
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

## <a name="listgeneric_iterator-stlclr"></a><a name="generic_iterator"></a>List:: generic_iterator (STL/CLR)

Tipo de un iterador que se va a usar con la interfaz genérica del contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerBidirectionalIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe un iterador genérico que se puede usar con la interfaz genérica para esta clase de contenedor de plantillas.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_generic_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::list<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::list<wchar_t>::generic_value gcval = *gcit;
    *++gcit = gcval;
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a a c
```

## <a name="listgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>List:: generic_reverse_iterator (STL/CLR)

Tipo de un iterador inverso que se va a usar con la interfaz genérica del contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseBidirectionalIterator<generic_value> generic_reverse_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe un iterador inverso genérico que se puede usar con la interfaz genérica para esta clase de contenedor de plantillas.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::list<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();
    cliext::list<wchar_t>::generic_value gcval = *gcit;
    *++gcit = gcval;
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a c c
```

## <a name="listgeneric_value-stlclr"></a><a name="generic_value"></a>List:: generic_value (STL/CLR)

Tipo de un elemento que se va a usar con la interfaz genérica del contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto de tipo `GValue` que describe el valor del elemento almacenado que se va a usar con la interfaz genérica para esta clase de contenedor de plantillas.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_generic_value.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::list<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::list<wchar_t>::generic_value gcval = *gcit;
    *++gcit = gcval;
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a a c
```

## <a name="listinsert-stlclr"></a><a name="insert"></a>List:: Insert (STL/CLR)

Agrega elementos en una posición especificada.

### <a name="syntax"></a>Sintaxis

```cpp
iterator insert(iterator where, value_type val);
void insert(iterator where, size_type count, value_type val);
template<typename InIt>
    void insert(iterator where, InIt first, InIt last);
void insert(iterator where,
    System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>Parámetros

*count*<br/>
Número de elementos que se van a insertar.

*first*<br/>
Principio del intervalo que se va a insertar.

*last*<br/>
Final del intervalo que se va a insertar.

*right*<br/>
Enumeración que se va a insertar.

*val*<br/>
Valor del elemento que se va a insertar.

*where*<br/>
Donde en el contenedor se insertará antes.

### <a name="remarks"></a>Observaciones

Cada una de las funciones miembro inserta, antes del elemento *al que apunta en la* secuencia controlada, una secuencia especificada por los operandos restantes.

La primera función miembro inserta un elemento con el valor *Val* y devuelve un iterador que designa el elemento recién insertado. Se usa para insertar un solo elemento antes de un lugar designado por un iterador.

La segunda función miembro inserta una repetición de elementos *Count* de Value *Val*. Se usa para insertar cero o más elementos contiguos que son todas las copias del mismo valor.

Si `InIt` es un tipo entero, la tercera función miembro se comporta igual que `insert(where, (size_type)first, (value_type)last)`. De lo contrario, inserta la secuencia [`first`, `last`). Se usa para insertar cero o más elementos contiguos copiados de otra secuencia.

La cuarta función miembro inserta la secuencia designada por la *derecha*. Se usa para insertar una secuencia descrita por un enumerador.

Al insertar un solo elemento, el número de copias de elementos es lineal en el número de elementos entre el punto de inserción y el extremo más cercano de la secuencia. (Al insertar uno o varios elementos en cualquier extremo de la secuencia, no se produce ninguna copia del elemento). Si `InIt` es un iterador de entrada, la tercera función miembro realiza una inserción única para cada elemento de la secuencia. De lo contrario, al insertar elementos `N`, el número de copias de elementos es lineal en `N` más el número de elementos entre el punto de inserción y el extremo más cercano de la secuencia.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_insert.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value using iterator
    cliext::list<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",
        *c1.insert(++it, L'x'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a repetition of values
    cliext::list<wchar_t> c2;
    c2.insert(c2.begin(), 2, L'y');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an iterator range
    it = c1.end();
    c2.insert(c2.end(), c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an enumeration
    c2.insert(c2.begin(),   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value using index
    it = c2.begin();
    ++it, ++it, ++it;
    c2.insert(it, L'z');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
    }
```

```Output
a b c
insert(begin()+1, L'x') = x
a x b c
y y
y y a x b
a x b c y y a x b
```

## <a name="listiterator-stlclr"></a><a name="iterator"></a>List:: iterator (STL/CLR)

El tipo de un iterador para la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto de tipo sin especificar `T1` que puede actuar como un iterador de acceso aleatorio para la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    cliext::list<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();

    // alter first element and redisplay
    it = c1.begin();
    *it = L'x';
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
x b c
```

## <a name="listlist-stlclr"></a><a name="list"></a>List:: List (STL/CLR)

Construye un objeto contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
list();
list(list<Value>% right);
list(list<Value>^ right);
explicit list(size_type count);
list(size_type count, value_type val);
template<typename InIt>
    list(InIt first, InIt last);
list(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>Parámetros

*count*<br/>
Número de elementos que se van a insertar.

*first*<br/>
Principio del intervalo que se va a insertar.

*last*<br/>
Final del intervalo que se va a insertar.

*right*<br/>
Objeto o intervalo que se va a insertar.

*val*<br/>
Valor del elemento que se va a insertar.

### <a name="remarks"></a>Observaciones

El constructor:

`list();`

Inicializa la secuencia controlada sin elementos. Se usa para especificar una secuencia controlada inicial vacía.

El constructor:

`list(list<Value>% right);`

Inicializa la secuencia controlada con la secuencia [`right.begin()`, `right.end()`). Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de lista de la *derecha*.

El constructor:

`list(list<Value>^ right);`

Inicializa la secuencia controlada con la secuencia [`right->begin()`, `right->end()`). Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de lista cuyo identificador es *correcto*.

El constructor:

`explicit list(size_type count);`

Inicializa la secuencia controlada con elementos de *recuento* cada uno con el valor `value_type()`. Se usa para rellenar el contenedor con los elementos que tienen el valor predeterminado.

El constructor:

`list(size_type count, value_type val);`

Inicializa la secuencia controlada con elementos de *recuento* cada uno con valor *Val*. Se usa para rellenar el contenedor con elementos que tienen el mismo valor.

El constructor:

`template<typename InIt>`

`list(InIt first, InIt last);`

Inicializa la secuencia controlada con la secuencia [`first`, `last`). Se usa para convertir la secuencia controlada en una copia de otra secuencia.

El constructor:

`list(System::Collections::Generic::IEnumerable<Value>^ right);`

Inicializa la secuencia controlada con la secuencia designada por el *derecho*del enumerador. Se usa para convertir la secuencia controlada en una copia de otra secuencia descrita por un enumerador.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_construct.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
// construct an empty container
    cliext::list<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    // construct with a repetition of default values
    cliext::list<wchar_t> c2(3);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

    // construct with a repetition of values
    cliext::list<wchar_t> c3(6, L'x');
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range
    cliext::list<wchar_t>::iterator it = c3.end();
    cliext::list<wchar_t> c4(c3.begin(), --it);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration
    cliext::list<wchar_t> c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    cliext::list<wchar_t> c7(c3);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying a container handle
    cliext::list<wchar_t> c8(%c3);
    for each (wchar_t elem in c8)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
    }
```

```Output
size() = 0
0 0 0
x x x x x x
x x x x x
x x x x x x
x x x x x x
x x x x x x
```

## <a name="listmerge-stlclr"></a><a name="merge"></a>List:: Merge (STL/CLR)

Combina dos secuencias controladas ordenadas.

### <a name="syntax"></a>Sintaxis

```cpp
void merge(list<Value>% right);
template<typename Pred2>
    void merge(list<Value>% right, Pred2 pred);
```

#### <a name="parameters"></a>Parámetros

*pronostica*<br/>
Comparador para pares de elementos.

*right*<br/>
Contenedor en el que se va a combinar.

### <a name="remarks"></a>Observaciones

La primera función miembro quita todos los elementos de la secuencia controlada por la *derecha* y los inserta en la secuencia controlada. Las dos secuencias deben estar ordenadas previamente por `operator<`--los elementos no deben disminuir en el valor a medida que avanza por cualquier secuencia. La secuencia resultante también se ordena por `operator<`. Esta función miembro se usa para combinar dos secuencias que aumentan el valor en una secuencia que también aumenta de valor.

La segunda función miembro se comporta igual que la primera, salvo que las secuencias se ordenan por `pred` -- `pred(X, Y)` debe ser false para cualquier elemento `X` que siga el elemento `Y` de la secuencia. Se usa para combinar dos secuencias ordenadas por una función de predicado o un delegado que se especifique.

Ambas funciones realizan una combinación estable: no se invierte ningún par de elementos en ninguna de las secuencias controladas originales en la secuencia controlada resultante. Además, si un par de elementos `X` y `Y` en la secuencia controlada resultante tiene una ordenación equivalente (`!(X < Y) && !(X < Y)`), un elemento de la secuencia controlada original aparece delante de un elemento de la secuencia controlada por la *derecha*.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_merge.cpp
// compile with: /clr
#include <cliext/list>

typedef cliext::list<wchar_t> Mylist;
int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'c');
    c1.push_back(L'e');

    // display initial contents " a c e"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    cliext::list<wchar_t> c2;
    c2.push_back(L'b');
    c2.push_back(L'd');
    c2.push_back(L'f');

    // display initial contents " b d f"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // merge and display
    cliext::list<wchar_t> c3(c1);
    c3.merge(c2);
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("c2.size() = {0}", c2.size());

    // sort descending, merge descending, and redisplay
    c1.sort(cliext::greater<wchar_t>());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    c3.sort(cliext::greater<wchar_t>());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    c3.merge(c1, cliext::greater<wchar_t>());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("c1.size() = {0}", c1.size());
    return (0);
    }
```

```Output
a c e
b d f
a b c d e f
c2.size() = 0
e c a
f e d c b a
f e e d c c b a a
c1.size() = 0
```

## <a name="listoperator-stlclr"></a><a name="op_as"></a>List:: Operator = (STL/CLR)

Reemplaza la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```
list<Value>% operator=(list<Value>% right);
```

#### <a name="parameters"></a>Parámetros

*right*<br/>
Contenedor que se va a copiar.

### <a name="remarks"></a>Observaciones

El operador miembro copia *directamente* en el objeto y, a continuación, devuelve `*this`. Se usa para reemplazar la secuencia controlada por una copia de la secuencia controlada a la *derecha*.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_operator_as.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2 = c1;
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="listpop_back-stlclr"></a><a name="pop_back"></a>List::p op_back (STL/CLR)

Quita el último elemento.

### <a name="syntax"></a>Sintaxis

```cpp
void pop_back();
```

### <a name="remarks"></a>Observaciones

La función miembro quita el último elemento de la secuencia controlada, que no debe estar vacío. Se usa para acortar la lista en un elemento de la parte posterior.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_pop_back.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // pop an element and redisplay
    c1.pop_back();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b
```

## <a name="listpop_front-stlclr"></a><a name="pop_front"></a>List::p op_front (STL/CLR)

Quita el primer elemento.

### <a name="syntax"></a>Sintaxis

```cpp
void pop_front();
```

### <a name="remarks"></a>Observaciones

La función miembro quita el primer elemento de la secuencia controlada, que no debe estar vacío. Se usa para acortar la lista en un elemento en primer plano.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_pop_front.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // pop an element and redisplay
    c1.pop_front();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
b c
```

## <a name="listpush_back-stlclr"></a><a name="push_back"></a>List::p ush_back (STL/CLR)

Agrega un nuevo último elemento.

### <a name="syntax"></a>Sintaxis

```cpp
void push_back(value_type val);
```

### <a name="remarks"></a>Observaciones

La función miembro inserta un elemento con el valor `val` al final de la secuencia controlada. Se usa para anexar otro elemento a la lista.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_push_back.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="listpush_front-stlclr"></a><a name="push_front"></a>List::p ush_front (STL/CLR)

Agrega un nuevo primer elemento.

### <a name="syntax"></a>Sintaxis

```cpp
void push_front(value_type val);
```

### <a name="remarks"></a>Observaciones

La función miembro inserta un elemento con el valor `val` al principio de la secuencia controlada. Se usa para anteponer otro elemento a la lista.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_push_front.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_front(L'a');
    c1.push_front(L'b');
    c1.push_front(L'c');

    // display contents " c b a"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="listrbegin-stlclr"></a><a name="rbegin"></a>List:: rbegin (STL/CLR)

Designa el principio de la secuencia controlada inversa.

### <a name="syntax"></a>Sintaxis

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve un iterador inverso que designa el último elemento de la secuencia controlada o justo después del principio de una secuencia vacía. Por lo tanto, designa el parámetro `beginning` de la secuencia inversa. Se usa para obtener un iterador que designe el principio de la secuencia controlada mostrada en orden inverso, indicado por `current`, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_rbegin.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    cliext::list<wchar_t>::reverse_iterator rit = c1.rbegin();
    System::Console::WriteLine("*rbegin() = {0}", *rit);
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);

    // alter first two items and reinspect
    *--rit = L'x';
    *++rit = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*rbegin() = c
*++rbegin() = b
a y x
```

## <a name="listreference-stlclr"></a><a name="reference"></a>List:: Reference (STL/CLR)

El tipo de una referencia a un elemento.

### <a name="syntax"></a>Sintaxis

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Observaciones

El tipo describe una referencia a un elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_reference.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    cliext::list<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::list<wchar_t>::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();

    // modify contents " a b c"
    for (it = c1.begin(); it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::list<wchar_t>::reference ref = *it;

        ref += (wchar_t)(L'A' - L'a');
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
A B C
```

## <a name="listremove-stlclr"></a><a name="remove"></a>List:: Remove (STL/CLR)

Quita un elemento con un valor especificado.

### <a name="syntax"></a>Sintaxis

```cpp
void remove(value_type val);
```

#### <a name="parameters"></a>Parámetros

*val*<br/>
Valor del elemento que se va a quitar.

### <a name="remarks"></a>Observaciones

La función miembro quita un elemento de la secuencia controlada para la que `((System::Object^)val)->Equals((System::Object^)x)` es true (si existe). Se utiliza para borrar un elemento arbitrario con el valor especificado.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_remove.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // fail to remove and redisplay
    c1.remove(L'A');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // remove and redisplay
    c1.remove(L'b');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a c
```

## <a name="listremove_if-stlclr"></a><a name="remove_if"></a>List:: remove_if (STL/CLR)

Quita los elementos que superan una prueba especificada.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Pred1>
    void remove_if(Pred1 pred);
```

#### <a name="parameters"></a>Parámetros

*pronostica*<br/>
Comprueba los elementos que se van a quitar.

### <a name="remarks"></a>Observaciones

La función miembro quita de la secuencia controlada (borra) cada elemento `X` para el que `pred(X)` es true. Se usa para quitar todos los elementos que cumplen una condición especificada como función o delegado.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_remove_if.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'b');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b b b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // fail to remove and redisplay
    c1.remove_if(cliext::binder2nd<cliext::equal_to<wchar_t> >(
        cliext::equal_to<wchar_t>(), L'd'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // remove and redisplay
    c1.remove_if(cliext::binder2nd<cliext::not_equal_to<wchar_t> >(
        cliext::not_equal_to<wchar_t>(), L'b'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b b b c
a b b b c
b b b
```

## <a name="listrend-stlclr"></a><a name="rend"></a>List:: Rend (STL/CLR)

Designa el final de la secuencia controlada inversa.

### <a name="syntax"></a>Sintaxis

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve un iterador inverso que apunta inmediatamente después del principio de la secuencia controlada. Por lo tanto, designa el parámetro `end` de la secuencia inversa. Se usa para obtener un iterador que designe el final de la secuencia controlada mostrada en orden inverso, indicado por `current`, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_rend.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    cliext::list<wchar_t>::reverse_iterator rit = c1.rend();
    --rit;
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);
    System::Console::WriteLine("*--rend() = {0}", *++rit);

    // alter first two items and reinspect
    *--rit = L'x';
    *++rit = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*-- --rend() = b
*--rend() = a
y x c
```

## <a name="listresize-stlclr"></a><a name="resize"></a>List:: Resize (STL/CLR)

Cambia el número de elementos.

### <a name="syntax"></a>Sintaxis

```cpp
void resize(size_type new_size);
void resize(size_type new_size, value_type val);
```

#### <a name="parameters"></a>Parámetros

*new_size*<br/>
Nuevo tamaño de la secuencia controlada.

*val*<br/>
Valor del elemento padding.

### <a name="remarks"></a>Observaciones

Las funciones miembro garantizan que [List:: Size (STL/CLR)](../dotnet/list-size-stl-clr.md)`()` en adelante devuelva *NEW_SIZE*. Si debe hacer que la secuencia controlada sea más larga, la primera función miembro anexa elementos con el valor `value_type()`, mientras que la segunda función miembro anexa elementos con el valor *Val*. Para que la secuencia controlada sea más corta, ambas funciones miembro borran eficazmente el último elemento [List:: Size (STL/CLR)](../dotnet/list-size-stl-clr.md)`() -` `new_size` veces. Se usa para asegurarse de que la secuencia controlada tiene el tamaño *NEW_SIZE*, ya sea recortando o rellenando la secuencia controlada actual.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_resize.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
// construct an empty container and pad with default values
    cliext::list<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());
    c1.resize(4);
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

    // resize to empty
    c1.resize(0);
    System::Console::WriteLine("size() = {0}", c1.size());

    // resize and pad
    c1.resize(5, L'x');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
0 0 0 0
size() = 0
x x x x x
```

## <a name="listreverse-stlclr"></a><a name="reverse"></a>List:: REVERSE (STL/CLR)

Invierte la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
void reverse();
```

### <a name="remarks"></a>Observaciones

La función miembro invierte el orden de todos los elementos de la secuencia controlada. Se utiliza para reflejar una lista de elementos.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_reverse.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // reverse and redisplay
    c1.reverse();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
c b a
```

## <a name="listreverse_iterator-stlclr"></a><a name="reverse_iterator"></a>List:: reverse_iterator (STL/CLR)

El tipo de un iterador invertido para la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto de tipo sin especificar `T3` que puede actuar como iterador inverso para la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_reverse_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" reversed
    cliext::list<wchar_t>::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();

    // alter first element and redisplay
    rit = c1.rbegin();
    *rit = L'x';
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
x b a
```

## <a name="listsize-stlclr"></a><a name="size"></a>List:: Size (STL/CLR)

Cuenta el número de elementos.

### <a name="syntax"></a>Sintaxis

```cpp
size_type size();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve la longitud de la secuencia controlada. Se utiliza para determinar el número de elementos que hay actualmente en la secuencia controlada. Si todo lo que le interesa es si la secuencia tiene un tamaño distinto de cero, vea [List:: Empty (STL/CLR)](../dotnet/list-empty-stl-clr.md)`()`.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_size.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

    // add elements and clear again
    c1.push_back(L'a');
    c1.push_back(L'b');
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

## <a name="listsize_type-stlclr"></a><a name="size_type"></a>List:: size_type (STL/CLR)

El tipo de una distancia con signo entre dos elementos.

### <a name="syntax"></a>Sintaxis

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Observaciones

El tipo describe un recuento de elementos no negativos.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_size_type.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    cliext::list<wchar_t>::size_type diff = 0;
    for (cliext::list<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="listsort-stlclr"></a><a name="sort"></a>List:: sort (STL/CLR)

Ordena la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
void sort();
template<typename Pred2>
    void sort(Pred2 pred);
```

#### <a name="parameters"></a>Parámetros

*pronostica*<br/>
Comparador para pares de elementos.

### <a name="remarks"></a>Observaciones

La primera función miembro reorganiza los elementos de la secuencia controlada para que se ordenen por `operator<`--los elementos no disminuyen en el valor a medida que avanza por la secuencia. Esta función miembro se usa para ordenar la secuencia en orden ascendente.

La segunda función miembro se comporta igual que la primera, salvo que la secuencia se ordena por `pred` -- `pred(X, Y)` es false para cualquier elemento `X` que sigue al elemento `Y` en la secuencia resultante. Se usa para ordenar la secuencia en el orden especificado por una función de predicado o un delegado.

Ambas funciones realizan una ordenación estable: no se invierte ningún par de elementos de la secuencia controlada original en la secuencia controlada resultante.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_sort.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // sort descending and redisplay
    c1.sort(cliext::greater<wchar_t>());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // sort ascending and redisplay
    c1.sort();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
c b a
a b c
```

## <a name="listsplice-stlclr"></a><a name="splice"></a>List:: Splice (STL/CLR)

Reunir vínculos entre nodos.

### <a name="syntax"></a>Sintaxis

```cpp
void splice(iterator where, list<Value>% right);
void splice(iterator where, list<Value>% right,
    iterator first);
void splice(iterator where, list<Value>% right,
    iterator first, iterator last);
```

#### <a name="parameters"></a>Parámetros

*first*<br/>
Principio del intervalo que se va a unir.

*last*<br/>
Final del intervalo que se va a unir.

*right*<br/>
Contenedor del que se va a unir.

*where*<br/>
Donde en el contenedor se va a insertar antes.

### <a name="remarks"></a>Observaciones

La primera función miembro inserta la secuencia controlada por *justo* delante del elemento de la secuencia controlada a *la que apunta.* También quita todos los elementos de la *derecha*. (`%right` no debe ser igual `this`). Se usa para unir una lista a otra.

La segunda función miembro quita el elemento al que apunta *primero* en la secuencia controlada por la *derecha* y lo inserta delante del elemento de la secuencia controlada a *la que apunta.* (Si `where` `==` `first` `||` `where` `== ++first`, no se produce ningún cambio). Se usa para unir un solo elemento de una lista en otro.

La tercera función miembro inserta el subintervalo designado por [`first`, `last`) de la secuencia controlada por *justo* delante del elemento de la secuencia controlada a *la que apunta.* También quita el subintervalo original de la secuencia controlada por la *derecha*. (Si `right` `==` `this`, el intervalo [`first`, `last`) no debe incluir el elemento al que apunta *Where*. Se usa para unir una subsecuencia de cero o más elementos de una lista a otra.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_splice.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // splice to a new list
    cliext::list<wchar_t> c2;
    c2.splice(c2.begin(), c1);
    System::Console::WriteLine("c1.size() = {0}", c1.size());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // return one element
    c1.splice(c1.end(), c2, c2.begin());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // return remaining elements
    c1.splice(c1.begin(), c2, c2.begin(), c2.end());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("c2.size() = {0}", c2.size());
    return (0);
    }
```

```Output
a b c
c1.size() = 0
a b c
a
b c
b c a
c2.size() = 0
```

## <a name="listswap-stlclr"></a><a name="swap"></a>List:: swap (STL/CLR)

Intercambia el contenido de dos contenedores.

### <a name="syntax"></a>Sintaxis

```cpp
void swap(list<Value>% right);
```

#### <a name="parameters"></a>Parámetros

*right*<br/>
Contenedor con el que se va a intercambiar el contenido.

### <a name="remarks"></a>Observaciones

La función miembro intercambia las secuencias controladas entre `*this` y *right*. Lo hace en tiempo constante y no inicia ninguna excepción. Se usa como una forma rápida de intercambiar el contenido de dos contenedores.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_swap.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    cliext::list<wchar_t> c2(5, L'x');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // swap and redisplay
    c1.swap(c2);
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
x x x x x
x x x x x
a b c
```

## <a name="listto_array-stlclr"></a><a name="to_array"></a>List:: to_array (STL/CLR)

Copia la secuencia controlada en una nueva matriz.

### <a name="syntax"></a>Sintaxis

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve una matriz que contiene la secuencia controlada. Se utiliza para obtener una copia de la secuencia controlada en forma de matriz.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_to_array.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // copy the container and modify it
    cli::array<wchar_t>^ a1 = c1.to_array();

    c1.push_back(L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display the earlier array copy
    for each (wchar_t elem in a1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c d
a b c
```

## <a name="listunique-stlclr"></a><a name="unique"></a>List:: Unique (STL/CLR)

Quita los elementos adyacentes que superan una prueba especificada.

### <a name="syntax"></a>Sintaxis

```cpp
void unique();
template<typename Pred2>
    void unique(Pred2 pred);
```

#### <a name="parameters"></a>Parámetros

*pronostica*<br/>
Comparador para pares de elementos.

### <a name="remarks"></a>Observaciones

La primera función miembro quita de la secuencia controlada (borra) todos los elementos que se comparan igual que el elemento anterior (si el elemento `X` precede al elemento `Y` y `X == Y`, la función miembro quita `Y`. Se usa para quitar todos los elementos, excepto una copia, de cada subsecuencia de elementos adyacentes que se comparan igual. Tenga en cuenta que si la secuencia controlada está ordenada, por ejemplo llamando a [List:: sort (STL/CLR)](../dotnet/list-sort-stl-clr.md)`()`, la función miembro deja solo elementos con valores únicos. (Por lo tanto, el nombre).

La segunda función miembro se comporta igual que la primera, salvo que quita cada elemento `Y` siguiente a un elemento `X` para el que `pred(X, Y)`. Se usa para quitar todas las copias de cada subsecuencia de elementos adyacentes que cumplan una función de predicado o un delegado que se especifiquen. Tenga en cuenta que si la secuencia controlada está ordenada, por ejemplo llamando a `sort(pred)`, la función miembro deja solo los elementos que no tienen una ordenación equivalente con otros elementos.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_unique.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display contents after unique
    cliext::list<wchar_t> c2(c1);
    c2.unique();
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display contents after unique(not_equal_to)
    c2 = c1;
    c2.unique(cliext::not_equal_to<wchar_t>());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a a b c
a b c
a a
```

## <a name="listvalue_type-stlclr"></a><a name="value_type"></a>List:: value_type (STL/CLR)

El tipo de un elemento.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del *valor*del parámetro de plantilla.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_value_type.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" using value_type
    for (cliext::list<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it)
        {   // store element in value_type object
        cliext::list<wchar_t>::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="operator-list-stlclr"></a><a name="op_neq"></a>Operator! = (list) (STL/CLR)

La comparación de la lista no es igual.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value>
    bool operator!=(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Contenedor izquierdo que se va a comparar.

*right*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Observaciones

La función de operador devuelve `!(left == right)`. Se usa para probar si la *izquierda* no se ordena igual que la *derecha* cuando las dos listas se comparan por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_operator_ne.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
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

## <a name="operatorlt-list-stlclr"></a><a name="op_lt"></a>Operator&lt; (list) (STL/CLR)

Lista de comparación inferior a.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value>
    bool operator<(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Contenedor izquierdo que se va a comparar.

*right*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Observaciones

La función de operador devuelve true si, para la posición más baja `i` para la que `!(right[i] < left[i])` también es true que `left[i] < right[i]`. De lo contrario, devuelve `left->size() < right->size()` se usa para probar si la *izquierda* está ordenada antes de la *derecha* cuando las dos listas se comparan por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_operator_lt.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
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

## <a name="operatorlt-list-stlclr"></a><a name="op_lteq"></a>operador&lt;= (lista) (STL/CLR)

Lista de comparación menor o igual que.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value>
    bool operator<=(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Contenedor izquierdo que se va a comparar.

*right*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Observaciones

La función de operador devuelve `!(right < left)`. Se usa para comprobar si la *izquierda* no se ordena después de la *derecha* cuando se comparan las dos listas elemento a elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_operator_le.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
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

## <a name="operator-list-stlclr"></a><a name="op_eq"></a>operador = = (lista) (STL/CLR)

Enumera la comparación de igualdad.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value>
    bool operator==(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Contenedor izquierdo que se va a comparar.

*right*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Observaciones

La función de operador devuelve true solo si las secuencias controladas por *left* y *right* tienen la misma longitud y, para cada posición `i`, `left[i] ==` `right[i]`. Se usa para probar si la *izquierda* se ordena igual que la *derecha* cuando se comparan las dos listas elemento a elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_operator_eq.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
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

## <a name="operatorgt-list-stlclr"></a><a name="op_gt"></a>Operator&gt; (list) (STL/CLR)

Lista de comparación mayor que.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value>
    bool operator>(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Contenedor izquierdo que se va a comparar.

*right*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Observaciones

La función de operador devuelve `right` `left`de `<`. Se usa para probar si la *izquierda* se ordena después de la *derecha* cuando se comparan las dos listas elemento a elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_operator_gt.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
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

## <a name="operatorgt-list-stlclr"></a><a name="op_gteq"></a>operador&gt;= (lista) (STL/CLR)

Lista de comparación mayor o igual que.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value>
    bool operator>=(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Contenedor izquierdo que se va a comparar.

*right*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Observaciones

La función de operador devuelve `!(left` `right)`de `<`. Se usa para probar si la *izquierda* no está ordenada antes de la *derecha* cuando se comparan las dos listas elemento a elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_list_operator_ge.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
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
