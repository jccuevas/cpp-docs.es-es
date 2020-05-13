---
title: Operadores de &lt;thread&gt;
ms.date: 11/04/2016
f1_keywords:
- thread/std::operator!=
- thread/std::operator&gt;
- thread/std::operator&gt;=
- thread/std::operator&lt;
- thread/std::operator&lt;&lt;
- thread/std::operator&lt;=
- thread/std::operator==
ms.assetid: e6bb6c0f-64f9-4cb2-9ff2-05b88a6ba7ac
helpviewer_keywords:
- std::operator!= (thread)
- std::operator&gt; (thread)
- std::operator&gt;= (thread)
- std::operator&lt; (thread)
- std::operator&lt;&lt; (thread)
- std::operator&lt;= (thread)
- std::operator== (thread)
ms.openlocfilehash: 6312d14dc681736ee396d5c7af6c50ba8d72cd3a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375833"
---
# <a name="ltthreadgt-operators"></a>Operadores de &lt;thread&gt;

||||
|-|-|-|
|[¡Operador!](#op_neq)|[Operador&gt;](#op_gt)|[Operador&gt;=](#op_gt_eq)|
|[Operador&lt;](#op_lt)|[Operador&lt;&lt;](#op_lt_lt)|[Operador&lt;=](#op_lt_eq)|
|[operadora](#op_eq_eq)|

## <a name="operatorgt"></a><a name="op_gt_eq"></a>Operador&gt;=

Determina si un objeto `thread::id` es mayor o igual que otro objeto.

```cpp
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto `thread::id` izquierdo.

*Correcto*\
Objeto `thread::id` derecho.

### <a name="return-value"></a>Valor devuelto

`!(Left < Right)`

### <a name="remarks"></a>Observaciones

Esta función no produce ninguna excepción.

## <a name="operatorgt"></a><a name="op_gt"></a>Operador&gt;

Determina si un objeto `thread::id` es mayor que otro objeto.

```cpp
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto `thread::id` izquierdo.

*Correcto*\
Objeto `thread::id` derecho.

### <a name="return-value"></a>Valor devuelto

`Right < Left`

### <a name="remarks"></a>Observaciones

Esta función no produce ninguna excepción.

## <a name="operatorlt"></a><a name="op_lt_eq"></a>Operador&lt;=

Determina si un objeto `thread::id` es menor o igual que otro objeto.

```cpp
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto `thread::id` izquierdo.

*Correcto*\
Objeto `thread::id` derecho.

### <a name="return-value"></a>Valor devuelto

`!(Right < Left)`

### <a name="remarks"></a>Observaciones

Esta función no produce ninguna excepción.

## <a name="operatorlt"></a><a name="op_lt"></a>Operador&lt;

Determina si un objeto `thread::id` es menor que otro objeto.

```cpp
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto `thread::id` izquierdo.

*Correcto*\
Objeto `thread::id` derecho.

### <a name="return-value"></a>Valor devuelto

**true** si *Left* precede a *Right* en el orden total; de lo contrario, **false**.

### <a name="remarks"></a>Observaciones

El operador define una ordenación total en todos los objetos `thread::id`. Estos objetos pueden usarse como claves en contenedores asociativos.

Esta función no produce ninguna excepción.

## <a name="operator"></a><a name="op_neq"></a>¡Operador!

Compara dos objetos `thread::id` para determinar si no son iguales.

```cpp
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto `thread::id` izquierdo.

*Correcto*\
Objeto `thread::id` derecho.

### <a name="return-value"></a>Valor devuelto

`!(Left == Right)`

### <a name="remarks"></a>Observaciones

Esta función no produce ninguna excepción.

## <a name="operator"></a><a name="op_eq_eq"></a>operadora

Compara dos objetos `thread::id` para determinar si son iguales.

```cpp
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto `thread::id` izquierdo.

*Correcto*\
Objeto `thread::id` derecho.

### <a name="return-value"></a>Valor devuelto

**true** si los dos objetos representan el mismo subproceso de ejecución o si ninguno de los objetos representa un subproceso de ejecución; de lo contrario, **false**.

### <a name="remarks"></a>Observaciones

Esta función no produce ninguna excepción.

## <a name="operatorltlt"></a><a name="op_lt_lt"></a>Operador&lt;&lt;

Inserta una representación de texto de un objeto `thread::id` en una secuencia.

```cpp
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```

### <a name="parameters"></a>Parámetros

*Ostr*\
Un objeto [basic_ostream](../standard-library/basic-ostream-class.md).

*Id*\
Objeto `thread::id` .

### <a name="return-value"></a>Valor devuelto

*Ostr*.

### <a name="remarks"></a>Observaciones

Esta función inserta *Id* en *Ostr*.

Si dos objetos `thread::id` son iguales, las representaciones de texto insertadas de dichos objetos son iguales.

## <a name="see-also"></a>Consulte también

[\<>de hilo](../standard-library/thread.md)
