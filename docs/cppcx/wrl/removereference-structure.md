---
title: RemoveReference (estructura)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RemoveReference
helpviewer_keywords:
- RemoveReference structure
ms.assetid: 43ff91bb-815a-440e-b9fb-7dcbb7c863af
ms.openlocfilehash: 7753c1ad41f12fa8c14d2f10c9e2f91e043a5846
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213608"
---
# <a name="removereference-structure"></a>RemoveReference (estructura)

Es compatible con la infraestructura de WRL y no está diseñada para utilizarse directamente desde el código.

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
Clase.

## <a name="remarks"></a>Observaciones

Quita la referencia o el rasgo de referencia rvalue del parámetro de plantilla de clase especificado.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

|Nombre|Descripción|
|----------|-----------------|
|`Type`|Sinónimo del parámetro de plantilla de clase.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`RemoveReference`

## <a name="requirements"></a>Requisitos

**Encabezado:** Internal. h

**Espacio de nombres:** Microsoft:: WRL::D etalles

## <a name="see-also"></a>Consulte también

[Microsoft::WRL::Details (espacio de nombres)](microsoft-wrl-details-namespace.md)
