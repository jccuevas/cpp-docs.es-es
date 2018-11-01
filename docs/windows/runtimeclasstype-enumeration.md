---
title: RuntimeClassType (enumeración)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
ms.openlocfilehash: 62a82d5fab9fd22e23a5244d4fda3b7f5202304c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626816"
---
# <a name="runtimeclasstype-enumeration"></a>RuntimeClassType (enumeración)

Especifica el tipo de [RuntimeClass](../windows/runtimeclass-class.md) instancia que se admite.

## <a name="syntax"></a>Sintaxis

```cpp
enum RuntimeClassType;
```

## <a name="members"></a>Miembros

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`ClassicCom`|Una clase de tiempo de ejecución COM clásica.|
|`Delegate`|Equivalente a `ClassicCom`.|
|`InhibitFtmBase`|Deshabilita `FtmBase` compatibilidad con mientras `__WRL_CONFIGURATION_LEGACY__` no está definido.|
|`InhibitWeakReference`|Deshabilita la compatibilidad de la referencia débil.|
|`WinRt`|Una clase en tiempo de ejecución de Windows.|
|`WinRtClassicComMix`|Combinación de `WinRt` y `ClassicCom`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)