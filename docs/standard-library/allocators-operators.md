---
title: '&lt;allocators&gt; (operadores)'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: a21708ca090b0db561391308f347d90b77c62645
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623569"
---
# <a name="ltallocatorsgt-operators"></a>&lt;allocators&gt; (operadores)

Estas son las funciones de operador de plantilla global definidas en los &lt; asignadores &gt; . Para las funciones de operador de miembro de clase, vea la documentación de la clase.

|||
|-|-|
|[operador! =](#op_neq)|[operador = =](#op_eq_eq)|

## <a name="operator"></a><a name="op_neq"></a>operador! =

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
|*salido*|Uno de los objetos de asignador cuya desigualdad se va a comprobar.|
|*correcta*|Uno de los objetos de asignador cuya desigualdad se va a comprobar.|

### <a name="return-value"></a>Valor devuelto

**True** si los objetos de asignador no son iguales y **False** si son iguales.

### <a name="remarks"></a>Observaciones

El operador de la plantilla devuelve `!(left == right)`.

## <a name="operator"></a><a name="op_eq_eq"></a>operador = =

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
|*salido*|Uno de los objetos de asignador cuya igualdad se va a comprobar.|
|*correcta*|Uno de los objetos de asignador cuya igualdad se va a comprobar.|

### <a name="return-value"></a>Valor devuelto

**True** si los objetos de asignador son iguales y **False** si no lo son.

### <a name="remarks"></a>Observaciones

Este operador de la plantilla devuelve `left.equals(right)`.

## <a name="see-also"></a>Consulte también

[\<allocators>](allocators-header.md)
