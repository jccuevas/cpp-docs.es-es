---
title: '&lt;functional&gt; (Funciones)'
ms.date: 02/21/2019
f1_keywords:
- functional/std::bind
- functional/std::bind1st
- functional/std::bind2nd
- functional/std::bit_and
- functional/std::bit_not
- functional/std::bit_or
- functional/std::bit_xor
- functional/std::cref
- type_traits/std::cref
- functional/std::mem_fn
- functional/std::mem_fun_ref
- functional/std::not1
- functional/std::not2
- functional/std::not_fn
- functional/std::ptr_fun
- functional/std::ref
- functional/std::swap
helpviewer_keywords:
- std::bind [C++]
- std::bind1st
- std::bind2nd
- std::bit_and [C++]
- std::bit_not [C++]
- std::bit_or [C++]
- std::bit_xor [C++]
- std::cref [C++]
ms.assetid: c34d0b45-50a7-447a-9368-2210d06339a4
ms.openlocfilehash: 546d8c61e875dd7c295e892359e39fa5a76867b4
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243789"
---
# <a name="ltfunctionalgt-functions"></a>&lt;functional&gt; (Funciones)

Estas funciones están en desuso en C ++ 11 y se quitan en C ++ 17:

||||
|-|-|-|
|[bind1st](#bind1st) |[bind2nd](#bind2nd)|[mem_fun](#mem_fun)|
|[mem_fun_ref](#mem_fun_ref)|[ptr_fun](#ptr_fun)||

Estas funciones están en desuso en C ++ 17:

|||
|-|-|
|[not1](#not1)|[not2](#not2)|

## <a name="bind"></a> Enlazar

Enlaza argumentos a un objeto al que se puede llamar.

```cpp
template <class FT, class T1, class T2, ..., class TN>
    unspecified bind(FT fn, T1 t1, T2 t2, ..., TN tN);

template <class RTy, class FT, class T1, class T2, ..., class TN>
    unspecified bind(FT fn, T1 t1, T2 t2, ..., TN tN);
```

### <a name="parameters"></a>Parámetros

*Fey*\
El tipo del objeto al que se va a llamar.

*TN*\
Tipo del enésimo argumento de llamada.

*fn*\
El objeto al que se va a llamar.

*tN*\
El enésimo argumento de llamada.

### <a name="remarks"></a>Comentarios

Los tipos de `FT, T1, T2, ..., TN` debe construir de copia, y `INVOKE(fn, t1, ..., tN)` debe ser una expresión válida para algunos valores `w1, w2, ..., wN`.

La primera función de plantilla devuelve un contenedor de llamadas de reenvío `g` con un tipo de resultado débil. El efecto de `g(u1, u2, ..., uM)` es `INVOKE(f, v1, v2, ..., vN, ` [invoke_result](../standard-library/invoke-result-class.md)`<FT cv (V1, V2, ..., VN)>::type)`, donde `cv` son los calificadores cv de `g` y los valores y tipos de los argumentos enlazados `v1, v2, ..., vN` vienen determinados como se indica a continuación. Úselo para enlazar los argumentos con un objeto al que se puede llamar para crear un objeto al que se puede llamar con una lista de argumentos adaptada.

La segunda función de plantilla devuelve un contenedor de llamadas de reenvío `g` con un tipo anidado `result_type` que es un sinónimo de `RTy`. El efecto de `g(u1, u2, ..., uM)` es `INVOKE(f, v1, v2, ..., vN, RTy)`, donde `cv` son los calificadores cv de `g` y los valores y tipos de los argumentos enlazados `v1, v2, ..., vN` están determinados como se indica a continuación. Úselo para enlazar los argumentos con un objeto al que se puede llamar para crear un objeto al que se puede llamar con una lista de argumentos adaptada y con un tipo de valor devuelto especificado.

Los valores de los argumentos enlazados `v1, v2, ..., vN` y sus tipos correspondientes `V1, V2, ..., VN` dependen del tipo del argumento correspondiente `ti` de tipo `Ti` en la llamada a `bind` y los calificadores cv `cv` del contenedor de llamadas `g` de la siguiente forma:

si `ti` es de tipo `reference_wrapper<T>`, el argumento `vi` es `ti.get()` y su tipo `Vi` es `T&`;

Si el valor de `std::is_bind_expression<Ti>::value` es **true** el argumento `vi` es `ti(u1, u2, ..., uM)` y su tipo `Vi` es `result_of<Ti` `cv` `(U1&, U2&, ..., UN&>::type`;

Si el valor `j` de `std::is_placeholder<Ti>::value` no es cero en el argumento `vi` es `uj` y su tipo `Vi` es `Uj&`;

de lo contrario, el argumento `vi` es `ti` y su tipo `Vi` es `Ti` `cv` `&`.

Por ejemplo, dada una función `f(int, int)`, la expresión `bind(f, _1, 0)` devuelve un contenedor de llamadas de reenvío `cw` de modo que `cw(x)` llama a `f(x, 0)`. La expresión `bind(f, 0, _1)` devuelve un contenedor de llamadas de reenvío `cw` de modo que `cw(x)` llama a `f(0, x)`.

El número de argumentos en una llamada a `bind` y el argumento `fn` debe ser igual al número de argumentos que se puede pasar al objeto que se puede llamar `fn`. Por ejemplo, `bind(cos, 1.0)` es correcta y ambos `bind(cos)` y `bind(cos, _1, 0.0)` son incorrectas.

El número de argumentos de la llamada de función al contenedor de llamadas devuelto por `bind` debe ser al menos tan grande como el valor numerado más alto de `is_placeholder<PH>::value` para todos los argumentos de marcador de posición en la llamada a `bind`. Por ejemplo, `bind(cos, _2)(0.0, 1.0)` es correcto (y devuelve `cos(1.0)`), y `bind(cos, _2)(0.0)` es incorrecto.

### <a name="example"></a>Ejemplo

```cpp
// std__functional__bind.cpp
// compile with: /EHsc
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std::placeholders;

void square(double x)
{
    std::cout << x << "^2 == " << x * x << std::endl;
}

void product(double x, double y)
{
    std::cout << x << "*" << y << " == " << x * y << std::endl;
}

int main()
{
    double arg[] = { 1, 2, 3 };

    std::for_each(&arg[0], arg + 3, square);
    std::cout << std::endl;

    std::for_each(&arg[0], arg + 3, std::bind(product, _1, 2));
    std::cout << std::endl;

    std::for_each(&arg[0], arg + 3, std::bind(square, _1));

    return (0);
}
```

```Output
1^2 == 1
2^2 == 4
3^2 == 9

1*2 == 2
2*2 == 4
3*2 == 6

1^2 == 1
2^2 == 4
3^2 == 9
```

## <a name="bind1st"></a> bind1st

Una función de plantilla auxiliar que crea un adaptador para convertir un objeto de función binaria en un objeto de función unaria. El primer argumento de la función binaria enlaza a un valor especificado. En desuso en C ++ 11, se ha quitado en C ++ 17.

```cpp
template <class Operation, class Type>
    binder1st <Operation> bind1st (const Operation& func, const Type& left);
```

### <a name="parameters"></a>Parámetros

*Func*\
El objeto de función binaria que se va a convertir en un objeto de función unaria.

*Izquierda*\
El valor al que se enlazará el primer argumento del objeto de función binaria.

### <a name="return-value"></a>Valor devuelto

El objeto de función unaria resultante de enlazar el primer argumento del objeto de función binaria con el valor *izquierdo*.

### <a name="remarks"></a>Comentarios

Los enlazadores de función son un tipo de adaptador de función. Ya que devuelven objetos de función, puede usarse en ciertos tipos de composición de funciones para construir expresiones más complicadas y eficaces.

Si *func* es un objeto de tipo `Operation` y `c` es una constante, a continuación, `bind1st( func, c )` es el mismo que el [binder1st](../standard-library/binder1st-class.md) constructor de clase `binder1st<Operation>(func, c)`y es más cómodo Utilice.

### <a name="example"></a>Ejemplo

```cpp
// functional_bind1st.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

// Creation of a user-defined function object
// that inherits from the unary_function base class
class greaterthan5: unary_function<int, bool>
{
public:
    result_type operator()(argument_type i)
    {
        return (result_type)(i > 5);
    }
};

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 5; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( " ;
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    // Count the number of integers > 10 in the vector
    vector<int>::iterator::difference_type result1a;
    result1a = count_if(v1.begin(), v1.end(), bind1st(less<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1a << "." << endl;

    // Compare: counting the number of integers > 5 in the vector
    // with a user defined function object
    vector<int>::iterator::difference_type result1b;
    result1b = count_if(v1.begin(), v1.end(), greaterthan5());
    cout << "The number of elements in v1 greater than 5 is: "
         << result1b << "." << endl;

    // Count the number of integers < 10 in the vector
    vector<int>::iterator::difference_type result2;
    result2 = count_if(v1.begin(), v1.end(), bind2nd(less<int>(), 10));
    cout << "The number of elements in v1 less than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 greater than 5 is: 4.
The number of elements in v1 less than 10 is: 2.
```

## <a name="bind2nd"></a> bind2nd

Una función de plantilla auxiliar que crea un adaptador para convertir un objeto de función binaria en un objeto de función unaria. Enlaza el segundo argumento de la función binaria a un valor especificado. En desuso en C ++ 11, se ha quitado en C ++ 17.

```cpp
template <class Operation, class Type>
    binder2nd <Operation> bind2nd(const Operation& func, const Type& right);
```

### <a name="parameters"></a>Parámetros

*Func*\
El objeto de función binaria que se va a convertir en un objeto de función unaria.

*Correcto*\
El valor al que se enlazará el segundo argumento del objeto de función binaria.

### <a name="return-value"></a>Valor devuelto

El resultado del objeto de función unario de enlazar el segundo argumento del objeto de función binaria a *derecho*.

### <a name="remarks"></a>Comentarios

Los enlazadores de función son un tipo de adaptador de función. Ya que devuelven objetos de función, puede usarse en ciertos tipos de composición de funciones para construir expresiones más complicadas y eficaces.

Si *func* es un objeto de tipo `Operation` y `c` es una constante, a continuación, `bind2nd(func, c)` es el mismo que el [binder2nd](../standard-library/binder2nd-class.md) constructor de clase `binder2nd<Operation>(func, c)`y más conveniente usar.

### <a name="example"></a>Ejemplo

```cpp
// functional_bind2nd.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

// Creation of a user-defined function object
// that inherits from the unary_function base class
class greaterthan15: unary_function<int, bool>
{
public:
    result_type operator()(argument_type i)
    {
        return (result_type)(i > 15);
    }
};

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 5; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    // Count the number of integers > 10 in the vector
    vector<int>::iterator::difference_type result1a;
    result1a = count_if(v1.begin(), v1.end(), bind2nd(greater<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1a << "." << endl;

    // Compare counting the number of integers > 15 in the vector
    // with a user-defined function object
    vector<int>::iterator::difference_type result1b;
    result1b = count_if(v1.begin(), v1.end(), greaterthan15());
    cout << "The number of elements in v1 greater than 15 is: "
         << result1b << "." << endl;

    // Count the number of integers < 10 in the vector
    vector<int>::iterator::difference_type result2;
    result2 = count_if(v1.begin(), v1.end(), bind1st(greater<int>(), 10));
    cout << "The number of elements in v1 less than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 greater than 15 is: 2.
The number of elements in v1 less than 10 is: 2.
```

## <a name="bit_and"></a> bit_and

Un objeto de función predefinido que realiza una operación AND bit a bit (binario `operator&`) sobre sus argumentos.

```cpp
template <class Type = void>
struct bit_and : public binary_function<Type, Type, Type> {
    Type operator()(
    const Type& Left,
    const Type& Right) const;
};

// specialized transparent functor for operator&
template <>
struct bit_and<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const  ->
        decltype(std::forward<T>(Left) & std::forward<U>(Right));
};
```

### <a name="parameters"></a>Parámetros

*Tipo*, *T*, *U*\
Cualquier tipo que admite un `operator&` que toma operandos de los tipos especificados o deducidos.

*Izquierda*\
Operando izquierdo de la operación AND bit a bit. La plantilla no especializada toma un argumento de referencia de valor l de tipo *tipo*. La plantilla especializada realiza el reenvío de valor l directo y los argumentos de referencia de valor r del tipo deducen *T*.

*Correcto*\
Operando derecho de la operación AND bit a bit. La plantilla no especializada toma un argumento de referencia de valor l de tipo *tipo*. La plantilla especializada realiza el reenvío de valor l directo y los argumentos de referencia de valor r del tipo deducen *U*.

### <a name="return-value"></a>Valor devuelto

Resultado de `Left & Right`. La plantilla especializada realiza el reenvío directo del resultado, que tiene el tipo devuelto por `operator&`.

### <a name="remarks"></a>Comentarios

El functor de `bit_and` está limitado a tipos enteros para los tipos de datos básicos, o a tipos definidos por el usuario que implementan el `operator&` binario.

## <a name="bit_not"></a> bit_not

Un objeto de función predefinido que realiza un operación (no) de complemento bit a bit (unario `operator~`) sobre su argumento. Agregado en C ++ 14.

```cpp
template <class Type = void>
struct bit_not : public unary_function<Type, Type>
{
    Type operator()(const Type& Right) const;
};

// specialized transparent functor for operator~
template <>
struct bit_not<void>
{
    template <class Type>
    auto operator()(Type&& Right) const -> decltype(~std::forward<Type>(Right));
};
```

### <a name="parameters"></a>Parámetros

*Tipo*\
Tipo que admite un `operator~` unario.

*Correcto*\
Operando de la operación de complemento bit a bit. La plantilla no especializada toma un argumento de referencia de valor l de tipo *tipo*. La plantilla especializada realiza el reenvío de un argumento de referencia lvalue o rvalue de tipo inferido directo *tipo*.

### <a name="return-value"></a>Valor devuelto

Resultado de `~ Right`. La plantilla especializada realiza el reenvío directo del resultado, que tiene el tipo devuelto por `operator~`.

### <a name="remarks"></a>Comentarios

El functor de `bit_not` está limitado a tipos enteros para los tipos de datos básicos, o a tipos definidos por el usuario que implementan el `operator~` binario.

## <a name="bit_or"></a> bit_or

Un objeto de función predefinido que realiza una operación OR bit a bit (`operator|`) sobre sus argumentos.

```cpp
template <class Type = void>
struct bit_or : public binary_function<Type, Type, Type> {
    Type operator()(
    const Type& Left,
    const Type& Right) const;
};

// specialized transparent functor for operator|
template <>
struct bit_or<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const
        -> decltype(std::forward<T>(Left) | std::forward<U>(Right));
};
```

### <a name="parameters"></a>Parámetros

*Tipo*, *T*, *U*\
Cualquier tipo que admite un `operator|` que toma operandos de los tipos especificados o deducidos.

*Izquierda*\
Operando izquierdo de la operación OR bit a bit. La plantilla no especializada toma un argumento de referencia de valor l de tipo *tipo*. La plantilla especializada realiza el reenvío de valor l directo y los argumentos de referencia de valor r del tipo deducen *T*.

*Correcto*\
Operando derecho de la operación OR bit a bit. La plantilla no especializada toma un argumento de referencia de valor l de tipo *tipo*. La plantilla especializada realiza el reenvío de valor l directo y los argumentos de referencia de valor r del tipo deducen *U*.

### <a name="return-value"></a>Valor devuelto

Resultado de `Left | Right`. La plantilla especializada realiza el reenvío directo del resultado, que tiene el tipo devuelto por `operator|`.

### <a name="remarks"></a>Comentarios

El functor de `bit_or` está limitado a tipos enteros para los tipos de datos básicos, o a tipos definidos por el usuario que implementan el `operator|`.

## <a name="bit_xor"></a> bit_xor

Un objeto de función predefinido que realiza una operación XOR bit a bit (binario `operator^`) sobre sus argumentos.

```cpp
template <class Type = void>
struct bit_xor : public binary_function<Type, Type, Type> {
    Type operator()(
    const Type& Left,
    const Type& Right) const;
};

// specialized transparent functor for operator^
template <>
struct bit_xor<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const
        -> decltype(std::forward<T>(Left) ^ std::forward<U>(Right));
};
```

### <a name="parameters"></a>Parámetros

*Tipo*, *T*, *U*\
Cualquier tipo que admite un `operator^` que toma operandos de los tipos especificados o deducidos.

*Izquierda*\
Operando izquierdo de la operación XOR bit a bit. La plantilla no especializada toma un argumento de referencia de valor l de tipo *tipo*. La plantilla especializada realiza el reenvío de valor l directo y los argumentos de referencia de valor r del tipo deducen *T*.

*Correcto*\
Operando derecho de la operación XOR bit a bit. La plantilla no especializada toma un argumento de referencia de valor l de tipo *tipo*. La plantilla especializada realiza el reenvío de valor l directo y los argumentos de referencia de valor r del tipo deducen *U*.

### <a name="return-value"></a>Valor devuelto

Resultado de `Left ^ Right`. La plantilla especializada realiza el reenvío directo del resultado, que tiene el tipo devuelto por `operator^`.

### <a name="remarks"></a>Comentarios

El functor de `bit_xor` está limitado a tipos enteros para los tipos de datos básicos, o a tipos definidos por el usuario que implementan el `operator^` binario.

## <a name="cref"></a> cref

Construye un `reference_wrapper` const a partir de un argumento.

```cpp
template <class Ty>
reference_wrapper<const Ty> cref(const Ty& arg);

template <class Ty>
reference_wrapper<const Ty> cref(const reference_wrapper<Ty>& arg);
```

### <a name="parameters"></a>Parámetros

*Ty*\
El tipo del argumento que se encapsulará.

*arg*\
El argumento que se encapsulará.

### <a name="remarks"></a>Comentarios

La primera función devuelve `reference_wrapper<const Ty>(arg.get())`. Úsela para encapsular una referencia const. La segunda función devuelve `reference_wrapper<const Ty>(arg)`. Úsela para volver a encapsular una referencia encapsulada como referencia const.

### <a name="example"></a>Ejemplo

```cpp
// std__functional__cref.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    int i = 1;

    std::cout << "i = " << i << std::endl;
    std::cout << "cref(i) = " << std::cref(i) << std::endl;
    std::cout << "cref(neg)(i) = "
        << std::cref(&neg)(i) << std::endl;

    return (0);
    }
```

```Output
i = 1
cref(i) = 1
cref(neg)(i) = -1
```

## <a name="invoke"></a> Invocar

Invoca cualquier objeto que se puede llamar con los argumentos especificados. Agregado en C ++ 17.

```cpp
template <class Callable, class... Args>
invoke_result_t<Callable, Args...>
    invoke(Callable&& fn, Args&&... args) noexcept(/* specification */);
```

### <a name="parameters"></a>Parámetros

*puede llamar*\
El tipo del objeto al que se va a llamar.

*args*\
Los tipos de argumentos de llamada.

*fn*\
El objeto al que se va a llamar.

*args*\
Argumentos de llamada.

*especificación*\
El **noexcept** especificación `std::is_nothrow_invocable_v<Callable, Args>)`.

### <a name="remarks"></a>Comentarios

Invoca el objeto que se puede llamar *fn* con los parámetros *args*. De hecho, `INVOKE(std::forward<Callable>(fn), std::forward<Args>(args)...)`, donde la pseudofunción `INVOKE(f, t1, t2, ..., tN)` debido a una de las siguientes acciones:

- `(t1.*f)(t2, ..., tN)` cuando `f` es un puntero a una función miembro de clase `T` y `t1` es un objeto de tipo `T`, una referencia a un objeto de tipo `T` o una referencia a un objeto de un tipo derivado de `T`. Es decir, cuando `std::is_base_of<T, std::decay_t<decltype(t1)>>::value` es true.

- `(t1.get().*f)(t2, ..., tN)` Cuando `f` es un puntero a función miembro de clase `T` y `std::decay_t<decltype(t1)>` es una especialización de `std::reference_wrapper`.

- `((*t1).*f)(t2, ..., tN)` Cuando `f` es un puntero a función miembro de clase `T` y `t1` no es uno de los tipos anteriores.

- `t1.*f` cuando N == 1 y `f` es un puntero a datos de miembro de una clase `T` y `t1` es un objeto de tipo `T`, una referencia a un objeto de tipo `T` o una referencia a un objeto de un tipo derivado de `T`.  Es decir, cuando `std::is_base_of<T, std::decay_t<decltype(t1)>>::value` es true.

- `t1.get().*f` Cuando N == 1 y `f` es un puntero a miembro de datos de una clase `T` y `std::decay_t<decltype(t1)>` es una especialización de `std::reference_wrapper`.

- `(*t1).*f` Cuando N == 1 y `f` es un puntero a miembro de datos de una clase `T` y `t1` no es uno de los tipos anteriores.

- `f(t1, t2, ..., tN)` en todos los demás casos.

Para obtener información sobre el tipo de resultado de un objeto que se puede llamar, vea [invoke_result](invoke-result-class.md). Para los predicados en tipos que se puede llamar, vea [is_invocable, is_invocable_r, is_nothrow_invocable, clases is_nothrow_invocable_r](is-invocable-classes.md).

### <a name="example"></a>Ejemplo

```cpp
// functional_invoke.cpp
// compile using: cl /EHsc /std:c++17 functional_invoke.cpp
#include <functional>
#include <iostream>

struct Demo
{
    int n_;

    Demo(int const n) : n_{n} {}

    void operator()( int const i, int const j ) const
    {
        std::cout << "Demo operator( " << i << ", "
            << j << " ) is " << i * j << "\n";
    }

    void difference( int const i ) const
    {
        std::cout << "Demo.difference( " << i << " ) is "
            << n_ - i << "\n";
    }
};

void divisible_by_3(int const i)
{
    std::cout << i << ( i % 3 == 0 ? " is" : " isn't" )
        << " divisible by 3.\n";
}

int main()
{
    Demo d{ 42 };
    Demo * pd{ &d };
    auto pmf = &Demo::difference;
    auto pmd = &Demo::n_;

    // Invoke a function object, like calling d( 3, -7 )
    std::invoke( d, 3, -7 );

    // Invoke a member function, like calling
    // d.difference( 29 ) or (d.*pmf)( 29 )
    std::invoke( &Demo::difference, d, 29 );
    std::invoke( pmf, pd, 13 );

    // Invoke a data member, like access to d.n_ or d.*pmd
    std::cout << "d.n_: " << std::invoke( &Demo::n_, d ) << "\n";
    std::cout << "pd->n_: " << std::invoke( pmd, pd ) << "\n";

    // Invoke a stand-alone (free) function
    std::invoke( divisible_by_3, 42 );

    // Invoke a lambda
    auto divisible_by_7 = []( int const i ) {
        std::cout << i << ( i % 7 == 0 ? " is" : " isn't" )
            << " divisible by 7.\n";
        };
    std::invoke( divisible_by_7, 42 );
}
```

```Output
Demo operator( 3, -7 ) is -21
Demo.difference( 29 ) is 13
Demo.difference( 13 ) is 29
d.n_: 42
pd->n_: 42
42 is divisible by 3.
42 is divisible by 7.
```

## <a name="mem_fn"></a> mem_fn

Genera un contenedor de llamadas simple.

```cpp
template <class RTy, class Ty>
unspecified mem_fn(RTy Ty::*pm);
```

### <a name="parameters"></a>Parámetros

*RTy*\
Tipo de valor devuelto de la función encapsulada.

*Ty*\
El tipo del puntero de función miembro.

### <a name="remarks"></a>Comentarios

La función de plantilla devuelve un contenedor de llamadas simple `cw`, con un tipo de resultado débil, tal que la expresión `cw(t, a2, ..., aN)` es el mismo que `INVOKE(pm, t, a2, ..., aN)`. No produce ninguna excepción.

El contenedor de llamadas devuelto procede de `std::unary_function<cv Ty*, RTy>` (y define el tipo anidado `result_type` como sinónimo de *RTy* y el tipo anidado `argument_type` como sinónimo de `cv Ty*`) solo si el tipo *Ty*  es un puntero a función miembro con el calificador cv `cv` que no toma ningún argumento.

El contenedor de llamadas devuelto procede de `std::binary_function<cv Ty*, T2, RTy>` (y define el tipo anidado `result_type` como sinónimo de *RTy*, el tipo anidado `first argument_type` como sinónimo de `cv Ty*`y el tipo anidado `second argument_type` como sinónimo de `T2`) solo si el tipo *Ty* es un puntero a función miembro con el calificador cv `cv` que toma un argumento, de tipo `T2`.

### <a name="example"></a>Ejemplo

```cpp
// std__functional__mem_fn.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

class Funs
    {
public:
    void square(double x)
        {
        std::cout << x << "^2 == " << x * x << std::endl;
        }

    void product(double x, double y)
        {
        std::cout << x << "*" << y << " == " << x * y << std::endl;
        }
    };

int main()
    {
    Funs funs;

    std::mem_fn(&Funs::square)(funs, 3.0);
    std::mem_fn(&Funs::product)(funs, 3.0, 2.0);

    return (0);
    }
```

```Output
3^2 == 9
3*2 == 6
```

## <a name="mem_fun"></a> mem_fun

Funciones de plantilla del asistente utilizadas para construir adaptadores de objeto de función para las funciones miembro cuando se inicializan con argumentos de puntero. En desuso en C ++ 11 para [mem_fn ()](#mem_fn) y [enlazar](#bind)y se quitan en C ++ 17.

```cpp
template <class Result, class Type>
mem_fun_t<Result, Type> mem_fun (Result(Type::* pMem)());

template <class Result, class Type, class Arg>
mem_fun1_t<Result, Type, Arg> mem_fun(Result (Type::* pMem)(Arg));

template <class Result, class Type>
const_mem_fun_t<Result, Type> mem_fun(Result (Type::* pMem)() const);

template <class Result, class Type, class Arg>
const_mem_fun1_t<Result, Type, Arg> mem_fun(Result (Type::* pMem)(Arg) const);
```

### <a name="parameters"></a>Parámetros

*pMem*\
Un puntero a la función miembro de clase `Type` que se convertirá en un objeto de función.

### <a name="return-value"></a>Valor devuelto

Un objeto de función **const** o **non_const** de tipo `mem_fun_t` o `mem_fun1_t`.

### <a name="example"></a>Ejemplo

```cpp
// functional_mem_fun.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

class StoreVals
{
    int val;
public:
    StoreVals() { val = 0; }
    StoreVals(int j) { val = j; }

    bool display() { cout << val << " "; return true; }
    int squareval() { val *= val; return val; }
    int lessconst(int k) {val -= k; return val; }
};

int main( )
{
    vector<StoreVals *> v1;

    StoreVals sv1(5);
    v1.push_back(&sv1);
    StoreVals sv2(10);
    v1.push_back(&sv2);
    StoreVals sv3(15);
    v1.push_back(&sv3);
    StoreVals sv4(20);
    v1.push_back(&sv4);
    StoreVals sv5(25);
    v1.push_back(&sv5);

    cout << "The original values stored are: " ;
    for_each(v1.begin(), v1.end(), mem_fun<bool, StoreVals>(&StoreVals::display));
    cout << endl;

    // Use of mem_fun calling member function through a pointer
    // square each value in the vector using squareval ()
    for_each(v1.begin(), v1.end(), mem_fun<int, StoreVals>(&StoreVals::squareval));
    cout << "The squared values are: " ;
    for_each(v1.begin(), v1.end(), mem_fun<bool, StoreVals>(&StoreVals::display));
    cout << endl;

    // Use of mem_fun1 calling member function through a pointer
    // subtract 5 from each value in the vector using lessconst ()
    for_each(v1.begin(), v1.end(),
        bind2nd (mem_fun1<int, StoreVals,int>(&StoreVals::lessconst), 5));
    cout << "The squared values less 5 are: " ;
    for_each(v1.begin(), v1.end(), mem_fun<bool, StoreVals>(&StoreVals::display));
    cout << endl;
}
```

## <a name="mem_fun_ref"></a> mem_fun_ref

Las funciones de plantilla del asistente usadas para crear adaptadores de objeto de función para las funciones miembro cuando se inicializan con argumentos de referencia. En desuso en C ++ 11, se ha quitado en C ++ 17.

```cpp
template <class Result, class Type>
mem_fun_ref_t<Result, Type> mem_fun_ref(Result (Type::* pMem)());

template <class Result, class Type, class Arg>
mem_fun1_ref_t<Result, Type, Arg> mem_fun_ref(Result (Type::* pMem)(Arg));

template <class Result, class Type>
const_mem_fun_ref_t<Result, Type> mem_fun_ref(Result Type::* pMem)() const);

template <class Result, class Type, class Arg>
const_mem_fun1_ref_t<Result, Type, Arg> mem_fun_ref(Result (T::* pMem)(Arg) const);
```

### <a name="parameters"></a>Parámetros

*pMem*\
Un puntero a la función miembro de clase `Type` que se convertirá en un objeto de función.

### <a name="return-value"></a>Valor devuelto

Un **const** o `non_const` objeto de función de tipo `mem_fun_ref_t` o `mem_fun1_ref_t`.

### <a name="example"></a>Ejemplo

```cpp
// functional_mem_fun_ref.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

class NumVals
   {
   int val;
   public:
   NumVals ( ) { val = 0; }
   NumVals ( int j ) { val = j; }

   bool display ( ) { cout << val << " "; return true; }
   bool isEven ( ) { return ( bool )  !( val %2 ); }
   bool isPrime( )
   {
      if (val < 2) { return true; }
      for (int i = 2; i <= val / i; ++i)
      {
         if (val % i == 0) { return false; }
      }
      return true;
   }
};

int main( )
{
   vector <NumVals> v1 ( 13 ), v2 ( 13 );
   vector <NumVals>::iterator v1_Iter, v2_Iter;
   int i, k;

   for ( i = 0; i < 13; i++ ) v1 [ i ] = NumVals ( i+1 );
   for ( k = 0; k < 13; k++ ) v2 [ k ] = NumVals ( k+1 );

   cout << "The original values stored in v1 are: " ;
   for_each( v1.begin( ), v1.end( ),
   mem_fun_ref ( &NumVals::display ) );
   cout << endl;

   // Use of mem_fun_ref calling member function through a reference
   // remove the primes in the vector using isPrime ( )
   v1_Iter = remove_if ( v1.begin( ),  v1.end( ),
      mem_fun_ref ( &NumVals::isPrime ) );
   cout << "With the primes removed, the remaining values in v1 are: " ;
   for_each( v1.begin( ), v1_Iter,
   mem_fun_ref ( &NumVals::display ) );
   cout << endl;

   cout << "The original values stored in v2 are: " ;
   for_each( v2.begin( ), v2.end( ),
   mem_fun_ref ( &NumVals::display ) );
   cout << endl;

   // Use of mem_fun_ref calling member function through a reference
   // remove the even numbers in the vector v2 using isEven ( )
   v2_Iter = remove_if ( v2.begin( ),  v2.end( ),
      mem_fun_ref ( &NumVals::isEven ) );
   cout << "With the even numbers removed, the remaining values are: " ;
   for_each( v2.begin( ),  v2_Iter,
   mem_fun_ref ( &NumVals::display ) );
   cout << endl;
}
```

```Output
The original values stored in v1 are: 1 2 3 4 5 6 7 8 9 10 11 12 13
With the primes removed, the remaining values in v1 are: 4 6 8 9 10 12
The original values stored in v2 are: 1 2 3 4 5 6 7 8 9 10 11 12 13
With the even numbers removed, the remaining values are: 1 3 5 7 9 11 13
```

## <a name="not1"></a> not1

Devuelve el complemento de un predicado unario. En desuso para [not_fn](#not_fn) en C ++ 17.

```cpp
template <class UnaryPredicate>
unary_negate<UnaryPredicate> not1(const UnaryPredicate& predicate);
```

### <a name="parameters"></a>Parámetros

*predicado*\
Predicado unario que se va a negar.

### <a name="return-value"></a>Valor devuelto

Un predicado unario que es la negación del predicado unario modificado.

### <a name="remarks"></a>Comentarios

Si un `unary_negate` se construye a partir de un predicado unario `predicate(x)`, a continuación, devuelve `!predicate(x)`.

### <a name="example"></a>Ejemplo

```cpp
// functional_not1.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 7; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    vector<int>::iterator::difference_type result1;
    // Count the elements greater than 10
    result1 = count_if(v1.begin(), v1.end(), bind2nd(greater<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;

    vector<int>::iterator::difference_type result2;
    // Use the negator to count the elements less than or equal to 10
    result2 = count_if(v1.begin(), v1.end(),
        not1(bind2nd(greater<int>(), 10)));

    cout << "The number of elements in v1 not greater than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 30 35 )
The number of elements in v1 greater than 10 is: 5.
The number of elements in v1 not greater than 10 is: 3.
```

## <a name="not2"></a> not2

Devuelve el complemento de un predicado binario. En desuso para [not_fn](#not_fn) en C ++ 17.

```cpp
template <class BinaryPredicate>
binary_negate<BinaryPredicate> not2(const BinaryPredicate& func);
```

### <a name="parameters"></a>Parámetros

*Func*\
Predicado binario que se va a negar.

### <a name="return-value"></a>Valor devuelto

Un predicado binario que es la negación del predicado binario modificado.

### <a name="remarks"></a>Comentarios

Si un `binary_negate` se construye a partir de un predicado binario `binary_predicate(x, y)`, a continuación, devuelve `!binary_predicate(x, y)`.

### <a name="example"></a>Ejemplo

```cpp
// functional_not2.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <cstdlib>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   v1.push_back( 6262 );
   v1.push_back( 6262 );
   for ( i = 0 ; i < 5 ; i++ )
   {
      v1.push_back( rand( ) );
   }

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in ascending order,
   // use default binary predicate less<int>( )
   sort( v1.begin( ), v1.end( ) );
   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in descending order,
   // use the binary_negate helper function not2
   sort( v1.begin( ), v1.end( ), not2(less<int>( ) ) );
   cout << "Resorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = ( 6262 6262 41 18467 6334 26500 19169 )
Sorted vector v1 = ( 41 6262 6262 6334 18467 19169 26500 )
Resorted vector v1 = ( 26500 19169 18467 6334 6262 6262 41 )
```

## <a name="not_fn"></a> not_fn

El `not_fn` plantilla de función toma un objeto que se puede llamar y devuelve un objeto que se puede llamar. Cuando más tarde se invoca el objeto devuelto que se puede llamar con algunos argumentos, se pasa al objeto original que se puede llamar y lógicamente niega el resultado. Conserva el comportamiento de la categoría de clasificación y el valor const del objeto ajustado que se puede llamar. `not_fn` Novedades de C ++ 17 y reemplaza el desuso `std::not1`, `std::not2`, `std::unary_negate`, y `std::binary_negate`.

```cpp
template <class Callable>
/* unspecified */ not_fn(Callable&& func);
```

### <a name="parameters"></a>Parámetros

*Func*\
Un objeto que se puede llamar para construir las llamadas de reenvío contenedor.

### <a name="remarks"></a>Comentarios

La función de plantilla devuelve un contenedor de llamadas, como `return call_wrapper(std::forward<Callable>(func))`, en función de esta clase solo exposition:

```cpp
class call_wrapper
{
   using FD = decay_t<Callable>;
   explicit call_wrapper(Callable&& func);

public:
   call_wrapper(call_wrapper&&) = default;
   call_wrapper(call_wrapper const&) = default;

   template<class... Args>
     auto operator()(Args&&...) & -> decltype(!declval<invoke_result_t<FD&(Args...)>>());

   template<class... Args>
     auto operator()(Args&&...) const& -> decltype(!declval<invoke_result_t<FD const&(Args...)>>());

   template<class... Args>
     auto operator()(Args&&...) && -> decltype(!declval<invoke_result_t<FD(Args...)>>());

   template<class... Args>
     auto operator()(Args&&...) const&& -> decltype(!declval<invoke_result_t<FD const(Args...)>>());

private:
  FD fd;
};
```

El constructor explícito en el objeto que se puede llamar *func* requiere tipo `std::decay_t<Callable>` para satisfacer los requisitos de `MoveConstructible`, y `is_constructible_v<FD, Callable>` debe ser true. Inicializa el objeto que se puede llamar ajustado `fd` desde `std::forward<Callable>(func)`y se produce cualquier excepción producida por la construcción de `fd`.

El contenedor expone los operadores de llamada que se distinguen por categoría referencia lvalue o rvalue y calificación de const, como se muestra aquí:

```cpp
template<class... Args> auto operator()(Args&&... args) & -> decltype(!declval<invoke_result_t<FD&(Args...)>>());
template<class... Args> auto operator()(Args&&... args) const& -> decltype(!declval<invoke_result_t<FD const&(Args...)>>());
template<class... Args> auto operator()(Args&&... args) && -> decltype(!declval<invoke_result_t<FD(Args...)>>());
template<class... Args> auto operator()(Args&&... args) const&& -> decltype(!declval<invoke_result_t<FD const(Args...)>>());
```

Los dos primeros son los mismos que `return !std::invoke(fd, std::forward<Args>(args)...)`. Los segundos dos son los mismos que `return !std::invoke(std::move(fd), std::forward<Args>(args)...)`.

### <a name="example"></a>Ejemplo

```cpp
// functional_not_fn_.cpp
// compile with: /EHsc /std:c++17
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main()
{
    std::vector<int> v1 = { 99, 6264, 41, 18467, 6334, 26500, 19169 };
    auto divisible_by_3 = [](int i){ return i % 3 == 0; };

    std::cout << "Vector v1 = ( " ;
    for (const auto& item : v1)
    {
        std::cout << item << " ";
    }
    std::cout << ")" << std::endl;

    // Count the number of vector elements divisible by 3.
    int divisible =
        std::count_if(v1.begin(), v1.end(), divisible_by_3);
    std::cout << "Elements divisible by three: "
        << divisible << std::endl;

    // Count the number of vector elements not divisible by 3.
    int not_divisible =
        std::count_if(v1.begin(), v1.end(), std::not_fn(divisible_by_3));
    std::cout << "Elements not divisible by three: "
        << not_divisible << std::endl;
}
```

```Output
Vector v1 = ( 99 6264 41 18467 6334 26500 19169 )
Elements divisible by three: 2
Elements not divisible by three: 5
```

## <a name="ptr_fun"></a> ptr_fun

Funciones de plantilla del asistente usadas para convertir punteros de funciones unarias y binarias, respectivamente, en funciones unarias y binarias adaptables. En desuso en C ++ 11, se ha quitado en C ++ 17.

```cpp
template <class Arg, class Result>
pointer_to_unary_function<Arg, Result, Result (*)(Arg)> ptr_fun(Result (*pfunc)(Arg));

template <class Arg1, class Arg2, class Result>
pointer_to_binary_function<Arg1, Arg2, Result, Result (*)(Arg1, Arg2)> ptr_fun(Result (*pfunc)(Arg1, Arg2));
```

### <a name="parameters"></a>Parámetros

*pfunc*\
El puntero de función unaria o binaria que se convertirá en una función adaptable.

### <a name="return-value"></a>Valor devuelto

La primera función de plantilla devuelve la función unaria [pointer_to_unary_function](../standard-library/pointer-to-unary-function-class.md) <`Arg`, **resultado**> (\* `pfunc`).

La segunda función de plantilla devuelve la función binaria [pointer_to_binary_function](../standard-library/pointer-to-binary-function-class.md) \< **Arg1**, **Arg2**, **resultado**> (\* `pfunc`).

### <a name="remarks"></a>Comentarios

Un puntero de función es un objeto de función. Se puede pasar a cualquier algoritmo que espera una función como un parámetro, pero no es adaptable. Información acerca de sus tipos anidados es necesaria usar un adaptador, por ejemplo, para enlazar un valor o para negar. La conversión de punteros de función unarios y binarios mediante la función del asistente `ptr_fun` permite a los adaptadores de función trabajar con punteros de función unarios y binarios.

### <a name="example"></a>Ejemplo

[!code-cpp[functional_ptr_fun#1](../standard-library/codesnippet/CPP/functional-functions_1.cpp)]

## <a name="ref"></a> ref

Construye un `reference_wrapper` a partir de un argumento.

```cpp
template <class Ty>
    reference_wrapper<Ty> ref(Ty& arg);

template <class Ty>
    reference_wrapper<Ty> ref(reference_wrapper<Ty>& arg);
```

### <a name="return-value"></a>Valor devuelto

Referencia a `arg`, específicamente, `reference_wrapper<Ty>(arg)`.

### <a name="example"></a>Ejemplo

El siguiente ejemplo define dos funciones: una enlazada a una variable de cadena y la otra enlazada a una referencia de la variable de cadena calculada mediante una llamada a `ref`. Cuando el valor de la variable cambia, la primera función continúa usando el valor antiguo y la segunda función usa el nuevo valor.

```cpp
#include <algorithm>
#include <functional>
#include <iostream>
#include <iterator>
#include <ostream>
#include <string>
#include <vector>
using namespace std;
using namespace std;
using namespace std::placeholders;

bool shorter_than(const string& l, const string& r) {
    return l.size() < r.size();
}

int main() {
    vector<string> v_original;
    v_original.push_back("tiger");
    v_original.push_back("cat");
    v_original.push_back("lion");
    v_original.push_back("cougar");

    copy(v_original.begin(), v_original.end(), ostream_iterator<string>(cout, " "));
    cout << endl;

    string s("meow");

    function<bool (const string&)> f = bind(shorter_than, _1, s);
    function<bool (const string&)> f_ref = bind(shorter_than, _1, ref(s));

    vector<string> v;

    // Remove elements that are shorter than s ("meow")

    v = v_original;
    v.erase(remove_if(v.begin(), v.end(), f), v.end());

    copy(v.begin(), v.end(), ostream_iterator<string>(cout, " "));
    cout << endl;

    // Now change the value of s.
    // f_ref, which is bound to ref(s), will use the
    // new value, while f is still bound to the old value.

    s = "kitty";

    // Remove elements that are shorter than "meow" (f is bound to old value of s)

    v = v_original;
    v.erase(remove_if(v.begin(), v.end(), f), v.end());

    copy(v.begin(), v.end(), ostream_iterator<string>(cout, " "));
    cout << endl;

    // Remove elements that are shorter than "kitty" (f_ref is bound to ref(s))

    v = v_original;
    v.erase(remove_if(v.begin(), v.end(), f_ref), v.end());

    copy(v.begin(), v.end(), ostream_iterator<string>(cout, " "));
    cout << endl;
}
```

```Output
tiger cat lion cougar
tiger lion cougar
tiger lion cougar
tiger cougar
```

## <a name="swap"></a> intercambio

Intercambia dos objetos `function`.

```cpp
template <class FT>
    void swap(function<FT>& f1, function<FT>& f2);
```

### <a name="parameters"></a>Parámetros

*FT*\
Tipo controlado por los objetos de función.

*F1*\
El primer objeto de función.

*F2*\
El segundo objeto de función.

### <a name="remarks"></a>Comentarios

La función devuelve `f1.swap(f2)`.

### <a name="example"></a>Ejemplo

```cpp
// std__functional__swap.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0(neg);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << "val == " << fn0(3) << std::endl;

    std::function<int (int)> fn1;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << std::endl;

    swap(fn0, fn1);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
empty == true

empty == true
empty == false
val == -3
```
