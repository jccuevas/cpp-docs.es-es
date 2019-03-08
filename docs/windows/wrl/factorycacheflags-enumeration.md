---
title: FactoryCacheFlags (Enumeración)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::FactoryCacheFlags
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
ms.openlocfilehash: 6fecacd6038d1c41e57515307c1b810d0623d16f
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54337555"
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags (Enumeración)

Determina si los objetos de fábrica se almacenan en caché.

## <a name="syntax"></a>Sintaxis

```cpp
enum FactoryCacheFlags;
```

## <a name="remarks"></a>Comentarios

De forma predeterminada, el generador de directiva de caché se especifica como el [ModuleType](moduletype-enumeration.md) parámetro de plantilla al crear un [módulo](module-class.md) objeto. Para reemplazar esta directiva, especifique un **FactoryCacheFlags** valor cuando se crea un objeto de fábrica.

|||
|-|-|
|`FactoryCacheDefault`|La directiva de caché de la `Module` se usa el objeto.|
|`FactoryCacheEnabled`|Permite el almacenamiento en caché de fábrica con independencia de la `ModuleType` parámetro de plantilla que se usa para crear un `Module` objeto.|
|`FactoryCacheDisabled`|Deshabilita la caché del generador con independencia de la `ModuleType` parámetro de plantilla que se usa para crear un `Module` objeto.|

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres**: Microsoft::WRL

## <a name="see-also"></a>Vea también

[Microsoft::WRL (espacio de nombres)](microsoft-wrl-namespace.md)