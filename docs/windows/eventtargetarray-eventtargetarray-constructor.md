---
title: Constructor Eventtargetarray | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray
dev_langs:
- C++
helpviewer_keywords:
- EventTargetArray, constructor
ms.assetid: 6c6d3737-3cd3-4515-a8f6-d27901bb8ed2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2bbf6cb67973d7538aa7aea0d846cbadf030d585
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42590657"
---
# <a name="eventtargetarrayeventtargetarray-constructor"></a>EventTargetArray::EventTargetArray (Constructor)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
EventTargetArray(
   _Out_ HRESULT* hr,
   size_t items
);
```

### <a name="parameters"></a>Parámetros

*recursos humanos*  
Después de las operaciones de este constructor, parámetro *hr* indica si la asignación de la matriz se realizó correctamente o no. La tabla siguiente enumeran los valores posibles para *hr*.

S_OK, la operación se realizó correctamente.

No se pudo asignar memoria E_OUTOFMEMORY para la matriz.

Parámetro S_FALSE *elementos* es menor o igual que cero.

*elementos*  
El número de elementos de matriz que se va a asignar.

## <a name="remarks"></a>Comentarios

Inicializa una nueva instancia de la **EventTargetArray** clase.

**EventTargetArray** se usa para mantener una matriz de controladores de eventos en un `EventSource` objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** event.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[EventTargetArray (clase)](../windows/eventtargetarray-class.md)  
[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)