---
title: ModuleType (enumeración)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ModuleType
helpviewer_keywords:
- ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
ms.openlocfilehash: 937649eada481f7c45359fa0816266f62dc03875
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54337501"
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

**Espacio de nombres**: Microsoft::WRL

## <a name="see-also"></a>Vea también

[Microsoft::WRL (espacio de nombres)](microsoft-wrl-namespace.md)