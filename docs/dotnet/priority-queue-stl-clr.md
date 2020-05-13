---
title: priority_queue (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::priority_queue
- cliext::priority_queue::assign
- cliext::priority_queue::const_reference
- cliext::priority_queue::container_type
- cliext::priority_queue::difference_type
- cliext::priority_queue::empty
- cliext::priority_queue::generic_container
- cliext::priority_queue::generic_value
- cliext::priority_queue::get_container
- cliext::priority_queue::operator=
- cliext::priority_queue::pop
- cliext::priority_queue::priority_queue
- cliext::priority_queue::push
- cliext::priority_queue::reference
- cliext::priority_queue::size
- cliext::priority_queue::size_type
- cliext::priority_queue::to_array
- cliext::priority_queue::top
- cliext::priority_queue::top_item
- cliext::priority_queue::value_comp
- cliext::priority_queue::value_compare
- cliext::priority_queue::value_type
helpviewer_keywords:
- priority_queue class [STL/CLR]
- <queue> header [STL/CLR]
- <cliext/queue> header [STL/CLR]
- assign member [STL/CLR]
- const_reference member [STL/CLR]
- container_type member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- generic_container member [STL/CLR]
- generic_value member [STL/CLR]
- get_container member [STL/CLR]
- operator= member [STL/CLR]
- pop member [STL/CLR]
- priority_queue member [STL/CLR]
- push member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- to_array member [STL/CLR]
- top member [STL/CLR]
- top_item member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 4d0000d3-68ff-4c4b-8157-7060540136f5
ms.openlocfilehash: e21e7ba4dc3a4ed270548506ac1a9e37a2c1a23a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208473"
---
# <a name="priority_queue-stlclr"></a>priority_queue (STL/CLR)

La clase de plantilla describe un objeto que controla una secuencia ordenada de longitud variable de elementos que tiene acceso limitado. Use el adaptador de contenedor `priority_queue` para administrar un contenedor subyacente como una cola de prioridad.

En la descripción siguiente, `GValue` es igual que el *valor* a menos que sea un tipo de referencia, en cuyo caso se `Value^`. Del mismo modo, `GContainer` es igual que el *contenedor* a menos que el último sea un tipo de referencia, en cuyo caso se `Container^`.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename Value,
    typename Container>
    ref class priority_queue
        System::ICloneable,
        Microsoft::VisualC::StlClr::IPriorityQueue<GValue, GContainer>
    { ..... };
```

### <a name="parameters"></a>Parámetros

*Valor*<br/>
Tipo de un elemento de la secuencia controlada.

*Contenedor*<br/>
Tipo del contenedor subyacente.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<cliext (/queue >

**Espacio de nombres:** cliext (

## <a name="declarations"></a>Declaraciones

|Definición de tipo|Descripción|
|---------------------|-----------------|
|[priority_queue::const_reference (STL/CLR)](#const_reference)|El tipo de una referencia constante a un elemento.|
|[priority_queue::container_type (STL/CLR)](#container_type)|Tipo del contenedor subyacente.|
|[priority_queue::difference_type (STL/CLR)](#difference_type)|El tipo de una distancia con signo entre dos elementos.|
|[priority_queue::generic_container (STL/CLR)](#generic_container)|Tipo de la interfaz genérica para el adaptador de contenedor.|
|[priority_queue::generic_value (STL/CLR)](#generic_value)|Tipo de un elemento de la interfaz genérica para el adaptador de contenedor.|
|[priority_queue::reference (STL/CLR)](#reference)|El tipo de una referencia a un elemento.|
|[priority_queue::size_type (STL/CLR)](#size_type)|El tipo de una distancia con signo entre dos elementos.|
|[priority_queue::value_compare (STL/CLR)](#value_compare)|Delegado de ordenación de dos elementos.|
|[priority_queue::value_type (STL/CLR)](#value_type)|El tipo de un elemento.|

|Función miembro|Descripción|
|---------------------|-----------------|
|[priority_queue::assign (STL/CLR)](#assign)|Reemplaza todos los elementos.|
|[priority_queue::empty (STL/CLR)](#empty)|Comprueba si no hay ningún elemento presente.|
|[priority_queue::get_container (STL/CLR)](#get_container)|Tiene acceso al contenedor subyacente.|
|[priority_queue::pop (STL/CLR)](#pop)|Quita el elemento de prioridad hghest.|
|[priority_queue::priority_queue (STL/CLR)](#priority_queue)|Construye un objeto contenedor.|
|[priority_queue::push (STL/CLR)](#push)|Agrega un nuevo elemento.|
|[priority_queue::size (STL/CLR)](#size)|Cuenta el número de elementos.|
|[priority_queue::top (STL/CLR)](#top)|Tiene acceso al elemento de prioridad más alta.|
|[priority_queue::to_array (STL/CLR)](#to_array)|Copia la secuencia controlada en una nueva matriz.|
|[priority_queue::value_comp (STL/CLR)](#value_comp)|Copia el delegado de ordenación de dos elementos.|

|Propiedad|Descripción|
|--------------|-----------------|
|[priority_queue::top_item (STL/CLR)](#top_item)|Tiene acceso al elemento de prioridad más alta.|

|Operator|Descripción|
|--------------|-----------------|
|[priority_queue::operator= (STL/CLR)](#op_as)|Reemplaza la secuencia controlada.|

## <a name="interfaces"></a>Interfaces

|Interfaz|Descripción|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplicar un objeto.|
|IPriorityQueue\<valor, contenedor >|Mantenga el adaptador de contenedor genérico.|

## <a name="remarks"></a>Observaciones

El objeto asigna y libera almacenamiento para la secuencia que controla a través de un contenedor subyacente, de tipo `Container`, que almacena `Value` elementos y crece a petición. Mantiene la secuencia ordenada como un montón, con el elemento de prioridad más alta (el elemento superior) accesible y extraíble. El objeto restringe el acceso para insertar nuevos elementos y extraer solo el elemento de prioridad más alta, implementando una cola de prioridad.

El objeto ordena la secuencia que controla llamando a un objeto delegado almacenado de tipo [priority_queue:: value_compare (STL/CLR)](../dotnet/priority-queue-value-compare-stl-clr.md). Puede especificar el objeto delegado almacenado al construir el priority_queue; Si no especifica ningún objeto delegado, el valor predeterminado es el `operator<(value_type, value_type)`de comparación. Puede tener acceso a este objeto almacenado llamando a la función miembro [priority_queue:: value_comp (STL/CLR)](../dotnet/priority-queue-value-comp-stl-clr.md)`()`.

Dicho objeto delegado debe imponer una ordenación débil estricta en los valores de tipo [priority_queue:: value_type (STL/CLR)](../dotnet/priority-queue-value-type-stl-clr.md). Esto significa que, para dos claves `X` y `Y`:

`value_comp()(X, Y)` devuelve el mismo resultado booleano en cada llamada.

Si `value_comp()(X, Y)` es true, `value_comp()(Y, X)` debe ser false.

Si `value_comp()(X, Y)` es true, se dice que `X` se ordena antes que `Y`.

Si `!value_comp()(X, Y) && !value_comp()(Y, X)` es true, se dice que `X` y `Y` tienen una ordenación equivalente.

Para cualquier elemento `X` que preceda a `Y` en la secuencia controlada, `key_comp()(Y, X)` es false. (Para el objeto de delegado predeterminado, las claves nunca disminuyen en el valor).

El elemento de prioridad más alta es, por lo tanto, uno de los elementos que no se ordenan antes que ningún otro elemento.

Puesto que el contenedor subyacente mantiene los elementos ordenados como un montón:

El contenedor debe admitir iteradores de acceso aleatorio.

Los elementos con una ordenación equivalente se pueden extraer en un orden diferente al que se insertaron. (El orden no es estable).

Por lo tanto, los candidatos para el contenedor subyacente incluyen [deque (STL/CLR)](../dotnet/deque-stl-clr.md) y [vector (STL/CLR)](../dotnet/vector-stl-clr.md).

## <a name="members"></a>Members

## <a name="priority_queueassign-stlclr"></a><a name="assign"></a>priority_queue:: Assign (STL/CLR)

Reemplaza todos los elementos.

### <a name="syntax"></a>Sintaxis

```cpp
void assign(priority_queue<Value, Container>% right);
```

#### <a name="parameters"></a>Parámetros

*right*<br/>
Adaptador de contenedor que se va a insertar.

### <a name="remarks"></a>Observaciones

La función miembro asigna `right.get_container()` al contenedor subyacente. Se usa para cambiar todo el contenido de la cola.

### <a name="example"></a>Ejemplo

```cpp
// cliext_priority_queue_assign.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign a repetition of values
    Mypriority_queue c2;
    c2.assign(c1);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
```

## <a name="priority_queueconst_reference-stlclr"></a><a name="const_reference"></a>priority_queue:: const_reference (STL/CLR)

El tipo de una referencia constante a un elemento.

### <a name="syntax"></a>Sintaxis

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Observaciones

El tipo describe una referencia constante a un elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_priority_queue_const_reference.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display reversed contents " c b a"
    for (; !c1.empty(); c1.pop())
        {   // get a const reference to an element
        Mypriority_queue::const_reference cref = c1.top();
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="priority_queuecontainer_type-stlclr"></a><a name="container_type"></a>priority_queue:: container_type (STL/CLR)

Tipo del contenedor subyacente.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Container value_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla `Container`.

### <a name="example"></a>Ejemplo

```cpp
// cliext_priority_queue_container_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c" using container_type
    Mypriority_queue::container_type wc1 = c1.get_container();
    for each (wchar_t elem in wc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
```

## <a name="priority_queuedifference_type-stlclr"></a><a name="difference_type"></a>priority_queue::d ifference_type (STL/CLR)

Tipos de una distancia con signo entre dos elementos.

### <a name="syntax"></a>Sintaxis

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Observaciones

El tipo describe un recuento de elementos posiblemente negativos.

### <a name="example"></a>Ejemplo

```cpp
// cliext_priority_queue_difference_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute negative difference
    Mypriority_queue::difference_type diff = c1.size();
    c1.push(L'd');
    c1.push(L'e');
    diff -= c1.size();
    System::Console::WriteLine("pushing 2 = {0}", diff);

    // compute positive difference
    diff = c1.size();
    c1.pop();
    c1.pop();
    c1.pop();
    diff -= c1.size();
    System::Console::WriteLine("popping 3 = {0}", diff);
    return (0);
    }
```

```Output
c a b
pushing 2 = -2
popping 3 = 3
```

## <a name="priority_queueempty-stlclr"></a><a name="empty"></a>priority_queue:: Empty (STL/CLR)

Comprueba si no hay ningún elemento presente.

### <a name="syntax"></a>Sintaxis

```cpp
bool empty();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve true para una secuencia controlada vacía. Es equivalente a [priority_queue:: Size (STL/CLR)](../dotnet/priority-queue-size-stl-clr.md)`() == 0`. Se utiliza para comprobar si la priority_queue está vacía.

### <a name="example"></a>Ejemplo

```cpp
// cliext_priority_queue_empty.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());

    // clear the container and reinspect
    c1.pop();
    c1.pop();
    c1.pop();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());
    return (0);
    }
```

```Output
c a b
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="priority_queuegeneric_container-stlclr"></a><a name="generic_container"></a>priority_queue:: generic_container (STL/CLR)

Tipo de la interfaz genérica para el contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Microsoft::VisualC::StlClr::IPriorityQueue<Value>
    generic_container;
```

### <a name="remarks"></a>Observaciones

El tipo describe la interfaz genérica para esta clase de adaptador de contenedor de plantillas.

### <a name="example"></a>Ejemplo

```cpp
// cliext_priority_queue_generic_container.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Mypriority_queue::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->push(L'd');
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify original and display generic
    c1.push(L'e');
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
d c b a
e d b a c
```

## <a name="priority_queuegeneric_value-stlclr"></a><a name="generic_value"></a>priority_queue:: generic_value (STL/CLR)

Tipo de un elemento que se va a usar con la interfaz genérica del contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto de tipo `GValue` que describe el valor del elemento almacenado que se va a usar con la interfaz genérica para esta clase de contenedor de plantillas. (`GValue` es `value_type` o `value_type^` si `value_type` es un tipo de referencia).

### <a name="example"></a>Ejemplo

```cpp
// cliext_priority_queue_generic_value.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get interface to container
    Mypriority_queue::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display in priority order using generic_value
    for (; !gc1->empty(); gc1->pop())
        {
        Mypriority_queue::generic_value elem = gc1->top();

        System::Console::Write("{0} ", elem);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
c b a
```

## <a name="priority_queueget_container-stlclr"></a><a name="get_container"></a>priority_queue:: get_container (STL/CLR)

Tiene acceso al contenedor subyacente.

### <a name="syntax"></a>Sintaxis

```cpp
container_type get_container();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve el contenedor subyacente. Se usa para omitir las restricciones impuestas por el contenedor del contenedor.

### <a name="example"></a>Ejemplo

```cpp
// cliext_priority_queue_get_container.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
```

## <a name="priority_queueoperator-stlclr"></a><a name="op_as"></a>priority_queue:: Operator = (STL/CLR)

Reemplaza la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
priority_queue <Value, Container>% operator=(priority_queue <Value, Container>% right);
```

#### <a name="parameters"></a>Parámetros

*right*<br/>
Adaptador de contenedor que se va a copiar.

### <a name="remarks"></a>Observaciones

El operador miembro copia *directamente* en el objeto y, a continuación, devuelve `*this`. Se usa para reemplazar la secuencia controlada por una copia de la secuencia controlada a la *derecha*.

### <a name="example"></a>Ejemplo

```cpp
// cliext_priority_queue_operator_as.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mypriority_queue c2;
    c2 = c1;
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
```

## <a name="priority_queuepop-stlclr"></a><a name="pop"></a>priority_queue::p OP (STL/CLR)

Quita el elemento de proirity más alto.

### <a name="syntax"></a>Sintaxis

```cpp
void pop();
```

### <a name="remarks"></a>Observaciones

La función miembro quita el elemento de prioridad máxima de la secuencia controlada, que no debe estar vacío. Se usa para acortar la cola en un elemento de la parte posterior.

### <a name="example"></a>Ejemplo

```cpp
// cliext_priority_queue_pop.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // pop an element and redisplay
    c1.pop();
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
b a
```

## <a name="priority_queuepriority_queue-stlclr"></a><a name="priority_queue"></a>priority_queue::p riority_queue (STL/CLR)

Construye un objeto de adaptador de contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
priority_queue();
priority_queue(priority_queue<Value, Container> right);
priority_queue(priority_queue<Value, Container> right);
explicit priority_queue(value_compare^ pred);
priority_queue(value_compare^ pred, container_type% cont);
template<typename InIt>
    priority_queue(InIt first, InIt last);
template<typename InIt>
    priority_queue(InIt first, InIt last,
        value_compare^ pred);
template<typename InIt>
    priority_queue(InIt first, InIt last,
        value_compare^ pred, container_type% cont);
```

#### <a name="parameters"></a>Parámetros

*continuación*<br/>
Contenedor que se va a copiar.

*first*<br/>
Principio del intervalo que se va a insertar.

*last*<br/>
Final del intervalo que se va a insertar.

*pronostica*<br/>
Predicado de ordenación para la secuencia controlada.

*right*<br/>
Objeto o intervalo que se va a insertar.

### <a name="remarks"></a>Observaciones

El constructor:

`priority_queue();`

crea un contenedor ajustado vacío, con el predicado de ordenación predeterminado. Se usa para especificar una secuencia controlada inicial vacía, con el predicado de ordenación predeterminado.

El constructor:

`priority_queue(priority_queue<Value, Container>% right);`

crea un contenedor ajustado que es una copia de `right.get_container()`, con el predicado de ordenación `right.value_comp()`. Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de cola a la *derecha*, con el mismo predicado de ordenación.

El constructor:

`priority_queue(priority_queue<Value, Container>^ right);`

crea un contenedor ajustado que es una copia de `right->get_container()`, con el predicado de ordenación `right->value_comp()`. Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de cola `*right`, con el mismo predicado de ordenación.

El constructor:

`explicit priority_queue(value_compare^ pred);`

crea un contenedor ajustado vacío, con el predicado de ordenación *Pred*. Se usa para especificar una secuencia controlada inicial vacía, con el predicado de ordenación especificado.

El constructor:

`priority_queue(value_compare^ pred, container_type cont);`

crea un contenedor ajustado vacío, con el predicado de ordenación *Pred*y, a continuación, inserta todos los elementos de *cont* . se usa para especificar una secuencia controlada inicial de un contenedor existente, con el predicado de ordenación especificado.

El constructor:

`template<typename InIt> priority_queue(InIt first, InIt last);`

crea un contenedor ajustado vacío con el predicado de ordenación predeterminado y, a continuación, envía la secuencia [`first`, `last`). Se usa para especificar una secuencia controlada inicial de un eqeuence especificado, con el predicado de ordenación especificado.

El constructor:

`template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred);`

crea un contenedor ajustado vacío, con el predicado de ordenación *Pred*y, a continuación, envía la secuencia [`first`, `last`). Se usa para especificar una secuencia controlada inicial de un seqeuence especificado, con el predicado de ordenación especificado.

El constructor:

`template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred, container_type% cont);`

crea un contenedor ajustado vacío, con el predicado de ordenación *Pred*y, a continuación, envía todos los elementos de *cont* más la secuencia [`first`, `last`). Se usa para especificar una secuencia controlada inicial de un contenedor existente y un seqeuence especificado, con el predicado de ordenación especificado.

### <a name="example"></a>Ejemplo

```cpp
// cliext_priority_queue_construct.cpp
// compile with: /clr
#include <cliext/queue>
#include <cliext/deque>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
typedef cliext::deque<wchar_t> Mydeque;
int main()
    {
// construct an empty container
    Mypriority_queue c1;
    Mypriority_queue::container_type^ wc1 = c1.get_container();
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');
    for each (wchar_t elem in wc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule
    Mypriority_queue c2 = cliext::greater<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    for each (wchar_t elem in wc1)
        c2.push(elem);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule by copying an underlying container
    Mypriority_queue c2x =
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);
   for each (wchar_t elem in c2x.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range
    Mypriority_queue c3(wc1->begin(), wc1->end());
    for each (wchar_t elem in c3.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Mypriority_queue c4(wc1->begin(), wc1->end(),
        cliext::greater<wchar_t>());
    for each (wchar_t elem in c4.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range, another container, and an ordering rule
    Mypriority_queue c5(wc1->begin(), wc1->end(),
        cliext::greater<wchar_t>(), *wc1);
    for each (wchar_t elem in c5.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct from a generic container
    Mypriority_queue c6(c3);
    for each (wchar_t elem in c6.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    Mypriority_queue c7(%c3);
    for each (wchar_t elem in c7.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule, by copying an underlying container
    Mypriority_queue c8 =
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);
    for each (wchar_t elem in c8.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
    }
```

```Output
size() = 0
c a b
size() = 0
a c b
a c b
c a b
a c b
a a b c c b
c a b
c a b
a c b
```

## <a name="priority_queuepush-stlclr"></a><a name="push"></a>priority_queue::p uscripción (STL/CLR)

Agrega un nuevo elemento.

### <a name="syntax"></a>Sintaxis

```cpp
void push(value_type val);
```

### <a name="remarks"></a>Observaciones

La función miembro inserta un elemento con el valor `val` en la secuencia controlada y reordena la secuencia controlada para mantener la disciplina del montón. Se utiliza para agregar otro elemento a la cola.

### <a name="example"></a>Ejemplo

```cpp
// cliext_priority_queue_push.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
```

## <a name="priority_queuereference-stlclr"></a><a name="reference"></a>priority_queue:: Reference (STL/CLR)

El tipo de una referencia a un elemento.

### <a name="syntax"></a>Sintaxis

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Observaciones

El tipo describe una referencia a un elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_priority_queue_reference.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify top of priority_queue and redisplay
    Mypriority_queue::reference ref = c1.top();
    ref = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
x a b
```

## <a name="priority_queuesize-stlclr"></a><a name="size"></a>priority_queue:: Size (STL/CLR)

Cuenta el número de elementos.

### <a name="syntax"></a>Sintaxis

```cpp
size_type size();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve la longitud de la secuencia controlada. Se utiliza para determinar el número de elementos que hay actualmente en la secuencia controlada. Si todo lo que le interesa es si la secuencia tiene un tamaño distinto de cero, vea [priority_queue:: Empty (STL/CLR)](../dotnet/priority-queue-empty-stl-clr.md)`()`.

### <a name="example"></a>Ejemplo

```cpp
// cliext_priority_queue_size.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());

    // pop an item and reinspect
    c1.pop();
    System::Console::WriteLine("size() = {0} after popping", c1.size());

    // add two elements and reinspect
    c1.push(L'a');
    c1.push(L'b');
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
c a b
size() = 3 starting with 3
size() = 2 after popping
size() = 4 after adding 2
```

## <a name="priority_queuesize_type-stlclr"></a><a name="size_type"></a>priority_queue:: size_type (STL/CLR)

El tipo de una distancia con signo entre dos elementos.

### <a name="syntax"></a>Sintaxis

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Observaciones

El tipo describe un recuento de elementos no negativos.

### <a name="example"></a>Ejemplo

```cpp
// cliext_priority_queue_size_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Mypriority_queue::size_type diff = c1.size();
    c1.pop();
    c1.pop();
    diff -= c1.size();
    System::Console::WriteLine("size difference = {0}", diff);
    return (0);
    }
```

```Output
c a b
size difference = 2
```

## <a name="priority_queueto_array-stlclr"></a><a name="to_array"></a>priority_queue:: to_array (STL/CLR)

Copia la secuencia controlada en una nueva matriz.

### <a name="syntax"></a>Sintaxis

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve una matriz que contiene la secuencia controlada. Se utiliza para obtener una copia de la secuencia controlada en forma de matriz.

### <a name="example"></a>Ejemplo

```cpp
// cliext_priority_queue_to_array.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // copy the container and modify it
    cli::array<wchar_t>^ a1 = c1.to_array();

    c1.push(L'd');
    for each (wchar_t elem in c1.get_container())
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
d c b a
c a b
```

## <a name="priority_queuetop-stlclr"></a><a name="top"></a>priority_queue:: Top (STL/CLR)

Tiene acceso al elemento de prioridad más alta.

### <a name="syntax"></a>Sintaxis

```cpp
reference top();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve una referencia al elemento superior (prioridad más alta) de la secuencia controlada, que no debe estar vacía. Se usa para tener acceso al elemento de prioridad más alta, cuando se sabe que existe.

### <a name="example"></a>Ejemplo

```cpp
// cliext_priority_queue_top.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last item
    System::Console::WriteLine("top() = {0}", c1.top());

    // alter last item and reinspect
    c1.top() = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

## <a name="priority_queuetop_item-stlclr"></a><a name="top_item"></a>priority_queue:: top_item (STL/CLR)

Tiene acceso al elemento de prioridad más alta.

### <a name="syntax"></a>Sintaxis

```cpp
property value_type back_item;
```

### <a name="remarks"></a>Observaciones

La propiedad tiene acceso al elemento superior (prioridad más alta) de la secuencia controlada, que no debe estar vacía. Se usa para leer o escribir el elemento de prioridad más alta, cuando se sabe que existe.

### <a name="example"></a>Ejemplo

```cpp
// cliext_priority_queue_top_item.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last item
    System::Console::WriteLine("top_item = {0}", c1.top_item);

    // alter last item and reinspect
    c1.top_item = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
top_item = c
x a b
```

## <a name="priority_queuevalue_comp-stlclr"></a><a name="value_comp"></a>priority_queue:: value_comp (STL/CLR)

Copia el delegado de ordenación de dos elementos.

### <a name="syntax"></a>Sintaxis

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve el delegado de ordenación que se usa para ordenar la secuencia controlada. Se usa para comparar dos valores.

### <a name="example"></a>Ejemplo

```cpp
// cliext_priority_queue_value_comp.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    Mypriority_queue::value_compare^ vcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mypriority_queue c2 = cliext::greater<wchar_t>();
    vcomp = c2.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
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

## <a name="priority_queuevalue_compare-stlclr"></a><a name="value_compare"></a>priority_queue:: value_compare (STL/CLR)

Delegado de ordenación para dos valores.

### <a name="syntax"></a>Sintaxis

```cpp
binary_delegate<value_type, value_type, int> value_compare;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del delegado que determina si el primer argumento se ordena antes que el segundo.

### <a name="example"></a>Ejemplo

```cpp
// cliext_priority_queue_value_compare.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    Mypriority_queue::value_compare^ vcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mypriority_queue c2 = cliext::greater<wchar_t>();
    vcomp = c2.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
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

## <a name="priority_queuevalue_type-stlclr"></a><a name="value_type"></a>priority_queue:: value_type (STL/CLR)

El tipo de un elemento.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del *valor*del parámetro de plantilla.

### <a name="example"></a>Ejemplo

```cpp
// cliext_priority_queue_value_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display reversed contents " a b c" using value_type
    for (; !c1.empty(); c1.pop())
        {   // store element in value_type object
        Mypriority_queue::value_type val = c1.top();

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```
