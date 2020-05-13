---
title: EnableIf (estructura)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::EnableIf
helpviewer_keywords:
- EnableIf structure
ms.assetid: 7825b283-e6b2-4f39-a4b9-c03bcd431b8e
ms.openlocfilehash: 44c6293b56e9e03c23d0d8cebf2a112e6fcf3664
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214037"
---
# <a name="enableif-structure"></a>EnableIf (estructura)

Es compatible con la infraestructura de WRL y no está diseñada para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <bool b, typename T = void>
struct EnableIf;

template <typename T>
struct EnableIf<true, T>;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Un tipo.

*b*<br/>
Expresión booleana.

## <a name="remarks"></a>Observaciones

Define un miembro de datos del tipo especificado por el segundo parámetro de plantilla si el primer parámetro de plantilla se evalúa como **true**.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

|Nombre|Descripción|
|----------|-----------------|
|`type`|Si el parámetro de plantilla *b* se evalúa como **true**, la especialización parcial define `type` de miembro de datos de tipo `T`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`EnableIf`

## <a name="requirements"></a>Requisitos

**Encabezado:** Internal. h

**Espacio de nombres:** Microsoft:: WRL::D etalles

## <a name="see-also"></a>Consulte también

[Microsoft::WRL::Details (espacio de nombres)](microsoft-wrl-details-namespace.md)
