---
title: Clase opcional
ms.date: 11/04/2016
f1_keywords:
- optional/std::optional
- optional/std::optional::has_value
- optional/std::optional::reset
- optional/std::optional::value
- optional/std::optional::value_or
helpviewer_keywords:
- optional/std::optional
- optional/std::optional::has_value
- optional/std::optional::reset
- optional/std::optional::value
- optional/std::optional::value_or
ms.openlocfilehash: d9c4bf5356e6ff163ecdf7e1a80bc55453d59003
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689146"
---
# <a name="optional-class"></a>Clase opcional

La plantilla de clase `optional<T>` describe un objeto que puede contener o no un valor de tipo `T`, conocido como el *valor contenido*.

Cuando una instancia de `optional<T>` contiene un valor, el valor contenido se asigna dentro del almacenamiento del objeto `optional`, en una región adecuadamente alineada para el tipo `T`. Cuando un `optional<T>` se convierte en `bool`, el resultado se `true` si el objeto contiene un valor; de lo contrario, es `false`.

El tipo de objeto contenido `T` no debe ser [in_place_t](in-place-t-struct.md) ni [nullopt_t](nullopt-t-structure.md). `T` debe ser *puede destruir*, es decir, su destructor debe reclamar todos los recursos de propiedad y puede que no se produzca ninguna excepción.

La clase `optional` es nueva en C++ 17.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
class optional
{
    using value_type = T;
};

template<class T> optional(T) -> optional<T>;
```

## <a name="members"></a>Miembros

### <a name="constructors"></a>Constructores

|||
|-|-|
| **Constructores y destructor** | |
|[optional](#optional) | Construye un objeto de tipo `optional`. |
|[~ opcional](#optional-destructor) | Destruye un objeto de tipo `optional`. |
| **Asignación** | |
| [operator=](#op_eq) | Reemplaza el `optional` por una copia de otro `optional`. |
| [emplace](#op_eq) | Inicializa el valor contenido con los argumentos especificados. |
| **Swap** | |
| [swap](#swap) | Intercambia el valor contenido o el estado vacío con otro `optional`. |
| **Observadores** | |
| [has_value](#has_value) | Devuelve un valor que indica si un objeto `optional` contiene un valor. |
| [valor](#value) | Devuelve el valor contenido. |
| [value_or](#value_or) | Devuelve el valor contenido o una alternativa si no hay ningún valor. |
| [operator->](#op_as) | Hace referencia al valor contenido de un objeto `optional`. |
| [operator*](#op_mem) | Hace referencia al valor contenido de un objeto `optional`. |
| [operator bool](#op_bool) | Devuelve un valor que indica si un objeto `optional` contiene un valor. |
| **Modificadores** | |
| [reset](#reset) | Restablece el `optional` destruyendo cualquier valor contenido. |

## <a name="has_value"></a>has_value

```cpp
constexpr bool has_value() const noexcept;
```

## <a name="optional"></a>constructor opcional

Construye un objeto de tipo `optional`.

```cpp
constexpr optional() noexcept;
constexpr optional(nullopt_t nullopt) noexcept;
constexpr optional(const optional& rhs);
constexpr optional(optional&& rhs) noexcept;

template <class... Args>
constexpr explicit optional(in_place_t, Args&&... args);

template <class U, class... Args>
constexpr explicit optional(in_place_t, initializer_list<U> i_list, Args&&... args);

template <class U = T>
explicit constexpr optional(U&& rhs);

template <class U>
explicit optional(const optional<U>& rhs);

template <class U>
explicit optional(optional<U>&& rhs);
```

### <a name="parameters"></a>Parámetros

\ *RHS*
La `optional` de la que se va a copiar o al que se va a cambiar la construcción del valor contenido.

*i_list*\
Lista de inicializadores de la que se va a construir el valor contenido.

\ *args*
Lista de argumentos de la que se va a construir el valor contenido.

### <a name="remarks"></a>Comentarios

`constexpr optional() noexcept;`
`constexpr optional(nullopt_t nullopt) noexcept;` estos constructores construyen un `optional` que no contiene un valor.

`constexpr optional(const optional& rhs);` el constructor de copias inicializa el valor contenido del valor contenido del argumento. Se define como **Deleted** a menos que `is_copy_constructible_v<T>` sea true y es trivial si `is_trivially_copy_constructible_v<T>` es true.

`constexpr optional(optional&& rhs) noexcept;` el constructor de movimiento inicializa el valor contenido moviendo desde el valor contenido del argumento. No participa en la resolución de sobrecarga a menos que `is_move_constructible_v<T>` sea true y es trivial si `is_trivially_move_constructible_v<T>` es true.

`template <class... Args> constexpr explicit optional(in_place_t, Args&&... args);` Direct inicializa el valor contenido como si utilizara los argumentos `std::forward<Args>(args)`. Este constructor se `constexpr` si el constructor de `T` utilizado es `constexpr`. No participa en la resolución de sobrecarga a menos que `is_constructible_v<T, Args...>` sea true.

`template <class U, class... Args> constexpr explicit optional(in_place_t, initializer_list<U> i_list, Args&&... args);` Direct inicializa el valor contenido como si utilizara los argumentos `i_list, std::forward<Args>(args)`. Este constructor se `constexpr` si el constructor de `T` utilizado es `constexpr`. No participa en la resolución de sobrecarga a menos que `is_constructible_v<T, initializer_list<U>&, Args&&...>` sea true.

`template <class U = T> explicit constexpr optional(U&& rhs);` Direct inicializa el valor contenido como si utilizara `std::forward<U>(v)`. Este constructor se `constexpr` si el constructor de `T` utilizado es `constexpr`. No participa en la resolución de sobrecarga a menos que `is_constructible_v<T, U&&>` sea true y `is_same_v<remove_cvref_t<U>, in_place_t>` y `is_same_v<remove_cvref_t<U>, optional>` sean false.

`template <class U> explicit optional(const optional<U>& rhs);` si *RHS* contiene un valor, Direct inicializa el valor contenido del valor contenido del argumento. No participa en la resolución de sobrecarga a menos que `is_constructible_v<T, const U&>` sea true y `is_constructible_v<T, optional<U>&>`, `is_constructible_v<T, optional<U>&&>`, `is_constructible_v<T, const optional<U>&>`, `is_constructible_v<T, const optional<U>&&>`, `is_convertible_v<optional<U>&, T>`, `is_convertible_v<optional<U>&&, T>`, `is_convertible_v<const optional<U>&, T>`y `is_convertible_v<const optional<U>&&, T>` sean todos falsos.

`template <class U> explicit optional(optional<U>&& rhs);` si *RHS* contiene un valor, Direct inicializa el valor contenido como si se usara `std::move(*rhs)`. No participa en la resolución de sobrecarga a menos que `is_constructible_v<T, U&&>` sea true y `is_constructible_v<T, optional<U>&>`, `is_constructible_v<T, optional<U>&&>`, `is_constructible_v<T, const optional<U>&>`, `is_constructible_v<T, const optional<U>&&>`, `is_convertible_v<optional<U>&, T>`, `is_convertible_v<optional<U>&&, T>`, `is_convertible_v<const optional<U>&, T>`y `is_convertible_v<const optional<U>&&, T>` sean todos falsos.

## <a name="optional-destructor"></a>~ (destructor opcional)

Destruye cualquier valor contenido que no sea trivialmente puede destruir, si está presente, invocando su destructor.

```cpp
~optional();
```

### <a name="remarks"></a>Comentarios

Si `T` es trivialmente puede destruir, `optional<T>` también se puede destruir de forma trivial.

## <a name="op_eq"></a> operator=

Reemplaza el valor contenido de un `optional` por una copia o se mueve de otro `optional` valor contenido.

```cpp
optional& operator=(nullopt_t) noexcept;
optional& operator=(const optional& rhs);
optional& operator=(optional&&) noexcept( /* see below */ );

template <class U = T>
    optional& operator=(U&&);

template <class U>
optional& operator=(const optional<U>&);

template <class U>
    optional& operator=(optional<U>&&);

template <class... Args>
T& emplace(Args&&...);

template <class U, class... Args>
T& emplace(initializer_list<U>, Args&&...);
```

## <a name="op_as"></a>operador->

Desreferencia el valor contenido de un objeto `optional`.

```cpp
constexpr const T* operator->() const;
constexpr T* operator->();
```

## <a name="op_mem"></a>Operator

Desreferencia el valor contenido de un objeto `optional`.

```cpp
constexpr const T& operator*() const&;
constexpr T& operator*() &;
constexpr T&& operator*() &&;
constexpr const T&& operator*() const&&;
```

## <a name="op_bool"></a>operador bool

Indica si el objeto `optional` tiene un valor contenido.

```cpp
constexpr explicit operator bool() const noexcept;
```

## <a name="reset"></a>determinado

De hecho, llama al destructor del objeto contenido, si existe, y lo establece en un estado no inicializado.

```cpp
void reset() noexcept;
```

## <a name="swap"></a>pasar

```cpp
template<class T>
void swap(optional<T>&, optional<T>&) noexcept;
```

## <a name="value"></a>valor

```cpp
constexpr const T& value() const&;
constexpr T& value() &;
constexpr T&& value() &&;
constexpr const T&& value() const&&;
```

## <a name="value_or"></a>value_or

```cpp
template <class U>
    constexpr T value_or(U&&) const&;
template <class U>
    constexpr T value_or(U&&) &&;
```

## <a name="see-also"></a>Vea también

[\<opcional >](optional.md)
