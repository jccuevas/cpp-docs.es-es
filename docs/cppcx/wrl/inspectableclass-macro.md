---
title: InspectableClass (Macro)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
ms.openlocfilehash: ee2a76edb967923a03ce6720b4163baf1cc48c32
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500475"
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

## <a name="remarks"></a>Comentarios

La macro **inspectableclass (** solo se puede usar con tipos de Windows Runtime.

## <a name="requirements"></a>Requisitos

**Encabezado:** implementa. h

**Espacio de nombres**: Microsoft::WRL

## <a name="see-also"></a>Vea también

[RuntimeClass (clase)](runtimeclass-class.md)