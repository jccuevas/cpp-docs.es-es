---
title: InspectableClass (Macro)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
ms.openlocfilehash: 55d5aed96ff7c8b01142f8d4de81a431fdfcc2d5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631600"
---
# <a name="inspectableclass-macro"></a>InspectableClass (Macro)

Establece el nivel de confianza y de nombre de clase en tiempo de ejecución.

## <a name="syntax"></a>Sintaxis

```cpp
InspectableClass(
   runtimeClassName,
   trustLevel)
```

### <a name="parameters"></a>Parámetros

*runtimeClassName*<br/>
El nombre textual completo de la clase en tiempo de ejecución.

*trustLevel*<br/>
Uno de los [TrustLevel](https://msdn.microsoft.com/library/br224625.aspx) valores enumerados.

## <a name="remarks"></a>Comentarios

El **InspectableClass** macro puede utilizarse solo con tipos de Windows en tiempo de ejecución.

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[RuntimeClass (clase)](../windows/runtimeclass-class.md)