---
title: ModuleBase (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ModuleBase
dev_langs:
- C++
helpviewer_keywords:
- ModuleBase class
ms.assetid: edce7591-6893-46f7-94a7-382827775548
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e6d60e5114d189ddede87899bb55fba25a296c57
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601476"
---
# <a name="modulebase-class"></a>ModuleBase (Clase)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
class ModuleBase;
```

## <a name="remarks"></a>Comentarios

Representa la clase base de la [módulo](../windows/module-class.md) clases.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[ModuleBase::ModuleBase (constructor)](../windows/modulebase-modulebase-constructor.md)|Inicializa una instancia de la clase `Module`.|
|[ModuleBase::~ModuleBase (destructor)](../windows/modulebase-tilde-modulebase-destructor.md)|Desinicializa la instancia actual de la `Module` clase.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[ModuleBase::DecrementObjectCount (método)](../windows/modulebase-decrementobjectcount-method.md)|Cuando se implementa, disminuye el número de objetos que sigue el módulo.|
|[ModuleBase::IncrementObjectCount (método)](../windows/modulebase-incrementobjectcount-method.md)|Cuando se implementa, incrementa el número de objetos que se hace un seguimiento mediante el módulo.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ModuleBase`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)