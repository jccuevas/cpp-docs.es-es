---
title: ModuleType (enumeración)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ModuleType
helpviewer_keywords:
- ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
ms.openlocfilehash: d822d214d9bad564286cd2c7494c9f480abdcf00
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50524753"
---
# <a name="moduletype-enumeration"></a>ModuleType (enumeración)

Especifica si un módulo debe admitir un servidor en proceso o un servidor fuera de proceso.

## <a name="syntax"></a>Sintaxis

```cpp
enum ModuleType;
```

## <a name="members"></a>Miembros

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`InProc`|Un servidor en proceso.|
|`OutOfProc`|Un servidor fuera de proceso.|
|`DisableCaching`|Deshabilitar el mecanismo de almacenamiento en caché en el módulo.|
|`InProcDisableCaching`|Combinación de `InProc` y `DisableCaching`.|
|`OutOfProcDisableCaching`|Combinación de `OutOfProc` y `DisableCaching`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)