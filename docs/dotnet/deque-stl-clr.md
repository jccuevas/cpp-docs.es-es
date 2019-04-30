---
title: deque (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::deque
- cliext::deque::assign
- cliext::deque::at
- cliext::deque::back
- cliext::deque::back_item
- cliext::deque::begin
- cliext::deque::clear
- cliext::deque::const_iterator
- cliext::deque::const_reference
- cliext::deque::const_reverse_iterator
- cliext::deque::deque
- cliext::deque::difference_type
- cliext::deque::empty
- cliext::deque::end
- cliext::deque::erase
- cliext::deque::front
- cliext::deque::front_item
- cliext::deque::generic_container
- cliext::deque::generic_iterator
- cliext::deque::generic_reverse_iterator
- cliext::deque::generic_value
- cliext::deque::insert
- cliext::deque::iterator
- cliext::deque::operator!=
- cliext::deque::operator[]
- cliext::deque::pop_back
- cliext::deque::pop_front
- cliext::deque::push_back
- cliext::deque::push_front
- cliext::deque::rbegin
- cliext::deque::reference
- cliext::deque::rend
- cliext::deque::resize
- cliext::deque::reverse_iterator
- cliext::deque::size
- cliext::deque::size_type
- cliext::deque::swap
- cliext::deque::to_array
- cliext::deque::value_type
- cliext::deque::operator<
- cliext::deque::operator<=
- cliext::deque::operator=
- cliext::deque::operator==
- cliext::deque::operator>
- cliext::deque::operator>=
helpviewer_keywords:
- deque class [STL/CLR]
- <deque> header [STL/CLR]
- <cliext/deque> header [STL/CLR]
- assign member [STL/CLR]
- assign member [STL/CLR]
- at member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- deque member [STL/CLR]
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
- operator!= member [STL/CLR]
- operator member [] [STL/CLR]
- pop_back member [STL/CLR]
- pop_front member [STL/CLR]
- push_back member [STL/CLR]
- push_front member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- resize member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- value_type member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator= member [STL/CLR]
- operator== member [STL/CLR]
- operator> member [STL/CLR]
- operator>= member [STL/CLR]
ms.assetid: dd669da3-3c0e-45e9-8596-f6b483720941
ms.openlocfilehash: ff5ddcfa101baf4c85145d1c6d64a6a3b9e7df58
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393771"
---
# <a name="deque-stlclr"></a>deque (STL/CLR)

La clase de plantilla describe un objeto que controla una secuencia de elementos de longitud variable que tiene acceso aleatorio. Usar el contenedor `deque` para administrar una secuencia de elementos que se parezca a un bloque de almacenamiento contiguo, pero que pueden ampliarse o reducirse en cualquiera de los extremos sin necesidad de copiar los elementos restantes. Por lo tanto puede implementar eficazmente un `double-ended queue`. (Por lo tanto, el nombre.)

En la descripción siguiente, `GValue` es el mismo que `Value` a menos que este último es un tipo de referencia, en cuyo caso es `Value^`.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename Value>
    ref class deque
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        Microsoft::VisualC::StlClr::IDeque<GValue>
    { ..... };
```

### <a name="parameters"></a>Parámetros

*GValue*<br/>
El tipo genérico de un elemento de la secuencia controlada.

*Valor*<br/>
Tipo de un elemento de la secuencia controlada.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<cliext/deque >

**Namespace:** cliext

## <a name="declarations"></a>Declaraciones

|Definición de tipo|Descripción|
|---------------------|-----------------|
|[deque::const_iterator (STL/CLR)](#const_iterator)|El tipo de un iterador constante para la secuencia controlada.|
|[deque::const_reference (STL/CLR)](#const_reference)|El tipo de una referencia constante a un elemento.|
|[deque::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|El tipo de un iterador invertido constante para la secuencia controlada.|
|[deque::difference_type (STL/CLR)](#difference_type)|El tipo de una distancia con signo entre dos elementos.|
|[deque::generic_container (STL/CLR)](#generic_container)|El tipo de la interfaz genérica para el contenedor.|
|[deque::generic_iterator (STL/CLR)](#generic_iterator)|El tipo de iterador para la interfaz genérica para el contenedor.|
|[deque::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|El tipo de un iterador inverso de la interfaz genérica para el contenedor.|
|[deque::generic_value (STL/CLR)](#generic_value)|El tipo de un elemento de la interfaz genérica para el contenedor.|
|[deque::iterator (STL/CLR)](#iterator)|El tipo de un iterador para la secuencia controlada.|
|[deque::reference (STL/CLR)](#reference)|El tipo de una referencia a un elemento.|
|[deque::reverse_iterator (STL/CLR)](#reverse_iterator)|El tipo de un iterador invertido para la secuencia controlada.|
|[deque::size_type (STL/CLR)](#size_type)|El tipo de una distancia con signo entre dos elementos.|
|[deque::value_type (STL/CLR)](#value_type)|El tipo de un elemento.|

|Función miembro|Descripción|
|---------------------|-----------------|
|[deque::assign (STL/CLR)](#assign)|Reemplaza todos los elementos.|
|[deque::at (STL/CLR)](#at)|Obtiene acceso a un elemento en una posición especificada.|
|[deque::back (STL/CLR)](#back)|Obtiene acceso al último elemento.|
|[deque::begin (STL/CLR)](#begin)|Designa el principio de la secuencia controlada.|
|[deque::clear (STL/CLR)](#clear)|Quita todos los elementos.|
|[deque::deque (STL/CLR)](#deque)|Construye un objeto contenedor.|
|[deque::empty (STL/CLR)](#empty)|Comprueba si no hay ningún elemento presente.|
|[deque::end (STL/CLR)](#end)|Designa el final de la secuencia controlada.|
|[deque::erase (STL/CLR)](#erase)|Quita los elementos de las posiciones especificadas.|
|[deque::front (STL/CLR)](#front)|Obtiene acceso al primer elemento.|
|[deque::insert (STL/CLR)](#insert)|Agrega elementos en una posición especificada.|
|[deque::pop_back (STL/CLR)](#pop_back)|Quita el último elemento.|
|[deque::pop_front (STL/CLR)](#pop_front)|Quita el primer elemento.|
|[deque::push_back (STL/CLR)](#push_back)|Agrega un nuevo elemento de la última.|
|[deque::push_front (STL/CLR)](#push_front)|Agrega un nuevo primer elemento.|
|[deque::rbegin (STL/CLR)](#rbegin)|Designa el principio de la secuencia controlada inversa.|
|[deque::rend (STL/CLR)](#rend)|Designa el final de la secuencia controlada inversa.|
|[deque::resize (STL/CLR)](#resize)|Cambia el número de elementos.|
|[deque::size (STL/CLR)](#size)|Cuenta el número de elementos.|
|[deque::swap (STL/CLR)](#swap)|Intercambia el contenido de dos contenedores.|
|[deque::to_array (STL/CLR)](#to_array)|Copia la secuencia controlada a una nueva matriz.|

|Propiedad|Descripción|
|--------------|-----------------|
|[deque::back_item (STL/CLR)](#back_item)|Obtiene acceso al último elemento.|
|[deque::front_item (STL/CLR)](#front_item)|Obtiene acceso al primer elemento.|

|Operador|Descripción|
|--------------|-----------------|
|[deque::operator!= (STL/CLR)](#op_neq)|Determina si dos `deque` objetos no son iguales.|
|[deque::operator(STL/CLR)](#operator)|Obtiene acceso a un elemento en una posición especificada.|
|[operator< (deque) (STL/CLR)](#op_lt)|Determina si un `deque` objeto es menor que otro `deque` objeto.|
|[operator<= (deque) (STL/CLR)](#op_lteq)|Determina si un `deque` objeto es menor o igual que otro `deque` objeto.|
|[operator= (deque) (STL/CLR)](#op_as)|Reemplaza la secuencia controlada.|
|[operator== (deque) (STL/CLR)](#op_eq)|Determina si un `deque` es igual a otro objeto `deque` objeto.|
|[operator> (deque) (STL/CLR)](#op_gt)|Determina si un `deque` es mayor que otro objeto `deque` objeto.|
|[operator>= (deque) (STL/CLR)](#op_gteq)|Determina si un `deque` objeto es mayor o igual que otro `deque` objeto.|

## <a name="interfaces"></a>Interfaces

|Interfaz|Descripción|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplicar un objeto.|
|<xref:System.Collections.IEnumerable>|Secuencia a través de los elementos.|
|<xref:System.Collections.ICollection>|Mantener el grupo de elementos.|
|<xref:System.Collections.Generic.IEnumerable%601>|Secuencia a través de los elementos con tipo.|
|<xref:System.Collections.Generic.ICollection%601>|Mantener el grupo de elementos con tipo.|
|<xref:System.Collections.Generic.IList%601>|Mantener un grupo ordenado de elementos con tipo.|
|IDeque<Value\>|Mantener contenedor genérico.|

## <a name="remarks"></a>Comentarios

El objeto asigna y libera almacenamiento para la secuencia que controla a través de una matriz de identificadores que designan los bloques de almacenado `Value` elementos. La matriz aumenta de tamaño a petición. Crecimiento se produce de manera que el costo de anteponer o anexar un nuevo elemento es el tiempo constante y ningún elemento restante se ven afectado. También puede quitar un elemento en cualquier extremo en tiempo constante y sin perturbar elementos restantes. Por lo tanto, un deque es un buen candidato para el contenedor subyacente para la clase de plantilla [(STL/CLR) de la cola](../dotnet/queue-stl-clr.md) o clase de plantilla [(STL/CLR) de la pila](../dotnet/stack-stl-clr.md).

Un `deque` objeto es compatible con los iteradores de acceso aleatorio, lo que significa que puede hacer referencia a un elemento directamente según su posición numérica, contando desde cero para el primer elemento (frontal), para [deque:: Size (STL/CLR)](#size) `() - 1` para el último elemento (atrás). También significa que un deque es un buen candidato para el contenedor subyacente para la clase de plantilla [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md).

Un iterador deque almacena un identificador a su objeto deque asociado, junto con la diferencia del elemento que este designa. Puede usar iteradores sólo con sus objetos de contenedor asociado. La diferencia de un elemento del deque es *no* necesariamente el mismo que su posición. El primer elemento insertado tiene sesgo cero, el siguiente elemento anexado tiene sesgo 1, pero el siguiente elemento antepuesto tiene sesgo -1.

Insertar o borrar los elementos en cualquier extremo hace *no* modificar el valor de un elemento almacenado en cualquier diferencia válido. Insertar o borrar un elemento interior, sin embargo, *puede* cambiar el valor del elemento almacenado en una inclinación especificada, por lo que también puede cambiar el valor designado por un iterador. (El contenedor que tenga que copiar los elementos de o hacia abajo para crear un "agujero" antes de una instrucción insert o para rellenar un "agujero" después de un borrado). No obstante, un iterador deque sigue siendo válido siempre y cuando su inclinación designa un elemento válido. Además, un iterador válido permanece dereferenceable--se puede usar para tener acceso o modificar el valor del elemento designa--siempre y cuando su inclinación no es igual a la diferencia para el iterador devuelto por `end()`.

Borrar o quitar un elemento llama al destructor para su valor almacenado. Destruir el contenedor, borra todos los elementos. Por lo tanto, un contenedor cuyo tipo de elemento es una clase ref garantiza que ningún elemento durar más que el contenedor. Sin embargo, tenga en cuenta que un contenedor de controladores no *no* destruir sus elementos.

## <a name="members"></a>Miembros

## <a name="assign"></a> deque::assign (STL/CLR)

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
Fin del intervalo que se va a insertar.

*right*<br/>
Enumeración que se va a insertar.

*val*<br/>
Valor del elemento que se va a insertar.

### <a name="remarks"></a>Comentarios

La primera función miembro reemplaza la secuencia controlada por una repetición de *recuento* elementos del valor *val*. Usarlo para rellenar el contenedor con elementos teniendo todos el mismo valor.

Si `InIt` es de tipo entero, la segunda función miembro comporta igual que `assign((size_type)first, (value_type)last)`. En caso contrario, reemplaza la secuencia controlada por la secuencia [`first`, `last`). Se usa para realizar el controlado de secuencia de una copia otra secuencia.

La tercera función miembro reemplaza la secuencia controlada por la secuencia designada por el enumerador *derecho*. Usa para realizar una copia de una secuencia descrita por un enumerador de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_assign.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // assign a repetition of values
    cliext::deque<wchar_t> c2;
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

## <a name="at"></a> deque::at (STL/CLR)

Obtiene acceso a un elemento en una posición especificada.

### <a name="syntax"></a>Sintaxis

```cpp
reference at(size_type pos);
```

#### <a name="parameters"></a>Parámetros

*pos*<br/>
Posición del elemento al que se accederá.

### <a name="remarks"></a>Comentarios

La función miembro devuelve una referencia al elemento de la secuencia controlada en la posición *pos*. Se usa para leer o escribir un elemento cuya posición conoce.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_at.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="back"></a> deque::back (STL/CLR)

Obtiene acceso al último elemento.

### <a name="syntax"></a>Sintaxis

```cpp
reference back();
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve una referencia al último elemento de la secuencia controlada, que debe estar vacío. Usa para acceder el último elemento, cuando se sabe que existe.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_back.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="back_item"></a> deque::back_item (STL/CLR)

Obtiene acceso al último elemento.

### <a name="syntax"></a>Sintaxis

```cpp
property value_type back_item;
```

### <a name="remarks"></a>Comentarios

La propiedad tiene acceso el último elemento de la secuencia controlada, que debe estar vacío. Usa para leer o escribir el último elemento, cuando se sabe que existe.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_back_item.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="begin"></a> deque::begin (STL/CLR)

Designa el principio de la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
iterator begin();
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve un iterador de acceso aleatorio que designa el primer elemento de la secuencia controlada o justo después del final de una secuencia vacía. Se usa para obtener un iterador que designa el `current` principio de la secuencia controlada, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_begin.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    cliext::deque<wchar_t>::iterator it = c1.begin();
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

## <a name="clear"></a> deque::clear (STL/CLR)

Quita todos los elementos.

### <a name="syntax"></a>Sintaxis

```cpp
void clear();
```

### <a name="remarks"></a>Comentarios

La función miembro llama eficazmente a [Erase (STL/CLR)](#erase) `(` [deque:: begin (STL/CLR)](#begin) `(),` [deque:: end (STL/CLR)](#end) `())`. Usarlo para asegurarse de que está vacía la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_clear.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="const_iterator"></a> deque::const_iterator (STL/CLR)

El tipo de un iterador constante para la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Comentarios

El tipo describe un objeto de tipo sin especificar `T2` que puede actuar como un iterador de acceso aleatorio constante para la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_const_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    cliext::deque<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="const_reference"></a> deque::const_reference (STL/CLR)

El tipo de una referencia constante a un elemento.

### <a name="syntax"></a>Sintaxis

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Comentarios

El tipo describe una referencia constante a un elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_const_reference.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    cliext::deque<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        cliext::deque<wchar_t>::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="const_reverse_iterator"></a> deque::const_reverse_iterator (STL/CLR)

El tipo de un iterador inverso constante de la secuencia controlada...

### <a name="syntax"></a>Sintaxis

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Comentarios

El tipo describe un objeto de tipo sin especificar `T4` que puede actuar como un iterador inverso constante de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" reversed
    cliext::deque<wchar_t>::const_reverse_iterator crit = c1.rbegin();
    cliext::deque<wchar_t>::const_reverse_iterator crend = c1.rend();
    for (; crit != crend; ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="deque"></a> deque::deque (STL/CLR)

Construye un objeto contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
deque();
deque(deque<Value>% right);
deque(deque<Value>^ right);
explicit deque(size_type count);
deque(size_type count, value_type val);
template<typename InIt>
    deque(InIt first, InIt last);
deque(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>Parámetros

*count*<br/>
Número de elementos que se van a insertar.

*first*<br/>
Principio del intervalo que se va a insertar.

*last*<br/>
Fin del intervalo que se va a insertar.

*right*<br/>
Objeto o intervalo que se va a insertar.

*val*<br/>
Valor del elemento que se va a insertar.

### <a name="remarks"></a>Comentarios

El constructor:

`deque();`

Inicializa la secuencia controlada sin elementos. Se usa para especificar una secuencia controlada inicial vacía.

El constructor:

`deque(deque<Value>% right);`

Inicializa la secuencia controlada por la secuencia [`right.begin()`, `right.end()`). Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto deque *derecho*. Para obtener más información sobre los iteradores, vea [deque:: begin (STL/CLR)](#begin) y [deque:: end (STL/CLR)](#end).

El constructor:

`deque(deque<Value>^ right);`

Inicializa la secuencia controlada por la secuencia [`right->begin()`, `right->end()`). Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto deque cuyo identificador es *derecho*.

El constructor:

`explicit deque(size_type count);`

Inicializa la secuencia controlada con *recuento* elementos con el valor `value_type()`. Usarlo para rellenar el contenedor con elementos todos los que tiene el valor predeterminado.

El constructor:

`deque(size_type count, value_type val);`

Inicializa la secuencia controlada con *recuento* elementos con el valor *val*. Usarlo para rellenar el contenedor con elementos teniendo todos el mismo valor.

El constructor:

`template<typename InIt>`

`deque(InIt first, InIt last);`

Inicializa la secuencia controlada por la secuencia [`first`, `last`). Usa para realizar una copia de otra secuencia de la secuencia controlada.

El constructor:

`deque(System::Collections::Generic::IEnumerable<Value>^ right);`

Inicializa la secuencia controlada con la secuencia designada por el enumerador *derecho*. Usa para realizar una copia de otra secuencia descrita por un enumerador de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_construct.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
// construct an empty container
    cliext::deque<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    // construct with a repetition of default values
    cliext::deque<wchar_t> c2(3);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

    // construct with a repetition of values
    cliext::deque<wchar_t> c3(6, L'x');
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range
    cliext::deque<wchar_t>::iterator it = c3.end();
    cliext::deque<wchar_t> c4(c3.begin(), --it);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration
    cliext::deque<wchar_t> c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    cliext::deque<wchar_t> c7(c3);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying a container handle
    cliext::deque<wchar_t> c8(%c3);
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

## <a name="difference_type"></a> deque::difference_type (STL/CLR)

Los tipos de una distancia con signo entre dos elementos.

### <a name="syntax"></a>Sintaxis

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Comentarios

El tipo describe un recuento con signo del elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_difference_type.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    cliext::deque<wchar_t>::difference_type diff = 0;
    for (cliext::deque<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it) ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (cliext::deque<wchar_t>::iterator it = c1.end();
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

## <a name="empty"></a> deque::empty (STL/CLR)

Comprueba si no hay ningún elemento presente.

### <a name="syntax"></a>Sintaxis

```cpp
bool empty();
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve true para una secuencia controlada vacía. Equivale a [deque:: Size (STL/CLR)](#size)`() == 0`. Usa para comprobar si el deque está vacío.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_empty.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="end"></a> deque::end (STL/CLR)

Designa el final de la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
iterator end();
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve un iterador de acceso aleatorio que apunta justo después del final de la secuencia controlada. Se usa para obtener un iterador que designa el `current` final de la secuencia controlada, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_end.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last two items
    cliext::deque<wchar_t>::iterator it = c1.end();
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

## <a name="erase"></a> deque::erase (STL/CLR)

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
Fin del intervalo que se va a borrar.

*where*<br/>
Elemento que se va a borrar.

### <a name="remarks"></a>Comentarios

La primera función miembro quita el elemento de la secuencia controlada señalada por *donde*. Usa para quitar un elemento único.

La segunda función miembro quita los elementos de la secuencia controlada en el intervalo [`first`, `last`). Usa para quitar cero o más elementos contiguos.

Ambas funciones miembro devuelven un iterador que designa el primer elemento que permanece más allá de los elementos quitados, o [deque:: end (STL/CLR)](#end) `()` si no existe ese elemento.

Al borrar los elementos, el número de copias del elemento es lineal en el número de elementos entre el final de la eliminación y el final de cuanto más cerca de la secuencia. (Al borrar uno o más elementos en cualquier extremo de la secuencia, se produce ninguna copia del elemento.)

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_erase.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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
    cliext::deque<wchar_t>::iterator it = c1.end();
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

## <a name="front"></a> deque::front (STL/CLR)

Obtiene acceso al primer elemento.

### <a name="syntax"></a>Sintaxis

```cpp
reference front();
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve una referencia al primer elemento de la secuencia controlada, que debe estar vacío. Usa para leer o escribir el primer elemento, cuando se sabe que existe.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_front.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="front_item"></a> deque::front_item (STL/CLR)

Obtiene acceso al primer elemento.

### <a name="syntax"></a>Sintaxis

```cpp
property value_type front_item;
```

### <a name="remarks"></a>Comentarios

La propiedad tiene acceso el primer elemento de la secuencia controlada, que debe estar vacío. Usa para leer o escribir el primer elemento, cuando se sabe que existe.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_front_item.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="generic_container"></a> deque::generic_container (STL/CLR)

El tipo de la interfaz genérica para el contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Microsoft::VisualC::StlClr::
    IDeque<generic_value>
    generic_container;
```

### <a name="remarks"></a>Comentarios

El tipo describe la interfaz genérica para esta clase de contenedor de plantilla.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_generic_container.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::deque<wchar_t>::generic_container^ gc1 = %c1;
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

## <a name="generic_iterator"></a> deque::generic_iterator (STL/CLR)

El tipo de iterador para su uso con la interfaz genérica para el contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerRandomAccessIterator<generic_value> generic_iterator;
```

### <a name="remarks"></a>Comentarios

El tipo describe un iterador genérico que puede usarse con la interfaz genérica para esta clase de contenedor de plantilla.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_generic_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::deque<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::deque<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::deque<wchar_t>::generic_value gcval = *gcit;
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

## <a name="generic_reverse_iterator"></a> deque::generic_reverse_iterator (STL/CLR)

El tipo de un iterador inverso para su uso con la interfaz genérica para el contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value> generic_reverse_iterator;
```

### <a name="remarks"></a>Comentarios

El tipo describe un iterador inverso genérico que puede usarse con la interfaz genérica para esta clase de contenedor de plantilla.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::deque<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::deque<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();
    cliext::deque<wchar_t>::generic_value gcval = *gcit;
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

## <a name="generic_value"></a> deque::generic_value (STL/CLR)

El tipo de un elemento para su uso con la interfaz genérica para el contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Comentarios

El tipo describe un objeto de tipo `GValue` que describe el valor del elemento almacenados para su uso con la interfaz genérica para esta clase de contenedor de plantilla.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_generic_value.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::deque<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::deque<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::deque<wchar_t>::generic_value gcval = *gcit;
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

## <a name="insert"></a> deque::insert (STL/CLR)

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
Fin del intervalo que se va a insertar.

*right*<br/>
Enumeración que se va a insertar.

*val*<br/>
Valor del elemento que se va a insertar.

*where*<br/>
Lugar en el contenedor que se va a insertar antes.

### <a name="remarks"></a>Comentarios

Cada uno de los miembros funciones inserta delante del elemento al que apunta *donde* en la secuencia controlada, una secuencia especificada por los operandos restantes.

La primera función miembro inserta un elemento con el valor *val* y devuelve un iterador que designa el elemento recién insertado. Usa para insertar un elemento único antes de un lugar designado por un iterador.

La segunda función miembro inserta una repetición de *recuento* elementos del valor *val*. Usa para insertar cero o más elementos contiguos que son todas las copias del mismo valor.

Si `InIt` es un tipo entero, la tercera función miembro se comporta igual que `insert(where, (size_type)first, (value_type)last)`. En caso contrario, inserta la secuencia [`first`, `last`). Usa para insertar cero o más elementos contiguos copiados de otra secuencia.

La cuarta función miembro inserta la secuencia designada por el *derecho*. Usa para insertar una secuencia descrita por un enumerador.

Al insertar un elemento único, el número de copias del elemento es lineal en el número de elementos entre el punto de inserción y el final de cuanto más cerca de la secuencia. (Al insertar uno o más elementos en cualquier extremo de la secuencia, se produce ninguna copia del elemento.) Si `InIt` es un iterador de entrada, la tercera función miembro realiza una inserción única para cada elemento de la secuencia. En caso contrario, al insertar `N` elementos, el número de copias del elemento es lineal en `N` junto con el número de elementos entre el punto de inserción y el final de cuanto más cerca de la secuencia.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_insert.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value using iterator
    cliext::deque<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",
        *c1.insert(++it, L'x'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a repetition of values
    cliext::deque<wchar_t> c2;
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

## <a name="iterator"></a> deque::iterator (STL/CLR)

El tipo de un iterador para la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Comentarios

El tipo describe un objeto de tipo sin especificar `T1` que puede actuar como un iterador de acceso aleatorio de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    cliext::deque<wchar_t>::iterator it = c1.begin();
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

## <a name="op_neq"></a> deque::operator!= (STL/CLR)

Deque comparación de desigualdad.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value>
    bool operator!=(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Contenedor izquierdo que se va a comparar.

*right*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Comentarios

Devuelve la función de operador `!(left == right)`. Usa para probar si *izquierdo* no está ordenado el mismo que *derecho* cuando los dos deques son comparado elemento por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_operator_ne.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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

## <a name="operator"></a> deque::operator(STL/CLR)

Obtiene acceso a un elemento en una posición especificada.

### <a name="syntax"></a>Sintaxis

```cpp
reference operator[](size_type pos);
```

#### <a name="parameters"></a>Parámetros

*pos*<br/>
Posición del elemento al que se accederá.

### <a name="remarks"></a>Comentarios

El operador miembro devuelve un referene al elemento en la posición *pos*. Usarlo para tener acceso a un elemento cuya posición conoce.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_operator_sub.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="pop_back"></a> deque::pop_back (STL/CLR)

Quita el último elemento.

### <a name="syntax"></a>Sintaxis

```cpp
void pop_back();
```

### <a name="remarks"></a>Comentarios

La función miembro quita el último elemento de la secuencia controlada, que debe estar vacío. Se usa para acortar el deque en un elemento en la parte trasera.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_pop_back.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="pop_front"></a> deque::pop_front (STL/CLR)

Quita el primer elemento.

### <a name="syntax"></a>Sintaxis

```cpp
void pop_front();
```

### <a name="remarks"></a>Comentarios

La función miembro quita el primer elemento de la secuencia controlada, que debe estar vacío. Se usa para acortar el deque en un elemento al principio.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_pop_front.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="push_back"></a> deque::push_back (STL/CLR)

Agrega un nuevo elemento de la última.

### <a name="syntax"></a>Sintaxis

```cpp
void push_back(value_type val);
```

### <a name="remarks"></a>Comentarios

La función miembro inserta un elemento con el valor `val` al final de la secuencia controlada. Se usa para anexar otro elemento que el deque.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_push_back.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="push_front"></a> deque::push_front (STL/CLR)

Agrega un nuevo primer elemento.

### <a name="syntax"></a>Sintaxis

```cpp
void push_front(value_type val);
```

### <a name="remarks"></a>Comentarios

La función miembro inserta un elemento con el valor `val` al principio de la secuencia controlada. Se usa para anteponer a otro elemento que el deque.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_push_front.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="rbegin"></a> deque::rbegin (STL/CLR)

Designa el principio de la secuencia controlada inversa.

### <a name="syntax"></a>Sintaxis

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve un iterador inverso que designa el último elemento de la secuencia controlada o inmediatamente después del principio de una secuencia vacía. Por tanto, designa el `beginning` de la secuencia inversa. Se usa para obtener un iterador que designa el `current` principio de la secuencia controlada mostrada en orden inverso, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_rbegin.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    cliext::deque<wchar_t>::reverse_iterator rit = c1.rbegin();
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

## <a name="reference"></a> deque::reference (STL/CLR)

El tipo de una referencia a un elemento.

### <a name="syntax"></a>Sintaxis

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Comentarios

El tipo describe una referencia a un elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_reference.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    cliext::deque<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::deque<wchar_t>::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();

    // modify contents " a b c"
    for (it = c1.begin(); it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::deque<wchar_t>::reference ref = *it;

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

## <a name="rend"></a> deque::rend (STL/CLR)

Designa el final de la secuencia controlada inversa.

### <a name="syntax"></a>Sintaxis

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve un iterador inverso que apunta inmediatamente después del principio de la secuencia controlada. Por tanto, designa el `end` de la secuencia inversa. Se usa para obtener un iterador que designa el `current` final de la secuencia controlada mostrada en orden inverso, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_rend.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    cliext::deque<wchar_t>::reverse_iterator rit = c1.rend();
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

## <a name="resize"></a> deque::resize (STL/CLR)

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
Valor del elemento de relleno.

### <a name="remarks"></a>Comentarios

Las funciones de miembro tanto asegúrese de que [deque:: Size (STL/CLR)](#size) `()` aquí en adelante devuelve *new_size*. Si tiene que realizar la secuencia controlada más larga, la primera función miembro anexa elementos con el valor `value_type()`, mientras que la segunda función miembro anexa elementos con el valor *val*. Para que la secuencia controlada más corta, ambas funciones miembro borrar eficazmente el último elemento [deque:: Size (STL/CLR)](#size) `() -` `new_size` veces. Se usa para asegurarse de que la secuencia controlada tiene tamaño *new_size*, recorte o relleno de la secuencia controlada actual.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_resize.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
// construct an empty container and pad with default values
    cliext::deque<wchar_t> c1;
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

## <a name="reverse_iterator"></a> deque::reverse_iterator (STL/CLR)

El tipo de un iterador invertido para la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Comentarios

El tipo describe un objeto de tipo sin especificar `T3` que puede actuar como un iterador inverso de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_reverse_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" reversed
    cliext::deque<wchar_t>::reverse_iterator rit = c1.rbegin();
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

## <a name="size"></a> deque::size (STL/CLR)

Cuenta el número de elementos.

### <a name="syntax"></a>Sintaxis

```cpp
size_type size();
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve la longitud de la secuencia controlada. Se usa para determinar el número de elementos actualmente en la secuencia controlada. Si lo único que interesa es si la secuencia tiene un tamaño distinto de cero, vea [deque:: Empty (STL/CLR)](#empty)`()`.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_size.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="size_type"></a> deque::size_type (STL/CLR)

El tipo de una distancia con signo entre dos elementos.

### <a name="syntax"></a>Sintaxis

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Comentarios

El tipo describe un recuento de elemento no negativo.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_size_type.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    cliext::deque<wchar_t>::size_type diff = c1.end() - c1.begin();
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="swap"></a> deque::swap (STL/CLR)

Intercambia el contenido de dos contenedores.

### <a name="syntax"></a>Sintaxis

```cpp
void swap(deque<Value>% right);
```

#### <a name="parameters"></a>Parámetros

*right*<br/>
Contenedor con el que se va a intercambiar el contenido.

### <a name="remarks"></a>Comentarios

La función miembro intercambia las secuencias controladas entre `*this` y *derecho*. Lo hace en tiempo constante y no inicia ninguna excepción. Úselo como una forma rápida para intercambiar el contenido de dos contenedores.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_swap.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    cliext::deque<wchar_t> c2(5, L'x');
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

## <a name="to_array"></a> deque::to_array (STL/CLR)

Copia la secuencia controlada a una nueva matriz.

### <a name="syntax"></a>Sintaxis

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve una matriz que contiene la secuencia controlada. Se usa para obtener una copia de la secuencia controlada en forma de matriz.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_to_array.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="value_type"></a> deque::value_type (STL/CLR)

El tipo de un elemento.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla *valor*.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_value_type.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" using value_type
    for (cliext::deque<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it)
        {   // store element in value_type object
        cliext::deque<wchar_t>::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="op_lt"></a> operador&lt; (deque) (STL/CLR)

Deque comparación menor.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value>
    bool operator<(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Contenedor izquierdo que se va a comparar.

*right*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Comentarios

El operador función devuelve true si, para la posición más baja `i` que `!(right[i] < left[i])` es también true que `left[i] < right[i]`. De lo contrario, devuelve `left->size() < right->size()` usarla para probar si *izquierdo* está ordenado antes *derecho* cuando los dos deques son comparado elemento por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_operator_lt.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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

## <a name="op_lteq"></a> operator&lt;= (deque) (STL/CLR)

Deque menor o igual comparación.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value>
    bool operator<=(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Contenedor izquierdo que se va a comparar.

*right*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Comentarios

Devuelve la función de operador `!(right < left)`. Se usa para probar si *izquierdo* no está ordenado después *derecho* cuando los dos deques son comparado elemento por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_operator_le.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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

## <a name="op_as"></a> operator= (deque) (STL/CLR)

Reemplaza la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
deque<Value>% operator=(deque<Value>% right);
```

#### <a name="parameters"></a>Parámetros

*right*<br/>
Contenedor que se va a copiar.

### <a name="remarks"></a>Comentarios

Las copias de operador miembro *derecho* al objeto, a continuación, devuelve `*this`. Se usa para reemplazar la secuencia controlada por una copia de la secuencia controlada en *derecho*.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_operator_as.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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

## <a name="op_eq"></a> operator== (deque) (STL/CLR)

Comparación de igualdad de deque.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value>
    bool operator==(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Contenedor izquierdo que se va a comparar.

*right*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Comentarios

Devuelve true solo si las secuencias se controlan mediante la función de operador *izquierdo* y *derecho* tienen la misma longitud y, para cada posición `i`, `left[i] ==` `right[i]`. Se usa para probar si *izquierdo* se ordenan igual *derecho* cuando los dos deques son comparado elemento por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_operator_eq.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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

## <a name="op_gt"></a> operador&gt; (deque) (STL/CLR)

Comparación mayor que el deque.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value>
    bool operator>(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Contenedor izquierdo que se va a comparar.

*right*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Comentarios

Devuelve la función de operador `right` `<` `left`. Se usa para probar si *izquierdo* se ordena después *derecho* cuando los dos deques son comparado elemento por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_operator_gt.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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

## <a name="op_gteq"></a> operator&gt;= (deque) (STL/CLR)

Comparación mayor o igual de deque.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value>
    bool operator>=(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Contenedor izquierdo que se va a comparar.

*right*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Comentarios

Devuelve la función de operador `!(left` `<` `right)`. Usa para probar si *izquierdo* no está ordenado antes *derecho* cuando los dos deques son comparado elemento por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_deque_operator_ge.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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