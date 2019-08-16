---
title: Funciones de &lt;utility&gt;
ms.date: 11/04/2016
f1_keywords:
- utility/std::exchange
- utility/std::forward
- utility/std::make_pair
- utility/std::move
- utility/std::swap
ms.assetid: b1df38cd-3a59-4098-9c81-83342eb719a4
helpviewer_keywords:
- std::exchange [C++]
- std::forward [C++]
- std::make_pair [C++]
- std::move [C++]
- std::swap [C++]
ms.openlocfilehash: 723b077500b9b741445efcd8574fb26cd53e5fc7
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246307"
---
# <a name="ltutilitygt-functions"></a>Funciones de &lt;utility&gt;

## <a name="asconst"></a> as_const

```cpp
template <class T> constexpr add_const_t<T>& as_const(T& t) noexcept;
template <class T> void as_const(const T&&) = delete;
```

### <a name="return-value"></a>Valor devuelto

Devuelve *T*.

## <a name="declval"></a> declval)

```cpp
template <class T> add_rvalue_reference_t<T> declval() noexcept;  // as unevaluated operand
```

## <a name="exchange"></a> Exchange

**(C++14)** Asigna un nuevo valor a un objeto y devuelve su valor anterior.

```cpp
template <class T, class Other = T>
    T exchange(T& val, Other&& new_val)
```

### <a name="parameters"></a>Parámetros

*Val*\
El objeto que va a recibir el valor de new_val.

*new_val*\
El objeto cuyo valor se ha copiado o movido a val.

### <a name="remarks"></a>Comentarios

Para los tipos complejos, `exchange` evita copiar el valor anterior cuando está disponible un constructor de movimiento, evita copiar el valor nuevo si es un objeto temporal o si se mueve, y acepta cualquier tipo como el valor nuevo, utilizando cualquier operador de asignación y conversión disponible. La función exchange es diferente de [STD](../standard-library/algorithm-functions.md#swap) en que el argumento izquierdo no se ha movido o copiado en el argumento derecho.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar `exchange`. En el mundo real, `exchange` resulta más útil con objetos grandes que cuesta mucho copiar:

```cpp
#include <utility>
#include <iostream>

using namespace std;

struct C
{
   int i;
   //...
};

int main()
{
   // Use brace initialization
   C c1{ 1 };
   C c2{ 2 };
   C result = exchange(c1, c2);
   cout << "The old value of c1 is: " << result.i << endl;
   cout << "The new value of c1 after exchange is: " << c1.i << endl;

   return 0;
}
```

```Output
The old value of c1 is: 1
The new value of c1 after exchange is: 2
```

## <a name="forward"></a> hacia delante

Convierte condicionalmente su argumento a una referencia de valor R si el argumento es un valor R o una referencia de valor R. Esto restaura el valor R de un argumento a la función de reenvío para permitir el reenvío directo.

```cpp
template <class Type>    // accepts lvalues
    constexpr Type&& forward(typename remove_reference<Type>::type& Arg) noexcept

template <class Type>    // accepts everything else
    constexpr Type&& forward(typename remove_reference<Type>::type&& Arg) noexcept
```

### <a name="parameters"></a>Parámetros

*Tipo*\
El tipo del valor pasado en *Arg*, que puede ser diferente que el tipo de *Arg*. Lo suele determinar un argumento de plantilla de la función de reenvío.

*arg*\
Argumento que se va a convertir.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia rvalue para *Arg* si el valor pasado en *Arg* era originalmente un valor r o una referencia a un valor r; de lo contrario, devuelve *Arg* sin modificar su tipo.

### <a name="remarks"></a>Comentarios

Debe especificar un argumento de plantilla explícito para llamar a `forward`.

`forward` no reenvía su argumento. En su lugar, convirtiendo condicionalmente su argumento a una referencia de valor R si era originalmente un valor R o una referencia de valor R, `forward` permite al compilador realizar la resolución de sobrecargas conociendo del tipo original del argumento reenviado. El tipo aparente de un argumento a una función de reenvío podría ser diferente de su tipo original, por ejemplo, cuando un valor r se usa como argumento a una función y se enlaza a un nombre de parámetro. Si tiene un nombre convierte un valor de l, con cualquier valor exista realmente como un valor r, `forward` restaura el valor r del argumento.

Restaurar el valor r del valor original del argumento para la resolución de sobrecarga se conoce como *el reenvío directo*. El reenvío directo permite que una función de plantilla acepte un argumento de cualquier tipo de referencia y restaure su valor R cuando sea necesario para la correcta resolución de sobrecargas. Mediante el reenvío directo, se puede conservar la semántica de movimiento para los valores R y evitar tener que proporcionar sobrecargas para las funciones que solo varían por el tipo de referencia de sus argumentos.

## <a name="from_chars"></a> from_chars

```cpp
from_chars_result from_chars(const char* first, const char* last, see below& value, int base = 10);

from_chars_result from_chars(const char* first, const char* last, float& value, chars_format fmt = chars_format::general); 

from_chars_result from_chars(const char* first, const char* last, double& value, chars_format fmt = chars_format::general); 

from_chars_result from_chars(const char* first, const char* last, long double& value, chars_format fmt = chars_format::general);
```

## <a name="get"></a> Obtener

Obtiene un elemento de un objeto `pair` , por posición de índice o por tipo.

```cpp
// get reference to element at Index in pair Pr
template <size_t Index, class T1, class T2>
    constexpr tuple_element_t<Index, pair<T1, T2>>&
    get(pair<T1, T2>& Pr) noexcept;

// get reference to element T1 in pair Pr
template <class T1, class T2>
    constexpr T1& get(pair<T1, T2>& Pr) noexcept;

// get reference to element T2 in pair Pr
template <class T2, class T1>
    constexpr T2& get(pair<T1, T2>& Pr) noexcept;

// get const reference to element at Index in pair Pr
template <size_t Index, class T1, class T2>
    constexpr const tuple_element_t<Index, pair<T1, T2>>&
    get(const pair<T1, T2>& Pr) noexcept;

// get const reference to element T1 in pair Pr
template <class T1, class T2>
    constexpr const T1& get(const pair<T1, T2>& Pr) noexcept;

// get const reference to element T2 in pair Pr
template <class T2, class T1>
    constexpr const T2& get(const pair<T1, T2>& Pr) noexcept;

// get rvalue reference to element at Index in pair Pr
template <size_t Index, class T1, class T2>
    constexpr tuple_element_t<Index, pair<T1, T2>>&&
    get(pair<T1, T2>&& Pr) noexcept;

// get rvalue reference to element T1 in pair Pr
template <class T1, class T2>
    constexpr T1&& get(pair<T1, T2>&& Pr) noexcept;

// get rvalue reference to element T2 in pair Pr
template <class T2, class T1>
    constexpr T2&& get(pair<T1, T2>&& Pr) noexcept;
```

### <a name="parameters"></a>Parámetros

*Índice*\
El índice de base 0 del elemento seleccionado.

*T1*\
El tipo del primer elemento par.

*T2*\
El tipo del segundo elemento par.

*incorporación de cambios*\
Par del que se selecciona.

### <a name="remarks"></a>Comentarios

Las funciones de plantilla devuelven una referencia a un elemento de su argumento `pair` .

Para las sobrecargas indexadas, si el valor de *índice* es 0, las funciones devuelven `pr.first` y si el valor de *índice* es 1, las funciones devuelven `pr.second`. El tipo `RI` es el tipo del elemento devuelto.

Para las sobrecargas que no tienen un parámetro de índice, se deduce el argumento de tipo de elemento que se va a devolver. Una llamada a `get<T>(Tuple)` se producirá un error del compilador si *pr* contiene más o menos de un elemento de tipo T.

### <a name="example"></a>Ejemplo

```cpp
#include <utility>
#include <iostream>
using namespace std;
int main()
{

    typedef pair<int, double> MyPair;

    MyPair c0(9, 3.14);

    // get elements by index
    cout << " " << get<0>(c0);
    cout << " " << get<1>(c0) << endl;

    // get elements by type (C++14)
    MyPair c1(1, 0.27);
    cout << " " << get<int>(c1);
    cout << " " << get<double>(c1) << endl;
}
```

```Output
9 3.14
1 0.27
```

## <a name="index_sequence"></a> index_sequence

```cpp
template<size_t... I>
    using index_sequence = integer_sequence<size_t, I...>;
```

## <a name="index_sequence_for"></a> index_sequence_for

```cpp
template<class... T>
    using index_sequence_for = make_index_sequence<sizeof...(T)>;
```

## <a name="make_index_sequence"></a> make_index_sequence

```cpp
template<size_t N>
    using make_index_sequence = make_integer_sequence<size_t, N>;
```

## <a name="make_integer_sequence"></a> make_integer_sequence

```cpp
template<class T, T N>
    using make_integer_sequence = integer_sequence<T, see below >;
```

## <a name="make_pair"></a> make_pair

Una función de plantilla que se usa para construir objetos de tipo `pair`, donde los tipos de componente se eligen automáticamente basándose en los tipos de datos que se pasan como parámetros.

```cpp
template <class T, class U>
    pair<T, U> make_pair(T& Val1, U& Val2);

template <class T, class U>
    pair<T, U> make_pair(T& Val1, U&& Val2);

template <class T, class U>
    pair<T, U> make_pair(T&& Val1, U& Val2);

template <class T, class U>
    pair<T, U> make_pair(T&& Val1, U&& Val2);
```

### <a name="parameters"></a>Parámetros

*val1*\
Valor que inicializa el primer elemento de `pair`.

*Val2*\
Valor que inicializa el segundo elemento de `pair`.

### <a name="return-value"></a>Valor devuelto

El objeto de par que se construye: `pair` < `T`,`U`> (`Val1`, `Val2`).

### <a name="remarks"></a>Comentarios

`make_pair` convierte el objeto de tipo [reference_wrapper (Clase)](../standard-library/reference-wrapper-class.md) en tipos de referencia y convierte las matrices y las funciones que decaen en punteros.

En el objeto `pair` devuelto, `T` se determina como sigue:

- Si el tipo de entrada `T` es `reference_wrapper<X>`, el tipo devuelto `T` es `X&`.

- De lo contrario, el tipo devuelto `T` es `decay<T>::type`. Si [Decay (clase)](../standard-library/decay-class.md) no es compatible, el tipo devuelto `T` es el mismo que el tipo de entrada `T`.

El tipo devuelto `U` se determina de igual forma a partir del tipo de entrada `U`.

Una ventaja de `make_pair` es que los tipos de objetos que se almacenan, se determinan automáticamente por el compilador y no tienen que especificarse explícitamente. No use los argumentos de plantilla explícitos como `make_pair<int, int>(1, 2)` cuando usas `make_pair` porque es detallado y agrega los problemas de referencia rvalue complejos que pueden provocar un error de compilación. En este ejemplo, la sintaxis correcta sería `make_pair(1, 2)`.

La función del asistente `make_pair` también permite pasar dos valores a una función que requiera un par como un parámetro de entrada.

### <a name="example"></a>Ejemplo

Para obtener un ejemplo sobre cómo usar la función del asistente `make_pair` para declarar e inicializar un par, vea [pair (Estructura)](../standard-library/pair-structure.md).

## <a name="move"></a> Mover

Convierte incondicionalmente su argumento en una referencia rvalue y de este modo indica que se puede mover si su tipo tiene habilitado el movimiento.

```cpp
template <class Type>
    constexpr typename remove_reference<Type>::type&& move(Type&& Arg) noexcept;
```

### <a name="parameters"></a>Parámetros

*Tipo*\
Pasa un tipo inferido a partir del tipo del argumento *Arg*, junto con las reglas de contracción de referencias.

*arg*\
Argumento que se va a convertir. Aunque el tipo de *Arg* parece estar especificado como una referencia rvalue, `move` también acepta argumentos lvalue porque las referencias de valor l se pueden enlazar a las referencias rvalue.

### <a name="return-value"></a>Valor devuelto

`Arg` como referencia rvalue, independientemente de si su tipo es un tipo de referencia.

### <a name="remarks"></a>Comentarios

El argumento de plantilla *tipo* no está pensado para especificarse explícitamente, sino para deducirse a partir del valor pasado en el tipo de *Arg*. El tipo de *tipo* aún más se ajusta según las reglas de contracción de referencias.

`move` no se mueve su argumento. En su lugar, al convertir incondicionalmente su argumento, que podría ser un valor l, en una referencia rvalue, permite al compilador mover posteriormente, en lugar de copia, el valor pasado en *Arg* si su tipo tiene habilitado el movimiento. Si su tipo no está habilitado el movimiento, se copia en su lugar.

Si el valor pasado en *Arg* es un valor l, es decir, tiene un nombre o se puede obtener su dirección, se invalida cuando se produce el movimiento. No hacer referencia al valor pasado en *Arg* por su nombre o dirección una vez que se han movido.

## <a name="moveif"></a> move_if_noexcept

```cpp
template <class T> constexpr conditional_t< !is_nothrow_move_constructible_v<T> && is_copy_constructible_v<T>, const T&, T&&> move_if_noexcept(T& x) noexcept;
```

## <a name="swap"></a> intercambio

Intercambia los elementos de dos tipos o [emparejar estructura](../standard-library/pair-structure.md) objetos.

```cpp
template <class T>
    void swap(T& left, T& right) noexcept(see below );
template <class T, size_t N>
    void swap(T (&left)[N], T (&right)[N]) noexcept(is_nothrow_swappable_v<T>);
template <class T, class U>
    void swap(pair<T, U>& left, pair<T, U>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Un objeto de tipo o `pair`.

*Correcto*\
Un objeto de tipo o `pair`.

### <a name="remarks"></a>Comentarios

Una ventaja de `swap` es que los tipos de objetos que se almacenan, se determinan automáticamente por el compilador y no tienen que especificarse explícitamente. No use los argumentos de plantilla explícitos como `swap<int, int>(1, 2)` cuando usas `swap` porque es detallado y agrega los problemas de referencia rvalue complejos que pueden provocar un error de compilación.

## <a name="to_chars"></a> to_chars

```cpp
to_chars_result to_chars(char* first, char* last, see below value, int base = 10);
to_chars_result to_chars(char* first, char* last, float value); 
to_chars_result to_chars(char* first, char* last, double value); 
to_chars_result to_chars(char* first, char* last, long double value);
to_chars_result to_chars(char* first, char* last, float value, chars_format fmt); 
to_chars_result to_chars(char* first, char* last, double value, chars_format fmt); 
to_chars_result to_chars(char* first, char* last, long double value, chars_format fmt);
to_chars_result to_chars(char* first, char* last, float value, chars_format fmt, int precision); 
to_chars_result to_chars(char* first, char* last, double value, chars_format fmt, int precision); 
to_chars_result to_chars(char* first, char* last, long double value, chars_format fmt, int precision);
```

### <a name="remarks"></a>Comentarios

Convierte el valor en una cadena de caracteres al rellenar el intervalo `[first, last)`, donde `[first, last)` debe ser un intervalo válido.
