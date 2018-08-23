---
title: Wrappers Namespace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details
- internal/Microsoft::WRL::Details
- async/Microsoft::WRL::Details
- corewrappers/Microsoft::WRL::Wrappers::Details
- client/Microsoft::WRL::Details
- module/Microsoft::WRL::Details
- event/Microsoft::WRL::Details
dev_langs:
- C++
helpviewer_keywords:
- Details namespace
ms.assetid: 6d3f04ac-9b53-4a82-a188-a85309ec34a4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3af5add0a934b59cf3027b7beb0ea000a7ae1415
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595712"
---
# <a name="microsoftwrlwrappersdetails-namespace"></a>Microsoft::WRL::Wrappers::Details (Espacio de nombres)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
namespace Microsoft::WRL::Wrappers::Details;
```

## <a name="members"></a>Miembros

### <a name="classes"></a>Clases

|Name|Descripción|
|----------|-----------------|
|[SyncLockT (clase)](../windows/synclockt-class.md)|Representa un tipo que puede tardar exclusivo o propiedad compartida de un recurso.|
|[SyncLockWithStatusT (clase)](../windows/synclockwithstatust-class.md)|Representa un tipo que puede tardar exclusivo o propiedad compartida de un recurso.|

### <a name="methods"></a>Métodos

|Name|Descripción|
|----------|-----------------|
|[CompareStringOrdinal (método)](../windows/comparestringordinal-method.md)|Compara dos especificado `HSTRING` objetos y devuelve un entero que indica su posición relativa en un criterio de ordenación.|

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Wrappers (espacio de nombres)](../windows/microsoft-wrl-wrappers-namespace.md)