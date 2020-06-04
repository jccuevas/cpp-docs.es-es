---
title: '&lt;allocators&gt; (operadores)'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: 7bc37e98ed85582cac8fc7ae21e54a6d5da9e06f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364956"
---
# <a name="ltallocatorsgt-operators"></a>&lt;allocators&gt; (operadores)

Estas son las funciones &lt;globales&gt;del operador de plantilla definidas en los asignadores. Para las funciones del operador de miembro de clase, consulte la documentación de la clase.

|||
|-|-|
|[¡Operador!](#op_neq)|[operadora](#op_eq_eq)|

## <a name="operator"></a><a name="op_neq"></a>¡Operador!

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
|*Izquierda*|Uno de los objetos de asignador cuya desigualdad se va a comprobar.|
|*Correcto*|Uno de los objetos de asignador cuya desigualdad se va a comprobar.|

### <a name="return-value"></a>Valor devuelto

**True** si los objetos de asignador no son iguales y **False** si son iguales.

### <a name="remarks"></a>Observaciones

El operador de la plantilla devuelve `!(left == right)`.

## <a name="operator"></a><a name="op_eq_eq"></a>operadora

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
|*Izquierda*|Uno de los objetos de asignador cuya igualdad se va a comprobar.|
|*Correcto*|Uno de los objetos de asignador cuya igualdad se va a comprobar.|

### <a name="return-value"></a>Valor devuelto

**True** si los objetos de asignador son iguales y **False** si no lo son.

### <a name="remarks"></a>Observaciones

Este operador de la plantilla devuelve `left.equals(right)`.

## <a name="see-also"></a>Consulte también

[\<asignadores>](../standard-library/allocators-header.md)
