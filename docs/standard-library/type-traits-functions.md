---
title: Funciones de &lt;type_traits&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: ff6d6066d90fe5049b89586ce657e62860c12f9f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861099"
---
# <a name="lttypetraitsgt-functions"></a>Funciones de &lt;type_traits&gt;

||||
|-|-|-|
|[is_assignable](#is_assignable)|[is_copy_assignable](#is_copy_assignable)|[is_copy_constructible](#is_copy_constructible)|
|[is_default_constructible](#is_default_constructible)|[is_move_assignable](#is_move_assignable)|[is_move_constructible](#is_move_constructible)|
|[is_nothrow_move_assignable](#is_nothrow_move_assignable)|[is_trivially_copy_assignable](#is_trivially_copy_assignable)|[is_trivially_move_assignable](#is_trivially_move_assignable)|
|[is_trivially_move_constructible](#is_trivially_move_constructible)|

## <a name="is_assignable"></a>  is_assignable

Comprueba si un valor de tipo `From` se puede asignar a un tipo `To`.

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>Parámetros

Para el tipo del objeto que recibe la asignación.

Desde el tipo del objeto que proporciona el valor.

### <a name="remarks"></a>Comentarios

La expresión no evaluada `declval<To>() = declval<From>()` debe tener un formato correcto. Tanto `From` como `To` deben ser tipos completos, `void` o matrices de límite desconocido.

## <a name="is_copy_assignable"></a>  is_copy_assignable

Comprueba si el tipo se puede copiar en la asignación.

```cpp
template <class Ty>
struct is_copy_assignable;
```

### <a name="parameters"></a>Parámetros

`Ty` El tipo de consulta.

### <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo `Ty` es una clase que tiene un operador de asignación de copia; en caso contrario, contiene false. Equivalente a is_assignable\<Ty&, const Ty&>.

## <a name="is_copy_constructible"></a>  is_copy_constructible

Comprueba si el tipo tiene un constructor de copia.

```cpp
template <class Ty>
struct is_copy_constructible;
```

### <a name="parameters"></a>Parámetros

`Ty` El tipo de consulta.

### <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo es true si el tipo `Ty` es una clase que tiene un constructor de copia; en caso contrario, es false.

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

`T` El tipo de consulta.

### <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo es true si el tipo `T` es una clase que tiene un constructor predeterminado; en caso contrario, es false. Es equivalente al elemento `is_constructible<T>`del predicado. El tipo `T` debe ser un tipo completo, `void`, o una matriz de límite desconocido.

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

`T` El tipo de consulta.

### <a name="remarks"></a>Comentarios

Un tipo se puede asignar mediante movimiento si una referencia a un valor R al tipo se puede asignar a una referencia al tipo. El predicado de tipo es equivalente a `is_assignable<T&, T&&>`. Los tipos que se pueden asignar mediante movimiento incluyen los tipos escalares a los que se puede hacer referencia y los tipos de clase que tienen operadores de asignación de movimiento generados por el compilador o definidos por el usuario.

## <a name="is_move_constructible"></a>  is_move_constructible

Comprueba si el tipo tiene un constructor de movimiento.

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>Parámetros

El tipo de T que se debe evaluar

### <a name="remarks"></a>Comentarios

Predicado de tipo que da como resultado True si el tipo `T` se puede construir mediante una operación de movimiento. Este predicado es equivalente a `is_constructible<T, T&&>`.

## <a name="is_nothrow_move_assignable"></a>  is_nothrow_move_assignable

Comprueba si el tipo tiene un operador de asignación de movimiento **nothrow**.

```cpp
template <class Ty>
struct is_nothrow_move_assignable;
```

### <a name="parameters"></a>Parámetros

`Ty` El tipo de consulta.

### <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo `Ty` tiene un operador de asignación de movimiento nothrow; en caso contrario, contiene false.

## <a name="is_trivially_copy_assignable"></a>  is_trivially_copy_assignable

Comprueba si el tipo tiene un operador de asignación de copia trivial.

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>Parámetros

`T` El tipo de consulta.

### <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo `T` es una clase que tiene un operador de asignación de copias trivial; en caso contrario, contiene false.

Un constructor de asignación para una clase `T` es trivial si se proporciona implícitamente, la clase `T` no tiene ninguna función virtual, la clase `T` no tiene ninguna base virtual, las clases de todos los miembros de datos no estáticos de tipo de clase tienen operadores de asignación triviales y las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen operadores de asignación triviales.

## <a name="is_trivially_move_assignable"></a>  is_trivially_move_assignable

Comprueba si el tipo tiene un operador de asignación de movimiento trivial.

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>Parámetros

`Ty` El tipo de consulta.

### <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo `Ty` es una clase que tiene un operador de asignación de movimiento trivial; en caso contrario, contiene false.

Un operador de asignación de movimiento para una clase `Ty` es trivial si:

se proporciona de forma implícita

la clase `Ty` no tiene ninguna función virtual

la clase `Ty` no tiene ninguna base virtual

las clases de todos los miembros de datos no estáticos del tipo de clase tienen operadores de asignación de movimiento triviales

las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen operadores de asignación de movimiento triviales

## <a name="is_trivially_move_constructible"></a>  is_trivially_move_constructible

Comprueba si el tipo tiene un constructor de movimiento trivial.

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>Parámetros

`Ty` El tipo de consulta.

### <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo `Ty` es una clase que tiene un constructor de movimiento trivial; en caso contrario, contiene false.

Un constructor de movimiento para una clase `Ty` es trivial si:

se declara de forma implícita

sus tipos de parámetro son equivalentes a los de una declaración implícita

la clase `Ty` no tiene ninguna función virtual

la clase `Ty` no tiene ninguna base virtual

la clase no tiene ningún miembro de datos no estáticos volátil

todas las bases directas de la clase `Ty` tienen constructores de movimiento trivial

las clases de todos los miembros de datos no estáticos del tipo de clase tienen constructores de movimiento triviales

las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen constructores de movimiento triviales

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
