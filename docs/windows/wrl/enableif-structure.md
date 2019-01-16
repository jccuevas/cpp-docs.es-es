---
title: EnableIf (estructura)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::EnableIf
helpviewer_keywords:
- EnableIf structure
ms.assetid: 7825b283-e6b2-4f39-a4b9-c03bcd431b8e
ms.openlocfilehash: 7b65b11b9a67ba69ca546e9bf5c169f3f2b61765
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54337531"
---
# <a name="enableif-structure"></a>EnableIf (estructura)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

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

## <a name="remarks"></a>Comentarios

Define un miembro de datos del tipo especificado por el segundo parámetro de plantilla si se evalúa como el primer parámetro de plantilla **true**.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|`type`|Si el parámetro de plantilla *b* se evalúa como **true**, la especialización parcial define el miembro de datos `type` a ser de tipo `T`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`EnableIf`

## <a name="requirements"></a>Requisitos

**Encabezado:** internal.h

**Espacio de nombres**: Microsoft::WRL::Details

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](microsoft-wrl-details-namespace.md)