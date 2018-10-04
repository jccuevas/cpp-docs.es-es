---
title: InterfaceList (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceList
dev_langs:
- C++
helpviewer_keywords:
- InterfaceList structure
ms.assetid: 6ec3228d-eb3e-4b7e-aef1-7dcf17bdf61a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3d9cbc1dfb31d744086e7a138521ae24f58e693f
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788661"
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

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)