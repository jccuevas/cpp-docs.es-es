---
title: InspectableClass (Macro)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
ms.openlocfilehash: cedf395ae98a423e0335851327b5fdda1a4bc7d6
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786091"
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
Uno de los [TrustLevel](/windows/desktop/api/inspectable/ne-inspectable-trustlevel) valores enumerados.

## <a name="remarks"></a>Comentarios

El **InspectableClass** macro puede utilizarse solo con tipos de Windows en tiempo de ejecución.

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres**: Microsoft::WRL

## <a name="see-also"></a>Vea también

[RuntimeClass (clase)](runtimeclass-class.md)