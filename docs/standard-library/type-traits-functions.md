---
title: Funciones de &lt;type_traits&gt;
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_assignable
- type_traits/std::is_copy_assignable
- type_traits/std::is_copy_constructible
- type_traits/std::is_default_constructible
- type_traits/std::is_move_assignable
- type_traits/std::is_move_constructible
- type_traits/std::is_nothrow_move_assignable
- type_traits/std::is_trivially_copy_assignable
- type_traits/std::is_trivially_move_assignable
- type_traits/std::is_trivially_move_constructible
ms.assetid: dce4492f-f3e4-4d5e-bdb4-5875321254ec
helpviewer_keywords:
- std::is_assignable
- std::is_copy_assignable
- std::is_copy_constructible
- std::is_default_constructible
- std::is_move_assignable
- std::is_move_constructible
- std::is_nothrow_move_assignable
- std::is_trivially_copy_assignable
- std::is_trivially_move_assignable
- std::is_trivially_move_constructible
ms.openlocfilehash: d607e68bd61a4f9aa6c00ab66c5ded3ecd508082
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68241506"
---
# <a name="lttypetraitsgt-functions"></a>Funciones de &lt;type_traits&gt;

||||
|-|-|-|
|[is_assignable](#is_assignable)|[is_copy_assignable](#is_copy_assignable)|[is_copy_constructible](#is_copy_constructible)|
|[is_default_constructible](#is_default_constructible)|[is_move_assignable](#is_move_assignable)|[is_move_constructible](#is_move_constructible)|
|[is_nothrow_move_assignable](#is_nothrow_move_assignable)|[is_nothrow_swappable](#is_nothrow_swappable)|[is_nothrow_swappable_with](#is_nothrow_swappable_with)|
|[is_swappable](#is_swappable)|[is_swappable_with](#is_swappable_with)|[is_trivially_copy_assignable](#is_trivially_copy_assignable)|
|[is_trivially_move_assignable](#is_trivially_move_assignable)|[is_trivially_move_constructible](#is_trivially_move_constructible)|

## <a name="is_assignable"></a>  is_assignable

Comprueba si un valor de *desde* tipo puede asignarse a un *a* tipo.

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>Parámetros

*En*<br/>
El tipo del objeto que recibe la asignación.

*From*<br/>
El tipo del objeto que proporciona el valor.

### <a name="remarks"></a>Comentarios

La expresión no evaluada `declval<To>() = declval<From>()` debe tener un formato correcto. Ambos *desde* y *a* deben ser tipos completos, **void**, o matrices de límite desconocido.

## <a name="is_copy_assignable"></a>  is_copy_assignable

Comprueba si el tipo se puede copiar en la asignación.

```cpp
template <class Ty>
struct is_copy_assignable;
```

### <a name="parameters"></a>Parámetros

*Ty*<br/>
Tipo que se va a consultar.

### <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *Ty* es una clase que tiene un copia operador de asignación, en caso contrario, es false. Equivalente a is_assignable\<Ty&, const Ty&>.

## <a name="is_copy_constructible"></a>  is_copy_constructible

Comprueba si el tipo tiene un constructor de copia.

```cpp
template <class Ty>
struct is_copy_constructible;
```

### <a name="parameters"></a>Parámetros

*Ty*<br/>
Tipo que se va a consultar.

### <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *Ty* es una clase que tiene un constructor de copias, en caso contrario, es false.

### <a name="example"></a>Ejemplo

```cpp
#include <type_traits>
#include <iostream>

struct Copyable
{
    int val;
};

struct NotCopyable
{
   NotCopyable(const NotCopyable&) = delete;
   int val;

};

int main()
{
    std::cout << "is_copy_constructible<Copyable> == " << std::boolalpha
        << std::is_copy_constructible<Copyable>::value << std::endl;
    std::cout << "is_copy_constructible<NotCopyable> == " << std::boolalpha
        << std::is_copy_constructible<NotCopyable>::value << std::endl;

    return (0);
}
```

```Output
is_copy_constructible<Copyable> == true
is_copy_constructible<NotCopyable > == false
```

## <a name="is_default_constructible"></a>  is_default_constructible

Comprueba si un tipo tiene un constructor predeterminado.

```cpp
template <class Ty>
struct is_default_constructible;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo que se va a consultar.

### <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *T* es un tipo de clase que tiene un constructor predeterminado, en caso contrario, es false. Es equivalente al elemento `is_constructible<T>`del predicado. Tipo *T* debe ser un tipo completo, **void**, o una matriz de límite desconocido.

### <a name="example"></a>Ejemplo

```cpp
#include <type_traits>
#include <iostream>

struct Simple
{
    Simple() : val(0) {}
    int val;
};

struct Simple2
{
    Simple2(int v) : val(v) {}
    int val;
};

int main()
{
    std::cout << "is_default_constructible<Simple> == " << std::boolalpha
        << std::is_default_constructible<Simple>::value << std::endl;
    std::cout << "is_default_constructible<Simple2> == " << std::boolalpha
        << std::is_default_constructible<Simple2>::value << std::endl;

    return (0);
}
```

```Output
is_default_constructible<Simple> == true
is_default_constructible<Simple2> == false
```

## <a name="is_move_assignable"></a>  is_move_assignable

Comprueba si el tipo se puede asignar mediante movimiento.

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo que se va a consultar.

### <a name="remarks"></a>Comentarios

Un tipo se puede asignar mediante movimiento si una referencia a un valor R al tipo se puede asignar a una referencia al tipo. El predicado de tipo es equivalente a `is_assignable<T&, T&&>`. Los tipos que se pueden asignar mediante movimiento incluyen los tipos escalares a los que se puede hacer referencia y los tipos de clase que tienen operadores de asignación de movimiento generados por el compilador o definidos por el usuario.

## <a name="is_move_constructible"></a>  is_move_constructible

Comprueba si el tipo tiene un constructor de movimiento.

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo que se debe evaluar

### <a name="remarks"></a>Comentarios

Un predicado de tipo que se evalúa como true si el tipo *T* puede crearse mediante el uso de una operación de movimiento. Este predicado es equivalente a `is_constructible<T, T&&>`.

## <a name="is_nothrow_move_assignable"></a>  is_nothrow_move_assignable

Comprueba si el tipo tiene un operador de asignación de movimiento **nothrow**.

```cpp
template <class Ty>
struct is_nothrow_move_assignable;
```

### <a name="parameters"></a>Parámetros

*Ty*<br/>
Tipo que se va a consultar.

### <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *Ty* tiene un nothrow mover operador de asignación, en caso contrario, es false.

## <a name="is_nothrow_swappable"></a>  is_nothrow_swappable

```cpp
template <class T> struct is_nothrow_swappable;
```

## <a name="is_nothrow_swappable_with"></a>  is_nothrow_swappable_with

```cpp
template <class T, class U> struct is_nothrow_swappable_with;
```

## <a name="is_swappable"></a>  is_swappable

```cpp
template <class T> struct is_swappable;
```

## <a name="is_swappable_with"></a>  is_swappable_with

```cpp
template <class T, class U> struct is_swappable_with;
```

## <a name="is_trivially_copy_assignable"></a>  is_trivially_copy_assignable

Comprueba si el tipo tiene un operador de asignación de copia trivial.

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo que se va a consultar.

### <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *T* es una clase que tiene un copia trivial operador de asignación, en caso contrario, es false.

Un constructor de asignación para una clase *T* es trivial si se proporciona implícitamente, la clase *T* no tiene ninguna función virtual, la clase *T* tiene ninguna base virtual, las clases de todos los miembros de datos no estáticos del tipo de clase tienen operadores de asignación triviales y las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen operadores de asignación triviales.

## <a name="is_trivially_move_assignable"></a>  is_trivially_move_assignable

Comprueba si el tipo tiene un operador de asignación de movimiento trivial.

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>Parámetros

*Ty*<br/>
Tipo que se va a consultar.

### <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *Ty* es una clase que tiene un movimiento trivial operador de asignación, en caso contrario, es false.

Un operador de asignación de movimiento para una clase *Ty* es trivial si:

se proporciona de forma implícita

la clase *Ty* no tiene ninguna función virtual

la clase *Ty* tiene ninguna base virtual

las clases de todos los miembros de datos no estáticos del tipo de clase tienen operadores de asignación de movimiento triviales

las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen operadores de asignación de movimiento triviales

## <a name="is_trivially_move_constructible"></a>  is_trivially_move_constructible

Comprueba si el tipo tiene un constructor de movimiento trivial.

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>Parámetros

*Ty*<br/>
Tipo que se va a consultar.

### <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *Ty* es una clase que tiene un constructor de movimiento trivial, en caso contrario, es false.

Un constructor de movimiento para una clase *Ty* es trivial si:

se declara de forma implícita

sus tipos de parámetro son equivalentes a los de una declaración implícita

la clase *Ty* no tiene ninguna función virtual

la clase *Ty* tiene ninguna base virtual

la clase no tiene ningún miembro de datos no estáticos volátil

todas las bases directas de la clase *Ty* tienen constructores de movimiento trivial

las clases de todos los miembros de datos no estáticos del tipo de clase tienen constructores de movimiento triviales

las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen constructores de movimiento triviales

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
