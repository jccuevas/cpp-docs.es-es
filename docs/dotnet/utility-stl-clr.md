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
ms.openlocfilehash: a841c41c8f640dcde2a3d98841f66f6c6dc04602
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208291"
---
# <a name="utility-stlclr"></a>utility (STL/CLR)

Incluya el encabezado de STL/CLR `<cliext/utility>` para definir la clase de plantilla `pair` y varias funciones de plantilla auxiliares.

## <a name="syntax"></a>Sintaxis

```cpp
#include <utility>
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<cliext (/Utility >

**Espacio de nombres:** cliext (

## <a name="declarations"></a>Declaraciones

|Clase|Descripción|
|-----------|-----------------|
|[pair (STL/CLR)](#pair)|Incluye un par de elementos.|

|Operator|Descripción|
|--------------|-----------------|
|[operator== (pair) (STL/CLR)](#op_eq)|Comparación de pares de igualdad.|
|[operator!= (pair) (STL/CLR)](#op_neq)|Comparación de emparejar no igual.|
|[operator< (pair) (STL/CLR)](#op_lt)|Comparación de un par menor que.|
|[Operator\<= (Pair) (STL/CLR)](#op_lteq)|Pareja de comparación menor o igual que.|
|[operator> (pair) (STL/CLR)](#op_gt)|Comparación mayor que.|
|[operator>= (pair) (STL/CLR)](#op_gteq)|Comparación mayor o igual que.|

|Función|Descripción|
|--------------|-----------------|
|[make_pair (STL/CLR)](#make_pair)|Cree un par de un par de valores.|

## <a name="members"></a>Members

## <a name="pair-stlclr"></a><a name="pair"></a>pair (STL/CLR)
La clase de plantilla describe un objeto que contiene un par de valores.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value1,
    typename Value2>
    ref class pair;
```

#### <a name="parameters"></a>Parámetros

*Value1*<br/>
Tipo del primer valor ajustado.

*Valor2*<br/>
Tipo del segundo valor ajustado.

## <a name="members"></a>Members

|Definición de tipo|Descripción|
|---------------------|-----------------|
|[pair::first_type (STL/CLR)](#first_type)|Tipo del primer valor ajustado.|
|[pair::second_type (STL/CLR)](#second_type)|Tipo del segundo valor ajustado.|

|Objeto miembro|Descripción|
|-------------------|-----------------|
|[pair::first (STL/CLR)](#first)|Primer valor almacenado.|
|[pair::second (STL/CLR)](#second)|Segundo valor almacenado.|

|Función miembro|Descripción|
|---------------------|-----------------|
|[pair::pair (STL/CLR)](#pair_pair)|Construye un objeto Pair.|
|[pair::swap (STL/CLR)](#swap)|Intercambia el contenido de dos pares.|

|Operator|Descripción|
|--------------|-----------------|
|[pair::operator= (STL/CLR)](#op_as)|Reemplaza el par almacenado de valores.|

## <a name="remarks"></a>Observaciones

El objeto almacena un par de valores. Esta clase de plantilla se usa para combinar dos valores en un solo objeto. Además, el `cliext::pair` de objeto (descrito aquí) almacena solo tipos administrados; para almacenar un par de tipos no administrados, utilice `std::pair`, declarado en `<utility>`.

## <a name="pairfirst-stlclr"></a><a name="first"></a>pair:: First (STL/CLR)

Primer valor ajustado.

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

## <a name="pairfirst_type-stlclr"></a><a name="first_type"></a>pair:: first_type (STL/CLR)

Tipo del primer valor ajustado.

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

## <a name="pairoperator-stlclr"></a><a name="op_as"></a>pair:: Operator = (STL/CLR)

Reemplaza el par almacenado de valores.

### <a name="syntax"></a>Sintaxis

```cpp
pair<Value1, Value2>% operator=(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parámetros

*right*<br/>
Pareja para copiar.

### <a name="remarks"></a>Observaciones

El operador miembro copia *directamente* en el objeto y, a continuación, devuelve `*this`. Se usa para reemplazar el par almacenado de valores por una copia del par almacenado de valores a la *derecha*.

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

## <a name="pairpair-stlclr"></a><a name="pair_pair"></a>pareja::p Air (STL/CLR)

Construye un objeto Pair.

### <a name="syntax"></a>Sintaxis

```cpp
pair();
pair(pair<Coll>% right);
pair(pair<Coll>^ right);
pair(Value1 val1, Value2 val2);
```

#### <a name="parameters"></a>Parámetros

*right*<br/>
Pareja para almacenar.

*valor1*<br/>
Primer valor que se va a almacenar.

*val2*<br/>
Segundo valor que se va a almacenar.

### <a name="remarks"></a>Observaciones

El constructor:

`pair();`

Inicializa el par almacenado con los valores construidos predeterminados.

El constructor:

`pair(pair<Value1, Value2>% right);`

Inicializa el par almacenado con `right.`[par:: First (STL/CLR)](../dotnet/pair-first-stl-clr.md) y `right.`[par:: Second (STL/CLR)](../dotnet/pair-second-stl-clr.md).

`pair(pair<Value1, Value2>^ right);`

Inicializa el par almacenado con `right->`[par:: First (STL/CLR)](../dotnet/pair-first-stl-clr.md) y `right>`[par:: Second (STL/CLR)](../dotnet/pair-second-stl-clr.md).

El constructor:

`pair(Value1 val1, Value2 val2);`

Inicializa el par almacenado con *val1* y *val2*.

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

## <a name="pairsecond-stlclr"></a><a name="second"></a>pair:: Second (STL/CLR)

Segundo valor ajustado.

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

## <a name="pairsecond_type-stlclr"></a><a name="second_type"></a>pair:: second_type (STL/CLR)

Tipo del segundo valor ajustado.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Value2 second_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla *value2*.

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

## <a name="pairswap-stlclr"></a><a name="swap"></a>pair:: swap (STL/CLR)

Intercambia el contenido de dos pares.

### <a name="syntax"></a>Sintaxis

```cpp
void swap(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parámetros

*right*<br/>
Par para intercambiar contenido con.

### <a name="remarks"></a>Observaciones

La función miembro intercambia el par almacenado de valores entre `*this` y *right*.

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

Cree una `pair` a partir de un par de valores.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value1,
    typename Value2>
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);
```

#### <a name="parameters"></a>Parámetros

*Value1*<br/>
Tipo del primer valor ajustado.

*Valor2*<br/>
Tipo del segundo valor ajustado.

*first*<br/>
Primer valor que se va a ajustar.

*second*<br/>
Segundo valor que se va a ajustar.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve `pair<Value1, Value2>(first, second)`. Se utiliza para construir un objeto `pair<Value1, Value2>` a partir de un par de valores.

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

## <a name="operator-pair-stlclr"></a><a name="op_neq"></a>Operator! = (Pair) (STL/CLR)

Comparación de emparejar no igual.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value1,
    typename Value2>
    bool operator!=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Par izquierdo que se va a comparar.

*right*<br/>
Par derecho que se va a comparar.

### <a name="remarks"></a>Observaciones

La función de operador devuelve `!(left == right)`. Se usa para probar si la *izquierda* no está ordenada de la misma forma que la *derecha* cuando se comparan los dos pares elemento a elemento.

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

## <a name="operatorlt-pair-stlclr"></a><a name="op_lt"></a>Operator&lt; (Pair) (STL/CLR)

Comparación de un par menor que.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value1,
    typename Value2>
    bool operator<(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Par izquierdo que se va a comparar.

*right*<br/>
Par derecho que se va a comparar.

### <a name="remarks"></a>Observaciones

La función de operador devuelve `left.first <` `right.first || !(right.first <` `left.first &&` `left.second <` `right.second`. Se usa para probar si la *izquierda* se ordena antes de la *derecha* cuando se comparan los dos pares elemento a elemento.

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

## <a name="operatorlt-pair-stlclr"></a><a name="op_lteq"></a>Operator&lt;= (Pair) (STL/CLR)

Pareja de comparación menor o igual que.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value1,
    typename Value2>
    bool operator<=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Par izquierdo que se va a comparar.

*right*<br/>
Par derecho que se va a comparar.

### <a name="remarks"></a>Observaciones

La función de operador devuelve `!(right < left)`. Se usa para probar si la *izquierda* no se *ordena después de* la hora a la que se comparan los dos pares elemento a elemento.

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

## <a name="operator-pair-stlclr"></a><a name="op_eq"></a>Operator = = (Pair) (STL/CLR)

Comparación de pares de igualdad.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value1,
    typename Value2>
    bool operator==(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Par izquierdo que se va a comparar.

*right*<br/>
Par derecho que se va a comparar.

### <a name="remarks"></a>Observaciones

La función de operador devuelve `left.first ==` `right.first &&` `left.second ==` `right.second`. Se usa para probar si la *izquierda* se ordena igual que la *derecha* cuando se comparan los dos pares elemento a elemento.

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

## <a name="operatorgt-pair-stlclr"></a><a name="op_gt"></a>Operator&gt; (Pair) (STL/CLR)

Comparación mayor que.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value1,
    typename Value2>
    bool operator>(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Par izquierdo que se va a comparar.

*right*<br/>
Par derecho que se va a comparar.

### <a name="remarks"></a>Observaciones

La función de operador devuelve `right` `left`de `<`. Se usa para comprobar si la *izquierda* se ordena después de la *derecha* cuando se comparan los dos pares elemento a elemento.

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

## <a name="operatorgt-pair-stlclr"></a><a name="op_gteq"></a>Operator&gt;= (Pair) (STL/CLR)

Comparación mayor o igual que.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value1,
    typename Value2>
    bool operator>=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Par izquierdo que se va a comparar.

*right*<br/>
Par derecho que se va a comparar.

### <a name="remarks"></a>Observaciones

La función de operador devuelve `!(left < right)`. Se usa para probar si la *izquierda* no está ordenada antes de la *derecha* cuando se comparan los dos pares elemento a elemento.

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
