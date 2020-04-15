---
title: utility (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/utility>
- cliext::pair
- cliext::pair::pair
- cliext::pair::first
- cliext::pair::first_type
- cliext::pair::second
- cliext::pair::second_type
- cliext::pair::swap
- cliext::make_pair
- cliext::pair::operator=
- cliext::pair::operator==
- cliext::pair::operator>=
- cliext::pair::operator>
- cliext::pair::operator!=
- cliext::pair::operator<=
- cliext::pair::operator<
helpviewer_keywords:
- <utility> header [STL/CLR]
- utility header [STL/CLR]
- <cliext/utility> header [STL/CLR]
- first member [STL/CLR]
- first_type member [STL/CLR]
- second member [STL/CLR]
- second_type member [STL/CLR]
- swap member [STL/CLR]
- make_pair function [STL/CLR]
- pair class [STL/CLR]
- pair member [STL/CLR]
- operator== member [STL/CLR]
- operator= member [STL/CLR]
- operator>= member [STL/CLR]
- operator> member [STL/CLR]
- operator!= member [STL/CLR]
- operator<= member [STL/CLR]
- operator< member [STL/CLR]
ms.assetid: fb48cb75-d5ef-47ce-b526-bf60dc86c552
ms.openlocfilehash: 6d025230abcff42e367a231e616a13f0f8c684f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320293"
---
# <a name="utility-stlclr"></a>utility (STL/CLR)

Incluya el encabezado `<cliext/utility>` STL/CLR para `pair` definir la clase de plantilla y varias funciones de plantilla auxiliares.

## <a name="syntax"></a>Sintaxis

```cpp
#include <utility>
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<cliext/utility>

**Espacio de nombres:** cliext

## <a name="declarations"></a>Declaraciones

|Clase|Descripción|
|-----------|-----------------|
|[pair (STL/CLR)](#pair)|Envuelva un par de elementos.|

|Operator|Descripción|
|--------------|-----------------|
|[operador (par) (STL/CLR)](#op_eq)|Par igual comparación.|
|[operador! (par) (STL/CLR)](#op_neq)|Par no igual comparación.|
|[operador< (par) (STL/CLR)](#op_lt)|Emparejar menos que la comparación.|
|[operador\<(par) (STL/CLR)](#op_lteq)|Empareje la comparación menor o igual.|
|[operador> (par) (STL/CLR)](#op_gt)|Par mayor que la comparación.|
|[operator>= (pair) (STL/CLR)](#op_gteq)|Par mayor o igual comparación.|

|Función|Descripción|
|--------------|-----------------|
|[make_pair (STL/CLR)](#make_pair)|Haga un par a partir de un par de valores.|

## <a name="members"></a>Miembros

## <a name="pair-stlclr"></a><a name="pair"></a>par (STL/CLR)

La clase de plantilla describe un objeto que ajusta un par de valores.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value1,
    typename Value2>
    ref class pair;
```

#### <a name="parameters"></a>Parámetros

*Valor1*<br/>
El tipo de primer valor ajustado.

*Valor2*<br/>
El tipo de segundo valor ajustado.

## <a name="members"></a>Miembros

|Definición de tipo|Descripción|
|---------------------|-----------------|
|[pair::first_type (STL/CLR)](#first_type)|El tipo del primer valor ajustado.|
|[pair::second_type (STL/CLR)](#second_type)|El tipo del segundo valor ajustado.|

|Objeto miembro|Descripción|
|-------------------|-----------------|
|[pair::first (STL/CLR)](#first)|El primer valor almacenado.|
|[pair::second (STL/CLR)](#second)|El segundo valor almacenado.|

|Función miembro|Descripción|
|---------------------|-----------------|
|[pair::pair (STL/CLR)](#pair_pair)|Construye un objeto de par.|
|[pair::swap (STL/CLR)](#swap)|Intercambia el contenido de dos pares.|

|Operator|Descripción|
|--------------|-----------------|
|[pair::operator= (STL/CLR)](#op_as)|Reemplaza el par de valores almacenados.|

## <a name="remarks"></a>Observaciones

El objeto almacena un par de valores. Utilice esta clase de plantilla para combinar dos valores en un solo objeto. Además, `cliext::pair` el objeto (descrito aquí) solo almacena tipos administrados; para almacenar un par de `std::pair`tipos `<utility>`no administrados use , declarado en .

## <a name="pairfirst-stlclr"></a><a name="first"></a>par::first (STL/CLR)

El primer valor ajustado.

### <a name="syntax"></a>Sintaxis

```cpp
Value1 first;
```

### <a name="remarks"></a>Observaciones

El objeto almacena el primer valor ajustado.

### <a name="example"></a>Ejemplo

```cpp
// cliext_pair_first.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairfirst_type-stlclr"></a><a name="first_type"></a>par::first_type (STL/CLR)

El tipo del primer valor ajustado.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Value1 first_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla *Value1*.

### <a name="example"></a>Ejemplo

```cpp
// cliext_pair_first_type.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairoperator-stlclr"></a><a name="op_as"></a>par::operador (STL/CLR)

Reemplaza el par de valores almacenados.

### <a name="syntax"></a>Sintaxis

```cpp
pair<Value1, Value2>% operator=(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parámetros

*Correcto*<br/>
Emparejar para copiar.

### <a name="remarks"></a>Observaciones

El operador miembro copia *right* to `*this`the object y, a continuación, devuelve . Se utiliza para reemplazar el par de valores almacenados con una copia del par de valores almacenados en *la derecha.*

### <a name="example"></a>Ejemplo

```cpp
// cliext_pair_operator_as.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

// assign to a new pair
    cliext::pair<wchar_t, int> c2;
    c2 = c1;
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);
    return (0);
    }
```

```Output
[x, 3]
[x, 3]
```

## <a name="pairpair-stlclr"></a><a name="pair_pair"></a>par::paire (STL/CLR)

Construye un objeto de par.

### <a name="syntax"></a>Sintaxis

```cpp
pair();
pair(pair<Coll>% right);
pair(pair<Coll>^ right);
pair(Value1 val1, Value2 val2);
```

#### <a name="parameters"></a>Parámetros

*Correcto*<br/>
Emparejar para almacenar.

*val1*<br/>
Primer valor a almacenar.

*val2*<br/>
Segundo valor a almacenar.

### <a name="remarks"></a>Observaciones

El constructor:

`pair();`

inicializa el par almacenado con valores construidos predeterminados.

El constructor:

`pair(pair<Value1, Value2>% right);`

inicializa el par `right.`almacenado con [pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md) y `right.` [pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md).

`pair(pair<Value1, Value2>^ right);`

inicializa el par `right->`almacenado con [pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md) y `right>` [pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md).

El constructor:

`pair(Value1 val1, Value2 val2);`

inicializa el par almacenado con *val1* y *val2.*

### <a name="example"></a>Ejemplo

```cpp
// cliext_pair_construct.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
// construct an empty container
    cliext::pair<wchar_t, int> c1;
    System::Console::WriteLine("[{0}, {1}]",
        c1.first == L'\0' ? "\\0" : "??", c1.second);

// construct with a pair of values
    cliext::pair<wchar_t, int> c2(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

// construct by copying another pair
    cliext::pair<wchar_t, int> c3(c2);
    System::Console::WriteLine("[{0}, {1}]", c3.first, c3.second);

// construct by copying a pair handle
    cliext::pair<wchar_t, int> c4(%c3);
    System::Console::WriteLine("[{0}, {1}]", c4.first, c4.second);

    return (0);
    }
```

```Output
[\0, 0]
[x, 3]
[x, 3]
[x, 3]
```

## <a name="pairsecond-stlclr"></a><a name="second"></a>par::segundo (STL/CLR)

El segundo valor ajustado.

### <a name="syntax"></a>Sintaxis

```cpp
Value2 second;
```

### <a name="remarks"></a>Observaciones

El objeto almacena el segundo valor ajustado.

### <a name="example"></a>Ejemplo

```cpp
// cliext_pair_second.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairsecond_type-stlclr"></a><a name="second_type"></a>par::second_type (STL/CLR)

El tipo del segundo valor ajustado.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Value2 second_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla *Value2*.

### <a name="example"></a>Ejemplo

```cpp
// cliext_pair_second_type.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairswap-stlclr"></a><a name="swap"></a>pair::swap (STL/CLR)

Intercambia el contenido de dos pares.

### <a name="syntax"></a>Sintaxis

```cpp
void swap(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parámetros

*Correcto*<br/>
Emparejar para intercambiar contenido con.

### <a name="remarks"></a>Observaciones

La función miembro intercambia el `*this` par almacenado de valores entre y *right*.

### <a name="example"></a>Ejemplo

```cpp
// cliext_pair_swap.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
    {
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct another container with repetition of values
    cliext::deque<wchar_t> d2(5, L'x');
    Mycoll c2(%d2);
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

## <a name="make_pair-stlclr"></a><a name="make_pair"></a>make_pair (STL/CLR)

Haga `pair` un a partir de un par de valores.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value1,
    typename Value2>
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);
```

#### <a name="parameters"></a>Parámetros

*Valor1*<br/>
El tipo del primer valor ajustado.

*Valor2*<br/>
El tipo del segundo valor ajustado.

*Primero*<br/>
Primer valor que se va a ajustar.

*Segundo*<br/>
Segundo valor para ajustar.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve `pair<Value1, Value2>(first, second)`. Se utiliza para `pair<Value1, Value2>` construir un objeto a partir de un par de valores.

### <a name="example"></a>Ejemplo

```cpp
// cliext_make_pair.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    c1 = cliext::make_pair(L'y', 4);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    return (0);
    }
```

```Output
[x, 3]
[y, 4]
```

## <a name="operator-pair-stlclr"></a><a name="op_neq"></a>operador! (par) (STL/CLR)

Par no igual comparación.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value1,
    typename Value2>
    bool operator!=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parámetros

*Izquierda*<br/>
Par izquierdo para comparar.

*Correcto*<br/>
Par correcto para comparar.

### <a name="remarks"></a>Observaciones

La función `!(left == right)`operator devuelve . Se utiliza para probar si *izquierda* no se ordena igual que *la derecha* cuando los dos pares se comparan elemento por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_pair_operator_ne.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] != [x 3] is {0}",
        c1 != c1);
    System::Console::WriteLine("[x 3] != [x 4] is {0}",
        c1 != c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] != [x 3] is False
[x 3] != [x 4] is True
```

## <a name="operatorlt-pair-stlclr"></a><a name="op_lt"></a>operador&lt; (par) (STL/CLR)

Emparejar menos que la comparación.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value1,
    typename Value2>
    bool operator<(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parámetros

*Izquierda*<br/>
Par izquierdo para comparar.

*Correcto*<br/>
Par correcto para comparar.

### <a name="remarks"></a>Observaciones

La función `left.first <` `right.first || !(right.first <` `left.first &&` `left.second <` `right.second`operator devuelve . Se utiliza para probar si *a la izquierda* se ordena el antes a la *derecha* cuando los dos pares se comparan elemento por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_pair_operator_lt.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] < [x 3] is {0}",
        c1 < c1);
    System::Console::WriteLine("[x 3] < [x 4] is {0}",
        c1 < c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] < [x 3] is False
[x 3] < [x 4] is True
```

## <a name="operatorlt-pair-stlclr"></a><a name="op_lteq"></a>operador&lt;(par) (STL/CLR)

Empareje la comparación menor o igual.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value1,
    typename Value2>
    bool operator<=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parámetros

*Izquierda*<br/>
Par izquierdo para comparar.

*Correcto*<br/>
Par correcto para comparar.

### <a name="remarks"></a>Observaciones

La función `!(right < left)`operator devuelve . Se utiliza para probar si *izquierda* no se ordena después de *la derecha* cuando los dos pares se comparan elemento por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_pair_operator_le.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] <= [x 3] is {0}",
        c1 <= c1);
    System::Console::WriteLine("[x 4] <= [x 3] is {0}",
        c2 <= c1);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] <= [x 3] is True
[x 4] <= [x 3] is False
```

## <a name="operator-pair-stlclr"></a><a name="op_eq"></a>operador (par) (STL/CLR)

Par igual comparación.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value1,
    typename Value2>
    bool operator==(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parámetros

*Izquierda*<br/>
Par izquierdo para comparar.

*Correcto*<br/>
Par correcto para comparar.

### <a name="remarks"></a>Observaciones

La función `left.first ==` `right.first &&` `left.second ==` `right.second`operator devuelve . Se utiliza para probar si *a la izquierda* se ordena igual que a la *derecha* cuando los dos pares se comparan elemento por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_pair_operator_eq.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] == [x 3] is {0}",
        c1 == c1);
    System::Console::WriteLine("[x 3] == [x 4] is {0}",
        c1 == c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] == [x 3] is True
[x 3] == [x 4] is False
```

## <a name="operatorgt-pair-stlclr"></a><a name="op_gt"></a>operador&gt; (par) (STL/CLR)

Par mayor que la comparación.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value1,
    typename Value2>
    bool operator>(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parámetros

*Izquierda*<br/>
Par izquierdo para comparar.

*Correcto*<br/>
Par correcto para comparar.

### <a name="remarks"></a>Observaciones

La función `right` `<` `left`operator devuelve . Se usa para probar si *la izquierda* se ordena después de *la derecha* cuando los dos pares se comparan elemento por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_pair_operator_gt.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] > [x 3] is {0}",
        c1 > c1);
    System::Console::WriteLine("[x 4] > [x 3] is {0}",
        c2 > c1);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] > [x 3] is False
[x 4] > [x 3] is True
```

## <a name="operatorgt-pair-stlclr"></a><a name="op_gteq"></a>operador&gt;(par) (STL/CLR)

Par mayor o igual comparación.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value1,
    typename Value2>
    bool operator>=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parámetros

*Izquierda*<br/>
Par izquierdo para comparar.

*Correcto*<br/>
Par correcto para comparar.

### <a name="remarks"></a>Observaciones

La función `!(left < right)`operator devuelve . Se utiliza para probar si *izquierda* no se ordena antes de *la derecha* cuando los dos pares se comparan elemento por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_pair_operator_ge.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] >= [x 3] is {0}",
        c1 >= c1);
    System::Console::WriteLine("[x 3] >= [x 4] is {0}",
        c1 >= c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] >= [x 3] is True
[x 3] >= [x 4] is False
```
