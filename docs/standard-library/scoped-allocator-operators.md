---
title: '&lt;scoped_allocator&gt; (operadores) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- scoped_allocator/std::operator!=
- scoped_allocator/std::operator==
dev_langs:
- C++
ms.assetid: 4dfe0805-cc6e-479f-887f-a1c164f73837
caps.latest.revision: 10
manager: ghogen
ms.openlocfilehash: 5cb569c5f27ab297fa4844d1d5b412a5f614c1f1
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
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
