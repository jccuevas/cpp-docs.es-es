---
title: FactoryCacheFlags (Enumeración)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::FactoryCacheFlags
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
ms.openlocfilehash: 8cf4af2ac0b4557fc6b175b84c47f83dd8a6e4ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398464"
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