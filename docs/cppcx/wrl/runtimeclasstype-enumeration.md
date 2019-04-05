---
title: RuntimeClassType (enumeración)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
ms.openlocfilehash: 80e8a120f7e3666721ff839a2a696388a64d734e
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035963"
---
# <a name="runtimeclasstype-enumeration"></a>RuntimeClassType (enumeración)

Especifica el tipo de [RuntimeClass](runtimeclass-class.md) instancia que se admite.

## <a name="syntax"></a>Sintaxis

```cpp
enum RuntimeClassType;
```

## <a name="members"></a>Miembros

### <a name="values"></a>Valores

|Name|Descripción|
|----------|-----------------|
|`ClassicCom`|Una clase de tiempo de ejecución COM clásica.|
|`Delegate`|Equivalente a `ClassicCom`.|
|`InhibitFtmBase`|Deshabilita `FtmBase` compatibilidad con mientras `__WRL_CONFIGURATION_LEGACY__` no está definido.|
|`InhibitWeakReference`|Deshabilita la compatibilidad de la referencia débil.|
|`WinRt`|Una clase en tiempo de ejecución de Windows.|
|`WinRtClassicComMix`|Combinación de `WinRt` y `ClassicCom`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres**: Microsoft::WRL

## <a name="see-also"></a>Vea también

[Microsoft::WRL (Espacio de nombres)](microsoft-wrl-namespace.md)