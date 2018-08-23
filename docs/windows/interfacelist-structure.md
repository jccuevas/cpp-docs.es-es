---
title: InterfaceList (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 61a8e7b36448a485705b914fbb37892271d7d9fc
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597171"
---
# <a name="interfacelist-structure"></a>InterfaceList (estructura)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <
   typename T,
   typename U
>
struct InterfaceList;
```

### <a name="parameters"></a>Parámetros

*T*  
Un nombre de interfaz la primera interfaz en la lista recursiva.

*U*  
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