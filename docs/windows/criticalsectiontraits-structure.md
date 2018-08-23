---
title: CriticalSectionTraits (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits
dev_langs:
- C++
helpviewer_keywords:
- CriticalSectionTraits structure
ms.assetid: c515a1b5-4eb0-40bc-9035-c4d9352c9de7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6d15f65ecc2253556a6812cfb90ef78f90c7fb29
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594739"
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits (estructura)

Se especializa un `CriticalSection` objeto sea compatible con una sección crítica no válida o una función para liberar una sección crítica.

## <a name="syntax"></a>Sintaxis

```
struct CriticalSectionTraits;
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|`Type`|Un **typedef** que define un puntero a una sección crítica. `Type` se define como `typedef CRITICAL_SECTION* Type;`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CriticalSectionTraits::GetInvalidValue (método)](../windows/criticalsectiontraits-getinvalidvalue-method.md)|Se especializa un `CriticalSection` plantilla para que la plantilla no siempre es válida.|
|[CriticalSectionTraits::Unlock (método)](../windows/criticalsectiontraits-unlock-method.md)|Se especializa un `CriticalSection` plantilla, por lo que admite liberar la propiedad del objeto especificado de sección crítica.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CriticalSectionTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** handletraits

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Wrappers::HandleTraits (espacio de nombres)](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)