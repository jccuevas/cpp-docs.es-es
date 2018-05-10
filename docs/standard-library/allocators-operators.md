---
title: '&lt;allocators&gt; (operadores) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
dev_langs:
- C++
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: 25e40157c1872df3e970bb234accab5c487c6287
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="ltallocatorsgt-operators"></a>&lt;allocators&gt; (operadores)

Éstas son las funciones de operador de plantilla global definidas en &lt;asignadores&gt;. Funciones de operador de miembro de clase, vea la documentación de la clase.

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a> operator!=

Comprueba la desigualdad entre los objetos de asignador de una clase especificada.

```cpp
template <class Type, class Sync>
bool operator!=(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|`left`|Uno de los objetos de asignador cuya desigualdad se va a comprobar.|
|`right`|Uno de los objetos de asignador cuya desigualdad se va a comprobar.|

### <a name="return-value"></a>Valor devuelto

**True** si los objetos de asignador no son iguales y **False** si son iguales.

### <a name="remarks"></a>Comentarios

El operador de la plantilla devuelve `!(left == right)`.

## <a name="op_eq_eq"></a>  operator==

Comprueba la igualdad entre los objetos de asignador de una clase especificada.

```cpp
template <class Type, class Sync>
bool operator==(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|`left`|Uno de los objetos de asignador cuya igualdad se va a comprobar.|
|`right`|Uno de los objetos de asignador cuya igualdad se va a comprobar.|

### <a name="return-value"></a>Valor devuelto

**True** si los objetos de asignador son iguales y **False** si no lo son.

### <a name="remarks"></a>Comentarios

Este operador de la plantilla devuelve `left.equals(right)`.

## <a name="see-also"></a>Vea también

[\<allocators>](../standard-library/allocators-header.md)
