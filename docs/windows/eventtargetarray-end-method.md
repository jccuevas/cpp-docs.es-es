---
title: Método Eventtargetarray | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::End
dev_langs:
- C++
helpviewer_keywords:
- End method
ms.assetid: 20c491b8-f355-4d8f-ad14-8f46121d9af6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 17f79830cf50d83058ee2f2665b94f86a53acd78
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428985"
---
# <a name="eventtargetarrayend-method"></a>EventTargetArray::End (Método)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
ComPtr<IUnknown>* End();
```

## <a name="return-value"></a>Valor devuelto

La dirección del último elemento de la matriz interna de controladores de eventos.

## <a name="remarks"></a>Comentarios

Obtiene la dirección del último elemento de la matriz interna de controladores de eventos.

## <a name="requirements"></a>Requisitos

**Encabezado:** event.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[EventTargetArray (clase)](../windows/eventtargetarray-class.md)<br/>
[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)