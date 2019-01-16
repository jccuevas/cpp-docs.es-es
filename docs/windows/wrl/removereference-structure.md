---
title: RemoveReference (estructura)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RemoveReference
helpviewer_keywords:
- RemoveReference structure
ms.assetid: 43ff91bb-815a-440e-b9fb-7dcbb7c863af
ms.openlocfilehash: 7364fd3a123336bd2419006a9de9d7880f12e538
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54337468"
---
# <a name="removereference-structure"></a>RemoveReference (estructura)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template<class T>
struct RemoveReference;

template<class T>
struct RemoveReference<T&>;

template<class T>
struct RemoveReference<T&&>;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Una clase.

## <a name="remarks"></a>Comentarios

Elimina el rasgo de referencia o referencia de rvalue desde el parámetro de plantilla de clase especificada.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|`Type`|Sinónimo del parámetro de plantilla de clase.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`RemoveReference`

## <a name="requirements"></a>Requisitos

**Encabezado:** internal.h

**Espacio de nombres**: Microsoft::WRL::Details

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](microsoft-wrl-details-namespace.md)