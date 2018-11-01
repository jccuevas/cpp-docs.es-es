---
title: stack (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::stack
- cliext::operator!=
- cliext::operator<
- cliext::operator<=
- cliext::operator==
- cliext::operator>
- cliext::operator>=
- cliext::stack::assign
- cliext::stack::const_reference
- cliext::stack::container_type
- cliext::stack::difference_type
- cliext::stack::empty
- cliext::stack::generic_container
- cliext::stack::generic_value
- cliext::stack::get_container
- cliext::stack::operator=
- cliext::stack::pop
- cliext::stack::push
- cliext::stack::reference
- cliext::stack::size
- cliext::stack::size_type
- cliext::stack::stack
- cliext::stack::to_array
- cliext::stack::top
- cliext::stack::top_item
- cliext::stack::value_type
helpviewer_keywords:
- <stack> header [STL/CLR]
- <cliext/stack> header [STL/CLR]
- stack class [STL/CLR]
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> member [STL/CLR]
- operator>= member [STL/CLR]
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
- push member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- stack member [STL/CLR]
- to_array member [STL/CLR]
- top member [STL/CLR]
- top_item member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 6ee96b9f-8a33-4cf7-b7e0-6535c24bdefb
ms.openlocfilehash: ec3863796f7c49c155af61576c15c1ca8a9d5109
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513885"
---
# <a name="stack-stlclr"></a>stack (STL/CLR)

La clase de plantilla describe un objeto que controla una secuencia de elementos de longitud variable que tiene acceso de último en entrar es el primero. Utilice el adaptador de contenedor `stack` para administrar un contenedor subyacente como una pila de inserción.

En la descripción siguiente, `GValue` es el mismo que *valor* a menos que este último es un tipo de referencia, en cuyo caso es `Value^`. De forma similar, `GContainer` es el mismo que *contenedor* a menos que este último es un tipo de referencia, en cuyo caso es `Container^`.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename Value,
    typename Container>
    ref class stack
        :   public
        System::ICloneable,
        Microsoft::VisualC::StlClr::IStack<GValue, GContainer>
    { ..... };
```

### <a name="parameters"></a>Parámetros

*Valor*<br/>
Tipo de un elemento de la secuencia controlada.

*Contenedor*<br/>
Tipo del contenedor subyacente.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<cliext/pila >

**Namespace:** cliext

## <a name="declarations"></a>Declaraciones

|Definición de tipo|Descripción|
|---------------------|-----------------|
|[stack::const_reference (STL/CLR)](#const_reference)|El tipo de una referencia constante a un elemento.|
|[stack::container_type (STL/CLR)](#container_type)|Tipo del contenedor subyacente.|
|[stack::difference_type (STL/CLR)](#difference_type)|El tipo de una distancia con signo entre dos elementos.|
|[stack::generic_container (STL/CLR)](#generic_container)|El tipo de la interfaz genérica para el adaptador de contenedor.|
|[stack::generic_value (STL/CLR)](#generic_value)|El tipo de un elemento de la interfaz genérica para el adaptador de contenedor.|
|[stack::reference (STL/CLR)](#reference)|El tipo de una referencia a un elemento.|
|[stack::size_type (STL/CLR)](#size_type)|El tipo de una distancia con signo entre dos elementos.|
|[stack::value_type (STL/CLR)](#value_type)|El tipo de un elemento.|

|Función miembro|Descripción|
|---------------------|-----------------|
|[stack::assign (STL/CLR)](#assign)|Reemplaza todos los elementos.|
|[stack::empty (STL/CLR)](#empty)|Comprueba si no hay ningún elemento presente.|
|[stack::get_container (STL/CLR)](#get_container)|Obtiene acceso al contenedor subyacente.|
|[stack::pop (STL/CLR)](#pop)|Quita el último elemento.|
|[stack::push (STL/CLR)](#push)|Agrega un nuevo elemento de la última.|
|[stack::size (STL/CLR)](#size)|Cuenta el número de elementos.|
|[stack::stack (STL/CLR)](#stack)|Construye un objeto contenedor.|
|[stack::top (STL/CLR)](#top)|Obtiene acceso al último elemento.|
|[stack::to_array (STL/CLR)](#to_array)|Copia la secuencia controlada a una nueva matriz.|

|Property|Descripción|
|--------------|-----------------|
|[stack::top_item (STL/CLR)](#top_item)|Obtiene acceso al último elemento.|

|Operador|Descripción|
|--------------|-----------------|
|[stack::operator= (STL/CLR)](#op_as)|Reemplaza la secuencia controlada.|
|[operator!= (stack) (STL/CLR)](#op_neq)|Determina si un `stack` no es igual a otro objeto `stack` objeto.|
|[operator< (stack) (STL/CLR)](#op_lt)|Determina si un `stack` objeto es menor que otro `stack` objeto.|
|[operator<= (stack) (STL/CLR)](#op_lteq)|Determina si un `stack` objeto es menor o igual que otro `stack` objeto.|
|[operator== (stack) (STL/CLR)](#op_eq)|Determina si un `stack` es igual a otro objeto `stack` objeto.|
|[operator> (stack) (STL/CLR)](#op_gt)|Determina si un `stack` es mayor que otro objeto `stack` objeto.|
|[operator>= (stack) (STL/CLR)](#op_gteq)|Determina si un `stack` objeto es mayor o igual que otro `stack` objeto.|

## <a name="interfaces"></a>Interfaces

|Interfaz|Descripción|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplicar un objeto.|
|IStack\<valor, el contenedor >|Mantener el adaptador de contenedor genérico.|

## <a name="remarks"></a>Comentarios

El objeto asigna y libera almacenamiento para la secuencia que controla a través de un contenedor subyacente, de tipo *contenedor*, que almacena *valor* elementos y crece a petición. El objeto restringe el acceso a insertando e incluyendo solo el último elemento, implementa una cola de último en entrar es el primero (también conocido como una cola LIFO o pila).

## <a name="members"></a>Miembros

## <a name="assign"></a> Stack::assign (STL/CLR)

Reemplaza todos los elementos.

### <a name="syntax"></a>Sintaxis

```cpp
void assign(stack<Value, Container>% right);
```

#### <a name="parameters"></a>Parámetros

*right*<br/>
Adaptador de contenedor se va a insertar.

### <a name="remarks"></a>Comentarios

La función miembro asigna `right.get_container()` al contenedor subyacente. Usa para cambiar todo el contenido de la pila.

### <a name="example"></a>Ejemplo

```cpp
// cliext_stack_assign.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign a repetition of values
    Mystack c2;
    c2.assign(c1);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="const_reference"></a> Stack::const_reference (STL/CLR)

El tipo de una referencia constante a un elemento.

### <a name="syntax"></a>Sintaxis

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Comentarios

El tipo describe una referencia constante a un elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_stack_const_reference.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display reversed contents " c b a"
    for (; !c1.empty(); c1.pop())
        {   // get a const reference to an element
        Mystack::const_reference cref = c1.top();
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="container_type"></a> Stack:: container_type (STL/CLR)

Tipo del contenedor subyacente.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Container value_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla *Container*.

### <a name="example"></a>Ejemplo

```cpp
// cliext_stack_container_type.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c" using container_type
    Mystack::container_type wc1 = c1.get_container();
    for each (wchar_t elem in wc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="difference_type"></a> Stack::difference_type (STL/CLR)

Los tipos de una distancia con signo entre dos elementos.

### <a name="syntax"></a>Sintaxis

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Comentarios

El tipo describe un recuento de elemento posiblemente negativo.

### <a name="example"></a>Ejemplo

```cpp
// cliext_stack_difference_type.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute negative difference
    Mystack::difference_type diff = c1.size();
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
a b c
pushing 2 = -2
popping 3 = 3
```

## <a name="empty"></a> Stack:: Empty (STL/CLR)

Comprueba si no hay ningún elemento presente.

### <a name="syntax"></a>Sintaxis

```cpp
bool empty();
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve true para una secuencia controlada vacía. Equivale a [Stack:: Size (STL/CLR)](../dotnet/stack-size-stl-clr.md)`() == 0`. Usa para comprobar si la pila está vacía.

### <a name="example"></a>Ejemplo

```cpp
// cliext_stack_empty.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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
a b c
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="generic_container"></a> Stack::generic_container (STL/CLR)

El tipo de la interfaz genérica para el adaptador de contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Microsoft::VisualC::StlClr::IStack<Value>
    generic_container;
```

### <a name="remarks"></a>Comentarios

El tipo describe la interfaz genérica para esta clase de adaptador de contenedor de plantilla.

### <a name="example"></a>Ejemplo

```cpp
// cliext_stack_generic_container.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get interface to container
    Mystack::generic_container^ gc1 = %c1;
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
a b c
a b c
a b c d
a b c d e
```

## <a name="generic_value"></a> Stack::generic_value (STL/CLR)

El tipo de un elemento para su uso con la interfaz genérica para el contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Comentarios

El tipo describe un objeto de tipo `GValue` que describe el valor del elemento almacenados para su uso con la interfaz genérica para esta clase de contenedor de plantilla. (`GValue` sea `value_type` o `value_type^` si `value_type` es un tipo ref.)

### <a name="example"></a>Ejemplo

```cpp
// cliext_stack_generic_value.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get interface to container
    Mystack::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// display in reverse using generic_value
    for (; !gc1->empty(); gc1->pop())
        {
        Mystack::generic_value elem = gc1->top();

        System::Console::Write("{0} ", elem);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
c b a
```

## <a name="get_container"></a> Stack::get_container (STL/CLR)

Obtiene acceso al contenedor subyacente.

### <a name="syntax"></a>Sintaxis

```cpp
container_type^ get_container();
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve un identificador para el contenedor subyacente. Usa para omitir las restricciones impuestas por el contenedor del contenedor.

### <a name="example"></a>Ejemplo

```cpp
// cliext_stack_get_container.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c" using container_type
    Mystack::container_type wc1 = c1.get_container();
    for each (wchar_t elem in wc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="op_as"></a> Stack:: operator = (STL/CLR)

Reemplaza la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
stack <Value, Container>% operator=(stack <Value, Container>% right);
```

#### <a name="parameters"></a>Parámetros

*right*<br/>
Adaptador de contenedor para copiar.

### <a name="remarks"></a>Comentarios

Las copias de operador miembro *derecho* al objeto, a continuación, devuelve `*this`. Se usa para reemplazar la secuencia controlada por una copia de la secuencia controlada en *derecho*.

### <a name="example"></a>Ejemplo

```cpp
// cliext_stack_operator_as.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
    c2 = c1;
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="pop"></a> Stack:: POP (STL/CLR)

Quita el último elemento.

### <a name="syntax"></a>Sintaxis

```cpp
void pop();
```

### <a name="remarks"></a>Comentarios

La función miembro quita el último elemento de la secuencia controlada, que debe estar vacío. Se usa para acortar la pila en un elemento en la parte trasera.

### <a name="example"></a>Ejemplo

```cpp
// cliext_stack_pop.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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
a b c
a b
```

## <a name="push"></a> Stack:: Push (STL/CLR)

Agrega un nuevo elemento de la última.

### <a name="syntax"></a>Sintaxis

```cpp
void push(value_type val);
```

### <a name="remarks"></a>Comentarios

La función miembro inserta un elemento con el valor `val` al final de la secuencia controlada. Se usa para anexar otro elemento a la pila.

### <a name="example"></a>Ejemplo

```cpp
// cliext_stack_push.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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
a b c
```

## <a name="reference"></a> Stack::Reference (STL/CLR)

El tipo de una referencia a un elemento.

### <a name="syntax"></a>Sintaxis

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Comentarios

El tipo describe una referencia a un elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_stack_reference.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify top of stack and redisplay
    Mystack::reference ref = c1.top();
    ref = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b x
```

## <a name="size"></a> Stack:: Size (STL/CLR)

Cuenta el número de elementos.

### <a name="syntax"></a>Sintaxis

```cpp
size_type size();
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve la longitud de la secuencia controlada. Se usa para determinar el número de elementos actualmente en la secuencia controlada. Si lo único que interesa es si la secuencia tiene un tamaño distinto de cero, vea [Stack:: Empty (STL/CLR)](../dotnet/stack-empty-stl-clr.md)`()`.

### <a name="example"></a>Ejemplo

```cpp
// cliext_stack_size.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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
a b c
size() = 3 starting with 3
size() = 2 after popping
size() = 4 after adding 2
```

## <a name="size_type"></a> Stack:: size_type (STL/CLR)

El tipo de una distancia con signo entre dos elementos.

### <a name="syntax"></a>Sintaxis

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Comentarios

El tipo describe un recuento de elemento no negativo.

### <a name="example"></a>Ejemplo

```cpp
// cliext_stack_size_type.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    Mystack::size_type diff = c1.size();
    c1.pop();
    c1.pop();
    diff -= c1.size();
    System::Console::WriteLine("size difference = {0}", diff);
    return (0);
    }
```

```Output
a b c
size difference = 2
```

## <a name="stack"></a> Stack:: Stack (STL/CLR)

Construye un objeto de adaptador de contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
stack();
stack(stack<Value, Container>% right);
stack(stack<Value, Container>^ right);
explicit stack(container_type% wrapped);
```

#### <a name="parameters"></a>Parámetros

*right*<br/>
Objeto que se va a copiar.

*Ajustado*<br/>
Contenedor ajustada para usarlo.

### <a name="remarks"></a>Comentarios

El constructor:

`stack();`

crea un contenedor vacío ajustado. Se usa para especificar una secuencia controlada inicial vacía.

El constructor:

`stack(stack<Value, Container>% right);`

crea un contenedor ajustado que es una copia de `right.get_container()`. Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de pila *derecho*.

El constructor:

`stack(stack<Value, Container>^ right);`

crea un contenedor ajustado que es una copia de `right->get_container()`. Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de pila `*right`.

El constructor:

`explicit stack(container_type% wrapped);`

usa el contenedor existente *ajustado* como el contenedor ajustado. Usa para construir una pila de un contenedor existente.

### <a name="example"></a>Ejemplo

```cpp
// cliext_stack_construct.cpp
// compile with: /clr
#include <cliext/stack>
#include <cliext/vector>

typedef cliext::stack<wchar_t> Mystack;
typedef cliext::vector<wchar_t> Myvector;
typedef cliext::stack<wchar_t, Myvector> Mystack_vec;
int main()
    {
// construct an empty container
    Mystack c1;
    System::Console::WriteLine("size() = {0}", c1.size());

// construct from an underlying container
    Myvector v2(5, L'x');
    Mystack_vec c2(v2);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container
    Mystack_vec c3(c2);
    for each (wchar_t elem in c3.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container through handle
    Mystack_vec c4(%c2);
    for each (wchar_t elem in c4.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
x x x x x
x x x x x
x x x x x
```

## <a name="to_array"></a> Stack::to_array (STL/CLR)

Copia la secuencia controlada a una nueva matriz.

### <a name="syntax"></a>Sintaxis

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve una matriz que contiene la secuencia controlada. Se usa para obtener una copia de la secuencia controlada en forma de matriz.

### <a name="example"></a>Ejemplo

```cpp
// cliext_stack_to_array.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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
a b c d
a b c
```

## <a name="top"></a> Stack:: Top (STL/CLR)

Obtiene acceso al último elemento.

### <a name="syntax"></a>Sintaxis

```cpp
reference top();
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve una referencia al último elemento de la secuencia controlada, que debe estar vacío. Usa para acceder el último elemento, cuando se sabe que existe.

### <a name="example"></a>Ejemplo

```cpp
// cliext_stack_top.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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

```Output
a b c
top() = c
a b x
```

## <a name="top_item"></a> Stack::top_item (STL/CLR)

Obtiene acceso al último elemento.

### <a name="syntax"></a>Sintaxis

```cpp
property value_type top_item;
```

### <a name="remarks"></a>Comentarios

La propiedad tiene acceso el último elemento de la secuencia controlada, que debe estar vacío. Usa para leer o escribir el último elemento, cuando se sabe que existe.

### <a name="example"></a>Ejemplo

```cpp
// cliext_stack_top_item.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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
a b c
top_item = c
a b x
```

## <a name="value_type"></a> Stack:: value_type (STL/CLR)

El tipo de un elemento.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla *valor*.

### <a name="example"></a>Ejemplo

```cpp
// cliext_stack_value_type.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display reversed contents " a b c" using value_type
    for (; !c1.empty(); c1.pop())
        {   // store element in value_type object
        Mystack::value_type val = c1.top();

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="op_neq"></a> operador! = (pila) (STL/CLR)

Pila de comparación de desigualdad.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value,
    typename Container>
    bool operator!=(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Contenedor izquierdo que se va a comparar.

*right*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Comentarios

Devuelve la función de operador `!(left == right)`. Usa para probar si *izquierdo* no está ordenado el mismo que *derecho* cuando las dos pilas son comparado elemento por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_stack_operator_ne.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
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

## <a name="op_lt"></a> operador&lt; (pila) (STL/CLR)

Pila menor de comparación.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value,
    typename Container>
    bool operator<(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Contenedor izquierdo que se va a comparar.

*right*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Comentarios

El operador función devuelve true si, para la posición más baja `i` que `!(right[i] < left[i])` es también true que `left[i] < right[i]`. De lo contrario, devuelve `left->` [Stack:: Size (STL/CLR)](../dotnet/stack-size-stl-clr.md) `() <` `right->size()` usarla para probar si *izquierdo* está ordenado antes *derecho* Cuando las dos pilas son comparado elemento por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_stack_operator_lt.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
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

## <a name="op_lteq"></a> operador&lt;= (pila) (STL/CLR)

Menor o igual la pila comparación.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value,
    typename Container>
    bool operator<=(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Contenedor izquierdo que se va a comparar.

*right*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Comentarios

Devuelve la función de operador `!(right < left)`. Usa para probar si *izquierdo* no está ordenado después *derecho* cuando las dos pilas son comparado elemento por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_stack_operator_le.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
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

## <a name="op_eq"></a> operador == (pila) (STL/CLR)

Comparación de igualdad de la pila.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value,
    typename Container>
    bool operator==(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Contenedor izquierdo que se va a comparar.

*right*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Comentarios

Devuelve true solo si las secuencias se controlan mediante la función de operador *izquierdo* y *derecho* tienen la misma longitud y, para cada posición `i`, `left[i] ==` `right[i]`. Se usa para probar si *izquierdo* se ordenan igual *derecho* cuando las dos pilas son comparado elemento por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_stack_operator_eq.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
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

## <a name="op_gt"></a> operador&gt; (pila) (STL/CLR)

Comparación mayor que la pila.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value,
    typename Container>
    bool operator>(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Contenedor izquierdo que se va a comparar.

*right*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Comentarios

Devuelve la función de operador `right` `<` `left`. Usa para probar si *izquierdo* se ordena después *derecho* cuando las dos pilas son comparado elemento por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_stack_operator_gt.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
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

## <a name="op_gteq"></a> operador&gt;= (pila) (STL/CLR)

Comparación igual o superior de la pila.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value,
    typename Container>
    bool operator>=(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Contenedor izquierdo que se va a comparar.

*right*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Comentarios

Devuelve la función de operador `!(left < right)`. Usa para probar si *izquierdo* no está ordenado antes *derecho* cuando las dos pilas son comparado elemento por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_stack_operator_ge.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
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