---
title: vector (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::vector
- cliext::vector::assign
- cliext::vector::at
- cliext::vector::back
- cliext::vector::back_item
- cliext::vector::begin
- cliext::vector::capacity
- cliext::vector::clear
- cliext::vector::const_iterator
- cliext::vector::const_reference
- cliext::vector::const_reverse_iterator
- cliext::vector::difference_type
- cliext::vector::empty
- cliext::vector::end
- cliext::vector::erase
- cliext::vector::front
- cliext::vector::front_item
- cliext::vector::generic_container
- cliext::vector::generic_iterator
- cliext::vector::generic_reverse_iterator
- cliext::vector::generic_value
- cliext::vector::insert
- cliext::vector::iterator
- cliext::vector::operator=
- cliext::vector::operator
- cliext::vector::pop_back
- cliext::vector::push_back
- cliext::vector::rbegin
- cliext::vector::reference
- cliext::vector::rend
- cliext::vector::reserve
- cliext::vector::resize
- cliext::vector::reverse_iterator
- cliext::vector::size
- cliext::vector::size_type
- cliext::vector::swap
- cliext::vector::to_array
- cliext::vector::value_type
- cliext::vector::vector
helpviewer_keywords:
- vector class [STL/CLR]
- <cliext/vector> header [STL/CLR]
- <vector> header [STL/CLR]
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> (vector) member [STL/CLR]
- operator>= member [STL/CLR]
- assign member [STL/CLR]
- at member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
- capacity member [STL/CLR]
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
- operator= member [STL/CLR]
- operator member [STL/CLR]
- pop_back member [STL/CLR]
- push_back member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- reserve member [STL/CLR]
- resize member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- value_type member [STL/CLR]
- vector member [STL/CLR]
ms.assetid: f90060d5-097a-4e9d-9a26-a634b5b9c6c2
ms.openlocfilehash: c6a001797e90bd7381358abb16612926442e8d9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371821"
---
# <a name="vector-stlclr"></a>vector (STL/CLR)

La clase de plantilla describe un objeto que controla una secuencia de longitud variable de elementos que tiene acceso aleatorio. Utilice el `vector` contenedor para administrar una secuencia de elementos como un bloque contiguo de almacenamiento. El bloque se implementa como una matriz que crece a petición.

En la descripción siguiente, `GValue` es lo mismo que *Value* a menos `Value^`que este último sea un tipo ref, en cuyo caso es .

## <a name="syntax"></a>Sintaxis

```cpp
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

### <a name="parameters"></a>Parámetros

*Valor*<br/>
Tipo de un elemento de la secuencia controlada.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<cliext/vector>

**Espacio de nombres:** cliext

## <a name="declarations"></a>Declaraciones

|Definición de tipo|Descripción|
|---------------------|-----------------|
|[vector::const_iterator (STL/CLR)](#const_iterator)|El tipo de un iterador constante para la secuencia controlada.|
|[vector::const_reference (STL/CLR)](#const_reference)|El tipo de una referencia constante a un elemento.|
|[vector::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|El tipo de un iterador invertido constante para la secuencia controlada.|
|[vector::difference_type (STL/CLR)](#difference_type)|El tipo de una distancia con signo entre dos elementos.|
|[vector::generic_container (STL/CLR)](#generic_container)|El tipo de la interfaz genérica para el contenedor.|
|[vector::generic_iterator (STL/CLR)](#generic_iterator)|El tipo de un iterador para la interfaz genérica para el contenedor.|
|[vector::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|El tipo de un iterador inverso para la interfaz genérica para el contenedor.|
|[vector::generic_value (STL/CLR)](#generic_value)|El tipo de un elemento para la interfaz genérica para el contenedor.|
|[vector::iterator (STL/CLR)](#iterator)|El tipo de un iterador para la secuencia controlada.|
|[vector::reference (STL/CLR)](#reference)|El tipo de una referencia a un elemento.|
|[vector::reverse_iterator (STL/CLR)](#reverse_iterator)|El tipo de un iterador invertido para la secuencia controlada.|
|[vector::size_type (STL/CLR)](#size_type)|El tipo de una distancia con signo entre dos elementos.|
|[vector::value_type (STL/CLR)](#value_type)|El tipo de un elemento.|

|Función miembro|Descripción|
|---------------------|-----------------|
|[vector::assign (STL/CLR)](#assign)|Reemplaza todos los elementos.|
|[vector::at (STL/CLR)](#at)|Obtiene acceso a un elemento en una posición especificada.|
|[vector::back (STL/CLR)](#back)|Obtiene acceso al último elemento.|
|[vector::begin (STL/CLR)](#begin)|Designa el principio de la secuencia controlada.|
|[vector::capacity (STL/CLR)](#capacity)|Notifica el tamaño de almacenamiento asignado del contenedor.|
|[vector::clear (STL/CLR)](#clear)|Quita todos los elementos.|
|[vector::empty (STL/CLR)](#empty)|Comprueba si no hay ningún elemento presente.|
|[vector::end (STL/CLR)](#end)|Designa el final de la secuencia controlada.|
|[vector::erase (STL/CLR)](#erase)|Quita los elementos de las posiciones especificadas.|
|[vector::front (STL/CLR)](#front)|Obtiene acceso al primer elemento.|
|[vector::insert (STL/CLR)](#insert)|Agrega elementos en una posición especificada.|
|[vector::pop_back (STL/CLR)](#pop_back)|Quita el último elemento.|
|[vector::push_back (STL/CLR)](#push_back)|Agrega un nuevo último elemento.|
|[vector::rbegin (STL/CLR)](#rbegin)|Designa el principio de la secuencia controlada inversa.|
|[vector::rend (STL/CLR)](#rend)|Designa el final de la secuencia controlada inversa.|
|[vector::reserve (STL/CLR)](#reserve)|Garantiza una capacidad de crecimiento mínima para el contenedor.|
|[vector::resize (STL/CLR)](#resize)|Cambia el número de elementos.|
|[vector::size (STL/CLR)](#size)|Cuenta el número de elementos.|
|[vector::swap (STL/CLR)](#swap)|Intercambia el contenido de dos contenedores.|
|[vector::to_array (STL/CLR)](#to_array)|Copia la secuencia controlada en una nueva matriz.|
|[vector::vector (STL/CLR)](#vector)|Construye un objeto contenedor.|

|Propiedad|Descripción|
|--------------|-----------------|
|[vector::back_item (STL/CLR)](#back_item)|Obtiene acceso al último elemento.|
|[vector::front_item (STL/CLR)](#front_item)|Obtiene acceso al primer elemento.|

|Operator|Descripción|
|--------------|-----------------|
|[vector::operator= (STL/CLR)](#op_as)|Reemplaza la secuencia controlada.|
|[vector::operator(STL/CLR)](#op)|Obtiene acceso a un elemento en una posición especificada.|
|[operador! (vector) (STL/CLR)](#op_neq)|Determina si `vector` un objeto no `vector` es igual a otro objeto.|
|[operador< (vector) (STL/CLR)](#op_lt)|Determina si `vector` un objeto es `vector` menor que otro objeto.|
|[operador<(vector) (STL/CLR)](#op_lteq)|Determina si `vector` un objeto es menor `vector` o igual que otro objeto.|
|[operador (vector) (STL/CLR)](#op_eq)|Determina si `vector` un objeto es `vector` igual a otro objeto.|
|[operador> (vector) (STL/CLR)](#op_gt)|Determina si `vector` un objeto es `vector` mayor que otro objeto.|
|[operator>= (vector) (STL/CLR)](#op_gteq)|Determina si `vector` un objeto es mayor `vector` o igual que otro objeto.|

## <a name="interfaces"></a>Interfaces

|Interfaz|Descripción|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplicar un objeto.|
|<xref:System.Collections.IEnumerable>|Secuenciar a través de elementos.|
|<xref:System.Collections.ICollection>|Mantener grupo de elementos.|
|<xref:System.Collections.Generic.IEnumerable%601>|Secuenciar a través de elementos con tipo.|
|<xref:System.Collections.Generic.ICollection%601>|Mantener grupo de elementos con tipo.|
|<xref:System.Collections.Generic.IList%601>|Mantener grupo ordenado de elementos con tipo.|
|Valor<IVector\>|Mantenga el contenedor genérico.|

## <a name="remarks"></a>Observaciones

El objeto asigna y libera almacenamiento para la secuencia que controla a través de una matriz almacenada de *Value* elementos, que crece a petición. El crecimiento se produce de tal manera que el costo de anexar un nuevo elemento se amortiza tiempo constante. En otras palabras, el costo de agregar elementos al final no aumenta, en promedio, a medida que la longitud de la secuencia controlada aumenta. Por lo tanto, un vector es un buen candidato para el contenedor subyacente para la pila de clases de plantilla [(STL/CLR).](../dotnet/stack-stl-clr.md)

A `vector` admite iteradores de acceso aleatorio, lo que significa que puede hacer referencia a un elemento `size() - 1` directamente dada su posición numérica, contando desde cero para el primer elemento (frontal), hasta el último elemento (atrás). También significa que un vector es un buen candidato para el contenedor subyacente para la clase de plantilla [priority_queue (STL/CLR).](../dotnet/priority-queue-stl-clr.md)

Un iterador vectorial almacena un identificador a su objeto vectorial asociado, junto con el sesgo del elemento que designa. Puede utilizar iteradores solo con sus objetos contenedor asociados. El sesgo de un elemento vectorial es el mismo que su posición.

Insertar o borrar elementos puede cambiar el valor del elemento almacenado en una posición determinada, por lo que el valor designado por un iterador también puede cambiar. (El contenedor puede tener que copiar elementos hacia arriba o hacia abajo para crear un agujero antes de una plaquita o para rellenar un agujero después de un borrado.) Sin embargo, un iterador vectorial sigue siendo `[0, size()]`válido siempre y cuando su sesgo esté en el rango. Además, un iterador válido sigue siendo dereferencable -- puede usarlo para acceder o modificar `size()`el valor del elemento que designa -- siempre y cuando su sesgo no sea igual a .

Al borrar o quitar un elemento, se llama al destructor para su valor almacenado. Al destruir el contenedor, se borran todos los elementos. Por lo tanto, un contenedor cuyo tipo de elemento es una clase ref garantiza que ningún elemento sobreviva al contenedor. Tenga en cuenta, sin embargo, que un contenedor de identificadores no destruye sus elementos.

## <a name="members"></a>Miembros

## <a name="vectorassign-stlclr"></a><a name="assign"></a>vector::assign (STL/CLR)

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

*Primero*<br/>
Inicio del rango para insertar.

*Última*<br/>
Fin del rango que se va a insertar.

*Correcto*<br/>
Enumeración que se va a insertar.

*Val*<br/>
Valor del elemento que se va a insertar.

### <a name="remarks"></a>Observaciones

La primera función miembro reemplaza la secuencia controlada por una repetición *de* elementos count de value *val*. Se utiliza para rellenar el contenedor con elementos que tienen el mismo valor.

Si `InIt` es un tipo entero, la segunda función miembro se comporta igual que `assign((size_type)first, (value_type)last)`. De lo contrario, reemplaza la secuencia`first`controlada `last`por la secuencia [ , ). Se utiliza para convertir la secuencia controlada en una copia de otra secuencia.

La tercera función miembro reemplaza la secuencia controlada por la secuencia designada por el *derecho*enumerador . Se usa para convertir la secuencia controlada en una copia de una secuencia descrita por un enumerador.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_assign.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// assign a repetition of values
    cliext::vector<wchar_t> c2;
    c2.assign(6, L'x');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign an iterator range
    c2.assign(c1.begin(), c1.end() - 1);
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

## <a name="vectorat-stlclr"></a><a name="at"></a>vector::at (STL/CLR)

Obtiene acceso a un elemento en una posición especificada.

### <a name="syntax"></a>Sintaxis

```cpp
reference at(size_type pos);
```

#### <a name="parameters"></a>Parámetros

*Pos*<br/>
Posición del elemento al que se accederá.

### <a name="remarks"></a>Observaciones

La función miembro devuelve una referencia al elemento de la secuencia controlada en *position pos*. Se utiliza para leer o escribir un elemento cuya posición conoces.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_at.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" using at
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1.at(i));
    System::Console::WriteLine();

// change an entry and redisplay
    c1.at(1) = L'x';
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1[i]);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a x c
```

## <a name="vectorback-stlclr"></a><a name="back"></a>vector::back (STL/CLR)

Obtiene acceso al último elemento.

### <a name="syntax"></a>Sintaxis

```cpp
reference back();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve una referencia al último elemento de la secuencia controlada, que debe ser no vacía. Se utiliza para acceder al último elemento, cuando se sabe que existe.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_back.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorback_item-stlclr"></a><a name="back_item"></a>vector::back_item (STL/CLR)

Obtiene acceso al último elemento.

### <a name="syntax"></a>Sintaxis

```cpp
property value_type back_item;
```

### <a name="remarks"></a>Observaciones

La propiedad tiene acceso al último elemento de la secuencia controlada, que debe ser no vacío. Se utiliza para leer o escribir el último elemento, cuando se sabe que existe.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_back_item.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorbegin-stlclr"></a><a name="begin"></a>vector::begin (STL/CLR)

Designa el principio de la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
iterator begin();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve un iterador de acceso aleatorio que designa el primer elemento de la secuencia controlada, o justo más allá del final de una secuencia vacía. Se usa para obtener un iterador que designe el principio de la secuencia controlada, indicado por `current`, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_begin.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items
    cliext::vector<wchar_t>::iterator it = c1.begin();
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

## <a name="vectorcapacity-stlclr"></a><a name="capacity"></a>vector::capacidad (STL/CLR)

Notifica el tamaño de almacenamiento asignado del contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
size_type capacity();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve el almacenamiento asignado actualmente para contener la secuencia controlada, un valor al menos tan grande como [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md)`()`. Se usa para determinar cuánto puede crecer el contenedor antes de que deba reasignar el almacenamiento para la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_capacity.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1.at(i));
    System::Console::WriteLine();

// increase capacity
    cliext::vector<wchar_t>::size_type cap = c1.capacity();
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        cap, c1.size() <= cap);
    c1.reserve(cap + 5);
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        c1.capacity(), cap + 5 <= c1.capacity());
    return (0);
    }
```

```Output
a b c
capacity() = 4, ok = True
capacity() = 9, ok = True
```

## <a name="vectorclear-stlclr"></a><a name="clear"></a>vector::clear (STL/CLR)

Quita todos los elementos.

### <a name="syntax"></a>Sintaxis

```cpp
void clear();
```

### <a name="remarks"></a>Observaciones

La función miembro llama eficazmente [vector::erase (STL/CLR)](../dotnet/vector-erase-stl-clr.md) `(` [vector::begin (STL/CLR)](../dotnet/vector-begin-stl-clr.md) `(),` [vector::end (STL/CLR)](../dotnet/vector-end-stl-clr.md)`())`. Se utiliza para asegurarse de que la secuencia controlada está vacía.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_clear.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorconst_iterator-stlclr"></a><a name="const_iterator"></a>vector::const_iterator (STL/CLR)

El tipo de un iterador constante para la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto de `T2` tipo no especificado que puede servir como un iterador de acceso aleatorio constante para la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_const_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    cliext::vector<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="vectorconst_reference-stlclr"></a><a name="const_reference"></a>vector::const_reference (STL/CLR)

El tipo de una referencia constante a un elemento.

### <a name="syntax"></a>Sintaxis

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Observaciones

El tipo describe una referencia constante a un elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_const_reference.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    cliext::vector<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        cliext::vector<wchar_t>::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="vectorconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>vector::const_reverse_iterator (STL/CLR)

El tipo de un iterador inverso constante para la secuencia controlada..

### <a name="syntax"></a>Sintaxis

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto de `T4` tipo no especificado que puede servir como un iterador inverso constante para la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" reversed
    cliext::vector<wchar_t>::const_reverse_iterator crit = c1.rbegin();
    cliext::vector<wchar_t>::const_reverse_iterator crend = c1.rend();
    for (; crit != crend; ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="vectordifference_type-stlclr"></a><a name="difference_type"></a>vector::difference_type (STL/CLR)

Los tipos de una distancia firmada entre dos elementos.

### <a name="syntax"></a>Sintaxis

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Observaciones

El tipo describe un recuento de elementos con signo.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_difference_type.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    cliext::vector<wchar_t>::difference_type diff = 0;
    for (cliext::vector<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it) ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

// compute negative difference
    diff = 0;
    for (cliext::vector<wchar_t>::iterator it = c1.end();
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

## <a name="vectorempty-stlclr"></a><a name="empty"></a>vector::vacío (STL/CLR)

Comprueba si no hay ningún elemento presente.

### <a name="syntax"></a>Sintaxis

```cpp
bool empty();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve true para una secuencia controlada vacía. Es equivalente a [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md)`() == 0`. Se utiliza para comprobar si el vector está vacío.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_empty.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorend-stlclr"></a><a name="end"></a>vector::end (STL/CLR)

Designa el final de la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
iterator end();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve un iterador de acceso aleatorio que apunta justo más allá del final de la secuencia controlada. Se usa para obtener un iterador que designe el final de la secuencia controlada, indicado por `current`, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_end.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last two items
    cliext::vector<wchar_t>::iterator it = c1.end();
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

## <a name="vectorerase-stlclr"></a><a name="erase"></a>vector::erase (STL/CLR)

Quita los elementos de las posiciones especificadas.

### <a name="syntax"></a>Sintaxis

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
```

#### <a name="parameters"></a>Parámetros

*Primero*<br/>
Comienzo del rango para borrar.

*Última*<br/>
Fin del alcance para borrar.

*where*<br/>
Elemento que se va a borrar.

### <a name="remarks"></a>Observaciones

La primera función miembro quita el elemento de la secuencia controlada señalada por *where*. Se utiliza para quitar un solo elemento.

La segunda función miembro quita los elementos de la secuencia controlada en el intervalo [`first`, `last`). Se utiliza para eliminar cero o más elementos contiguos.

Ambas funciones miembro devuelven un iterador que designa el primer elemento restante más allá de los elementos quitados, o [vector::end (STL/CLR)](../dotnet/vector-end-stl-clr.md) `()` si no existe dicho elemento.

Al borrar elementos, el número de copias de elementos es lineal en el número de elementos entre el final del borrado y el final más cercano de la secuencia. (Al borrar uno o más elementos en cualquiera de los extremos de la secuencia, no se producen copias de elementos.)

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_erase.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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
    cliext::vector<wchar_t>::iterator it = c1.end();
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

## <a name="vectorfront-stlclr"></a><a name="front"></a>vector::front (STL/CLR)

Obtiene acceso al primer elemento.

### <a name="syntax"></a>Sintaxis

```cpp
reference front();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve una referencia al primer elemento de la secuencia controlada, que debe ser no vacía. Se utiliza para leer o escribir el primer elemento, cuando se sabe que existe.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_front.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorfront_item-stlclr"></a><a name="front_item"></a>vector::front_item (STL/CLR)

Obtiene acceso al primer elemento.

### <a name="syntax"></a>Sintaxis

```cpp
property value_type front_item;
```

### <a name="remarks"></a>Observaciones

La propiedad tiene acceso al primer elemento de la secuencia controlada, que debe ser no vacío. Se utiliza para leer o escribir el primer elemento, cuando se sabe que existe.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_front_item.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorgeneric_container-stlclr"></a><a name="generic_container"></a>vector::generic_container (STL/CLR)

El tipo de la interfaz genérica para el contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Microsoft::VisualC::StlClr::
    IVector<generic_value>
    generic_container;
```

### <a name="remarks"></a>Observaciones

El tipo describe la interfaz genérica para esta clase contenedora de plantilla.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_generic_container.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
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

## <a name="vectorgeneric_iterator-stlclr"></a><a name="generic_iterator"></a>vector::generic_iterator (STL/CLR)

El tipo de un iterador para su uso con la interfaz genérica para el contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerRandomAccessIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe un iterador genérico que se puede usar con la interfaz genérica para esta clase de contenedor de plantilla.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_generic_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    cliext::vector<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::vector<wchar_t>::generic_value gcval = *gcit;
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

## <a name="vectorgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>vector::generic_reverse_iterator (STL/CLR)

El tipo de un iterador inverso para su uso con la interfaz genérica para el contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value> generic_reverse_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe un iterador inverso genérico que se puede usar con la interfaz genérica para esta clase de contenedor de plantilla.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    cliext::vector<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();
    cliext::vector<wchar_t>::generic_value gcval = *gcit;
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

## <a name="vectorgeneric_value-stlclr"></a><a name="generic_value"></a>vector::generic_value (STL/CLR)

El tipo de un elemento para su uso con la interfaz genérica para el contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Observaciones

El tipo describe un `GValue` objeto de tipo que describe el valor del elemento almacenado para su uso con la interfaz genérica para esta clase contenedora de plantilla.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_generic_value.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    cliext::vector<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::vector<wchar_t>::generic_value gcval = *gcit;
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

## <a name="vectorinsert-stlclr"></a><a name="insert"></a>vector::inserción (STL/CLR)

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

*Primero*<br/>
Inicio del rango para insertar.

*Última*<br/>
Fin del rango que se va a insertar.

*Correcto*<br/>
Enumeración que se va a insertar.

*Val*<br/>
Valor del elemento que se va a insertar.

*where*<br/>
Dónde en el contenedor para insertar antes.

### <a name="remarks"></a>Observaciones

Cada una de las funciones miembro inserta, antes de que el elemento señale por *donde* en la secuencia controlada, una secuencia especificada por los operandos restantes.

La primera función miembro inserta un elemento con valor *val* y devuelve un iterador que designa el elemento recién insertado. Se utiliza para insertar un único elemento antes de un lugar designado por un iterador.

La segunda función miembro inserta una repetición de elementos *count* de value *val*. Se utiliza para insertar cero o más elementos contiguos que son todas copias del mismo valor.

Si `InIt` es un tipo entero, la tercera función miembro se comporta igual que `insert(where, (size_type)first, (value_type)last)`. De lo contrario, inserta`first` `last`la secuencia [ , ). Se utiliza para insertar cero o más elementos contiguos copiados de otra secuencia.

La cuarta función miembro inserta la secuencia designada por la *derecha*. Se utiliza para insertar una secuencia descrita por un enumerador.

Al insertar un único elemento, el número de copias de elementos es lineal en el número de elementos entre el punto de inserción y el extremo más cercano de la secuencia. (Al insertar uno o más elementos en cualquiera de los extremos de la secuencia, no se producen copias de elementos.) Si `InIt` es un iterador de entrada, la tercera función miembro realiza eficazmente una inserción única para cada elemento de la secuencia. De lo contrario, al insertar `N` elementos, `N` el número de copias de elementos es lineal en más el número de elementos entre el punto de inserción y el extremo más cercano de la secuencia.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_insert.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert a single value using iterator
    cliext::vector<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",
        *c1.insert(++it, L'x'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert a repetition of values
    cliext::vector<wchar_t> c2;
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

## <a name="vectoriterator-stlclr"></a><a name="iterator"></a>vector::iterator (STL/CLR)

El tipo de un iterador para la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto de `T1` tipo no especificado que puede servir como un iterador de acceso aleatorio para la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    cliext::vector<wchar_t>::iterator it = c1.begin();
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

## <a name="vectoroperator-stlclr"></a><a name="op_as"></a>vector::operador (STL/CLR)

Reemplaza la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
vector<Value>% operator=(vector<Value>% right);
```

#### <a name="parameters"></a>Parámetros

*Correcto*<br/>
Contenedor que se va a copiar.

### <a name="remarks"></a>Observaciones

El operador miembro copia *right* to `*this`the object y, a continuación, devuelve . Se utiliza para reemplazar la secuencia controlada con una copia de la secuencia controlada a *la derecha.*

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_operator_as.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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

## <a name="vectoroperatorstlclr"></a><a name="op"></a>vector::operador (STL/CLR)

Obtiene acceso a un elemento en una posición especificada.

### <a name="syntax"></a>Sintaxis

```cpp
reference operator[](size_type pos);
```

#### <a name="parameters"></a>Parámetros

*Pos*<br/>
Posición del elemento al que se accederá.

### <a name="remarks"></a>Observaciones

El operador miembro devuelve un referencia al elemento en la posición *pos*. Se utiliza para acceder a un elemento cuya posición conoces.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_operator_sub.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" using subscripting
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1[i]);
    System::Console::WriteLine();

// change an entry and redisplay
    c1[1] = L'x';
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1[i]);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a x c
```

## <a name="vectorpop_back-stlclr"></a><a name="pop_back"></a>vector::pop_back (STL/CLR)

Quita el último elemento.

### <a name="syntax"></a>Sintaxis

```cpp
void pop_back();
```

### <a name="remarks"></a>Observaciones

La función miembro quita el último elemento de la secuencia controlada, que debe ser no vacío. Se utiliza para acortar el vector por un elemento en la parte posterior.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_pop_back.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorpush_back-stlclr"></a><a name="push_back"></a>vector::push_back (STL/CLR)

Agrega un nuevo último elemento.

### <a name="syntax"></a>Sintaxis

```cpp
void push_back(value_type val);
```

### <a name="remarks"></a>Observaciones

La función miembro inserta `val` un elemento con valor al final de la secuencia controlada. Se utiliza para anexar otro elemento al vector.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_push_back.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorrbegin-stlclr"></a><a name="rbegin"></a>vector::rbegin (STL/CLR)

Designa el principio de la secuencia controlada inversa.

### <a name="syntax"></a>Sintaxis

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve un iterador inverso que designa el último elemento de la secuencia controlada, o justo más allá del principio de una secuencia vacía. Por lo tanto, designa el parámetro `beginning` de la secuencia inversa. Se usa para obtener un iterador que designe el principio de la secuencia controlada mostrada en orden inverso, indicado por `current`, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_rbegin.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items in reversed sequence
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rbegin();
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

## <a name="vectorreference-stlclr"></a><a name="reference"></a>vector::referencia (STL/CLR)

El tipo de una referencia a un elemento.

### <a name="syntax"></a>Sintaxis

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Observaciones

El tipo describe una referencia a un elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_reference.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    cliext::vector<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::vector<wchar_t>::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();

// modify contents " a b c"
    for (it = c1.begin(); it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::vector<wchar_t>::reference ref = *it;

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

## <a name="vectorrend-stlclr"></a><a name="rend"></a>vector::rend (STL/CLR)

Designa el final de la secuencia controlada inversa.

### <a name="syntax"></a>Sintaxis

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve un iterador inverso que apunta justo más allá del principio de la secuencia controlada. Por lo tanto, designa el parámetro `end` de la secuencia inversa. Se usa para obtener un iterador que designe el final de la secuencia controlada mostrada en orden inverso, indicado por `current`, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_rend.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rend();
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

## <a name="vectorreserve-stlclr"></a><a name="reserve"></a>vector::reserve (STL/CLR)

Garantiza una capacidad de crecimiento mínima para el contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
void reserve(size_type count);
```

#### <a name="parameters"></a>Parámetros

*count*<br/>
Nueva capacidad mínima del contenedor.

### <a name="remarks"></a>Observaciones

La función `capacity()` miembro garantiza que en adelante devuelve al menos *count*. Se utiliza para asegurarse de que el contenedor no necesita reasignar el almacenamiento para la secuencia controlada hasta que haya crecido al tamaño especificado.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_reserve.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1.at(i));
    System::Console::WriteLine();

// increase capacity
    cliext::vector<wchar_t>::size_type cap = c1.capacity();
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        cap, c1.size() <= cap);
    c1.reserve(cap + 5);
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        c1.capacity(), cap + 5 <= c1.capacity());
    return (0);
    }
```

```Output
a b c
capacity() = 4, ok = True
capacity() = 9, ok = True
```

## <a name="vectorresize-stlclr"></a><a name="resize"></a>vector::resize (STL/CLR)

Cambia el número de elementos.

### <a name="syntax"></a>Sintaxis

```cpp
void resize(size_type new_size);
void resize(size_type new_size, value_type val);
```

#### <a name="parameters"></a>Parámetros

*new_size*<br/>
Nuevo tamaño de la secuencia controlada.

*Val*<br/>
Valor del elemento de relleno.

### <a name="remarks"></a>Observaciones

Las funciones miembro garantizan que [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md) `()` en adelante devuelve *new_size*. Si debe hacer que la secuencia controlada sea más larga, la primera función miembro anexa elementos con value `value_type()`, mientras que la segunda función miembro anexa elementos con valor *val*. Para que la secuencia controlada sea más corta, ambas funciones miembro borran eficazmente las `new_size` últimas veces del [vector de elemento::size (STL/CLR).](../dotnet/vector-size-stl-clr.md) `() -` Se utiliza para asegurarse de que la secuencia controlada tiene *new_size*de tamaño, ya sea recortando o rellenando la secuencia controlada actual.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_resize.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
// construct an empty container and pad with default values
    cliext::vector<wchar_t> c1;
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

## <a name="vectorreverse_iterator-stlclr"></a><a name="reverse_iterator"></a>vector::reverse_iterator (STL/CLR)

El tipo de un iterador invertido para la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto de `T3` tipo no especificado que puede servir como un iterador inverso para la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_reverse_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" reversed
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rbegin();
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

## <a name="vectorsize-stlclr"></a><a name="size"></a>vector::tamaño (STL/CLR)

Cuenta el número de elementos.

### <a name="syntax"></a>Sintaxis

```cpp
size_type size();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve la longitud de la secuencia controlada. Se utiliza para determinar el número de elementos actualmente en la secuencia controlada. Si lo que le importa es si la secuencia tiene un tamaño distinto de cero, consulte [vector::vacío (STL/CLR)](../dotnet/vector-empty-stl-clr.md)`()`.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_size.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorsize_type-stlclr"></a><a name="size_type"></a>vector::size_type (STL/CLR)

El tipo de una distancia con signo entre dos elementos.

### <a name="syntax"></a>Sintaxis

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Observaciones

El tipo describe un recuento de elementos no negativos.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_size_type.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    cliext::vector<wchar_t>::size_type diff = c1.end() - c1.begin();
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="vectorswap-stlclr"></a><a name="swap"></a>vector::swap (STL/CLR)

Intercambia el contenido de dos contenedores.

### <a name="syntax"></a>Sintaxis

```cpp
void swap(vector<Value>% right);
```

#### <a name="parameters"></a>Parámetros

*Correcto*<br/>
Contenedor con el que se va a intercambiar el contenido.

### <a name="remarks"></a>Observaciones

La función miembro intercambia las `*this` secuencias controladas entre y *derecha*. Lo hace en tiempo constante y no produce excepciones. Se utiliza como una forma rápida de intercambiar el contenido de dos contenedores.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_swap.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct another container with repetition of values
    cliext::vector<wchar_t> c2(5, L'x');
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

## <a name="vectorto_array-stlclr"></a><a name="to_array"></a>vector::to_array (STL/CLR)

Copia la secuencia controlada en una nueva matriz.

### <a name="syntax"></a>Sintaxis

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve una matriz que contiene la secuencia controlada. Se utiliza para obtener una copia de la secuencia controlada en forma de matriz.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_to_array.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorvalue_type-stlclr"></a><a name="value_type"></a>vector::value_type (STL/CLR)

El tipo de un elemento.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla *Value*.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_value_type.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" using value_type
    for (cliext::vector<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it)
        {   // store element in value_type object
        cliext::vector<wchar_t>::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="vectorvector-stlclr"></a><a name="vector"></a>vector::vector (STL/CLR)

Construye un objeto contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
vector();
vector(vector<Value>% right);
vector(vector<Value>^ right);
explicit vector(size_type count);
vector(size_type count, value_type val);
template<typename InIt>
    vector(InIt first, InIt last);
vector(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>Parámetros

*count*<br/>
Número de elementos que se van a insertar.

*Primero*<br/>
Inicio del rango para insertar.

*Última*<br/>
Fin del rango que se va a insertar.

*Correcto*<br/>
Objeto o intervalo que se va a insertar.

*Val*<br/>
Valor del elemento que se va a insertar.

### <a name="remarks"></a>Observaciones

El constructor:

`vector();`

inicializa la secuencia controlada sin elementos. Se utiliza para especificar una secuencia controlada inicial vacía.

El constructor:

`vector(vector<Value>% right);`

inicializa la secuencia controlada con`right.begin()`la `right.end()`secuencia [ , ). Se utiliza para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto vectorial *right*.

El constructor:

`vector(vector<Value>^ right);`

inicializa la secuencia controlada con`right->begin()`la `right->end()`secuencia [ , ). Se utiliza para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto vectorial cuyo identificador es *correcto.*

El constructor:

`explicit vector(size_type count);`

inicializa la secuencia controlada *count* con elementos `value_type()`count cada uno con value . Se utiliza para rellenar el contenedor con elementos todos con el valor predeterminado.

El constructor:

`vector(size_type count, value_type val);`

inicializa la secuencia controlada con elementos *count* cada uno con value *val*. Se utiliza para rellenar el contenedor con elementos que tienen el mismo valor.

El constructor:

`template<typename InIt>`

`vector(InIt first, InIt last);`

inicializa la secuencia controlada con`first`la `last`secuencia [ , ). Se utiliza para convertir la secuencia controlada en una copia de otra secuencia.

El constructor:

`vector(System::Collections::Generic::IEnumerable<Value>^ right);`

inicializa la secuencia controlada con la secuencia designada por el *derecho*enumerador . Se usa para convertir la secuencia controlada en una copia de otra secuencia descrita por un enumerador.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_construct.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
// construct an empty container
    cliext::vector<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());

// construct with a repetition of default values
    cliext::vector<wchar_t> c2(3);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

// construct with a repetition of values
    cliext::vector<wchar_t> c3(6, L'x');
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an iterator range
    cliext::vector<wchar_t>::iterator it = c3.end();
    cliext::vector<wchar_t> c4(c3.begin(), --it);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an enumeration
    cliext::vector<wchar_t> c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container
    cliext::vector<wchar_t> c7(c3);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying a container handle
    cliext::vector<wchar_t> c8(%c3);
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

## <a name="operator-vector-stlclr"></a><a name="op_neq"></a>operador! (vector) (STL/CLR)

Vector no es igual comparación.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value>
    bool operator!=(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parámetros

*Izquierda*<br/>
Contenedor izquierdo que se va a comparar.

*Correcto*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Observaciones

La función `!(left == right)`operator devuelve . Se utiliza para probar si *izquierda* no se ordena igual que *la derecha* cuando los dos vectores se comparan elemento por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_operator_ne.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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

## <a name="operatorlt-vector-stlclr"></a><a name="op_lt"></a>operador&lt; (vector) (STL/CLR)

Vector menor que la comparación.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value>
    bool operator<(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parámetros

*Izquierda*<br/>
Contenedor izquierdo que se va a comparar.

*Correcto*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Observaciones

La función operator devuelve true `i` if, `!(right[i] < left[i])` para la `left[i] < right[i]`posición más baja para la que también es cierto que . De lo `left->size() < right->size()` contrario, devuelve Se utiliza para probar si *left* se ordena antes *de la derecha* cuando los dos vectores se comparan elemento por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_operator_lt.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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

## <a name="operatorlt-vector-stlclr"></a><a name="op_lteq"></a>operador&lt;(vector) (STL/CLR)

Vector menor o igual comparación.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value>
    bool operator<=(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parámetros

*Izquierda*<br/>
Contenedor izquierdo que se va a comparar.

*Correcto*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Observaciones

La función `!(right < left)`operator devuelve . Se utiliza para probar si *izquierda* no se ordena después de *right* cuando los dos vectores se comparan elemento por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_operator_le.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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

## <a name="operator-vector-stlclr"></a><a name="op_eq"></a>operador (vector) (STL/CLR)

Comparación de vectores igual.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value>
    bool operator==(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parámetros

*Izquierda*<br/>
Contenedor izquierdo que se va a comparar.

*Correcto*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Observaciones

La función operator devuelve true solo si *right* las secuencias controladas por `i` *izquierda* y derecha tienen la misma longitud y, para cada posición, `left[i] ==` `right[i]`. Se utiliza para probar si *a la izquierda* se ordena igual que a la *derecha* cuando los dos vectores se comparan elemento por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_operator_eq.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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

## <a name="operatorgt-vector-stlclr"></a><a name="op_gt"></a>operador&gt; (vector) (STL/CLR)

Vector mayor que la comparación.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value>
    bool operator>(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parámetros

*Izquierda*<br/>
Contenedor izquierdo que se va a comparar.

*Correcto*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Observaciones

La función `right` `<` `left`operator devuelve . Se utiliza para probar si *la izquierda* se ordena después de *la derecha* cuando los dos vectores se comparan elemento por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_operator_gt.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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

## <a name="operatorgt-vector-stlclr"></a><a name="op_gteq"></a>operador&gt;(vector) (STL/CLR)

Vector mayor o igual comparación.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value>
    bool operator>=(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parámetros

*Izquierda*<br/>
Contenedor izquierdo que se va a comparar.

*Correcto*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Observaciones

La función `!(left < right)`operator devuelve . Se utiliza para probar si *izquierda* no se ordena antes *de la derecha* cuando los dos vectores se comparan elemento por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_vector_operator_ge.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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
