---
title: IsSame (estructura)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsSame
- internal/Microsoft::WRL::Details::IsSame::value
helpviewer_keywords:
- Microsoft::WRL::Details::IsSame structure
- Microsoft::WRL::Details::IsSame::value constant
ms.assetid: 1eddbc3f-3cc5-434f-8495-e4477e1f868e
ms.openlocfilehash: fcaf33309521b44163022e0ffa9b1e03e53e2551
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371342"
---
# <a name="issame-structure"></a>IsSame (estructura)

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename T1, typename T2>
struct IsSame;

template <typename T1>
struct IsSame<T1, T1>;
```

### <a name="parameters"></a>Parámetros

*T1*<br/>
Un tipo.

*T2*<br/>
Otro tipo.

## <a name="remarks"></a>Observaciones

Comprueba si un tipo especificado es el mismo que otro tipo especificado.

## <a name="members"></a>Miembros

### <a name="public-constants"></a>Constantes públicas

Nombre                    | Descripción
----------------------- | --------------------------------------------------
[IsSame::value](#value) | Indica si un tipo es el mismo que otro.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IsSame`

## <a name="requirements"></a>Requisitos

**Encabezado:** internal.h

**Espacio de nombres:** Microsoft::WRL::Details

## <a name="issamevalue"></a><a name="value"></a>IsSame::value

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
template <typename T1, typename T2>
struct IsSame
{
    static const bool value = false;
};

template <typename T1>
struct IsSame<T1, T1>
{
    static const bool value = true;
};
```

### <a name="remarks"></a>Observaciones

Indica si un tipo es el mismo que otro.

`value`es **true** si los parámetros de plantilla son los mismos y **false** si los parámetros de plantilla son diferentes.
