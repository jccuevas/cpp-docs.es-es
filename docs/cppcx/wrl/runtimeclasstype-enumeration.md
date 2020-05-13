---
title: RuntimeClassType (enumeración)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
ms.openlocfilehash: 53f0172968c28762bb1305e274bbd47494cdaf4c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213582"
---
# <a name="runtimeclasstype-enumeration"></a>RuntimeClassType (enumeración)

Especifica el tipo de instancia de [RuntimeClass](runtimeclass-class.md) que se admite.

## <a name="syntax"></a>Sintaxis

```cpp
enum RuntimeClassType;
```

## <a name="members"></a>Members

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`ClassicCom`|Una clase en tiempo de ejecución COM clásica.|
|`Delegate`|Equivalente a `ClassicCom`.|
|`InhibitFtmBase`|Deshabilita la compatibilidad con `FtmBase` mientras no se define `__WRL_CONFIGURATION_LEGACY__`.|
|`InhibitWeakReference`|Deshabilita la compatibilidad con referencias débiles.|
|`WinRt`|Una clase Windows Runtime.|
|`WinRtClassicComMix`|Combinación de `WinRt` y `ClassicCom`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** implementa. h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Consulte también

[Microsoft::WRL (espacio de nombres)](microsoft-wrl-namespace.md)
