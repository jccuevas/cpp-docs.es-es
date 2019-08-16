---
title: '&lt;forward_list&gt; (Operadores)'
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::operator!=
- forward_list/std::operator==
- forward_list/std::operatoroperator&gt;
- forward_list/std::operatoroperator&gt=;
- forward_list/std::operatoroperator&lt;
- forward_list/std::operatoroperator&lt;=
ms.assetid: 57492e09-3836-4dbc-9ae5-78ecf506c190
helpviewer_keywords:
- std::operator!= (forward_list)
- std::operator== (forward_list)
- std::operatoroperator&gt; (forward_list)
- std::operatoroperator&gt=; (forward_list)
- std::operatoroperator&lt; (forward_list)
- std::operatoroperator&lt;= (forward_list)
ms.openlocfilehash: 64a49273cafd72158f176ee34ec271557ebee097
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240660"
---
# <a name="ltforwardlistgt-operators"></a>&lt;forward_list&gt; (Operadores)

## <a name="op_eq_eq"></a> operador ==

Comprueba si el objeto de lista de reenvíos del lado izquierdo del operador es igual que el objeto de lista de reenvíos del lado derecho.

```cpp
bool operator==(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto de tipo `forward_list`.

*Correcto*\
Objeto de tipo `forward_list`.

### <a name="remarks"></a>Comentarios

Esta función de plantilla sobrecarga `operator==` para comparar dos objetos de clase de plantilla `forward_list`. La función devuelve `distance(left.begin(), end()) == distance(right.begin(),right.end()) && equal(left. begin(),left. end(),right.begin())`.

## <a name="op_neq"></a> operador! =

Comprueba si el objeto de lista de reenvíos del lado izquierdo del operador no es igual que el objeto de lista de reenvíos del lado derecho.

```cpp
bool operator!=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto de tipo `forward_list`.

*Correcto*\
Objeto de tipo `forward_list`.

### <a name="return-value"></a>Valor devuelto

**True** si las listas no son iguales; **False** si son iguales.

### <a name="remarks"></a>Comentarios

Esta función de plantilla devuelve `!(left == right)`.

## <a name="op_lt"></a> operator&lt;

Comprueba si el objeto de lista de reenvíos del lado izquierdo del operador es menor que el objeto de lista de reenvíos del lado derecho.

```cpp
bool operator<(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto de tipo `forward_list`.

*Correcto*\
Objeto de tipo `forward_list`.

### <a name="return-value"></a>Valor devuelto

**True** si la lista del lado izquierdo del operador es menor pero no igual que la lista del lado derecho del operador. En caso contrario, **False**.

### <a name="remarks"></a>Comentarios

Esta función de plantilla sobrecarga `operator<` para comparar dos objetos de clase de plantilla `forward_list`. La función devuelve `lexicographical_compare(lhs. begin(), lhs. end(), rhs.begin(), rhs.end())`.

## <a name="op_lt_eq"></a> Operador&lt;=

Comprueba si el objeto de lista de reenvíos del lado izquierdo del operador es menor o igual que el objeto de lista de reenvíos del lado derecho.

```cpp
bool operator<=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto de tipo `forward_list`.

*Correcto*\
Objeto de tipo `forward_list`.

### <a name="return-value"></a>Valor devuelto

**True** si la lista del lado izquierdo del operador es menor o igual que la lista del lado derecho del operador. En caso contrario, **False**.

### <a name="remarks"></a>Comentarios

Esta función de plantilla devuelve `!(right < left)`.

## <a name="op_gt"></a> operator&gt;

Comprueba si el objeto de lista de reenvíos del lado izquierdo del operador es mayor que el objeto de lista de reenvíos del lado derecho.

```cpp
bool operator>(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto de tipo `forward_list`.

*Correcto*\
Objeto de tipo `forward_list`.

### <a name="return-value"></a>Valor devuelto

**True** si la lista del lado izquierdo del operador es mayor que la lista del lado derecho del operador. En caso contrario, **False**.

### <a name="remarks"></a>Comentarios

Esta función de plantilla devuelve `right < left`.

## <a name="op_gt_eq"></a> Operador&gt;=

Comprueba si el objeto de lista de reenvíos del lado izquierdo del operador es mayor o igual que el objeto de lista de reenvíos del lado derecho.

```cpp
bool operator>=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto de tipo `forward_list`.

*Correcto*\
Objeto de tipo `forward_list`.

### <a name="return-value"></a>Valor devuelto

**True** si la lista de reenvíos en el lado izquierdo del operador es mayor o igual a la lista de reenvíos en el lado derecho del operador; en caso contrario **false**.

### <a name="remarks"></a>Comentarios

La función de plantilla devuelve `!(left < right)`.
