---
title: InterfaceList (estructura)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceList
helpviewer_keywords:
- InterfaceList structure
ms.assetid: 6ec3228d-eb3e-4b7e-aef1-7dcf17bdf61a
ms.openlocfilehash: 745348e81888b5a87c57fbb99d397fcd423c3ee1
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59025554"
---
# <a name="interfacelist-structure"></a>InterfaceList (estructura)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename T, typename U>
struct InterfaceList;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Un nombre de interfaz la primera interfaz en la lista recursiva.

*U*<br/>
Un nombre de interfaz las interfaces restantes en la lista recursiva.

## <a name="remarks"></a>Comentarios

Se utiliza para crear una lista recursiva de las interfaces.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|`FirstT`|Sinónimo de parámetro de plantilla *T*.|
|`RestT`|Sinónimo de parámetro de plantilla *U*.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`InterfaceList`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres**: Microsoft::WRL::Details

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](microsoft-wrl-details-namespace.md)