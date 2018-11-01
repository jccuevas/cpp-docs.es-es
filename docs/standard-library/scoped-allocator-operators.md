---
title: '&lt;scoped_allocator&gt; (operadores)'
ms.date: 11/04/2016
f1_keywords:
- scoped_allocator/std::operator!=
- scoped_allocator/std::operator==
ms.assetid: 4dfe0805-cc6e-479f-887f-a1c164f73837
ms.openlocfilehash: 7c9f2c3a2425bf3ac6e62ce7fcecfe9315c3e04e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512468"
---
# <a name="ltscopedallocatorgt-operators"></a>&lt;scoped_allocator&gt; (operadores)

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a> operator!=

Comprueba si dos objetos `scoped_allocator_adaptor` no son iguales.

```cpp
template <class Outer, class... Inner>
bool operator!=(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>Parámetros

*left*<br/>
Objeto `scoped_allocator_adaptor` izquierdo.

*right*<br/>
Objeto `scoped_allocator_adaptor` derecho.

### <a name="return-value"></a>Valor devuelto

`!(left == right)`

## <a name="op_eq_eq"></a>  operator==

Comprueba si dos objetos `scoped_allocator_adaptor` son iguales.

```cpp
template <class Outer, class... Inner>
bool operator==(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>Parámetros

*left*<br/>
Objeto `scoped_allocator_adaptor` izquierdo.

*right*<br/>
Objeto `scoped_allocator_adaptor` derecho.

### <a name="return-value"></a>Valor devuelto

`left.outer_allocator() == right.outer_allocator() && left.inner_allocator() == right.inner_allocator()`

## <a name="see-also"></a>Vea también

[<scoped_allocator>](../standard-library/scoped-allocator.md)<br/>
