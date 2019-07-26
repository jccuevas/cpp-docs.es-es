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
ms.openlocfilehash: c0593b8016cf45abe64114958ccda84eb3704844
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458435"
---
# <a name="ltthreadgt-operators"></a>Operadores de &lt;thread&gt;

||||
|-|-|-|
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|
|[operator&lt;](#op_lt)|[operator&lt;&lt;](#op_lt_lt)|[operator&lt;=](#op_lt_eq)|
|[operator==](#op_eq_eq)|

## <a name="op_gt_eq"></a> operator&gt;=

Determina si un objeto `thread::id` es mayor o igual que otro objeto.

```cpp
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parámetros

*Salido*\
Objeto `thread::id` izquierdo.

*Correcta*\
Objeto `thread::id` derecho.

### <a name="return-value"></a>Valor devuelto

`!(Left < Right)`

### <a name="remarks"></a>Comentarios

Esta función no produce ninguna excepción.

## <a name="op_gt"></a> operator&gt;

Determina si un objeto `thread::id` es mayor que otro objeto.

```cpp
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parámetros

*Salido*\
Objeto `thread::id` izquierdo.

*Correcta*\
Objeto `thread::id` derecho.

### <a name="return-value"></a>Valor devuelto

`Right < Left`

### <a name="remarks"></a>Comentarios

Esta función no produce ninguna excepción.

## <a name="op_lt_eq"></a> operator&lt;=

Determina si un objeto `thread::id` es menor o igual que otro objeto.

```cpp
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parámetros

*Salido*\
Objeto `thread::id` izquierdo.

*Correcta*\
Objeto `thread::id` derecho.

### <a name="return-value"></a>Valor devuelto

`!(Right < Left)`

### <a name="remarks"></a>Comentarios

Esta función no produce ninguna excepción.

## <a name="op_lt"></a>  operator&lt;

Determina si un objeto `thread::id` es menor que otro objeto.

```cpp
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parámetros

*Salido*\
Objeto `thread::id` izquierdo.

*Correcta*\
Objeto `thread::id` derecho.

### <a name="return-value"></a>Valor devuelto

**true** si la *izquierda* precede a la *derecha* en el orden total; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

El operador define una ordenación total en todos los objetos `thread::id`. Estos objetos pueden usarse como claves en contenedores asociativos.

Esta función no produce ninguna excepción.

## <a name="op_neq"></a> operator!=

Compara dos objetos `thread::id` para determinar si no son iguales.

```cpp
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parámetros

*Salido*\
Objeto `thread::id` izquierdo.

*Correcta*\
Objeto `thread::id` derecho.

### <a name="return-value"></a>Valor devuelto

`!(Left == Right)`

### <a name="remarks"></a>Comentarios

Esta función no produce ninguna excepción.

## <a name="op_eq_eq"></a>  operator==

Compara dos objetos `thread::id` para determinar si son iguales.

```cpp
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parámetros

*Salido*\
Objeto `thread::id` izquierdo.

*Correcta*\
Objeto `thread::id` derecho.

### <a name="return-value"></a>Valor devuelto

**true** si los dos objetos representan el mismo subproceso de ejecución o si ningún objeto representa un subproceso de ejecución; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

Esta función no produce ninguna excepción.

## <a name="op_lt_lt"></a> operator&lt;&lt;

Inserta una representación de texto de un objeto `thread::id` en una secuencia.

```cpp
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```

### <a name="parameters"></a>Parámetros

*Ostr*\
Un objeto [basic_ostream](../standard-library/basic-ostream-class.md).

*Sesión*\
Objeto `thread::id`.

### <a name="return-value"></a>Valor devuelto

*Ostr*.

### <a name="remarks"></a>Comentarios

Esta función inserta el *identificador* en *ostr*.

Si dos objetos `thread::id` son iguales, las representaciones de texto insertadas de dichos objetos son iguales.

## <a name="see-also"></a>Vea también

[\<thread>](../standard-library/thread.md)
