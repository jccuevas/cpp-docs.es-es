---
title: ModuleType (enumeración)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ModuleType
helpviewer_keywords:
- ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
ms.openlocfilehash: 3c7486cbc761975dd133f229f23dcf0b70e7e3ac
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039162"
---
# <a name="moduletype-enumeration"></a>ModuleType (enumeración)

Especifica si un módulo debe admitir un servidor en proceso o un servidor fuera de proceso.

## <a name="syntax"></a>Sintaxis

```cpp
enum ModuleType;
```

## <a name="members"></a>Miembros

### <a name="values"></a>Valores

|Name|Descripción|
|----------|-----------------|
|`InProc`|Un servidor en proceso.|
|`OutOfProc`|Un servidor fuera de proceso.|
|`DisableCaching`|Deshabilitar el mecanismo de almacenamiento en caché en el módulo.|
|`InProcDisableCaching`|Combinación de `InProc` y `DisableCaching`.|
|`OutOfProcDisableCaching`|Combinación de `OutOfProc` y `DisableCaching`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres**: Microsoft::WRL

## <a name="see-also"></a>Vea también

[Microsoft::WRL (Espacio de nombres)](microsoft-wrl-namespace.md)