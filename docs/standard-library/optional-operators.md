---
title: '&lt;opcional&gt; operadores'
ms.date: 11/04/2016
f1_keywords:
- optional/std::operator!=
- optional/std::operator==
- optional/std::operatoroperator&gt;
- optional/std::operatoroperator&gt=;
- optional/std::operatoroperator&lt;
- optional/std::operatoroperator&lt;=
ms.assetid: 57492e09-3836-4dbc-9ae5-78ecf506c190
helpviewer_keywords:
- std::operator!= (optional)
- std::operator== (optional)
- std::operatoroperator&gt; (optional)
- std::operatoroperator&gt=; (optional)
- std::operatoroperator&lt; (optional)
- std::operatoroperator&lt;= (optional)
ms.openlocfilehash: c5d0de435180054b186400384fc0583df5b03246
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268927"
---
# <a name="ltoptionalgt-operators"></a>&lt;opcional&gt; operadores

## <a name="op_eq_eq"></a> operador ==

Comprueba si el objeto `optional` en el lado izquierdo del operador es igual al objeto `optional` del lado derecho.

```cpp
template <class T, class U> constexpr bool operator==(const optional<T>& left, const optional<U>& right);
template <class T> constexpr bool operator==(const optional<T>& left, nullopt_t right) noexcept;
template <class T> constexpr bool operator==(nullopt_t left, const optional<T>& right) noexcept;
template <class T, class U> constexpr bool operator==(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator==(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Un objeto de tipo `optional`, `nullopt_t`, o `T`.

*Correcto*\
Un objeto de tipo `optional`, `nullopt_t`, o `T`.

## <a name="op_neq"></a> operador! =

Comprueba si el objeto `optional` en el lado izquierdo del operador no es igual al objeto `optional` del lado derecho.

```cpp
template <class T, class U> constexpr bool operator!=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator!=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator!=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator!=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator!=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Un objeto de tipo `optional`, `nullopt_t`, o `T`.

*Correcto*\
Un objeto de tipo `optional`, `nullopt_t`, o `T`.

### <a name="remarks"></a>Comentarios

Esta función de plantilla devuelve `!(left == right)`.

## <a name="op_lt"></a> operator&lt;

Comprueba si el objeto `optional` en el lado izquierdo del operador es menor que el objeto `optional` del lado derecho.

```cpp
template <class T, class U> constexpr bool operator<(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Un objeto de tipo `optional`, `nullopt_t`, o `T`.

*Correcto*\
Un objeto de tipo `optional`, `nullopt_t`, o `T`.

### <a name="return-value"></a>Valor devuelto

**True** si la lista del lado izquierdo del operador es menor pero no igual que la lista del lado derecho del operador. En caso contrario, **False**.

## <a name="op_lt_eq"></a> operator&lt;=

Comprueba si el objeto `optional` en el lado izquierdo del operador es menor o igual que el objeto `optional` del lado derecho.

```cpp
template <class T, class U> constexpr bool operator<=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Un objeto de tipo `optional`, `nullopt_t`, o `T`.

*Correcto*\
Un objeto de tipo `optional`, `nullopt_t`, o `T`.

### <a name="return-value"></a>Valor devuelto

**True** si la lista del lado izquierdo del operador es menor o igual que la lista del lado derecho del operador. En caso contrario, **False**.

### <a name="remarks"></a>Comentarios

Esta función de plantilla devuelve `!(right < left)`.

## <a name="op_gt"></a> operator&gt;

Comprueba si el objeto `optional` en el lado izquierdo del operador es mayor que el objeto `optional` del lado derecho.

```cpp
template <class T, class U> constexpr bool operator>(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Un objeto de tipo `optional`, `nullopt_t`, o `T`.

*Correcto*\
Un objeto de tipo `optional`, `nullopt_t`, o `T`.

### <a name="return-value"></a>Valor devuelto

**True** si la lista del lado izquierdo del operador es mayor que la lista del lado derecho del operador. En caso contrario, **False**.

### <a name="remarks"></a>Comentarios

Esta función de plantilla devuelve `right < left`.

## <a name="op_gt_eq"></a> Operador&gt;=

Comprueba si el objeto `optional` en el lado izquierdo del operador es mayor o igual que el objeto `optional` del lado derecho.

```cpp
template <class T, class U> constexpr bool operator>=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Un objeto de tipo `optional`, `nullopt_t`, o `T`.

*Correcto*\
Un objeto de tipo `optional`, `nullopt_t`, o `T`.

### <a name="return-value"></a>Valor devuelto

**true** si el `optional` del lado izquierdo del operador es mayor o igual que el `optional` del lado derecho del operador. De lo contrario es **false**.

### <a name="remarks"></a>Comentarios

La función de plantilla devuelve `!(left < right)`.