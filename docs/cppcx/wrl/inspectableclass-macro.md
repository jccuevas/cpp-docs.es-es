---
title: InspectableClass (Macro)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
ms.openlocfilehash: 755a8f58ffc290d73d6060b0b0924905ecbf6028
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213881"
---
# <a name="inspectableclass-macro"></a>InspectableClass (Macro)

Establece el nombre de clase en tiempo de ejecución y el nivel de confianza.

## <a name="syntax"></a>Sintaxis

```cpp
InspectableClass(
   runtimeClassName,
   trustLevel)
```

### <a name="parameters"></a>Parámetros

*runtimeClassName*<br/>
Nombre textual completo de la clase en tiempo de ejecución.

*trustLevel*<br/>
Uno de los valores enumerados de [trustLevel](/windows/win32/api/inspectable/ne-inspectable-trustlevel) .

## <a name="remarks"></a>Observaciones

La macro **inspectableclass (** solo se puede usar con tipos de Windows Runtime.

## <a name="requirements"></a>Requisitos

**Encabezado:** implementa. h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Consulte también

[RuntimeClass (clase)](runtimeclass-class.md)
