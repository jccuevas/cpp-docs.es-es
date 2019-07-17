---
title: variante de clase
ms.date: 04/04/2019
f1_keywords:
- variant/std::variant
- variant/std::variant::emplace
- variant/std::variant::index
- variant/std::variant::valueless_by_exception
helpviewer_keywords:
- variant/std::variant
- variant/std::variant::emplace
- variant/std::variant::index
- variant/std::variant::valueless_by_exception
ms.openlocfilehash: 9bfdf644374a0b825fd0ca02bf4164a766cb42a3
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269307"
---
# <a name="variant-class"></a>variante de clase

Cualquier instancia de la variante en un momento dado o contiene un valor de uno de sus tipos alternativos o no contiene ningún valor.

## <a name="syntax"></a>Sintaxis

```cpp
template <class... Types>
    class variant
```

## <a name="members"></a>Miembros

### <a name="constructors"></a>Constructores

|||
|-|-|
|[Variant](#variant)|Construye un objeto de tipo `variant`.|

### <a name="functions"></a>Funciones

|||
|-|-|
|[emplace](#emplace)|Crea un nuevo valor contenido.|
|[index](#index)|Devuelve el índice de un valor independiente.|
|[swap](#swap)||
|[valueless_by_exception](#emplace)|Devuelve **false** si la variante contiene un valor.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator=](#op_eq)|La variante se reemplaza con una copia de otro tipo de variante.|

## <a name="emplace"></a> emplace

Crea un nuevo valor contenido.

```cpp
template <class T, class... Args>
    T& emplace(Args&&...);
template <class T, class U, class... Args>
    T& emplace(initializer_list<U>, Args&&...);
template <size_t I, class... Args>
    variant_alternative_t<I, variant<Types...>>& emplace(Args&&...);
template <size_t I, class U, class... Args>
    variant_alternative_t<I, variant<Types...>>& emplace(initializer_list<U>, Args&&...);
```

## <a name="index"></a> Índice

Devuelve el índice de un valor independiente.

```cpp
constexpr size_t index() const noexcept;
```

## <a name="variant"></a> Variant

Construye un objeto de tipo `variant`. También incluye un destructor.

```cpp
constexpr variant() noexcept(see below);
variant(const variant&);
variant(variant&&) noexcept(see below);
template <class T>
    constexpr variant(T&&) noexcept(see below);
template <class T, class... Args>
    constexpr explicit variant(in_place_type_t<T>, Args&&...);
template <class T, class U, class... Args>
    constexpr explicit variant(in_place_type_t<T>, initializer_list<U>, Args&&...);
template <size_t I, class... Args>
    constexpr explicit variant(in_place_index_t<I>, Args&&...);
template <size_t I, class U, class... Args>
    constexpr explicit variant(in_place_index_t<I>, initializer_list<U>, Args&&...);

template <class Alloc>
    variant(allocator_arg_t, const Al&);
template <class Alloc>
    variant(allocator_arg_t, const Al&, const variant&);
template <class Alloc>
    variant(allocator_arg_t, const Al&, variant&&);
template <class Alloc, class T>
    variant(allocator_arg_t, const Al&, T&&);
template <class Alloc, class T, class... Args>
    variant(allocator_arg_t, const Al&, in_place_type_t<T>, Args&&...);
template <class Alloc, class T, class U, class... Args>
    variant(allocator_arg_t, const Al&, in_place_type_t<T>, initializer_list<U>, Args&&...);
template <class Alloc, size_t I, class... Args>
    variant(allocator_arg_t, const Al&, in_place_index_t<I>, Args&&...);
template <class Alloc, size_t I, class U, class... Args>
    variant(allocator_arg_t, const Al&, in_place_index_t<I>, initializer_list<U>, Args&&...);

~variant();
```

### <a name="parameters"></a>Parámetros

*Al*\
La clase de asignador que se usa con este objeto.

## <a name="op_eq"></a> operator=

La variante se reemplaza con una copia de otro tipo de variante.

```cpp
variant& operator=(const variant&);
variant& operator=(variant&&) noexcept(see below);
template <class T>
    variant& operator=(T&&) noexcept(see below);
```

## <a name="swap"></a> intercambio

```cpp
void swap(variant&) noexcept(see below);
```

## <a name="valueless"></a> valueless_by_exception

Devuelve **false** si la variante contiene un valor.

```cpp
constexpr bool valueless_by_exception() const noexcept;
```
