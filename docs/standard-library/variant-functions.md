---
title: '&lt;Variant&gt; funciones'
ms.date: 04/04/2019
f1_keywords:
- variant/std::get
- variant/std::get_if
- variant/std::holds_alternative
- variant/std::visit
ms.openlocfilehash: d558eb086e076ba22722080b0c19f3d5733136d2
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427624"
---
# <a name="ltvariantgt-functions"></a>&lt;Variant&gt; funciones

## <a name="get"></a>Obtener

Obtiene la variante de un objeto.

```cpp
template <size_t I, class... Types>
    constexpr variant_alternative_t<I, variant<Types...>>& get(variant<Types...>&);
template <size_t I, class... Types>
    constexpr variant_alternative_t<I, variant<Types...>>&& get(variant<Types...>&&);
template <size_t I, class... Types>
    constexpr const variant_alternative_t<I, variant<Types...>>& get(const variant<Types...>&);
template <size_t I, class... Types>
    constexpr const variant_alternative_t<I, variant<Types...>>&& get(const variant<Types...>&&);
template <class T, class... Types>
    constexpr T& get(variant<Types...>&);
template <class T, class... Types>
    constexpr T&& get(variant<Types...>&&);
template <class T, class... Types>
    constexpr const T& get(const variant<Types...>&);
template <class T, class... Types>
    constexpr const T&& get(const variant<Types...>&&);
```

## <a name="get_if"></a>get_if

Obtiene la variante de un objeto, si existe.

```cpp
template <size_t I, class... Types>
    constexpr add_pointer_t<variant_alternative_t<I, variant<Types...>>> get_if(variant<Types...>*) noexcept;
template <size_t I, class... Types>
    constexpr add_pointer_t<const variant_alternative_t<I, variant<Types...>>> get_if(const variant<Types...>*) noexcept;
template <class T, class... Types>
    constexpr add_pointer_t<T> get_if(variant<Types...>*) noexcept;
template <class T, class... Types>
    constexpr add_pointer_t<const T> get_if(const variant<Types...>*) noexcept;
```

## <a name="holds_alternative"></a>holds_alternative

Devuelve **true** si existe una variante.

```cpp
template <class T, class... Types>
    constexpr bool holds_alternative(const variant<Types...>&) noexcept;
```

## <a name="swap"></a>pasar

```cpp
template <class... Types>
    void swap(variant<Types...>&, variant<Types...>&) noexcept(see below);
```

## <a name="variant_npos"></a>variant_npos

```cpp
namespace std {
    inline constexpr size_t variant_npos = -1;
}
```

## <a name="visit"></a>Revise

Se desplaza a la siguiente **variante**.

```cpp
template <class Visitor, class... Variants>
    constexpr see below
        visit(Visitor&&, Variants&&...);
```
