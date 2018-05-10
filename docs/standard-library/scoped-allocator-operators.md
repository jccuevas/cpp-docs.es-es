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
ms.openlocfilehash: 66cf60dd3d70719fe42645215b1190c9fb752ff3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
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

`left` La izquierda `scoped_allocator_adaptor` objeto.

`right` El derecho `scoped_allocator_adaptor` objeto.

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

`left` La izquierda `scoped_allocator_adaptor` objeto.

`right` El derecho `scoped_allocator_adaptor` objeto.

### <a name="return-value"></a>Valor devuelto

`left.outer_allocator() == right.outer_allocator() && left.inner_allocator() == right.inner_allocator()`

## <a name="see-also"></a>Vea también

[<scoped_allocator>](../standard-library/scoped-allocator.md)<br/>
