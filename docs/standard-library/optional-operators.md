---
title: '&lt;operadores opcionales&gt;'
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
ms.openlocfilehash: 9bdef0669f90da7865f7652ff4528e51e584e1a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373636"
---
# <a name="ltoptionalgt-operators"></a>&lt;operadores opcionales&gt;

## <a name="operator"></a><a name="op_eq_eq"></a>operadora

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
Un objeto `optional`de `nullopt_t`tipo `T`, , o .

*Correcto*\
Un objeto `optional`de `nullopt_t`tipo `T`, , o .

## <a name="operator"></a><a name="op_neq"></a>¡Operador!

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
Un objeto `optional`de `nullopt_t`tipo `T`, , o .

*Correcto*\
Un objeto `optional`de `nullopt_t`tipo `T`, , o .

### <a name="remarks"></a>Observaciones

Esta función de plantilla devuelve `!(left == right)`.

## <a name="operatorlt"></a><a name="op_lt"></a>Operador&lt;

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
Un objeto `optional`de `nullopt_t`tipo `T`, , o .

*Correcto*\
Un objeto `optional`de `nullopt_t`tipo `T`, , o .

### <a name="return-value"></a>Valor devuelto

**True** si la lista del lado izquierdo del operador es menor pero no igual que la lista del lado derecho del operador. En caso contrario, **False**.

## <a name="operatorlt"></a><a name="op_lt_eq"></a>Operador&lt;=

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
Un objeto `optional`de `nullopt_t`tipo `T`, , o .

*Correcto*\
Un objeto `optional`de `nullopt_t`tipo `T`, , o .

### <a name="return-value"></a>Valor devuelto

**True** si la lista del lado izquierdo del operador es menor o igual que la lista del lado derecho del operador. En caso contrario, **False**.

### <a name="remarks"></a>Observaciones

Esta función de plantilla devuelve `!(right < left)`.

## <a name="operatorgt"></a><a name="op_gt"></a>Operador&gt;

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
Un objeto `optional`de `nullopt_t`tipo `T`, , o .

*Correcto*\
Un objeto `optional`de `nullopt_t`tipo `T`, , o .

### <a name="return-value"></a>Valor devuelto

**True** si la lista del lado izquierdo del operador es mayor que la lista del lado derecho del operador. En caso contrario, **False**.

### <a name="remarks"></a>Observaciones

Esta función de plantilla devuelve `right < left`.

## <a name="operatorgt"></a><a name="op_gt_eq"></a>Operador&gt;=

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
Un objeto `optional`de `nullopt_t`tipo `T`, , o .

*Correcto*\
Un objeto `optional`de `nullopt_t`tipo `T`, , o .

### <a name="return-value"></a>Valor devuelto

**true** si el `optional` del lado izquierdo del operador es mayor o igual que el `optional` del lado derecho del operador. De lo contrario es **false**.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve `!(left < right)`.
