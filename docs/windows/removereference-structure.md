---
title: RemoveReference (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RemoveReference
dev_langs:
- C++
helpviewer_keywords:
- RemoveReference structure
ms.assetid: 43ff91bb-815a-440e-b9fb-7dcbb7c863af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d73c9f99eec3fd3ec01d4ae5d41418c67cb472f9
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597470"
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

*T*  
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

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)