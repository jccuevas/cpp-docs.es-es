---
title: InterfaceList (estructura)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceList
helpviewer_keywords:
- InterfaceList structure
ms.assetid: 6ec3228d-eb3e-4b7e-aef1-7dcf17bdf61a
ms.openlocfilehash: 7fd06f71bc4d8097366dc0e87d7ff92c5a12a790
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213868"
---
# <a name="interfacelist-structure"></a>InterfaceList (estructura)

Es compatible con la infraestructura de WRL y no está diseñada para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename T, typename U>
struct InterfaceList;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Un nombre de interfaz; la primera interfaz de la lista recursiva.

*U*<br/>
Un nombre de interfaz; las interfaces restantes de la lista recursiva.

## <a name="remarks"></a>Observaciones

Se utiliza para crear una lista recursiva de interfaces.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

|Nombre|Descripción|
|----------|-----------------|
|`FirstT`|Sinónimo del parámetro de plantilla *T*.|
|`RestT`|Sinónimo del parámetro de plantilla *U*.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`InterfaceList`

## <a name="requirements"></a>Requisitos

**Encabezado:** implementa. h

**Espacio de nombres:** Microsoft:: WRL::D etalles

## <a name="see-also"></a>Consulte también

[Microsoft::WRL::Details (espacio de nombres)](microsoft-wrl-details-namespace.md)
