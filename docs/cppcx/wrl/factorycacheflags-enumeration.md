---
title: FactoryCacheFlags (Enumeración)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::FactoryCacheFlags
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
ms.openlocfilehash: 250c8c8e7ade72bd1a9cd63f0b515774058f0723
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214011"
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags (Enumeración)

Determina si los objetos de generador están almacenados en caché.

## <a name="syntax"></a>Sintaxis

```cpp
enum FactoryCacheFlags;
```

## <a name="remarks"></a>Observaciones

De forma predeterminada, la Directiva de almacenamiento en caché de la factoría se especifica como el parámetro de plantilla [ModuleType](moduletype-enumeration.md) cuando se crea un objeto de [módulo](module-class.md) . Para invalidar esta Directiva, especifique un valor de **factorycacheflags (** al crear un objeto de generador.

|||
|-|-|
|`FactoryCacheDefault`|Se usa la Directiva de almacenamiento en caché del objeto `Module`.|
|`FactoryCacheEnabled`|Habilita el almacenamiento en caché de fábrica independientemente del parámetro de plantilla `ModuleType` que se usa para crear un objeto `Module`.|
|`FactoryCacheDisabled`|Deshabilita el almacenamiento en caché de fábrica independientemente del parámetro de plantilla `ModuleType` que se usa para crear un objeto `Module`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** implementa. h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Consulte también

[Microsoft::WRL (espacio de nombres)](microsoft-wrl-namespace.md)
