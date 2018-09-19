---
title: AddTail (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::AddTail
dev_langs:
- C++
helpviewer_keywords:
- AddTail method
ms.assetid: d0fafab9-049c-40e0-a40c-d126c9ee63e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6609bba6d7adbddda152007e4db45c82f8039bc0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603683"
---
# <a name="eventtargetarrayaddtail-method"></a>EventTargetArray::AddTail (Método)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
void AddTail(
   _In_ IUnknown* element
);
```

### <a name="parameters"></a>Parámetros

*Elemento*  
Puntero al controlador de eventos para anexar.

## <a name="remarks"></a>Comentarios

El controlador de eventos especificado se anexa al final de la matriz interna de controladores de eventos.

**AddTail()** está pensado para ser utilizado internamente por sólo el `EventSource` clase.

## <a name="requirements"></a>Requisitos

**Encabezado:** event.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[EventTargetArray (clase)](../windows/eventtargetarray-class.md)  
[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)