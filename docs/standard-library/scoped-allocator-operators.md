---
title: '&lt;scoped_allocator&gt; (operadores)'
ms.date: 11/04/2016
f1_keywords:
- scoped_allocator/std::operator!=
- scoped_allocator/std::operator==
ms.assetid: 4dfe0805-cc6e-479f-887f-a1c164f73837
ms.openlocfilehash: 45da89793c3f4ea131404fc3392413e7aea9ef3e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373381"
---
# <a name="ltscoped_allocatorgt-operators"></a>&lt;scoped_allocator&gt; (operadores)

|||
|-|-|
|[¡Operador!](#op_neq)|[operadora](#op_eq_eq)|

## <a name="operator"></a><a name="op_neq"></a>¡Operador!

Comprueba si dos objetos `scoped_allocator_adaptor` no son iguales.

```cpp
template <class Outer, class... Inner>
bool operator!=(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto `scoped_allocator_adaptor` izquierdo.

*Correcto*\
Objeto `scoped_allocator_adaptor` derecho.

### <a name="return-value"></a>Valor devuelto

`!(left == right)`

## <a name="operator"></a><a name="op_eq_eq"></a>operadora

Comprueba si dos objetos `scoped_allocator_adaptor` son iguales.

```cpp
template <class Outer, class... Inner>
bool operator==(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto `scoped_allocator_adaptor` izquierdo.

*Correcto*\
Objeto `scoped_allocator_adaptor` derecho.

### <a name="return-value"></a>Valor devuelto

`left.outer_allocator() == right.outer_allocator() && left.inner_allocator() == right.inner_allocator()`

## <a name="see-also"></a>Consulte también

[>de scoped_allocator<](../standard-library/scoped-allocator.md)
