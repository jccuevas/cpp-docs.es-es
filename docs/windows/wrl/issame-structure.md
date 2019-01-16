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
ms.openlocfilehash: b659f832756b79289181db34fa8d6fc0d974609d
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54337713"
---
# <a name="issame-structure"></a>IsSame (estructura)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

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

## <a name="remarks"></a>Comentarios

Las pruebas si un tipo especificado es igual que otro tipo especificado.

## <a name="members"></a>Miembros

### <a name="public-constants"></a>Constantes públicas

nombre                    | Descripción
----------------------- | --------------------------------------------------
[IsSame::value](#value) | Indica si un tipo es igual a otro.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IsSame`

## <a name="requirements"></a>Requisitos

**Encabezado:** internal.h

**Espacio de nombres**: Microsoft::WRL::Details

## <a name="value"></a>IsSame::value

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

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

### <a name="remarks"></a>Comentarios

Indica si un tipo es igual a otro.

`value` es **true** si los parámetros de plantilla son los mismos, y **false** si los parámetros de plantilla son diferentes.
