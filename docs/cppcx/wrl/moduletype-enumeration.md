---
title: ModuleType (enumeración)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ModuleType
helpviewer_keywords:
- ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
ms.openlocfilehash: 8425a15d594f7b8b30027d3576ee86015b656130
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213725"
---
# <a name="moduletype-enumeration"></a>ModuleType (enumeración)

Especifica si un módulo debe admitir un servidor en proceso o un servidor fuera de proceso.

## <a name="syntax"></a>Sintaxis

```cpp
enum ModuleType;
```

## <a name="members"></a>Members

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`InProc`|Un servidor en proceso.|
|`OutOfProc`|Un servidor fuera de proceso.|
|`DisableCaching`|Deshabilitar mecanismo de almacenamiento en caché en el módulo.|
|`InProcDisableCaching`|Combinación de `InProc` y `DisableCaching`.|
|`OutOfProcDisableCaching`|Combinación de `OutOfProc` y `DisableCaching`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** Module. h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Consulte también

[Microsoft::WRL (espacio de nombres)](microsoft-wrl-namespace.md)
