---
title: ImplementsHelper (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper
dev_langs:
- C++
helpviewer_keywords:
- ImplementsHelper structure
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4ff40e03bf464d4c6f434b491c8b48d2b797d72b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440542"
---
# <a name="implementshelper-structure"></a>ImplementsHelper (estructura)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <
   typename RuntimeClassFlagsT,
   typename ILst,
   bool IsDelegateToClass
>
friend struct Details::ImplementsHelper;
```

### <a name="parameters"></a>Parámetros

*RuntimeClassFlagsT*<br/>
Un campo de marcas que especifica uno o más [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) enumeradores.

*ILst*<br/>
Una lista de identificadores de interfaz.

*IsDelegateToClass*<br/>
Especificar **true** si la instancia actual de `Implements` es una clase base de la primera Id. de interfaz en *ILst*; en caso contrario, **false**.

## <a name="remarks"></a>Comentarios

Ayuda a implementar la [implementa](../windows/implements-structure.md) estructura.

Recorre una lista de interfaces y los agrega como clases base y como la información necesaria para habilitar esta plantilla `QueryInterface`.

## <a name="members"></a>Miembros

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ImplementsHelper`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)