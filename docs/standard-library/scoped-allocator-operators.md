---
title: '&lt;scoped_allocator&gt; (operadores) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- scoped_allocator/std::operator!=
- scoped_allocator/std::operator==
dev_langs:
- C++
ms.assetid: 4dfe0805-cc6e-479f-887f-a1c164f73837
ms.openlocfilehash: c2c61e3fce5d1cf58f59bc9dd51920bccc0eb2f3
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966477"
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

*Izquierda* la izquierda `scoped_allocator_adaptor` objeto.

*Derecha* derecho `scoped_allocator_adaptor` objeto.

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

*Izquierda* la izquierda `scoped_allocator_adaptor` objeto.

*Derecha* derecho `scoped_allocator_adaptor` objeto.

### <a name="return-value"></a>Valor devuelto

`left.outer_allocator() == right.outer_allocator() && left.inner_allocator() == right.inner_allocator()`

## <a name="see-also"></a>Vea también

[<scoped_allocator>](../standard-library/scoped-allocator.md)<br/>
