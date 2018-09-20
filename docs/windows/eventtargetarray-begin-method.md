---
title: Método Eventtargetarray | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::Begin
dev_langs:
- C++
helpviewer_keywords:
- Begin method
ms.assetid: 1cc7fdfd-a2c4-4b28-93cf-1c82842294ba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b818595d8ad32295dbce1498161898b215e1885f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433781"
---
# <a name="eventtargetarraybegin-method"></a>EventTargetArray::Begin (Método)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
ComPtr<IUnknown>* Begin();
```

## <a name="return-value"></a>Valor devuelto

La dirección del primer elemento de la matriz interna de controladores de eventos.

## <a name="remarks"></a>Comentarios

Obtiene la dirección del primer elemento de la matriz interna de controladores de eventos.

## <a name="requirements"></a>Requisitos

**Encabezado:** event.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[EventTargetArray (clase)](../windows/eventtargetarray-class.md)<br/>
[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)