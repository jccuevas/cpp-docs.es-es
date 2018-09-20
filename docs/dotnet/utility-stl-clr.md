---
title: la utilidad (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 307d3c2f95d006ae36ff39cf3c16ff3fd65a4c34
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374241"
---
# <a name="utility-stlclr"></a>utility (STL/CLR)

Incluya el encabezado STL/CLR `<cliext/utility>` para definir la clase de plantilla `pair` y varias funciones auxiliares de plantilla.

## <a name="syntax"></a>Sintaxis

```cpp
#include <utility>
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<cliext/utilidad >

**Namespace:** cliext

## <a name="declarations"></a>Declaraciones

|Clase|Descripción|
|-----------|-----------------|
|[pair (STL/CLR)](#pair)|Encapsular un par de elementos.|

|Operador|Descripción|
|--------------|-----------------|
|[operator== (pair) (STL/CLR)](#op_eq)|Comparación de igualdad del par.|
|[operator!= (pair) (STL/CLR)](#op_neq)|Par de comparación de desigualdad.|
|[operator< (pair) (STL/CLR)](#op_lt)|Par de comparación menor.|
|[operador\<= (par) (STL/CLR)](#op_lteq)|Menor o igual emparejar comparación.|
|[operator> (pair) (STL/CLR)](#op_gt)|Comparación mayor que el par.|
|[operator>= (pair) (STL/CLR)](#op_gteq)|Comparación igual o mayor del par.|

|Función|Descripción|
|--------------|-----------------|
|[make_pair (STL/CLR)](#make_pair)|Realizar un par de un par de valores.|

## <a name="members"></a>Miembros

##<a name="pair"></a> par (STL/CLR)
La clase de plantilla describe un objeto que encapsula un par de valores.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value1,
    typename Value2>
    ref class pair;
```

#### <a name="parameters"></a>Parámetros

*Valor1*<br/>
El tipo de valor incluido en primer lugar.

*Value2*<br/>
El tipo del segundo valor ajustado.

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

|Operador|Descripción|
|--------------|-----------------|
|[pair::operator= (STL/CLR)](#op_as)|Reemplaza el par de valores almacenado.|

## <a name="remarks"></a>Comentarios

El objeto almacena un par de valores. Utilice esta clase de plantilla para combinar dos valores en un único objeto. Además, el objeto `cliext::pair` (descritas aquí) almacena solo los tipos administrados; para almacenar un par de no administrado usan tipos `std::pair`, declarado en `<utility>`.

## <a name="first"></a> Pair::First (STL/CLR)

El primer valor ajustado.

### <a name="syntax"></a>Sintaxis

```cpp
Value1 first;
```

### <a name="remarks"></a>Comentarios

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

## <a name="first_type"></a> Pair::first_type (STL/CLR)

El tipo del primer valor ajustado.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Value1 first_type;
```

### <a name="remarks"></a>Comentarios

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

## <a name="op_as"></a> Pair::operator = (STL/CLR)

Reemplaza el par de valores almacenado.

### <a name="syntax"></a>Sintaxis

```cpp
pair<Value1, Value2>% operator=(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parámetros

*right*<br/>
Par para copiar.

### <a name="remarks"></a>Comentarios

Las copias de operador miembro *derecho* al objeto, a continuación, devuelve `*this`. Se usa para reemplazar el par de valores almacenado por una copia del par de valores almacenado *derecho*.

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

## <a name="pair_pair"></a> Pair::Pair (STL/CLR)

Construye un objeto de par.

### <a name="syntax"></a>Sintaxis

```cpp
pair();
pair(pair<Coll>% right);
pair(pair<Coll>^ right);
pair(Value1 val1, Value2 val2);
```

#### <a name="parameters"></a>Parámetros

*right*<br/>
Par para almacenar.

*val1*<br/>
Primer valor que se almacenará.

*Val2*<br/>
Segundo valor que se almacenará.

### <a name="remarks"></a>Comentarios

El constructor:

`pair();`

Inicializa el par almacenado con valores construido de forma predeterminada.

El constructor:

`pair(pair<Value1, Value2>% right);`

Inicializa el par almacenado con `right.` [pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md) y `right.` [pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md).

`pair(pair<Value1, Value2>^ right);`

Inicializa el par almacenado con `right->` [pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md) y `right>` [pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md).

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

## <a name="second"></a> Pair::Second (STL/CLR)

El segundo valor incluido.

### <a name="syntax"></a>Sintaxis

```cpp
Value2 second;
```

### <a name="remarks"></a>Comentarios

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

## <a name="second_type"></a> Pair::second_type (STL/CLR)

El tipo del segundo valor ajustado.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Value2 second_type;
```

### <a name="remarks"></a>Comentarios

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

## <a name="swap"></a> Pair::swap (STL/CLR)

Intercambia el contenido de dos pares.

### <a name="syntax"></a>Sintaxis

```cpp
void swap(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parámetros

*right*<br/>
Par para intercambiar el contenido.

### <a name="remarks"></a>Comentarios

La función miembro intercambia el par de valores entre almacenado `*this` y *derecho*.

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

## <a name="make_pair"></a> make_pair (STL/CLR)

Realizar un `pair` en un par de valores.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value1,
    typename Value2>
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);
```

#### <a name="parameters"></a>Parámetros

*Valor1*<br/>
El tipo del primer valor ajustado.

*Value2*<br/>
El tipo del segundo valor ajustado.

*first*<br/>
Primer valor de ajuste de línea.

*segundo*<br/>
Segundo valor para ajustar.

### <a name="remarks"></a>Comentarios

La función de plantilla devuelve `pair<Value1, Value2>(first, second)`. Utilícelo para construir un `pair<Value1, Value2>` objeto a partir de un par de valores.

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

## <a name="op_neq"></a> operador! = (par) (STL/CLR)

Par de comparación de desigualdad.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value1,
    typename Value2>
    bool operator!=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Par izquierdo para comparar.

*right*<br/>
Par derecho para comparar.

### <a name="remarks"></a>Comentarios

Devuelve la función de operador `!(left == right)`. Usa para probar si *izquierdo* no está ordenado el mismo que *derecho* cuando los dos pares no son comparado elemento por elemento.

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

## <a name="op_lt"></a> operador&lt; (par) (STL/CLR)

Par de comparación menor.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value1,
    typename Value2>
    bool operator<(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Par izquierdo para comparar.

*right*<br/>
Par derecho para comparar.

### <a name="remarks"></a>Comentarios

Devuelve la función de operador `left.first <` `right.first || !(right.first <` `left.first &&` `left.second <` `right.second`. Usarlo para probar si *izquierdo* se ordena la antes *derecho* cuando los dos pares no son comparado elemento por elemento.

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

## <a name="op_lteq"></a> operador&lt;= (par) (STL/CLR)

Menor o igual emparejar comparación.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value1,
    typename Value2>
    bool operator<=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Par izquierdo para comparar.

*right*<br/>
Par derecho para comparar.

### <a name="remarks"></a>Comentarios

Devuelve la función de operador `!(right < left)`. Se usa para probar si *izquierdo* no está ordenado después *derecho* cuando los dos pares no son comparado elemento por elemento.

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

## <a name="op_eq"></a> operador == (par) (STL/CLR)

Comparación de igualdad del par.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value1,
    typename Value2>
    bool operator==(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Par izquierdo para comparar.

*right*<br/>
Par derecho para comparar.

### <a name="remarks"></a>Comentarios

Devuelve la función de operador `left.first ==` `right.first &&` `left.second ==` `right.second`. Se usa para probar si *izquierdo* se ordenan igual *derecho* cuando los dos pares no son comparado elemento por elemento.

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

## <a name="op_gt"></a> operador&gt; (par) (STL/CLR)

Comparación mayor que el par.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value1,
    typename Value2>
    bool operator>(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Par izquierdo para comparar.

*right*<br/>
Par derecho para comparar.

### <a name="remarks"></a>Comentarios

Devuelve la función de operador `right` `<` `left`. Se usa para probar si *izquierdo* se ordena después *derecho* cuando los dos pares no son comparado elemento por elemento.

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

## <a name="op_gteq"></a> operador&gt;= (par) (STL/CLR)

Comparación igual o mayor del par.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Value1,
    typename Value2>
    bool operator>=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Par izquierdo para comparar.

*right*<br/>
Par derecho para comparar.

### <a name="remarks"></a>Comentarios

Devuelve la función de operador `!(left < right)`. Usa para probar si *izquierdo* no está ordenado antes *derecho* cuando los dos pares no son comparado elemento por elemento.

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