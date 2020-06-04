---
title: IsBaseOfStrict (estructura)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict
- internal/Microsoft::WRL::Details::IsBaseOfStrict::value
helpviewer_keywords:
- Microsoft::WRL::Details::IsBaseOfStrict structure
- Microsoft::WRL::Details::IsBaseOfStrict::value constant
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
ms.openlocfilehash: 71db5a1b52a7d7d5471c15591fb34d954b465d07
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371356"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict (estructura)

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename Base, typename Derived>
struct IsBaseOfStrict;

template <typename Base>
struct IsBaseOfStrict<Base, Base>;
```

### <a name="parameters"></a>Parámetros

*Base*<br/>
El tipo base.

*Derivado*<br/>
El tipo derivado.

## <a name="remarks"></a>Observaciones

Comprueba si un tipo es la base de otro.

La primera plantilla comprueba si un tipo se deriva de un tipo base, lo que puede producir **true** o **false**. La segunda plantilla comprueba si un tipo se deriva de sí mismo, lo que siempre produce **false**.

## <a name="members"></a>Miembros

### <a name="public-constants"></a>Constantes públicas

Nombre                            | Descripción
------------------------------- | --------------------------------------------------
[IsBaseOfStrict::value](#value) | Indica si un tipo es la base de otro.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IsBaseOfStrict`

## <a name="requirements"></a>Requisitos

**Encabezado:** internal.h

**Espacio de nombres:** Microsoft::WRL::Details

## <a name="isbaseofstrictvalue"></a><a name="value"></a>IsBaseOfStrict::value

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
static const bool value = __is_base_of(Base, Derived);
```

### <a name="remarks"></a>Observaciones

Indica si un tipo es la base de otro.

`value`es **true** `Base` si type es una `Derived`clase base del tipo , de lo contrario es **false**.
