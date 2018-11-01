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
ms.openlocfilehash: 4126b81f61bd37a7a12e0621c323ec832c5b2ab7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605345"
---
# <a name="ltforwardlistgt-operators"></a>&lt;forward_list&gt; (Operadores)

||||
|-|-|-|
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|
|[operator&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|

## <a name="op_eq_eq"></a>  operator==

Comprueba si el objeto de lista de reenvíos del lado izquierdo del operador es igual que el objeto de lista de reenvíos del lado derecho.

```cpp
bool operator==(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*left*|Objeto de tipo `forward_list`.|
|*right*|Objeto de tipo `forward_list`.|

### <a name="remarks"></a>Comentarios

Esta función de plantilla sobrecarga `operator==` para comparar dos objetos de clase de plantilla `forward_list`. La función devuelve `distance(left.begin(), end()) == distance(right.begin(),right.end()) && equal(left. begin(),left. end(),right.begin())`.

## <a name="op_neq"></a> operator!=

Comprueba si el objeto de lista de reenvíos del lado izquierdo del operador no es igual que el objeto de lista de reenvíos del lado derecho.

```cpp
bool operator!=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*left*|Objeto de tipo `forward_list`.|
|*right*|Objeto de tipo `forward_list`.|

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

|Parámetro|Descripción|
|---------------|-----------------|
|*left*|Objeto de tipo `forward_list`.|
|*right*|Objeto de tipo `forward_list`.|

### <a name="return-value"></a>Valor devuelto

**True** si la lista del lado izquierdo del operador es menor pero no igual que la lista del lado derecho del operador. En caso contrario, **False**.

### <a name="remarks"></a>Comentarios

Esta función de plantilla sobrecarga `operator<` para comparar dos objetos de clase de plantilla `forward_list`. La función devuelve `lexicographical_compare(lhs. begin(), lhs. end(), rhs.begin(), rhs.end())`.

## <a name="op_lt_eq"></a> operator&lt;=

Comprueba si el objeto de lista de reenvíos del lado izquierdo del operador es menor o igual que el objeto de lista de reenvíos del lado derecho.

```cpp
bool operator<=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*left*|Objeto de tipo `forward_list`.|
|*right*|Objeto de tipo `forward_list`.|

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

|Parámetro|Descripción|
|---------------|-----------------|
|*left*|Objeto de tipo `forward_list`.|
|*right*|Objeto de tipo `forward_list`.|

### <a name="return-value"></a>Valor devuelto

**True** si la lista del lado izquierdo del operador es mayor que la lista del lado derecho del operador. En caso contrario, **False**.

### <a name="remarks"></a>Comentarios

Esta función de plantilla devuelve `right < left`.

## <a name="op_gt_eq"></a> operator&gt;=

Comprueba si el objeto de lista de reenvíos del lado izquierdo del operador es mayor o igual que el objeto de lista de reenvíos del lado derecho.

```cpp
bool operator>=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*left*|Objeto de tipo `forward_list`.|
|*right*|Objeto de tipo `forward_list`.|

### <a name="return-value"></a>Valor devuelto

**True** si la lista de reenvíos en el lado izquierdo del operador es mayor o igual a la lista de reenvíos en el lado derecho del operador; en caso contrario **false**.

### <a name="remarks"></a>Comentarios

La función de plantilla devuelve `!(left < right)`.

## <a name="see-also"></a>Vea también

[<forward_list>](../standard-library/forward-list.md)<br/>
